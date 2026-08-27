# 08 — EVIDENCE WATCHTOWER: honest change over time

A single evidence batch is a photograph of what one person captured on one afternoon.
The intelligence in competitive creative is in the **derivative** — what appeared, what
stopped appearing, whose creative is being repeated more. This file adds that, using
only user-submitted snapshots.

**There are no automatic sweeps.** AdMirror never revisits a Meta URL. The system's job
is to remember the search, prompt the user at the right moment, and compute a
transparent, honest diff between what they submitted then and what they submit now.

## 1. What changes versus an API-driven watchtower

| API-driven | Evidence Watchtower |
|---|---|
| Nightly automated sweep | Reminder to the user; they capture |
| "Ad stopped running" | "Not observed in the latest submitted snapshot" |
| Kill detection after N absent sweeps | `likely no longer active` only after **3 comparable** snapshots |
| Complete cohort assumed | Coverage score on every snapshot; comparability checked before diffing |
| Survival analysis over full population | Duration visible in evidence, per ad, with censoring stated plainly |

The weaker guarantee is the honest one. A competitor ad missing from a user's second
capture may have stopped, or may be on page three, or may have been filtered out by a
slightly different search. The system must not resolve that ambiguity by assuming.

## 2. Schema

```sql
watch_targets(id, workspace_id, search_reference_id, competitor_id, market_id,
              intended_filters jsonb,        -- country, language, active_status, media_type
              cadence interval default '14 days',
              last_snapshot_id null, next_reminder_at, enabled bool)

snapshots(id, workspace_id, search_reference_id, batch_id, captured_at,
          item_count, coverage_score, comparable_hash, declared_filters jsonb)

snapshot_diffs(id, workspace_id, from_snapshot_id, to_snapshot_id,
               comparable bool, comparability jsonb, result jsonb, created_at)

ad_observations(id, workspace_id, ad_id, snapshot_id, observed bool,
                variant_count, platforms text[], copy_hash, asset_hash null)

ad_status(ad_id primary key, workspace_id,
          first_observed_at, last_observed_at,
          consecutive_absences int, status text,
          -- observed | not_observed_recently | likely_no_longer_active
          status_reason jsonb)
```

`comparable_hash` = hash of (search_reference_id, declared country, language,
active_status, media_type, search_type). Two snapshots are **comparable** only when
their hashes match. Store the components too, so the UI can say *which* condition
differs rather than just refusing.

## 3. The cycle

1. **Watch target created** from a saved search after its first batch closes.
2. **Reminder fires** at `next_reminder_at` — in-app task, email, or Slack. It carries
   the direct Ad Library link and the exact filters to use, so re-capture is one click
   plus a scroll. Reminders that require the user to reconstruct the search will not be
   acted on.
3. **User submits a new batch** against the same search reference → new snapshot.
4. **Comparability check** runs first. If hashes differ, the diff is still produced but
   flagged `comparable: false`, and every bucket is degraded to indicative wording.
5. **Diff computed** (§4) and surfaced.
6. **Status updated** (§5).

`pg_cron` (`06 §A6`) fires reminders only. It never fetches anything.

## 4. The diff

Match ads across snapshots by, in order: `library_id`, content hash, perceptual hash
(Hamming ≤ 8), normalised copy cosine ≥ 0.92. Record which rule matched each pair and
show it — a match the user can't verify is a diff they won't trust.

| Bucket | Definition | Wording in every surface |
|---|---|---|
| Newly observed | in B, not in A | "Newly observed in this snapshot" |
| Not observed | in A, not in B | **"Not observed in the latest submitted snapshot"** |
| Changed copy | matched, text differs | "Copy changed since [date]" + text diff |
| Changed creative | matched, asset hash differs | "Creative changed since [date]" |
| Newly repeated | cluster variant count grew | "Repeated across [n] submitted variants, up from [m]" |
| Still observed | in both, unchanged | "Observed in consecutive snapshots" |

Forbidden in this file's output and its UI: *killed, stopped running, paused, scaling
budget, winning, top performing, dead.* An ad's absence from a user's capture is not an
observation about Meta; it is an observation about the capture.

## 5. Status derivation

```
observed                    seen in the latest comparable snapshot
not_observed_recently       absent from 1-2 comparable snapshots
likely_no_longer_active     absent from >= 3 CONSECUTIVE COMPARABLE snapshots
```

Non-comparable snapshots **do not increment** `consecutive_absences`. A user who
re-captured with a different country filter has produced no evidence about that ad's
status, and the counter must not move.

`status_reason` records the snapshot ids, their capture dates and their
`comparable_hash`, so the UI can show the full basis for a status claim. Any status
stronger than `observed` is rendered with that basis one click away.

## 6. Trend signals — only what the evidence supports

Emit as `signals` for the briefing, each carrying the evidence backing it:

| Signal | Trigger | Note |
|---|---|---|
| `NEW_CONCEPT` | New ad > 0.4 cosine from every existing cluster in this market | The strongest available signal |
| `REPETITION_UP` | Variant count within submitted evidence grew ≥ 3× | "in submitted evidence" is part of the signal name in the UI |
| `COPY_CHANGED` | Matched ad, different text | Often an offer or claim change |
| `CREATIVE_CHANGED` | Matched ad, different asset | |
| `LONG_RUNNING` | Visible start date ≥ 90 days before latest observation | Evidence-backed duration only |
| `NOT_OBSERVED` | Absent from a comparable snapshot | Never phrased as a stop |
| `NEW_ADVERTISER` | Advertiser appears that isn't in the competitor map | |
| `COVERAGE_DROP` | New snapshot's coverage score materially below the previous | Internal; tells the user their capture thinned |

`COVERAGE_DROP` matters more here than any competitor signal: a quiet diff produced by
a thinner capture looks exactly like a quiet market, and only this signal separates
them.

## 7. Agent prompt — `snapshot_analyst.md`

```
You compare two user-submitted evidence snapshots of the same public Ad Library search
and write the briefing the brand's marketing lead needs.

You receive: both snapshots with their capture dates, coverage scores and declared
filters; the computed diff; the comparability verdict; and the previous briefing.

Rules you must not break:
- These snapshots are what ONE PERSON captured on TWO occasions. They are not a census
  of the advertiser's activity. Every conclusion inherits that limit; say so once,
  clearly, and let it stand.
- An ad absent from the newer snapshot is "not observed in the latest submitted
  snapshot". You may NEVER write that an ad was killed, stopped, paused or retired.
  You may note that absence across three comparable snapshots suggests it is likely no
  longer active — only when the diff says three comparable snapshots exist.
- If `comparable` is false, lead with that. Say which condition differs and treat every
  bucket as indicative. Do not narrate a change that a filter difference explains.
- If coverage dropped between snapshots, say so before interpreting anything. A thinner
  capture explains most "quiet" diffs and you must rule it out first.
- Distinguish a new ad (a hypothesis) from a concept repeated across several submitted
  variants (a result the advertiser appears to be leaning on). Never call a single new
  ad a competitor "doubling down".
- Forbidden vocabulary for competitor ads: best performing, impressions, spend, ROAS,
  CTR, conversion, scaling budget, winning.
- If the diff is genuinely small, say the period was quiet. Do not manufacture a
  narrative from three low-severity changes — a briefing that cries wolf gets filtered
  to spam, and then the one that mattered is missed too.
- Every claim cites the signal ids and snapshot ids backing it.
- At most 2 recommended actions, each tied to a specific evidence item.

Return:
{
 "comparable": bool,
 "comparability_note": null|"which condition differs and what that invalidates",
 "coverage_note":"how complete each capture was, and whether coverage moved",
 "headline":"one sentence, or 'Quiet period in submitted evidence'",
 "period_verdict":"quiet|normal|active|not_comparable",
 "developments":[{"what","who","evidence":{"signal_ids":[],"snapshot_ids":[]},
                  "interpretation","new_or_repeated":"new|repeated|changed|absent"}],
 "recommended_actions":[{"action","evidence_item_id","rationale"}],
 "capture_suggestions":[],   // what to capture next time to close a coverage gap
 "limitations":"what these snapshots could not show"
}
```

`capture_suggestions` is the field that compounds. Each briefing should make the next
capture better targeted than the last.

## 8. Frontend

- **S12 — Watchtower** `/watch`: watch targets with cadence, last capture date, next
  reminder, and a **Capture now ↗** button opening the saved search. Below, the diff
  feed with briefings pinned.
- **Snapshot timeline** per search reference (`04 §S8`), with the comparability panel
  above every diff.
- **Board Δ column:** rank movement versus the previous **comparable** snapshot, plus a
  variant-count sparkline. Absent when no comparable prior snapshot exists — show a
  dash and a tooltip, not a zero.
- **Digest:** email/Slack of the briefing, sent only when `period_verdict` is not
  `quiet` or a high-severity signal fired. Honour the agent's restraint — never send a
  digest for a briefing that said the period was quiet.
- Every status label deeper than `observed` links to its `status_reason` basis.

## 9. Definition of done

- [ ] No code path in the watchtower issues a network request to a Meta URL.
- [ ] Two comparable snapshots produce a correct diff with a recorded match rule per
      pair.
- [ ] Non-comparable snapshots produce a flagged diff, degraded wording, and no change
      to `consecutive_absences`.
- [ ] `likely_no_longer_active` cannot be reached in fewer than 3 comparable snapshots
      — unit-tested.
- [ ] The words "killed", "stopped running" and "paused" appear nowhere in watchtower
      output or UI. CI grep, blocking.
- [ ] A thinner second capture triggers `COVERAGE_DROP` and the briefing leads with it.
- [ ] A quiet period produces a briefing that says so, and no digest is sent.
