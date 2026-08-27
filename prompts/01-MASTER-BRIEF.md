# 01 — MASTER BRIEF (give this to every agent, first)

You are building **AdMirror**, a competitive-creative engine for paid social.

## 1. The user story

> I type my brand name and the country I sell in. AdMirror figures out who I am and
> who I'm up against, and hands me ready-made public Meta Ad Library searches for each
> competitor in my market. I open them in my own browser, and paste or upload what I
> find — links, copy, screenshots, recordings. AdMirror normalises that evidence,
> ranks it honestly against what I actually captured, and tears down the structure of
> each ad. I read the teardowns, tick the two angles I want, and press **Force
> Generation**. AdMirror writes the script, renders the opening frame, and generates
> three finished variants plus a test plan — mine, in my voice, on the same winning
> angle. Weeks later I revisit the same saved search, submit a new batch, and see an
> honest diff.

## 2. Source modes

AdMirror is source-agnostic by design. **Browser Evidence Mode is the v1 default and
the only mode that ships without external approval.**

| Mode | Status | What it is |
|---|---|---|
| **Browser Evidence Mode** | **v1 default** | The user searches the public Ad Library in their own browser and submits what they find. AdMirror never requests the Library itself. |
| Official Ad Library API | optional adapter, later | Requires an approved app and an identity-confirmed token. Slots in behind the same adapter boundary. |
| Licensed provider | optional, disabled by default | A contracted third-party data source. Enabled only after its terms, permitted-use scope, retention rights and attribution obligations are reviewed and recorded. |

**Do not block the build on Meta API approval.** Build Browser Evidence Mode first.
Preserve the adapter boundary so another source can be enabled later without touching
the analysis, provenance, safety or generation layers.

### 2.1 What AdMirror must never do

These are not tunable. Do not implement, and do not propose as a fallback:

- Web scraping, DOM harvesting, headless crawlers, or browser automation for bulk
  collection.
- Reverse-engineered or undocumented Meta endpoints; extraction of a page's hidden
  network data.
- Cookie or session extraction, CAPTCHA handling, proxy rotation, rate-limit evasion.
- Automatic downloading of competitor media from `ad_snapshot_url` or any Library URL.
- Any background request to a user-pasted Ad Library URL. A pasted URL is a **reference
  and a link the user clicks** — never an endpoint the system calls.

A pasted Ad Library search URL may be used only to: reproduce the search reference,
give the user a link to open, describe the filters they selected, and attach a source
record to evidence they submit manually.

## 3. The pipeline

A durable, resumable state machine. Every step writes a `run_steps` row and streams an
event to the frontend. Any step can be retried in isolation.

```
 1  INTAKE              brand name, website (optional), target market, objective
 2  BRAND_RESEARCH      web research -> Brand Dossier
 3  COMPETITOR_MAP      derive + verify competitor set for THIS market
 4  DISCOVERY_PLAN      build public Ad Library search links per competitor ×
                        market × language × media type — displayed, never fetched
--- 5  EVIDENCE_INTAKE  <<<  USER ACTION: open the searches, submit ads as links,
                        copy, screenshots, recordings or authorised media
 6  EVIDENCE_NORMALIZE  extract normalised ad records; dedupe on transparent evidence
 7  EVIDENCE_RANK       Evidence-Backed Opportunity Score + coverage score
 8  TEARDOWN            structural analysis, with modality and evidence quality shown
--- 9  HUMAN_GATE  <<<  USER ACTION: review, select angles, press Force Generation
10  ANGLE_TRANSFER      winning ad -> brand-safe iteration brief (angle, not asset)
11  SCRIPT              script-writer skill -> hook + beats + VO + on-screen text
12  FIRST_FRAME         nano-banana-prompter skill -> image prompt -> render -> QA
13  MOTION              seedance-2-prompter skill -> I2V prompt -> Seedance -> poll
14  POST                variants, captions, thumbnail, brand + safety + similarity gate
15  DELIVER             asset bundle + provenance record
```

**Steps 1–4 run unattended. Step 5 requires the user.** Steps 6–8 run unattended on
what they submitted. Step 9 blocks. Steps 10–15 run unattended.

This is a change from any earlier draft: in Browser Evidence Mode there are **two**
mandatory human actions, not one. Evidence capture is the user's job, by design — it
is what makes the mode lawful and honest. Do not describe steps 1–8 as fully
unattended anywhere in the product, the docs, or the UI.

"Without your interference" still holds where it matters: **the user never writes a
prompt.** Their input is the intake form, the evidence they capture, and the gate.

Extended by later files: `07` adds the user's own ad account (phases 0, 16–18).
`08` adds user-submitted evidence snapshots and diffs. `09` fans step 13 out into a
creative matrix plus a test plan.

## 4. The metric-honesty rule (non-negotiable)

The public Ad Library does not publish per-ad impressions, spend, CTR, ROAS or
conversions for ordinary commercial ads. Neither does the official API — those fields
exist only for political and issue ads. EU/UK ads carry a published `eu_total_reach`
under the DSA, visible in the Library UI.

Therefore:

- **A performance number for a commercial competitor ad exists only if the user saw it
  and entered it.** Store it as evidence with its source, capture time and the fact
  that a human asserted it. Never derive one.
- `sort_data[mode]=total_impressions` in a Library URL is a **UI-side sort request**.
  It does not mean the returned ads expose individual impression counts, and result
  order is not an impression count. Do not treat it as one.
- Ranking uses the **Evidence-Backed Opportunity Score** over signals actually
  captured. Definition in `02 §7`.
- Every score carries a **coverage score** — how complete the evidence set is for that
  advertiser, search and market. An incomplete set is never "the market's best ads".

### 4.1 Field-level provenance

Every field on every ad record carries a `provenance_kind`:

```
observed_in_user_evidence   the user's submitted artefact shows it
user_asserted               the user typed it; no artefact confirms it
derived_from_evidence       computed by us from submitted evidence
model_interpretation        an LLM's reading of the evidence
unknown                     not captured
```

### 4.2 Language rules

**Forbidden** for commercial competitor ads unless the exact value was visibly supplied
by the user and is shown qualified with its source and capture time: *best performing,
impressions, spend, ROAS, CTR, conversion, scaling budget.*

**Allowed:** *appeared first in the user-captured Library result order; running since
[date], as visible in submitted evidence; repeated across [n] submitted variants;
high opportunity score within this evidence set; observed in consecutive snapshots.*

Enforce this with a CI grep over UI strings and agent outputs (`10 §3`).

## 5. The "copy" rule

The promise is "their best angle, your ad". Build it as **angle transfer, not asset
transfer**:

- **Transfer:** the hook mechanism, the persuasion angle, the objection handled, the
  format and pacing, the offer structure, the CTA shape, the emotional beat order.
- **Do not transfer:** their footage, voiceover, music, talent likeness, logo,
  trademarks, slogan verbatim, or distinctive trade dress.
- Step 14 runs a **similarity gate**: no shared 7-gram with the source copy, embedding
  cosine < 0.88. Over threshold => regenerate with a divergence instruction, max 2
  retries, then surface to the user.

This is a product spec, not a legal opinion. Ship the gate.

## 6. Untrusted input

Every pasted URL, uploaded file, screenshot, OCR result, transcript and file metadata
is **untrusted input written by someone else**. All of it flows into LLM context. The
protections in `11-SECURITY.md` are mandatory and must be extended, never relaxed, as
new evidence types are added.

## 7. Stack

- **Data plane:** **Supabase** — Postgres 16 + pgvector, Auth, Storage, Realtime,
  `pg_cron`, Edge Functions. RLS multi-tenancy from day one. See `06`.
- **Control plane:** Python 3.12, FastAPI, ARQ workers, Redis. The agent pipeline runs
  here, not in Edge Functions.
- **Owned-media measurement:** **Supermetrics** (`06` Part B). The user's own accounts
  only — never competitor data.
- **Frontend:** Next.js 15 (App Router), TypeScript, Tailwind, shadcn/ui, TanStack
  Query, Supabase Realtime.
- **Agents:** Claude Agent SDK; `claude-opus-5` for strategy and judgement,
  `claude-sonnet-5` for high-volume extraction.
- **Media:** provider adapters — imagine.art first, then BytePlus ModelArk (Seedance)
  and Gemini image (Nano Banana). Never hard-code one vendor.

## 8. V1 is complete when a user can

1. Enter a brand and target market.
2. Receive suggested competitor searches.
3. Open a public Meta Ad Library search in their own browser.
4. Submit 5–20 ads as URLs, screenshots, copy, or authorised media files.
5. See a clearly qualified evidence board and useful structural teardowns.
6. Select an ad angle at the human gate.
7. Generate three original, brand-safe creative variants and a test plan.
8. Revisit the same search later, submit another batch, and see an honest diff.
