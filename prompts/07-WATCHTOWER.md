# 07 — WATCHTOWER: from snapshot to trend

`01-BACKEND.md` harvests the Ad Library once per run. That is a photograph. The
intelligence in competitive creative is in the **derivative** — what launched this
week, what got killed, whose variant count is spiking. This file adds continuous
observation. It is the second-largest gap in the base spec after `05`.

## 1. Why a single harvest under-reads the data

- **Kill detection is invisible.** `ad_delivery_stop_time` is frequently null while an
  ad is live. You only learn an ad stopped by observing that it is no longer returned.
  A one-shot harvest cannot distinguish "running" from "stopped yesterday".
- **Velocity is invisible.** 23 variants is a fact. *23 variants, up from 4 eleven days
  ago* is a decision — a competitor is scaling a winner right now, and that is worth
  more than any static score.
- **Longevity is right-censored.** Ads still running have unknown final lifespans.
  Averaging observed durations across a mix of finished and running ads is statistically
  wrong and biases toward short-lived ads (see §4).

## 2. Schema

```sql
ad_observations(id, workspace_id, ad_id, observed_at, seen bool,
                variant_count int, publisher_platforms text[],
                eu_total_reach bigint null, creative_bodies_hash text,
                primary key (ad_id, observed_at))

ad_lifecycle(ad_id primary key, workspace_id,
             first_observed_at, last_seen_at,
             confirmed_dead_at timestamptz null,   -- absent from N consecutive sweeps
             observed_days int, censored bool,     -- true = still running
             peak_variant_count int, variant_velocity_7d numeric)

watch_targets(id, workspace_id, competitor_id, market_id,
              cadence interval default '1 day', enabled bool, last_run_at)

signals(id, workspace_id, market_id, competitor_id, ad_id null,
        kind, severity, payload jsonb, detected_at, acknowledged_at)
```

`ad_observations` is append-only and will be the largest table in the system. Partition
by month, and retain full rows 90 days then roll up to daily aggregates.

## 3. The nightly sweep

Fired by `pg_cron` (`06 §A6`). For each enabled `watch_target`:

1. Re-run that target's slice of the stored `QUERY_PLAN` — same countries, same
   languages, same page IDs. **Reusing the stored plan is what makes the comparison
   valid.** A re-planned query returns a different population and every diff is noise.
2. Write one `ad_observations` row per ad returned, plus `seen=false` rows for ads
   previously seen in this target and absent now.
3. Update `ad_lifecycle`. Mark `confirmed_dead_at` only after **3 consecutive** absent
   sweeps — the API returns partial pages and transient gaps, and a one-sweep absence
   produces false death notices that destroy trust in the feed.
4. Run the diff engine (§5) and emit `signals`.
5. Recompute PPS with the trend components from §4.

Budget: sweeps share the same per-workspace API call ceiling as runs. When the budget
binds, degrade in this order — drop ATTENTION-tier competitors, then secondary
languages, then reduce cadence to every other day. Log every degradation as a signal
so the user knows coverage dropped rather than the market going quiet.

## 4. Trend components for PPS

Add to the score in `01 §7`, and re-normalise the weights:

```
variant_velocity_7d = (variant_count_now - variant_count_7d_ago) / 7
scaling            = tanh(variant_velocity_7d / p75(velocity | market))     [0,1]
survival_percentile = KM_survival_rank(days_live | cohort)                   [0,1]
```

**Survival, done properly.** Fit a Kaplan-Meier curve per cohort where still-running
ads are right-censored observations rather than completed lifespans. `survival_percentile`
is then "this ad has outlived X% of comparable ads", which is exactly the question and
is not answerable by sorting on `days_live`. Anything simpler systematically
under-values currently-running winners, which are the only ads that matter.

Revised tier B weights once ≥ 14 days of observation exist for a cohort:

| Component | weight |
|---|---|
| survival_percentile | 0.28 |
| scale (variant count) | 0.20 |
| **scaling (velocity)** | **0.18** |
| iteration | 0.12 |
| recency | 0.12 |
| breadth | 0.10 |

Cohorts with < 14 days of observation keep the original `01 §7` weights and a
`trend_available: false` flag. Never silently mix the two — the UI must say which
scoring regime produced a number.

## 5. Diff engine — the signals worth waking someone for

| Signal | Trigger | Severity |
|---|---|---|
| `NEW_ANGLE` | New ad whose embedding is > 0.4 cosine distance from every existing cluster in this market | high |
| `SCALING` | variant_count up ≥ 3× in 7 days, floor of +5 | high |
| `KILLED_FAST` | Confirmed dead with lifespan < 10 days — they tested and rejected it, which is free negative evidence | medium |
| `EVERGREEN_BROKEN` | An ad live > 120 days stops — their control just changed | high |
| `NEW_ENTRANT` | A page not in the competitor set appears repeatedly on category keyword queries | medium |
| `FORMAT_SHIFT` | A competitor's format mix moves > 25 points in 30 days | medium |
| `GEO_EXPANSION` | Existing creative appears in a country it wasn't running in | medium |
| `OFFER_CHANGE` | Extracted offer/price language changes on a scaled creative | high |
| `COVERAGE_DROP` | Our own sweep was degraded or rate-limited | low, internal |

`KILLED_FAST` deserves emphasis: knowing what a competitor *stopped* running is
information almost nobody collects, and it is only available if you were watching.

## 6. New agent prompt — `signal_analyst.md`

```
You review one week of competitive signals for a single brand and market and write
the briefing its marketing lead actually needs.

You receive: the signal list with payloads, the current leaderboard, the previous
week's briefing, and the brand dossier.

Rules:
- Lead with what CHANGED. The leaderboard is available on its own; do not restate it.
- Distinguish a competitor testing from a competitor scaling. A new ad is a
  hypothesis. Five variants of it eleven days later is a result. Say which you are
  looking at, and never describe a single new ad as a competitor "doubling down".
- A killed ad is evidence too. Say what its death suggests they learned.
- If the week was genuinely quiet, say the week was quiet. Do not manufacture a
  narrative from three low-severity signals — a briefing that cries wolf weekly gets
  filtered to spam by week four, and then the one that mattered is missed too.
- Every claim cites the signal ids backing it.
- Recommend at most 2 actions, each tied to a specific ad the user could generate
  against this week. Fewer, sharper recommendations beat a list.

Return:
{
 "headline":"one sentence, the single most important development, or 'Quiet week'",
 "week_verdict":"quiet|normal|active|significant_shift",
 "developments":[{"what","who","evidence_signal_ids":[],
                  "interpretation","testing_or_scaling":"testing|scaling|retiring"}],
 "threats":[], "openings":[],
 "recommended_actions":[{"action","source_ad_id","rationale"}],
 "confidence_note":"what this briefing could not see, including any coverage drops"
}
```

## 7. Frontend

- **New S10 — Watchtower** `/watch`: a reverse-chronological signal feed, filterable
  by severity and competitor, with the weekly briefing pinned at the top. Each signal
  expands to a before/after — the ad as it was, the ad as it is.
- **Leaderboard (S3):** add a **Δ column** — rank movement vs 7 days ago, plus a
  variant-count sparkline per card. A card that was #9 and is now #2 is the most
  actionable object on the screen.
- **Ad cards:** a small survival curve where the PPS ring shows longevity, so "outlived
  84% of this cohort" is visible rather than buried in the derivation table.
- **Digest:** weekly email/Slack of the briefing. Send only when
  `week_verdict != "quiet"`, or on a `high` severity signal. Respect the agent's own
  restraint rule — do not send a digest the agent said was empty.

## 8. Definition of done

- [ ] Two sweeps a day apart produce a valid diff with no false deaths.
- [ ] An ad removed from the API is confirmed dead only after 3 absent sweeps.
- [ ] The stored query plan, not a fresh plan, drives every sweep.
- [ ] Kaplan-Meier survival ranks running ads correctly against completed ones, with a
      unit test on a synthetic censored dataset.
- [ ] The leaderboard Δ column matches recomputed historical ranks.
- [ ] A quiet week produces a briefing that says so, and no digest is sent.
