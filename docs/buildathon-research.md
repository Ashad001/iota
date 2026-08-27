# Imagine Buildathon — Research & Strategy

**Team:** **IOTA** — *Imagine on Their Apps*
**Event:** Imagine Buildathon, Fri 28 Aug 2026 · $1,000 pool ($500/$300/$200)
**Constraint:** Imagine Computer must be the core build environment.
**Judged on:** Technical Depth · Innovation & Originality · Product Quality & UX · Growth & Distribution Potential · Impact & Business Potential · Demo & Storytelling
**Compiled:** 2026-08-26

---

## 1. What Imagine Computer actually is

### Public positioning
Launched **6 Aug 2026**. Headline on the product page: *"One AI Agent for Chat, Docs, Slides, Images, Sheets, Video & Music."* Press framing:

> "If generative AI shortened the distance between imagination and creation, agentic AI can shorten the distance between intention and execution."

The pitch is the chatbot→agent jump: a chatbot explains how to build a website, an agent builds one. Company context from the release: bootstrapped, founded by brothers Ahmed, Abdullah and Zain, **3.5M+ MAU**, millions in ARR, Imagine 1.5 / 2.0 models benchmarked competitively.

### What it actually runs on (from `~/Documents/imagine-art-projects`)
Internally the stack is **"Hermes" / `cloud-computer`** — a vendored build of Nous Research's **Computer Agent** (MIT) — with **`imagine-computer-web`** (Next.js + Turborepo + pnpm) as the front end. `ai-teams-FE` confirms the naming: *"a consumer-facing frontend for the cloud-computer (hermes) agent."*

> Caveat: this is inferred from repo naming and the internal front ends. I have not verified that the hosted imagine.art/computer runs this exact build — but `imagine-computer-web`, `cloud-computer`, and the Hermes references line up.

Interfaces exposed by the agent runtime:
- **WebSocket JSON-RPC 2.0** at `/api/ws` — `session.create`, `prompt.submit`, `session.interrupt`; server pushes `message.delta`, `tool.start`, `approval.request`. **This is the only way to run an agent turn — there is no REST endpoint for it.**
- **REST** for everything else — `/api/profiles`, `/api/sessions`, `/api/cron/jobs`, `/api/kanban/board`, `/api/files`, `/api/memory`, `/api/status`.
- Sessions bind to a **profile**; Hermes rebinds `COMPUTER_HOME` per turn and persists to that profile's own `state.db`. **Multiple independent agents, one socket.**

---

## 2. Verified capability surface — the unfair advantages

Extracted from `cloud-computer/toolsets.py`, `tools/`, `skills/`, `plugins/`, `gateway/`.

| Capability | Tools | Why it matters for growth |
|---|---|---|
| **Real browser** | `browser_navigate/click/type/scroll/snapshot/press/back`, `browser_vision`, `browser_console`, `browser_dialog`, **`browser_cdp`**, `computer_use` | Reaches things with **no API**: ChatGPT/Perplexity/AI-Overview answers, marketplace dashboards, logged-in surfaces |
| **Research** | `web_search`, `web_extract`, `x_search`, `research` toolset, `blogwatcher`, `arxiv` | Continuous market/competitor listening |
| **Scheduling** | `cronjob` + `cron/scheduler.py`, `blueprint_catalog`, `suggestions` | **Growth loops that run without you.** Cron jobs can be scoped to toolsets to cut token cost |
| **Parallel fan-out** | `delegate_task` (incl. `background=true`), `async_delegation` | 100 prompts / 50 pages / 20 competitors at once. No recursive delegation |
| **Generative media** | `image_gen` (fal, xai, krea, openai, deepinfra, openrouter), `video_gen`, `tts`, `xai_video_edit/extend`, `vision_analyze`, `video_analyze` | **The moat. Only ImagineArt can make the artifact, not just the copy.** |
| **Code + shell** | `execute_code`, `terminal`, `read_terminal`, `file`, `patch`, `project_*` | Can build and ship real software |
| **Memory / learning** | `memory`, `session_search` (FTS5), `context_engine`, Honcho user modeling, self-authoring `skills` | Gets better at your niche over time |
| **Ops surface** | `kanban_*` (create/block/comment/attach/complete), `todo`, `open_preview` | A visible work queue — *demos beautifully* |
| **Multi-channel delivery** | Gateway: Telegram, Discord, **Slack**, **WhatsApp**, Signal, weixin, CLI | Human-in-the-loop approvals where the team already is |
| **Extensibility** | MCP + `mcp_oauth`; optional MCPs for n8n, Linear, Blender, Unreal | Plugs into existing stacks |
| **Pre-built skills** | 13-skill **LinkedIn suite** (post-writer, humanizer, hook-extractor, thread-monitor, engager-analytics, repurposer, comment-drafter, claim-check, reply-handler, profile-optimizer, content-planner, employee-advocacy), `xurl` for X, email, github | Content distribution partly solved out of the box |

**The combination that nothing else has:** browser automation + cron + parallel subagents + *generative media* + multi-channel human approval, in one runtime with memory.

Every growth tool on the market can write text. **This one can produce the proof.**

---

## 3. Market research — what's crowded, what's open

### GEO / AI search visibility → **crowded, and monitoring-only**
- Market: **$1.01B (2025) → $1.48B (2026) → $17.02B (2034)**, 45.5% CAGR.
- **92% of marketers plan to optimize for AI search; only 40.6% actually do.**
- AI platform visits **+70% YoY** (Jun 2025 → May 2026).
- At least **10 tools** already: Profound, AthenaHQ, Peec AI, Otterly.ai, Knowatoa, Scrunch AI, Brandlight, Goodie AI, + Ahrefs Brand Radar and Semrush AI Toolkit.
- Consensus: GEO is **"80% strategic, 20% technical."**

> **The gap:** all ten *measure*. They hand you a visibility score and stop. None of them **close the loop** — diagnose *which source* an LLM cited, manufacture the missing citation-worthy artifact, publish it, then re-measure. A dashboard is a commodity in this category now.

### Community / Reddit distribution → **high intent, hostile to automation**
- **r/SaaS now bans promotional and ad-generation SaaS outright.** Reddit punishes anything that reads unnatural; agencies treating it as a channel get clients banned.
- What works: value-first, numbers + method, zero pitch. Native participation.
- Practitioner subs worth targeting: r/AgentLLM, r/LangChain, r/LocalLLaMA, r/cursor, r/ClaudeAI, r/Automate.
- 2026 pattern: *"the teams that win aren't sending more emails — they're running networks of agents handling outreach, publishing and follow-ups."*

### Comparable agentic-builder growth
- **Lovable:** $100M ARR in 8 months; ~$13.3B valuation, $400–500M ARR by Aug 2026.
- **Replit:** ~$525M ARR, targeting $1B by end of 2026; 85% of Fortune 500 have employees on it.
- **Replit's actual moat was distribution, not model quality** — no-install browser environment, multiplayer, a free tier with real compute, and early dominance in India/Pakistan/MENA/Africa while Western tools ignored those markets.

### ImagineArt's own position
Competing against Canva, Midjourney, Leonardo, TESS AI, Simplified, AKOOL — **40+ serious competitors** by early 2026. Commodity model quality, brutal SEO competition. Distribution, not capability, is the constraint.

---

## 4. Strategic thesis for winning this

Four things separate a winning hackathon build here from a competent one:

1. **Use primitives nobody else will touch.** Most entries will be "a chat UI that calls an LLM." That scores ~5/10 on Technical Depth. Cron + `delegate_task` fan-out + `browser_cdp` + generative media in one loop scores 10/10 — and is only possible *because* it's Imagine Computer. It also satisfies the "IC must be core" rule structurally, not cosmetically.
2. **Generate proof, not copy.** ImagineArt's asset is that it can *make the thing*. A growth product that outputs an actual image/video/site as the growth artifact is defensible; one that outputs text is not.
3. **Solve a problem ImagineArt visibly has.** Scores twice — Impact *and* Storytelling. Judges are almost certainly the founders.
4. **Demo must show the machine running, not a result.** The kanban board + Slack approvals make autonomy *visible*. A static dashboard screenshot does not.

**Avoid:** another GEO tracker, another "AI writes your blog posts," another analytics dashboard, another chat wrapper. All four will be in the room.

---

## 5. Ranked concepts

### 🥇 #1 — "Everywhere Engine": the Distribution Compiler

**Thesis:** *In 2026 you don't win by getting users to your site. You win by being inside the tools they already have open.*

An agent that takes a product's API and **compiles it into new host-app surfaces automatically** — Figma plugin, Framer plugin, Chrome extension, WordPress plugin, n8n node, Zapier app, Shopify app, Discord bot, MCP server, VS Code extension — each one a listing in a marketplace that has its own organic search traffic.

**Why this is credible, not hypothetical:** this repo already contains **7 hand-built integrations** — After Effects, Premiere, Figma, Framer, WordPress, n8n, MCP (+ auth) — plus researched specs for Shopify, Zapier and Make in `docs/integrations/`. Months of manual work, proven valuable. **The build automates exactly that.**

**Pipeline:** ingest API spec → `delegate_task` fan-out, one subagent per target host → each researches the host's plugin API (`web_search` + `web_extract`) → scaffolds and builds in an isolated workspace (`terminal`, `execute_code`, `file`) → generates icon/screenshots/demo video (`image_gen`, `video_gen`) → writes the listing copy → `browser_cdp` drives the marketplace submission → cron re-checks review status and reports to Slack.

| Rubric | Score | Note |
|---|---|---|
| Technical Depth | 10 | codegen, OAuth, packaging, marketplace automation, parallel builds |
| Originality | 9 | "distribution compiler" isn't a category yet |
| Product & UX | 7 | builder console + build matrix |
| Growth Potential | 9 | each marketplace = an organic discovery channel with its own search |
| Business Impact | 9 | proven internally; sellable to every AI-API company (Fal, ElevenLabs, Replicate) |
| Demo | 9 | "watch it ship a working plugin in 6 minutes" |

**Risks & mitigations**
- *Marketplace review latency* — you can't get a Figma listing approved live. **Demo an instant-publish target**: n8n community node (npm), Chrome unpacked, or Framer dev mode. Show the others as submitted/pending.
- *"Is this growth or dev tooling?"* — frame relentlessly as distribution surface-area. Product-led growth is a listed challenge area; marketplace presence is textbook distribution.
- Target user must be stated as **AI product companies capped by being a destination website**, not "our team."

---

### 🥈 #2 — "Intercept": proof-driven demand capture

**Thesis:** Show up at the moment of intent with the thing they asked for, already made.

1. **Listen** — cron + `browser` + `web_search` + `x_search` sweep Reddit, X, YouTube comments, Quora, G2 and AI-answer prompts for buying intent in the category.
2. **Qualify** — score intent × reach × recency, and **rule out** by subreddit rules and promo bans (this is the judgment that keeps it out of spam territory).
3. **Prove** — actually *do the thing they asked for* with ImagineArt's models. Someone asks "can any AI do X?" → the agent generates X.
4. **Approve** — draft a native, value-first reply with the artifact; human approves from **Slack/WhatsApp** via the gateway.
5. **Attribute** — unique tracked link per reply → clicks → signups.
6. **Compound** — winning replies get repurposed by the LinkedIn skill suite into posts, threads and a how-to page.

| Rubric | Score | Note |
|---|---|---|
| Technical Depth | 8 | |
| Originality | 8 | inline proof generation is unique to ImagineArt |
| Product & UX | 9 | approval inbox is a real product |
| Growth Potential | 9 | direct, attributable acquisition |
| Business Impact | 8 | |
| Demo | **10** | live thread → generated proof → Slack approve → tracked click. Most visceral option. |

**Risk:** platform ToS and spam optics. **Must** be human-in-the-loop, rule-aware, and demoed on owned channels or a sandbox. Handled well, the compliance layer becomes evidence of product judgment — which judges reward.

---

### 🥉 #3 — "Answer-Engine Closer": GEO that acts

The only GEO product that closes the loop: measure citation share → identify *which URLs* the LLM actually cited → diagnose why competitors win them → manufacture the missing artifact (comparison page, data study, free tool, reference entry) → publish → re-measure weekly via cron.

Strong on Growth (9) and Depth (8) but **Originality drops to ~6** — the category has ten players and judges will pattern-match to "another visibility tool." **Demo is the real weakness: SEO lift isn't demoable in real time.** Only viable if built early enough to show a genuine week-over-week before/after.

---

### Considered and set aside
- **pSEO free-tool factory** — hundreds of micro-tools as landing pages. Real mechanic (remove.bg, Canva) and IC can build sites, but reads as mass-generated content; Google is punishing it; visually boring to demo.
- **"AI Growth Employee"** — duplicates `ai-employees-v2`, already built internally.
- **Share-your-output viral loop** — needs real user data to be non-hypothetical.

---

## 6. Recommendation

**Build #1 (Everywhere Engine). Steal #2's demo discipline.**

It wins on the two rubric lines that actually decide hackathons — Originality and Technical Depth — it's grounded in work already proven valuable inside the company, and Ashad has the deepest possible domain credibility on it (7 of these built by hand).

**Pick #2 instead if** the priority is the single most visceral 3-minute demo, or if marketplace publishing turns out to be too slow to show live.

### Demo script (3 min)
1. **The problem, in one line** — "We have 3.5M MAU and we're still a website people have to remember to visit. Our competitors are already inside Figma, Canva and Photoshop." Show the 7 hand-built plugins: *"these took months."*
2. **The ask** — paste the ImagineArt API spec, name a host app never built for.
3. **The machine** — kanban board fills live; subagents fan out; terminal builds; icon and demo video generate.
4. **The payoff** — a *working* plugin, installed and running, generating a real image inside the host app.
5. **The loop** — Slack message: submission status, review ETA, listing traffic. "This runs every week without me."
6. **The business** — every AI API company has this problem. Marketplace listings are search surfaces we don't own yet.

### Open questions to settle before building
- Which host app for the live demo? Needs instant publish — n8n community node, Chrome unpacked, or Framer dev mode.
- Solo or squad (max 4)?
- Do we demo against ImagineArt's own API, or a neutral third-party API to prove generality?

---

## Sources

- [ImagineArt Moves from Generative AI to Agentic AI with Imagine Computer — GlobeNewswire](https://www.globenewswire.com/news-release/2026/08/06/3340654/0/en/imagineart-moves-from-generative-ai-to-agentic-ai-with-imagine-computer.html)
- [Same release — Yahoo Finance](https://finance.yahoo.com/technology/ai/articles/imagineart-moves-generative-ai-agentic-082000182.html) · [AI Magazine](https://aimagazine.com/globenewswire/3340654) · [Manila Times](https://www.manilatimes.net/2026/08/07/tmt-newswire/globenewswire/imagineart-moves-from-generative-ai-to-agentic-ai-with-imagine-computer/2400469)
- [Imagine Computer — product page](https://www.imagine.art/imagine-computer)
- [What Is Imagine Computer? — ImagineArt blog](https://www.imagine.art/blogs/what-is-imagine-computer)
- [GEO Services Market Outlook 2026–2034 — Intel Market Research](https://www.intelmarketresearch.com/generative-engine-optimization-services-market-36546)
- [AI Search Visibility Tools 2026: 10 Compared & Priced — Industry Lens](https://industry-lens.com/intelligence/ai-search)
- [GEO Statistics 2026 — Omnibound](https://www.omnibound.ai/blog/generative-engine-optimization-statistics)
- [AI answer-engine visibility becomes a measurable discipline — MarketScale](https://www.marketscale.com/industries/marketing-tech/ai-answer-engine-visibility-becomes-a-measurable-discipline-as-geo-platforms-multiply-in-2026)
- [GEO, AEO and SEO in 2026 — Writer](https://writer.com/blog/geo-aeo-optimization/)
- [Mastering generative engine optimization in 2026 — Search Engine Land](https://searchengineland.com/mastering-generative-engine-optimization-in-2026-full-guide-469142)
- [Replit's Growth Playbook: $2.5M to $250M ARR — Startup Riders](https://www.startupriders.com/p/replit-growth-playbook)
- [Replit vs Lovable vs Bolt.new: $4.3B Valuation Gap — Tech Insider](https://tech-insider.org/replit-vs-lovable-vs-bolt-new-2026/)
- [Best Subreddits for AI Marketing in 2026 — Linkeddit](https://linkeddit.com/blog/best-subreddits-for-ai-marketing-2026)
- [Best Reddit Marketing Agencies for SaaS 2026 — Growthner](https://growthner.com/blog/best-reddit-marketing-agencies-for-saas/)
- [ImagineArt competitors — G2](https://www.g2.com/products/imagineart/competitors/alternatives)

**Internal (read-only):** `cloud-computer/{toolsets.py,tools/,skills/,plugins/,gateway/,cron/}`, `cloud-computer/ai-teams-FE/README.md`, `cloud-computer/ai-employees-v2/README.md`, `video-editor/imagine-computer-web/README.md`, `imagine-art-film-studio-beta/{*-plugin,imagine-mcp,docs/integrations}`, `atlas/atlas-automation-tool`.
