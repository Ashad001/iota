# 09 — EVALS: making prompt changes falsifiable

Ten LLM agents run in sequence. Without evals, every prompt edit is a guess, nobody
can tell a regression from variance, and the pack in `02-AGENT-PROMPTS.md` decays into
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
| `query_planner` | schema-valid queries; budget respected; `country=ALL` never used for scoring | 100% |
| `creative_analyst` | agreement with G1 labels (Cohen's κ on hook type & format) | κ ≥ 0.6 |
| `score_auditor` | banned-vocabulary violations ("impressions", "spend", "CTR"…) | **0** |
| `angle_transfer_strategist` | guardrail completeness; substitution correctly triggered when proof is absent | ≥ 0.9 |
| `script_director` | word-count budget, hook ≤ 3s, banned words, claim→proof mapping | 100% mechanical pass |
| `qa_judge` | precision/recall on a seeded set of known-bad creatives | recall ≥ 0.95 on BLOCKs |
| `performance_attributor` | correct refusal on low-n cases | 100% |
| `signal_analyst` | correct "quiet week" verdict on synthetic quiet weeks | ≥ 0.9 |

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
ran (`02 §11`). Add:

```sql
prompt_variants(id, agent, version, content_hash, active bool, traffic_pct int)
```

Route a slice of production traffic to a candidate prompt, join to `ad_performance`
via `05 §2 phase 17`, and you can eventually answer "does prompt v7 of the script
director produce ads with better thumbstop rates". That is the real eval; everything
above is a proxy that lets you ship safely until you have enough ads to run it.

Do not enable this before ~200 published ads exist. Below that the answer will be noise
and you will act on it.

## 6. CI wiring

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
