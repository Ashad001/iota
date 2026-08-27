# 08 — CREATIVE MATRIX: one angle, many ads

`00-MASTER-BRIEF.md` step 13 produces one video per selected source ad. That is not
how paid social is actually run. A media buyer needs a **testable matrix** and a plan
for what to test in what order. This file specs the fan-out.

## 1. The matrix

From one `briefs` row, generate a grid rather than a single asset:

```
axes:
  hook      A | B | C          (already produced by script-writer in stage 11)
  format    primary | contrast (e.g. UGC talking-head vs studio demo)
  aspect    9:16 | 1:1 | 16:9  (crops/regenerations, not separate concepts)
  locale    per market language
```

Default v1 matrix: **3 hooks × 1 format × 1 aspect = 3 videos**, sharing one body.
This is the correct default — it isolates the hook, which is the highest-leverage
variable and the only one worth testing first at small budgets.

Expansions the user can turn on at the gate:
- `+contrast format` -> 6 videos. Use when the source cluster contains two distinct
  formats carrying the same angle.
- `+aspects` -> reframes, generated at stage 14, not re-generated from scratch.
- `+locales` -> §4.

Hard cap the matrix at 12 assets per gate press and show the cost before generating.

## 2. Body reuse — do not regenerate what you already have

Only the hook beat changes across hook variants. Generate the shared body **once** and
concatenate each hook onto it. This cuts generation cost roughly by the number of
variants and — more importantly — makes the test valid, because the only difference
between variants really is the hook. Regenerating the body per variant introduces
uncontrolled variation and the test measures nothing.

Requirements:
- The hook shot must end on a frame that cuts cleanly to the body's first frame. Pass
  the body's opening frame to `motion_director` as the hook shot's target end state.
- Store `scripts.shared_body_video_id` and assemble in ffmpeg at stage 14.
- Colour-match hook and body before concatenation; a visible grade jump at 00:03 reads
  as a broken ad.

## 3. The test plan (new stage 15b)

Generation without a testing plan hands the user a folder of MP4s. Emit a plan.

New agent prompt — `test_planner.md`:

```
You write the media-buying test plan for a generated creative matrix. You receive the
matrix, the brand's objective, the market, and — when a connected ad account exists —
the account's trailing 30-day median CPM, CTR and cost per result.

Rules:
- Test ONE variable at a time. Round 1 is hooks against a shared body. Do not propose
  a round that varies hook and format simultaneously; it cannot be read.
- Size the test from the account's actual costs, not a rule of thumb. State the
  minimum spend per variant required to reach a readable result at the account's CPM,
  and the number of days that takes at the proposed daily budget.
- If the budget the user has cannot produce a readable result, SAY SO and propose
  fewer variants instead of a longer test. Three variants on an unreadable budget is
  three wasted budgets.
- Define the kill criterion and the winner criterion up front, in metrics the platform
  actually reports. Thumbstop rate for hook tests, cost per result for the final read.
- No connected account means no cost data: say the plan is un-costed and give the
  structure only. Do not invent a CPM.

Return:
{
 "rounds":[{"round","variable_under_test","variants":[asset_ids],
            "shared":[what is held constant],
            "daily_budget_per_variant"|null,"min_days","min_spend_per_variant"|null,
            "primary_metric","kill_criterion","winner_criterion"}],
 "readable": bool,
 "readability_note":"what makes this readable or not at this budget",
 "next_round_logic":"what the winner of round 1 feeds into",
 "assumptions":[]
}
```

Render it in S6 as a table, and export as CSV alongside the asset bundle.

## 4. Localisation fan-out

One angle across a multi-language market (GCC en/ar, EU DACH/FR, CA en/fr) is
translation-plus, not translation.

Per locale:
- **Re-script, don't translate.** Run `script_director` again with the same brief and
  a locale instruction. Idioms, humour and the hook mechanism rarely survive literal
  translation; a re-scripted hook in the target language will outperform a translated
  one every time.
- **Re-render the first frame** when the locale implies different casting, wardrobe,
  setting or on-screen script. Reuse the frame only when it is genuinely locale-neutral
  (product-only, abstract, or text-free).
- **Regenerate motion** only if the frame changed; otherwise re-use the video and swap
  the VO and burned captions.
- **RTL handling** for Arabic and Hebrew: caption alignment, punctuation direction, and
  numeral form (Eastern vs Western Arabic numerals) are per-market decisions. Put them
  in `MarketProfile`, not in the renderer.
- Every locale variant records `parent_script_id`, so the matrix stays traceable and
  the results roll up to the angle.

## 5. Non-video outputs

Not every winning angle should be a video, and the pipeline already has what it needs
to produce the alternatives:

- **Static ad** — stage 12's frame plus burned headline. Near-free, since the frame
  already exists. Ship this by default alongside every video; statics still win a
  meaningful share of tests and cost nothing extra here.
- **Carousel** — one frame per beat from the script's beat table, 3–5 cards.
- **Copy-only variants** — 3 primary-text options per asset from the script's angle,
  for the same creative. Meta tests text cheaply; give the buyer the ammunition.

Gate this on `gen-media-router`'s verdict (`04 §6`) when it is installed, and always
show it in the timeline as an explicit node so the choice is visible.

## 6. Message match — check the destination

An ad that promises something the landing page doesn't deliver fails regardless of
creative quality, and this is cheap to catch. Add to stage 14 QA:

Fetch the brief's destination URL, extract its above-the-fold headline, primary offer
and CTA, then judge coherence against the ad. Extend `qa_judge.md` with:

```
"message_match":{"page_headline","page_offer","page_cta",
                 "ad_promise","match":"strong|partial|broken",
                 "gap":null|"what the ad promises that the page doesn't deliver"}
```

`broken` is a **WARN**, not a BLOCK — the user may be about to change the page, and
the app should not refuse to deliver an asset over a destination it does not control.

## 7. Schema additions

```sql
matrices(id, workspace_id, brief_id, axes jsonb, cap int, created_at)
matrix_cells(id, matrix_id, hook_variant, format, aspect, locale,
             script_id, frame_id, video_id, parent_script_id null,
             role text check (role in ('primary','contrast','locale','static','carousel')))
test_plans(id, matrix_id, plan jsonb, readable bool, created_at)
```

`videos` gains `shared_body_video_id` and `is_assembled`.

## 8. Definition of done

- [ ] One gate press yields 3 videos differing only in their first 3 seconds.
- [ ] The shared body is generated exactly once, provable from `videos` rows.
- [ ] Hook/body concatenation has no visible grade or audio seam at the cut.
- [ ] A locale variant is re-scripted, not translated, and RTL captions render right.
- [ ] The test plan refuses to claim readability on an insufficient budget.
- [ ] A static variant ships alongside every video at no extra generation call.
