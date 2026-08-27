# 01 — BACKEND SPEC

Read `00-MASTER-BRIEF.md` first. Build exactly this. Where it says *decide*, decide
and write it down in `docs/decisions/`.

> **Overridden by `06-SUPABASE-AND-SUPERMETRICS.md`:** §1 (layout), §2 (schema — every
> table gains `workspace_id` + RLS) and §3's SSE endpoint (replaced by Supabase
> Realtime). §4–§11 stand as written. Read 06 before starting.

## 1. Layout

```
backend/
  app/
    api/            FastAPI routers
    core/           config, auth, logging, errors
    db/             SQLAlchemy models, alembic migrations
    adapters/
      adsource/     base.py, meta_graph.py, thirdparty.py, snapshot_render.py
      image/        base.py, imagine_art.py, gemini.py
      video/        base.py, imagine_art.py, modelark.py
      asr/          base.py, whisper.py
    agents/         one module per pipeline agent; loads prompts/ + skills
    prompts/        VERBATIM copies of 02-AGENT-PROMPTS.md
    pipeline/       steps/, orchestrator.py, state.py, events.py
    scoring/        pps.py, clustering.py, dedupe.py
    geo/            market_profiles.py, resolver.py
    workers/        arq worker defs
  tests/
```

## 2. Domain model (Postgres)

```sql
brands(id, name, website, dossier jsonb, palette jsonb, voice jsonb,
       assets jsonb, created_at)

markets(id, brand_id, label, country_codes text[], languages text[],
        metric_tier char(1), currency, profile jsonb)

competitors(id, brand_id, market_id, name, domain, fb_page_ids text[],
            tier smallint, rationale text, evidence jsonb, verified bool)

ads(id, library_id unique, page_id, page_name, competitor_id, market_id,
    ad_creation_time, delivery_start, delivery_stop,
    creative_bodies text[], link_titles text[], link_captions text[],
    link_descriptions text[], snapshot_url, publisher_platforms text[],
    languages text[], media_type,
    eu_total_reach bigint null, reach_breakdown jsonb null,
    target_ages jsonb null, target_gender text null, target_locations jsonb null,
    raw jsonb, first_seen_at, last_seen_at)

ad_assets(id, ad_id, kind, storage_key, width, height, duration_s,
          sha256, phash, bytes)

ad_analysis(id, ad_id, transcript, ocr_text, vision_description,
            hook_text, hook_type, format, angle, offer, cta,
            beats jsonb, embedding vector(1536), model, created_at)

ad_scores(id, ad_id, market_id, longevity, scale, breadth, recency,
          reach_pct, iteration, pps numeric, confidence char(1),
          inputs jsonb, computed_at)

ad_clusters(id, market_id, label, concept_summary, centroid vector(1536),
            member_ad_ids bigint[])

runs(id, brand_id, market_id, status, current_step, config jsonb,
     cost_cents, created_at, updated_at)

run_steps(id, run_id, step, status, attempt, input_hash, output jsonb,
          error jsonb, started_at, ended_at, tokens_in, tokens_out, cost_cents)

gates(id, run_id, kind, payload jsonb, decision jsonb, decided_at, decided_by)

briefs(id, run_id, source_ad_ids bigint[], angle jsonb, guardrails jsonb)
scripts(id, brief_id, hook, beats jsonb, vo, on_screen_text jsonb, cta,
        duration_s, aspect, skill_version, raw jsonb)
frames(id, script_id, prompt, provider, model, image_key, qa jsonb, accepted bool)
videos(id, script_id, frame_id, prompt, provider, model, provider_task_id,
       seed, status, video_key, duration_s, aspect, audio jsonb)
provenance(id, video_id, source_ad_ids bigint[], similarity jsonb, c2pa jsonb)
```

Indexes: `ads(market_id, delivery_start desc)`, `ads(page_id)`,
`ad_scores(market_id, pps desc)`, ivfflat on `ad_analysis.embedding`.

## 3. HTTP API

```
POST   /v1/brands                     {name, website?}                -> brand
POST   /v1/runs                       {brand_id|name, market, objective, config}
GET    /v1/runs/{id}                  full run state
GET    /v1/runs/{id}/events           SSE: step transitions + partial payloads
GET    /v1/runs/{id}/competitors
GET    /v1/runs/{id}/leaderboard      ?tier=&format=&cluster=  ranked ads + scores
GET    /v1/ads/{id}/teardown          analysis + assets + score breakdown
POST   /v1/runs/{id}/gate             {selected_ad_ids[], overrides{}, force:true}
POST   /v1/runs/{id}/steps/{step}/retry
GET    /v1/runs/{id}/assets
POST   /v1/webhooks/video/{provider}  async completion callback
```

SSE event envelope:
```json
{"run_id":"...","seq":41,"step":"ADS_HARVEST","status":"running",
 "progress":{"done":118,"total":300},"message":"Nike / AE / en — page 3",
 "payload":{}, "ts":"..."}
```

## 4. Meta Ad Library client (`adapters/adsource/meta_graph.py`)

Endpoint: `GET https://graph.facebook.com/v23.0/ads_archive`

Auth: user access token from an app with Ad Library API access; the token owner must
have completed identity confirmation. Store per-workspace, refresh on 190.

**Request params to support**

| Param | Notes |
|---|---|
| `ad_reached_countries` | **required**. ISO-3166-1 alpha-2 array, or `ALL`. |
| `search_terms` | max 100 chars. |
| `search_type` | `KEYWORD_UNORDERED` (default) \| `KEYWORD_EXACT_PHRASE` |
| `search_page_ids` | up to **10** page IDs per call — chunk larger sets |
| `ad_type` | `ALL` for commercial work |
| `ad_active_status` | `ACTIVE` \| `INACTIVE` \| `ALL` |
| `ad_delivery_date_min/max` | `YYYY-MM-DD` |
| `media_type` | `ALL\|IMAGE\|MEME\|VIDEO\|NONE` |
| `publisher_platforms` | `FACEBOOK, INSTAGRAM, AUDIENCE_NETWORK, MESSENGER, WHATSAPP, OCULUS, THREADS, STREAMING_SERVICES` |
| `languages` | ISO 639-1 array |
| `fields` | comma-joined; request only commercial-legal fields (see below) |
| `limit`, `after` | cursor pagination via `paging.cursors.after` |

**Field set for `ad_type=ALL`** — request exactly these, nothing more:
```
id,ad_creation_time,ad_creative_bodies,ad_creative_link_captions,
ad_creative_link_descriptions,ad_creative_link_titles,ad_delivery_start_time,
ad_delivery_stop_time,ad_snapshot_url,page_id,page_name,publisher_platforms,
languages,eu_total_reach,age_country_gender_reach_breakdown,target_ages,
target_gender,target_locations,beneficiary_payers,total_reach_by_location
```
The EU/DSA fields return null outside the EU/UK. That is expected — it drives the
confidence tier, it is not an error.

Never request `impressions`, `spend`, `demographic_distribution`,
`delivery_by_region`, `estimated_audience_size`, `currency` or `bylines` on
`ad_type=ALL`. They are political-ads-only and will error or return empty.

**Resilience**
- Respect `X-Business-Use-Case-Usage` / `X-App-Usage`; back off when
  `call_count`/`total_cputime` > 80.
- Error 613 / 4 / 17 => exponential backoff with jitter, cap 5 retries.
- Error 190 => surface a re-auth event to the frontend, pause the run, do not fail it.
- Persist every raw page response to `runs/{id}/raw/{hash}.json` in object storage for
  replay and audit.
- Hard budget per run: `config.max_ads` (default 600) and `config.max_api_calls`
  (default 400). Log and surface when a cap truncates results — never truncate silently.

## 5. Geography resolver (`geo/`) — this is a headline feature, treat it as one

A `MarketProfile` is the unit of targeting:

```python
MarketProfile(
  id="gcc-en-ar",
  label="Gulf (UAE, KSA, KW, QA, BH, OM)",
  country_codes=["AE","SA","KW","QA","BH","OM"],
  languages=["en","ar"],
  metric_tier="B",              # non-EU -> no reach data
  currency="AED",
  weights={"AE":0.35,"SA":0.40,"KW":0.07,"QA":0.08,"BH":0.04,"OM":0.06},
  platform_hint={"INSTAGRAM":0.55,"FACEBOOK":0.35},
  notes=["Ramadan/Eid seasonality","Arabic RTL copy","local ad content rules"],
)
```

Rules the resolver must enforce:

1. **Never score off `ad_reached_countries=["ALL"]`.** `ALL` is legal in the API and
   fine for a first discovery sweep, but it collapses distinct markets into one bucket
   and makes longevity and variant counts meaningless. Scoring queries are always
   per-country.
2. **Fan out to (country × language).** A brand in the UAE runs different creative in
   `en` and `ar`. One query per pair; aggregate afterwards with `weights`.
3. **Tier is derived from geography, not configured.** EU-27 + UK => tier A (reach
   published under the DSA). Everything else => tier B. Cohorts with <3 ads or <14
   days of history => tier C regardless.
4. **Aggregation across countries is weighted, and the weights are shown in the UI.**
   An ad live in all six GCC states outscores one live only in Bahrain, and the user
   can see why.
5. Ship ~20 preset profiles (US, UK, EU-DACH, EU-FR, EU-NORDICS, GCC, SEA, IN, BR,
   MX, AU, JP, KR, TR, ZA, NG, PK, ID, CA, global-en) plus a custom builder.

`QUERY_PLAN` output is an explicit, inspectable list of API calls:

```json
{"queries":[
 {"country":"AE","language":"en","search_page_ids":["1234","5678"],
  "media_type":"ALL","ad_active_status":"ACTIVE","est_calls":6},
 {"country":"AE","language":"ar","search_terms":"skincare serum","est_calls":4}
]}
```
The frontend renders this before execution. That is the "searches correctly based on
the geography" promise made visible.

## 6. Creative ingest (`CREATIVE_INGEST`)

For each shortlisted ad:
1. Resolve media. If `SNAPSHOT_RENDER_ENABLED=false`, run **text-only mode**: teardown
   from `ad_creative_bodies` + `link_titles` + `link_descriptions` alone, and mark the
   analysis `modality: "text_only"`. The app must be genuinely useful in this mode.
2. If enabled: fetch media, store to S3, compute `sha256` + perceptual hash.
3. Video => ASR transcript (word timestamps), keyframe extraction at scene cuts,
   OCR each keyframe for on-screen text.
4. Image => OCR + vision description.
5. Embed `hook_text + angle + offer` with a text embedding model into
   `ad_analysis.embedding`.

Dedupe: two ads are the *same creative* if image phash Hamming ≤ 8, or video first-
frame phash ≤ 8 and transcript cosine ≥ 0.95, or (text-only mode) normalised body
cosine ≥ 0.92. Same-creative ads collapse into one row with `variant_count = n`.
**That collapse is the single most valuable signal in the system** — an advertiser
running one creative across 40 ad IDs is telling you it wins.

## 7. Proxy Performance Score (`scoring/pps.py`)

Computed per ad, within a cohort = (competitor × market).

```
days_live    = clamp((min(stop_time, now) - start_time).days, 1, 730)
longevity    = ln(1 + days_live) / ln(1 + p95(days_live | cohort))          [0,1]
scale        = ln(1 + variant_count) / ln(1 + p95(variant_count | cohort))  [0,1]
breadth      = |publisher_platforms ∩ {FB,IG,AN,MSGR}| / 4                  [0,1]
recency      = exp(-days_since_start / 45)                                  [0,1]
iteration    = ln(1 + distinct_creative_bodies_same_concept) / ln(1 + p95)  [0,1]
reach_pct    = percentile_rank(eu_total_reach | cohort)   # tier A only, else null
```

Weights:

| Component | Tier A (EU/UK) | Tier B (rest) |
|---|---|---|
| reach_pct | 0.35 | — |
| longevity | 0.25 | 0.35 |
| scale | 0.15 | 0.28 |
| iteration | 0.07 | 0.14 |
| recency | 0.10 | 0.13 |
| breadth | 0.08 | 0.10 |

`pps = round(100 * Σ(w_i · c_i), 1)`. Tier C ads get `pps = null` and a
`status: "emerging"` flag.

Guards:
- Cohort with n < 5 => widen to (market) level for percentile bases, and drop
  `confidence` one tier.
- An ad live > 365 days with `variant_count = 1` and no recent siblings is an
  **evergreen/abandoned** case — down-weight `longevity` by 0.5 and tag it.
- Persist every input in `ad_scores.inputs` so the UI can show the full derivation.
  Any score the user can't audit is a score they won't believe.

Clustering: HDBSCAN (or k-means with silhouette selection) over `ad_analysis.embedding`
within a market. Each cluster gets an LLM-written `concept_summary`. The leaderboard
shows **top ad per cluster**, not the top 20 ads — otherwise one competitor's 40
variants of one idea own the whole board.

## 8. Human gate (step 9)

`runs.status = 'AWAITING_GATE'`; the worker exits cleanly (does not block a slot).
`POST /v1/runs/{id}/gate` with:

```json
{"selected_ad_ids":[9911,9925],
 "overrides":{"aspect":"9:16","duration_s":12,"tone":"confident, dry",
              "must_include":["free returns"],"must_avoid":["price claims"],
              "offer":"20% off first order"},
 "force":true}
```

`force:true` proceeds even when the QA/brand-safety judge in step 14 flags a
**warning**. It never bypasses a **block** (similarity gate over threshold, or a
prohibited-claim finding). Warnings vs blocks are enumerated in `02-AGENT-PROMPTS.md §10`.

Gate decisions are persisted and replayable: re-running from the gate with a different
selection must not re-harvest.

## 9. Generation stages (10–15)

Run inside a Claude Agent SDK session with the user's skills mounted — see
`04-SKILL-REFERENCES.md`. Sequence per selected source ad:

1. **ANGLE_TRANSFER** -> `briefs` row.
2. **SCRIPT** -> `script-writer` skill -> `scripts` row. Validate: hook ≤ 3s of
   speech, total VO within `duration_s`, on-screen text ≤ 6 words per card.
3. **FIRST_FRAME** -> `nano-banana-prompter` skill produces the image prompt ->
   image adapter renders -> vision QA loop (max 2 corrections) against a checklist:
   product accuracy, text legibility, brand palette, no artefacts, aspect correct.
4. **MOTION** -> `seedance-2-prompter` skill produces an image-to-video prompt that
   binds the accepted frame (`@Image` reference) -> video adapter submits ->
   poll or webhook -> download to S3. Capture and persist the `seed`.
5. **POST** -> aspect variants (9:16 master, 1:1, 16:9), burned captions from the
   script's own timing, thumbnail, then the similarity + brand-safety gate.
6. **DELIVER** -> bundle + `provenance` row linking back to `source_ad_ids`.

Every generation stage stores its exact prompt. Reproducibility is the point.

## 10. Cost, limits, ops

- Per-run cost ceiling in `runs.config.max_cost_cents`; stop and gate when hit.
- Structured JSON logs with `run_id`/`step`/`attempt` on every line.
- OpenTelemetry spans per step; count Meta API calls as a first-class metric.
- Cache Ad Library responses 6h keyed on the full normalised query.
- `GET /healthz` checks Postgres, Redis, and one cheap Meta call against a known page.
- Secrets via env only. Never log tokens or `ad_snapshot_url` query strings.

## 11. Definition of done

- [ ] `POST /v1/runs` with `{name:"Higgsfield", market:"US"}` reaches `AWAITING_GATE`
      unattended, with ≥3 verified competitors and ≥40 scored ads.
- [ ] Every leaderboard number traces to `ad_scores.inputs` via the teardown endpoint.
- [ ] Killing the worker mid-harvest and restarting resumes without duplicate ads.
- [ ] Gate -> delivered MP4 with audio, correct aspect, in one unattended pass.
- [ ] Text-only mode (`SNAPSHOT_RENDER_ENABLED=false`) completes end to end.
- [ ] Similarity gate demonstrably blocks a near-verbatim script in a test.
