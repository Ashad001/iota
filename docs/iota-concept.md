# IOTA — concept on Sapphire

**Team:** IOTA — *Interrupt Only To Approve*
**Positioning:** an autonomous growth team that lives in your notch
**Surface:** Sapphire (macOS notch app, AGPL-3.0, fork `Ashad001/Sapphire`, upstream `cshariq/Sapphire`)
**Engine:** Imagine Computer / Hermes
**Compiled:** 2026-08-26

---

## Alignment with the brief

**Hits four listed areas:** marketing automation, content distribution, customer acquisition, automation.

**Risk:** framed as "an ambient approval surface," this reads as a productivity/ops product and invites the question *"where's the growth?"*

**Fix — framing, not rebuild.** Lead with **"an autonomous growth team that lives in your notch."** Every agent in the demo must be a visibly *growth* agent: lead-finding, community replies, ad creative, published pages. The product is growth; ambient approval is the mechanism that lets it ship.

**Open risk — the build-environment rule.** The brief requires Imagine Computer to be *the core environment used to build*. Sapphire needs Xcode on macOS; if the hackathon's IC credits run in a Linux cloud container, **it cannot compile the Swift app.** Verify early. Mitigation: keep the bulk of the product on the IC side (agent fleet, orchestration, bridge service) with the notch as a thin client, and have IC author the Swift even where compilation happens locally.

---

## The growth problem

Autonomous growth agents in 2026 are mostly theater, and **the reason is not model capability — it's approval latency.**

Every serious agent deployment hits the same wall. An agent drafts a reply, a post, an outreach email, a landing page. A human must approve it. That means: notification → open dashboard → load context → read → decide → click. Call it 4–8 minutes of human attention per item, most of it spent *re-loading context the agent already has*.

So throughput collapses to human attention, and teams pick one of two failure modes:

1. **Don't run the agents.** The fleet becomes a demo that never ships work.
2. **Run them unsupervised.** This produces the spam that got promotional SaaS *banned outright from r/SaaS* and gets accounts killed across Reddit, LinkedIn and cold email.

Both are distribution failures. The industry response has been to build more dashboards — but a dashboard is precisely the thing that costs the 4–8 minutes. **You cannot fix an attention bottleneck with a destination you have to visit.**

> **The bottleneck is approval latency. The fix is an ambient approval surface — one that costs a glance, not a context switch.**

---

## The product

**IOTA turns the notch into the control surface for an autonomous growth team.**

Imagine Computer runs the agents. Sapphire's notch is their face — always visible, above every app, never stealing focus.

| Stage | What happens | Powered by |
|---|---|---|
| **Work** | Agents run unattended — monitor mentions, research competitors, draft posts, generate creative, build pages | `cronjob`, `delegate_task(background=true)`, `web_search`, `browser_cdp` |
| **Surface** | Ambient status in the notch. Quiet when fine; a pulse when something needs a human | Sapphire `LiveActivityManager` |
| **Decide** | Glance shows the artifact itself — the actual image, the actual post. Approve or reject with one gesture | Hermes `approval.request` over `/api/ws` |
| **Create in place** | The notch sees what you're working on and offers the asset *before you go looking* | `AskScreen` capture + `vision_analyze` + `image_gen` |
| **Report** | Attributed result comes back to the same surface — clicks, signups, citations | `kanban_*`, `memory` |

### Why the technical fit is unusually good

Sapphire already solved the hard part. `LiveActivityManager` runs ~30 `checkForX() -> (ActivityType, LiveActivityContent, TimeInterval?)?` probes and displays the **highest-priority hit** from an explicit integer ranking (`music = 10` … `systemHUD = 100`, `intelligenceAgent = 120`).

That is an **ambient attention-ranking engine** — exactly what an agent fleet needs so twelve agents don't shout at once. Adding IOTA is one new `ActivityType` at the top of the priority ladder plus a `checkForAgentApproval()` probe. The ranking, the animation, the focus-safety and the display arbitration already exist and are battle-tested.

Meanwhile Hermes already emits `approval.request` as an unsolicited event frame over the WebSocket. **Both halves of the handshake exist.** The build is the bridge, not the primitives.

Extension points are documented in `docs/architecture-study.md` §4: `LiveActivityType` (`SettingsModel.swift:1610`) + `ActivityType` + two mapping inits + a `checkForX()` + a view in `LiveActivityComponents.swift`.

---

## Target users

**Primary** — growth and marketing teams deploying agent fleets. The person who owns "we're going to run 20 agents" and discovered the agents now need a full-time babysitter. They have the agents; they can't afford the attention.

**Secondary** — solo founders and indie makers doing growth alongside the actual job. They will never open a growth dashboard because they are already in Xcode, Figma or a Google Doc. Ambient is the only surface they will ever actually use.

**Third** — anyone running Imagine Computer at all. The approval bottleneck isn't specific to growth; it's specific to *agency*. Growth is where it bites first because volume matters most there.

---

## Measurable impact

The metric is **agent throughput per human-hour**, and it decomposes cleanly:

- **Median time-to-approval** — dashboard baseline is minutes-to-hours (notification → visit → context). Target: seconds.
- **Approval rate** — how many queued items actually get decided vs. rot in a queue.
- **Items shipped per week** — posts, replies, pages, creatives.
- **Attributed downstream** — clicks and signups per approved item, tracked per link.

The demo can show the first two live. The others need a week of running, which is worth starting before Friday.

---

## Demo script (3 min)

1. **The problem, physically.** Open a real agent dashboard. Start a stopwatch. Narrate the context-reload. *"This is four minutes, and I have twelve of these today."*
2. **Switch to the notch.** Agents are running — ambient, quiet, unobtrusive. You're working in another app the whole time.
3. **The pulse.** Notch expands: an actual generated ad creative, the target thread, the draft copy. One glance = full context.
4. **The gesture.** Approve. It ships. Never left the app, never lost focus.
5. **The loop.** 30 seconds later the notch reports the tracked click.
6. **The scale.** *"Twelve approvals took ninety seconds. In a dashboard that's an hour. That's the difference between a fleet that ships and a fleet that's a screenshot."*

---

## Honest flags

**AGPL-3.0 is the real strategic constraint.** Sapphire is AGPL with the §13 network clause. A fork that ImagineArt distributes must also be AGPL — ImagineArt cannot ship this as proprietary software built on this codebase. Three honest paths:

1. **Contribute upstream.** The integration lands in Sapphire as AGPL. This is legitimate distribution — ImagineArt gets into an open-source Mac app that already has users, a Discord and a release channel. It is exactly the IOTA thesis, and it is the cleanest option.
2. **Build a clean-room notch surface.** More work, fully ownable, no license entanglement.
3. **Arm's-length separate process.** Legally grey. Do not bet a product on it.

For the hackathon, path 1 is correct and honest — and worth saying out loud to the judges rather than letting them discover it. "We know the license; here's how we'd ship it" is a point *for* you on business judgment.

**Sapphire is not ours.** Upstream is `cshariq/Sapphire`. Any real plan involves that maintainer. Worth naming in the demo.

**Scope discipline.** The pre-intent creative feature (stage 4) is the crowd-pleaser but the approval loop (stages 1–3, 5) is the actual product. If time compresses, ship the loop and demo creation as a stretch.

---

## Alternatives considered

- **Ambient growth analytics in the notch** — metrics always visible. Cute, but it is a dashboard in a smaller box. Low originality; judges will pattern-match instantly.
- **Notch as pure creative surface** — drop an image, get it enhanced. Good UX, but it's a feature, not a growth product, and doesn't answer "what growth problem?"
- **Growth engine for Sapphire itself** (stars, Discord, downloads) — real, but niche audience and weak business case for ImagineArt.
- **Screen-aware pre-intent creation as the headline** — strong "wow" and directly an ImagineArt distribution play ("zero-search-intent distribution"), but privacy optics need care and the growth thesis is softer than the approval-bottleneck one. Better as a module than the headline.

---

## Source notes

Internal, read-only: `Documents/ashad001/saphire/saphire/` — `docs/architecture-study.md`, `Sapphire/Services/AskScreen/AskScreenService.swift` (417 lines, OpenRouter streaming), `Sapphire/Widgets/AskScreen/`, `LICENSE` (AGPL-3.0), `README.md`, git remotes. Hermes surface per `docs/buildathon-research.md`.
