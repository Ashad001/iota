# 02 — BACKEND SPEC

Read `01-MASTER-BRIEF.md` first. Where it says *decide*, decide and write it down in
`docs/decisions/`.

> **Overridden by `06-SUPABASE-SUPERMETRICS.md`:** §1 (layout), §2 (schema — every table
> gains `workspace_id` + RLS) and §3's streaming endpoint (replaced by Supabase
> Realtime). §4 onward stands as written. Read 06 before starting.

## 1. Layout

```
backend/
  app/
    api/            FastAPI routers
    core/           config, auth, logging, errors
    db/             SQLAlchemy models, migrations
    adapters/
      evidence/     base.py, manual_ad.py, search_reference.py,
                    user_upload.py, licensed_provider.py
      adsource/     base.py                # official-API adapter: interface only in v1
      image/        base.py, imagine_art.py, gemini.py
      video/        base.py, imagine_art.py, modelark.py
      asr/          base.py, whisper.py
      measurement/  base.py, supermetrics.py
    agents/         one module per pipeline agent
    prompts/        VERBATIM copies of 03-AGENT-PROMPTS.md
    pipeline/       steps/, orchestrator.py, state.py, events.py
    scoring/        ebos.py, coverage.py, clustering.py, dedupe.py
    evidence/       url_parser.py, intake.py, normalize.py, snapshots.py
    geo/            market_profiles.py, resolver.py
    workers/
  tests/
```

## 2. Source model

`AdSourceAdapter` remains the boundary, but Meta Graph is **not** the primary source
and is not required for v1. The primary interface is:

```python
class EvidenceSourceAdapter(Protocol):
    kind: Literal["manual_ad", "ad_library_search_reference",
                  "user_uploaded_evidence", "licensed_provider"]
    async def ingest(self, batch_id: UUID, payload: dict) -> list[EvidenceItem]: ...
```

### 2.1 `manual_ad`
User enters advertiser, copy, headline, CTA, platform(s), active/inactive status,
visible start date, and an optional Ad Library URL. Every field is stored with its
`provenance_kind` — `observed_in_user_evidence` when an attached artefact shows it,
`user_asserted` when they typed it unsupported.

### 2.2 `ad_library_search_reference`
User pastes a public Ad Library search URL. Parse and store **only safe, non-secret
filter metadata**: `q` / search term, `country`, `content_languages`, `active_status`,
`media_type`, `search_type`, and the requested `sort_data[mode]`. Preserve the original
URL verbatim as a reference link.

**The system never issues a request to this URL** — not to validate it, not to follow a
redirect, not to fetch a preview or favicon, not from a worker and not from an Edge
Function. Parsing is pure string work on a validated URL (`11 §2`). Write a test that
fails if any code path can reach the network from the parser.

Store the requested sort mode as *a filter the user chose*, never as a claim about the
data. `sort_data[mode]=total_impressions` means the user asked the UI to sort; it does
not mean any returned ad exposes an impression count.

### 2.3 `user_uploaded_evidence`
Screenshots, screen recordings, images, video files, exported text, or a CSV the user
is authorised to provide. Store the original file, its SHA-256, capture timestamp,
declared source URL, and uploader identity. **OCR, transcription, vision description
and structural teardown run only on user-supplied assets** — never on anything the
system fetched itself.

### 2.4 `licensed_provider`
Optional, **disabled by default**, surfaced in the UI as a separate paid data-source
option. May be enabled only after the provider's contract, terms, permitted-use scope,
retention rights and attribution obligations have been explicitly reviewed and recorded
in `licensed_sources`. A provider with no recorded review cannot be enabled by config
alone — the check is in code.

## 3. Domain model

```sql
brands(id, workspace_id, name, website, dossier jsonb, palette jsonb,
       voice jsonb, created_at)

markets(id, workspace_id, brand_id, label, country_codes text[], languages text[],
        currency, profile jsonb)

competitors(id, workspace_id, brand_id, market_id, name, domain,
            tier smallint, rationale, evidence jsonb, verified bool)

-- a saved public search the user can revisit; a reference, never an endpoint
search_references(id, workspace_id, competitor_id, market_id,
                  url text,                      -- verbatim, for the user to open
                  parsed jsonb,                  -- q, country, languages, active_status,
                                                 -- media_type, search_type, sort_mode
                  label, created_by, created_at)

evidence_batches(id, workspace_id, run_id, search_reference_id null,
                 label, captured_at, submitted_by, submitted_at,
                 declared_market_id, declared_filters jsonb,
                 item_count, coverage_score numeric, notes)

evidence_items(id, workspace_id, batch_id, source_kind,
               library_id null, library_url null,
               advertiser, page_name null,
               copy text[], headline null, cta null,
               platforms text[], active_status null,
               visible_start_date date null, visible_result_rank int null,
               observed_at, raw_input jsonb,
               provenance jsonb,        -- {field: provenance_kind} for EVERY field above
               created_at)

evidence_files(id, workspace_id, evidence_item_id, kind,
               storage_key, mime, bytes, sha256, phash null,
               declared_source_url null, captured_at,
               scan_status, scan_result jsonb, quarantined bool)

ads(id, workspace_id, market_id, competitor_id,
    library_id null, first_evidence_item_id, latest_evidence_item_id,
    advertiser, copy text[], headline, cta, platforms text[],
    active_status, visible_start_date, variant_count int,
    modality text,            -- full | screenshot | video | text_only | partial
    provenance jsonb, is_own_brand bool default false,
    first_observed_at, last_observed_at)

ad_analysis(id, ad_id, transcript, ocr_text, vision_description,
            hook_text, hook_type, format, angle, offer, cta,
            beats jsonb, modality, evidence_quality,
            anomaly jsonb null, embedding vector(1536), model, created_at)

ad_scores(id, ad_id, batch_id, market_id,
          duration_visible, platform_breadth, variant_repetition, recency,
          evidenced_rank numeric null, ebos numeric, coverage_score numeric,
          inputs jsonb, computed_at)

snapshots(id, workspace_id, search_reference_id, batch_id,
          captured_at, comparable_hash, item_count)
snapshot_diffs(id, workspace_id, from_snapshot_id, to_snapshot_id,
               comparable bool, comparability jsonb, result jsonb, created_at)

runs / run_steps / gates / briefs / scripts / frames / videos / provenance
    -- as before; runs.source_mode in ('browser_evidence','official_api','licensed')

licensed_sources(id, workspace_id, provider, contract_ref, permitted_use text,
                 retention_rights text, attribution_required text,
                 reviewed_by, reviewed_at, enabled bool default false)
```

Indexes: `evidence_items(batch_id)`, `ads(market_id)`, `ad_scores(batch_id, ebos desc)`,
HNSW on `ad_analysis.embedding`.

## 4. HTTP API

```
POST   /v1/brands
POST   /v1/runs                       {brand_id|name, market, objective, config}
GET    /v1/runs/{id}
GET    /v1/runs/{id}/discovery-plan   suggested search links (display only)
POST   /v1/runs/{id}/search-refs      persist a pasted Library URL (parse, no fetch)
POST   /v1/runs/{id}/batches          open an evidence batch
POST   /v1/batches/{id}/items         add an ad: url | copy | manual fields
POST   /v1/batches/{id}/files         upload screenshot / recording / media / CSV
POST   /v1/batches/{id}/close         triggers EVIDENCE_NORMALIZE + RANK
GET    /v1/runs/{id}/board            ranked evidence board + coverage
GET    /v1/ads/{id}/teardown
POST   /v1/runs/{id}/gate             {selected_ad_ids[], overrides{}, force:true}
GET    /v1/search-refs/{id}/snapshots
POST   /v1/search-refs/{id}/snapshots {batch_id}   -> creates comparison snapshot
GET    /v1/snapshots/{a}/diff/{b}
GET    /v1/runs/{id}/assets
POST   /v1/webhooks/video/{provider}
```

**There is no harvest endpoint.** If a route would cause the server to request a Meta
URL, it does not belong in this API.

## 5. Discovery plan (step 4)

Produces displayable search links, one per competitor × country × language × media
type, using the public Ad Library URL format the user already knows:

```
https://www.facebook.com/ads/library/?active_status=active&ad_type=all
  &country=AE&content_languages[0]=ar&media_type=all
  &q=<competitor>&search_type=keyword_unordered
```

Rules:
- **One link per country.** `country=ALL` collapses markets and makes duration and
  repetition signals meaningless; offer it only as an explicit "broad sweep" link the
  user chooses.
- Fan out to (country × language) — a brand in the UAE runs different creative in `en`
  and `ar`.
- Generate both advertiser-name and category-keyword links; the keyword links surface
  advertisers the competitor map missed.
- Emit the link **and** the human-readable filter summary, so the user can confirm the
  search matches the market they meant.
- The backend renders these. It does not open, prefetch, validate over the network, or
  follow them.

`MarketProfile` and the geo resolver are unchanged from the original spec: country
codes, languages, weights, currency, seasonality and compliance notes, ~20 presets plus
a custom builder. It now drives link generation instead of API queries.

## 6. Evidence normalize (step 6)

1. Parse each item into a normalised ad record, preserving per-field `provenance_kind`.
2. For uploaded files: SHA-256, perceptual hash for images and video first frames, OCR,
   ASR with word timestamps, vision description.
3. **Dedupe only on transparent evidence** — matching `library_id`, matching content
   hash, perceptual hash Hamming ≤ 8 on supplied files, or normalised copy cosine
   ≥ 0.92. Record which rule fired on every merge, and show it in the UI.
4. Collapsed duplicates set `variant_count`. This is repetition **within the submitted
   set** — it is not a claim about how many variants the advertiser is running.
5. Set `modality` per ad: `full | screenshot | video | text_only | partial`.

Never infer a field the evidence does not show. `unknown` is a valid, common, and
useful value.

## 7. Evidence-Backed Opportunity Score (`scoring/ebos.py`)

Replaces the old Proxy Performance Score. Computed per ad within an evidence batch —
**not within "the market"**, because the batch is what was actually observed.

Score only signals actually captured:

```
duration_visible   = ln(1 + days_since_visible_start) / ln(1 + p95(batch))   [0,1]
                     null when no start date was visible
platform_breadth   = |platforms observed| / 4                                [0,1]
variant_repetition = ln(1 + variant_count) / ln(1 + p95(batch))              [0,1]
recency            = exp(-days_since_observed_at / 45)                       [0,1]
evidenced_rank     = 1 - (visible_result_rank / batch_size)                  [0,1]
                     only when the user captured the Library result order
```

Components with no evidence are **dropped and the remaining weights renormalised** —
never zero-filled, which would silently punish an ad for what the user didn't capture.

| Component | weight |
|---|---|
| duration_visible | 0.30 |
| variant_repetition | 0.25 |
| evidenced_rank | 0.20 |
| recency | 0.15 |
| platform_breadth | 0.10 |

`ebos = round(100 * Σ(wᵢ·cᵢ) / Σ(wᵢ present), 1)`

### 7.1 Coverage score

```
coverage_score = mean(
    item_count / expected_min(=10),                      capped at 1
    fraction of items with a Library URL,
    fraction of items with a creative artefact (not text-only),
    fraction of items with a visible start date,
    fraction of competitors in the plan represented in this batch
)
```

Bands: `< 0.35` **thin**, `0.35–0.7` **partial**, `> 0.7` **substantial**. No band ever
means complete. `coverage_score` is stored on the batch and on every score row, and is
rendered on every card (`04 §5`).

### 7.2 Hard rules

- An `ebos` may never be presented without its `coverage_score`.
- Phrase results as **"highest opportunity score in this submitted evidence set"**.
  Never "the market's best ads", never "top performing".
- A batch below the thin threshold ranks but is labelled, and the board shows the
  coverage warning prominently rather than in a tooltip.
- Persist every input in `ad_scores.inputs`. A score the user cannot audit is a score
  they will not believe, and here it is also a score they cannot verify against their
  own eyes.

Clustering by concept (embedding over hook + angle + offer) still applies, so one
advertiser's repeated creative doesn't own the board.

## 8. Human gate (step 9) — unchanged and still mandatory

`runs.status = 'AWAITING_GATE'`; the worker exits cleanly. `POST /v1/runs/{id}/gate`
carries `selected_ad_ids`, creative `overrides`, and `force`.

`force:true` proceeds past **warnings**. It never bypasses a **block** — similarity
over threshold, third-party IP, unsubstantiated claim, or regulated-category violation
(`03 §10`).

## 9. Generation (steps 10–15)

Unchanged from the original spec and independent of source mode: angle transfer →
script (`script-writer`) → first frame (`nano-banana-prompter`) → motion
(`seedance-2-prompter`) → post + gates → deliver. See `05-SKILL-INTEGRATION.md` and
`09-CREATIVE-MATRIX.md`.

The generation half never learns which source mode produced the evidence. That
separation is what lets an official API or licensed provider be enabled later without
touching analysis, provenance, safety or generation.

## 10. Ops

- Per-run cost ceiling in `runs.config.max_cost_cents`.
- Structured JSON logs with `run_id`/`step`/`attempt`; never log a Library URL's query
  string wholesale, and never log uploaded file contents.
- OpenTelemetry spans per step.
- Retention: competitor evidence binaries default to 180 days, then delete the files
  and keep derived analysis. Configurable, documented, enforced by a job.

## 11. Definition of done

- [ ] A run reaches `EVIDENCE_INTAKE` unattended with ≥3 verified competitors and a
      displayed discovery plan of per-country search links.
- [ ] No code path issues a network request to a facebook.com URL. Proven by test.
- [ ] 12 submitted ads normalise, dedupe with a recorded reason per merge, and rank
      with a coverage score.
- [ ] Every field on a board card resolves to a `provenance_kind`.
- [ ] Text-only evidence completes the pipeline end to end.
- [ ] Gate -> three delivered variants + test plan in one unattended pass.
- [ ] The similarity gate demonstrably blocks a near-verbatim script.
- [ ] A licensed provider cannot be enabled without a recorded contract review.
