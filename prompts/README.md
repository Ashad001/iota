# AdMirror — Agent Build Prompt Pack

A hand-off pack for a coding agent (Claude Code / Agent SDK) to build **AdMirror**:
an app that takes a brand name, researches the brand, finds its competitors on the
Meta Ads Library for a chosen geography, ranks their best-performing ads, shows you
the evidence, and — once you hit **Force Generation** — writes a script, renders a
first frame, and generates a finished video ad in your brand's voice. Then it
publishes, measures, and learns from what it made.

## Files

**Core — build this first**

| File | What it is |
|---|---|
| `00-MASTER-BRIEF.md` | Product definition, pipeline state machine, the two non-negotiable rules | 
| `01-BACKEND.md` | Schema, endpoints, Meta client, geo resolver, the scoring formula |
| `02-AGENT-PROMPTS.md` | The 10 pipeline sub-agent system prompts, verbatim, with schemas |
| `03-FRONTEND.md` | 7 screens, the gate, the metric-provenance component |
| `04-SKILL-REFERENCES.md` | How your seedance / nano-banana / script-writer skills mount |

**Infrastructure — read before writing code**

| File | What it is |
|---|---|
| `06-SUPABASE-AND-SUPERMETRICS.md` | Supabase as data plane (auth, RLS, storage, realtime, cron); Supermetrics for owned-media measurement. **Overrides `01 §1–3` and `05 phase 17`.** |

**Extensions — each one materially changes the product**

| File | What it adds | Why it matters |
|---|---|---|
| `05-CLOSED-LOOP.md` | Own ad account: self-harvest, publish as draft, measure, learn | The only *measured* truth in the system; calibrates the scoring model |
| `07-WATCHTOWER.md` | Continuous observation, kill detection, velocity signals, survival analysis | Turns a photograph into a trend; unlocks "they're scaling this right now" |
| `08-CREATIVE-MATRIX.md` | One angle → N testable variants, localisation, statics, test plan | Matches how paid social is actually run |

**Quality — not optional if this ships**

| File | What it adds |
|---|---|
| `09-EVALS.md` | Golden sets, per-agent metrics, variance discipline, CI gates |
| `10-SECURITY.md` | Prompt injection via competitor ad copy, RLS tenancy, secret handling |

## How to use

1. Read `00` and `06` yourself and change anything you disagree with.
2. Start a fresh agent session per lane. Opening message = `00` + `06` + that lane's
   file. Backend lane gets `01`, `02`, `04`; frontend lane gets `03`.
3. `02-AGENT-PROMPTS.md` is not documentation — it *is* the prompts. They ship into
   the repo as files under `backend/prompts/` and load at runtime.
4. Build `05` / `07` / `08` as phase two, but **add `workspace_id` and RLS from commit
   one** (`06 §A3`) — retrofitting tenancy is the one thing here that is genuinely
   painful to do late.

## Build order

```
1  Supabase project + schema + RLS + the CI tenancy test   (06)
2  Meta adapter + geo resolver + harvest + PPS             (01 §4-7)
3  Agents 1-5 + the leaderboard + teardown drawer          (02, 03 S1-S4)
4  Gate + generation stages with skills mounted            (02 §6-10, 04)
5  Evals, before the prompts calcify                       (09)
6  Injection hardening                                     (10)
7  Closed loop, watchtower, matrix                         (05, 07, 08)
```

## The two things to not let the agent get wrong

**There is no public impression number for commercial Meta ads.** The API returns
`impressions`/`spend` only for political and issue ads. Everything performance-shaped
in this app is *inferred* and must be labelled as such. `00 §4` and `01 §7` define
what may be inferred and how. If the agent ships a UI showing "1.2M impressions" on a
competitor card, it fabricated it — reject the PR.

**Every input is attacker-controlled text.** Competitor ad copy, OCR, transcripts and
fetched web pages all flow into LLM context, and anyone can put text there for the
price of one cheap ad. `10-SECURITY.md` is not boilerplate; read it before the
creative analyst gets built.
