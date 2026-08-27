# 00 — MASTER BRIEF (give this to every agent, first)

You are building **AdMirror**, a competitive-creative engine for paid social.

## 1. The user story

> I type my brand name and the country I sell in. AdMirror figures out who I am,
> figures out who I'm up against, pulls their live Meta ads for *that* geography,
> ranks which of those ads are actually working, and shows me the evidence for each
> one. I read the teardowns, tick the two I want, and press **Force Generation**.
> AdMirror then writes the script, renders the opening frame, and generates a
> finished video ad — mine, in my voice, built on the same winning angle. I did not
> write a prompt at any point.

## 2. The pipeline (this is the app)

A durable, resumable state machine. Every step writes a `run_steps` row and streams
an event to the frontend. Any step can be retried in isolation.

```
 1  INTAKE              brand name, website (optional), target market, objective
 2  BRAND_RESEARCH      web research -> Brand Dossier
 3  COMPETITOR_MAP      derive + verify competitor set for THIS market
 4  QUERY_PLAN          geo/language decomposition into concrete Ad Library queries
 5  ADS_HARVEST         paginate Meta Ad Library, normalise, dedupe
 6  CREATIVE_INGEST     pull media, transcribe, OCR, vision-describe, hash
 7  SCORE               Proxy Performance Score + confidence tier + concept clustering
 8  TEARDOWN            per top-ad structural analysis (hook / angle / offer / CTA)
--- 9  HUMAN_GATE  <<<  user reviews metrics, selects winners, presses Force Generation
10  ANGLE_TRANSFER      winning ad -> brand-safe creative brief (angle, not asset)
11  SCRIPT              script-writer skill -> hook + beats + VO + on-screen text
12  FIRST_FRAME         nano-banana-prompter skill -> image prompt -> render -> QA loop
13  MOTION              seedance-2-prompter skill -> I2V prompt -> Seedance -> poll
14  POST                aspect variants, captions, thumbnail, brand+safety check
15  DELIVER             asset bundle + provenance record
```

Extended by later files: `05` adds phase 0 (SELF_HARVEST) and phases 16–18
(PUBLISH / MEASURE / LEARN). `07` adds continuous observation feeding steps 5–7.
`08` fans step 13 out into a creative matrix plus a test plan.

Steps 1–8 run unattended. Step 9 blocks. Steps 10–15 run unattended.
"Without your interference" means **no prompt writing by the user, ever** — the only
human input in the whole system is the intake form and the gate decision.

## 3. Hard architectural rules

1. **Durable over clever.** Every step is idempotent and keyed by
   `(run_id, step, input_hash)`. A crash at step 13 must not re-run steps 1–12.
2. **The LLM never touches raw HTTP.** All Meta / provider calls go through typed
   adapters. Agents receive normalised objects and return structured JSON.
3. **Every agent call is schema-validated on the way out.** Use tool-call forced
   structured output. A free-text answer where an object was expected is a failure,
   not something to parse with a regex.
4. **Skills are loaded, not paraphrased.** The generation stages run through the
   Claude Agent SDK with the user's own skills mounted (see `04-SKILL-REFERENCES.md`).
   Do not reimplement `seedance-2-prompter`'s grammar in Python. Load the skill.
5. **Provenance is a first-class table.** Every generated asset records which source
   ad IDs informed it and what the similarity check returned.

## 4. The metric-honesty rule (non-negotiable)

The Meta Ad Library API (`GET /{version}/ads_archive`) returns `impressions`, `spend`,
`demographic_distribution`, `delivery_by_region` and `estimated_audience_size`
**only for `ad_type=POLITICAL_AND_ISSUE_ADS`**. For ordinary commercial ads you get:

- `id`, `page_id`, `page_name`
- `ad_creation_time`, `ad_delivery_start_time`, `ad_delivery_stop_time`
- `ad_creative_bodies[]`, `ad_creative_link_titles[]`, `ad_creative_link_captions[]`,
  `ad_creative_link_descriptions[]`
- `ad_snapshot_url`, `publisher_platforms[]`, `languages[]`
- EU/UK only, under the DSA: `eu_total_reach`, `age_country_gender_reach_breakdown`,
  `target_ages`, `target_gender`, `target_locations`, `beneficiary_payers`,
  `total_reach_by_location`

Therefore:

- There is **no impression count** for a commercial ad outside the EU/UK. The
  `sort_data[mode]=total_impressions` parameter in the public web UI is a UI-side
  sort, not an API field. Do not promise it, do not scrape a number for it, do not
  invent one.
- Ranking is done by a **Proxy Performance Score (PPS)** built from longevity,
  variant scale, platform breadth, recency, iteration depth and — where legally
  published — EU reach. Full definition in `01-BACKEND.md §7`.
- Every number in the UI carries a provenance badge: `MEASURED` (came from Meta),
  `INFERRED` (computed by us), or `MODELLED` (LLM judgement). See `03-FRONTEND.md §5`.
- Confidence tiers: **A** = EU/UK market with reach data. **B** = non-EU, proxy-only.
  **C** = insufficient history (<14 days or <3 ads in cohort) — shown as "Emerging",
  never ranked against A/B.

Getting this right is the difference between a tool a media buyer trusts and a toy.

## 5. The "copy" rule

The product promise is "copies their best ad in your brand's iteration". Build it as
**angle transfer, not asset transfer**:

- **Transfer:** the hook mechanism, the persuasion angle, the objection handled, the
  format/pacing, the offer structure, the CTA shape, the emotional beat order.
- **Do not transfer:** their footage, their voiceover audio, their music, their
  talent's likeness, their logo, their registered trademarks, their slogan verbatim,
  or their distinctive trade dress.
- Step 14 runs a **similarity gate**: generated script vs source ad copy must be
  below a configured n-gram overlap threshold (default: no shared 7-gram, cosine on
  embeddings < 0.88). Over threshold => regenerate with a divergence instruction,
  max 2 retries, then surface to the user.

This is not a legal opinion; it is a product spec. Ship the gate.

## 6. Data-access posture

- **Primary path:** official Ad Library API. It requires an app with Ad Library API
  access and an identity-confirmed user token. Build for this first.
- **Adapter path:** the codebase exposes `AdSourceAdapter`; third-party providers
  (Apify, ScrapeCreators, etc.) can be dropped in behind the same interface for
  markets or fields the official API doesn't cover.
- **Snapshot media:** `ad_snapshot_url` renders the actual creative. Fetching media
  from it programmatically is outside the documented API surface and is governed by
  Meta's terms. Put it behind `SNAPSHOT_RENDER_ENABLED` (default `false`), document
  the tradeoff in the README, and make the app fully functional without it (text-only
  teardown mode).

Surface this choice to the operator. Do not silently scrape.

## 7. Stack

- **Data plane:** **Supabase** — Postgres 16 + pgvector, Auth, Storage, Realtime,
  `pg_cron`, Edge Functions. RLS multi-tenancy from day one. See `06`.
- **Control plane:** Python 3.12, FastAPI, ARQ workers, Redis. The agent pipeline runs
  here, not in Edge Functions.
- **Owned-media measurement:** **Supermetrics** (Meta/TikTok/Google Ads insights).
  Owned accounts only — never competitor data. See `06` Part B.
- **Agents:** Claude Agent SDK (`claude-agent-sdk`), model `claude-opus-5` for
  strategy/teardown, `claude-sonnet-5` for high-volume normalisation and extraction.
- **Frontend:** Next.js 15 (App Router), TypeScript, Tailwind, shadcn/ui,
  TanStack Query, SSE for the run stream.
- **Media:** provider-adapter pattern. First-class adapters for **imagine.art**
  (the operator's own platform), BytePlus ModelArk (Seedance 2.0), and Google
  Gemini image (Nano Banana). Never hard-code one vendor.
