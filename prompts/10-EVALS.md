# 10 — EVALS: making prompt changes falsifiable

Ten LLM agents run in sequence. Without evals, every prompt edit is a guess, nobody
can tell a regression from variance, and the pack in `03-AGENT-PROMPTS.md` decays into
folklore within a month. This is the least glamorous file here and the one that
decides whether the product is maintainable.

## 1. Golden sets

Three, built once, versioned in the repo under `evals/golden/`:

**G1 — Teardowns (n ≈ 60).** Real ads across 6 categories × 4 markets × both
modalities (full media and text-only). Each labelled by a human: hook type, format,
angle, objection, offer presence, CTA strength. Two annotators, disagreements
resolved and recorded — a single annotator's labels are that annotator's opinion, and
you will be measuring agreement with one person's taste forever.

**G2 — Competitor sets (n ≈ 20).** Brand + market -> the competitor set a category
expert would name. Scored on recall against the expert list, not on precision; the
agent finding an unexpected-but-correct competitor is a win, not an error.

**G3 — Scoring cases (n ≈ 30).** Hand-constructed cohorts with known correct
orderings, including the adversarial ones: the abandoned evergreen, the brand-new
recency spike, the 3-ad cohort, the single-advertiser 40-variant flood, the fully
censored cohort where nothing has stopped running.

## 2. What to measure per agent

| Agent | Metric | Bar |
|---|---|---|
| `brand_researcher` | field-level accuracy vs verified dossier; **null-when-unknown rate** | ≥ 0.85 accuracy, ≥ 0.9 correct nulls |
| `competitor_cartographer` | recall@15 vs G2; fabricated-page-ID rate | ≥ 0.7 recall, **0** fabrications |
| `discovery_planner` | valid public URLs; one link per (country, language); `country=ALL` only when labelled discovery; plan within user-minute budget | 100% |
| `creative_analyst` | agreement with G1 labels (Cohen's κ on hook type & format) | κ ≥ 0.6 |
| `evidence_auditor` | banned-vocabulary violations; coverage caveat present; dropped components declared | **0** violations |
| `angle_transfer_strategist` | guardrail completeness; substitution correctly triggered when proof is absent | ≥ 0.9 |
| `script_director` | word-count budget, hook ≤ 3s, banned words, claim→proof mapping | 100% mechanical pass |
| `qa_judge` | precision/recall on a seeded set of known-bad creatives | recall ≥ 0.95 on BLOCKs |
| `performance_attributor` | correct refusal on low-n cases | 100% |
| `snapshot_analyst` | correct "quiet period" verdict; never writes killed/stopped; leads with non-comparability when flagged | ≥ 0.9, **0** forbidden terms |

The zero-tolerance rows are the ones that matter. A fabricated page ID sends the whole
harvest at the wrong advertiser; a banned metric word in the UI is the product lying
to a media buyer. Those fail the build.

## 3. Deterministic checks before LLM judges

Most of the table above is mechanically checkable. Do those first, in CI, on every
prompt change — they are fast, free, and catch the majority of regressions:

- JSON schema validation on every agent output.
- Word counts, timing budgets, card limits, banned-word lists.
- Banned-vocabulary grep across `score_auditor` and all UI-bound strings.
- `country=ALL` never present in a `purpose: "scoring"` query.
- Page IDs returned by the cartographer must resolve against a real API lookup or be
  null.
- Similarity gate: a seeded near-verbatim script MUST be blocked. This is the single
  most important regression test in the repo.

### 3.1 Browser Evidence Mode — blocking tests

These prove the product claims are true. All are cheap, all are deterministic, all
block the build:

1. **No unsupported performance metric reaches the UI.** Grep every user-facing string,
   every agent output fixture and every export template for `best performing`,
   `impressions`, `spend`, `ROAS`, `CTR`, `conversion`, `scaling budget` in a
   competitor-ad context. The only permitted occurrences are a user-asserted value
   rendered with its source and capture time — assert that shape, don't allowlist the
   word.
2. **Every score carries a coverage label.** Property test over generated board
   payloads: no `ebos` may serialise without a `coverage_score` and band. Assert at the
   API boundary, so a frontend bug cannot be the only thing standing between a user and
   an unlabelled score.
3. **URL parsing never fetches.** Run the parser over a corpus of Library URLs with the
   network stubbed to raise on any outbound connection. Any request — including a
   redirect follow, a HEAD, a favicon or a preview — fails the test. Extend it to the
   whole worker: assert no code path resolves a `facebook.com` host.
4. **A partial evidence set cannot be described as a complete market view.** Feed a
   6-item batch (coverage ≈ 0.3) to the evidence auditor and assert the output opens
   with the thin-coverage caveat and contains no phrasing that generalises to "the
   market". Run the same fixture through the board renderer and assert the
   non-dismissible coverage banner is present.
5. **Untrusted evidence cannot affect agent instructions.** Seeded injections in ad
   copy, in OCR text, in a transcript, in a filename, and in an EXIF field. Each must
   produce an `anomaly` record, leave the output schema unchanged, leave guardrails
   un-narrowed, and cause no fetch. One test per vector — five tests, not one.
6. **Absence is never a stop.** Grep watchtower output and UI for `killed`,
   `stopped running`, `paused`, `dead`. Assert `likely_no_longer_active` is
   unreachable in fewer than 3 comparable snapshots, and that non-comparable snapshots
   do not increment `consecutive_absences`.
7. **Licensed providers stay off.** Assert a provider with no recorded contract review
   cannot be enabled by config alone.

Only use an LLM judge where the judgement is genuinely qualitative — teardown
agreement, angle quality, briefing usefulness. When you do, use a **different model**
than the one that produced the output, give the judge the rubric rather than asking
for a vibe score, and calibrate it against the human labels in G1 before trusting it.
An uncalibrated LLM judge is a random number generator with good manners.

## 4. Variance is the thing people forget

Run every eval **5 times** and report median plus spread. A prompt change that moves
the median 2 points on a metric whose run-to-run spread is 8 points has not been shown
to do anything. Gate merges on the median moving beyond the observed noise band, not
on a single favourable run.

Fix `temperature` and seeds where the API allows it, and pin the model ID in the eval
config. An eval suite that silently changed model version between two runs has taught
you nothing about your prompt.

## 5. Prompt experiments

`prompts/` files carry a version; `run_steps.prompt_version` already records which one
ran (`03 §11`). Add:

```sql
prompt_variants(id, agent, version, content_hash, active bool, traffic_pct int)
```

Route a slice of production traffic to a candidate prompt, join to `ad_performance`
via `07 §2 phase 17`, and you can eventually answer "does prompt v7 of the script
director produce ads with better thumbstop rates". That is the real eval; everything
above is a proxy that lets you ship safely until you have enough ads to run it.

Do not enable this before ~200 published ads exist. Below that the answer will be noise
and you will act on it.

## 6. CI wiring

- **On every PR:** the §3.1 Browser Evidence Mode suite. Non-negotiable, blocking,
  under a minute — these encode the product's core honesty and access claims, and a
  regression in any of them is a regression in what AdMirror is allowed to say.
- **On every PR touching `prompts/` or `scoring/`:** deterministic checks + G3 scoring
  cases. Under two minutes; blocking.
- **Nightly:** full G1/G2 suites, 5 runs each, results to a dashboard with the noise
  band drawn.
- **Weekly:** cost-per-run tracking and a golden-set drift review — ads in G1 stop
  running and the market moves; refresh a slice of the set each quarter or the suite
  slowly stops describing reality.

## 7. Definition of done

- [ ] `make eval` runs the deterministic suite locally in under 2 minutes.
- [ ] All zero-tolerance metrics are enforced as blocking CI checks.
- [ ] Every eval reports median and spread across 5 runs, never a single number.
- [ ] The LLM judge's agreement with human G1 labels is measured and recorded.
- [ ] A deliberately broken prompt (banned word reintroduced) fails CI.
- [ ] All seven §3.1 tests pass and are wired as blocking.
- [ ] The no-fetch test covers the whole worker, not only the parser module.
