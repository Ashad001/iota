# 03 — FRONTEND SPEC

Read `00-MASTER-BRIEF.md` first.

Next.js 15 App Router, TypeScript strict, Tailwind, shadcn/ui, TanStack Query,
SSE via `EventSource` for the run stream, Zustand for gate-selection state only.

The frontend has one job beyond looking good: **make the machine's reasoning
inspectable**, so the user can decide whether to force generation with real
information rather than vibes.

## 1. Screens

### S1 — Intake  `/new`
Three fields, nothing else:
- Brand name (required) — free text, autocompletes against previous runs.
- Website (optional) — improves dossier confidence; show that as a hint.
- Target market — searchable select over the preset `MarketProfile`s, plus
  "Build custom" (multi-select countries + languages).
- Objective — chips: Sales · Leads · App installs · Awareness.
- Advanced (collapsed): ad count cap, cost ceiling, media type, active/inactive,
  lookback window.

On submit `POST /v1/runs` and route to S2. If the brand researcher returns
`disambiguation_needed`, show a modal with the candidates — this is the only
interruption before the gate.

### S2 — Research Console  `/runs/[id]`
Live, streaming, left-rail step tracker: the 15 pipeline steps with status,
elapsed time, and a running cost counter.

The main panel swaps as steps complete:
- **BRAND_RESEARCH** -> Dossier card: positioning, ICP chips, voice sample, palette
  swatches, proof points each linking to its source URL.
- **COMPETITOR_MAP** -> competitor grid, grouped DIRECT / ADJACENT / ATTENTION, each
  with `why_useful` and a confidence bar. Every card has a **Remove** toggle — the
  user can prune before harvest, and pruning re-runs only QUERY_PLAN onwards.
- **QUERY_PLAN** -> render the query table. This is the geography feature made
  visible: `Country · Language · Pages · Terms · Est. calls`, with the total, the
  `coverage_note`, and anything in `dropped` shown in amber. Make it beautiful; it is
  the moment the user believes the app is targeting correctly.
- **ADS_HARVEST / CREATIVE_INGEST** -> a live-filling grid of ad thumbnails with a
  per-country progress bar.

### S3 — Ad Leaderboard  `/runs/[id]/board`
The centrepiece. One card per **concept cluster**, expandable to its variants —
never a flat list, or one advertiser's 40 variants own the board.

Each card shows:
- Creative thumbnail (or, in text-only mode, a typographic rendering of the ad copy —
  make this deliberate and good-looking, not an empty state).
- Advertiser, tier badge, country flags where it runs.
- **PPS** as a 0–100 ring with the confidence letter (A/B/C) inside it.
- Four metric chips, each with its provenance badge:
  - `Live 94 days` — INFERRED
  - `23 variants` — INFERRED
  - `FB · IG · AN` — MEASURED
  - `EU reach 1.2M` — MEASURED (tier A only; absent otherwise, never zero-filled)
- The `evidence_line` from the score auditor, verbatim.
- Hook type + format tags.
- A checkbox: **Use this angle**.

Controls: filter by tier / format / hook type / country / active-only. Sort by PPS,
longevity, variants, recency. A prominent **"Why this ranking?"** button opening the
`blind_spots` paragraph.

Tier C ads appear in a separate **Emerging** strip at the bottom, unranked, labelled
"too new to score".

### S4 — Teardown Drawer
Opens over the board on card click.
- Left: media player (or copy card), with the transcript scrubbing in sync and OCR
  text overlaid at its timestamps.
- Right: the structural teardown — hook / angle / objection / beat timeline / offer /
  CTA / proof / production complexity.
- Bottom: **Score derivation** — an expandable table of every PPS input, its raw
  value, its normalised value, its weight, and its contribution. Nothing hidden.
- Footer: `Use this angle` + `Compare` (side-by-side of up to 3 ads).

### S5 — The Gate  `/runs/[id]/gate`
Unlocks once ≥1 ad is selected. A summary sheet:
- The selected ads, and for each, a one-line preview of the reanchored angle
  AdMirror intends to build (from a cheap pre-pass of the angle strategist).
- Overrides: aspect, duration, tone, must-include, must-avoid, offer text.
- Estimated cost and time for the generation run.
- A single primary button: **Force Generation**.
- Under it, plain text: what `force` does and does not override — it proceeds past
  warnings, never past blocks. Do not bury this in a tooltip.

### S6 — Generation Timeline  `/runs/[id]/generate`
Vertical timeline, one node per stage, each expanding to show the real artifact:
- **Angle transfer** -> the brief, with `divergence_note` called out.
- **Script** -> the three hook variants, the beat table with timings, word count vs
  duration budget as a bar.
- **First frame** -> the rendered image, the prompt used, and each QA loop iteration
  with its failures. Show the retries; they are the most interesting part.
- **Motion** -> the shot list, the Seedance prompt per shot, task status, then the
  clip.
- **QA** -> findings by severity with the similarity report.
- **Deliver** -> the player, aspect variants, download bundle, prompt export.

### S7 — Library  `/library`
All runs, all generated assets, filterable by brand and market. Each asset links back
to its source ads through the provenance record — one click from a finished video to
the competitor ad whose angle it inherited.

## 2. Streaming

Subscribe to `/v1/runs/{id}/events`. Reduce events into a normalised run store keyed
by `seq`; on reconnect, `GET /v1/runs/{id}` to resync, then resume from `last_seq`.
Never render from the SSE stream alone — it can drop.

Show meaningful messages, not spinners. `"Nike / AE / ar — page 3 of ~7"` beats
"Loading…" every time. The step tracker keeps the user oriented during a run that
legitimately takes several minutes.

## 3. Gate state

Selection lives in Zustand, persisted to `sessionStorage` per run so a refresh at the
board does not lose picks. It is submitted once, to `POST /v1/runs/{id}/gate`.

## 4. Empty and failure states worth building properly

- **No active ads for this competitor in this country.** Say exactly that, and offer
  a one-click widen: neighbouring countries, or include inactive ads from the last
  180 days.
- **Re-auth required** (Meta error 190). The run pauses, does not die. Banner with a
  reconnect action; resume from the paused step.
- **Cap hit.** "Stopped at 600 ads (your cap). 4 competitors partially harvested."
  Name which ones. Offer to raise the cap and continue.
- **Text-only mode.** A persistent, calm banner explaining that media rendering is
  disabled and teardowns are copy-based. Not an error — a mode.

## 5. Metric honesty in the UI (enforced, not aspirational)

Implement a single `<Metric>` component. It takes `value`, `label`, and a required
`provenance: 'MEASURED' | 'INFERRED' | 'MODELLED'` prop. There is no default.

- `MEASURED` — solid badge. Came from Meta's API verbatim.
- `INFERRED` — outline badge. Computed by our scoring from Meta data.
- `MODELLED` — dashed badge. An LLM's judgement.

Rules:
- Every number displayed anywhere in the app renders through `<Metric>`. Add an ESLint
  rule or a test that fails on raw numeric metric rendering in card components.
- The words "impressions", "spend", "CTR", "ROAS" and "views" must not appear in the
  UI in reference to a commercial ad. There is no such data. A grep test in CI is
  cheap and worth it.
- Hovering any INFERRED badge shows the formula and the inputs for that specific ad.
- The PPS ring always shows its confidence letter. A score with no confidence letter
  is a bug.

## 6. Design direction

Dense, dark, instrument-panel — this is a tool for someone who reads ad accounts all
day, not a landing page. Type-led hierarchy, one accent colour used only for the
things the user acts on (Use this angle, Force Generation). Creative thumbnails are
the only saturated colour on the board; everything else recedes so the ads pop.

Motion only where it carries information: the streaming step tracker, the PPS ring
counting up as scores land, the timeline advancing. No decorative animation.

Full keyboard path through the board: `j/k` move, `space` select, `enter` open
teardown, `g` gate.

## 7. Definition of done

- [ ] Intake -> gate with no page reload and no lost events across a reconnect.
- [ ] Every leaderboard number carries a provenance badge; CI grep test passes.
- [ ] Score derivation table matches `ad_scores.inputs` exactly.
- [ ] Query plan table renders before harvest and shows drops.
- [ ] Gate selection survives a refresh.
- [ ] Generation timeline shows real prompts and real QA retries, not summaries.
