# AdMirror — Build Pack & Router

**Read this file first. It tells you which of the other 19 files you need.**

AdMirror takes a brand name and a target market, researches the brand and its
competitors, hands the user ready-made public Meta Ad Library searches, ranks the
evidence they submit, and — after a human gate — writes a script, renders a first
frame, and generates three finished ad variants plus a test plan.

## What AdMirror does not do

**Browser Evidence Mode does not scrape Meta and does not provide complete automated
market coverage.**

The user searches the public Ad Library in their own browser and submits what they
find. AdMirror never requests a Meta URL — not to harvest, not to validate a pasted
link, not to fetch a preview. A pasted Ad Library URL is a saved reference and a link
the user clicks; it is never an endpoint the system calls.

Consequently, **every board reflects the ads that user submitted, not a complete Meta
inventory.** There are no per-ad impressions, spend, ROAS, CTR or conversion figures
for commercial competitor ads — those are not published, and AdMirror never invents,
infers or implies them. Ranking is an *opportunity score over submitted evidence*,
always shown with a coverage score.

An official Ad Library API adapter and licensed third-party providers can be enabled
later behind the same boundary, without changing the analysis, provenance, safety or
generation layers. Neither is required for v1.

Full rules: `01 §2.1`, `01 §4`, `11-SECURITY.md`.

---

## Routing

### By task

| I need to… | Read |
|---|---|
| Understand the product, the pipeline, the honesty rules | **`01`** — always first |
| Build the API, schema, evidence intake, scoring | `02`, then `06` |
| Write or change an agent's system prompt | `03` |
| Build any screen | `04` |
| Mount the skills / wire the generation stages | `05`, then `19` |
| Set up Postgres, auth, storage, realtime, cron | `06` |
| Connect the user's own ad account; measure and learn | `07` |
| Track competitors over time | `08` |
| Turn one angle into a testable set of ads | `09` |
| Keep prompt changes falsifiable | `10` |
| Handle uploads, URLs, injection, tenancy | `11` |

### By file

| # | File | What it is | When it matters |
|---|---|---|---|
| 01 | `01-MASTER-BRIEF.md` | Product definition, source modes, 15-step pipeline, metric-honesty and provenance rules | Every agent, first, always |
| 02 | `02-BACKEND.md` | Evidence adapters, schema, API, discovery plan, EBOS + coverage scoring | Backend work |
| 03 | `03-AGENT-PROMPTS.md` | The 10 pipeline system prompts, verbatim, with output schemas | Any LLM stage |
| 04 | `04-FRONTEND.md` | 9 screens: intake, collect evidence, board, teardown, gate, timeline, diffs | Frontend work |
| 05 | `05-SKILL-INTEGRATION.md` | Which skill owns which stage; mounting; the three guards | Generation stages |
| 06 | `06-SUPABASE-SUPERMETRICS.md` | Supabase data plane (RLS, storage, realtime, cron); Supermetrics for owned media. **Overrides `02 §1–4`** | Before writing any code |
| 07 | `07-CLOSED-LOOP.md` | Own ad account: baseline, publish as draft, measure, learn | Phase two |
| 08 | `08-EVIDENCE-WATCHTOWER.md` | User-submitted snapshots, comparability, honest diffs | Phase two |
| 09 | `09-CREATIVE-MATRIX.md` | 3 hooks over a shared body, localisation, statics, test plan | Generation |
| 10 | `10-EVALS.md` | Golden sets, per-agent metrics, the seven blocking honesty tests | Before prompts calcify |
| 11 | `11-SECURITY.md` | URL validation, upload handling, prompt injection, RLS tenancy | Before evidence intake ships |
| 12 | `12-SKILL-scriptwriting.md` | `script-writer` — hooks, beats, retention, ad copy | Stage 11 |
| 13 | `13-SKILL-image-core.md` | Nano Banana grammar, realism, optics, framing, in-image text | Stage 12 |
| 14 | `14-SKILL-image-casting-and-ads.md` | Regional casting accuracy, ad layout, product framing | Stage 12, market-specific |
| 15 | `15-SKILL-image-styles.md` | Illustration, anime, CGI, fine-art, director signatures | Stage 12, stylised briefs only |
| 16 | `16-SKILL-video-seedance2.md` | Seedance 2.0 grammar, director mode, motion | Stage 13 |
| 17 | `17-SKILL-video-director.md` | Operation routing, production grammar, shot craft | Stage 13 |
| 18 | `18-SKILL-video-v2v-and-routing.md` | Footage edits, VFX, model choice | Edits; ambiguous briefs |
| 19 | `19-SKILL-MANIFEST.md` | Skill provenance, SHA-256 table, unbundle script, mount guards | Setting up skills |

### By keyword

| Looking for | Go to |
|---|---|
| "impressions", "best performing", forbidden wording | `01 §4.2`, enforced by `10 §3.1` |
| Coverage score, thin evidence, partial view | `02 §7.1`, `04 §5` |
| `provenance_kind`, field-level provenance | `01 §4.1`, `04 §5` |
| Pasted Ad Library URL handling | `02 §2.2`, `11 §2b` |
| Screenshot / recording / CSV upload | `02 §2.3`, `04 §3`, `11 §2c` |
| "Is this ad dead?" | `08 §5` — three comparable snapshots, never "killed" |
| Hooks, retention, emotional arcs | `12` |
| Photoreal, anti-AI-look, phone-shot UGC | `13` |
| Gulf / MENA / South Asia / SEA casting | `14` |
| Arabic or RTL creative | `09 §4`, `14` |
| `@Image` binding, camera registers, native audio | `16` |
| Prompt injection via ad copy or OCR | `11 §1–2`, `03` untrusted-content block |
| Multi-tenancy, RLS | `06 §A3`, `11 §4` |
| Hook A/B testing, shared body, test plan | `09` |

---

## How to use

1. Read `01` and `06` yourself and change anything you disagree with.
2. Start a fresh agent session per lane. Opening message = `01` + `06` + the lane file.
   - **Backend:** `02`, `03`, `05`, `11`
   - **Frontend:** `04`, `11`
   - **Generation:** `05`, `09`, `19`, plus the skill bundles for the stage at hand
3. `03-AGENT-PROMPTS.md` is not documentation — it *is* the prompts. They ship into the
   repo as files under `backend/prompts/` and load at runtime.
4. `12`–`18` are not documentation either — they are the skill files, bundled. Unbundle
   with the script in `19 §4` to `backend/.claude/skills/`, or read them directly when
   an agent needs the craft knowledge without mounting anything.

## Build order

```
1  Supabase project + schema + RLS + the CI tenancy test        06, 11
2  Intake -> brand research -> competitor map -> discovery plan 02, 03
3  Evidence intake: URLs, uploads, quarantine, provenance       02, 04, 11
4  Normalize + EBOS + coverage + board + teardown               02, 03, 04
5  Gate + generation with skills mounted                        03, 05, 19
6  Creative matrix + test plan                                  09
7  The seven honesty tests, before the prompts calcify          10
8  Snapshots + diffs; own-account closed loop                   08, 07
```

Step 1 is the one that is genuinely painful to retrofit — `workspace_id` and RLS belong
on every table from the first commit. Everything else can land in any order.

## The three things to not let an agent get wrong

**Never fetch a Meta URL.** The strongest access control in the product is that nothing
in the system requests one. An exception "just to validate the link" reintroduces the
entire scraping surface. Test for it at the worker level, not just the parser (`10 §3.1`).

**Never present a score without its coverage.** An opportunity score over 8 submitted
ads is a useful signal and a terrible market summary. The difference is one label, and
it must be structurally impossible to omit — assert it at the API boundary.

**Every input is attacker-controlled text.** Ad copy, OCR, transcripts, filenames, EXIF
fields, CSV cells. Anyone can put text in front of this pipeline for the price of one
cheap ad. `11-SECURITY.md` is not boilerplate.
