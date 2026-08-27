# 05 — CLOSED LOOP: your own ad account

Read `00-MASTER-BRIEF.md` first. This file fixes the largest gap in the base spec:
**AdMirror as originally specced generates an ad and never finds out whether it
worked.** Everything in files 00–04 is inference off public data. This file connects
the one source of *measured* truth available — the user's own ad account — and turns
the product from a generator into a system that learns.

## 1. Why this is the highest-value addition

The competitor half of the app can never measure anything (see `00 §4`). But the
user's own Meta ad account has real `impressions`, `spend`, `ctr`, `thumbstop rate`,
`hook retention`, `cost per result`. Three things unlock at once:

1. **Ground truth on AdMirror's output.** Did the generated ad beat the account
   average? That's the only honest answer to "does this product work".
2. **Calibration of the Proxy Performance Score.** Once you have N generated ads with
   real results traced back to the source angles that inspired them, you can regress
   actual performance against PPS components and re-fit the weights in `01 §7` from
   data instead of judgement. The weights table becomes empirical.
3. **Brand-accurate reference assets.** The user's own best ads are the correct
   reference images for identity locking in stage 12.

## 2. Three new pipeline phases

Insert around the existing 15:

```
 0  SELF_HARVEST     the user's own Meta page, through the same Ad Library path
 …  (existing 1-15)
16  PUBLISH          push generated creative to Ads Manager as a PAUSED draft
17  MEASURE          pull Insights on published ads, attribute back to source angles
18  LEARN            re-fit scoring weights + update the hook pattern library
```

Phases 16–18 are optional per workspace and gated on the user connecting an account.
The app must remain fully functional without them.

### Phase 0 — SELF_HARVEST

Run the exact same Ad Library harvest against the user's *own* page ID, in the same
market. Costs almost nothing and produces three things:

- **A baseline row on the leaderboard.** Show the user's own best ad ranked alongside
  competitors, same PPS, same evidence line. This single UI element is the most
  persuasive thing in the app — "your longest-running ad is 31 days; theirs is 94."
- **Their own voice, evidenced.** Feed their real ad copy into the Brand Dossier's
  `voice` field instead of inferring register from a homepage.
- **Brand reference imagery** for stage 12 identity locking, pulled from creative they
  already ran and already cleared.

Store with `is_own_brand = true` on `ads`. Never let own-brand ads contaminate
competitor cohort percentile bases in scoring — filter them out of `p95()` inputs.

### Phase 16 — PUBLISH

Meta Marketing API, `ads_management` scope. Push as a **paused draft**, never live:

```
POST /act_{ad_account_id}/advideos       upload the MP4        -> video_id
POST /act_{ad_account_id}/adimages       upload the thumbnail  -> image_hash
POST /act_{ad_account_id}/adcreatives    body/title/link/CTA   -> creative_id
POST /act_{ad_account_id}/ads            status=PAUSED         -> ad_id
```

Rules:
- `status: PAUSED`, always. Publishing a live ad that spends money is the user's
  action in Ads Manager, not the app's. Do not add a "launch" button in v1.
- Write `admirror_run_id` and `admirror_brief_id` into the ad's `name` and into a
  `tracking_specs`/URL tag so attribution survives even if the user renames it.
- One creative per hook variant from stage 11, all in one paused ad set, so the user
  walks into Ads Manager with a ready A/B test rather than a single asset.
- Verify scope, ad account access and page permissions at connect time and surface a
  precise error, not a generic failure, when any are missing.

App review is required for `ads_management` on a public app. Build against a dev app
with the user's own account first; note the review dependency in the README.

### Phase 17 — MEASURE

> **Overridden by `06-SUPABASE-AND-SUPERMETRICS.md` Part B:** measurement is pulled
> through Supermetrics rather than a direct Meta Insights client. The derived metrics,
> the trailing-median baseline and the `MEASURED`-only-for-own-ads rule below all
> stand unchanged — only the transport changes.

Nightly job per connected account, for every published `admirror` ad:

```
GET /{ad_id}/insights
  fields = impressions, reach, frequency, spend, clicks, ctr, cpc, cpm,
           actions, cost_per_action_type, video_thruplay_watched_actions,
           video_p25/p50/p75/p100_watched_actions, video_play_actions
  date_preset = maximum   (also pull daily for the trend)
```

Derive the metrics that actually matter for creative diagnosis:

```
thumbstop_rate   = video_p25_watched / impressions      # is the hook working?
hold_rate        = video_p75_watched / video_p25_watched # is the body working?
completion       = video_p100_watched / video_play
cost_per_result  = spend / primary_action_count
```

Store in `ad_performance(ad_id, admirror_video_id, date, metric, value)`. Compare each
against the account's trailing 30-day median for the same objective — absolute numbers
are meaningless across accounts, relative lift is not.

**This is the one place in the entire app where `MEASURED` metrics about performance
legitimately appear.** They are about the user's own ads only. Do not let this data
leak into competitor cards.

### Phase 18 — LEARN

Two artefacts, both cross-run and cross-brand:

**a. Weight re-fit.** Once ≥ 40 published ads have ≥ 7 days of data, regress
normalised `cost_per_result` lift against the PPS component values of each ad's
source angle. Output a proposed weight vector. **Propose, never auto-apply** — show
the operator the old weights, the new weights, the sample size and the fit quality,
and let them accept. Auto-tuning a scoring model on 40 noisy samples is how you build
a system that confidently ranks garbage.

**b. Hook pattern library.** New table:

```sql
hook_patterns(id, mechanism, format, category, market_id,
              source_ad_count, generated_ad_count,
              median_thumbstop_lift, median_cpr_lift, n, updated_at)
```

Aggregate every teardown's `hook.type` × `format` × brand category × market, joined to
real results where they exist. After a few months this answers "problem-agitate hooks
outperform stat hooks in skincare/GCC by 1.4× on thumbstop" — which is a genuine asset
no single run can produce and no competitor can copy from you.

Surface it in the UI as a **Patterns** tab, and feed it into `angle_transfer_strategist`
as an extra input: "in this category and market, these mechanisms have historically
carried."

## 3. New agent prompt — `performance_attributor.md`

```
You explain why a generated ad performed the way it did. You receive: the generated
ad's script and teardown, its real performance metrics indexed against the account's
trailing median, and the source competitor angle it inherited.

Diagnose at the creative level, using the funnel the metrics describe:
- Low thumbstop  -> the hook failed. The first 3 seconds, the frame, or the format.
- Good thumbstop, low hold -> the hook wrote a cheque the body didn't cash.
- Good hold, low CTR -> the offer or CTA failed, or the ad sold the wrong thing.
- Good CTR, bad cost per result -> the ad is fine; the mismatch is downstream.

Be specific about which beat failed and why. Never explain a result with "the
creative didn't resonate".

Where n is small, say so plainly and refuse the diagnosis. An ad with 400 impressions
is not evidence of anything, and a confident story told about noise is worse than
silence — it will be fed back into the pattern library and poison it.

Return:
{
 "verdict":"outperformed|inline|underperformed|insufficient_data",
 "n_sufficient": bool, "impressions", "days_live",
 "funnel_stage_failing":"hook|body|offer|downstream|none",
 "diagnosis":"2-3 sentences, beat-level",
 "angle_verdict":"the inherited angle transferred well | did not transfer",
 "next_iteration":[{"change","rationale","expected_effect"}],
 "pattern_signal":null|{"mechanism","format","direction":"positive|negative",
                        "confidence":"low|medium|high"}
}
```

## 4. Frontend additions

- **S1 Intake:** "Connect Meta ad account" as an optional step, clearly marked as
  unlocking real measurement. Explain what is read and that nothing is ever launched.
- **S3 Leaderboard:** the user's own best ad pinned at the top of the board in a
  distinct "You" row, same metric treatment, same score derivation.
- **S6 Generation timeline:** a final `Publish to Ads Manager (paused)` node.
- **New S8 — Results** `/results`: every published AdMirror ad with real metrics
  indexed to account median, the `performance_attributor` diagnosis, and a one-click
  "generate the next iteration" that feeds `next_iteration` straight back into the
  angle transfer stage as overrides.
- **New S9 — Patterns** `/patterns`: the hook pattern library, filterable by category
  and market, with sample sizes shown on every cell. Grey out any cell with n < 5
  rather than showing a seductive number built on three data points.

## 5. Definition of done

- [ ] Self-harvest puts the user's own best ad on the board with a real PPS.
- [ ] A generated video reaches Ads Manager as a paused draft with all three hook
      variants and correct attribution tags.
- [ ] Insights land nightly and index correctly against account trailing median.
- [ ] The attributor refuses to diagnose an ad with < 1,000 impressions.
- [ ] Weight re-fit runs, proposes, and requires explicit operator acceptance.
- [ ] Own-brand ads are provably excluded from competitor percentile bases.
