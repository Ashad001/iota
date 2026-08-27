# Review — AdMirror prompt pack (`Prompts/`, 12 files, 2,332 lines)

**Reviewed:** 2026-08-26 · full read of all 12 files

## Verdict

Unusually good. The metric-honesty rule, the security file, and the angle-transfer/similarity-gate design are the work of someone who has thought about how this fails in production, not just how it demos. If this were a Q4 roadmap I'd sign it off with the fixes below.

It is also, as written, **not buildable by Friday**, and it has **one rule violation** that matters more than any technical finding.

---

## What is genuinely strong

Worth naming, because these are the parts to protect when cutting scope:

- **`00 §4` metric honesty.** Correctly identifies that `impressions`/`spend` are political-ads-only, forbids inventing them, and pushes everything through a provenance badge with a CI grep test (`03 §5`). This single rule is what separates a tool a media buyer trusts from a toy, and the spec knows it.
- **`10-SECURITY.md` in full.** Prompt injection via competitor ad copy is a real and under-discussed threat, and the mitigations are correct: no tools on ingesting agents, schema forcing, and — the best idea in the pack — **guardrails computed in Python as a union, so an injection can add one but never remove one**. Keeping raw competitor copy away from the QA judge is the right instinct.
- **Kaplan-Meier for longevity (`07 §4`).** Right-censoring running ads is statistically correct and almost nobody does it. Sorting on `days_live` systematically undervalues currently-running winners, which are the only ads that matter.
- **`KILLED_FAST` as free negative evidence (`07 §5`).** Knowing what a competitor *stopped* is information nearly no one collects.
- **Shared-body reuse (`08 §2`).** Regenerating the body per hook variant would make the test measure nothing. This shows real media-buying knowledge.
- **Refusal behaviours.** `performance_attributor` refusing below n, `signal_analyst` being allowed to say "quiet week", `test_planner` refusing to claim readability on an insufficient budget. Systems that can say "I don't know" are rare and valuable.
- **Eval variance discipline (`09 §4`).** Median plus spread over 5 runs, gated on the noise band. Most teams never get here.

---

## Critical — these block the buildathon

### C1. Imagine Computer is not the build environment

The brief: *"Imagine Computer must be the core environment used to build the product."*

The pack specifies FastAPI + ARQ + Redis + Supabase + Next.js 15, with the agent layer on the **Claude Agent SDK** (`04 §3`). `imagine.art` appears only as one media provider adapter among several (`00 §7`, `04 §5`). As written this is a Claude Code project that happens to call imagine.art for rendering — which is the opposite of what the rule asks.

This is a disqualification risk, not a style note. Either the pipeline runs *in* Imagine Computer, or the build itself is visibly done in it. Decide which, and make it structural rather than cosmetic.

### C2. Ad Library API access cannot be obtained by Friday

`01 §4` is right that the endpoint needs "an app with Ad Library API access and an identity-confirmed user token" — and that identity confirmation takes days to weeks. `00 §6` says *"Primary path: official Ad Library API… Build for this first."*

For a Friday demo that ordering is backwards. The `AdSourceAdapter` seam already exists (`00 §6`); build the third-party adapter **first** and treat the official API as the post-hackathon migration. Verified working today: an Apify Ad Library actor over plain REST, or a browser render (see `meta-ad-library-feasibility.md` — the page hydrates fully with no login despite a 403 on the document).

Phase 16 PUBLISH additionally needs `ads_management` app review. The spec acknowledges this; just don't put it anywhere near the demo path.

---

## Significant — product correctness

### S1. `CREATIVE_INGEST` runs before `SCORE` — the cost bug

`00 §2` orders the pipeline `5 ADS_HARVEST → 6 CREATIVE_INGEST → 7 SCORE`. So every harvested ad — up to `max_ads` default **600** (`01 §4`) — gets media fetch, ASR, keyframe extraction, per-keyframe OCR and vision description *before* anything decides which ads are worth looking at.

`01 §6` says "for each **shortlisted** ad", but no step before 6 produces a shortlist. Either the word is doing work the spec never defines, or it means all 600.

This is the dominant cost in the system and it is spent almost entirely on ads that will rank badly.

**Fix — reorder:**
```
5  ADS_HARVEST
6  CHEAP_SCORE      PPS from metadata alone — longevity, variant count,
                    breadth, recency. All present in the API response. Free.
6b CLUSTER          on ad-copy text embeddings (copy is already in the response)
6c SHORTLIST        top N per cluster, N ≈ 30–50 total
7  CREATIVE_INGEST  media/ASR/OCR/vision on the shortlist only
8  RESCORE          fold in content signals
9  TEARDOWN
```
Cuts ingest cost by roughly an order of magnitude and changes nothing the user sees.

### S2. The no-shared-7-gram BLOCK will fire on boilerplate — and can't be forced past

`00 §5` and `02 §10` both make **any** shared 7-gram with the source ad a `BLOCK`, and `01 §8` states force "never bypasses a block".

A 7-gram is seven consecutive words. `"free shipping on all orders over $50"` is a 7-gram. So is most of `"30 day money back guarantee no questions asked"`. Category boilerplate is *shared by construction* — that's what makes it boilerplate. The result is a user who cannot generate an ad, with no override, because their competitor also offers free returns.

**Fix:** block only on **distinctive** n-grams — weight by inverse document frequency against a category corpus, or maintain a boilerplate stoplist, and require the shared 7-gram to be rare before it blocks. Keep the hard block for genuinely distinctive phrasing and trade dress; that's the case the rule is actually for.

### S3. Variant count is confounded, and it carries ~50% of the tier-B score

`01 §6` calls variant collapse *"the single most valuable signal in the system"*. It's a good signal, but it is not clean: advertisers routinely duplicate one creative across many ad sets for CBO and budget-testing reasons, and agencies bulk-upload as a matter of habit. **40 ad IDs is often 40 ad sets, not 40 tests of a winner.**

Worse, the revised tier-B weights in `07 §4` put `scale` 0.20 + `scaling` 0.18 + `iteration` 0.12 = **0.50 of the score on three heavily collinear measures of the same underlying construct** ("how much are they duplicating this"). An advertiser with a bulk-upload habit dominates the board for structural reasons unrelated to performance.

**Fix:** collapse `scale` and `scaling` into one component (level + velocity of duplication), cap its combined weight near 0.30, and treat duplication *across distinct copy variants* as a stronger signal than duplication of identical copy — the former is testing, the latter is account structure.

### S4. `variant_count` has no column

`01 §6` says same-creative ads "collapse into one row with `variant_count = n`", and `01 §7` reads `variant_count` in the PPS formula. The `ads` DDL in `01 §2` has no such column. It exists only on `ad_observations` (`07 §2`), which is added two files later.

Add `variant_count int not null default 1` and `variant_ad_ids text[]` to `ads`. Also worth adding: `ad_scores` has no unique constraint on `(ad_id, market_id)`, so recomputation will silently accumulate duplicate score rows.

### S5. Text-only dedupe over-collapses

`01 §6` dedupes text-only ads at "normalised body cosine ≥ 0.92". Advertisers very commonly run **identical copy against different creative** — that's the standard creative test. Text-only mode will merge genuinely distinct creatives into one row and inflate `variant_count`, which then inflates `scale`, which is 20–28% of the score.

Since `SNAPSHOT_RENDER_ENABLED` defaults to `false`, **this is the default path.** Either raise the threshold sharply in text-only mode, or cap `variant_count`'s contribution when `modality == "text_only"` and say so in the UI.

---

## Minor

- **`03 §2` still specifies SSE.** `06 §A4` deletes `GET /v1/runs/{id}/events` in favour of Supabase Realtime, but `03 §2` still tells the frontend agent to use `EventSource`. The override note in `06` covers it, but patch `03` — the frontend lane reads it as its primary instruction.
- **Verify the Graph API version.** `01 §4` pins `v23.0`. Meta ships roughly three versions a year; confirm what's current before building, and note that deprecated versions return confusing errors rather than clean ones.
- **No cost model anywhere.** `01 §10` has `max_cost_cents` but nobody has done the arithmetic. Ten agents, five on Opus, plus vision/ASR across the shortlist — a single run's cost should be estimated before pricing is discussed. S1's reordering is the main lever.
- **G1 needs ~60 ads double-annotated by hand** (`09 §1`). Correct for a real product, impossible this week. Fine — just don't let it block.

---

## Recommended one-day cut

Keep the soul, drop the infrastructure. In priority order:

**Build:**
1. Adapter-first data access (Apify REST, or the verified browser path) — never the official API.
2. `brand_researcher` → `competitor_cartographer` → `query_planner` → harvest, **one market, 2–3 competitors**.
3. Metadata-only PPS + copy-text clustering (S1's cheap path — no media ingest at all on day one).
4. `creative_analyst` teardown on the **top 5** ads only.
5. The gate.
6. `angle_transfer_strategist` → `script_director` → `frame_director` → `motion_director` → one finished video.
7. Provenance row + the similarity gate (with S2's rarity fix).

**Keep because they're cheap and they're the differentiator:**
- Metric honesty and the `<Metric>` provenance badge. It costs nothing and it is the entire credibility of the demo. *"Every competitor tool on the market shows you a fake performance number. We show you what we actually know."* That line wins the room.
- The `AdSourceAdapter` seam.

**Drop entirely for now:** Supabase + RLS, FastAPI/ARQ/Redis, watchtower (`07`), creative matrix (`08`), closed loop (`05`), Supermetrics (`06B`), evals (`09`).

**Carry forward regardless of scope:** `workspace_id` on every table from commit one (`06 §A3`). The pack is right that this is the one thing genuinely painful to retrofit — and it's a single column, not an architecture.

---

## The framing note

`05-CLOSED-LOOP.md §1` is the best argument in the pack and it's buried in file five:

> *AdMirror as originally specced generates an ad and never finds out whether it worked.*

Even if the closed loop isn't built this week, **say this on stage**. A judge will ask "how do you know the generated ad is any good?" — and having already named your own product's largest gap, with the architecture to close it, is a far stronger answer than being caught by the question.
