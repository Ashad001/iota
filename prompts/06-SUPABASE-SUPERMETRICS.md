# 06 — SUPABASE (data plane) + SUPERMETRICS (owned-media measurement)

This file **overrides** the infrastructure choices in `01-BACKEND.md §1–3` and the
measurement mechanics in `05-CLOSED-LOOP.md §2 phase 17`. Everything else in those
files stands.

## Part A — Supabase

### A1. The split: data plane vs control plane

Supabase is the **data plane**. It does not replace the pipeline workers.

| Concern | Owner |
|---|---|
| Postgres + pgvector, migrations, RLS | Supabase |
| Auth, workspaces, membership | Supabase Auth |
| Media storage (ad creative, frames, videos, brand kit) | Supabase Storage |
| Run streaming to the browser | Supabase Realtime |
| Nightly watchtower + measurement jobs | `pg_cron` + `pg_net` |
| Provider webhooks (video completion) | Supabase Edge Functions |
| **The 15-step agent pipeline** | **FastAPI + ARQ workers, unchanged** |

Be explicit about the last row. A run takes minutes and calls Claude repeatedly; Edge
Functions are the wrong shape for it. Do not let the agent try to implement the
pipeline in Deno.

### A2. Project layout change

```
supabase/
  migrations/          # supabase db diff -f <name>
  functions/
    video-webhook/     # provider -> updates videos row -> Realtime does the rest
    supermetrics-sync/ # invoked by pg_cron
  seed.sql
backend/               # as 01-BACKEND.md, minus its own storage + auth layers
web/
```

Local dev is `supabase start`. Everything in `02 §3` becomes a migration. Enable
`vector`, `pg_cron`, `pg_net`, `pg_trgm`.

### A3. Multi-tenancy via RLS — do this on day one

Add `workspace_id uuid not null` to **every** domain table in `02 §3`. This is not
optional and retrofitting it later is painful.

```sql
create table workspaces(id uuid primary key default gen_random_uuid(),
                        name text not null, created_at timestamptz default now());

create table workspace_members(workspace_id uuid references workspaces on delete cascade,
                               user_id uuid references auth.users on delete cascade,
                               role text check (role in ('owner','editor','viewer')),
                               primary key (workspace_id, user_id));

create or replace function current_workspaces() returns setof uuid
language sql stable security definer set search_path = public as $$
  select workspace_id from workspace_members where user_id = auth.uid()
$$;

-- applied to brands, markets, competitors, ads, ad_assets, ad_analysis,
-- ad_scores, ad_clusters, runs, run_steps, gates, briefs, scripts,
-- frames, videos, provenance, hook_patterns, ad_performance
alter table ads enable row level security;
create policy ads_read on ads for select
  using (workspace_id in (select current_workspaces()));
create policy ads_write on ads for all
  using (workspace_id in (select current_workspaces()))
  with check (workspace_id in (select current_workspaces()));
```

Write a test that enumerates `information_schema.tables` and **fails CI** if any
domain table lacks RLS or lacks `workspace_id`. One unguarded table is a cross-tenant
data leak.

Workers use the **service role key** and bypass RLS — so workers must set
`workspace_id` explicitly on every insert. The browser uses the anon key and never
sees another tenant's rows.

### A4. Realtime replaces the hand-rolled SSE

`02 §4`'s `GET /v1/runs/{id}/events` goes away. Two channels, deliberately split:

**Durable step transitions -> `postgres_changes` on `run_steps`.**
Survives reconnects, replayable from the table, exactly the 15 nodes the UI draws.

```ts
supabase.channel(`run:${runId}`)
  .on('postgres_changes',
      { event: '*', schema: 'public', table: 'run_steps', filter: `run_id=eq.${runId}` },
      applyStepUpdate)
  .subscribe()
```

**High-frequency progress -> Realtime `broadcast`, never the database.**
"Competitor B / AE / ar — item 11 of 14" fires hundreds of times per run. Writing each tick to
Postgres is pure waste and makes `run_steps` unreadable.

```python
await supabase.channel(f"run:{run_id}").send_broadcast(
    "progress", {"step": "EVIDENCE_NORMALIZE", "done": 11, "total": 14,
                 "message": "Competitor B / AE / ar — screenshot 3"})
```

Broadcast is lossy by design; that is correct here. On reconnect the UI resyncs
authoritative state from `run_steps` and simply resumes ticking. Keep the frontend
rule from `04 §2`: never render from the stream alone.

### A5. Storage

Private buckets, no public access: `ad-media`, `generated`, `brand-kit`.
Path convention `{workspace_id}/{run_id}/{kind}/{id}.{ext}` — workspace first, so a
storage RLS policy can match on the first path segment.

```sql
create policy "read own workspace media" on storage.objects for select
using (bucket_id = 'generated'
   and (storage.foldername(name))[1] in (select current_workspaces()::text));
```

Serve to the browser with short-TTL signed URLs (60s for previews, 300s for
downloads). Never store a Meta `ad_snapshot_url` in a public bucket or log it — it
carries access tokens in its query string.

### A6. Scheduled work — `pg_cron` + `pg_net`

Replaces the external scheduler for the two recurring jobs:

```sql
select cron.schedule('watchtower-nightly', '0 3 * * *', $$
  select net.http_post(
    url    := current_setting('app.worker_url') || '/internal/watchtower/tick',
    headers:= jsonb_build_object('Authorization','Bearer '||current_setting('app.internal_key')),
    body   := '{}'::jsonb);
$$);

select cron.schedule('supermetrics-sync', '0 5 * * *', $$
  select net.http_post(url := '.../functions/v1/supermetrics-sync', ...);
$$);
```

Keep secrets in Vault (`vault.create_secret`), read via `current_setting`, never
inline in the cron body — `cron.job` is readable.

### A7. Vector search

`ad_analysis.embedding vector(1536)` with an HNSW index (better recall/latency than
ivfflat at this scale, and no rebuild-on-growth problem):

```sql
create index on ad_analysis using hnsw (embedding vector_cosine_ops);
```

Expose clustering + nearest-angle lookup as a `security definer` RPC that filters by
workspace, so the browser can query it directly through PostgREST without the worker
in the loop.

### A8. Connection pooling caveat (this will bite you)

Workers connect through **Supavisor**. Transaction mode does not support prepared
statements — SQLAlchemy/asyncpg will fail confusingly. Either use session mode
(port 5432 direct) for the workers, or set `statement_cache_size=0` and
`prepared_statement_cache_size=0` on asyncpg. Decide once, write it in
`docs/decisions/`, and put it in the README before someone loses an afternoon.

---

## Part B — Supermetrics

### B1. What it is and is not for, in this app

Supermetrics is an **owned-media** connector. It pulls *your* ad accounts' performance
data out of Meta, Google, TikTok, LinkedIn and friends.

| Use Supermetrics for | Do NOT use Supermetrics for |
|---|---|
| Phase 17 MEASURE — real metrics on published AdMirror ads | Competitor harvesting |
| Phase 0 baseline — the brand's historical account performance | Anything touching the Meta **Ad Library** |
| Multi-channel results (TikTok/Google) once you generate beyond Meta | Public/competitor creative of any kind |

Say this in the code as a comment on the adapter class. An agent that hasn't read it
will reach for Supermetrics to solve the competitor problem, burn a day, and discover
it doesn't do that. Competitor data comes from `adapters/adsource/` and only there.

### B2. Why use it instead of calling the Meta Marketing API directly

`07 §2 phase 17` originally specced a direct Insights client. Supermetrics replaces it
and is the better trade for this app:

- No `ads_read`/`ads_management` app review to unblock measurement (you still need
  `ads_management` for phase 16 PUBLISH — that dependency does not go away).
- No OAuth token lifecycle, refresh, or per-account permission debugging.
- Schema normalisation and Meta's attribution-window and breakdown mess handled.
- The same adapter reaches TikTok Ads and Google Ads later with a changed `ds_id`,
  which is where this product goes next.

The cost is a paid dependency and a sync latency of hours, not minutes. That is fine —
phase 17 is a nightly job by design; nobody needs creative-fatigue analysis in
real time.

### B3. Adapter — `adapters/measurement/supermetrics.py`

Implement against `MeasurementAdapter` so a direct Meta Insights client can be swapped
in later without touching the pipeline:

```python
class MeasurementAdapter(Protocol):
    async def list_accounts(self, ws: UUID) -> list[AdAccount]: ...
    async def fetch_ad_performance(
        self, account: AdAccount, since: date, until: date,
        ad_ids: list[str] | None = None) -> list[AdPerformanceRow]: ...
```

Supermetrics query shape (verify against current docs before building — they run more
than one API generation):

```
POST https://api.supermetrics.com/enterprise/v2/query/data/json
{
  "ds_id": "FA",                       # FA = Facebook Ads; AW/GA4/TT for others
  "ds_accounts": ["act_1234567890"],
  "ds_user": "<connected user id>",
  "date_range_type": "custom",
  "start_date": "2026-08-01", "end_date": "2026-08-27",
  "fields": ["date","ad_id","ad_name","impressions","reach","clicks","cost",
             "ctr","cpc","cpm","video_views_p25","video_views_p75",
             "video_views_p100","actions","cost_per_action"],
  "filters": [...],
  "max_rows": 100000
}
```

**Discover fields, do not hard-code them.** Call the schema/fields endpoint at startup,
cache the result, and validate your requested field IDs against it. Supermetrics field
IDs differ per data source and change; a hard-coded list is a silent breakage waiting
for a Tuesday. Fail loudly at boot if a required field is missing from the schema.

Other requirements:
- Idempotent upsert into `ad_performance` on `(ad_id, date, metric)`.
- Re-fetch a **7-day trailing window** every night, not just yesterday. Ad platform
  numbers are restated for days after the fact; a single-day fetch bakes in stale
  values.
- Persist the raw response to Storage under `{workspace_id}/measurement/{date}.json`
  for audit and replay.
- Rate limits and quota are per team — back off and surface quota exhaustion as a
  workspace-level banner, not a silent no-op.

### B4. Attribution join

The join key between AdMirror and Supermetrics is the Meta `ad_id` returned by phase
16, stored on `videos.published_ad_id`. Belt and braces, because users rename things:

1. `ad_id` exact match (primary).
2. `ad_name` prefix `AM-{run_id_short}-{variant}` (fallback).
3. URL tag `?utm_content=admirror_{brief_id}_{variant}` (last resort, and it also
   makes the data usable in the user's own analytics).

Rows that match none of these are **not** AdMirror ads — keep them anyway. The
account's non-AdMirror ads are exactly what you need for the trailing-median baseline
in `07 §2 phase 17`. Store them with `admirror_video_id = null`.

### B5. What this unlocks in `07 §2 phase 18`

With multi-channel owned data flowing, the hook pattern library gains a `channel`
dimension: the same angle can win on Meta and die on TikTok, and after a few hundred
ads AdMirror can say which. Add `channel` to `hook_patterns` now, even while Meta is
the only value — a column is cheap, a migration over a live pattern table is not.

### B6. Definition of done

- [ ] Every domain table has `workspace_id` + RLS; the CI enumeration test passes.
- [ ] A second workspace provably cannot read the first's ads, media, or runs.
- [ ] The run UI updates from `postgres_changes`, resyncs correctly after a forced
      disconnect, and no progress tick is written to Postgres.
- [ ] Signed URLs expire; no bucket is public; no snapshot URL is ever logged.
- [ ] `pg_cron` fires both nightly jobs; secrets come from Vault, not the job body.
- [ ] Supermetrics field IDs are schema-validated at boot and fail loudly when absent.
- [ ] Re-running a night's sync twice produces zero duplicate `ad_performance` rows.
- [ ] Non-AdMirror account ads are ingested and drive the trailing-median baseline.
