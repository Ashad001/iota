# Meta Ad Library — scrape feasibility test

**Tested:** 2026-08-26 17:48 UTC · headless Chromium (Playwright) + curl
**Target:** `facebook.com/ads/library/?...&view_all_page_id=762198483641760` → **Grok by SpaceXAI**, ~24 active ads

## Verdict: works, no login

| Check | Result |
|---|---|
| Document HTTP status | **403** |
| Page actually renders | **Yes** — 20,277 chars of text, 24 `<video>`, 23 `<img>` |
| Login required | **No** — "Log in" appears in nav only |
| Video URLs extractable | **Yes** — 24, with posters |
| Ad copy extractable | **Yes** |
| Library IDs + start dates | **Yes** |
| Asset download (plain curl) | **Yes** — 3,045,036-byte MP4 |
| CORS | `access-control-allow-origin: *` |
| Range requests | Supported (`accept-ranges: bytes`) |

**The 403 is a red herring.** The document request returns 403 but the SPA hydrates and renders the full result set anyway. Anything that checks the status code and bails will wrongly conclude it's blocked.

### Extracted per ad
- Advertiser name (`Grok by SpaceXAI`)
- Result count (`~24 results`)
- Library ID (`1060839320244350`, `1094976809841142`, …)
- Start date (`Started running on 19 Aug 2026`)
- Ad copy — e.g. *"SpaceXAI just released Grok Bot, your team of always-on, delightful digital colleagues."* · *"meet my newest hires 👀"*
- Video URL + poster URL
- Variant flag (`This ad has multiple versions`)

## Two gotchas that will bite

**1. Signed URLs expire in ~4–5 days.** The `oe=` param is a hex Unix timestamp:

```
oe=6A94CF05 → 2026-08-31 00:47 UTC   (tested at 2026-08-26 17:49 UTC)
oe=6A950C4D → 2026-08-31 05:08 UTC
```

So download assets immediately; never store the URL as a durable reference.

**2. Keep the full query string intact.** Stripping `stp` / `efg` params broke the signature — the poster fetch returned **22 bytes of ASCII** (an error body) instead of a JPEG. The video, fetched with its params intact, worked fine. Pass the whole signed string through verbatim.

## Implication for the product

The "your product, in their best ad" idea is technically unblocked: a browser can read a competitor's live ad set, pull creatives and copy, and hand the assets straight to `image_gen` / `video_gen`. Imagine Computer has every piece — `browser_cdp` to render, `terminal` to fetch, the media models to regenerate.

**Ship-it caveat, worth saying out loud to judges:** automated scraping is against Facebook's ToS, and Meta publishes an **official Ad Library API** (linked in the page's own nav) covering this same public transparency data. For a hackathon demo, reading public transparency data in a browser is defensible; for anything shipped, the API is the sanctioned route. Knowing the difference — and saying so — reads as judgment, not as a limitation.

## Connectors — checked, and mostly not there

From `cloud-computer/ai-teams-FE/connectors.json` (37 entries). The file's own `_comment` is unusually honest and worth quoting:

> *"`kind` is the honesty contract, not decoration: 'wired' means create_agent writes a real MCP server block for it; 'local-stand-in' means it currently resolves to `@modelcontextprotocol/server-filesystem` scoped to the agent's own workspace (a folder, NOT the branded service); 'planned' means templates may declare it and cards render it, but nothing is wired yet."*

| Status | Count | Which |
|---|---|---|
| **wired** | **2** | gmail, slack |
| local-stand-in | 2 | drive, sheets — *a filesystem folder, not the real service* |
| **planned** (nothing wired) | **33** | apify, shopify, hubspot, salesforce, reddit, linkedin, x, outreachmagic, stripe, notion, github, figma, supabase, youtube, telegram, whatsapp, zendesk, intercom, airtable, jira, linear, asana, discord, zoom, quickbooks, polymarket, spotify, obsidian, googledocs, googleslides, googlecalendar, homeassistant, applehealth |

**No Meta/Facebook connector exists** — not wired, not even planned.

> Scope caveat: this registry belongs to `ai-teams-FE` (the "AI Agents Marketplace" frontend), not necessarily the hosted imagine.art/computer product. Treat it as a strong signal, not proof of what the hosted product exposes — verify on the actual hackathon account before depending on any connector.

### The practical takeaway

**For an agent with a terminal and a browser, connectors are a convenience, not a requirement.** Any REST API is one `curl` away. Three real paths for ad data, in order of preference:

1. **Apify REST API directly** — Apify publishes Facebook Ad Library scraper actors, callable over plain HTTPS with a token. No connector needed; skips both the ToS problem and Meta app review. Fastest sanctioned-ish route.
2. **Meta's official Ad Library API** — properly sanctioned, but requires a Meta app and review. Too slow for Friday; correct for a shipped product.
3. **Browser** — verified working above. Fine for a demo, not for a product.

Also available: Imagine Computer supports **MCP** (`mcp_oauth`, `mcporter`, `fastmcp`, plus `optional-mcps` for blender / linear / n8n / unreal). Attaching an MCP server is the general-purpose escape hatch — and the **n8n** MCP in particular bridges to hundreds of integrations without waiting on the built-in registry.

**Do not build a demo whose critical path depends on a `planned` connector.** Gmail and Slack are the only two that are real today.

## Repro

```bash
# 1. Render (headless is fine, no auth, ignore the 403)
#    then in-page: [...document.querySelectorAll('video')].map(v => ({src: v.src, poster: v.poster}))

# 2. Download with the FULL signed query string
curl -o ad.mp4 "https://video.<host>.fbcdn.net/o1/v/t2/f2/...&oh=...&oe=..."
```

Sample artifacts pulled during the test: `fresh.mp4` (3.0 MB), `adtest.mp4` (400 KB range fetch) — scratchpad only.
