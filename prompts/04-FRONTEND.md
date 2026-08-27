# 04 — FRONTEND SPEC

Read `01-MASTER-BRIEF.md` first.

Next.js 15 App Router, TypeScript strict, Tailwind, shadcn/ui, TanStack Query, Supabase
Realtime, Zustand for gate-selection state only.

The frontend has two jobs beyond looking good:

1. **Make evidence capture fast enough that people actually do it.** In Browser
   Evidence Mode the user is the collection mechanism. Every extra click is evidence
   that never gets submitted, and a thin board is a useless board.
2. **Make the machine's reasoning and its limits inspectable**, so the user decides
   whether to force generation knowing exactly what the board does and does not cover.

## 1. Screens

### S1 — Intake `/new`
Brand name (required), website (optional, improves dossier confidence), target market
(searchable preset `MarketProfile`s + custom builder), objective chips. Advanced:
cost ceiling, media type, lookback.

Show the source mode plainly: *"AdMirror doesn't pull from Meta automatically. You'll
search the public Ad Library yourself and submit what you find — usually 10–20 minutes
for a market."* Setting the expectation here is what stops the board from disappointing
later.

### S2 — Research Console `/runs/[id]`
Left-rail step tracker over the 15 pipeline steps, with status, elapsed time and a
running cost counter. Main panel swaps as steps complete:

- **BRAND_RESEARCH** → Dossier card: positioning, ICP chips, voice sample, palette
  swatches, proof points each linking to its source URL.
- **COMPETITOR_MAP** → grid grouped DIRECT / ADJACENT / ATTENTION, each with
  `why_useful` and a confidence bar. **Remove** toggles let the user prune before the
  discovery plan is built.
- **DISCOVERY_PLAN** → the search table (§2). This is the handoff moment.

### S3 — Collect Evidence `/runs/[id]/collect`  ← the centre of gravity in v1

**A. Saved searches.** The discovery plan rendered as a table:
`Competitor · Country · Language · Media type · Filters` with a prominent **Open in
Meta Ad Library ↗** button per row (`target="_blank" rel="noopener noreferrer"`).
Each row shows the human-readable filter summary so the user can confirm the search
matches the market they meant.

The user may also **paste their own Ad Library search URL**. Parse it, display the
parsed filter context back to them, save it as a `search_reference`, and show the same
Open button. Make clear that AdMirror stores the link and the filters — it does not
visit the link.

**B. Submit evidence.** An open batch, tied to a search reference, accepting:

- **Ad Library URL** — paste one or many, newline-separated.
- **Copy/paste** — paste ad text directly.
- **Screenshot** — paste from clipboard (`Ctrl/⌘+V` anywhere on the page) or drop.
- **Screen recording** / uploaded image / video.
- **Manual fields** — advertiser, headline, CTA, platforms, active status, visible
  start date, visible result position.

Clipboard paste is the single highest-leverage interaction on this screen. Someone
alt-tabbing between the Library and AdMirror will paste dozens of screenshots if it
takes one keystroke, and will submit four ads if it takes a file dialog.

**C. Capture checklist.** Per item, a compact row of fields — advertiser, Library URL,
observed date/time, market, language, active status, visible start date, platform(s),
creative/copy — each toggling between `observed`, `user asserted`, and `unknown`.
Default to `unknown`; never pre-fill a guess into a field the user will click past.

**D. Live coverage meter.** A persistent panel: item count, coverage score and band,
competitors represented vs planned, and the specific gap — *"No evidence yet for
Competitor C; 6 of 14 items have no visible start date."* Tell the user what to go get
next. This turns coverage from a scolding into a checklist.

**E. Close batch** → runs EVIDENCE_NORMALIZE + EVIDENCE_RANK.

### S4 — Evidence Board `/runs/[id]/board`
One card per concept cluster, expandable to variants.

Header, always visible and not dismissible:

> **This board reflects the ads you submitted, not a complete Meta inventory.**
> Evidence set "GCC — August" · 14 ads · captured 27 Aug 2026 · coverage **partial (0.52)**

Each card shows:
- Creative thumbnail, or — for text-only items — a deliberate typographic rendering of
  the ad copy. Design this properly; in v1 it will be common, and an empty grey box
  makes good evidence look like missing evidence.
- Advertiser, market, `modality` badge (`full` / `screenshot` / `video` / `text_only` /
  `partial`).
- **EBOS** as a 0–100 ring, with the coverage band shown next to it, never alone.
- Metric chips, each with its `provenance_kind` badge:
  - `Running since 12 Jun` — observed in user evidence
  - `Repeated across 5 submitted variants` — derived from evidence
  - `FB · IG` — observed
  - `Appeared 2nd in captured result order` — observed *(absent when order wasn't captured)*
- Source count, capture date, and whether rank/order was **visible** or **inferred**.
- A one-line plain-language limitation statement.
- Checkbox: **Use this angle**.

Filters: competitor, modality, format, hook type, country. Sort: EBOS, visible
duration, variants, recency. A **"Why this ranking?"** button opens the score
derivation and the coverage breakdown.

### S5 — Teardown Drawer
Left: the submitted artefact — image, player with synced transcript, or copy card —
with OCR overlaid at its timestamps. Right: hook / angle / objection / beat timeline /
offer / CTA / proof / production complexity, with `modality` and evidence quality at
the top. Bottom: full EBOS derivation — every input, raw value, normalised value,
weight, contribution, and which components were dropped for lack of evidence. Footer:
`Use this angle`, `Compare` (up to 3), and **`Add more evidence for this ad`**.

### S6 — The Gate `/runs/[id]/gate`
Unlocks at ≥1 selection. Shows the selected ads with a one-line preview of the
reanchored angle, plus overrides (aspect, duration, tone, must-include, must-avoid,
offer). Estimated cost and time. One primary button: **Force Generation**.

Directly beneath it, in plain text — not a tooltip: what `force` does and does not
override (proceeds past warnings, never past blocks), and, when coverage is thin, a
restatement that this angle was chosen from a partial view of the market.

### S7 — Generation Timeline `/runs/[id]/generate`
One node per stage, each expanding to the real artefact: the brief with its
`divergence_note`; the three hook variants and the beat table with a word-budget bar;
the rendered frame with its prompt **and each QA retry with its failures**; the shot
list and Seedance prompts; QA findings by severity with the similarity report; then the
player, variants, bundle and prompt export. Show the retries — they are the most
informative part of the screen.

### S8 — Snapshots & Diff `/search-refs/[id]`
Timeline of evidence batches captured against one saved search. **Compare** any two:

| Bucket | Wording |
|---|---|
| Newly observed | ads present in B, absent in A |
| **Not observed in the latest submitted snapshot** | present in A, absent in B — *never* "killed" or "stopped running" |
| Changed copy | matched by library ID or hash, text differs — with a text diff |
| Changed creative | same ad, different asset hash |
| Newly repeated concepts | cluster whose variant count grew |

Above every diff, a **comparability panel**: same search reference? same declared
filters? same market? capture dates. When any differ, the diff renders with a
prominent *"these snapshots are not directly comparable"* banner and the buckets are
labelled as indicative only.

An ad only reaches `likely no longer active` after **three comparable snapshots**
missing it, and the UI states the rule inline wherever that status appears.

### S9 — Library `/library`
All runs and generated assets, filterable by brand and market, each linking back
through the provenance record to the evidence item whose angle it inherited.

*(`07-CLOSED-LOOP.md` adds S10 Results and S11 Patterns when an ad account is
connected; `08` adds the Evidence Watchtower feed.)*

## 2. Streaming

Subscribe to `postgres_changes` on `run_steps` filtered by `run_id` for durable step
transitions; take high-frequency progress from Realtime `broadcast` (`06 §A4`). On
reconnect, refetch run state and resume. Never render from the stream alone.

Show meaningful messages, not spinners.

## 3. Upload handling

- Client-side type and size validation before upload (`11 §3`), with server-side
  revalidation as the authority.
- Files land quarantined; the card shows a scanning state and becomes analysable only
  after the scan clears.
- Strip EXIF/location metadata from images on ingest unless the user opts in.
- Preview via short-TTL signed URLs only.
- Show SHA-256 and capture time on every uploaded artefact in the teardown drawer.

## 4. Empty and failure states worth building properly

- **Empty board.** Not an error — the expected state before capture. Route straight
  back to S3 with the specific next action: *"Open the UAE / Arabic search for
  Competitor B."*
- **Thin coverage at the gate.** Allow proceeding; state plainly that the angle was
  selected from a partial view.
- **Unparseable pasted URL.** Explain what was expected, keep the raw string, and let
  the user attach it as a plain reference anyway.
- **Quarantined file.** Say what happened and what to do; never silently drop it.
- **Non-comparable snapshots.** Explain which condition differs and offer to recapture
  with matching filters.

## 5. Provenance in the UI (enforced, not aspirational)

One `<Metric>` component. Required props: `value`, `label`, and
`provenance: 'observed_in_user_evidence' | 'user_asserted' | 'derived_from_evidence' |
'model_interpretation' | 'unknown'`. **There is no default.**

- observed — solid badge
- user asserted — solid outline badge, plus "entered by you" on hover
- derived — outline badge; hover shows the formula and this ad's inputs
- model interpretation — dashed badge
- unknown — muted placeholder, never `0` and never blank

Rules, all CI-enforced (`10 §3`):
- Every number in the app renders through `<Metric>`.
- The words **best performing, impressions, spend, ROAS, CTR, conversion, scaling
  budget** must not appear in reference to a commercial competitor ad. A grep test over
  UI strings is cheap and blocking.
- A user-asserted performance figure may be shown **only** with its source and capture
  time attached.
- An EBOS ring never renders without its coverage band.
- Every board and every export carries the coverage statement.

## 6. Design direction

Dense, dark, instrument-panel — a tool for someone who reads ad accounts all day. One
accent colour, reserved for actions: Open in Ad Library, Use this angle, Force
Generation. Creative thumbnails are the only saturated colour on the board.

Motion only where it carries information: the step tracker, the coverage meter filling
as evidence lands, the EBOS ring counting up, the timeline advancing.

Keyboard-first collection: `⌘V` paste anywhere to attach, `Enter` to commit an item,
`j/k` to move, `space` to select, `g` to gate. The collection screen should feel like a
capture tool, not a form.

## 7. Definition of done

- [ ] A user can go intake → search links → 12 submitted ads → ranked board without
      reading instructions.
- [ ] Clipboard paste attaches a screenshot as an evidence item in one keystroke.
- [ ] The coverage warning is present on the board, the gate and every export.
- [ ] Every number carries a provenance badge; the CI grep test passes.
- [ ] No absent ad is ever labelled "killed" or "stopped running".
- [ ] A diff across non-comparable snapshots renders its banner and degrades wording.
- [ ] Score derivation matches `ad_scores.inputs`, including dropped components.
- [ ] Gate selection survives a refresh.
