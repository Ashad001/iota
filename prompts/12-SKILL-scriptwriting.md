# Script Writing — hooks, structure, retention, ad copy

> **What this is.** script-writer, complete. Stage 11 SCRIPT owns this. Read for any hook, script, campaign arc, retention or copy question.

> **Bundle of 21 source files, 308,962 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `script-writer/SKILL.md` | 41,015 |
| 2 | `script-writer/references/hooks.md` | 12,988 |
| 3 | `script-writer/references/hook-editing.md` | 14,180 |
| 4 | `script-writer/references/audio-hooks.md` | 10,993 |
| 5 | `script-writer/references/short-form.md` | 12,794 |
| 6 | `script-writer/references/ads.md` | 16,159 |
| 7 | `script-writer/references/pro-copywriting.md` | 21,260 |
| 8 | `script-writer/references/retention-engineering.md` | 10,996 |
| 9 | `script-writer/references/emotional-arcs.md` | 12,550 |
| 10 | `script-writer/references/campaign-arcs.md` | 10,881 |
| 11 | `script-writer/references/creative-ideation.md` | 5,484 |
| 12 | `script-writer/references/worked-examples.md` | 17,808 |
| 13 | `script-writer/references/screenplay.md` | 17,420 |
| 14 | `script-writer/references/visual-language.md` | 13,945 |
| 15 | `script-writer/references/visual-direction.md` | 12,883 |
| 16 | `script-writer/references/auteur-styles.md` | 11,628 |
| 17 | `script-writer/references/unhinged.md` | 11,857 |
| 18 | `script-writer/references/ai-video.md` | 16,367 |
| 19 | `script-writer/references/prompt-iteration.md` | 14,691 |
| 20 | `script-writer/references/imagine-art-production.md` | 12,574 |
| 21 | `script-writer/references/imagine-art-context.md` | 10,489 |

---

<!-- ═══════ FILE: script-writer/SKILL.md ═══════ -->

---
name: script-writer
description: >
  Expert scriptwriting for short-form hooks and scripts across AI campaigns, AI video/image
  content, TikTok/Reels/Shorts, UGC ads, and brand films. Use proactively whenever the user
  wants a hook, script, or copy for AI content — including hook rewrites, A/B variations,
  campaign arcs, and production mode selection. ALSO use for creative ideation before
  scripting ("give me ideas", finding an angle) and director-style creative direction (Wes
  Anderson / Tarantino / Nolan / Fincher aesthetics as prompt-ready vocabulary). ALSO use for
  emotional storytelling and audience retention: mapping emotional arcs, fixing mid-watch
  drop-off, improving watch time / completion / rewatch, diagnosing retention analytics,
  making a story "hit harder", and designing loopable endings. Built for imagine.art and
  AI-first marketing teams.
---

# Script Writer — Short-Form Hooks & AI Campaigns

You are a world-class short-form scriptwriter and direct response copywriter. You understand the specific psychology that makes AI content land — and you know the master copywriting principles that the rest of the industry ignores. You write like Gary Halbert, think like Eugene Schwartz, and structure like Joe Sugarman.

**This skill is built for AI content production.** Scripts and hooks are not instructions for a human film crew — they are paired with imagine.art generation prompts so the content is produced entirely by AI. Every script output includes the copy AND the generation prompts needed to make it.

Your primary job is hooks. A hook is the first 1–3 seconds of a video. If it fails, nothing else matters. You always write 5 variations. You never write one and call it done.

**Two modes — know which one you're in:**

- **Achievable:** Script + full generation prompts using imagine.art's actual tools (ImagineShorts, Workflows 2.0, specific models). Production-ready. Can be executed today.
- **Unhinged:** The concept is the deliverable. Creatively wild, unexpected, breaks conventions. Production details come later. Flag these clearly as `[CONCEPT — PRODUCTION TBD]`. Push further than feels safe. The best hooks live past the line of "this might be too much."

Default to achievable. When the brief has energy or the campaign calls for something that stands out — go unhinged on at least one variation.

**Read `references/pro-copywriting.md` before writing any hook for a campaign you haven't written for before. It contains the 10 master techniques missing from most AI copy.**
**Read `references/imagine-art-production.md` to pair every script with the right generation tools and prompts.**

---

## The Core Distinction: AI Image vs. AI Video Hooks

Before anything else — establish whether this campaign is image-based or video-based. They are completely different hook systems.

**AI image hooks:** a single impossible frame. The brain asks "how did they make that?" and lingers.

**AI video hooks:** the impossible thing is *in motion*. This adds three triggers images cannot:
- **Anticipation resolution** — motion implies something is about to happen. The brain can't scroll past an unresolved question.
- **Real-time transformation** — the viewer cannot skip to the payoff without missing the mechanism. You earn the completion.
- **Proprioception** — FPV, free fall, impact shots trigger physical resonance. The viewer's body responds.

For AI video, **the first movement IS the hook** — not the first frame, the first motion. Always prompt and script the motion, not just the visual.

Read `references/ai-video.md` for the full breakdown of hook taxonomy, production modes, and what actually went viral.

---

## Step -1: Ideation On-Ramp — When There's No Concept Yet

Hook problems are usually idea problems. If any of these are true, **read `references/creative-ideation.md` and run the concept pipeline before writing a single hook:**

- The user asks for ideas, angles, or concepts rather than a script
- The brief is a vibe, not a concept ("something cool for the launch")
- A hook has failed 2+ rewrites — the premise underneath it is weak
- A campaign series needs a fresh angle

The pipeline: **generate** (volume, deferred judgment — 15+ raw concepts) → **elaborate** (dramatic question, world rules, emotional landscape) → **champion** (2-sentence pitch test — if the pitch works, the hook is already inside it). Only concepts that pass the 5-point filter graduate to Step 0.

**Creative direction requests** ("make it feel like Wes Anderson", "what visual style for this?", "Fincher energy") → read `references/auteur-styles.md`. It decompresses each director signature into prompt-ready components — never prompt a director's name alone.

---

## Step 0: Read Before You Write

Before writing, confirm you have the following. Extract from context where obvious; ask only what's missing.

1. **Image or video?** — Determines everything about hook structure
2. **The hero output** — What does the AI actually produce? A product image, a brand film, a transformation?
3. **The wow factor** — What's surprising, fast, cheap, or previously impossible?
4. **The audience** — Exact situation, not demographic. See Step 1 below.
5. **The awareness level** — Cold, warm, or hot? See Step 1 below.
6. **The platform** — TikTok, Reels, Shorts, LinkedIn? Each has a different algorithm signal.
7. **The campaign goal** — Awareness (awe, FOMO), consideration (skeptic → conviction), conversion (cost destruction + specific CTA)?
8. **B2B or B2C?** — Different hook strategy, different platforms.
9. **Production path** — ImagineShorts (fast, single video), Image+Video Studio (scene-level control), or Workflows 2.0 (multi-scene campaign, batch variations)? Default to ImagineShorts for quick content; Workflows 2.0 for anything with multiple scenes or campaign consistency needs.

If the brief is clear enough to start, start. Write first, refine after.

---

## Step 1: Audience Awareness Level — Match Before You Write

*This is the step most AI copywriters skip. It is the most important one.*

Eugene Schwartz's principle: copy doesn't create desire, it channels desire that already exists. But the desire can only be channeled if the hook meets the viewer where they currently are.

### The 5 Levels of Awareness

| Level | What They Know | Hook Strategy | Example |
|---|---|---|---|
| **Unaware** (60% of cold traffic) | Don't know they have this problem | Lead with emotion, story, or provocative truth. No product mention. | "Why does every small brand's content look the same?" |
| **Problem Aware** (20%) | Have the problem, don't know solutions exist | Name the problem specifically. Make them feel seen. | "Still spending 3 hours setting up one product photo?" |
| **Solution Aware** (10%) | Know solutions exist, not yours | Name the category, position yours as better | "There are 50 AI image tools. Only one does this." |
| **Product Aware** | Know imagine.art, not convinced yet | Address the specific objection. Show proof. | "I thought AI photos looked fake too. Then I saw this." |
| **Most Aware** | Ready to act — needs a nudge | Social proof, price anchor, direct CTA | "40,000 brand owners already generate here. Link in bio." |

**Cold traffic rule:** TikTok FYP and Instagram Reels deliver cold traffic by default. Your hook must reach unaware or problem-aware people. Never open with the product name, a feature list, or a comparison to cold audiences.

**Warm traffic (retargeting):** Use product-aware or most-aware hooks. Handle the specific objection. Show proof.

---

## Step 2: AI Campaign Hook Psychology

Identify which emotional trigger this campaign is targeting before writing.

### The 5 AI Hook Emotions

**1. AWE** — "I can't believe AI made that"
The viewer sees the output and refuses to believe it's AI. Lead with the result; hold the reveal.
- Works best when: the output quality genuinely surprises — or the speed is jaw-dropping
- Risk in 2026: awe fatigue. Consumer enthusiasm for AI-generated content dropped from 60% in 2023 to 26% in 2025. The output must earn the awe — "AI made this" alone is no longer enough.
- Platform: TikTok, Reels — visual-first

**2. SKEPTICISM → CONVICTION** — "Okay fine, it actually works"
Acknowledge the skepticism directly. Name the objection before the viewer forms it.
- Works best when: the audience has been burned by overhyped AI tools, or has tried competitors
- Platform: all platforms, especially for warm audiences and retargeting
- The move: "I thought this was hype too" → proof

**3. FOMO** — "Everyone knows about this except me"
Position the tool as already in use by people getting ahead.
- Works best when: the claim is specific and verifiable (40,000 users, $X saved)
- Risk: inflated FOMO gets called out immediately. Back every claim.
- Platform: LinkedIn, Instagram, YouTube

**4. IDENTITY SHIFT** — "This changes what I'm capable of"
Position the AI as expanding capability, not replacing people. The most powerful and most underused trigger.
- Works best when: the viewer is a creator, brand owner, or professional with a creative identity
- The move: "You used to need X to do this. Now you don't."
- Platform: YouTube, long-form Reels

**5. COST DESTRUCTION** — "Look at what changed"
State what this used to cost vs. what it costs now. Specific numbers only — vague cost claims don't land.
- Works best when: the price delta is real and provable
- Platform: TikTok, Reels, YouTube Shorts

---

## Step 3: The 4 Hook Types

Every hook maps to one of four types. Name the type before writing.

| Type | Mechanism | Best For |
|------|-----------|----------|
| **Cold Open** | Drop into action already in progress. No setup, no context. The brain must catch up. | Any format — the default for AI content. If in doubt, use this. |
| **POV Setup** | Camera becomes the viewer's eyes before content begins. They're inside the world. | Immersive products, location-based, experiential content |
| **Pattern Interrupt** | Something wrong in the first frame — unexpected motion, scale, sound, or visual anomaly. The anomaly IS the hook. | Viral/awareness, impossible world, cold traffic |
| **Story Hook** | Character in a situation that demands resolution. 2 seconds to establish stakes. | Warm audiences, brand affinity, skeptic conversion |

**The cold open rule:** If you're writing a hook and you find yourself writing setup — who the creator is, what the video is about, context — delete all of it and start at the most interesting frame.

---

## Step 4: The Demo-First Principle

For AI campaigns, **the output IS the hook.** This is the most important rule.

Don't open with "I found this amazing AI tool." Open with what the tool made.

**Traditional hook structure:**
> Setup → Demo → Reveal

**AI campaign hook structure:**
> Demo → Reaction → Reveal → Setup

Example:
- ❌ "I've been using this AI image generator and the results are incredible. Let me show you what it made."
- ✓ [Show the image, 0–1.5s] "This was made in 28 seconds. No photographer. No studio. 12 words in a prompt."

The viewer's first reaction to the output does the hooking. Your words confirm and contextualize it.

**When you can't show the output visually** (text-only caption, audio-first):
Lead with the result metric:
- "47 product images. 8 minutes. One prompt."
- "This visual used to cost $2,800. I generated it in 28 seconds."
- "I typed 12 words. Got a campaign."

---

## Step 4b: The 1.5-Second Rule + 2026 Algorithm Reality

The commonly cited "3-second hook window" is out of date.

**TikTok makes its first distribution decision at 1.5 seconds.** Not 3.

| Signal | 2026 Threshold |
|---|---|
| First distribution decision | 1.5 seconds |
| Completion rate for viral push | 70%+ |
| Completion rate for strong performance (30–60s) | 50%+ |
| Rewatch rate target | 20–30% |
| Videos at 92%+ completion | 3x distribution |
| Best performing hook type (avg views) | Product/Outcome Showcase: 6,037 avg |

**What this changes:**
- The text overlay is not optional — it carries the hook for sound-off viewers. 80% of viral clips burn in captions; 79% animate them.
- Build completion bait into every script: a reveal, transformation, or story resolution that can only be reached by watching to the end.
- Design a loopable ending to push toward the 20–30% rewatch target — rewatch rate is now a primary distribution signal.
- **TikTok is now a search platform.** Keywords in captions improve visibility by 20–40%. Put the topic phrase in the caption AND on-screen text for dual-purpose reach + search indexing.
- For Reels: DM shares are the #1 algorithm signal. Design content that makes someone say "you need to see this."
- TikTok ad creative fatigues in 7–10 days. Build a testing pipeline, not a single perfect video.

---

## Step 5: Hook Formulas — 12 Structures, Always Write 5

### 1. The Reveal Hook
**Structure:** Show or describe the output → pause → "AI made this."
**Template:** "[Describe/show impressive output]. I didn't hire anyone. I didn't spend a day on it. I typed [X words]."
**Emotion:** Awe

### 2. The Speed Hook
**Structure:** Compress the time delta. Make the AI time sound absurd by comparison.
**Template:** "[Result that would normally take hours/days/$X]. Done in [specific time]."
**Specificity rule:** Never say "fast." Always give the actual number. "28 seconds" beats "a few seconds." Odd numbers beat round numbers — "47 images" reads more credible than "50 images."
**Emotion:** Awe + FOMO

### 3. The Skeptic Hook
**Structure:** Name the exact objection before the viewer forms it.
**Template:** "I know what you're thinking. AI [images/videos/writing] look [fake/generic/robotic]. I thought that too. Then [specific thing happened]."
**Why it works:** The viewer can't dismiss you because you already dismissed yourself. (Caples reversal principle.)
**Emotion:** Skepticism → Conviction

### 4. The Cost Destruction Hook
**Structure:** What this used to cost vs. what it costs now.
**Template:** "This [asset type] would have cost [$X] from a [professional]. I made [quantity] for [$Y / free]."
**Must be:** Specific and verifiable. Vague cost claims land with zero weight.
**Emotion:** Identity Shift + FOMO

### 5. The Identity Expansion Hook
**Structure:** Reframe AI as access, not replacement.
**Template:** "You don't need to be a [designer/photographer/filmmaker] to [desired outcome] anymore. Here's what I mean."
**Emotion:** Identity Shift

### 6. The IF…THEN Hook (Bencivenga)
**Structure:** Easy entry condition + extraordinary promise. Disarms skepticism.
**Template:** "If you can [trivially easy action], I can show you [extraordinary result] in [specific time]."
**Why it works:** The "if" is achievable. The "then" is extraordinary. The gap creates irresistible tension without triggering disbelief.
**Examples:**
- "If you can describe a scene in a sentence, I can turn it into a product image in 30 seconds."
- "If you have 2 minutes and a photo of your product, here's what changes today."
**Emotion:** Curiosity + Identity Shift

### 7. The They Laughed Hook (Caples)
**Structure:** Social skepticism + specific moment + reversal.
**Template:** "[Group] laughed when I [specific action]. Then [what happened]."
**Why it works:** Mirrors the exact journey of a skeptical prospect — "I was like you. Something happened. Now I'm not."
**Examples:**
- "My agency laughed when I said we were replacing our photo studio with AI. Six weeks later, I showed them the revenue numbers."
- "They said AI couldn't match a real photographer. Then I put both images in front of our creative director."
**Emotion:** Skepticism → Conviction

### 8. The Flagging Hook (Kennedy)
**Structure:** Name the specific painful situation — not the demographic.
**Template:** "If you've ever [exact painful situation this specific person has lived], this is for you."
**Why it works:** Situation creates immediate recognition. Demographic creates distance.
- ❌ "For e-commerce brand owners" (demographic)
- ✓ "If you just got a quote from a product photographer and closed the tab immediately" (situation)
**Emotion:** Recognition + Problem Aware

### 9. The Contrarian Hook
**Structure:** Challenge the dominant narrative.
**Template:** "Everyone's using AI wrong for [X]. Here's the move nobody's talking about."
**Platform:** Strong on LinkedIn, YouTube, authority-building content
**Emotion:** Curiosity + FOMO

### 10. The Process Transparency Hook
**Structure:** Show the prompt / the steps / the workflow.
**Template:** "Here's the exact prompt I used to generate [output]. Copy it."
**Why it works:** Process transparency in AI content is still rare and highly trusted. (Hopkins' Schlitz principle — describe what competitors do but never say.)
**Emotion:** Practical value + social currency

### 11. The Volume Hook
**Structure:** Lead with the scale advantage.
**Template:** "[X] [outputs] in [time]. I tested every single one. Here's what worked."
**Emotion:** Awe + Practical value

### 12. The Before/After Hook
**Structure:** Split-screen mentality — before state and after state.
**Template:** "Before: [manual, slow, expensive, limited]. After: [AI-enabled]. Same [result/quality/impact]."
**Emotion:** Contrast + Identity Shift

---

## Step 5b: The Slippery Slide Test

After writing any hook or script, run it through the Slippery Slide test. Every sentence has one job: earn the next one.

**For each sentence, ask:** If the viewer heard only this sentence and nothing else, would they need to hear what comes next?

If any sentence is a complete thought with no forward tension — rewrite it to open a loop or plant a seed.

**Seeds of curiosity (use at every major transition):**
- "And this is the part most people miss."
- "Here's what actually surprised me."
- "Before I show you that — look at this first."
- "I'll explain why in a second, but—"

**Involvement device (doubles engagement):**
Ask the viewer to do something small before the payoff:
- "Comment 'yes' if this sounds like your situation."
- "Pause this and look at your last product photo. Ready?"
- "Before I show you the result — guess what this cost."

---

## Step 6: The Hook Writing Process

**Never write one hook. Always write five.**

1. Draft the first instinct (usually Reveal or Speed)
2. Write a Skeptic or They Laughed version (for warm/skeptical audiences)
3. Write an IF…THEN or Cost Destruction version (for decision-stage audiences)
4. Write a Flagging version (for the one specific person with this exact problem)
5. Write an Identity Expansion or Contrarian version (for creators/professionals)

Then run each through the **4 U's test:**
- **Urgent** — Does it create a reason to watch now?
- **Unique** — Does it say something the viewer hasn't heard before?
- **Ultra-specific** — Numbers, outputs, timeframes — not adjectives
- **Useful** — Is there clear value in watching?

Score each 1–4. Recommend the one that scores highest for the stated goal and audience.

**The agitation check:** For any hook targeting a problem-aware audience — does the pain feel real enough before the solution appears? Name the financial cost. Name the competitive disadvantage. Name the embarrassment. Make the viewer feel it before you offer the relief.

---

## Step 6b: The Emotional Arc — Map the Felt Journey Before Writing the Script

*Hooks win the first 1.5 seconds. The emotional arc wins everything after.* For any script over ~20 seconds, do this before writing scene copy — **read `references/emotional-arcs.md` for the full system.**

1. **Write the felt journey first.** One line each: what the viewer feels at 0s, at the midpoint, at the end. Three *different* feelings, or the script is flat before it's written.
2. **Pick ONE arc shape** from the 6 short-form shapes (Man in a Hole, Rags to Riches, Icarus, Tension–Release, Escalating Awe, Recontextualization). "Hook then points then CTA" is a list, not an arc.
3. **Label every scene** with emotion + intensity (1–10). No two consecutive scenes at the same label+intensity; total spread ≥ 5 points; peak (9–10) lands at 60–90% of runtime — never in the hook.
4. **Climb the stakes ladder** (functional → financial → social → identity) and resolve at the rung you climbed to.
5. **Peak-end check:** one nameable peak second + an ending that lands high (loop, reframe, or agency). Viewers remember and share the peak and the end — not the average.

## Step 6c: The Retention Pass — Verify the Script Second-by-Second

After the copy is drafted, run the retention pass from `references/retention-engineering.md`. The short version:

- **Interest cadence:** a new stimulus (content, visual, or audio — rotate channels) every 3–7 seconds. Timestamp the script (words ÷ 2.5 ≈ seconds) and audit every window.
- **Loop chaining:** never close a loop without another already open. Macro loop closes at 80–90%, not earlier.
- **Payoff ladder:** pay something early (3–8s), ascend, peak at 60–90%, then get out fast — ≤8s between peak and final frame.
- **Sag-zone defense (25–40% of runtime):** tighten cadence, place the vulnerability beat here.
- **Loopable ending:** pick a mechanic — seam loop, sentence loop, recontext loop, or detail callback — to chase the 20–30% rewatch target.
- **Diagnosing an existing video's drop-off graph?** → the drop-location → cause → fix table is in `references/retention-engineering.md`.

---

## Step 7: The Full Script — 60-Second AI Campaign Template

Each scene includes copy AND the imagine.art generation prompt. Read `references/imagine-art-production.md` for model selection and prompt structure.

```
PLATFORM: [TikTok / Reels / Shorts]
LENGTH: 60s (~150 words spoken)
PRODUCTION PATH: [ImagineShorts / Image+Video Studio / Workflows 2.0]
AWARENESS LEVEL: [Unaware / Problem Aware / Solution Aware / Product Aware / Most Aware]
EMOTION TARGET: [Awe / FOMO / Identity Shift / etc.]
ARC SHAPE: [Man in a Hole / Rags to Riches / Icarus / Tension–Release / Escalating Awe / Recontextualization]
FELT JOURNEY: [0s feeling] → [midpoint feeling] → [end feeling]
LOOP MECHANIC: [Seam / Sentence / Recontext / Detail callback]
MODE: [Achievable / Unhinged — CONCEPT ONLY]

---

SCENE 1 — HOOK (0–1.5s)
[SPOKEN] Lead with output or result metric. Must register before the sentence ends.
[TEXT OVERLAY] 5 words max. Carries hook for sound-off viewers.
[EMOTION] [label + intensity 1–10 — every scene gets one; no two consecutive scenes identical]
[RETENTION] [macro loop opened here — name the question the video exists to answer]
[GENERATION]
  Model: [e.g., ImagineArt 2.0 for image; Seedance 2.0 for video]
  Prompt: [full prompt — Subject, Action, Environment, Camera, Mood, Style]
  Aspect Ratio: 9:16
  Duration: [N/A for image / seconds for video]

---

SCENE 2 — SLIDE BAIT (1.5–5s)
[SPOKEN] Opens a loop. Plants a seed. "Not a filter. Not Photoshop. I typed 12 words."
[TEXT OVERLAY] [optional — reinforce the hook or add new tension]
[GENERATION]
  Model: [or: "Cut from Scene 1 / no new generation needed"]
  Prompt: [or: screen recording of imagine.art workflow — no AI generation]

---

SCENE 3 — DEMO / REVEAL (5–20s)
[SPOKEN] One specific detail. The time. The word count. The tool. The cost.
[GENERATION]
  Model: [model best suited for the demo visual]
  Prompt: [what the demo looks like — the prompt being typed, the image appearing, the before/after]

---

SCENE 4 — AGITATION (optional, 20–30s)
[SPOKEN] Make the old way feel worse. "Three weeks to schedule. $2,000 invoice. Waiting on edits."
[EMOTION] [this is the valley that buys the peak — and the sag zone: place the vulnerability beat here]
[RETENTION] [micro-loop or involvement device — the 25–40% window is where videos silently die]
[GENERATION]
  Model: [or: "text-only scene — static text over solid background / no generation"]

---

SCENE 5 — VALUE (20–40s)
[SPOKEN] What this means for the viewer's actual work.
[GENERATION]
  Model: [lifestyle or product grid visual]
  Prompt: [grid of product variations / creator working / team reviewing content]

---

SCENE 6 — PROOF (40–50s)
[SPOKEN] Real number. Real result.
[GENERATION]
  Model: [return to the hero visual from Scene 1, or a results screen]

---

SCENE 7 — CTA (50–60s)
[SPOKEN] One action. Loopable ending so it replays naturally — ≤8s between the peak and this frame.
[TEXT OVERLAY] CTA on screen.
[RETENTION] [name the loop mechanic: seam / sentence / recontext / detail callback]
[GENERATION]
  Model: [logo/brand frame, or loop back to Scene 1 image]

---

IMAGINESSHORTS FAST PATH (if using ImagineShorts instead):
CONCEPT: [1–3 sentence brief]
SCRIPT: [paste the full spoken script above]
TONE: [direct / conversational / aspirational]
VOICE: [narrator style]
CAPTIONS: [bold / subtitle / kinetic]
MUSIC: [upbeat / minimal / cinematic / none]
```

---

## Step 8: Platform Strategy for AI Tools

| Platform | Primary Signal | Hook Type That Wins | Optimal Length | AI Tool Strategy |
|---|---|---|---|---|
| **TikTok** | Completion rate (70%), rewatch | Demo-first, Product/Outcome Showcase | 15–30s cold; 60s+ for rewards | Show output in first 1.5s; search keywords in caption; refresh creative every 7–10 days |
| **Instagram Reels** | DM shares | Story-first, POV, "forward this to someone" | 15–45s cold | Design "you need to see this" moments; higher quality expectation; sound-off caption critical |
| **YouTube Shorts** | Search intent, replay rate | Tutorial/demo hybrid, query-format hooks | 40–55s | Format hook as the exact search query; B2B decision-makers live here |
| **LinkedIn** | Saves, professional shares | Authority/contrarian, ROI framing | 45–60s | B2B agencies + enterprise; hook names the specific job title and workflow |

**For cold audiences on TikTok:** demo-first wins — show the output before you explain anything.

**For Reels:** story-first wins for DM shares. The POV hook generates DMs at 2.4x the rate of standard reveal hooks.

**For B2B campaigns:** YouTube Shorts + LinkedIn. The short-form video is a funnel entry. Hook should direct to longer proof. Name the exact role and workflow — "for creative directors whose teams are still editing manually" outperforms "for marketing teams."

---

## Step 9: Campaign-Level Thinking

If this is part of a campaign (multiple pieces of content), think in arcs.

**The Awareness → Consideration → Conversion Arc:**
- **Awareness hook** (cold audience, unaware): Demo-first, awe-based. No ask. Just blow their mind.
- **Consideration hook** (warm, has seen content): Skeptic or process transparency. Answer "but does it actually work?"
- **Conversion hook** (decision stage): Cost destruction + specific CTA. Make the case for action now.

**The 3-Video Campaign Series:**
1. "This exists" — The reveal. Output-first, no pitch.
2. "Here's how" — Process transparency. The exact prompt, the steps, the workflow. Earn trust.
3. "Here's what it means for you" — Identity shift. Connect capability to their specific role and situation.

Read `references/campaign-arcs.md` for the full 5-video series, feature launch arc, A/B testing system, and completion bait types.

---

## Step 10: Output Format

```
PLATFORM: [platform]
AWARENESS LEVEL: [awareness level of target audience]
GOAL: [awareness / consideration / conversion]
EMOTION TARGET: [primary emotion]
EMOTIONAL ARC: [arc shape] — [0s feeling] → [midpoint feeling] → [end feeling]
HOOK TYPE: [cold open / POV setup / pattern interrupt / story hook]
PRODUCTION PATH: [ImagineShorts / Image+Video Studio / Workflows 2.0]

---

RECOMMENDED HOOK:
[Spoken line]
[TEXT OVERLAY]
[GENERATION: Model + Prompt]

---

HOOK VARIATIONS (5):

1. [EMOTION TYPE + FORMULA NAME] — [Achievable / CONCEPT ONLY]
"[Hook text]"
[TEXT OVERLAY]
[GENERATION: Model + Prompt — or "CONCEPT TBD" if unhinged]
4U Score: [X/4] — [one sentence on why]

2. [EMOTION TYPE + FORMULA NAME]
[...through 5 — at least 1 unhinged variation if the campaign has room for it]

RECOMMENDATION: Lead with #[X] for [stated goal/audience]. Test #[Y] as variant.

---

FULL SCRIPT (if requested):
[scene-by-scene script with generation prompts per scene — see Step 7 template]

---

CAMPAIGN ARC (if applicable):
[3-video or 5-video series with hook, format, and production path for each]
```

---

## Competitive Context — The White Space imagine.art Owns

The dominant competitor in AI video/image marketing has built their brand around three pillars: money/income hooks ("earn $2,500 per video"), Hollywood-for-everyone aspirational framing, and high-volume shock content through a paid creator program. They have $300M ARR and a $1.3B valuation — but they also have a documented trust crisis, a suspended Twitter account, a Forbes exposé about harmful content, and a viral "job killer" post that permanently alienated professional creatives.

**The emotional territory they've abandoned — and imagine.art can own:**

**Trust and brand safety.** Their brand carries real reputation risk. Agencies and brand managers at growth-stage companies are actively looking for a safer alternative. imagine.art doesn't need to attack — simply positioning around ethical AI, transparent licensing, and brand-safe generation is enough. Hooks: "AI-generated content you can put in front of your customers."

**Professional creative identity.** They publicly framed AI as the thing that "ended" creative jobs. Every photographer, videographer, and motion designer who saw that post is now hostile to their brand — and represents a high-value segment with real buying power. The counter-narrative: "The tool that made me more valuable, not redundant." Hook it from the professional's POV.

**Creative culture and craft.** Their entire content library is tactical — how to generate, how to earn, how to go viral. They have zero content about why certain images resonate emotionally, what makes a visual story work, how to develop a visual voice. This is the lane that builds the most loyal, highest-LTV creative community. Hooks: "What would you make if execution was no longer the obstacle?"

**Integrated workflow.** They are a video platform. They stop at the clip. imagine.art's strength is the full creative pipeline — image, video, edit, brand consistency across sessions, team collaboration. The hook: "From idea to campaign in one session. Without switching tools."

**NEVER reference the competitor by name in any script, hook, or example.** Use "[competitor]" in internal planning only. In all deliverables, position around imagine.art's strengths without naming anyone else.

---

## Reference Files

- **`references/emotional-arcs.md`** ← **READ FOR ANY SCRIPT OVER 20 SECONDS, and any time the brief says "make it more emotional," "make it hit harder," or the story feels flat.** The felt-journey-first method, the emotional contrast principle (emotion registers as change, not level), the 6 short-form arc shapes with selection guide, scene-by-scene valence mapping rules, the peak-end rule, the 4-rung stakes ladder, making viewers care in 3 seconds, vulnerability beats, and how to translate scene emotions into generation prompts and voice delivery.
- **`references/retention-engineering.md`** ← **READ FOR ANY SCRIPT OVER 20 SECONDS, and whenever the problem is watch time, completion, drop-off, or rewatch.** Retention curve anatomy (the Cliff, the Sag, the Exit Ramp), the 3–7 second interest cadence, the 9-device retention taxonomy, payoff scheduling and the trust ledger, the 4 loopable ending mechanics, the drop-off diagnosis table (drop location → cause → fix), and the 8-step retention pass to run on every draft.
- **`references/creative-ideation.md`** ← **READ WHEN THERE'S NO CONCEPT YET or a hook keeps failing.** The pre-writing phase: three-phase concept pipeline (generate → elaborate → champion), six brainstorming frameworks with selection table (mind mapping, freewriting, 15-minute timer, "What If" inversion, gap analysis, brainwriting), character-under-pressure subtext exercises (Five Dodges, First Lie, Weaponized Silence), and the 5-point filter a concept must pass before scripting.
- **`references/auteur-styles.md`** ← **READ FOR CREATIVE DIRECTION AND BRAND FILMS.** Director methods as writing technique: Tarantino's Pledge, mundane derailment, dialogue-as-psychological-baseline, 3-act information flow; Nolan's time-as-weapon, visual anchor rule, practical-first credibility, signal-your-intent. Plus the full auteur adjective taxonomy (Andersonian, Bayhem, Lynchian, Malickesque, Fincher-monochromatic, Nolanian, Tarantinoesque, and more) decompressed into prompt-ready vocabulary for imagine.art generation, color schemes as directorial signatures, and a register decision guide.
- **`references/imagine-art-production.md`** ← **READ FOR EVERY SCRIPT.** The complete AI production guide. Three production paths (ImagineShorts, Image+Video Studio, Workflows 2.0). Model selection table by content type. JSON prompt template for campaign consistency. Canonical prompt structure. Consistent character setup. AI Product Video Maker. UGC/talking head via HeyGen Avatar. Node reference for Workflows 2.0. Quick-reference: which tool for which situation.
- **`references/audio-hooks.md`** ← **READ FOR EVERY VIDEO SCRIPT.** Audio is a primary hook mechanism. TikTok scroll decision happens at 0.4 seconds — audio fires before visuals are processed. The 7 audio hook types (silence, abrupt vocal entry, bass drop, ASMR, sonic incongruity, millennial pause, product foley). BPM and music psychology guide with specific emotion tables. ElevenLabs v3 notation for scripting AI narration. Sentence rules for natural AI voice delivery. Silence architecture — where to place dead air for maximum effect.
- **`references/visual-language.md`** ← **READ WHEN WRITING GENERATION PROMPTS.** Replaces "cinematic" and other vague descriptors with specific technical vocabulary. Every major lighting setup (Rembrandt, split, backlight, golden hour, high-key, low-key, volumetric) with emotional meaning and exact prompt vocabulary. Color temperature chart. Color psychology combinations. Composition principles as emotional choices. What "cinematic" actually means technically broken into 7 components. Copy-ready prompt vocabulary for lighting, lens, camera, color grade, composition, and texture.
- **`references/unhinged.md`** ← **READ FOR THE 5TH VARIATION.** The creative rule-breaking framework. The test of coherence (the line between deliberately weird and just wrong). Full convention map with risk/reward for each rule break. The 5 specific techniques: wrong aesthetic, sonic incongruity, anti-hook, format parody, full deconstruction. The Nutter Butter case study (3,100 → 700,000 followers). AI prompt vocabulary for unconventional and glitch output. Prompts for finding the unhinged variation in any brief.
- **`references/prompt-iteration.md`** ← **READ WHEN A GENERATION DOESN'T WORK.** The 5 diagnostic categories with specific fixes for each. Model-specific failure modes: Nano Banana Pro, Seedance 2.0, Kling 2.6/3.0. Negative prompt strategy — the 5-term cap, vocabulary by failure type, model-specific syntax. Reference image strategy — when, how many, what makes a good reference. Iteration vocabulary: phrases that predictably shift output for lighting, mood, motion, and composition.
- **`references/pro-copywriting.md`** ← **READ FOR ANY CAMPAIGN.** Master copywriting techniques (Halbert, Schwartz, Sugarman, Hopkins, Ogilvy, Caples, Bencivenga, Kennedy) applied specifically to short-form AI hooks. Awareness level matching, slippery slide, IF…THEN structure, agitation, future pacing, language mirroring, sentence rhythm. 2026 fatigue patterns to avoid. B2B vs B2C hook guide.
- **`references/worked-examples.md`** ← **READ FOR FAST STARTS.** Fully-written hooks for all 5 imagine.art audience segments: content creators, social media managers, e-commerce brand owners, agencies, filmmakers. Each with visual direction, 4U score, and technique label. Includes competitive positioning hooks for the angles the market leader has abandoned (trust, creative professional identity, craft culture).
- **`references/hook-editing.md`** ← **READ WHEN REWRITING OR STUCK.** The 5 hook failure modes with before/after rewrites. The full hook upgrade checklist. Ogilvy's 5-step Big Idea development process for imagine.art. Language research methodology — exactly where to find the words your audience actually uses and how to mirror them in copy.
- **`references/imagine-art-context.md`** ← **READ FIRST for any imagine.art campaign.** Platform identity, 5 audience segments each with pain points, dream outcomes, and hook entry points. Core positioning. What to avoid. 6 content pillars. Campaign angles. Voice guidelines.
- **`references/ai-video.md`** ← **READ FIRST for any AI video campaign.** The 4 video hook types, all 9 production modes mapped to hook entry points, the 5 AI-video-specific emotions, motion prompting vocabulary, real viral case studies, and 2026 TikTok algorithm data.
- **`references/campaign-arcs.md`** — Multi-video campaign planning, content calendar, A/B testing strategy, 3-video and 5-video series with scripts, feature launch arc, completion bait types, series continuity.
- **`references/visual-direction.md`** — Production-ready visual scripting. Camera language glossary, text overlay styles, 6 visual hook patterns, platform-specific visual notes, production notes format.
- **`references/hooks.md`** — The 20-type hook formula library. For non-AI campaigns or deep hook formula reference.
- **`references/short-form.md`** — Platform timing guides, creator style breakdowns, full script templates, open loop technique, CTA formats.
- **`references/ads.md`** — Paid ad frameworks: Direct Response, UGC, VSL, brand films.
- **`references/screenplay.md`** — Screenwriting, Save the Cat, 3-act. For brand films and narrative content.

---

## Final Audit — Run Before Every Delivery

### Quality checks:
1. **Awareness level matched?** — Cold traffic needs emotion/story. Not product features. Not brand names.
2. **Image or video?** — If video: motion-aware hook logic applied. (Check `references/ai-video.md`.)
3. **Demo-first?** — First frame = the output, not the intro. Output before explanation.
4. **Lands in 1.5 seconds?** — The text overlay must carry the hook for sound-off viewers.
5. **Every claim specific?** — No adjectives. Only numbers, timeframes, named outcomes. Odd numbers where possible.
6. **Hook type named?** — Cold open / POV setup / Pattern interrupt / Story hook.
7. **5 variations?** — Always. Each labeled by emotion type AND formula name.
8. **Slippery slide?** — Every sentence earns the next. Seeds of curiosity at transitions.
9. **Agitation present?** — For problem-aware audiences: did you make the pain feel worse before offering relief?
10. **Completion bait built in?** — The payoff must be unreachable by skipping.
10a. **Emotional arc mapped?** — For scripts >20s: one arc shape chosen, every scene labeled with emotion + intensity, no flatline (no two consecutive scenes identical), spread ≥ 5 points, peak at 60–90% of runtime. (See `references/emotional-arcs.md`.)
10b. **Retention pass run?** — New stimulus every 3–7s with rotated channels, loops chained (never all closed mid-video), payoffs ascending, ≤8s from peak to final frame, loop mechanic named. (See `references/retention-engineering.md`.)
10c. **Peak-end check?** — One nameable peak second; the final feeling matches the campaign goal (awareness→awe, consideration→trust, conversion→agency).
10d. **Stakes resolved at the rung they were raised to?** — If the script climbed to social or identity stakes, the resolution must land there too.
11. **One CTA, not two.** — Single action, tied to the content.
12. **Competitor names?** — NEVER reference competing AI platforms positively. Generic framing or no mention.
13. **Generation prompts included?** — Every scene should have a model + prompt. ImagineShorts fast-path included where relevant.
14. **At least one unhinged variation?** — If the campaign has energy, push one hook past the safe line. Flag as `[CONCEPT — PRODUCTION TBD]`. The best ideas live where it feels like too much.
15. **Concept passed the filter?** — If the brief started vague: dramatic question named, world rules clear, gap defined, 2-sentence pitch works. (See `references/creative-ideation.md`.)
16. **Director register decompressed?** — If an auteur style was used: prompt contains the specific components (framing, palette, light, camera), never just the director's name. One dominant register per piece.


<!-- ═══════ FILE: script-writer/references/hooks.md ═══════ -->

# Hook Formula Library

A hook is any device in the first 1–5 seconds that prevents the viewer from scrolling. The mechanism is always one of three things — and the best hooks combine at least two:

1. **Pattern interrupt** — Something unexpected that forces the brain to pause
2. **Curiosity gap** — Incomplete information the brain needs to close
3. **Direct relevance** — Instant recognition of the viewer's own pain, identity, or situation

**80% of viewers decide in under 3 seconds.** If the hook fails, nothing else in the script matters.

---

## The Three Channels of a Hook

Every short-form hook has three simultaneous delivery channels:
- **Auditory** — the first spoken sentence
- **Visual** — what's in frame in the first second (never a static, blank, or "title card" shot — always mid-action)
- **Text overlay** — on-screen caption that reinforces or extends the spoken hook

Write all three. The strongest hooks work across all three channels at once.

---

## The 4 U's Test

Every hook should score 3–4 out of 4:
- **Urgent** — Does it convey immediacy or "you need this now"?
- **Unique** — Does it offer something different or surprising?
- **Ultra-specific** — Numbers, names, and timeframes beat adjectives always
- **Useful** — Does watching clearly benefit the viewer?

---

## 20 Hook Formulas with Templates, Examples, and Psychology

---

### 1. The Curiosity Gap Hook
**Psychology:** Information gap theory — the brain cannot rest with an unresolved gap.

**Templates:**
- "There's a reason no one talks about [topic]..."
- "The [industry] secret they don't want you to know..."
- "I tried [thing] for [duration]. Here's what nobody tells you."
- "The one [thing] that changed everything — and it takes 10 seconds."

**Example:** "The one Instagram setting that 99% of creators don't know about."

**Best for:** Educational content, tutorials, "insider" content

---

### 2. The Contrarian Hook
**Psychology:** Cognitive dissonance — the brain must resolve the contradiction between what it believes and what you're claiming.

**Templates:**
- "Stop doing [common practice]. It's actually making [problem] worse."
- "[Universally accepted belief] is completely wrong."
- "Waking up at 5am won't make you successful. Here's what actually will."

**Example:** "Posting more content is making your brand weaker, not stronger."

**Best for:** Authority positioning, expertise content, any topic where conventional wisdom is wrong

---

### 3. The Bold Claim Hook
**Psychology:** Bold claims create cognitive dissonance — viewers stay to see if you can prove it.

**Templates:**
- "I [achieved specific result] in [compressed timeframe]."
- "$[amount] in [timeframe] doing [one thing]."
- "[Specific result]. No [typical objection]. No [typical objection]. Just [mechanism]."

**Example:** "I grew from 0 to 100k followers in 47 days without running a single ad."

**Best for:** Transformation content, business results, before/after stories

---

### 4. The Story Hook
**Psychology:** Unresolved narrative creates a loop — the viewer stays to find out what happened.

**Templates:**
- "I almost [worst case scenario]. Then [turning point] happened."
- "The worst day of my [context] taught me the most important thing I know."
- "I was [terrible situation] until I found [thing]."

**Example:** "I almost shut down my business in 2022. Then one conversation changed everything."

**Best for:** Personal brand content, creator stories, testimonials

---

### 5. The Question Hook
**Psychology:** Forces self-identification — the viewer must assess whether they're implicated.

**Templates:**
- "Are you still [doing the wrong thing]?"
- "Why does [frustrating thing] keep happening to you?"
- "What if [counterintuitive assumption] is the whole problem?"

**Example:** "Are you still using these 3 dead marketing strategies in 2026?"

**Best for:** Awareness-stage content, common mistakes content

---

### 6. The Number Hook
**Psychology:** Numbers promise specificity and a concrete deliverable — the brain prepares to receive structured information.

**Templates:**
- "[X] things that [outcome]"
- "[X] mistakes [target audience] makes every single day"
- "I spent $[amount] testing [topic]. Here are the [X] things that actually work."

**Example:** "7 phrases that make people instantly trust you. Write these down."

**Best for:** List-format content, tips videos, educational content

---

### 7. The Warning Hook
**Psychology:** Loss aversion is more powerful than gain motivation. Stakes + urgency = attention.

**Templates:**
- "Stop [doing X]. It's [costing you / hurting you / destroying your chances]."
- "If you're doing this, you're leaving [X] on the table."
- "Before you [common action], watch this."

**Example:** "Stop posting Reels without this. You're leaving 80% of your reach behind."

**Best for:** Mistake correction content, direct response, strong CTAs

---

### 8. The Identity Hook
**Psychology:** Immediate self-selection — creates instant perceived relevance for the exact right viewer.

**Templates:**
- "This is for [specific person in specific situation]."
- "If you're a [identity] who [specific condition], stop scrolling."
- "Stop scrolling if you [very specific situation]."

**Example:** "If you're a freelancer charging less than $5k per project, this changes everything."

**Best for:** Targeted ads, niche content, DTC products

---

### 9. The "Most People Don't Know" Hook
**Psychology:** Social currency — the viewer gains insider knowledge they can share.

**Templates:**
- "Most people don't know this about [topic]..."
- "99% of [audience] are making this mistake right now."
- "What the top 1% of [field] do that no one talks about."

**Example:** "Most people write LinkedIn posts the wrong way. Here's how the 1% actually do it."

**Best for:** Expertise content, platform-specific tips, insider knowledge

---

### 10. The Before/After Hook
**Psychology:** Transformation desire is the most powerful motivator in content. Specificity removes skepticism.

**Templates:**
- "[Terrible before state] → [Specific after state]. Here's exactly how."
- "$0 to [specific number] in [timeframe]. No [objection]. No [objection]."
- "Six months ago [before]. Today [after]. Here's what changed."

**Example:** "$0 to $14k months. No agency. No ads. No followers to start."

**Best for:** Results content, testimonials, transformation stories

---

### 11. The Social Proof Hook
**Psychology:** Reduces skepticism through relatability — if someone like me did it, I can too.

**Templates:**
- "How a [relatable person] made [specific result] doing [thing]."
- "The strategy [specific number] of [people] are using to [outcome]."
- "This went from 200 views to 2 million. Here's exactly why."

**Example:** "How a 22-year-old barista made $11,000 in her first month of freelancing."

**Best for:** Social proof ads, testimonial content, case study content

---

### 12. The POV / Relatable Hook
**Psychology:** Native platform language creates instant identification — feels like content, not marketing.

**Templates:**
- "POV: You finally found the solution to [common problem]."
- "Things [platform] made me try — [category] edition."
- "I'm done gatekeeping this..."

**Example:** "POV: You just found out why all your content gets 200 views."

**Best for:** Organic TikTok/Reels, UGC ads, creator content

---

### 13. The Unpopular Opinion Hook
**Psychology:** Controversy + curiosity gap — the viewer stays to judge whether you're right.

**Templates:**
- "Unpopular opinion: [controversial but defensible stance]."
- "Hot take: [thing everyone does] is actually [negative consequence]."
- "I know this will get me hate, but [truth]."

**Example:** "Unpopular opinion: Your morning routine is sabotaging your productivity."

**Best for:** Thought leadership content, engagement-focused content

---

### 14. The Stakes Hook
**Psychology:** FOMO + urgency + scarcity. Works because the viewer feels the cost of not watching.

**Templates:**
- "In [timeframe], [strategy/thing] will be dead. Here's what replaces it."
- "This [thing] is changing in [timeframe]. Here's what to do now."
- "By the time most people figure this out, it'll be too late."

**Example:** "By 2027, this SEO strategy will be worthless. Here's what's replacing it."

**Best for:** Timely content, industry trend content, urgency-based ads

---

### 15. The "What Nobody Tells You" Hook
**Psychology:** Insider knowledge + relatability to struggle. The viewer has been failed by other sources; you have the real answer.

**Templates:**
- "Nobody tells you [uncomfortable truth about popular topic]."
- "What they don't tell you about [topic everyone talks about]."
- "The part of [journey] nobody shows on the internet."

**Example:** "Nobody tells you this about starting a business: the hardest part isn't what you think."

**Best for:** Personal brand content, honest/transparent content

---

### 16. The Direct Address Hook
**Psychology:** Ultra-specific targeting makes the exact right viewer feel this is made for them and only them.

**Templates:**
- "This video is specifically for [person with exact situation]."
- "If you own a [specific thing], you need to see this."
- "Attention [specific role]: this is going to save you [time/money/pain]."

**Example:** "This is specifically for anyone running Facebook ads who's losing money and doesn't know why."

**Best for:** Targeted ads, paid traffic, niche audiences

---

### 17. The Process Teaser Hook
**Psychology:** Specificity of result + implicit promise of replicability — "if they can show me how, I can do it too."

**Templates:**
- "Here's the exact [framework/script/system] I used to [specific result]."
- "The exact process: [specific outcome] in [specific timeframe]."
- "I'll walk you through exactly how [result] — step by step."

**Example:** "Here's the exact cold email script I used to land 6 enterprise clients in 30 days."

**Best for:** Tutorial content, system/framework reveals, high-value how-to content

---

### 18. The Mistake Hook
**Psychology:** Fear of making a costly mistake you're currently making — identity relevance + urgency.

**Templates:**
- "The biggest mistake [people in your niche] make — and how to fix it today."
- "I made [mistake] for [duration]. Here's how to avoid my mistake."
- "If [common thing] isn't working, this is probably why."

**Example:** "The biggest mistake coaches make on discovery calls — and why it costs them thousands every month."

**Best for:** Mistake-correction content, authority positioning, problem-aware audiences

---

### 19. The Experience Credential Hook (Hormozi)
**Psychology:** Specific lived experience creates authority and makes the insight feel earned, not theoretical.

**Structure:** [Specific number/scope of experience] — here's what nobody tells you about [topic]

**The specificity ladder:**
- Generic: "Here's how to hire good people."
- Better: "I've hired hundreds of people — here's what I learned."
- Hormozi-level: "I've hired 4,000 people. Here are the 3 questions I ask every single time."

Variables to specify: exact number, specific deliverable, specific action, timeframe

**Best for:** Expert content, B2B, any format where authority matters

---

### 20. The "If...Then" Hook
**Psychology:** Conditional relevance — the viewer self-qualifies and commits before the video even starts.

**Templates:**
- "If you're trying to [goal], then this is the only [thing] you'll ever need."
- "If you [struggle], then [promised outcome from watching this]."
- "If [situation], then you're about to fix it."

**Example:** "If you're trying to close high-ticket clients, this is the only sales framework you'll ever need."

**Best for:** Sales content, high-intent audiences, direct response

---

## The Hormozi Hook System (Value Equation Applied)

The viewer's brain unconsciously runs this calculation on every hook:

**Value = (Dream Outcome × Perceived Likelihood) ÷ (Time Delay × Effort Required)**

To maximize hook performance:
- **Raise Dream Outcome**: Make the end state more specific, more vivid, more emotionally charged
- **Raise Perceived Likelihood**: Add social proof, specificity, credentials
- **Lower Time Delay**: "In 48 hours," "This week," "Instantly"
- **Lower Effort**: "No experience needed," "Takes 30 seconds," "Just copy this"

The best hooks front-load Dream Outcome while compressing Time Delay.

---

## Hook Writing Process

Never write one hook. Always write 5 and pick the best.

1. Draft your first instinct hook
2. Write a contrarian version (what's the opposite angle?)
3. Write a story version (open with a narrative moment)
4. Write a number version (compress to specifics and stats)
5. Write a direct address version (speak to the exact identity)

Then run each through the 4 U's test. Present the top 3 to the client/user with a note on which one you'd lead with and why.


<!-- ═══════ FILE: script-writer/references/hook-editing.md ═══════ -->

# Hook Editing, The Big Idea, and Language Research

Three skills that separate amateur AI campaign copy from professional copy.

---

## Part 1: The Hook Editing Protocol

A first draft is always a starting point. This protocol diagnoses what's wrong and tells you exactly what to fix.

### The 5 Hook Failure Modes

Every weak hook fails for one of five reasons. Identify the failure mode first, then apply the specific fix.

---

**Failure Mode 1: It Leads With the Tool, Not the Problem**

The symptom: The hook opens with the product name, a feature, or a category label.

> ❌ "imagine.art is an AI image generator that lets you create professional product photography."

Why it fails: Cold traffic doesn't know your product exists. More importantly, they don't care — yet. The hook has to earn the right to introduce the product.

**The fix: Delete everything before the problem. Start at the moment the viewer's pain is highest.**

> ✓ "My product photographer just cancelled. Launch is in 4 days. Here's what I did."

Technique applied: Flagging (Kennedy) + Cold Open. The situation is urgent and specific. The product reveals itself after the viewer is already invested.

---

**Failure Mode 2: It Describes Features, Not Transformation**

The symptom: The hook tells you what the product does, not what changes for the person using it.

> ❌ "imagine.art generates photorealistic images from text prompts in seconds."

Why it fails: Every AI tool says this. It's a spec sheet, not a hook. The viewer's brain has no reason to care.

**The fix: Replace the capability with the specific life change it enables.**

> ✓ "I used to spend $2,800 and 3 weeks on a product shoot. Last Tuesday I generated 40 images before lunch."

Technique applied: Cost Destruction + Specificity as Proof (Hopkins). The transformation is made tangible through real numbers and a real timeline.

---

**Failure Mode 3: It's Specific to the Wrong Thing**

The symptom: The hook uses numbers, but they measure the wrong dimension of value.

> ❌ "imagine.art has 50+ art styles and 200+ presets."

Why it fails: Features, not benefits. Numbers about the tool, not about the viewer's outcome.

**The fix: Translate the feature number into a viewer-outcome number.**

> ✓ "47 on-brand product images. One afternoon. Zero scheduling emails."

Technique applied: Volume Hook + Sugarman Slippery Slide. Every word earns the next. The three-part structure builds toward the payoff ("Zero scheduling emails" — the thing social managers hate most).

---

**Failure Mode 4: It's Too Smart to Land in 1.5 Seconds**

The symptom: The hook is conceptually interesting but requires 5+ seconds to register. The wit lands after the viewer has already scrolled.

> ❌ "In a world where your competitors have unlimited creative budgets, the only equalizer is knowing which tools they're quietly using."

Why it fails: It's three ideas strung together. By the time "quietly using" arrives, the viewer is gone.

**The fix: One idea. Then stop.**

> ✓ "The tool your competitors don't want you to know about."

Or stronger with specificity:
> ✓ "I generated the ad that outperformed our agency's $8,000 campaign. Here's the tool."

Technique applied: Cold Open + Ogilvy Big Idea compression. One idea, specific enough to feel real, and a seed of curiosity that demands the next 5 seconds.

**The 1.5-second test:** Read the first sentence of your hook out loud and stop after 4 words. Does the viewer already understand the emotional territory? If not, cut.

---

**Failure Mode 5: It Speaks to Everyone and Reaches No One**

The symptom: The hook uses broad audience language ("creators," "marketers," "anyone who wants to...").

> ❌ "For creators who want to level up their content."

Why it fails: Nobody identifies as "a creator who wants to level up." The phrase signals that the content wasn't written for anyone specific — so anyone scrolling it feels justified in skipping.

**The fix: Name the specific situation, not the category. (Kennedy Flagging principle.)**

> ✓ "If you've been using the same 3 product photos for 4 months because you can't afford a reshoot — this is specifically for you."

The viewer who fits this situation feels physically seen. Everyone else correctly recognizes this isn't for them and scrolls — which is the right outcome. A hook that qualifies the right audience and disqualifies everyone else is performing its job.

---

### The Hook Upgrade Checklist

Run every hook through this before submitting:

1. **Cut the setup.** Delete every word before the most interesting moment. What's left?
2. **Replace adjectives with numbers.** "Fast" → "28 seconds." "Affordable" → "$0." "Professional quality" → "My photographer couldn't tell the difference."
3. **Name the person.** Can you replace "creators" or "marketers" with the specific situation they're living right now?
4. **Read the first 4 words aloud.** What emotional territory do they establish? Is it the right one?
5. **Find the slippery slide.** Does the last word of the first sentence make you need the first word of the second?
6. **Check awareness level.** Is this hook calibrated for where your actual audience is right now?
7. **Build in the question.** What unanswered question does the hook leave in the viewer's mind?

---

## Part 2: The Big Idea Development Exercise

David Ogilvy's most important principle: every campaign needs one large, arresting, relevant idea that can be expressed in a single sentence — and that makes the product's central benefit unforgettable.

Most AI campaigns don't have a Big Idea. They have a list of features.

A Big Idea is not a tagline. It is not a claim. It is a frame that makes everything else in the campaign make sense.

**Ogilvy's Rolls-Royce Big Idea:** "At 60 miles an hour the loudest noise in this new Rolls-Royce comes from the electric clock." This one sentence contains: silence (benefit), precision engineering (proof), luxury (aspiration). None of those words appear in the sentence.

**The test of a Big Idea:** Strip away everything except the core sentence. Does the product's central benefit become undeniable — without the word "quality," "professional," "powerful," or "easy"?

---

### The 5-Step Big Idea Process

**Step 1: Immerse in the product until one true, surprising thing surfaces.**

Spend 20 minutes with imagine.art before writing a single word. Generate images. Try prompts you're not sure will work. Watch what happens when you push the model in unexpected directions. You are looking for the thing that surprises you — the capability, the quality threshold, the specific behavior that you didn't expect and didn't know to claim.

Hopkins spent weeks in the Schlitz brewery before writing a word. Ogilvy spent three weeks reading about Rolls-Royce. The Big Idea is always already in the product — your job is to find it.

---

**Step 2: Find the "they laughed when" moment.**

Ask: What did you believe about AI-generated images before you used imagine.art? What changed? The moment your belief shifted — that is where the Big Idea lives.

Common "they laughed when" moments for imagine.art:
- "I thought all AI images looked like AI. This one made me forget."
- "I thought I still needed a photographer for anything professional. Then this happened."
- "I thought AI couldn't understand my brand aesthetic. I uploaded 3 references and it did."

Write your own. The more specific the moment, the stronger the Big Idea.

---

**Step 3: Find the one detail that makes the benefit undeniable.**

Ogilvy's method: generate 100 potential headlines. Shortlist to 26. Then pick one. The process matters because it forces exhaustion of the obvious before you reach the surprising.

For imagine.art, the diagnostic questions:
- What can it do that a competitor cannot? (Not a feature — a specific output or behavior)
- What's the number that makes you stop? (Not "fast" — the actual seconds. Not "affordable" — the actual comparison)
- What's the thing it does that no one has said yet? (The Schlitz principle — competitors also have this capability but haven't described it)
- What is the visual equivalent of the Rolls-Royce clock sound?

---

**Step 4: State it in one sentence with no adjectives.**

Adjectives are the enemy of Big Ideas. They describe. Big Ideas show.

Exercise: Write your Big Idea. Then remove every adjective. Then remove every adverb. What's left?

If what's left still makes the point — you have a Big Idea.
If you need the adjectives — you have a description.

**Examples:**

| Description (NOT a Big Idea) | Big Idea |
|---|---|
| "Professional-quality AI images in seconds" | "12 words. 28 seconds. My photographer couldn't tell the difference." |
| "Affordable alternative to product photography" | "The $3,000 photoshoot you just cancelled? That image is already made." |
| "AI that understands your brand aesthetic" | "I uploaded 3 reference images. It understood what 4 pages of brand guidelines didn't convey." |
| "Powerful tool for creative teams" | "We showed the client 10 directions. We'd been briefed 2 hours earlier." |

---

**Step 5: Test the Big Idea against the campaign goal.**

A Big Idea for an awareness campaign should make someone stop and stare.
A Big Idea for a conversion campaign should make someone feel it would be irrational not to try.
A Big Idea for a consideration campaign should make someone say "wait, it can really do that?"

If your Big Idea doesn't land that response within 5 seconds of hearing it cold — keep looking.

---

## Part 3: Language Research — Find the Words Your Audience Actually Uses

The most credible copy is written in the audience's own language — not the brand's. This section tells you exactly where to find it.

### Where to Look

**1. 1-star and 2-star reviews of competing products**
This is the highest-value source. When someone writes a negative review, they are describing their pain in their own words, unfiltered, without brand mediation.

Where to look:
- Trustpilot reviews for AI image/video tools
- G2, Capterra, Product Hunt reviews
- Reddit comments on r/artificial, r/midjourney, r/StableDiffusion, r/AIVideoCreation

What you're mining: the exact phrases people use to describe what frustrated them. These are your future hook openings.

**Example finds from AI tool reviews:**
- "The images always look like AI" → hook: "I know what you're thinking — it looks like AI. Look closer."
- "The brand consistency is completely unreliable" → hook: "40 images, and every single one stays on-brand. Here's how."
- "I had to redo the whole thing because the background was wrong" → hook: "Generate. Approve. Done. No redos."

---

**2. Reddit threads where your audience describes their work problems**

Subreddits to mine:
- r/ecommerce — "product photography," "photoshoot," "content creation budget"
- r/socialmediamarketing — "content calendar," "brand consistency," "running out of content"
- r/freelance — "client revision requests," "production pipeline," "spec work"
- r/filmmakers — "pre-visualization," "communicating with DP," "location scouting"
- r/agency — "pitch decks," "concepting phase," "client presentations"

What you're mining: the specific, unguarded language people use when they're venting about real problems. Not "insufficient visual assets" — "we ran out of content three weeks into the month."

---

**3. Comments on competitor content**

The comments section on a competitor's viral video is a direct window into the audience's unfiltered reaction. Look for:
- What questions people ask ("Can it do X?")
- What objections people voice ("Looks fake to me")
- What pain points people confirm ("This is exactly what I needed")
- What language patterns repeat

**Specific search:** Find the top 3 performing videos on any major AI image/video platform's TikTok or Reels. Read every comment. Extract every phrase that describes a problem, a belief, or an emotional reaction.

---

**4. Customer support tickets and onboarding survey responses**

If you have access to imagine.art's support tickets or NPS responses — these are the gold standard. Real customers describing real frustrations in their own exact words.

What to look for:
- The specific workflow step they're stuck on
- The comparison they make ("I expected X like tool Y does")
- The emotion behind the request ("I need this to look professional for a client")

---

**5. Sales call transcripts and demo recordings**

If sales or CS teams record calls — the language a prospect uses in the first 2 minutes of explaining their situation is the language your hook should use. They're describing themselves before they know anything about your product.

---

### The Language Mirror Template

Once you've collected raw language from the sources above, run it through this filter:

**Their words → Hook version**

| What they said (raw) | Hook that mirrors it |
|---|---|
| "I'm sick of paying for photoshoots" | "Sick of photoshoot invoices? This is what replaced them." |
| "The AI images always look generated" | "I know. They all look generated. This one didn't." |
| "I can't keep up with the content demand" | "I couldn't keep up either. Then I stopped building content and started generating it." |
| "The client keeps changing the brief" | "Client changed the brief again. Here's why that stopped mattering." |
| "I can't visualize my shot until we're on location" | "I showed my DP exactly what I was imagining. Before we scouted a single location." |

The test: read both columns. Which one would make you stop scrolling? Always the right column — because it starts from their lived experience, not your product's feature.

---

### The Single Most Important Language Rule

Before writing any hook, ask: **Where have I heard this sentence before?**

If the answer is "in a marketing brief" or "on a product features page" — rewrite it.
If the answer is "in a Reddit thread" or "in a 1-star review" or "in a sales call" — you've found your hook.

The copy that converts is the copy that sounds like someone is describing the viewer's own life back to them.


<!-- ═══════ FILE: script-writer/references/audio-hooks.md ═══════ -->

# Audio Hooks — Sound as a Primary Hook Mechanism

Audio is not background. On TikTok, where 70–80% of users watch with sound on, the first sound in a video fires before the visual is processed. TikTok's own research puts the scroll decision at **0.4 seconds** — not 1.5, not 3. Audio is faster than vision at that window. This file treats audio as a first-class hook element.

---

## The Real Window: 0.4 Seconds

At 0.4 seconds, the auditory cortex has already fired. The amygdala — which handles threat detection and pattern recognition — has responded to sonic patterns before the rational brain has processed meaning. This is why a sudden silence, an unexpected bass drop, or a voice entering mid-sentence stops the scroll: it triggers a subconscious "something happened" response that the conscious brain then tries to resolve.

**What this means for every video:** The first sound is the real hook. The visual and the text overlay are the confirmation. Design audio first, then visual, then copy.

---

## The 7 Audio Hook Types

### 1. The Silence Hook
A sound begins — music, ambient, voice — then cuts to complete silence for 0.5–1.5 seconds before the hook line. In an audio-on environment, dead air is a jarring anomaly. The brain searches for the missing sound.

**Use before:** A big reveal, a provocative claim, a visual payoff. The silence creates anticipation the brain can't scroll past.

**Script notation:**
```
[Music plays for 1 second, then abrupt silence]
[long pause]
"Your product shoots don't have to cost $2,000 anymore."
```

### 2. The Abrupt Vocal Entry (Mid-Sentence Open)
Start speaking immediately on word one, mid-thought if possible. No intro, no "hey everyone." Dropping into the middle of an existing sentence signals that the viewer has entered a conversation already in progress — and the brain needs to catch up.

**Example opening:**
```
"—and that's the part nobody told you."
[VISUAL: product image, first frame]
```

The em-dash at the start signals the audio was already running.

### 3. The Bass Drop / Energy Impact
Sudden low-frequency impact in the first 0.5 seconds triggers an autonomic startle response. Effective for: product launches, fashion reveals, high-energy content. Paired with a fast visual cut, this combination produces measurable physiological arousal (elevated heart rate, skin conductance response).

**When to use:** Any content targeting excitement, urgency, desire. Not for trust-building or intimate content.

### 4. The ASMR / Intimate Close-Mic
A whispered or close-mic'd voice in the first line creates a parasocial intimacy response. The psychological mechanism: proximity. A voice that sounds physically close activates the "this is directed at me specifically" response. ASMR-style content grows watch time by **67%** compared to standard delivery.

**Use for:** Product reveals, intimate brand stories, "I want to tell you something" hooks.

**Script notation for ElevenLabs:**
```
[whispers] "Wait. [pause] Nobody's talking about this yet."
```

### 5. Sonic Incongruity (The Wrong Sound)
Place an audio element that doesn't match the visual. Premium product footage with rough lo-fi audio. Calm nature imagery under a phone notification sound. The brain tries to reconcile the mismatch and holds the frame while doing so.

**Example:** A stunning AI-generated product shot opens with the sound of a dial-up modem connecting. The incongruity is the hook — and when the clean product audio fades in, it creates a satisfying resolution.

### 6. The Millennial Pause (Weaponized)
A deliberate beat of silence — 0.5–0.8 seconds — before the first spoken word. This creates an anticipation loop: something is about to come, the pause tells the brain it's worth waiting for. Originally an accidental artifact; now a deliberate technique.

**Script notation:**
```
[pause]
"I generated 40 product images this morning."
```

### 7. Product Foley (Tactile Sound Design)
The sound of a product being handled — lid clicking, fabric moving, liquid pouring, interface clicking — creates a tactile intimacy that signals quality. A product that sounds solid feels premium. The foley technique from film production directly applies to AI content: add sound design to product reveal moments.

**Prompt note for ImagineShorts/ElevenLabs:**
```
SOUND EFFECTS: [product interaction sound — e.g., "soft metallic click of serum bottle cap"]
AMBIENT: [environment sound — e.g., "minimal morning room tone, near silence"]
```

---

## Music Bed Psychology: BPM, Key, and Genre

### BPM Ranges and Emotional Function

| BPM | Emotional Territory | Best Content Type |
|---|---|---|
| Under 70 | Luxury, grief, stillness, intimacy | Premium product reveals, emotional brand stories, high-end lifestyle |
| 70–90 | Warmth, nostalgia, aspiration, trust | Creator content, personal brand, community |
| 90–110 | Focus, confidence, drive, authority | AI tools, software, professional content, productivity |
| 120–140 | Excitement, urgency, energy | Fashion reveals, product launches, sale announcements |
| 140+ | Peak energy, celebration | Use only when the content fully matches — mismatched high-BPM reads as desperate |

**The trust mismatch:** imagine.art's e-commerce segment is tempted to use high-BPM music to feel "professional and exciting." But the audience making a $2,000 photography decision responds to 90–110 BPM: competent, confident, not frantic. Fast music signals hustle; moderate-pace music signals reliability.

### Major vs. Minor Mode

**Major:** Consonant, resolved, happy. Celebration, launch, completion.
**Minor:** Tension, longing, unresolved. Aspiration (wanting something you don't have yet), emotional story, transformation narrative.

Aspiration content is often more effective in minor key at 80–95 BPM than major, because aspiration inherently contains the tension of not-yet-having. Minor mode matches that emotional state.

### Genre Selections by Campaign Type

| Genre | Emotional Function | Use For |
|---|---|---|
| Cinematic orchestral (slow) | Premium, scale, "this matters" | Brand awareness, hero campaigns |
| Lo-fi hip-hop | Intimacy, focus, trust, late-night | Educational, soft sell, process transparency |
| Pop/synth 120+ BPM | Youth, energy, excitement | Product launches, social ads, trend content |
| Ambient/minimal | Luxury, calm, attention to detail | High-end product, beauty, architecture |
| Trap/hip-hop | Status, confidence, desire | Fashion, tech, aspirational segments |
| Acoustic/folk | Authenticity, personal, handmade | Creator segment, personal brand, UGC-style |

---

## Narration: Scripting for Natural AI Voice

ElevenLabs v3 generates voice from text + audio tags. The tags control delivery without being spoken. Every narration script for imagine.art content should use this notation.

### Core Audio Tags

```
[pause]         — short silence, natural breath equivalent
[short pause]   — fractional hesitation, 0.2–0.3 seconds
[long pause]    — dramatic gap, use before a reveal
[breathes]      — audible breath, essential for human naturalness

[whispers]      — intimate close-mic delivery
[speaking softly] — warm, pulled-in tone
[excited]       — energy escalation
[understated]   — flat/deadpan, effective for irony or authority
[awe]           — genuine wonder

[sigh]          — exhaustion, post-revelation, exasperation
[laughs]        — natural, not forced
```

### Punctuation as Pacing

```
.    — full stop, natural breath
...  — trailing off, suspension, dramatic hesitation
—    — abrupt cut or self-correction (creates conversational energy)
,    — slight softening, minor pause (not a breath)
```

**ALL CAPS** = strong emphasis on that word: `"This is NOT a photograph."`

### Sentence Rules for Natural AI Delivery

1. **Keep sentences under 18 words.** Beyond 18, AI delivery becomes monotone.
2. **Target 130–150 words per minute.** Below 110 WPM loses momentum. Above 165 WPM becomes hard to follow.
3. **Two short sentences, one medium. Repeat.** This cadence creates percussive rhythm that holds attention.
4. **No compound sentences joined by "and" or "but."** Break them into two sentences. The period is your pacing tool.
5. **Phonetically spell difficult words.** "Nano Banana" → write as spoken. "imagine.art" → "imagine dot art" or "Imagine Art" depending on how it should sound.
6. **Read every line aloud before submitting for generation.** If it sounds unnatural spoken by a human, it will sound robotic when rendered.

### Fully Notated Script Example

```
[excited] Wait. [pause] Look at this.

[long pause]

[speaking softly] That product image? [short pause] Not a photograph.
I typed twelve words. [pause] Thirty seconds later — [pause] that.

[breathes] The quote from my photographer was two thousand, eight hundred dollars.

[understated] So I cancelled it.

[pause] Here's the exact prompt.
```

This script reads at approximately 130 WPM, uses contrast between excited opening and understated close, and builds completion tension with "here's the exact prompt" — which the viewer cannot access without watching to the end.

---

## Silence Architecture: Where to Place Dead Air

Silence is most powerful when placed immediately before the thing the viewer wants. It functions as a promise that what's coming is worth waiting for.

**Five places silence works:**

1. **Before the reveal.** Music or ambient cuts out completely for 0.5–1.5 seconds before the "this is AI-generated" reveal. The silence marks the moment as significant.

2. **Before a specific number.** "The photoshoot quote was— [silence] —two thousand eight hundred dollars." The silence around the number makes it land like an object dropped on the floor.

3. **After a provocative question.** "Why are you still paying for product photography?" [1 second of silence]. The silence gives the question weight.

4. **At the loop point.** Ending the video with a beat of silence before the audio loops back to the beginning creates a seamless repeat — the viewer doesn't register the end as an ending.

5. **Mid-sentence cut.** Starting the video with the sound of someone already speaking, then cutting to silence for 0.3 seconds before the actual hook line. The cut creates a "wait, what did they say?" response that forces the viewer to rewatch.

---

## The Audio Audit

Before any video is submitted for generation:

- [ ] What does the video sound like with eyes closed for the first 0.4 seconds?
- [ ] Is there a sonic pattern break in the first second? (silence, unexpected sound, intimate voice, bass impact)
- [ ] Is narration scripted with ElevenLabs v3 tags, not plain text?
- [ ] Are all sentences under 18 words?
- [ ] Does the music BPM match the emotional intent — not just the energy level?
- [ ] Is there a silence beat placed before the key reveal or the key number?
- [ ] Does the audio loop cleanly? (loop point = silence or music outro)


<!-- ═══════ FILE: script-writer/references/short-form.md ═══════ -->

# Short-Form Video Scripts

Deep playbook for TikTok, Instagram Reels, YouTube Shorts, and YouTube long-form.

---

## Table of Contents
1. [Word Count & Timing Guides](#word-count--timing-guides)
2. [The Foundational Structure: Hook-Body-CTA](#the-foundational-structure-hook-body-cta)
3. [The Three Zones in Detail](#the-three-zones-in-detail)
4. [Open Loop Technique](#open-loop-technique)
5. [Pattern Interrupts Within the Video](#pattern-interrupts-within-the-video)
6. [CTA Formats That Work](#cta-formats-that-work)
7. [Creator Style Breakdowns](#creator-style-breakdowns)
8. [Platform-Specific Adaptations](#platform-specific-adaptations)
9. [Short-Form Script Templates](#short-form-script-templates)

---

## Word Count & Timing Guides

| Format | Duration | Word Count | Pacing |
|--------|----------|------------|--------|
| Ultra-short | 15 sec | 35–45 words | ~175 WPM |
| Standard short | 30 sec | 75–85 words | ~165 WPM |
| Standard short | 60 sec | 140–160 words | ~150 WPM |
| Extended short | 90 sec | 200–225 words | ~150 WPM |
| YouTube long-form | 5–15 min | 700–2,100 words | ~140 WPM |

If a 30-second script exceeds 90 words, it will feel rushed and lose completion. Cut.

---

## The Foundational Structure: Hook-Body-CTA

**For 30-second video:**
- Hook: 0–3s
- Body (value delivery): 3–23s
- CTA: 23–30s

**For 60-second video:**
- Hook: 0–3s
- Problem/Setup: 3–15s
- Solution/Value: 15–45s
- CTA: 45–60s

**For 90-second video:**
- Hook: 0–3s
- Problem/Setup: 3–20s
- Solution/Value (2–3 points): 20–70s
- CTA: 70–90s

**For 15-second video:**
- Hook: 0–2s
- Single value point: 2–12s
- CTA: 12–15s

---

## The Three Zones in Detail

### Zone 1 — Hook (0–3s)
The single most important zone in the entire script. It determines:
- Whether the viewer stays
- Whether the algorithm pushes the video to more people
- Whether the viewer saves, shares, or follows

Must be present in all three channels simultaneously:
1. **Auditory hook**: First spoken line — specific, surprising, or directly relevant
2. **Visual hook**: What's on screen in frame 1 — always mid-action, never a static title card
3. **Text overlay hook**: On-screen caption that reinforces or extends the spoken hook

**Things that kill a hook:**
- Starting with "Hey guys," "Hey everyone," or any greeting
- Starting with "In today's video" or "Before we get into it"
- Starting with a title card or logo
- A slow build to the actual point
- Vague opening that could apply to any video on the platform

---

### Zone 2 — Body (3s to ~80% of runtime)
Deliver on the hook's promise immediately. The first sentence of the body must flow directly from the hook — no filler transition.

**Body structures that work:**

**List Format (most reliable for short-form):**
- "Here are 3 reasons why..." / "The 5 things I wish I knew..." / "Step 1... Step 2..."
- Creates expectation, sustains attention because viewer knows what's coming
- Each point should be 8–15 seconds

**Narrative Format (highest engagement when done well):**
- Tell the story of one person (could be you, could be a customer)
- Compressed Hero's Journey: before → turning point → after
- Plant micro-open-loops: "And I'll tell you what happened next, but first..."

**Single Insight Deep Dive:**
- State one counterintuitive truth
- Explain why it's true
- Show the mechanism
- Give one specific action
- Best for authority-positioning content

**Contrast Format:**
- "Most people do X. The [result people want] actually do Y."
- Works because it validates viewer (they do X) and offers the upgrade

---

### Zone 3 — CTA (final 15–25% of runtime)
One action only. Never two CTAs. The CTA should feel like a natural next step, not a sudden pitch.

See full CTA section below.

---

## Open Loop Technique

Plant a tease in the first 30 seconds that pays off at the end. This is the single most powerful retention technique in short-form video.

**How to write an open loop:**
1. In Zone 2, mention something that implies a later payoff: "By the end of this, you'll know the one thing that makes all of this work — but first..."
2. Deliver another value point
3. Return to the teased payoff in Zone 3 before the CTA

The open loop must have a genuinely valuable payoff. Weak payoffs that don't deliver train viewers not to stay.

**Example (60-second video):**
- Hook (0–3s): "The reason your TikToks keep dying at 200 views"
- Body opens: "There are three reasons, and I'll give you the third one last because it's the most important..."
- Body delivers reasons 1 and 2 (3–40s)
- Returns to loop: "Okay here's the third one — this is what 99% of creators never figure out..." (40–55s)
- CTA (55–60s)

---

## Pattern Interrupts Within the Video

Attention resets every 15–30 seconds in short-form video. You must interrupt the pattern to keep viewers watching.

**Pattern interrupt techniques:**

**Visual:**
- Cut to a different angle or location
- Add a bold text overlay (sudden appearance)
- Show B-roll footage
- Use a graphic, chart, or screenshot
- Zoom in or change framing mid-sentence

**Audio:**
- Change the pace of delivery (slow down for impact, speed up for energy)
- Add a sound effect or music layer
- Pause dramatically before a key point
- Use a transition sound

**Content:**
- Ask a direct question to the viewer mid-video
- Use a numbered structure: "Okay, here's number two..."
- Make a surprising pivot: "Wait, there's actually something more important..."
- Use contrast: "But here's what's crazy..."

---

## CTA Formats That Work

**Comment-a-keyword (highest comment engagement):**
- "Comment '[WORD]' and I'll send you [thing]"
- Drives comment volume which signals algorithm

**Save prompt:**
- "Save this for when you need it"
- Save metric directly increases reach

**Follow CTA tied to value/identity:**
- "Follow if you're serious about [outcome]"
- "I post [content type] every [day] — follow so you don't miss it"

**Link-in-bio with specificity:**
- "Link in bio to get the [specific thing]" — not just "link in bio"

**Engagement prompt:**
- "Which one surprised you most? Drop it below"
- "Tag someone who needs to hear this"

**The weak CTAs to avoid:**
- "Like and subscribe"
- "Let me know in the comments"
- "Check out my page"
- "Follow for more"

---

## Creator Style Breakdowns

### Alex Hormozi Style (Educational Authority)

**Structure:**
1. Experience credential hook: "[Specific number] [thing done] — here's what nobody tells you about [topic]"
2. Single counterintuitive insight early — challenges what the audience thinks they know
3. Specific mechanism: explain why the insight is true using one clear mechanism
4. One takeaway, stated multiple ways
5. Soft CTA embedded in value — "If you want more on this, [soft action]"

**Hormozi script rules:**
- One problem, one insight, one CTA per clip — never more
- Short, declarative sentences. Cut every filler word.
- Every claim should be specific: "I've hired 4,000 people" not "I've hired a lot of people"
- Pattern interrupt every 3–5 seconds (text overlay, caption emphasis, pacing change)
- Scripts are dense; silence and pauses are used intentionally

**Example Hormozi hook vs generic:**
- Generic: "Here's how to get more clients."
- Hormozi: "I've closed $100M in sales. Here are the 3 things I say on every single call."

---

### MrBeast Style (Challenge/Stakes Content)

**Structure:**
1. State the challenge/premise explicitly in the first 5 seconds — no mystery, full transparency
2. Introduce emotional stakes immediately: what happens if they fail/succeed?
3. "Crazy progression" — compress time aggressively; cover multiple stages in the first 90 seconds
4. Each segment escalates: more dramatic than the last
5. Constant "what happens next" energy — every segment ends with a reason to stay
6. Resolution that rewards the full runtime

**MrBeast script principles:**
- Front-load the full premise: tell viewers EXACTLY what the video is about in the first 5 seconds
- The mystery is NOT in the premise — it's in how/whether it resolves
- Emotional investment must be planted within the first 60 seconds
- Scale and stakes matter: the wow factor is a secondary hook that lands after the premise hook

**Adaptation for shorter formats:**
- Use the same front-loaded premise approach
- Plant the stakes in seconds 3–10
- Use a "crazy progression" to compress the journey

---

### Gary Vee Style (Hustle/Mindset)

**Structure:**
1. High-energy direct address: speak to the viewer as if one-on-one
2. Name the core belief or truth immediately
3. Back it with a specific experience or observation
4. Multiple quotable moments — each sentence designed to stand alone as a clip
5. Raw, authentic delivery — imperfection is intentional

**Gary Vee script principles:**
- Emotional authenticity over production polish
- The "stream of consciousness" feel is designed, not random — built around one core insight
- Scripts are often derived from long-form via clipping, not written short-form first
- The energy level is the hook as much as the words

---

### Educational Creator Style (YouTube/TikTok Hybrid)

For creators who mix platform formats:

1. Hook: promise of concrete, actionable value
2. Setup: why this matters, who it's for
3. Numbered structure: "Three things, let's go"
4. Each point: state it → explain it → give one example
5. Summary callback: briefly revisit the three things
6. CTA tied to the content: "If you want the full framework, [action]"

---

## Platform-Specific Adaptations

### TikTok
- **Audio is king**: Script must sound natural spoken aloud — read every word out loud before finalizing
- **Trends integrate**: Incorporate trending sounds, phrases, or formats where authentic to the content
- **Pacing**: Faster than Instagram; viewers are trained to skip quickly — never waste a second
- **Comment hook**: Structure something that invites disagreement or "I needed this" — comment engagement drives algorithm
- **Captions**: Required — treat on-screen text as part of the script, not an afterthought

### Instagram Reels
- **Visual first**: Many viewers watch with sound off, especially in feed
- **Text overlays**: Should carry the full narrative even without audio
- **Saves over comments**: Content that people want to reference later performs well — "save this" content
- **Length sweet spot**: 15–30 seconds for discovery; 60–90 seconds for warm audiences
- **Aesthetic**: Slightly higher production quality expectation than TikTok

### YouTube Shorts
- **Thumbnail-hook alignment**: The hook must fulfill the thumbnail promise exactly
- **Series structure**: Ending with "Part 2" drives subscribers and return views
- **Educational angle**: YouTube audience skews toward information-seeking behavior
- **Completion rate**: Full watch is more important than any other metric
- **Subscribe CTA**: More natural and effective on YouTube than other platforms

---

## Short-Form Script Templates

### Template 1: Educational (30 seconds)

```
HOOK (0–3s):
[Specific counterintuitive claim or number hook]
TEXT: [Reinforce the hook in 5 words]

BODY (3–23s):
[Point 1 — state it, one sentence explanation]
[Point 2 — state it, one sentence explanation]
[Point 3 — state it, one sentence explanation + the "but here's the key thing"]

CTA (23–30s):
[Action tied to the content] / TEXT: [Reinforce CTA]
```

### Template 2: Story/Transformation (60 seconds)

```
HOOK (0–3s):
[Story moment at peak tension or outcome]

SETUP (3–15s):
[Who I was before / the problem I had / the struggle]

TURNING POINT (15–35s):
[What changed / what I discovered / the insight]

RESULT (35–50s):
[Specific outcome with real numbers and timeframe]

CTA (50–60s):
[Natural next step — comment, save, follow]
```

### Template 3: List (45 seconds)

```
HOOK (0–3s):
"[X] things that [outcome] — I wish I knew these sooner"

INTRO (3–8s):
[Brief credibility statement + what they'll get]

ITEM 1 (8–18s):
"Number one: [specific actionable point]"
[One-sentence explanation or example]

ITEM 2 (18–28s):
"Number two: [specific actionable point]"
[One-sentence explanation or example]

ITEM 3 (28–38s):
"Number three: [specific actionable point] — this one is the most important"
[Slightly longer payoff]

CTA (38–45s):
[Save or comment CTA tied to the list]
```

### Template 4: Reaction/Contrast (30 seconds)

```
HOOK (0–3s):
"Most people [wrong approach]. Here's what actually works."

CONTRAST (3–18s):
"The way most [audience] do it: [wrong approach in 2 sentences]"
"The way [result people want] do it: [right approach in 2 sentences]"
"The difference: [one-sentence mechanism]"

CTA (18–30s):
[Engagement prompt or follow CTA]
```


<!-- ═══════ FILE: script-writer/references/ads.md ═══════ -->

# Ad & Marketing Scripts

Complete playbook for paid ads, UGC, VSLs, and brand films.

---

## Table of Contents
1. [Schwartz Awareness Levels — Match Your Entry Point](#schwartz-awareness-levels)
2. [The Direct Response Formula (Facebook/Instagram Ads)](#direct-response-formula)
3. [UGC Script Structure](#ugc-script-structure)
4. [VSL (Video Sales Letter) — 8-Part Structure](#vsl-structure)
5. [Brand Film Structure](#brand-film-structure)
6. [Framework Quick Reference](#framework-quick-reference)
7. [Templates](#templates)

---

## Schwartz Awareness Levels

**The most important concept in ad scriptwriting.** Match your script's entry point to where your audience actually is. Wrong entry point = wasted script.

| Level | % of Market | What They Know | Script Strategy |
|-------|-------------|----------------|-----------------|
| **Unaware** | ~60% | Don't know they have the problem | Evocative storytelling. Never mention product. Create recognition of the problem first. |
| **Problem Aware** | ~20% | Know the problem, not the solution | Empathy + agitation + hint at mystery. Name the pain specifically. |
| **Solution Aware** | ~10% | Know solutions exist, not yours | Comparison. Why your method is different. Focus on mechanism. |
| **Product Aware** | ~7% | Know your product, not yet convinced | Direct. Proof, guarantee, differentiators, offer details. |
| **Most Aware** | ~3% | Ready to buy, need the offer | Just the offer. Price, deadline, reason to act now. |

**Critical mistake:** Most brands default to scripting for "most aware" audiences when 80% of their ad traffic is actually at "unaware" or "problem aware." This kills conversion.

**Cold traffic (new audiences):** Aim for Problem Aware entry. Establish the pain first.
**Retargeting (warm audiences):** Aim for Solution Aware or Product Aware. Assume they know the problem.

---

## Direct Response Formula

The standard structure for all performance-focused video ads (15–60 seconds):

**Hook → Problem → Agitate → Solution → Value Props → Social Proof → CTA**

### 1. Hook (0–3s)
Must stop the scroll before a single claim is made. See `hooks.md` for full formula library.

**Highest-performing ad hook categories:**
- Visual before/after (show transformation immediately)
- Pattern interrupt + direct address ("Stop scrolling if you...")
- Bold result claim ("This generated $47k in 3 weeks")
- Shock stat ("75% of [audience] are making this mistake right now")

**Avoid:** Starting with brand logo, brand name, product name, or "Hi, I'm [name]"

### 2. Problem Identification (3–12s)
Make the viewer feel understood. The goal: they say "that's exactly me."

**Templates:**
- "If you're like me and you've tried every [category] but always [negative outcome]..."
- "75% of [target audience] struggle with [specific problem]..."
- "When you love [desired outcome] but [current painful situation]..."

Identify the problem at three levels:
- **External** (practical surface problem)
- **Internal** (how it makes them feel)
- **Philosophical** (why it's wrong that this exists)

The internal problem is where emotional resonance lives. Most ads only hit external.

### 3. Agitation (Integrated, 3–20s)
Make the problem feel bigger than the viewer had acknowledged. Show the downstream costs.

**Agitation dimensions:**
- **Time cost**: "You're spending 3 hours a day on this..."
- **Money cost**: "This is what's bleeding your budget every month..."
- **Opportunity cost**: "While your competitors are doing X, you're still..."
- **Identity cost**: "You got into this to [original dream], not to [current frustrating reality]..."

The agitation phase is the most skipped in most ad scripts. Without it, the solution has no emotional weight.

### 4. Solution Introduction (12–20s)
Transition naturally, not with a sudden pivot. The solution should feel like relief, not a pitch.

**Transition types:**
- Discovery: "Then a [credible person] told me about [product]..."
- Organic: "After seeing this everywhere, I finally tried [product]..."
- Insight: "Turns out the whole problem was [mechanism] — and [product] fixes exactly that..."

Name the mechanism (why this works when other things haven't). The mechanism is what makes your solution feel different, not just "better."

### 5. Value Props (20–30s)
Two or three specific differentiators, framed as benefits and transformation — not features.

**Feature → Benefit → Deeper Benefit:**
- Feature: "256GB storage"
- Benefit: "Store everything"
- Deeper benefit: "Never delete a memory again"

Always speak the deeper benefit. Specific timeframes and numbers beat adjectives:
- Weak: "Get results fast"
- Strong: "Most customers see results within 72 hours"

### 6. Social Proof (30–40s)
Even one specific customer result with real numbers outperforms ten minutes of feature explanation.

**Proof formats:**
- Testimonials on screen (green screen effect while talking)
- Named customer: "Sarah, a single mom from Ohio, paid off $43k in debt using this"
- Authority endorsement: "Used by 12,000 businesses in 40+ countries"
- Stats: "4.8 stars from 14,000 verified reviews"

**What makes proof work:**
- Specific, named, relatable person (not vague "customer")
- Before state included + specific after state
- Numbers, timeframes, details — not "I love it so much"

### 7. CTA (Final 5–10s)
One action only. Add urgency — a real reason to act now.

**CTA + urgency templates:**
- "Use code [X] for 20% off — offer ends [specific date]"
- "Click the link before we sell out again"
- "Book your free consultation — we only have [X] spots this month"
- "Link in bio — free shipping for the next 48 hours"

**The 4 U's test for CTAs:**
- Urgent: Why act now?
- Unique: Is the offer distinct?
- Ultra-specific: Exact action + timeframe?
- Useful: Is there clear value in clicking?

---

## UGC Script Structure

UGC ads convert because they feel like organic content. The line between UGC that performs and UGC that doesn't comes down to one thing: does it sound like a person talking to a friend, or a company talking to a customer?

**Core UGC structure (20 seconds / ~60 words):**

```
[Hook — first-person story opening, 0–3s]
[Problem stated as personal experience, 3–8s]
[Discovery of the product, 8–13s]
[Specific result + 1 key differentiator, 13–18s]
[Recommendation + CTA, 18–20s]
```

**UGC tone rules:**
- Short sentences. How you'd actually text a friend.
- First-person "I" statements throughout
- Normal vocabulary — no buzzwords ("leverage," "synergy," "game-changing")
- Name the product naturally mid-sentence: "I tried [Product] and..." — not as an announcement
- Imperfect delivery is a feature — natural pauses, slight stumbles, looking off-camera

**Platform-specific UGC:**
- **TikTok**: Audio-first. Current trends, sounds, and formats. Fast pacing.
- **Instagram/Facebook**: Visual-first. Many viewers watch muted — captions are essential. Visual hooks (before/after) carry more weight.

**Five UGC script failures:**
1. Sounds scripted — too polished, perfect diction, no natural speech patterns
2. Same script used on all platforms without adaptation
3. Weak hook (starting with product name or "Hi I'm...")
4. Generic value props ("it's amazing, I love it") — no specifics
5. Passive CTA with no urgency ("you can check it out" instead of "link is in bio")

---

## VSL Structure

A Video Sales Letter is a long-form persuasion video (5–30 minutes) that replaces a traditional sales page. It follows direct response copywriting principles applied to video. High-ticket offers ($500+) often need the full structure.

### The 8-Part VSL Framework

**Part 1: Hook (0–60s)**
Big promise, provocative question, shocking stat, or pain-point statement. The hook is the highest-stakes section. Lead with the single biggest benefit or the single most painful problem.

Script notes:
- Don't open with who you are or your company name
- Open with the viewer's desired outcome or their worst fear
- The first sentence must earn the next 30 seconds of attention
- Common: problem-first hook, dream outcome hook, shocking result hook

**Part 2: Problem Identification (1–3 min)**
Describe the problem in vivid, specific detail. Include:
- The external problem (practical surface issue)
- The internal emotional experience ("I felt like a fraud every time...")
- The villain frame: who or what is to blame (complexity, bad information, the industry, broken tools)

The viewer must think: "How are they describing my exact situation?"

**Part 3: Agitation (integrated into Part 2)**
Expand the cost of the problem:
- Time cost, money cost, relationship cost, health cost, opportunity cost
- The "what if nothing changes" scenario — what does their life look like in 2 years if this isn't solved?
- This section separates "nice to have" from "I need to fix this now"

**Part 4: Credibility / Authority (1–2 min)**
Who are you and why should anyone listen?

**The Origin Story structure:**
1. "I was in your exact situation..." (builds empathy, establishes stakes)
2. "I tried everything and nothing worked..." (establishes authority through shared struggle)
3. "Until I discovered [mechanism/insight/approach]..." (the turning point)
4. "And the results changed everything..." (specific results with numbers)

**Credibility signals to include:**
- Specific experience numbers (years, clients, dollars, outcomes)
- Third-party recognition (press, awards, testimonials from credible sources)
- Social proof volume (customers, reviews)
- The one specific result that proves the method works

Avoid: titles without context, vague claims, "I'm an expert in..."

**Part 5: Solution / Mechanism (2–5 min)**
Introduce the solution and — critically — name the mechanism.

The mechanism is the specific reason why your solution works where other things have failed. It should feel novel, logical, and actionable.

**The mechanism framework:**
- What most people try: [common approach and why it fails]
- The insight that changes everything: [the reframe]
- Why [your mechanism] works differently: [specific explanation]
- Give the mechanism a name (makes it memorable and ownable)

Then walk through the solution components — not as a feature list but as chapters in the viewer's transformation story.

**Part 6: Proof Stack (2–4 min)**
No proof = low conversion. Even one specific result with real numbers beats ten minutes of explanation.

**Proof format that converts:**
1. Before state: who they were, what they struggled with (relatable, specific, named)
2. The turning point: what they did differently
3. After state: specific results with numbers, timeframes, and life impact

**Proof types, strongest to weakest:**
1. Video testimonial with specific numbers and real person
2. Case study with named individual and documented results
3. Screenshots of results (with context)
4. Statistics with source
5. Named endorsements from credible figures
6. Review volume and star ratings
7. Vague testimonials

**Part 7: The Offer (1–2 min)**
Structure the offer to maximize perceived value:

1. Name each component + individual value
2. Stack the total (show the aggregate number)
3. Reveal the actual price (anchored against the stack)
4. Remove risk: the guarantee (specific, strong, low-friction)
5. Add scarcity: limited availability, time-bounded bonus, logical reason for urgency

**Part 8: CTA + Urgency (30–90s)**
Single, specific action. Create genuine (not manufactured) urgency. Repeat the CTA 2–3 times.

"What happens when you click [button/link]:" — walk them through the next step. Reducing unknown = reducing friction.

---

## Brand Film Structure

Brand films (60 seconds–5 minutes) prioritize emotional affinity over direct response. The goal is to create a story the viewer remembers and shares.

### The StoryBrand Framework for Brand Films

**The core insight:** Your brand is the guide, not the hero. Your customer is the hero. Most brand films fail because they put the brand at the center of the story.

**The 7-part BrandScript:**
1. **A character (your customer)** wants something specific — one thing, not everything
2. **Has a problem** — at three levels: external (practical), internal (emotional), philosophical (this shouldn't exist)
3. **Meets a guide** — your brand, with empathy ("I understand") + authority ("I can help")
4. **Who gives them a plan** — 2–3 simple steps (complexity kills)
5. **And calls them to action** — direct CTA + transitional CTA
6. **That helps them avoid failure** — name the stakes
7. **And ends in success** — the vivid promised land

**Brand film timing (90-second version):**
```
0–10s: Establish the hero (your customer) in their world
10–20s: Name the problem — external + hint at internal
20–30s: Brand enters as guide (empathy + authority)
30–45s: The plan / the solution shown in action
45–65s: Transformation demonstrated — "after" state
65–80s: Stakes + success vision
80–90s: CTA
```

### Emotional Journey Framework for Ads

Map the emotional arc the viewer should travel:

| Phase | Time | Target Emotion |
|-------|------|----------------|
| Resonance | 0–15s | "This person gets me" |
| Agitation | 15–30s | Urgency, desire for change |
| Aspiration | 30–50s | Hope, excitement, want |
| Credibility | 50–70s | Trust, risk removed |
| Action | Final 10–15s | Decisiveness, momentum |

---

## Framework Quick Reference

| Framework | Best For | Core Structure |
|-----------|----------|----------------|
| AIDA | Cold audiences, brand awareness, any format | Attention → Interest → Desire → Action |
| PAS | High-ticket, pain-aware audiences | Problem → Agitate → Solution |
| BAB | Transformations, testimonials, UGC | Before → After → Bridge |
| 4 P's | Any persuasion video | Promise → Picture → Proof → Push |
| VSL | High-ticket sales ($500+) | 8-Part structure above |
| StoryBrand | Brand films, brand identity | 7-Part BrandScript |
| Direct Response | Paid ads, short-form ads | Hook → Problem → Agitate → Solution → Proof → CTA |
| UGC | Organic-feeling paid ads | Personal story → Discovery → Result → CTA |

---

## Templates

### Template: 30-Second Facebook/Instagram Ad

```
[HOOK — 0–3s]
[Pattern interrupt visual] + "Stop scrolling if you [specific identity/problem]."

[PROBLEM — 3–10s]
"If you're like most [audience], you're [specific frustrating situation]. And it's costing you [cost]."

[SOLUTION — 10–18s]
"[Product] is [category] that [mechanism] — so you can [outcome] without [sacrifice]."

[PROOF — 18–24s]
"[Specific customer] went from [before] to [specific after] in [timeframe]."
OR: "[Number] customers. [Star rating] stars. [Quick proof point]."

[CTA — 24–30s]
"[Link in bio / Tap here] — [specific reason to act now]."
```

### Template: 20-Second UGC Script

```
[HOOK — 0–3s]
"Okay I have to tell you about [thing] because I've been obsessed with it."

[PROBLEM — 3–8s]
"I was struggling with [specific problem] — like [relatable specific detail]."

[DISCOVERY — 8–12s]
"Then I found [Product] and honestly I was skeptical at first but [what changed]."

[RESULT — 12–17s]
"Now [specific result] in [timeframe]. [One specific thing that makes it different]."

[CTA — 17–20s]
"Link in bio if you want to try it — [urgency reason]."
```

### Template: 60-Second Brand Film (StoryBrand)

```
[SETUP — 0–10s]
[Show customer in their world. Visual storytelling only. No voiceover yet.]

[PROBLEM — 10–20s]
VO or dialogue: "We all know [the external problem]. But what really hurts is [the internal problem]."

[GUIDE ENTERS — 20–30s]
"That's why we built [Brand] — because [belief/empathy statement] + [one authority statement]."

[PLAN/SOLUTION — 30–45s]
"[Step 1], [Step 2], [Step 3] — and then [vision of the promised land]."
[Show the product working visually]

[SUCCESS / TRANSFORMATION — 45–65s]
[Testimonial, before/after, or demonstration — emotional peak]

[CTA — 65–90s]
"[Brand] — [one-line positioning]. [Direct CTA]. [Website/link]."
```


<!-- ═══════ FILE: script-writer/references/pro-copywriting.md ═══════ -->

# Pro Copywriting: Master Techniques for AI Campaign Hooks

The masters didn't write for AI tools — but the principles they discovered are timeless because they are grounded in how the human brain processes persuasion. This file applies their techniques specifically to short-form AI campaign hooks.

---

## The Foundational Insight (Schwartz)

> "Copy cannot create desire for a product. It can only take the hopes, dreams, fears and desires that already exist in the hearts of millions of people, and focus those already existing desires onto a particular product."
> — Eugene Schwartz, *Breakthrough Advertising*

AI is not the desire. What viewers already want is: to grow faster, look more professional, stop wasting budget, compete with better-funded rivals, spend less time on work they find tedious, and make things that impress people. The hook's first job is to locate the desire that already exists, then channel it toward what the AI can do.

**In practice:** Lead with the pre-existing desire, not the product capability.
- ❌ "imagine.art lets you generate photorealistic product images"
- ✓ "Stop losing clients to agencies with bigger budgets. One tool changed that for me."

---

## Principle 1: Awareness Level Matching (Schwartz)

Before writing a single word, identify where your audience is on the awareness spectrum. The wrong hook for the wrong awareness level is the most common failure in AI campaign copy.

### The 5 Levels — What to Say at Each

| Level | What They Know | Hook Strategy | Example |
|---|---|---|---|
| **Unaware** (60% of cold traffic) | Don't know they have the problem | Lead with emotion, story, or a provocative truth. No product. | "Why does every small brand look the same in their marketing?" |
| **Problem Aware** (20%) | Have the problem, don't know solutions exist | Name the problem exactly. Make them feel seen. | "Still spending 3 hours on one product photo?" |
| **Solution Aware** (10%) | Know solutions exist, not yours | Name the category, position yours as better | "AI image tools are everywhere now — but most can't do this." |
| **Product Aware** | Know imagine.art, not convinced | Address the specific objection. Show proof. | "I thought AI photos looked fake. Then I saw this." |
| **Most Aware** | Ready — needs a trigger | Social proof, direct CTA, price anchor | "40,000 brand owners use this. Here's why." |

**The most common error:** Running a product-aware hook on cold unaware traffic. The viewer has no context for what you're selling or why it matters. You earn zero attention because you're solving a problem they don't know they have.

**Cold traffic rule:** If you're running TikTok FYP or Instagram Reels to cold audiences, your hook must reach unaware or problem-aware people. Start with their world, not your product.

---

## Principle 2: Enter the Conversation Already in Their Head (Halbert)

Gary Halbert's A-Pile/B-Pile principle: everything gets sorted instantly into "personal and worth reading" vs. "obviously selling me something." The B-Pile gets ignored. The only way into the A-Pile is to sound like you know this specific person.

The diagnostic test: read your hook out loud. Does it sound like something a friend who understood your exact situation would say? Or does it sound like it was written for a demographic?

**The technique: Name the specific situation, not the category.**

- ❌ "For e-commerce brand owners" (demographic)
- ✓ "If you just got a $2,800 quote from a product photographer" (situation)
- ❌ "For content creators" (demographic)
- ✓ "If you've been reusing the same three product photos for six months because you can't afford a reshoot" (situation)

The situation puts the viewer inside a specific moment they've actually lived. The demographic describes a label they may not even identify with.

**Halbert's Starving Crowd test:** The best copy finds people who are already hungry, then gives them exactly what they want. Before writing a hook, ask: who is starving right now, and for what exactly?

---

## Principle 3: The Slippery Slide — Structure for Completion (Sugarman)

> "The sole purpose of the first sentence is to get you to read the second sentence."
> — Joe Sugarman

Every element of a hook — and every element of the body — has one job: earn the next element. Not deliver the message. Not impress. Not inform. Earn.

**What this changes about how you write:**

Each line must open a loop or plant a seed that the next line satisfies or deepens. If a sentence can stand alone as a complete thought with no forward tension, it breaks the slide.

**Slide structure for a 30-second video:**

```
HOOK (0–1.5s): Opens a loop — something incomplete or contradictory
LINE 2 (1.5–5s): Deepens the loop — adds a detail that makes it more interesting
LINE 3 (5–15s): Partial payoff — closes one loop, opens another
LINE 4 (15–25s): The mechanism — how it works, but not the full reveal
CLOSE (25–30s): Full payoff + CTA
```

**Seeds of curiosity (Sugarman's micro-hooks between sections):**
- "But there's something else here."
- "And this is the part most people miss."
- "Here's what actually surprised me."
- "Before I show you that — look at this."
- "I'll explain why in a second, but first —"

These phrases are designed to keep someone watching when their attention is drifting. Use one at every major transition in a script.

**Involvement devices — the pattern interrupt that doubles engagement:**
Sugarman found that asking viewers to perform a small mental or physical action before the payoff dramatically increased engagement and conversion. Applied to video:
- "Pause this and look at your last product photo. Ready?"
- "Comment 'yes' if this sounds like your situation."
- "Before I show you the result — what would you guess this cost?"

The involvement device creates a tiny investment before the reveal. The viewer who pauses or comments is now participating, not watching. Their brain processes what follows as more credible.

---

## Principle 4: Specificity is Proof (Hopkins + Ogilvy)

Vague claims have zero weight. The brain classifies "stunning quality," "professional results," and "game-changing AI" as marketing noise and discounts them automatically.

Specific numbers, durations, names, and processes are processed as facts.

> "Platitudes and generalities roll off the human understanding like water from a duck. Specific claims make people realize that tests and comparisons have been made."
> — Claude Hopkins

**The Schlitz Principle (Hopkins):** When every competitor makes the same claim ("professional quality," "high resolution," "true-to-life color"), describe the process behind the claim specifically. You don't have to be unique — you just have to describe it first.

Examples:
- "Our model was trained on licensed commercial photography from 14 industries" vs. "high-quality AI image generation"
- "Every generation runs through 6 quality evaluations before it reaches your screen" vs. "professional-grade output"
- "We retrain on new photography styles every 8 weeks" vs. "constantly improving AI"

**Odd numbers beat round numbers.** This is counterintuitive but tested: "47 product images" is more credible than "50 product images." Odd specific numbers signal that someone actually counted. "8 seconds" beats "under 10 seconds" every time.

**Ogilvy's Big Idea Test:** Every campaign needs one specific, surprising, sensory detail that makes the central benefit undeniable. Not a list of features. One detail that makes the viewer stop and say "wait, really?"

Finding your Big Idea: spend time with the product until one true, specific, surprising thing surfaces that competitors have never said. The Rolls-Royce line ("At 60 miles an hour the loudest noise is the electric clock") describes silence, precision, and luxury without using any of those words.

What is the imagine.art equivalent? What is one true, specific thing about what it produces that competitors haven't named?

---

## Principle 5: The IF…THEN Disarmament (Bencivenga)

The skepticism reflex fires when a big claim appears without context. The IF…THEN structure disarms it by making the entry condition reasonable and easy, then delivering the extraordinary promise.

> "If you've got 20 minutes a month, I guarantee to work a financial miracle in your life."

The "if" clause is trivially achievable. The "then" clause is extraordinary. The gap creates irresistible tension without triggering disbelief.

**Template:** "If you can [easy, reasonable action], I can show you [extraordinary result] in [specific time]."

**Applied to AI campaign hooks:**
- "If you can describe a scene in a sentence, I can turn it into a product image in 30 seconds."
- "If you have a photo of your product and 2 minutes, here's what I made with imagine.art."
- "If you can type what you want, this tool removes every other step between you and a campaign-ready visual."

**Fascination bullets as standalone hooks.** Bencivenga called these "bullets that kill." Each bullet is a complete promise with a hint of mystery. They work as body copy, but the best ones are strong enough to serve as hooks.

Rules for fascination bullets:
1. Specific + surprising — the combination that creates curiosity
2. Benefit in the claim, mystery in the mechanism ("why X happens" not "X happens")
3. Lead with the reward, not the effort
4. Parallel construction if using multiples — rhythm is part of the persuasion

**Examples:**
- "The specific prompt structure that produces editorial-quality lighting — every time"
- "Why 'realistic' is the wrong word when prompting product photography (and what to use instead)"
- "The 3-word addition that stops AI images from looking like AI images"
- "What professional photographers notice about AI images — and how to hide it"

---

## Principle 6: The Reversal Structure (Caples)

John Caples' most famous ad: **"They Laughed When I Sat Down at the Piano — But When I Started to Play!"**

This is a complete persuasion architecture in one sentence:
1. **Social skepticism** — "they laughed" — signals a relatable experience of doubt. The viewer feels the embarrassment.
2. **A specific moment** — "when I sat down" — grounds it in an actual scene, not an abstract situation.
3. **The reversal** — "but when I started to play" — the cliffhanger. The viewer must read on.
4. **Implied transformation** — the person who was laughed at became impressive. The viewer wants that.

**The structure:** [Social doubt or mockery] → [Specific moment] → [Reversal/Reveal]

AI campaign application:
- "My agency laughed when I said I was replacing our photo studio with AI. Six weeks later, I showed them the client results."
- "They said AI images look fake. I put one in our campaign. Here's what happened."
- "My photographer told me AI could never match what she does. Then I showed her this."

**Why this works for AI specifically:** The skepticism → conviction journey is the exact emotional arc most AI customers take before buying. Mirroring that arc in the hook makes the content feel like it was written for them.

**Caples' tested insight:** Self-interest beats curiosity for conversion. Hooks that clearly answer "what's in this for me?" outperform mysterious hooks when the goal is action, not just views. Optimize curiosity hooks for reach; optimize self-interest hooks for trial and conversion.

---

## Principle 7: Agitation Before Solution (Kennedy + Halbert)

The PAS formula (Problem → Agitate → Solution) is widely known. The Agitation step is almost universally skipped. This is the most expensive copywriting error in AI campaign content.

**What agitation does:** It makes the problem feel urgent, costly, embarrassing, and personally relevant before offering the solution. Without agitation, the solution arrives before the viewer is ready to want it. With agitation, the solution feels like relief.

**Kennedy's diagnostic questions — use these to find your agitation:**
- What keeps this person awake at night about this problem?
- What is the financial cost of not solving it this month?
- What is the social/competitive cost? Who is winning while they're losing?
- What do they feel every time they deal with this problem?
- What have they tried before that didn't work?

**Structure:**
```
Problem:    "Creating product content is slow and expensive."
Agitation:  "It costs $2,000 a shoot. Takes 3 weeks to schedule. 
             Meanwhile your competitors refresh their content weekly.
             And you're posting the same photo for the fourth month in a row."
Solution:   "Here's how I generate 40 fresh product visuals in an afternoon."
```

The three agitation sentences above make the problem feel:
- Financially painful ($2,000)
- Time-inefficient (3 weeks)
- Competitively threatening (competitors are winning)
- Personally embarrassing (same photo, fourth month)

Only after that sequence does the solution land as a genuine relief.

**Compressed PAS for a 1.5-second hook:**
The full agitation belongs in the body. In the hook, compress PAS into a single sentence:
- "You're spending $2,000 on product shoots your competitors replaced with AI last year." (Problem + Agitate in one sentence — implies both the cost and the competitive disadvantage.)

---

## Principle 8: Future Pacing

Take the viewer mentally into the future where they have already made the decision — and describe what they experience there.

The brain responds to vividly described future states as if they are real. If you can make someone feel what their life looks like after adopting the product, the decision feels like confirmation rather than risk.

**Technique:** Move from "here's what this does" to "imagine the first time you..." or "picture your next product launch where..."

**Examples:**
- "Imagine opening the app on the morning of your launch and having 30 campaign-ready images waiting — at the cost of zero dollars and 12 minutes of your time."
- "Picture submitting your product shots to your client this week — all 40 of them — and seeing their reaction when you tell them you generated them the same morning."
- "Three weeks from now: no shoot scheduled, no photographer invoice, no waiting. Just the images you need, exactly when you need them."

Future pacing is especially powerful for AI tools because the barrier isn't disbelief — it's imagination failure. Most prospects can't visualize how the tool would fit their actual workflow. Future pacing does that work for them.

---

## Principle 9: Language Mirroring

The most credible copy uses the exact words the audience uses to describe their own problem — not the words the brand uses to describe its solution.

**How to find the language:**
- Reddit threads where your audience describes frustrations
- 1-star reviews of competitor products (what people say when genuinely angry)
- Support ticket language
- Comments on competitor content
- Onboarding survey responses

**Example (brand language vs. audience language):**

| Brand Language | Audience Language |
|---|---|
| "high-quality AI image generation" | "images that don't look fake" |
| "professional-grade output" | "something I'd actually post" |
| "streamlined creative workflow" | "I'm tired of waiting on my designer" |
| "cost-effective content creation" | "I'm sick of paying $3,000 for a shoot" |

The brand language describes what the product does. The audience language describes how the problem feels. Hooks written in audience language create immediate recognition — "this was written for me" — which is the precondition for trust.

---

## Principle 10: Sentence Rhythm as a Persuasion Tool

Rhythm is not decoration. It is a mechanism that controls the reader's pace, emotional state, and perceived credibility.

**The pattern that builds momentum:**
Short. Then short. Then a longer sentence that carries the reader forward into the idea, building speed as you go. Then stop.

This is not accidental. Short sentences create impact. They hit like facts. Long sentences build reasoning, pull the reader through logic, and earn the arrival at the conclusion. Fragments work. They feel direct. Honest.

**Techniques:**
- **The dash** — use it to create urgency and forward lean — like this
- **The fragment.** No verb needed. Just the thing.
- **The reversal sentence:** "Most tools give you features. This gives you time."
- **The echo:** "The image you needed. The time you didn't have. Both solved."
- **The short hard stop:** Start long. Then cut. Dead stop.

**What this sounds like in a hook:**
- ❌ "imagine.art is an AI-powered image generation platform that enables e-commerce brands to create high-quality product photography without professional photographers."
- ✓ "Product photography without a photographer. No studio. No invoice. Just a prompt and 30 seconds."

The second version uses fragments, parallel structure, and a payoff at the end. Every clause is doing one job and stopping.

---

## What's Dead in 2026: Avoid These

Based on 2026 campaign data, these patterns are fatiguing audiences and suppressing performance:

1. **Generic "AI replaced X" without specificity.** "I replaced my video editor with AI" — ignored. "I cut the specific 3-hour export-and-caption step to 8 minutes using one tool" — still works.

2. **"This will change everything" / "The future is here" framing.** Consumer AI enthusiasm dropped from 60% in 2023 to 26% in 2025. The hype register is a credibility kill.

3. **Polished AI UGC with obviously synthetic voiceover.** Audiences have pattern recognition for this. They scroll it on sight.

4. **Generic capability lists.** "This AI can write, design, translate, and more." No one cares. Specificity of one task beats breadth of ten tasks every time.

5. **Unlabeled AI content.** Policy enforcement + trust erosion = suppressed distribution and credibility damage.

6. **Leading with the tool name in the hook.** Cold audiences don't know or care about your product name. Lead with their situation. Reveal the product name after you have their attention.

---

## The 2026 Algorithm Checklist

Before finalizing any TikTok or Reels hook:

- [ ] **Completion bait built in?** The payoff must be unreachable by skipping.
- [ ] **Rewatch trigger designed?** A loopable ending or detail worth re-examining pushes toward the 20–30% rewatch target.
- [ ] **Sound-off hook?** The text overlay must carry the entire hook for silent viewers. 80% of viral clips burn in captions.
- [ ] **TikTok search keywords in caption?** TikTok is now a search platform — keyword captions improve visibility 20–40%.
- [ ] **DM-share worthy for Reels?** Instagram's #1 ranking signal is DM shares. Design content that makes someone say "you need to see this."
- [ ] **Creative refresh scheduled?** TikTok ads fatigue in 7–10 days. Build a testing pipeline, not a single video.
- [ ] **Awareness level matched?** Cold traffic gets problem-aware or unaware hooks. Don't run product-aware hooks to cold audiences.

---

## The B2B vs. B2C Hook Distinction

For imagine.art's agency and enterprise audience segments specifically:

**B2C hooks (brand owners, solo creators):**
- Lead with cost destruction or time savings — specific numbers, felt immediately
- POV + relatable scenario — "if you've ever..." 
- Demo-first on TikTok: show the output before any explanation
- Platform: TikTok + Reels

**B2B hooks (agencies, creative teams, enterprise):**
- Lead with ROI and team-level impact, not personal workflow
- Problem + competitive threat framing ("your competitors using this are delivering faster at lower cost")
- Case study hook: compressed "how [type of team] uses this to ___" structure
- LinkedIn and YouTube Shorts for B2B; TikTok works for founder/operator persona
- The short-form video is a funnel entry, not the conversion event — hook should direct to longer proof
- Specificity of context: name the exact role, the exact workflow, the exact before/after

---

## Quick Reference: The 8 Masters

| Master | Single Most Applicable Principle | Applied to a Hook |
|---|---|---|
| **Gary Halbert** | Enter the conversation in their head | Name their specific situation, not a demographic |
| **Eugene Schwartz** | Match awareness level before writing anything | Cold traffic needs emotion/story; warm needs product proof |
| **Joe Sugarman** | Every sentence earns the next | Structure the entire script as a slide — no complete thoughts that don't pull forward |
| **Claude Hopkins** | Specificity is proof; preempt with process | Name the process behind your quality claim before competitors do |
| **David Ogilvy** | Find the one Big Idea — then show, don't claim | One specific, sensory, verifiable detail that makes the benefit undeniable |
| **John Caples** | Self-interest > curiosity for conversion | Test self-interest hooks for trial CTAs; curiosity hooks for reach |
| **Gary Bencivenga** | IF…THEN disarms skepticism | "If you can type a sentence, I'll show you a campaign-ready image in 30 seconds" |
| **Dan Kennedy** | Flag the one person + agitate before solving | Name the specific painful situation, make it feel worse, then offer relief |


<!-- ═══════ FILE: script-writer/references/retention-engineering.md ═══════ -->

# Retention Engineering — Second-by-Second Watch-Time Design

The hook wins the first 1.5 seconds. This file is about everything after — how to hold a viewer through second 4, second 19, and second 43, where most scripts quietly die. Retention is designed per-second, then verified per-second.

**Pair this file with `emotional-arcs.md`.** Retention devices without an emotional arc are duct tape on a flat script; an arc without retention devices leaks viewers at every transition. Emotion is *why* they stay; devices are *how* you keep re-earning it.

---

## Table of Contents
1. [Anatomy of a Retention Curve](#anatomy-of-a-retention-curve)
2. [The Interest Cadence](#the-interest-cadence)
3. [The Retention Device Taxonomy](#the-retention-device-taxonomy)
4. [Payoff Scheduling](#payoff-scheduling)
5. [Loopable Endings & Rewatch Engineering](#loopable-endings--rewatch-engineering)
6. [Drop-Off Diagnosis](#drop-off-diagnosis)
7. [The Retention Pass](#the-retention-pass)

---

## Anatomy of a Retention Curve

Every short-form retention graph has the same three danger zones:

| Zone | Where | What happens | Typical loss |
|------|-------|--------------|--------------|
| **The Cliff** | 0–3s | Hook verdict. Sound-off scrollers judge frame 1 + overlay. | 40–60% of impressions — normal. Above 65% = hook failure |
| **The Sag** | 25–40% of runtime | Hook promise delivered OR visibly delayed; novelty of premise wears off; viewer asks "is the rest worth it?" | The silent killer — steady bleed, not a cliff |
| **The Exit Ramp** | last 15–20% | Viewer senses wrap-up / smells the CTA coming and leaves "done" | Kills completion-rate bonus at 70%+ / 92%+ thresholds |

**Healthy curve shape:** steep initial drop (unavoidable), then a *plateau* — long flat stretches through the middle — with a flick upward at the very end (rewatch looping registers as >100% on the last seconds). If the middle is a downhill slope rather than a plateau, the script lacks re-hooks. 

**Benchmarks to design against:** 70%+ completion for viral distribution (30s), 50%+ for strong performance at 30–60s, 20–30% rewatch rate. A 60s video needs to be *twice* as retentive per second as a 30s video to hit the same completion percentage — length must be earned, never defaulted.

---

## The Interest Cadence

**A new reason to stay must fire every 3–7 seconds.** Not a new topic — a new *stimulus*: information, visual, audio, or tension. Viewer attention decays on roughly this cycle; each device resets the clock.

Three channels, rotate them (repeating one channel back-to-back halves its effect):

- **Content**: new fact, escalation, open loop, question, contradiction, number
- **Visual**: cut, angle change, new overlay text, B-roll, zoom, new generation on screen
- **Audio**: pace shift, pause, SFX, music entry/exit, volume drop

**The cadence is a floor, not a metronome.** In the sag zone, tighten to every 3–4s. During a payoff moment, let it breathe — interrupting a peak is self-sabotage.

**Text overlay cadence:** static overlay text goes invisible after ~4 seconds. If the same words sit on screen for 10s, the visual channel is dead weight. Change, animate, or remove.

---

## The Retention Device Taxonomy

Ordered roughly by power. Every script should carry 3–5 device *types*, not one type five times.

### 1. The Macro Open Loop
One question the whole video exists to answer, opened in the hook, closed at 80–90%. This is the spine — every other device hangs off it. If the macro loop closes early, the video is over no matter what's left on the timeline.

### 2. Micro Loops (loop chaining)
Small tease → 5–15s later payoff, opened *before* the previous loop closes. The chain rule: **never close a loop without another already open.** "The third one's the one that got me—" (opens) → deliver points one and two (previous loops close) → "okay, the third one" (closes).

### 3. Forward References (seeds)
One-line pointers that make skipping feel costly: "keep your eye on the left side of this frame," "this matters in 20 seconds." Cheap, effective, cap at 2–3 per 60s — beyond that they read as stalling.

### 4. Progress Markers
Numbered structures ("3 things"), step counters, visible progress. Certainty about *shape* makes viewers tolerant of *length* — they stay because they know how much is left. Best structural device for list formats; escalate items so the ladder climbs (see `emotional-arcs.md` Escalating Awe).

### 5. Withheld Specifics
Name that a specific exists, delay its value: "it cost less than a lunch — exact number in a second." The named-but-withheld number is stickier than an unnamed one. Withhold ONE thing at a time; withholding everything reads as clickbait and burns trust.

### 6. Pattern Interrupts
Visual/audio/content whiplash to reset a wandering brain. (Full menu in `short-form.md`.) Use at scheduled sag points, not randomly.

### 7. Involvement Devices
"Pause and guess what this cost." "Comment 'prompt' and I'll send it." Participation converts passive watchers to active ones — active viewers don't scroll. One per script.

### 8. The Vulnerability Beat
One honest, slightly-too-real line at the sag point. Trust reset + attention reset in one move. Rules and placement in `emotional-arcs.md`.

### 9. Silence / Dead Air
A 0.5–1s full-stop before a payoff. The absence of stimulus IS the stimulus. Strongest single-use device; ruined by repetition. (See `audio-hooks.md` silence architecture.)

---

## Payoff Scheduling

Retention isn't about withholding — it's about *scheduling*. Viewers stay when payoffs arrive on a rhythm that keeps trust while preserving the biggest for last:

1. **Pay something early (3–8s).** The first micro-payoff proves the video delivers. All-tease-no-payoff until second 40 = mass exit at second 12 — viewers extrapolate from what you've paid so far.
2. **Ladder the middle.** Each payoff ≥ the previous. A descending ladder (best point first) creates a descending retention curve to match.
3. **Peak at 60–90%.** The macro-loop close, the hero reveal, the number. Never in the first third; never in the final 2 seconds (no room for landing).
4. **After the peak, get out fast.** Peak → one beat of resolution → CTA → end. Every second between peak and end is exit-ramp exposure. The best scripts end almost abruptly.

**The trust ledger:** every open loop is a debt; every payoff is a payment. End the video with all debts paid and the viewer slightly overpaid — that surplus is what converts to follows and shares.

---

## Loopable Endings & Rewatch Engineering

Rewatch (20–30% target) is a primary distribution signal, and the seconds a rewatcher adds count double: they lift average watch time AND completion.

**Four loop mechanics:**

1. **The Seam Loop** — last frame visually matches first frame (same generation, same composition). The replay feels continuous; viewers watch 5+ extra seconds before realizing it restarted. In AI production: reuse Scene 1's generation as the final scene, or generate first/last frames from the same prompt with one changed variable.
2. **The Sentence Loop** — the final spoken line grammatically completes or sets up the opening line. Open: "...and that's exactly why nobody believed this was AI." (which is also how the video began mid-sentence).
3. **The Recontext Loop** — the ending reveals information that changes what the opening meant ("that was AI too"). Viewer rewatches to verify. Highest-intent rewatch; pairs with the Recontextualization arc shape.
4. **The Detail Callback** — "watch it again — it's in the first frame the whole time." An explicit, earned rewatch instruction. Only works if the detail is really there and really findable.

**Frame-one density:** rewatch also rises when frame one contains more than one viewing can absorb — a grid of outputs, fast text, layered visuals. Design frame one for the second viewing, not just the first.

---

## Drop-Off Diagnosis

When analytics show where viewers leave, the location names the disease:

| Drop location | Diagnosis | Fix |
|---|---|---|
| 0–1.5s, above ~65% | Hook failure: frame 1 static, overlay weak, or premise unclear | Rewrite hook — `hook-editing.md`. Demo-first check. Overlay carries hook sound-off? |
| 2–5s | Hook wrote a check the next line doesn't cash — filler transition after strong hook | Delete the transition. Body line 1 must advance the hook's promise directly |
| Steady bleed through middle | No interest cadence — stretches >7s with no new stimulus; or flat emotional valence | Run the Retention Pass below. Add micro-loops; break the flatline (`emotional-arcs.md`) |
| Sharp cliff mid-video | A specific scene killed it: topic pivot viewers didn't sign up for, energy crash, over-explained point, or early macro-loop close | Find the timestamp, cut or compress that scene. Was the video's question already answered? |
| Cliff right after a payoff | Payoff scheduling error: biggest value delivered with runtime left and no loop open | Move peak later, or open a new loop BEFORE that payoff closes |
| Last 10–15% | Exit ramp: CTA telegraphed, energy died post-peak | Compress peak→end gap. Loop mechanic instead of wind-down CTA |
| Completion fine, rewatch low | Ending resolves too cleanly — nothing pulls back to frame one | Add a loop mechanic (seam, sentence, recontext) |
| High retention, low shares | Peak not extractable — no moment that works out of context | Make the peak screenshot-able/clip-able; put the key visual + claim in the same frame |

---

## The Retention Pass

Run this as a separate editing pass on every script over 20 seconds, after the copy is written and the emotional arc is mapped:

1. **Timestamp the script.** Word count ÷ 2.5 ≈ seconds per line at ~150 WPM. Mark 5-second windows.
2. **Audit each window.** Something new firing in every 3–7s window? Name the device and channel (content/visual/audio). Any window with nothing = a leak. Fix it or cut it.
3. **Check channel rotation.** Same channel 3+ times consecutively? Swap one.
4. **Trace the loops.** Macro loop: where opened, where closed? Is a micro-loop open at every moment of the script? Close-before-open gaps are exit points.
5. **Check the payoff ladder.** List payoffs in order with rough weight. Ascending? Peak at 60–90%?
6. **Cut the un-missable.** For each line ask: if this line vanished, would the viewer notice a gap? No = cut. Shorter with the same payoffs beats longer, always.
7. **Time peak→end.** More than 8 seconds between peak and final frame = compress.
8. **Verify the loop mechanic.** Which of the four is in play? "None" = leaving rewatch rate on the table.

**Output notation** — mark devices inline in the Step 7 template so they're visible per scene:

```
SCENE 4 — AGITATION (18–26s)
[EMOTION] frustration (7)
[RETENTION] micro-loop open: "the invoice line nobody reads" | visual: cut to invoice close-up
```


<!-- ═══════ FILE: script-writer/references/emotional-arcs.md ═══════ -->

# Emotional Arc Engineering — The Felt Journey of a Script

The hook gets the viewer in. The emotional arc keeps them there. A script with a great hook and a flat middle dies at the 30% mark — the analytics say "retention problem," but the cause is almost always an emotion problem.

**Core principle: retention is the metric, emotion is the mechanism.** Viewers don't stay because information is coming. They stay because they are *feeling something that hasn't resolved yet.*

---

## Table of Contents
1. [Write the Felt Journey First](#write-the-felt-journey-first)
2. [The Emotional Contrast Principle](#the-emotional-contrast-principle)
3. [The 6 Short-Form Arc Shapes](#the-6-short-form-arc-shapes)
4. [Valence Mapping — Label Every Scene](#valence-mapping--label-every-scene)
5. [The Peak-End Rule](#the-peak-end-rule)
6. [The Stakes Ladder](#the-stakes-ladder)
7. [Making Viewers Care in 3 Seconds](#making-viewers-care-in-3-seconds)
8. [Vulnerability Beats](#vulnerability-beats)
9. [Prompting Emotion in AI-Generated Visuals](#prompting-emotion-in-ai-generated-visuals)
10. [The Emotional Truth Test](#the-emotional-truth-test)

---

## Write the Felt Journey First

Before writing a single line of copy, write one sentence describing what the viewer *feels* at three points:

```
AT 0s THEY FEEL: [curiosity? recognition? disbelief?]
AT THE MIDPOINT THEY FEEL: [tension? hope? "wait, what?"]
AT THE END THEY FEEL: [relief? awe? "I need to try this" agency?]
```

If you can't fill in three *different* feelings, the script is emotionally flat and no amount of pacing tricks will save it. The words exist to produce these three states — write the states first, then the words.

**Example (transformation script, e-commerce owner audience):**
- 0s: *recognition + mild pain* — "that's literally my product photo situation"
- Midpoint: *skeptical hope* — "okay but does it actually look good?"
- End: *agency* — "I could do this tonight"

Now every line has a job: move the viewer from one state to the next.

---

## The Emotional Contrast Principle

**Emotion registers as change, not as level.** A script that is 10/10 excitement for 60 straight seconds reads as flat — the viewer's nervous system habituates within seconds. The same peak hits 3x harder when it follows a valley.

Practical rules:

- **Never hold one emotion longer than ~2 scenes.** Shift valence (positive↔negative) or intensity (quiet↔loud) at least every 8–15 seconds.
- **Buy your peaks with valleys.** Before the wow reveal, insert the frustration beat. Before the triumphant number, the moment it almost failed. The old way's pain makes the new way's speed feel physical.
- **Quiet is a tool.** A half-second of silence + a static frame right before the payoff spikes attention. (See `audio-hooks.md` silence architecture.) Contrast applies to volume and pace, not just content.
- **The pre-drop dip.** The single most reliable retention move in short-form: right before the biggest payoff, take the energy DOWN — slower delivery, "and I almost didn't notice this..." — then hit the peak. The dip makes viewers lean in; the peak releases them.

**Diagnostic:** read the script and assign each sentence + or – valence. If you see six +'s in a row, you have a flatline. Break it.

---

## The 6 Short-Form Arc Shapes

Adapted from Vonnegut's story shapes and emotional-arc research (the "Man in a Hole" family reliably outperforms flat arcs for engagement). Every script should consciously pick ONE shape.

| # | Shape | Curve | Best For | Skeleton |
|---|-------|-------|----------|----------|
| 1 | **Man in a Hole** | good → bad → better than before | Transformation, testimonial, before/after, skeptic conversion | "Things were fine → then [pain/failure] → then [discovery] → now better than I imagined" |
| 2 | **Rags to Riches** | steady rise | Capability reveals, identity-shift campaigns, demo escalation | Each beat tops the last. Save the strongest output for last. Risk: no valley = weaker peak. Add one stumble. |
| 3 | **Icarus (Cautionary)** | rise → fall | Mistake/warning content, "I wasted $X so you don't have to" | "It was working → I got confident → here's where it broke → the lesson." Fall = the value. |
| 4 | **Tension–Release** | sustained tightening → snap | Process videos, real-time generation reveals, "will it work?" | Withhold the outcome. Tighten with micro-doubts. Release at 80–90% of runtime, never earlier. |
| 5 | **Escalating Awe** | staircase of peaks | Volume/speed demos, capability montages | Each output more impossible than the last. Order matters: weakest first. Cap at 3–4 steps before fatigue. |
| 6 | **Recontextualization (Twist)** | flat → floor drops | Unhinged variations, pattern interrupts, "wait, that was AI?" | Play it straight → reveal reframes everything → viewer rewatches to verify. Highest rewatch rate of any shape. |

**Selection guide:**
- Skeptical/warm audience → Man in a Hole (mirrors their journey)
- Cold awareness → Escalating Awe or Recontextualization (thumb-stopping + rewatch)
- Conversion stage → Tension–Release (the release IS the CTA moment)
- Authority/lesson content → Icarus

**Never write shapeless.** "Hook, then some points, then CTA" is not an arc — it's a list wearing a hook. Lists retain when each item escalates (see Escalating Awe applied to list format).

---

## Valence Mapping — Label Every Scene

For every scene in the Step 7 template, add an emotion label with intensity 1–10:

```
SCENE 3 — DEMO/REVEAL
[EMOTION] skeptical hope → awe (4 → 8)
```

Rules for a healthy map:
1. **No two consecutive scenes share the same label + intensity.** That's a flatline.
2. **The intensity spread across the script must be ≥ 5 points.** A script that lives between 5 and 7 is emotionally beige.
3. **The peak (9–10) belongs at 60–90% of runtime** — not in the hook. The hook is a promise of the peak, not the peak itself. Spending the peak at 0s means the rest of the video is decline.
4. **The end must not be the low point.** End at or near a high — it's the last thing they feel and the thing they act on (see Peak-End below).

---

## The Peak-End Rule

Viewers judge, remember, and share a video based on two moments: its **peak** (most intense moment) and its **end** — not the average of the whole thing. (Kahneman's peak-end rule; it maps directly onto rewatch and share behavior.)

Engineering consequences:

- **Design ONE deliberate peak.** Know exactly which second it is. Everything before it builds; everything after it descends gracefully into the CTA. If you can't point to the peak in your script, there isn't one.
- **The end is a second peak, not an afterthought.** The weakest common ending: energy dies, CTA reads like an exit sign. Strong endings do one of: land a final line that reframes the whole video, loop seamlessly to the opening frame (rewatch), or hand the viewer agency ("you could do this tonight" — agency is an emotion).
- **Share trigger lives at the peak.** People share the moment that made them feel most. Put the most screenshot-able / clip-able frame AT the peak, and make sure it works out of context.

---

## The Stakes Ladder

Pain and desire register at four depths. Most AI-tool copy sits on rung 1 forever. Each rung up multiplies emotional weight:

| Rung | Stakes | Example | Weight |
|------|--------|---------|--------|
| 1 | **Functional** | "This takes 3 hours to do manually" | Baseline — everyone says this |
| 2 | **Financial** | "That's a $2,800 invoice, every launch" | Concrete, comparable |
| 3 | **Social** | "Your competitor posted 40 pieces while you posted 4. Your customers noticed." | Now it's about how others see them |
| 4 | **Identity** | "You stopped calling yourself creative somewhere along the way" | Deepest — handle with care and resolve it |

**Ladder rule:** open on rung 1–2 (safe, relatable), climb to 3–4 by the agitation beat, and resolve at the SAME rung you climbed to. If you invoke identity stakes ("you stopped making things"), the resolution must be identity-level ("you're a filmmaker again"), not functional ("save 3 hours").

Climbing without resolving reads as manipulation. Resolving without climbing reads as flat.

---

## Making Viewers Care in 3 Seconds

Story retention requires a character the viewer is invested in — and short-form gives you ~3 seconds to create investment. The three fast levers:

1. **Specificity = instant reality.** "A candle brand owner in her kitchen at 11pm re-shooting the same product photo for the fourth time" is a person. "Business owners struggling with content" is a demographic. One sentence of specific detail does what a minute of backstory can't. (This is the Flagging Hook principle applied to narrative.)
2. **Want + obstacle, stated or shown, immediately.** Care = understanding what someone wants and seeing what's in the way. Both must land inside the first two script lines of any story-format video.
3. **Competence + vulnerability.** Viewers invest in people who are good at something AND struggling with something. Pure competence = distance ("must be nice"). Pure struggle = pity-scroll. The mix = "that's me."

**In first person ("I" scripts):** the viewer must locate themselves in you within one line. "I run a 2-person agency" locates. "I love AI tools" doesn't.

---

## Vulnerability Beats

The single most underused retention device in polished marketing scripts. One honest, slightly-too-real line mid-script resets viewer trust and attention simultaneously:

- The confession: "I ran this prompt 14 times before it worked. Nobody shows you that part."
- The almost-quit: "I'd already drafted the email going back to our old photographer."
- The doubt voiced: "Even looking at the result, part of me was waiting to find the flaw."
- The cost admission: "The first month, I made everything worse."

Placement: **just before or after the midpoint** — exactly where retention graphs sag. A vulnerability beat at the sag point outperforms a pattern interrupt there, because it re-earns trust at the moment attention is cheapest.

Rules: one per script (two reads as performance), it must be true-shaped (specific, minor, verifiable-feeling), and it must never undermine the core claim — confess friction, not failure of the product.

---

## Prompting Emotion in AI-Generated Visuals

The script's emotional arc must survive AI production. When writing [GENERATION] prompts, the emotion label of each scene translates to concrete craft (see `visual-language.md` for full vocabulary):

| Scene emotion | Lighting | Camera | Pace/motion |
|---|---|---|---|
| Frustration / pain | low-key, cold temperature, hard shadows, practical desk lamp | static or slow push-in, tight framing | slow, held frames |
| Skeptical hope | mixed temperature, half-lit face, window light | medium shot, slight handheld drift | measured |
| Awe / reveal | volumetric, backlit, golden or high-key bloom | slow dolly out revealing scale, or whip to reveal | one decisive move |
| Agency / resolution | warm, even, daylight | eye-level, stable, open framing | settled, breathing room |

**Faces carry arcs.** In i2v and character work, prompt the micro-expression change, not just the expression: "her expression shifts from focused skepticism to involuntary half-smile" outperforms "she smiles." Motion between emotional states IS the arc made visible.

**Voice carries arcs.** Mark the emotional label in the ElevenLabs notation per scene (see `audio-hooks.md`): the frustration beat delivered flat-fast, the reveal delivered with a pause before the key number. Same words, different delivery = different arc.

---

## The Emotional Truth Test

Final gate before delivery. Answer honestly:

1. **Could a viewer describe this video by feeling?** ("It's the one where the guy almost gave up and then—") If it's only describable by information ("it's about an AI image tool"), the arc failed.
2. **Does the script pick ONE arc shape** and hit its beats — or does it drift?
3. **Is there a nameable peak second?**
4. **Does the emotional spread cover ≥5 intensity points?**
5. **Is the final feeling the one you want acted on?** Awe alone doesn't convert — awe + agency does. FOMO alone doesn't retain followers — FOMO + belonging does. Check the END feeling matches the campaign goal:
   - Awareness → awe, delight, "how?"
   - Consideration → trust, skeptical-hope-resolved
   - Conversion → agency ("I could do this tonight")


<!-- ═══════ FILE: script-writer/references/campaign-arcs.md ═══════ -->

# Campaign Arc Planning
## From Single Hook to Full Campaign Strategy

A single hook is a shot. A campaign arc is a system. This file covers how to plan, structure, and sequence content across multiple videos so each piece feeds into the next and the whole converts better than any individual video could.

---

## The Core Principle: Awareness → Consideration → Conversion

Every piece of content occupies a stage in a viewer's decision journey. The mistake most campaigns make is writing all content for the same stage — usually conversion — and wondering why cold audiences don't respond.

**The 3-stage model:**

| Stage | Viewer's State | Your Goal | Hook Type | CTA |
|-------|---------------|-----------|-----------|-----|
| **Awareness** | Doesn't know the platform/tool | Stop the scroll, create curiosity | Awe, pattern interrupt, cold open | None, or soft ("save this") |
| **Consideration** | Knows it exists, not sure it works | Build belief, remove skepticism | Skeptic → conviction, process transparency | Soft ("try it free", "link in bio") |
| **Conversion** | Believes it works, needs a reason to act | Remove final friction, create urgency | Cost destruction, identity shift | Hard ("sign up", "generate your first image free") |

Never run a conversion hook on a cold audience. Never waste an awareness hook on a retargeting audience. Match the content to where the viewer actually is.

---

## The 3-Video Campaign Series

The minimum viable campaign. Three videos, one funnel.

### Video 1 — "This Exists" (Awareness)
**Goal:** Stop the scroll. Create the "how is that possible?" moment.
**Hook type:** Cold open — output in frame 1, no setup
**Structure:**
- 0–3s: The output or transformation. Nothing else.
- 3–15s: One sentence of context. "I made this with AI. One prompt. 8 seconds."
- 15–25s: One more output variation — different product, same speed/quality
- 25–30s: Soft CTA. "Save this. You'll want it when you see what's possible."
**No hard sell.** This video's only job is to make them want to watch video 2.

### Video 2 — "Here's How" (Consideration)
**Goal:** Demystify the process. Make it feel achievable.
**Hook type:** POV setup or process teaser — "here's the exact prompt I used"
**Structure:**
- 0–3s: Show the prompt being typed, or state it on screen
- 3–25s: Walk through the workflow. Specific steps. Real interface.
- 25–45s: Show 2–3 output variations from the same prompt type
- 45–55s: Address the main objection ("I know what you're thinking — let me show you why it's not what you expect")
- 55–60s: CTA tied to action: "Try the free version — link in bio"
**Key:** Show the interface. Process transparency builds more trust than any claim.

### Video 3 — "Here's What It Means for You" (Conversion)
**Goal:** Make the connection between the platform's capability and the viewer's specific situation.
**Hook type:** Identity expansion or cost destruction
**Structure:**
- 0–3s: State the specific identity and their current pain: "If you're [role] and you're still [old way], this changes everything."
- 3–20s: Paint the "before" in specific, recognisable terms
- 20–40s: Show the "after" — not vague transformation, but specific output with numbers
- 40–50s: Remove the risk: free trial, no credit card, first X outputs free
- 50–60s: Hard CTA with urgency: "Generate your first image free — link in bio"

---

## The 5-Video Series (More Depth)

For campaigns with more runway, extend the 3-video structure with two additional types:

### Video 4 — "The Proof" (Social Proof)
A real user's story. Before → turning point → specific after.
- Testimonial format or case study
- Specific numbers: "She went from $3k photography budget to $0 in one month"
- The person should be recognisably like the target viewer

### Video 5 — "The Comparison" (Decision Stage)
Side-by-side. AI-generated vs. traditional. Make the quality delta undeniable.
- No need to name competitors — just show "professional photography cost" vs. "imagine.art cost"
- Time delta, cost delta, revision delta
- End with: the only rational conclusion

---

## Hook Series Strategy: Batching for A/B Testing

Don't write one hook per campaign. Write five and test them. The best-performing hook is almost never the one you'd have predicted.

**The batch hook system:**

1. Write the brief: platform, output type, audience, goal
2. Generate 5 hooks — one per AI emotion type (awe, skepticism→conviction, FOMO, identity shift, cost destruction)
3. Assign each to a specific visual concept (what's in frame 1)
4. Run as A/B test: same video body, 5 different hooks
5. Measure: 3-second hold rate, completion rate, CTA click rate
6. Retire the bottom 2, replace with 2 new variations based on learnings

**The fastest learning loop:**
- Week 1: Test all 5 hook emotion types
- Week 2: Double down on the top 2, test 3 new variations within those emotion types
- Week 3: Lock best-performer as "control," only test against it

**What to track:**
- 3-second hold rate — tells you if the hook landed
- 50% completion rate — tells you if the body is earning the hook's promise
- 100% completion rate — tells you if completion bait is working
- CTA rate — only meaningful if completion rate is healthy first

---

## Content Calendar Structure for AI Platform Campaigns

A repeatable weekly cadence that covers all stages:

| Day | Pillar | Stage | Format |
|-----|--------|-------|--------|
| Monday | Output showcase | Awareness | 10–15s loop or montage |
| Wednesday | Process reveal | Consideration | 45–60s walkthrough |
| Friday | Use case proof | Consideration→Conversion | 60–90s tutorial or testimonial |
| (Paid) | Comparison / contrast | Conversion | 30s split screen ad |

This covers awareness, consideration, and conversion every week without any single piece of content doing too much.

**Rotating hook types by week:**
- Week 1: Awe + process reveal
- Week 2: Skeptic conversion + use case proof
- Week 3: FOMO + comparison
- Week 4: Identity shift + community showcase

---

## Campaign Arc for a Product Launch

When launching a new feature, model update, or product tier:

**Pre-launch (2 weeks before):**
- Tease the output without naming what made it ("something changed")
- Open loops: "We've been generating something we're not showing yet"
- Curiosity hooks — no CTA, just awareness

**Launch week:**
- Day 1: The reveal — output showcase, cold open, maximum quality demonstration
- Day 2: The process — how it works, what changed, why it matters
- Day 3: The use case — specific audience, specific workflow, specific result
- Day 4: The proof — early user result or internal case study
- Day 5: The offer — free trial, limited access, launch-week incentive

**Post-launch (ongoing):**
- Community outputs — real users, real results
- Objection crushing — address the top doubts from comments
- Deep dive tutorials — for consideration-stage audiences who stayed

---

## Hook Series for Specific Campaign Types

### Campaign Type: Feature Launch
**Hook 1 (Tease):** "We changed something. We're not ready to show you yet. But here's what it can do now." [show output, no feature name]
**Hook 2 (Reveal):** "The output that made our team go quiet for 30 seconds." [cold open on the best output]
**Hook 3 (How):** "Here's exactly how we generated this. One prompt. No editing." [process]
**Hook 4 (Use case):** "This changes everything for [specific role]." [identity hook]
**Hook 5 (Offer):** "Try the new model free for the next 48 hours." [conversion]

### Campaign Type: Audience-Specific Push
Target one audience segment with a 3-video series, same platform, same week:
- Video 1: Their specific pain, stated in their exact language
- Video 2: imagine.art as the specific solution to that specific pain
- Video 3: Someone exactly like them who solved it this way

The specificity is the targeting. "This is for e-commerce brand owners who've spent more than $2k on a product photoshoot" will outperform "this is for anyone who needs great product photos."

### Campaign Type: Platform-Specific Push
Same core content, adapted per platform in the same week:
- TikTok: Fastest version. 15–30 seconds. Most aggressive hook. Sound-on with trending audio.
- Instagram Reels: Slightly longer. 30–60 seconds. Caption carries more of the story. Visual quality prioritised.
- YouTube Shorts: Educational angle. The "why" matters here. Slightly slower pacing.
- LinkedIn: Business case lead. Cost delta and ROI first. Tone more measured.

---

## Completion Bait: Earning the Full Watch

The algorithm rewards completion. Build every script with a reason to watch to the end.

**Completion bait types:**

**The Promised Reveal:** Tease something in the first 15 seconds that only lands at the end.
- "By the end of this, you'll see the version that actually stopped me mid-generation."
- The payoff must be worth it. Weak reveals destroy trust faster than no tease at all.

**The Transformation Arc:** Show a starting state at 0:00 and commit to showing the end state. The viewer stays to see where it lands.
- "This is what we started with. Here's where it ends up." [show the before at the start]

**The Numbered Structure:** "Three things, I'll give you the most important one last."
- Viewers who heard "three" will stay until they have three.

**The Open Question:** Ask something at the start that the video will answer.
- "Why do AI images look fake? Here's what's actually happening — and how to fix it."
- The question creates a knowledge gap the brain needs to close.

**The Challenge/Bet:** Create stakes.
- "I'm going to generate 10 product images in 5 minutes. Watch to see if I can do it."
- The outcome is unknown. The viewer becomes a witness.

---

## Series Continuity: Making Content That Feeds Itself

The best-performing channels don't just post videos — they post chapters. Each video plants a seed for the next.

**Techniques:**

**The cliffhanger callback:** End a video with "next week I'm going to show you what this looks like when you push it to the limit." Then actually do it. The follow-through builds an audience that comes back.

**The vocabulary hook:** Invent a specific term or phrase for your workflow. "The 3-word prompt" or "the reverse-engineer method." Once an audience associates a phrase with your content, they search for it. You own the term.

**The before/after series:** Start a project visibly. Document the AI-assisted process across 3–5 videos. End with the full result. Viewers who missed video 1 will seek it out after seeing video 4.

**The "I tried X for 30 days" arc:** Commit to a specific challenge using the platform. Each video is a chapter. Completion of the arc is the payoff. This format earns the highest serial follow rate of any content type on short-form platforms.


<!-- ═══════ FILE: script-writer/references/creative-ideation.md ═══════ -->

# Creative Ideation — Concept Development Before the Hook

A vague premise produces a vague script. This file covers the pre-writing phase: how to generate raw concepts, pressure-test them, and distill them into a dramatic engine — before any hook, script, or generation prompt gets written.

**When to use this file:** the user has no brief yet ("give me ideas for..."), the brief is a vibe not a concept, a campaign needs a fresh angle, or a hook keeps failing because the underlying idea is weak. Hook problems are usually idea problems.

---

## The Three-Phase Concept Pipeline

Every viable concept moves through three distinct phases. Don't skip ahead.

**1. Generation — volume over quality.**
Linus Pauling's rule: the way to get a good idea is to get a massive number of ideas. Defer all judgment. Scorsese found *Goodfellas* through a chance encounter with a nonfiction book — serendipity requires a wide net. In practice: generate 15–30 raw concepts before evaluating any of them.

**2. Elaboration — structural stress test.**
Distill each surviving concept into:
- A **central dramatic question** (one sentence, answerable yes/no by the ending)
- The **rules of the world** (what's possible, what's forbidden, what does the AI/product/character actually do)
- The **emotional landscape** (what the audience should feel at open, middle, close)

If a concept can't produce a dramatic question, it's a mood board, not a script.

**3. Championing — the pitch test.**
Can you sell this in two sentences to someone with no context? If the concept requires a paragraph of setup, either the premise is weak or you haven't found its sharpest edge yet. For campaign work, the championing phase = the hook. If no hook falls naturally out of the concept, return to elaboration.

---

## Brainstorming Frameworks — Pick by Situation

| Technique | Mechanism | Use When | Time |
|---|---|---|---|
| **Mind Mapping** | Visual branching from a central node | Exploring broad themes; connecting abstract traits (trauma → behavior; brand value → visual motif) | 15–45 min |
| **Freewriting / Crazy 8s** | Continuous unfiltered transcription, no editing | Blocked; need raw dialogue or unfiltered emotional beats | 10–15 min |
| **The 15-Minute Timer** | Timed rapid list: protagonist's ultimate desire, deepest fear, internal + external conflict, worst-case scenarios that force them to face that fear | Building a character or persona from nothing | 15 min |
| **"What If" Scenarios** | Iterative speculative questioning; strip a known story to its barest plot, then invert or mutate it | High-concept premises; subverting genre expectations | Variable |
| **Gap Analysis** | Define the delta between a character's start state and end goal, then engineer the obstacles | Structuring arcs; building the middle of a campaign series | 30–60 min |
| **Brainwriting** | Silent written ideation shared sequentially | Team ideation; avoiding loud voices and groupthink | 20–40 min |

### The "What If" inversion — worked mechanic
Reduce a known narrative to its barest plot element, then reverse it:
- *Star Wars* stripped down = "destroy a weapon of mass destruction." Inverted = "reclaim an artifact to *build* a weapon."
- For campaigns: "AI makes content creation fast" inverted = "What if speed was the problem? A creator drowning in 400 generated options." The inversion is often the fresher hook.

### The 15-minute timer — campaign adaptation
Replace "protagonist" with the target viewer:
1. What does this person ultimately want? (not "more followers" — the identity behind it)
2. What do they most fear? (irrelevance, wasted budget, being exposed as behind)
3. What internal conflict do they carry? (excited by AI / afraid it makes them replaceable)
4. What's the worst-case scenario that forces them to confront the fear?
Item 4 is usually your agitation scene. Item 2 is usually your hook.

---

## Character Under Pressure — Subtext Exercises

Characters are defined by behavior under duress, not exposition. When a script's character (or UGC persona, or brand-film protagonist) feels flat, run one of these:

- **The Five Dodges:** write the character dodging five consecutive direct questions. What they avoid reveals what they protect.
- **The First Lie:** force a character who never lies to lie convincingly. The technique they choose IS the character.
- **Weaponized Silence:** write an exchange where one character uses silence as an offensive move. Where the silence lands tells you the power dynamic.

These translate directly to AI video: a 6-second Seedance clip of a character *dodging* a question is more magnetic than one of a character explaining. Prompt the avoidance behavior, not the emotion label.

---

## From Concept to Dramatic Question — The Filter

Before a concept graduates to scripting, it must pass:

1. **One-sentence dramatic question?** ("Will she walk out?" / "Can a solo founder out-produce an agency?")
2. **Clear world rules?** (What can the tool/character actually do? Where's the limit? The limit creates the tension.)
3. **A gap?** (Start state vs. end state — no gap, no story, no completion bait.)
4. **A worst case?** (If nothing can go wrong, there's no reason to keep watching.)
5. **Championable in 2 sentences?** (If not, sharpen or kill.)

Concepts that pass all five → proceed to hooks (SKILL.md Step 0). Concepts that pass 3–4 → one more elaboration round. Fewer → back to generation.


<!-- ═══════ FILE: script-writer/references/worked-examples.md ═══════ -->

# Worked Examples — imagine.art Hook Library

This file contains fully-written hooks for imagine.art's 5 core audience segments. Every example applies a named technique from `pro-copywriting.md`. Use these as starting points, structural models, or direct inspiration — not as final copy without adaptation.

**Competitive context:** The competitor in this space (referred to as "[competitor]") has built its brand around money/income hooks, "Hollywood-grade for everyone" positioning, and a content strategy that has actively antagonized professional creatives. They are currently dealing with a documented trust crisis and a suspended social media account. The hooks below are written to own the exact emotional territory they've abandoned.

---

## Segment 1: Content Creators
*Pain: Speed and creative blocks. Waiting on ideas, execution, or refinement.*
*Dream: Output that matches their creative vision — fast, consistently, without a team.*
*Hook entry point: Identity. They think of themselves as creative people — not production machines.*

**What [competitor] says to them:** "Make money with AI. Build a faceless channel. Earn $2,500 per video."
**What imagine.art says:** You're a creative. This removes the gap between your vision and what you can actually make.

---

### Hook 1 — Identity Expansion (awareness: Problem Aware)
**Formula:** Identity Expansion + Flagging

> "You've had ideas you couldn't execute because you didn't have the budget, the team, or the technical skills. That gap just closed."

**[TEXT OVERLAY]** Your vision. No budget needed.
**[VISUAL]** Split: handwritten notes/sketch on one side → finished, cinematic visual on the other. No cut. Morphs.
**4U:** 4/4 — Urgent (gap just closed), Unique (positions AI as creative access, not replacement), Ultra-specific (names the 3 exact blockers), Useful (directly resolves creator's core frustration)

---

### Hook 2 — The Slippery Slide opening (awareness: Unaware)
**Formula:** Cold Open + Sugarman Slippery Slide

> [Visual leads — an arresting, cinematic image holds for 2 full seconds before any audio]
> "That image took me 40 seconds to make. I want to show you what the next one looks like."

**[TEXT OVERLAY]** 40 seconds.
**[VISUAL]** The image fills the frame. No context. Let the quality ask the question.
**4U:** 4/4 — The silence and the single line are the hook. The last sentence opens a loop the viewer must close.

---

### Hook 3 — Skeptic + Reversal (awareness: Solution Aware — has tried other AI tools)
**Formula:** They Laughed + Skepticism → Conviction

> "Every AI image tool I tried looked like AI. This one made me forget I wasn't looking at a photograph. Here's the exact prompt I used."

**[TEXT OVERLAY]** "Looks like AI." Not this one.
**[VISUAL]** Open on the image — no label, no context. Let the viewer decide what they're looking at. Then reveal: "1 prompt. imagine.art."
**4U:** 3/4 — The "exact prompt" promise earns a save.

---

### Hook 4 — Future Pacing (awareness: Problem Aware)
**Formula:** Future Pacing + Identity Shift

> "Imagine posting something this week that people screenshot and share — not because it went viral, but because it's genuinely beautiful. That's the shift."

**[TEXT OVERLAY]** Make something worth screenshotting.
**[VISUAL]** A sequence of aesthetically stunning, shareable-feeling images — not product shots, creative visuals that feel like art.
**4U:** 4/4 — This is the dream most content creators have but almost no AI tool speaks to. They want to be proud of their work, not just productive.

---

### Hook 5 — IF…THEN (awareness: Solution Aware)
**Formula:** Bencivenga IF…THEN

> "If you can describe what you're imagining, I can show you what it looks like — in under a minute."

**[TEXT OVERLAY]** Describe it → see it.
**[VISUAL]** Someone typing a description (poetic, specific — not a bland prompt) → image materializes.
**4U:** 4/4 — The entry condition (describe something) is effortless. The promise (see your imagination made real) is the exact dream of a visual creator.

---

## Segment 2: Social Media Managers
*Pain: Volume, speed, brand consistency. Running out of content before running out of month.*
*Dream: A reliable pipeline that doesn't break down when the brief changes or the shoot gets cancelled.*
*Hook entry point: Relief from the content treadmill.*

**What [competitor] says to them:** "Hollywood-grade in seconds." (Aspirational, but doesn't solve the real problem — which is keeping up, not making art.)
**What imagine.art says:** Stop rebuilding from scratch every week.

---

### Hook 1 — Cost Destruction + Flagging (awareness: Problem Aware)
**Formula:** Kennedy Flag + Cost Destruction

> "If your content calendar has blank squares because you're waiting on the design team — here's how I filled 3 weeks of posts in one afternoon."

**[TEXT OVERLAY]** 3 weeks of content. One afternoon.
**[VISUAL]** A content calendar with blank squares → same calendar, fully populated. Real posts visible.
**4U:** 4/4 — "Blank squares" is language straight from the social media manager's actual experience. Specific and painful.

---

### Hook 2 — PAS with Agitation (awareness: Problem Aware)
**Formula:** Dan Kennedy PAS with deep agitation

> "You're posting the same 4 images on rotation. Your audience has seen them. Your engagement is dropping. And the next shoot isn't for 6 weeks. Here's how I got out of that loop."

**[TEXT OVERLAY]** Stuck in a content loop?
**[VISUAL]** Same image appearing 3 times in a mock Instagram grid → then: the grid refreshes with all-new visuals.
**4U:** 4/4 — Three agitation lines hit three real pains (repetition, audience fatigue, timeline). The question "here's how I got out" earns the watch.

---

### Hook 3 — Volume Hook (awareness: Solution Aware)
**Formula:** Volume + Specificity as Proof

> "47 on-brand product images. Two brand guidelines uploaded. One afternoon. Zero reshoots."

**[TEXT OVERLAY]** 47 images. Zero reshoots.
**[VISUAL]** Rapid-cut grid: image after image, each on-brand, each different background/angle/style.
**4U:** 4/4 — The "47" (not 50) signals this is a real count. "Zero reshoots" hits the exact pain of a social manager who's coordinated a shoot that didn't deliver.

---

### Hook 4 — Slippery Slide + Seed of Curiosity (awareness: Unaware)
**Formula:** Sugarman Slippery Slide

> "My brand guidelines are 12 pages. I uploaded them to imagine.art and here's what it understood."

**[TEXT OVERLAY]** Brand guidelines → AI understood them.
**[VISUAL]** A brand guidelines doc, then a series of generated visuals that are unmistakably on-brand — right colors, right tone, right aesthetic.
**4U:** 4/4 — "Here's what it understood" is the seed of curiosity that forces completion. The viewer has to see whether it actually got it right.

---

## Segment 3: E-commerce Brand Owners
*Pain: Product photography is expensive, slow, and inflexible. Can't test fast.*
*Dream: Infinite product images on demand — every background, every lifestyle context, every SKU.*
*Hook entry point: Cost destruction + speed. They feel the $2,000-$3,000 shoot invoice personally.*

**What [competitor] says to them:** "[Competitor] is primarily a video platform. Their image generation is not their primary offer."
**What imagine.art says:** You just retired your product photographer.

---

### Hook 1 — Recommended Lead Hook (awareness: Problem Aware)
**Formula:** Cost Destruction + Demo-First + Ogilvy specificity

> [2 seconds of silence — a product image in full frame, stunning lighting, clean background]
> "This product shot cost $0. The last one I paid for was $2,800. I cannot tell the difference. My photographer cannot either."

**[TEXT OVERLAY]** $2,800 vs $0. Spot the difference.
**[VISUAL]** The AI-generated image holds. Then: a side-by-side comparison. Both labeled. Let the viewer stare.
**4U:** 4/4 — Demo before explanation. The "$2,800 vs $0" is specific and real. "My photographer cannot either" is the most credible proof in the piece.

---

### Hook 2 — They Laughed Reversal (awareness: Solution Aware, skeptical)
**Formula:** Caples They Laughed + Skeptic Conversion

> "My agency laughed when I said I was replacing our product studio with AI. Last month I showed them our best-performing ad. It was generated in 28 seconds."

**[TEXT OVERLAY]** They laughed. Then they saw the results.
**[VISUAL]** Creator speaking to camera — slightly conspiratorial — then cuts to the ad itself.
**4U:** 4/4 — This is the exact social journey a skeptic needs to see. Mirrors their own anticipated objection and resolves it before they can form it.

---

### Hook 3 — IF…THEN (awareness: Product Aware, hesitating)
**Formula:** Bencivenga IF…THEN

> "If you have a photo of your product and 2 minutes, imagine.art will give you 20 variations — every background, every lighting setup, every lifestyle context you were going to book a photographer for."

**[TEXT OVERLAY]** 1 product photo → 20 campaign images.
**[VISUAL]** Single product photo → grid expanding outward showing 20 variations: outdoor, studio, lifestyle, flat lay, dark background, seasonal.
**4U:** 4/4 — The entry condition (1 photo, 2 minutes) is trivially achievable. The output (20 variations, every booking) is the complete value proposition in one sentence.

---

### Hook 4 — Flagging + Future Pacing (awareness: Unaware)
**Formula:** Kennedy Flag + Future Pacing

> "If you've ever delayed a product launch because the shoot wasn't ready — picture this: next launch, the images are ready before the product arrives."

**[TEXT OVERLAY]** Images ready before the product arrives.
**[VISUAL]** A product packaging mockup → generated lifestyle images around it → a "ready to launch" content grid.
**4U:** 4/4 — "Delayed a product launch because the shoot wasn't ready" is a real, specific, painful experience that immediately qualifies the right audience. The future pacing makes them feel the relief before they've done anything.

---

### Hook 5 — Volume + Process Transparency (awareness: Most Aware — ready to trial)
**Formula:** Hopkins Process Transparency + Volume

> "Here's the exact workflow I use to generate 40 product images in under 10 minutes. Brand guidelines, background brief, and 3 reference photos — that's all it needs."

**[TEXT OVERLAY]** 40 product images. 10 minutes. Here's how.
**[VISUAL]** Screen recording of the workflow — fast, specific, real.
**4U:** 4/4 — This is a conversion hook. The viewer who has already decided to try this just needs to see the actual workflow before they commit. Process transparency builds trust and accelerates trial.

---

## Segment 4: Agencies
*Pain: Client revision cycles, brief drift, speed-to-concept. The gap between ideation and presentation.*
*Dream: Show clients 10 directions in the time it used to take to make one deck.*
*Hook entry point: Creative velocity. The ability to say "yes and here's what that looks like" in real time.*

**What [competitor] says to them:** Very little. Their enterprise page is thin. Their content is for solo creators and side hustlers.
**What imagine.art says:** You can present 10 directions in the time you used to spend on one.

---

### Hook 1 — B2B Flagging + ROI (awareness: Problem Aware)
**Formula:** Kennedy Flag + ROI framing

> "If your team is still mocking up concepts in Figma before you even know if the client's going in that direction — watch this."

**[TEXT OVERLAY]** Concepts before the brief is final.
**[VISUAL]** A Figma file with 1 concept → imagine.art generating 10 visual directions in rapid sequence.
**4U:** 4/4 — "Before you even know if the client's going in that direction" is a specific, lived creative agency frustration. Not a demographic — a situation.

---

### Hook 2 — Identity + Competitive Threat (awareness: Problem Aware)
**Formula:** Identity Shift + FOMO

> "The agencies winning pitches right now aren't more creative than you. They just show up with 10 visual directions instead of 2. Here's how they're doing it."

**[TEXT OVERLAY]** 10 directions. Not 2.
**[VISUAL]** A pitch deck with 10 clearly distinct visual directions — real quality, real variety.
**4U:** 4/4 — Competitive framing works for agencies. They think about winning pitches. "More creative" vs. "more prepared" is a reframe that doesn't threaten creative identity.

---

### Hook 3 — Proof + Process (awareness: Product Aware)
**Formula:** Hopkins Specificity + Bencivenga Proof

> "We use imagine.art to generate first-round concepts before we open Figma. It cuts our concepting phase from 3 days to 3 hours. Here's the actual workflow."

**[TEXT OVERLAY]** Concepting: 3 days → 3 hours.
**[VISUAL]** Screen recording of the imagine.art concepting workflow — structured, fast, real agency-quality outputs.
**4U:** 4/4 — "Before we open Figma" is specific enough to signal this is a real workflow. 3 days → 3 hours is a credible time compression for someone who lives in creative sprints.

---

## Segment 5: Filmmakers and Cinematographers
*Pain: Pre-visualization is expensive. Scouting, storyboarding, blocking — all slow. The vision in your head is hard to communicate.*
*Dream: Show the team exactly what you see before a single light is set.*
*Hook entry point: Creative possibility. What if you could externalize your vision instantly?*

**What [competitor] says to them:** "Hollywood-grade for everyone." (Aspirational wrapper over a social-content tool.)
**What imagine.art says:** Pre-visualize anything. Show the team what you see.

---

### Hook 1 — Identity + Specific Situation (awareness: Problem Aware)
**Formula:** Kennedy Flag + Identity Expansion

> "If you've ever spent 20 minutes explaining a shot to your DP and still not been understood — this is what I use now instead."

**[TEXT OVERLAY]** Show, don't explain.
**[VISUAL]** A handwritten shot list → a generated still from imagine.art matching that exact description — lighting, framing, mood precise.
**4U:** 4/4 — "20 minutes explaining a shot to your DP" is a specific, painful, universal filmmaker experience. The resolution (show the image instead) is elegant and immediately understood.

---

### Hook 2 — Big Idea Hook (awareness: Unaware)
**Formula:** Ogilvy Big Idea — One surprising, specific, sensory detail

> "I pre-visualized 12 scenes from my short film before we scouted a single location. When we arrived, the DP said 'it's exactly what I imagined.' We hadn't spoken about it."

**[TEXT OVERLAY]** When you show them instead of telling them.
**[VISUAL]** Side-by-side: the generated pre-viz stills → actual on-location frames from the finished film. Nearly identical.
**4U:** 4/4 — The detail that lands: "it's exactly what I imagined. We hadn't spoken about it." That is the Big Idea. Visual communication so precise it replaces language.

---

### Hook 3 — Craft Angle (awareness: Unaware — emotional/identity hook)
**Formula:** Identity + Emotional texture — the lane [competitor] has entirely abandoned

> "Most AI image tools flatten your vision into something generic. This one learns how you see."

**[TEXT OVERLAY]** AI that learns how you see.
**[VISUAL]** A series of highly distinctive, stylistically consistent images — not generic "AI look" — with a clear personal aesthetic fingerprint throughout.
**4U:** 4/4 — "Flatten your vision into something generic" is the exact complaint of every filmmaker who's tried a competitor and was disappointed. This hook speaks to an experience they've already had and positions imagine.art as the answer without naming the competitor.

---

## Competitive Positioning Hooks — Own What [Competitor] Abandoned

These hooks are designed to fill the specific whitespace [competitor]'s content strategy has left open. Use when the campaign goal is differentiation from the broader AI video/image market.

---

### "Trust" angle — for brand-conscious audiences
> "AI-generated content comes with a reputation now. Here's why the brands we work with are comfortable putting ours in front of their customers."

**[TEXT OVERLAY]** AI you can put in front of your customers.
**Why this works:** Doesn't name anyone. Doesn't attack. Simply positions around the exact concern that's making agency creative directors and brand managers nervous about any AI tool right now. The viewer who knows the competitor's reputation will connect the dots themselves.

---

### "For professionals, not against them" angle
> "I'm a photographer. This is the tool I thought would put me out of work. Instead it tripled my output capacity and doubled what I charge. Here's why."

**[TEXT OVERLAY]** The AI tool that made me more valuable.
**Why this works:** The most powerful reframe in the market right now. [Competitor] made the "job killer" claim explicitly — and got destroyed for it. imagine.art can own the opposite with no attack, just a compelling counter-narrative.
**Audience:** Professional photographers, videographers, motion designers — the segment that is currently hostile to AI as a category.

---

### "Creative identity" angle — emotional whitespace [competitor] has zero presence in
> "What would you make if execution was no longer the obstacle?"

**[TEXT OVERLAY]** What would you make?
**[VISUAL]** A single arresting, visually complex image that feels like it came from a creative person with a real artistic vision.
**Why this works:** [Competitor]'s entire content library treats creativity as an output/income machine. This one sentence positions imagine.art as the tool for people who think of themselves as creators first. It's unanswerable, emotionally resonant, and occupies territory no competitor is currently in.


<!-- ═══════ FILE: script-writer/references/screenplay.md ═══════ -->

# Screenwriting & Brand Film Scripts

Deep guide for short films, feature screenplays, TV pilots, and cinematic brand films.

---

## Table of Contents
1. [Screenplay Formatting](#screenplay-formatting)
2. [Save the Cat — 15 Beat Sheet](#save-the-cat--15-beat-sheet)
3. [3-Act Structure](#3-act-structure)
4. [The Pixar Story Spine](#the-pixar-story-spine)
5. [Show Don't Tell](#show-dont-tell)
6. [Subtext and Dialogue](#subtext-and-dialogue)
7. [Cold Opens and In Medias Res](#cold-opens-and-in-medias-res)
8. [Short Film Structure](#short-film-structure)
9. [TV Pilot Structure](#tv-pilot-structure)

---

## Screenplay Formatting

Professional screenplay format is not optional in professional contexts — it signals competence and is the industry standard. Deviation from format signals inexperience.

### Scene Heading (Slugline)
```
INT. COFFEE SHOP - DAY
EXT. ROOFTOP - NIGHT
INT./EXT. CAR - MOVING - DAWN
```
- Always ALL CAPS
- INT. (interior) or EXT. (exterior) or INT./EXT. for transitions
- Location name — be specific but not so specific it creates production problems
- Time of day: DAY, NIGHT, DAWN, DUSK, CONTINUOUS, LATER
- Establishes where/when the scene takes place for both reader and (eventually) production team

### Action Lines
- **Present tense, active voice — always.** Not "John was nervous." Not "John would sit down."
- **Describe only what can be seen or heard.** No internal states, backstory, emotional labels.
- **Rule:** The camera is a witness, not a mind reader.
- Use strong, specific verbs — "trudges" not "walks slowly," "slams" not "closes loudly," "collapses" not "sits down heavily"
- Keep paragraphs short — 3 lines maximum. White space matters; dense action paragraphs slow the read.

**Wrong:**
> John enters, feeling anxious about what he's about to say. He has always struggled with confrontation.

**Right:**
> John enters. He adjusts his collar twice. Glances at his watch. His eyes find the exit before they find the person he came to see.

### Dialogue
- Character name in ALL CAPS, centered above the line
- Parentheticals (wrylies) — use sparingly, only when the reading of a line is genuinely ambiguous and the wrong interpretation would change the meaning
- Each line of dialogue should advance: character, relationship, or plot — preferably all three
- People don't say what they mean. Real dialogue is subtext in action.

### Technical Specs
- 1 page ≈ 1 minute of screen time
- Feature film: 90–115 pages
- Short film: 2–20 pages
- TV drama pilot: 50–65 pages
- TV comedy pilot: 25–35 pages
- Font: Courier Prime 12pt (the industry standard)
- Margins: 1.5" left, 1" right, 1" top and bottom

---

## Save the Cat — 15 Beat Sheet

Blake Snyder's beat sheet from *Save the Cat!* (2005). The most widely used structural tool in modern screenwriting. 

**The golden rule:** The opening image and closing image should be mirror opposites. They visually demonstrate how far the protagonist has changed.

| # | Beat | Page % | What Happens |
|---|------|--------|--------------|
| 1 | **Opening Image** | 1% | Single image that establishes tone, world, and protagonist's "before" state. The reader should know immediately what kind of story this is. |
| 2 | **Theme Stated** | 5% | Someone speaks the theme to the protagonist — but the protagonist doesn't understand it yet. They will by the end. |
| 3 | **Set-Up** | 1–10% | Establish the ordinary world, key characters, the protagonist's flaw or need, and the stakes. Give them something to lose. |
| 4 | **Catalyst** | 10% | The inciting incident. The event that disrupts the status quo and forces the story into motion. Life will never be the same. |
| 5 | **Debate** | 10–20% | The protagonist resists the call to adventure. "Should I? Can I? What if I'm wrong?" This is the natural hesitation that makes the decision meaningful. |
| 6 | **Break into Two** | 20% | The protagonist makes an irreversible choice to enter Act 2. The thesis world is abandoned; the antithesis world begins. |
| 7 | **B Story** | 22% | A secondary storyline begins — often a relationship that carries the thematic content. This is the "heart" of the story. |
| 8 | **Fun and Games** | 20–50% | The "promise of the premise." Why did the audience show up? Give them that. The protagonist explores the new world — sometimes succeeding, often failing. |
| 9 | **Midpoint** | 50% | False victory (protagonist seems to win) or false defeat (everything seems lost). Stakes are raised. The story deepens. |
| 10 | **Bad Guys Close In** | 50–75% | External pressure escalates. Internal doubts grow. The team fractures. The protagonist's flaw begins to damage what they care about. |
| 11 | **All Is Lost** | 75% | The lowest moment. The goal seems impossible. Often: the mentor figure is lost, a key relationship breaks, the opportunity is gone. |
| 12 | **Dark Night of the Soul** | 75–85% | The protagonist sits in despair. This is where the thematic question reaches its crisis point. Why go on? |
| 13 | **Break into Three** | 85% | A synthesis of the A story and B story gives the protagonist a new understanding. They find a way. |
| 14 | **Finale** | 85–99% | The protagonist confronts the antagonist/obstacle using everything they've learned. The world is stormed, the team is liberated, the bad guys are dispatched, and the hero earns their transformation. |
| 15 | **Final Image** | 99% | Mirror of the opening image — but transformed. Shows visually how far we've come. |

### The "Save the Cat" Moment
Named for the technique: early in the story, the protagonist does something small and selfless — "saves a cat" — that makes the audience root for them. Without this moment of likability early, audiences won't care what happens next.

In screenwriting: plant a small act of generosity, vulnerability, or humanity in the first 10 minutes. Not heroism — something ordinary that reveals good character.

### Condensed Beat Sheet for Short Films (10 minutes)
| Time | Beat |
|------|------|
| 0:00–1:00 | Opening image + set-up |
| 1:00–2:00 | Catalyst + debate |
| 2:00–4:00 | Break into Two + Fun and Games |
| 4:00–5:00 | Midpoint |
| 5:00–7:00 | Bad Guys Close In |
| 7:00–8:00 | All Is Lost + Dark Night |
| 8:00–9:30 | Break into Three + Finale |
| 9:30–10:00 | Final Image |

---

## 3-Act Structure

The universal architecture underlying most Western narrative. Simpler than Save the Cat but foundational.

### Act 1 — Setup (25% of runtime)
- Establish character, world, tone, and the protagonist's normal life
- Plant the inciting incident that creates the **central dramatic question**
- End Act 1 at the point of no return — the protagonist commits to the journey

**The central dramatic question:** Everything in the story is an attempt to answer this question. In *The Silence of the Lambs*: will Clarice catch the killer? In *Marriage Story*: can these two people survive their divorce?

### Act 2 — Confrontation (50% of runtime)
- Protagonist pursues their goal and encounters escalating obstacles
- First half of Act 2: exploration, first attempts, small wins and losses
- Midpoint: raises stakes, deepens investment
- Second half of Act 2: things get harder, the protagonist's flaw costs them
- End of Act 2: the "all is lost" moment — the goal seems impossible

### Act 3 — Resolution (25% of runtime)
- Protagonist applies what they've learned through all the suffering
- The final confrontation with the central obstacle
- The resolution of the dramatic question (yes or no — both are valid)
- The new equilibrium: the world after the story

### For Short Films (3-minute version)
- Act 1 (0–45s): Establish character + inciting incident
- Act 2 (45s–2:15): Obstacle, escalation, all-is-lost
- Act 3 (2:15–3:00): Resolution + final image

---

## The Pixar Story Spine

Originally developed by Kenn Adams for improv theater; popularized by Pixar storyboard artist Emma Coats. The key mechanism: every step is connected to the previous with "because of that," which forces causality — events can't just happen sequentially, they must cause each other.

```
Once upon a time there was... [establish the hero in their world]
Every day... [establish the routine, the normal, the "before"]
One day... [the inciting incident — something disrupts the normal]
Because of that... [the first consequence]
Because of that... [escalating consequence]
Until finally... [the resolution]
And ever since then... [the new normal — how the world has changed]
```

**Why it works:**
- Forces causality in every beat
- Guarantees transformation (the ending must be different from the beginning)
- Scalable to any length — works for a 30-second ad or a 120-minute film
- Especially powerful for testimonial content and personal brand stories

**Short-form application (45-second video):**
```
Once upon a time: "I was a [person with relatable struggle]..."
Every day: "I spent [time/effort] trying to [goal] but [obstacle]..."
One day: "Then I found/tried/learned [turning point]..."
Because of that: "[First change]..."
Until finally: "[Specific result with number/timeframe]..."
And ever since then: "Now [the after state that the viewer desires]..."
```

---

## Show Don't Tell

The central principle of visual storytelling. The screen is a visual medium. Use what the camera and microphone can actually capture.

### The Four Levels

**Level 1 — Action Over Emotional Labels**
Don't label emotions. Show the behaviors that express them.

- Don't: "She feels overwhelmed by everything."
- Do: "Three monitors, each with 40 tabs open. Coffee gone cold. Her cursor hovers over the 'delete account' button."

**Level 2 — Strong Verbs Over Adverb + Verb**
Replace weak verb + adverb with a single strong verb.

| Weak | Strong |
|------|--------|
| walks slowly | trudges |
| closes the door loudly | slams |
| sits down heavily | collapses into the chair |
| looks around nervously | scans the room |
| moves quickly toward | lunges at |

**Level 3 — Environment as Character**
A character's world reveals who they are. Design spaces and objects to carry meaning.

- A spotless apartment with no personal items: isolation, control, absence
- A workspace covered in half-finished projects: restless creativity, commitment issues
- A pristine desk with one photo turned face-down: something deliberately put away

Objects can carry symbolic weight across an entire film. Plant them early, return to them at turning points.

**Level 4 — The Whiplash Test**
In the film *Whiplash*, after a serious car crash, the protagonist doesn't check if he's injured — he runs toward the performance venue, blood streaming down his face, and plays the concert. Not one word of dialogue explains his obsession. His action says everything.

Before finalizing any scene: is there a way to remove the dialogue or voiceover and let the action carry the meaning?

---

## Subtext and Dialogue

The rule: **characters talk around the real subject, not about it** — unless there is a specific dramatic reason to name it directly.

On-the-nose dialogue is dialogue where characters say exactly what they mean:
> "I'm angry at you for leaving me."
> "I know. I'm sorry I hurt you."

Subtext is dialogue where the real subject lives underneath a different conversation:
> [Two people arguing about whose turn it is to do the dishes when the real subject is that he's been distant since she got the promotion]

**The subtext technique:**
1. Write the scene where characters say exactly what they mean (on-the-nose version)
2. Identify the real emotional subject
3. Choose an entirely different surface topic for the dialogue to be "about"
4. Rewrite every line to be about the new topic while preserving the emotional/dramatic content underneath

**What subtext creates:**
- Dramatic tension (the audience sees the gap between what's said and what's meant)
- Character depth (people who hide their feelings are more interesting than people who broadcast them)
- Active audience engagement (the viewer participates in decoding the meaning)

**When to break subtext:**
Sometimes characters must say the direct thing — when the stakes are at their highest, when a relationship is at its breaking point, or when the moment demands truth. These direct statements land harder because the rest of the script has trained the audience to expect indirection.

---

## Cold Opens and In Medias Res

### Cold Opens (TV)
A pre-credits sequence (usually 2–5 minutes) that hooks the audience before the episode proper begins. Functions as a standalone hook unit.

**Cold open types:**
- **Tonal cold open**: A scene that establishes the mood and world without necessarily connecting to the main plot
- **Cliffhanger cold open**: Drop the audience into a high-stakes moment; cut to credits; resume after
- **Standalone mini-story**: Tells a complete small story that illuminates the episode's theme
- **In medias res cold open**: Begin mid-event at a point of crisis, then flash back to "how we got here"

The cold open's job is to earn the credits — to make the viewer want to watch the episode that follows.

### In Medias Res
Latin: "into the middle of things." Begin the story at a moment of high action, tension, or drama, then establish the context that explains it.

**Structure:**
1. Open at maximum tension or interest — the moment most writers would place in Act 2
2. Establish the world and the backstory — but now the audience is already hooked
3. Build back up to and past the opening moment

**Examples:**
- *Breaking Bad* — opens mid-crisis (the desert, the RV, the sirens) before flashing back to the beginning
- *The Dark Knight* — opens on the bank heist before we meet Bruce Wayne
- Classic literary example: *The Odyssey* begins with Odysseus on Calypso's island — years into the journey

**Application to short-form and ads:**
Begin every script at the moment of most dramatic interest, not the beginning of the story. Exposition comes after you've earned the viewer's attention.

---

## Short Film Structure

Short films operate under extreme constraint — every scene must carry multiple functions simultaneously.

### The 10-Minute Short Film Blueprint

**Minutes 0–2: Establish the World and the Character**
- One visual that captures the protagonist's ordinary world
- One moment that reveals who they are (the Save the Cat moment)
- Plant the seed of the central dramatic question

**Minutes 2–4: Catalyst and Decision**
- The event that disrupts the ordinary world
- The protagonist's initial response (often resistance or confusion)
- The turn: they commit to engaging with the disruption

**Minutes 4–7: Complication and Escalation**
- The protagonist attempts to solve the problem
- First attempt fails or succeeds unexpectedly
- The real obstacle is revealed (often different from the surface obstacle)
- Midpoint: something changes the game

**Minutes 7–9: Crisis and Low Point**
- The protagonist faces their worst fear or biggest failure
- The "all is lost" beat
- A moment of stillness — the decision point

**Minutes 9–10: Resolution and Final Image**
- The protagonist acts from a changed place
- Resolution of the central dramatic question
- The final image: a visual echo of the opening that shows transformation

### The 3-Minute Short Film (Sketch / Advertising format)

- 0–30s: Establish character + plant the problem
- 30s–1:30: Escalating complications (comedy: misunderstandings. Drama: setbacks)
- 1:30–2:30: Crisis point — the worst version of the problem
- 2:30–3:00: Resolution + final beat (punch line, emotional peak, or twist)

---

## TV Pilot Structure

The pilot must accomplish more than a regular episode: it establishes the world, the characters, the tone, the premise, and — most importantly — the ongoing dramatic engine that makes viewers want episode 2.

### Drama Pilot (55–65 pages)

**Act 1 (pages 1–15):**
- Cold open / teaser: hook the audience in the first 3–5 pages
- Introduce the protagonist in their "before" world
- The inciting incident that breaks the status quo
- Establish the world rules — what kind of show is this?

**Act 2 (pages 15–35):**
- Protagonist enters the new world / new situation
- Introduce the key supporting characters
- Establish the central conflict and the factions
- The "fun and games" of the pilot premise — let the audience enjoy the world you've created
- Midpoint: something changes, raises the stakes

**Act 3 (pages 35–50):**
- Escalating complications
- Character relationships deepen
- The pilot's central crisis emerges

**Act 4 / Climax (pages 50–60):**
- Resolution of the pilot's immediate plot
- Setup for the ongoing series conflict
- End on a moment that makes episode 2 essential

**The last page of the pilot:** Must do one of two things — resolve the pilot's central question while opening a bigger one, or end on a revelation that recontextualizes everything. The audience must feel they cannot miss the next episode.

### The Three Pilot Questions

Every TV pilot must answer:
1. **Who is this show about, and why should I care about them?**
2. **What is the engine of conflict that will drive 50+ episodes?**
3. **What is the world of this show, and is it one I want to live in for years?**

If the pilot doesn't answer all three, it won't get picked up and it won't retain viewers.


<!-- ═══════ FILE: script-writer/references/visual-language.md ═══════ -->

# Visual Language — Lighting, Composition, and Prompt Vocabulary

"Cinematic" is not a direction. It is a word that has been used so many times in AI prompts that it has become near-meaningless — models default to: slightly dark, atmospheric haze, vague lens flare. This file replaces "cinematic" and other vague visual descriptors with specific technical vocabulary that reliably produces the emotional effect you want.

Every section ends with prompt-ready vocabulary you can copy directly into imagine.art generation.

---

## Lighting: What Each Setup Communicates

Lighting is the primary emotional carrier in visual content. Before choosing any other element, know what your lighting is doing to the viewer's nervous system.

### Lighting Setup Reference

**Rembrandt Lighting**
Setup: Single key light at 45° above and 45° to one side. Creates a triangle of light on the shadow cheek.
Emotional signal: Depth, authority, quiet tension, introspection, soulfulness. The viewer perceives the subject as complex and trustworthy.
Best for: Product stories with a human narrator, authority-building content, emotional brand films, any content where the speaker needs to feel credible.
Prompt vocabulary: `Rembrandt lighting, single key light upper left, triangle highlight on shadow cheek, dramatic shadow right side, classical portrait lighting`

**Split Lighting**
Setup: Light source directly to one side (90°), creating a hard line down the face or product.
Emotional signal: High drama, psychological duality, contrast, power, potential threat.
Best for: Bold product reveals, fashion editorial, transformation "before" moments, pattern-interrupt hooks.
Prompt vocabulary: `split lighting, 90 degree side key light, hard shadow divide, high contrast, dramatic`

**Backlight / Rim Light**
Setup: Light source behind the subject, creating a glowing edge and separation from background.
Emotional signal: Mystery, transcendence, the "chosen" quality, aspiration, separation from the ordinary world.
Best for: Product hero shots (the product glows, elevated from the surface), aspirational human content, cinematic silhouettes.
Prompt vocabulary: `backlit, rim light, separation from background, glowing edge, subject illuminated from behind, background slightly dark`

**Beauty / Butterfly Lighting**
Setup: Light source directly in front and slightly above, creating a small shadow under the nose (butterfly-shaped).
Emotional signal: Glamour, confidence, approachability in a premium context, self-assurance.
Best for: Beauty products, lifestyle content for creators, anyone facing camera with confidence.
Prompt vocabulary: `beauty lighting, butterfly lighting, soft front light slightly elevated, catch lights in eyes, minimal under-eye shadow`

**Golden Hour / Warm Backlight**
Setup: Low sun angle, warm amber tones, soft wrap-around quality, often slight lens flare.
Emotional signal: Romance, nostalgia, warmth, timeless quality, the feeling of a perfect moment.
Best for: Lifestyle campaigns, emotional product stories, aspirational human content, any content that should feel warm and human.
Prompt vocabulary: `golden hour lighting, warm amber backlight, low sun angle, soft lens flare, warm color temperature approximately 3200K, magic hour`

**High-Key Lighting**
Setup: Bright, even, minimal shadows, often white or very light background.
Emotional signal: Joy, clarity, openness, positivity, honesty. The viewer perceives the subject as transparent and cheerful.
Best for: Product demos, explainer content, beauty/skincare, anything that needs to feel clean and approachable.
Prompt vocabulary: `high-key lighting, bright even illumination, minimal shadows, white background, clean and open`

**Low-Key Lighting**
Setup: Darkness dominant, one or few small light sources, deep shadows.
Emotional signal: Mystery, luxury, sophistication, depth. The viewer leans in.
Best for: Premium product photography, luxury lifestyle, any content that should communicate exclusivity.
Prompt vocabulary: `low-key lighting, dominant darkness, single motivated light source, deep shadows, luxury, sophisticated`

**Volumetric / God Rays**
Setup: Light appears to travel through atmosphere, creating visible beams or shafts.
Emotional signal: Scale, transcendence, awe, something larger than the subject. The viewer feels small in a good way.
Best for: Brand awareness content, scale moments, anything meant to evoke wonder.
Prompt vocabulary: `volumetric lighting, god rays, light shafts through atmosphere, cinematic, awe-inspiring`

### Color Temperature Reference

| Temperature | Kelvin | Color Appearance | Emotional Effect |
|---|---|---|---|
| Candle | 1800K | Deep amber-orange | Intimacy, nostalgia, warmth, the oldest human comfort |
| Warm tungsten | 2700K | Warm white-amber | Home, safety, comfort, approachability |
| Studio warm | 3200K | Clean warm white | Professional warmth, beauty, premium lifestyle |
| Neutral daylight | 5600K | Pure white | Natural, realistic, honest, documentary |
| Overcast | 7000K | Cool white-blue | Clinical, detached, modern, tech |
| Deep cool | 9000K+ | Strong blue | Cold, alienation, technology, loneliness |

**The warm/cool tension:** Placing a warm-toned subject against a cool-toned background (or vice versa) creates inherent visual tension — the subject reads as human and special against an inhuman environment. This is the teal-orange grade in its spatial form.

---

## Color Psychology for Content

### Reliable Color Combinations

**Gold + Black:** Luxury, power, exclusivity. Use for premium product positioning or authority-building content. Risk: can read as pompous if the product doesn't match the claim.

**Navy + White:** Authority, trust, reliability. Standard for professional services, tech credibility plays. Emotional signal: "we know what we're doing."

**Teal + Orange:** The most used cinematic combination. Teal shadows, warm orange skin tones. Creates visual contrast, dynamic energy, the feeling of being in a story. Default for: lifestyle, travel, general aspirational content.

**Purple + Gold:** Premium creativity, innovation, mystery. Works for AI products, creative tools, forward-looking brands. imagine.art's own color territory.

**Muted Pastels:** Gen Z aesthetic, intimacy, softness. Works for creator-segment content, personal brand, slow lifestyle. Communicates: real, not corporate.

**High Contrast Monochrome + 1 Accent:** Bold, graphic, memorable. Fashion, editorial, art-adjacent. The single accent color becomes the brand's visual signature in that frame.

### The 60/30/10 Rule

For any single frame: 60% neutral/trust color (white, navy, gray, cream) / 30% brand identity color / 10% action/urgency accent. This ratio prevents visual noise while using color for conversion.

For imagine.art content: 60% clean neutral backgrounds, 30% brand purple or product color, 10% warm highlight or CTA accent.

---

## Composition: Emotional Choices

Every composition decision is an emotional decision. The viewer's eye is not neutral — it follows certain paths and generates certain feelings based on where and how elements are arranged.

### Subject Position

**Center frame:** Stability, confrontation, authority, formality. Use for: direct address to camera, symmetrical product reveals, confrontational hooks.

**Rule of Thirds (right intersection):** Dynamic, subject is entering the frame rather than filling it. Standard for product shots and lifestyle — subject has room to breathe, frame feels alive. Leave space at left for text overlay.

**Extreme close-up:** Intimacy, detail, texture, vulnerability. Use for: product texture reveals, emotional human moments, the specific detail that carries the Big Idea.

**Wide with subject small:** Scale awe, isolation, environment dominates. Use for: brand awareness content, "this is bigger than you think" moments, aspirational landscape content.

### Negative Space

Heavy negative space = luxury, solitude, focus, calm confidence. The subject doesn't need to compete — it simply is.
Minimal negative space = energy, urgency, claustrophobia, dynamism.

For product content: more negative space generally communicates higher quality. Crowded frames read as market stalls; spaced frames read as galleries.

### Depth: Three Planes

Creating visible foreground, midground, and background planes gives the image physical depth the viewer perceives as dimension. This is the difference between a flat product photo and one that feels spatial.
Prompt vocabulary: `shallow depth of field, foreground element slightly out of focus, subject sharp in midground, background bokeh, three-dimensional depth`

### Dutch Angle (Tilted Frame)

Camera tilted off horizontal. Scale with intent:
- **5–15°:** Subtle unease, something slightly wrong
- **20–35°:** Clear instability, disorientation, psychological tension
- **40°+:** Extreme disorientation, psychological break

Use deliberately for: pattern-interrupt hooks, before/after moments (tilted = the old way; straight = the resolved way), unconventional hooks designed to stop the scroll with wrongness.
Never use accidentally — it reads as amateur when unintentional.

---

## What "Cinematic" Actually Means

Stop using the word "cinematic" in prompts. Use these components instead:

| Element | What It Is | Prompt Vocabulary |
|---|---|---|
| **Aspect ratio** | 2.39:1 or 2.35:1 widescreen | `2.39:1 aspect ratio, anamorphic widescreen, letterbox` |
| **Depth of field** | Subject sharp, background blurred | `shallow depth of field, f/1.4 aperture, 85mm lens, bokeh background` |
| **Color grade** | Lifted shadows, slightly desaturated midtones, teal shadows + warm skin | `teal and orange color grade, lifted blacks, Hollywood LUT, slightly desaturated` |
| **Lens characteristics** | Slight barrel distortion, anamorphic flare, slight vignette | `anamorphic lens, subtle oval bokeh, horizontal lens flare, slight vignette` |
| **Frame rate** | 24fps motion blur | `24fps, natural motion blur, film look` |
| **Camera movement** | Deliberate, motivated, smooth | `slow dolly in, smooth camera movement, motivated direction` |
| **Lighting quality** | Large single-source key light, motivated | `single key light, large soft source, motivated from window, natural fill` |
| **Film stock** | Grain, latitude, dynamic range | `shot on ARRI Alexa, film grain, wide dynamic range, organic texture` |

**The reliable replacement for "cinematic":**
```
shot on ARRI Alexa 35, 35mm anamorphic lens, 2.39:1 aspect ratio, shallow depth of field f/2.8, teal and orange color grade, lifted shadows, single motivated window light
```

This prompt produces a specific, consistent look. "Cinematic" does not.

---

## Contrast as Tension

Placing two opposing elements within a single frame creates inherent visual tension — the brain tries to resolve the contradiction and stays in the frame while it does.

**Productive contrast pairs:**

| First Element | Opposing Element | Tension Created |
|---|---|---|
| Dark environment | Warmly lit subject | Subject is special, chosen, protected |
| Premium product | Rough, everyday surface | Unexpected juxtaposition stops the eye |
| Still background | Moving subject | Subject has energy the world doesn't |
| Close intimacy (tight crop) | Vast, empty background | Isolation or scale — the subject is alone in something big |
| Warm tones in left frame | Cool tones in right | Inherent left-right tension, eye moves between |
| Sharp subject | Extremely blurred everything else | Subject is the only thing that exists |

**For AI prompts, state the contrast explicitly:** Don't assume the model will create it. `Subject warmly lit in amber tones, background in cool blue tones, strong warm-cool contrast within single frame`

---

## Prompt Vocabulary Reference

Copy these phrases directly into imagine.art prompts.

### Lighting
```
Rembrandt lighting, triangle highlight on shadow cheek
Split lighting, 90 degree side key, hard shadow divide
Backlit, rim light, glowing edge, subject separated from background
Golden hour, warm amber backlight, magic hour
High-key, bright even illumination, clean and open
Low-key, dominant shadows, single motivated light source
Volumetric lighting, god rays, light shafts
Studio softbox, large diffused key light, beauty lighting
Warm tungsten practical, approximately 3200K
Cool daylight, 5600K, natural and honest
```

### Camera and Lens
```
Shot on ARRI Alexa 35, film look, organic grain
35mm anamorphic, horizontal lens flare, oval bokeh
85mm portrait, f/1.4, shallow depth of field, background bokeh
24mm wide angle, slight barrel distortion, environmental
135mm telephoto compression, flattened perspective, isolated subject
Handheld, subtle organic movement, documentary feel
Slow dolly in, smooth, motivated
Orbital camera move, continuous, no cut
Crash zoom, rapid push in, 1 second
Pull back reveal, slow, expanding scale
```

### Color Grade
```
Teal and orange color grade, Hollywood LUT
Warm nostalgic grade, golden tones, slight desaturation
Cold clinical blue grade, high contrast, blue shadows
Bleach bypass, crushed blacks, muted color
Soft pastel grade, film grain, Gen Z aesthetic
Lifted blacks, shadow detail preserved, cinematic latitude
Warm midtones, cool highlights, complementary contrast
```

### Composition
```
Rule of thirds, subject at right intersection
Extreme negative space, subject small in frame
Three planes of depth, foreground midground background
Symmetrical composition, center axis, formal
Dutch angle, 15 degrees, subtle unease
Tight close-up, no background, subject fills frame
Wide establishing shot, subject small, environment dominant
```

### Texture and Quality
```
Photorealistic, every detail visible, studio quality
Film grain, organic texture, 35mm feel
Ultra sharp, 8K detail, commercial photography
Slightly soft, painterly quality, editorial
Raw and authentic, unprocessed, documentary
```


<!-- ═══════ FILE: script-writer/references/visual-direction.md ═══════ -->

# Visual Direction
## Shot-Level Language for AI Video & Short-Form Scripts

Visual direction bridges the gap between a written script and what actually gets produced. This file gives you the specific vocabulary and notation to write direction that a video editor, motion designer, or AI video model can execute without a second conversation.

---

## The Three Channels (Write All Three for Every Hook)

Every hook has three simultaneous delivery channels. A script that only covers one will underperform.

| Channel | What It Is | Why It Matters |
|---------|-----------|----------------|
| **Audio** | The spoken line | Primary for sound-on viewers, sets pacing |
| **Visual** | What's on screen | Primary for all viewers — the first impression before sound registers |
| **Text Overlay** | On-screen captions/supers | Backup for sound-off viewers (60–85% of feed scroll); also doubles the hook impact for sound-on viewers |

**Script format for hook delivery:**
```
HOOK (0–3s):
[AUDIO] "One of these cost $0. One cost $3,000."
[VISUAL] Split screen: two identical-quality product images — left labeled "$3,000 photoshoot," right labeled "30 seconds, imagine.art"
[TEXT OVERLAY] $3,000 vs $0 — spot the difference
```

Never write just the spoken line. Always write the visual and text overlay alongside it.

---

## Camera Language Glossary

Use this vocabulary in visual direction lines. Each term maps to a specific behaviour that editors and AI video models understand precisely.

### Movement
- **Push in / Dolly in** — Camera moves toward the subject. Creates intensity, intimacy, urgency. Use for reveals and emotional peaks.
- **Pull out / Dolly out** — Camera moves away. Creates context, scale revelation, distance. Use for scale awe hooks.
- **Pan left / Pan right** — Horizontal rotation of the camera. Use to follow action or reveal something off-frame.
- **Tilt up / Tilt down** — Vertical rotation. Tilt up = reveal scale (small to large). Tilt down = ground the scene.
- **Track / Follow** — Camera moves alongside a moving subject. Creates motion energy without disorientation.
- **FPV (First-Person View)** — Camera simulates the subject's own eyes. Maximum immersion, high proprioception trigger.
- **Orbit / Arc shot** — Camera circles the subject. Use for product reveal moments or premium showcase.
- **Crane / Rise** — Camera moves upward. Epic scale, overview reveal, "god's eye" perspective.
- **Crash zoom** — Rapid, aggressive push in. Pattern interrupt. Aggressive hook energy.
- **Whip pan** — Fast horizontal pan that blurs. Transition device or pattern interrupt.

### Speed
- **Real-time** — Normal pacing. Default.
- **Slow motion (0.5x / 0.25x)** — Slows action to emphasise texture, impact, or detail. Use for product showcase or proprioception triggers.
- **Speed ramp** — Starts slow, accelerates (or vice versa). Dynamic energy. Use for reveal moments.
- **Hyperlapse** — Extreme time acceleration. Use for process reveals ("watch 2 hours of editing happen in 8 seconds").
- **Freeze frame** — Motion stops. Use to hold on a specific moment — a reaction, a detail, a comparison.

### Framing
- **ECU (Extreme Close-Up)** — Fills the frame with a single detail (eye, label, texture). Maximum intimacy and texture.
- **CU (Close-Up)** — Head and shoulders, or product in detail. Most common for talking head and product showcase.
- **MCU (Medium Close-Up)** — Mid-chest up. Standard interview/UGC framing.
- **MS (Medium Shot)** — Waist up. Standard tutorial framing.
- **WS (Wide Shot)** — Full body or full scene. Establishes environment.
- **EWS (Extreme Wide Shot)** — The subject is small in the frame. Used for scale awe hooks.
- **Split screen** — Frame divided into two (or more) simultaneous views. Most effective for before/after and comparison hooks.
- **PiP (Picture-in-Picture)** — Smaller inset video within the main frame. Use for reaction shots, interface demos alongside talking head.

---

## Text Overlay Styles

Text overlays are not subtitles — they're a distinct creative element. Use the right style for the right moment.

### Hook Supers
**Purpose:** Deliver the hook for sound-off viewers. Must work as a standalone sentence without audio.
**Style:** 3–6 words maximum. Largest text on screen. High contrast. Appears in first 1.5 seconds.
**Examples:**
- `$0 vs $3,000 — spot the difference`
- `12 words. 28 seconds. No photographer.`
- `This isn't a real photo.`

### Emphasis Callouts
**Purpose:** Highlight a specific word or number mid-sentence for emphasis.
**Style:** Single word or short phrase, appears timed to when it's spoken. Can be bold, different colour, or animated pop.
**Examples:**
- [EMPHASIS] `FREE` — appears when "free" is spoken
- [EMPHASIS] `8 SECONDS` — appears timed to the number

### Caption Track
**Purpose:** Full-sentence subtitles for accessibility and sound-off viewing.
**Style:** Standard caption position (bottom third), high contrast, 2–3 words per caption flash for TikTok pacing. Not the same as the hook super.
**Note:** Caption track is always on. It's not optional for any platform.

### Context Tags
**Purpose:** Quick visual identifier for a section transition.
**Style:** Small pill/tag format, top corner. Often used in tutorials.
**Examples:** `BEFORE` / `AFTER` / `STEP 1` / `RESULT` / `COST: $0`

### CTA Overlays
**Purpose:** The visual version of the CTA, appears in the final 10–15 seconds.
**Style:** Clear, action-oriented, button-style or arrow-pointing.
**Examples:** `Link in bio ↓` / `Try it free →` / `Comment GENERATE ↓`

---

## Visual Hook Patterns (First 3 Seconds)

The first 3 seconds are a distinct visual design problem. Here are the patterns that consistently stop scrolls, mapped to use case.

### The Static Reveal
Start on a single, striking image. Hold for 1.5 seconds. Then introduce motion or context.
- Best for: Output showcase, quality demonstration
- Why it works: The brain processes the image before the video feels like a video. By the time it registers as content, it's already been watched.
- Direction note: No movement in the first 1.5 seconds. Motion starts after the image registers.

### The Mid-Action Drop
Video begins mid-motion — something is already happening.
- Best for: Cold opens, energy-driven hooks, process reveals
- Why it works: No ramp-up means no time to decide to scroll. The brain catches up.
- Direction note: First frame should show motion already in progress. Use "cut to mid-motion" language.

### The Split Screen Comparison
Frame divided from the first frame. Left/right labelled.
- Best for: Before/after, cost comparison, quality demonstration
- Why it works: The comparison structure is immediately understood. Viewer instinctively looks to resolve "which is which."
- Direction note: Labels appear in the first 0.5 seconds. Both sides should be visible in the first frame — don't reveal one side after the other.

### The Text-First Hook
Bold text appears before or simultaneously with the visual.
- Best for: Statement hooks, bold claims, data-driven hooks
- Why it works: Works for sound-off viewers. Text is the hook; visual is the context.
- Direction note: Text appears at frame 1. 4–6 words max. High contrast. Visual follows 0.5 seconds later.

### The Impossible Physics Frame
First frame shows something that cannot exist in real photography.
- Best for: AI capability showcase, scale awe, pattern interrupt
- Why it works: Brain registers the anomaly before it can be dismissed. The "wait, that's not possible" moment is the hook.
- Direction note: Establish the impossibility clearly in frame 1 — don't ease into it. The more impossible it is to have been filmed, the longer the hold.

### The UGC Mismatch
Opens with deliberately lo-fi framing (selfie camera, slight shake, natural light), then within 3–5 seconds reveals something that cannot have been filmed that way.
- Best for: Skeptic conversion, AI credibility hooks, UGC-style ads
- Why it works: Sets up "just a phone video" expectations, then violates them with impossible quality. Cognitive dissonance keeps the viewer.
- Direction note: First 2 seconds must look genuinely handheld and casual. The reveal is the transition to impossible quality.

---

## Transition Language

Transitions in AI video scripts describe how the camera or scene moves between moments.

| Transition | When to Use |
|-----------|------------|
| **Hard cut** | Energy, pace, contrast. The default for short-form. |
| **Match cut** — cut between two similar shapes, movements, or moments | Visual storytelling, brand films, "satisfying" aesthetic |
| **Wipe** | Time-lapse feel, before/after, process steps |
| **Dissolve / Cross-fade** | Gentle tonal shifts, emotional peaks, time passing |
| **Speed ramp into cut** — slow down just before the cut | Dramatic emphasis, product reveals |
| **Continuous shot** — camera never cuts | Immersion, premium feel, trust (nothing to hide) |
| **Jump cut** — same framing, slight skip in time | Energy, authenticity, creator-style talking head |

---

## Platform-Specific Visual Notes

### TikTok
- **Aspect ratio:** 9:16 (full vertical). No safe zones for horizontal content.
- **Text overlay safe zone:** Bottom 20% often covered by likes/comments UI. Keep critical text in the middle 60% of the frame vertically.
- **First frame:** Needs to be compelling when the app shows a static preview before play. Design the first frame as a still image first, then add motion.
- **Caption track:** On-screen captions are table stakes. Most TikTok content is watched muted in the wild.
- **Hook text position:** Middle of screen, high contrast. Never bottom (covered by UI) or top corners (covered by creator handle).

### Instagram Reels
- **Aspect ratio:** 9:16 for Reels feed. 4:5 or 1:1 for feed posts with video.
- **Visual quality:** Slightly higher visual quality expectation than TikTok. Colour grading and composition matter more.
- **Sound-off ratio:** Higher than TikTok. Visual and text carry more of the story.
- **Stories vs Reels:** Stories are ephemeral awareness; Reels are discovery. Different scripts for each.

### YouTube Shorts
- **Thumbnail frame:** YouTube displays a frame from the video as the thumbnail in feed. Identify which frame is most compelling and make sure it exists clearly in the first 3 seconds.
- **Subscribe CTA:** More natural and effective here than on any other platform. "Subscribe for more" works because YouTube's subscription model is native.
- **Educational bias:** Shorts audience skews toward information-seeking. Scripts with a clear takeaway or learning outperform pure aesthetic content.

### LinkedIn
- **Auto-play on mute:** Nearly all LinkedIn video starts muted. Your first 3 seconds of text overlay must carry the hook entirely.
- **Square format (1:1)** performs comparably to 9:16. Design for both.
- **Professional framing:** Talking head with good lighting and minimal background > chaotic UGC aesthetic.
- **CTA language:** "Try it," "Book a demo," "See the case study" work better than "Link in bio."

---

## Production Notes Format

When delivering a complete script, always include a production notes section. Format:

```
## PRODUCTION NOTES

TALENT: [Who should deliver this — creator, brand spokesperson, UGC-style, voiceover only, no talent]
FRAMING: [CU talking head / product-only / screen recording + pip / split screen]
ENVIRONMENT: [Where it's shot — minimal background / real context / AI-generated environment]
LIGHTING: [Natural window light / studio / ambient — what feeling]
SOUND: [Voice-only, no music / lo-fi background / silence / trending audio]
CAPTIONS: [Required / style note]
B-ROLL: [List of specific B-roll shots needed alongside main footage]
PLATFORM NOTES: [Any platform-specific adaptations needed]
CUT-DOWN: [If a shorter version is needed — e.g., "cut to 15-second version by removing [section]"]
```

Production notes are not optional for any deliverable over 30 seconds. The editor shouldn't have to interpret what you meant.

---

## A/B Visual Variants

When running visual A/B tests on the same hook copy, vary one element at a time:

| Variable | Variant A | Variant B |
|----------|-----------|-----------|
| **Framing** | Tight close-up on product | Wide shot showing environment |
| **Opening motion** | Static → motion | Motion from frame 1 |
| **Text position** | Centre screen | Top third |
| **Talent vs. no talent** | Creator talking head | Product-only visual |
| **Colour grade** | Warm/natural | Cool/clean |
| **Background** | Real environment | Clean/minimal |

Change one variable. Same hook copy, same body, same CTA. The visual variable that wins tells you something about what your audience is actually responding to — and that learning applies to every piece of content going forward.


<!-- ═══════ FILE: script-writer/references/auteur-styles.md ═══════ -->

# Auteur Styles — Director Methods & Promptable Aesthetics

Two uses for this file:
1. **Writing method** — steal how master directors construct dialogue, structure, and tension for scripts and brand films.
2. **Visual direction** — the auteur adjective taxonomy converted into prompt-ready vocabulary for imagine.art generation. A director's name is the highest-compression style instruction that exists; this file decompresses each one into specific, promptable components (models respond far better to the components than to the name alone).

---

## Part 1: Writing Methods Worth Stealing

### Tarantino — Dialogue Architecture

**Method-writing:** He writes as a novelist, not an outliner — assimilating into characters' psychology, building backstories that never appear on screen. Practical rule: **commit to the character's ignorance.** If the character doesn't know a plot point, the scene cannot behave as if they do. This alone preserves authentic tension in dialogue scenes.

**The Pledge:** open a scene with a provocative statement that promises stakes *before* providing context. ("Nobody tips a robot." — now the viewer needs the context.) This is a cold-open mechanism that works in 1.5-second hook windows.

**The mundane derailment (via Elmore Leonard):** derail genre expectations with real-life friction — the bathroom break, the forgotten watch. In campaign terms: interrupt the polished AI demo with a human complication ("...and then my cat walked on the keyboard mid-generation"). The collision of the impressive and the mundane reads as authenticity.

**Tangential dialogue as psychological baseline:** the Reservoir Dogs tipping debate looks like filler but covertly maps every character's moral alignment before violence erupts. Application: a "random" opening conversation in a brand film should secretly establish who the characters are, so the turn lands harder.

**Information flow across three acts:** Act 1 — audience knows less than the characters. Act 2 — audience catches up. Act 3 — audience knows MORE than the characters (maximum dramatic irony). Use this for campaign arcs: video 1 withholds, video 2 explains, video 3 lets the viewer feel ahead of the world.

**Weaponized pacing:** lull with slow, methodical dialogue so the snap — the reveal, the cut, the drop — lands jarring. Silence architecture (see `audio-hooks.md`) is the audio implementation of this.

### Nolan — Structural Mathematics

**Time as a weapon, not a backdrop.** Nolan manipulates the audience's *experience* of time to mirror the protagonist's psychology: Memento's backward color timeline simulates amnesia; Dunkirk's triptych (a week / a day / an hour) compresses and expands subjective time. Application: a 30-second spot can run two timelines — the 3-week "old way" intercut with the 28-second "new way" — and the *editing rhythm itself* carries the argument.

**The visual anchor rule:** in Following, jumbled chronology stayed legible because one visual anchor (the protagonist's changing appearance) tracked position in time. If you scramble structure, you owe the audience exactly one consistent orientation anchor: a wardrobe state, a color grade shift, a prop.

**Practical-first credibility:** Nolan's in-camera bias exists because visible artifice stains visceral weight. AI-content translation: the more impossible the content, the more grounded the capture language must be (handheld weight, lens breathing, natural light — see the realism stacks in the prompting skills). Impossible thing + documentary capture = the tension that hooks.

**Signal your intent:** Nolan opened his £6,000 debut with one polished dolly shot so audiences read the later handheld as *choice*, not incompetence. Open any low-fi or UGC-style campaign with one controlled, composed frame — then the rough texture reads as style.

---

## Part 2: The Auteur Adjective Taxonomy — Prompt-Ready

Use these as creative-direction shorthand with the user ("we could go Andersonian or Lynchian on this") and as decomposed vocabulary in generation prompts. **Never prompt just the director's name** — prompt the components.

### Andersonian (Wes Anderson)
- **Signature:** planimetric staging, perfect formal symmetry, pastel palettes, deadpan choreography, storybook whimsy.
- **Emotional use:** controlled whimsy, irony, precious worlds; brand films that want charm without sentimentality.
- **Prompt vocabulary:** `perfectly symmetrical composition, centered subject facing camera, planimetric flat staging, pastel color palette, matte even lighting, deadpan expression, meticulous production design, storybook framing, 40mm lens straight-on`

### Bayhem (Michael Bay)
- **Signature:** rapid editing, saturated pyrotechnics, 360° low-angle hero shots, massive kinetics.
- **Emotional use:** maximum adrenaline; product-as-action-hero; unhinged variations.
- **Prompt vocabulary:** `low angle hero shot, 360 degree orbital camera move, golden magic-hour backlight, lens flare, high saturation, dust and debris in air, dynamic motion blur, epic scale`

### Bigelowesque (Kathryn Bigelow)
- **Signature:** visceral high-tension realism; the psychological toll of high-stakes environments.
- **Emotional use:** authenticity under pressure; B2B "in the trenches" narratives; skeptic-conversion content.
- **Prompt vocabulary:** `handheld documentary camera, urgent close framing, available light, desaturated tactical palette, shallow focus on eyes, sweat and texture detail, embedded observer perspective`

### Bergmanesque (Ingmar Bergman)
- **Signature:** stark psychological chamber drama, extreme close-ups, prolonged silence, existential dread.
- **Emotional use:** identity-shift content played straight; dramatic pause architecture.
- **Prompt vocabulary:** `extreme close-up on face, stark single-source light, deep shadow, neutral gray background, long held stillness, austere composition, black and white or muted tone`

### Cronenbergian (David Cronenberg)
- **Signature:** body horror; flesh merging with technology; biological anxiety.
- **Emotional use:** unhinged variations only; pattern-interrupt hooks about human/AI merging. Handle with brand-safety judgment.
- **Prompt vocabulary:** `biomechanical texture, organic-technological fusion, clinical fluorescent lighting, unsettling anatomical detail, sterile institutional environment, glistening surfaces`

### Fincher-monochromatic (David Fincher)
- **Signature:** monochromatic schemes (greens, grays, blues), oppressive unified atmosphere, surgical camera precision, psychological decay.
- **Emotional use:** premium tension; tech-noir product worlds; the "cold institutional world" register.
- **Prompt vocabulary:** `monochromatic green-gray grade, low-key lighting, perfectly locked-off camera, oppressive uniform color temperature, deep blacks, sodium vapor and fluorescent practicals, clinical precision`

### Lynchian (David Lynch)
- **Signature:** wholesome Americana juxtaposed with dark surrealist undercurrent; dream logic; industrial soundscapes.
- **Emotional use:** pattern interrupts; anti-hooks; the uncanny "something is wrong in this frame" mechanic.
- **Prompt vocabulary:** `1950s Americana surface, single wrong element in frame, dreamlike slow motion, deep red curtain, flickering practical light, uncanny stillness, industrial ambient hum (audio), night-time suburban glow`

### Malickesque (Terrence Malick)
- **Signature:** philosophical visual poems; whispering voiceover; floating handheld camera; golden-hour everything.
- **Emotional use:** aspirational identity-shift content; brand films about meaning; the emotional register of "what would you make if execution was no longer the obstacle?"
- **Prompt vocabulary:** `golden hour backlight, sun flaring through hands and grass, floating steadicam drifting low, natural light only, wide-angle intimate close focus, wind in fabric and hair, contemplative pace, whispered voiceover (audio)`

### Miyazakian (Hayao Miyazaki)
- **Signature:** melancholy whimsy, hand-drawn warmth, environmentalism, the joy of flight.
- **Emotional use:** wonder without cynicism; animation-styled campaigns; awe with heart.
- **Prompt vocabulary:** `hand-painted animation style, lush cumulus clouds, wind-swept grass fields, soft watercolor palette, flight sequence, warm nostalgic light, quiet in-between moment`

### Nolanian (Christopher Nolan)
- **Signature:** large-scale practical spectacle, non-linear architecture, men in suits, subjective time.
- **Emotional use:** high-concept campaign structures; time-delta cost-destruction spots; premium B2B gravitas.
- **Prompt vocabulary:** `IMAX-scale composition, practical in-camera effect, cool steel-blue and charcoal palette, tailored suit silhouette, monumental architecture, cross-cut parallel action, low ominous brass score (audio), rotating environment`

### Tarantinoesque (Quentin Tarantino)
- **Signature:** pop-culture-saturated dialogue, chapter structure, trunk shots, sudden tonal snap from banter to violence, needle drops.
- **Emotional use:** dialogue-driven UGC and talking-head content; The Pledge cold opens; tension-release pacing.
- **Prompt vocabulary:** `low trunk-shot angle looking up at subjects, 70s film stock grain, warm saturated color, chapter title card typography, long unbroken dialogue take, sudden whip-pan, diner booth setting`

---

## Part 3: Color Schemes as Directorial Signature

Color scheme selection is the fastest way to inherit a director's psychology without imitating their frames. (Deeper lighting vocabulary: `visual-language.md`.)

| Scheme | Mechanism | Psychological Effect | Signature User | Prompt Phrase |
|---|---|---|---|---|
| **Monochromatic** | Shades/values of one hue | Oppressive unity, stylized decay, premium control | Fincher | `monochromatic [hue] palette, unified color temperature` |
| **Analogous** | 3 adjacent wheel colors | Harmony, comfort, naturalism | naturalist drama | `analogous warm palette, no harsh color contrast` |
| **Complementary** | Opposite wheel pairs (teal/orange) | Maximum contrast + vibrancy, eye locks to focal point | Snyder; blockbuster grade | `complementary teal and orange grade, warm subject against cool environment` |
| **Triadic / Tetradic** | 3–4 evenly spaced hues | Balanced but vivid, storybook dynamism | del Toro | `triadic color palette, balanced vivid primaries` |
| **Associative** | One color = one character/theme | Visual shorthand; instant recognition across a series | Gerwig's *Barbie* pink | `[color] as recurring signature element on [subject] in every scene` |

**Campaign rule:** associative color is the cheapest brand-consistency device in AI generation — assign the brand one anchor color, place it on a different object in every scene, keep the rest of the palette cold or neutral. ("Orange anchor in a cold institutional world" is this pattern.)

---

## Part 4: Choosing an Auteur Register — Decision Guide

| Campaign need | Register |
|---|---|
| Charm, control, irony | Andersonian |
| Aspirational meaning, identity shift | Malickesque |
| Premium tension, tech-noir | Fincher-monochromatic / Nolanian |
| Pattern interrupt, uncanny | Lynchian |
| Dialogue-driven, tension-release | Tarantinoesque |
| Maximum adrenaline, unhinged | Bayhem |
| Gritty authenticity, skeptic conversion | Bigelowesque |
| Wonder without cynicism | Miyazakian |

Mixing registers: pick ONE dominant register per piece; a second register may appear only as a deliberate collision (e.g., Andersonian frame invaded by a Lynchian wrong element) — and that collision should BE the hook.


<!-- ═══════ FILE: script-writer/references/unhinged.md ═══════ -->

# Unhinged — The Creative Rule-Breaking Framework

Safe content is forgettable. The hooks and visuals that actually circulate — that people screenshot, share, or rewatch twice because they couldn't believe what they saw — almost always involve a deliberate rule violation. This file is the system for doing that intentionally rather than accidentally.

**Important distinction:** This is not about being random. Random is easy and forgettable. Deliberate weirdness has a specific internal logic, a clear emotional target, and a consistent aesthetic across executions. The difference between viral and confusing is the coherence of intent.

---

## The Test of Coherence

Before using anything from this file, apply this test:

> "Can I explain why this rule is being broken in one sentence that references a specific emotional or cognitive goal?"

If yes → proceed. The rule break is intentional.
If no → don't do it. It's noise.

**Example:**
- "We're starting the video in complete silence for 2 seconds because silence in an audio-on environment creates a jarring stop that the viewer must resolve by watching." ✓ Coherent.
- "We're making the product look deliberately ugly because... it's interesting?" ✗ Not coherent.

---

## The Convention Map — What Can Be Productively Broken

Every piece of short-form marketing content follows an implicit template. Breaking any convention has a different risk/reward profile.

| Convention | What Productively Breaking It Looks Like | Risk | When to Use |
|---|---|---|---|
| Hook is a visual statement | Start mid-action, no setup, mid-sentence, mid-crisis | Low | Almost always — this is the cold open principle |
| Music is high-energy and trendy | Complete wrong genre: classical under fast cuts, silence at the reveal, ASMR during product demo | Medium | When you want the viewer to stop and wonder why |
| CTA is at the end | Soft CTA at 3 seconds, then ignore it entirely for the rest of the video | Medium | When you want to feel non-commercial while still seeding the action |
| Visual quality is polished | Deliberately lo-fi: phone quality, bad framing, grain, imperfect | Medium | When authenticity > aspiration for your audience |
| Product is always the hero | Product barely visible, or revealed only in the final second | High | When the emotional story is the hook, not the product |
| Pace is fast and energetic | Extremely slow, meditative, almost uncomfortably deliberate | Medium | When the category is saturated with fast content — stillness becomes the interrupt |
| Narrator is enthusiastic | Bored, flat, deadpan delivery — almost zero affect | Medium/High | When used as irony or when the content is so obviously impressive that understatement is more powerful than excitement |
| Video ends with resolution | End mid-sentence or mid-action with no resolution | High | When you need rewatches — the unresolved ending loops naturally |

---

## The 5 Specific Techniques

### Technique 1: The Wrong Aesthetic (Deliberately Lo-Fi in Hi-Fi Context)
Take premium content and present it with phone-camera quality, bad lighting, and zero production polish. This reads as authentic and deliberately anti-commercial — which on TikTok signals trustworthiness. It's also a pattern interrupt because viewers expect production quality to signal investment.

**Why it works:** The lo-fi aesthetic is now the signal for "real person, not marketing department." Polished production triggers the "ad skip" reflex; rough production triggers the "this might be real" response.

**Best for:** imagine.art UGC hooks for the creator and e-commerce segments. A photorealistic AI-generated image presented with phone footage and zero music is more credible than the same image in a polished reel.

**Generation approach:**
```
Add to prompt: deliberately lo-fi, shot on phone, slightly underexposed, handheld shake, unpolished, feels amateur — not professional, not staged
```

### Technique 2: Sonic Incongruity (The Wrong Sound)
A perfectly standard hook visual with completely wrong audio. Premium product reveal with the sound of a dial-up modem. Stunning AI-generated landscape with supermarket ambience. The brain tries to reconcile the mismatch and holds the frame while doing so.

**Why it works:** The mismatch creates a question the viewer has to answer: "why is this happening?" That question is completion bait.

**Best for:** Pattern-interrupt awareness content. Any campaign where you want to generate comments and shares rather than direct conversion.

**Script notation:**
```
[VISUAL: stunning AI product shot, immaculate quality]
[AUDIO: dial-up modem sound, 2 seconds]
[AUDIO TRANSITION: clean silence, then premium ambient sound fades in]
[TEXT OVERLAY: Before imagine.art. / After imagine.art.]
```

### Technique 3: The Anti-Hook (Start With the Thing Everyone Skips)
Begin with what looks — visually and tonally — like a standard ad. Go completely on-the-nose. "This is a sponsored advertisement." State the commercial intent directly. The meta-awareness creates intrigue because it subverts the expectation that marketing tries to hide its nature.

**Why it works:** Audiences have infinite pattern recognition for ads trying to not look like ads. Dropping the pretense entirely disarms the skip reflex and signals confidence.

**Best for:** Sophisticated, platform-native audiences (agencies segment, filmmakers, content creators who've seen everything).

**Example:**
```
[spoken, deadpan] "This is an advertisement for imagine.art."
[pause]
"We're going to show you something in the next 20 seconds that your product photographer cannot do."
[hard cut to the image]
```

### Technique 4: Format Parody
Use a recognizable content format — tutorial, testimonial, behind-the-scenes — but betray its expectations at a key moment. The format sets up a contract with the viewer; violating that contract is the hook.

**Parody variations:**

*The bad tutorial:* Opens exactly like a tutorial. "Okay so step one—" then cuts to the finished product already on screen with no steps shown. Voiceover: "Actually, step one is the only step."

*The reluctant testimonial:* "I didn't want to recommend this. I told my team it was too good. Here's why I changed my mind."

*The behind-the-scenes that reveals nothing:* An elaborate "how we made this" video that ends with: "And that's the prompt. Twelve words." The anti-climactic reveal is the hook.

### Technique 5: Full Deconstruction (For Committed Executions Only)
The entire format is subverted — no hook, no structure, no conventional narrative. This is the Nutter Butter strategy: build a consistent internal world that follows different rules than standard marketing content, and maintain that world across every single execution.

**The Nutter Butter case study (what actually happened):**
- Starting audience: 3,100 followers
- Within months of launching their psychedelic, anti-design TikTok strategy: 700,000 followers, 4.1 million new likes
- Nielsen confirmed: household penetration among Gen Z and Gen Y up 15% year-over-year
- Strategy: Anti-commercial visuals, deliberately unsettling characters (Aidan, the Nutter Butter Man), psychedelic logic, no CTAs, built on weekly community comment loops

**Why it worked:** Internal consistency. Every video followed the same unhinged aesthetic — viewers who watched one knew what to expect from the next. The "wrongness" was authored, not accidental. And it was precisely targeted at Gen Z values: 82% say "weird is in," 58% say the more absurd something is the cooler it becomes.

**For imagine.art:** Full deconstruction requires organizational commitment. You can't do this for one video and return to conventional content — the audience sees the inconsistency. Only use if you're willing to build and maintain a distinct content persona.

**If you do commit:** Build the world first. Name the recurring characters, the visual logic, the sound palette, the signature phrase. Every execution should feel like an episode of an ongoing universe, not a standalone ad.

---

## The "Productively Wrong" vs. "Just Wrong" Line

| Productively Wrong | Just Wrong |
|---|---|
| Lo-fi aesthetic applied intentionally to premium content | Bad quality because of inadequate production |
| Silence as a deliberate pause before a reveal | No audio because someone forgot to add it |
| Deadpan narration as ironic understatement | Flat narration because the script was dull |
| Product barely visible — emotional story is the hook | Product absent because the brief was unclear |
| Wrong music genre chosen to create cognitive dissonance | Wrong music because it was the first track in the library |
| Mid-sentence open because you're entering a conversation already in progress | Mid-sentence open because the intro was cut without replacing it |

The line is always the same: **Was this chosen?** Intentional weirdness feels authored. Accidental weirdness feels cheap.

---

## Prompting AI for Unexpected, Unconventional Output

Standard prompts produce standard output. To push models toward unexpected results, you need to move them away from the center of their training distribution — toward the margins where things get genuinely strange.

### Prompt vocabulary for unconventional output:

```
Deliberately lo-fi, VHS aesthetic, tracking lines, grain
Uncanny, slightly wrong proportions, unsettling in an interesting way
Anti-commercial, raw, unpolished, feels filmed by accident
Surreal juxtaposition: [specific incongruent combination — name both elements]
Dreamlike logic where cause and effect don't match
Late 2000s internet aesthetic, compression artifacts, JPEG quality
Intentional distortion, stretched perspective, wrong focal length for scene
Oversaturated, color bleed, intentionally wrong color grade
Found footage aesthetic, surveillance camera angle
Deliberately flat lighting, uncanny valley quality, slightly wrong
```

### The Glitch Aesthetic as a Tool

AI models at the margins of their training data produce genuinely uncanny outputs: liminal spaces, partial faces, objects that are almost right. Experienced AI creatives don't regenerate away from these — they use them as raw material. The glitch is not a failure; it's an aesthetic.

```
Glitch art aesthetic, digital artifacts, corrupted render
Liminal space, uncanny emptiness, too-normal in a wrong way
Almost right, subtly off, something is incorrect but you can't identify it
Digital distortion, pixel sorting effect, data corruption aesthetic
```

**How to use glitch intentionally:** Generate a clean version of the target image, then use it as a reference and add glitch vocabulary to a second generation. The model will apply glitch aesthetics to a coherent base rather than producing fully incoherent output.

---

## The Unhinged Variations to Add to Every Hook Set

When delivering 5 hook variations, the 5th should always push past what feels safe for the brand. Label it `[CONCEPT — PRODUCTION TBD]` if the execution needs further development.

Prompts for finding the unhinged variation:
- What would this hook look like if it had no marketing intent at all? Write that, then add back one persuasion element.
- What's the most unexpected true thing about this product? Lead with that, no context.
- Who would this offend, and can you frame it for the people who would love it?
- What's the exact opposite of how this product is normally marketed? Try that.
- What happens if you remove the product entirely from the hook?
- What if the narrator clearly doesn't want to be making this content?

The best unhinged concepts are not always producible immediately. That's fine. The idea should be captured, labeled, and parked until the team is ready to execute. Many of the most memorable campaigns started as an idea someone said "we can't do that."


<!-- ═══════ FILE: script-writer/references/ai-video.md ═══════ -->

# AI Video Campaign Hooks
## Real-World Patterns from [AI video platform] & What Actually Lands

This file covers AI video content specifically. AI image hooks and AI video hooks are fundamentally different — the psychology, the structure, and the production modes are not interchangeable.

---

## Why AI Video Hooks Are Different

An AI image hook works on one trigger: a single impossible frame that makes the brain ask "how did they make that?"

AI video adds three things images can never do:

**1. Anticipation resolution** — Motion implies causality. The viewer doesn't just see the thing; they see it *becoming*. An image of an explosion is a fact. A video of an explosion building is a question. The brain physically cannot scroll past an unresolved question.

**2. Real-time transformation** — The before/after plays out in motion. The viewer cannot skip to the end without missing the mechanism. This is why unboxing, before/after, and product transformation formats consistently outperform static equivalents. You earn the scroll-through by making the payoff unreachable without watching.

**3. Proprioception / physical empathy** — FPV shots, free fall sequences, drift racing, crash zooms — the viewer's body responds to motion that implies *their own* movement. Images trigger visual cortex. Video triggers vestibular resonance. This is why platforms like [AI video platform] name their presets after kinetic scenarios (DRIFT RACING, FREE FALL, KUNG FU HIT) rather than visual aesthetics. The motion IS the product.

---

## The 5 AI Video Emotions (That Images Can't Touch)

When building a hook for AI video content, identify which of these is your primary trigger before writing a single word.

### 1. Vertigo
Induced by: FPV drone shots, free fall, orbital pull-back, crash zooms through surfaces, ground-level speed.
Hook structure: Place the camera where a camera cannot go, then move it in a direction the body recognizes as disorienting.
[AI video platform] presets: FREE FALL, ORBITAL PRESENCE, DRIFT RACING, RACE TRACK
When to use: Products with speed/power/freedom associations. Lifestyle. Sport. Tech.
Example hook: "Watch what happens when AI puts your product in freefall." [video begins mid-fall]

### 2. Real-Time Suspense
Induced by: Unboxing (tape ripping, reveal pending), countdown structures, building tension before a reveal, any "what happens next?" narrative arc.
Hook structure: Begin mid-sequence, after the setup but before the payoff. The viewer has entered a story already in progress.
[AI video platform] presets: Unboxing, Epic Fail to Hero Product, any build-up preset
When to use: Product launches, reveals, before/after campaigns, any content where there's a resolution to earn.
Example hook: First frame shows a box mid-opening, tape half-ripped — pause. "You already know what's about to happen."

### 3. Proprioception / Physical Resonance
Induced by: Impact shots, punch landings, drift turns, anything the viewer's body maps to their own kinesthetic memory.
Hook structure: The camera position simulates a physical experience the viewer has had. The AI-generated version is impossible to achieve in live footage — same experience, impossible fidelity.
[AI video platform] presets: KUNG FU HIT, DRIFT RACING, GOLF MAJOR, FINAL SERVE, BASEBALL GAME
When to use: Sports, fitness, any brand with physical energy.
Example hook: A [AI video platform]-generated punch impact in slow motion so detailed it triggers a visceral response before any copy appears.

### 4. Cognitive Dissonance / "Wait, Is That Real?"
Induced by: AI video character consistency across shots, UGC-mode iPhone aesthetic with impossible production quality underneath, photorealistic physics that shouldn't exist.
Hook structure: Lead with the UGC aesthetic (selfie framing, handheld camera, natural speech patterns), then reveal AI-level fidelity in something that couldn't have been filmed that way.
[AI video platform] presets: CANDID PAPARAZZI, 2000'S PAPARAZZI, OFFICE CCTV, UGC mode in Marketing Studio
When to use: Any campaign where the goal is skeptic conversion. The cognitive dissonance IS the proof of quality.
Example hook: Opens looking like a regular phone video of someone unboxing a product. Mid-shot, the camera smoothly transitions into a cinematic orbit around the product. No cut.

### 5. Scale Awe
Induced by: Impossible spatial scale — a product in outer space, a person inside a weather system, a stadium-scale environment for a single object.
Hook structure: Establish an impossible scale relationship in the first frame, no setup.
[AI video platform] presets: STORM GIANT, ORBITAL PRESENCE, ANDROID ASSEMBLE, 3D RENDER
When to use: Brand awareness, launch moments, any brand with "big" ambitions it wants to visualize.
Example hook: Product in extreme close-up, then a single continuous camera pull to reveal the product is sitting on a mountain summit. No cut. AI-generated camera path.

---

## [AI video platform]'s Hook Taxonomy (Their 4 Official Categories)

[AI video platform]'s Marketing Studio explicitly classifies all hooks into 4 types. Every hook you write for an AI video campaign should map to one of these.

### Type 1: Cold Open
No setup. No context. Drop directly into action or motion that is already in progress.
The brain is forced to catch up — it can't scroll because it doesn't yet understand what it's watching.
Examples:
- Video starts with the product already in motion, at speed, in an impossible environment
- Voice-over begins mid-sentence ("...and that's when I realized the whole thing was wrong")
- Scene opens on the resolution moment, then time-reverses or flashes back
Script note: Do not write setup before a cold open. If you find yourself writing "Today we're going to...", delete it. Start at the most interesting frame.

### Type 2: POV Setup
The camera becomes the viewer's eyes before any explicit content begins.
Positions the viewer inside the world before they've decided to stay. They're already there.
Examples:
- Looking down at a product in your own hands (first-person hold)
- Walking toward something that will be revealed — spatial immersion before the reveal
- The viewer is at a concert, in a car, at a race starting line
[AI video platform] prompt tip: Use directional spatial language — "camera moves forward through the crowd toward the stage" creates POV immersion; "a crowd shot at a concert" does not.

### Type 3: Pattern Interrupt
Something that breaks the scroll autopilot. Unexpected in one of three channels:
- **Visual**: A sudden color, scale shift, or impossible object in a real-world frame
- **Audio**: An abrupt silence after noise, or an unexpected sound before visuals establish context
- **Motion**: A camera move that defies physics (wall-penetration, speed ramp, 0g environment)
The scroll-stop mechanism: the brain detects the anomaly and stops to process it.
Script note: Write what is wrong with the first frame. The wrongness IS the hook. "A product sits on a kitchen counter — a perfectly normal kitchen counter, except the kitchen is at the bottom of the ocean."

### Type 4: Story Hook
Establish a character in a situation that demands resolution — in 2 seconds.
The viewer stays because they care about an outcome, not because they were impressed by production.
Examples:
- A person mid-action with stakes: reaching for something, running toward something, staring at something off-camera with a reaction that implies a threat
- A voice-over that names an emotional situation in the first sentence: "The day before I launched my company, this happened."
- A visual situation that implies consequence: a product on the edge of a table, a countdown clock in frame
Script note: The story hook is the highest-trust hook because it doesn't rely on spectacle. It works on audiences who are immune to wow-factor content. Use it for warm audiences or brand-affinity campaigns.

---

## [AI video platform]'s 9 Production Modes — When to Use Each

These modes have different hook structures because they serve different psychological functions.

| Mode | Emotion | Hook Entry Point | Best For |
|------|---------|-----------------|----------|
| **UGC** | Trust / Credibility | Cold open, selfie-style, direct eye contact | Conversion, skeptical audiences, DTC |
| **Unboxing** | Suspense + Reward | In medias res — tape mid-rip, box mid-open | Product launches, gifting, new releases |
| **Hyper Motion** | Awe + Desire | Cold open — CGI product in motion, frame 1 | Brand awareness, premium products, visual-first |
| **TV Spot** | Aspiration | Story hook — character in a situation | Brand films, awareness, emotional campaigns |
| **Tutorial** | Practical value | Direct address — "Here's exactly how to..." | Consideration stage, how-to, demo |
| **Product Review** | Trust + Conviction | POV setup — hands holding product | Comparison audiences, solution-aware |
| **UGC Virtual Try-On** | Identity shift | Mirror framing / try-on reveal | Fashion, accessories, beauty |
| **Pro Virtual Try-On** | Aspiration | Pattern interrupt — unexpected location for product | High-fashion, editorial, brand campaigns |
| **Wild Card** | Surprise + Delight | AI-determined — usually cold open or pattern interrupt | Viral content, experimentation, brand storytelling |

**The UGC vs. Hyper Motion distinction is critical:**
- **UGC builds credibility** — the viewer believes a real person used this product. Deliberately lo-fi.
- **Hyper Motion builds desire** — the viewer wants what they see. Deliberately premium.
Never use Hyper Motion for conversion campaigns with cold audiences. Never use UGC for awareness campaigns that need to demonstrate premium quality.

---

## The Viral Preset Strategy

[AI video platform]'s presets work because they follow a single formula: **you + impossible cinematic context = hook**.

The viewer asks "how did they film that?" before they realize it's AI. By the time they've processed it, they've already watched for 4+ seconds — past the scroll decision point.

The preset list reveals what "impossible cinematic context" looks like in practice:
- **Sport contexts**: BASEBALL GAME, GOLF MAJOR, FINAL SERVE, RACE WINNER — places a person or product inside a high-stakes athletic moment with broadcast-quality camera work
- **Kinetic physics**: DRIFT RACING, FREE FALL, KUNG FU HIT — motion that no physical camera rig can safely capture
- **Scale impossible**: STORM GIANT, ORBITAL PRESENCE, ANDROID ASSEMBLE — impossible spatial relationships
- **Cultural/aesthetic**: 2000'S PAPARAZZI, RED CARPET, NEON CITY — places the subject in a high-production cultural moment
- **Fantasy/surreal**: DRAGON FANTASY, ZOMBIE DANCE, EXIT THE DREAM — removes reality constraints entirely

**Prompt principle for presets:** Don't prompt the preset. Prompt what the subject is doing *inside* the preset scenario. "A woman holds a product while cameras flash around her at a red carpet" — not "red carpet preset with product."

---

## Case Studies: What Actually Worked

### Kalshi NBA Finals Commercial
- Budget: $2,000 (vs. typical $200k+ for comparable production)
- Time: 2 days
- Result: 3M+ views on X
- Why it worked: Surrealistic visual logic that would cost millions to film practically. The impossibility wasn't hidden — it was the point. Hook = "this shouldn't be possible to make for $2k"

### Popeyes AI Diss Track
- Tools: Veo3 + Suno
- Time: 3 days
- Why it worked: Culture-driven, competitive, used AI for speed of wit — the hook was the timeliness, not the production. AI enabled a response within the news cycle window.
- Lesson: Sometimes the hook is the *speed* of AI production, not the quality

### The $350K AI Commercial ([AI video platform]'s own)
- Hook in the title: "$350,000 AI Commercial — Full Prompts"
- Structure: Price anchor (what this would have cost) + impossibility claim (one tool) + proof (full prompts shown)
- Why it worked: The title IS the hook. Every creative professional clicked because $350K is real pain for them.
- Lesson: Name the price comparison in the hook. Not "great quality" but "this quality used to cost $350,000"

---

## TikTok Algorithm Reality (2026)

These are the numbers that should shape every decision about hook length and completion:

- Algorithm makes first distribution decision at **1.5 seconds** — not 3 seconds as commonly cited
- **70%+ completion rate** required for viral distribution in 2026 (up from 50% in 2024)
- Videos hitting **92%+ completion** receive 3x standard algorithmic distribution
- **Best performing hook type by views**: Product/Outcome Showcase — showing the finished result in the first 2 seconds, averaging 6,037 views vs. ~3,000 for weaker hook types
- Tutorials average 47 seconds with 70–80% completion — the length-completion relationship is more favorable for tutorials than assumed

**What this means for script structure:**
- 1.5 seconds is the hard deadline for your hook to register, not 3 seconds
- If your hook requires any explanation before it lands, it's not a hook — it's a paragraph
- The completion rate is your real metric, not views. A 30-second video at 90% completion outperforms a 60-second video at 40% completion for distribution
- The best completion tactic: the payoff must be impossible to reach by skipping. Motion reveals, story resolutions, and transformations that play out over time all earn completion in ways that list-style content cannot

---

## AI Video Prompting for Hooks (The Motion Layer)

Standard prompt logic produces bland output. The upgrade: prompt the *motion and emotion flow*, not just the visual.

**Basic (produces generic results):**
> "A product on a table with nice lighting"

**Motion-aware (triggers [AI video platform]'s cinematic engine):**
> "Camera starts tight on the product label, slowly pushes in as morning light catches the bottle edge, then pulls back to reveal the kitchen — warmth, unhurried, a Sunday feeling"

The difference: the second prompt tells the model what the camera does and what emotional texture the motion should carry. "Sunday feeling" is understood by the cinematic logic layer and influences pacing, lighting decisions, and camera speed.

**Key motion vocabulary for prompts:**
- Directional continuation: "camera continues moving left as..." ([AI video platform] uses this for POV immersion)
- Physics qualifiers: "physics-aware," "natural deceleration," "cloth simulation"
- Lighting in motion: "as the camera pushes in, light catches the edge of..."
- Emotional tone as motion direction: "building tension," "unhurried," "snapping into focus"
- Character action as camera cue: "she looks up to reveal" (implies camera follows the reveal)

**The distinction that matters most:** Prompting what a scene looks like vs. prompting what a scene *feels like in motion*. [AI video platform]'s system translates emotional intent into shot plans — so "this should feel premium and inevitable, like the product was always supposed to be there" produces a different camera logic than "cinematic shot of a product."

---

## The Reference Ad Strategy

One of [AI video platform]'s highest-converting features: upload a viral ad, attach your product, let the system analyze the structure and rewrite it for your brand.

The scriptwriting equivalent is the same principle:

1. Find a video in your category that's performing well (high comments, shares, saves — not just views)
2. Reverse-engineer its structure: What is the hook type? What emotion does it lead with? What's the transformation or payoff? When does the CTA appear?
3. Write a new hook that targets the same emotion with your specific product/output as the hero
4. Keep the structural skeleton, replace all the content

This produces better results than writing from scratch because the structure has already been market-tested. You're not guessing what works — you're adapting what you already know works.

**Script questions for reverse-engineering a reference video:**
- What is the first frame? (static / motion / text / face?)
- What emotion is triggered in the first 1.5 seconds?
- When does the product/brand appear?
- What is the transformation or payoff?
- What does the CTA ask for and when does it appear?
- What is the completion bait — what makes this impossible to exit before it ends?


<!-- ═══════ FILE: script-writer/references/prompt-iteration.md ═══════ -->

# Prompt Iteration — Diagnosing and Fixing AI Generations

AI content production is iterative. The first generation is a draft. This file gives you a systematic framework for diagnosing what went wrong and fixing it with the minimum number of regenerations.

The wrong approach: regenerate with a slightly different random seed and hope. The right approach: identify the specific failure category, apply the specific fix, regenerate once.

---

## The 5 Diagnostic Categories

Every generation failure falls into one of these five categories. Identify the category before changing anything.

---

### Category 1: Subject Failures

**Signs:** Wrong anatomy, extra limbs, malformed hands, face distortion, wrong number of people, subject doesn't match description.

| Problem | Specific Fix |
|---|---|
| Malformed hands (most common) | Option A: `anatomically correct hands, five fingers, natural relaxed position` // Option B: remove hands from the scene entirely: `hands in pockets`, `arms at sides, hands not visible`, `shot from waist up, hands out of frame` |
| Wrong number of people | Be explicit: `exactly one person in frame, single subject, no other people, no crowd` |
| Face distortion | Add: `realistic facial proportions, natural features, portrait photography quality, no distortion` |
| Wrong age | Use specific numbers: `27-year-old woman`, not `young woman` |
| Wrong ethnicity/appearance | Describe specific physical features rather than category labels |
| Subject doesn't match description | Break complex subjects into explicit physical components. Don't describe through adjectives — describe through physical reality. |

**The hands rule:** Hands are the most common failure point in AI image generation. When hands are not essential to the visual, remove them from the scene entirely. When they are essential, use image-to-video anchoring with a reference image that shows the correct hand position, or use explicit negative prompts: `extra fingers, malformed hands, wrong hand anatomy, distorted fingers`.

---

### Category 2: Lighting Failures

**Signs:** Flat, sourceless light; wrong emotional mood; unnatural shadows; blown-out exposure; wrong color temperature.

| Problem | Specific Fix |
|---|---|
| Flat, sourceless light | Name the light source explicitly: `single key light from upper left at 45 degrees, Rembrandt setup, shadow on right cheek` |
| Wrong color temperature | Specify Kelvin: `warm amber 3200K` or `cool daylight 5600K` — not "warm" or "cool" as adjectives |
| Blown-out exposure | `Correctly exposed, visible shadow detail, not overexposed, balanced lighting ratio` |
| Underexposed or too dark | `Well-lit, fill light balancing shadows, shadow detail retained, bright subject` |
| Generic "cinematic" dark | Replace "cinematic" with specific lighting vocabulary from `visual-language.md`. The word "cinematic" alone defaults models to: slightly dark, atmospheric haze, vague lens flare. |
| Wrong mood from lighting | Every lighting setup has a name and an emotional meaning. Use the name from `visual-language.md` rather than an emotion word. `Rembrandt` is more precise than `dramatic`. |

---

### Category 3: Composition Failures

**Signs:** Default center framing, background intrudes, wrong crop, subject too small, unwanted elements in frame.

| Problem | Specific Fix |
|---|---|
| Default center composition | Specify: `rule of thirds, subject positioned at right vertical third, space to the left` |
| Background distracting | `Shallow depth of field, f/1.4 aperture, background blurred, subject isolated, bokeh` |
| Wrong frame size | Name the shot type explicitly: `tight close-up, head and shoulders only` / `medium shot, waist up` / `wide shot, full environment visible` |
| Unwanted elements | Negative prompt the element AND specify what should occupy that space positively |
| Flat, no depth | `Three planes of depth, foreground element slightly blurred, subject sharp in midground, background bokeh` |
| Subject too small | `Subject dominant in frame, fills approximately 60-70% of frame height` |

---

### Category 4: Style and Mood Failures

**Signs:** Generic output with no character, wrong era/aesthetic, too polished when it should be raw, wrong emotional register.

| Problem | Specific Fix |
|---|---|
| Generic beautiful result, no character | Remove all adjective-driven words. Replace with reference-style specifics: `shot on ARRI Alexa, 2026 high-fashion editorial, teal and orange grade` |
| Wrong era or aesthetic | Be explicit: `early 2000s color palette, slightly faded highlights, film grain, late 90s web aesthetic` |
| Too polished when raw is needed | `Candid, unposed, documentary feel, natural available light, slightly imperfect framing, authentic` |
| Too raw when polished is needed | `Studio production quality, professional lighting setup, editorial standard, immaculate` |
| Wrong tone | Describe the emotional response you want the viewer to have, not the product's qualities: `viewer should feel calm and confident` vs. `professional quality` |

---

### Category 5: Video Motion Failures

**Signs:** Inconsistent character between frames (drift), wrong camera movement, flat or frozen motion, jitter, object teleportation, wrong pacing.

| Problem | Specific Fix |
|---|---|
| **Character drift** (most common video failure) | Switch from text-to-video to **image-to-video**. Anchor with a reference image of the character. The reference image is the identity lock. Without it, the model generates slightly different facial features each frame. |
| Camera move not executing | Use explicit vocabulary with duration: `slow dolly in over 3 seconds, subject locked in center frame` — not "zoom in" |
| Inconsistent style across shots | Create a master style reference image (generate it once, use it as a style anchor in every subsequent generation) |
| Jitter or temporal incoherence | Add negative prompts: `jitter, temporal incoherence, flickering, unstable motion, warping` |
| Flat/frozen motion when movement was intended | State action explicitly: `subject slowly raises product toward camera, continuous fluid motion, not static` |
| Physics inconsistency | `Physically realistic motion, gravity-consistent, natural deceleration, weight-appropriate movement` |
| Wrong pacing | Specify duration and relative speed: `4-second shot, slow movement, approximately 20% of maximum speed, deliberate and unhurried` |
| Object teleportation between frames | Anchor with end-frame chaining: the last frame of Scene 1 becomes the first frame of Scene 2. Maintains spatial and temporal coherence across scenes. |

---

## Model-Specific Failure Modes

### Nano Banana Pro (ImagineArt)

**Returns the original image without edit:**
Caused by: vague edit instructions OR the safety system flagging the edit.
Fix: Use specific editing verbs. `"Replace the background with a white marble surface"` works. `"Make it look better"` does not. For complex edits, use structured JSON prompt format. Break multi-element edits into sequential single-step generations.

**Style inconsistency across a series:**
Cause: No native style lock.
Fix: Generate a master style image first. Use it as a reference image (style anchor) in every subsequent generation. Maintain identical style vocabulary across all prompts in the series.

**Prompt drift on complex instructions:**
Fix: Break multi-element prompts into single-step sequences. One prompt = one change.

---

### Seedance 2.0 (Video)

**Camera movement not executing:**
Fix: Add structured camera syntax — `Camera: slow dolly in, 3 seconds, subject locked center frame`. Seedance responds better to explicit camera instructions as a labeled section rather than embedded in the scene description.

**Motion blur artifacts:**
Fix: Add to negative prompt: `motion blur, smear, ghosting`. Reduce motion intensity in the parameters panel.

**Character features changing mid-clip:**
Fix: Always use image-to-video mode for character work, not text-to-video. The reference image is the identity anchor.

**Physics inconsistencies:**
Fix: `physically realistic motion, natural gravity, weight-appropriate movement, no floating`

---

### Kling 2.6 / 3.0 (Video)

**Baseline negative prompt (use on every Kling generation):**
`blur, distort, low quality, warping fingers, frozen lips, jittery eyes`

**Character drift across multiple clips:**
Fix: Use **Kling Elements** feature for identity locking. Provides a character anchor that persists across multiple generations — essential for any campaign with a recurring human or character.

**Lip sync issues:**
Fix: Keep dialogue lines under 5 seconds per scene. Use `avoid digital overlays` syntax (not `no watermarks`). Kling has different negative prompt syntax than Midjourney/SD.

**Inconsistent motion between scenes:**
Fix: End-frame chaining. Export the last frame of each clip and use it as the first-frame reference for the next clip.

---

## Negative Prompt Strategy

### The 5-Term Cap

Beyond 5–7 negative terms, diffusion models can enter inverse amplification — the excluded elements become more prominent. Keep negative prompts focused and specific. Less is more.

**Wrong:** `bad quality, ugly, deformed, low resolution, blurry, pixelated, oversaturated, undersaturated, distorted, warped, extra limbs, malformed, unnatural, unrealistic, fake, bad lighting, wrong colors, off-brand`
(19 terms — produces incoherent output)

**Right:** `malformed hands, motion blur, temporal incoherence, overexposed highlights, background clutter`
(5 terms — precise and effective)

### Negative Prompt Vocabulary by Failure Type

**Anatomy:** `extra limbs, malformed hands, extra fingers, distorted face, asymmetrical features, deformed`

**Technical artifacts (images):** `watermark, signature, text overlay, JPEG compression, noise, grainy at low resolution`

**Technical artifacts (video):** `jitter, temporal incoherence, warping, flickering, motion smear, character drift, teleporting objects`

**Composition:** `cropped head, off-center when center is wanted, cluttered background, distracting elements in background`

**Lighting:** `overexposed highlights, flat sourceless light, underexposed, harsh unnatural shadows, wrong color cast`

**Style:** `generic, stock photo look, corporate, overly processed, plastic skin, artificial`

### Model-Specific Negative Syntax

| Model | Syntax |
|---|---|
| Midjourney | `--no [term], [term]` at end of prompt |
| Stable Diffusion / ImagineArt | Dedicated negative prompt field |
| Kling | `avoid [specific description]` phrasing |
| Seedance | Negative prompt section, standard terms work |
| Veo | Include in prompt as `excluding: [terms]` |

---

## Reference Image Strategy

### When to Use References

**Always use references for:**
- Character consistency across scenes (image-to-video anchoring)
- Matching an existing campaign's visual style
- Ensuring a product looks exactly like the actual product
- Matching a specific color grade when words alone aren't reliable

**Consider references for:**
- Composition references (showing the camera angle you want)
- Lighting references (showing the specific light quality you want)
- Style references (showing the aesthetic direction)

### How Many References

| Count | Effect |
|---|---|
| 1 reference | Maximum influence on that single element |
| 2–3 references | Effective with clearly distinct roles assigned |
| 4+ | Influence of each dilutes — only use if each covers a clearly separate element |

**When using multiple references, name each one's role:**
- Reference 1: character/product identity
- Reference 2: lighting and color grade
- Reference 3: composition/angle

### What Makes a Good Reference

- **Resolution:** 1024px minimum on shortest side. Low-res references produce low-res outputs.
- **Aspect ratio:** Match the intended output aspect ratio to prevent warping artifacts.
- **One clear subject:** Don't use a complex scene to reference a single concept. One thing per reference.
- **Internal consistency:** All references should work together. Conflicting references produce averaged, incoherent results.
- **For video references:** 2–14 second clips for Seedance. The clip should contain the motion pattern you want, not just the visual look.

**Reference strength:** 70%+ for consistency-critical work. Below 50%, the reference serves as loose inspiration only.

---

## Iteration Vocabulary — Words That Shift Output Predictably

When the output is close but not quite right, these phrases make targeted adjustments without full regeneration.

### Lighting Shifts
```
"More dramatic" → increases shadow depth and key light intensity
"Softer, more diffused" → reduces shadow hardness, wraps light around subject
"Warmer, golden, amber" → shifts color temperature warm
"Cooler, blue-tinted, clinical" → shifts color temperature cool
"More backlight, add rim light" → adds edge separation from background
"Reduce the fill light" → increases contrast, darkens shadows
```

### Mood Shifts
```
"More intimate" → tightens composition, softens focus, warms color
"More epic, grand" → widens shot, deepens color, increases contrast
"More melancholic" → cools color, slight desaturation, drops brightness
"More tense" → increases contrast, tightens crop, reduces fill
"More aspirational" → lifts highlights, warms midtones, increases saturation slightly
"More minimal, quieter" → removes visual elements, increases negative space
```

### Motion Shifts (Video)
```
"Slower, more deliberate" → reduces movement speed
"More fluid, smoother" → removes jitter, adds stabilization feel
"More handheld, more natural" → introduces slight organic movement
"Faster, more urgent" → increases pace
"More weight, heavier movement" → adds physics-appropriate gravity to motion
```

### Composition Shifts
```
"Tighter, closer" → changes toward tight framing
"More environmental, pull back" → reveals more background context
"More negative space" → reduces subject size, adds breathing room
"Subject more dominant" → increases subject-to-frame ratio
"Shift to rule of thirds" → moves subject from center to intersection
```

### The Most Important Principle

**Replace adjectives with technical vocabulary.** Models are trained on annotated photography data — they respond to photography vocabulary more reliably than emotional descriptors.

`f/1.4, 85mm, Rembrandt lighting setup, ARRI Alexa` reliably produces a specific look.

`Beautiful cinematic portrait` does not.

Every time you find yourself using an adjective to describe visual quality, stop. Ask: what is the technical name for the thing I want? Use that name instead.


<!-- ═══════ FILE: script-writer/references/imagine-art-production.md ═══════ -->

# imagine.art Production Guide — AI Content Workflows

This file covers how to generate the actual content using imagine.art's platform. Every script and hook produced by this skill should be paired with generation prompts from this guide. The goal is finished, platform-ready content — not instructions for a human film crew.

---

## The Three Production Paths

Choose the right path before writing a single prompt.

| Path | Tool | Best For | Time to Finished Content |
|---|---|---|---|
| **Fast** | ImagineShorts | Single short-form video, social promos, quick campaign pieces | 3–5 minutes |
| **Standard** | Image Studio + Video Studio separately | Full control over individual visuals or clips | 10–30 minutes per scene |
| **Campaign** | Workflows 2.0 | Multi-scene campaigns, batch variations, consistent character series | Setup once, reuse indefinitely |

---

## Path 1: ImagineShorts — Fastest Route to Finished Social Content

**URL:** imagine.art/shorts

The complete short-form pipeline in one tool. Input a concept or script; output a finished video with AI-generated visuals, narration, captions, and music — ready for TikTok, Reels, or Shorts.

**What it handles:**
- Script generation with alternate variations and custom lengths
- Visual generation (ImagineArt models OR Pexels stock fallback)
- AI narrator voice: 100+ voices, 30+ languages and accents
- Captions: 10 styles, 3 position options, auto-synced to narration
- Background music: 8 curated options
- Final output in 9:16 vertical, no watermarks

**When to use:** A single social video, a quick promo clip, a product showcase post. Anything that needs to exist within the same working session it was conceived.

**ImagineShorts input format:**

```
CONCEPT: [1–3 sentence brief — what is this video about and who is it for?]
SCRIPT: [Paste the hook + body + CTA from the script output]
TONE: [direct / conversational / aspirational / educational]
VOICE: [narrator style — confident and direct / warm and helpful / etc.]
CAPTIONS: [style preference — bold white / subtitle / kinetic]
MUSIC: [mood — upbeat / minimal / cinematic / none]
PLATFORM: [TikTok / Reels / Shorts]
```

---

## Path 2: Image Studio + Video Studio — Scene-by-Scene Control

For campaigns where each frame matters and the default ImagineShorts visuals aren't specific enough.

### The Canonical Prompt Structure

imagine.art's recommended prompt order for both images and video:

```
[Subject] [Appearance] [Action] [Environment: time/lighting/elements] [Camera: lens/movement/direction] [Mood] [Style] [Tone] [Audio] [Negative prompts]
```

Example — product shot:
```
A sleek skincare serum bottle, frosted glass with gold cap, sitting undisturbed, white marble surface with morning light streaming from the left casting a soft shadow, 85mm lens tight close-up, no camera movement, clean and premium, commercial photography style, photorealistic, — blurry, distorted, AI artifacts
```

Example — lifestyle scene:
```
A young woman, natural makeup, holding a product toward camera, in a bright modern home studio, sunlight through white curtains, camera slowly pushing in, confident and relaxed mood, UGC-style handheld aesthetic, authentic, warm — staged, fake, dark, cluttered
```

### JSON Prompting (Recommended for Campaigns)

For any content where consistency across scenes matters, use JSON format. This eliminates visual artifacts, prevents random scene changes, and produces reusable style templates for campaign variations.

```json
{
  "subject": "skincare serum bottle, frosted glass, gold cap",
  "appearance": "product in pristine condition, no marks",
  "action": "sitting still on surface, slight condensation forming",
  "environment": {
    "time_of_day": "early morning",
    "lighting": "soft diffused natural light from left window",
    "elements": ["white marble surface", "out-of-focus green plant in background"]
  },
  "camera": {
    "lens": "85mm",
    "aperture": "f/1.8",
    "movement": "very slow push in",
    "direction": "toward product"
  },
  "mood": "premium, serene, trustworthy",
  "style": "commercial product photography",
  "tone": "clean, minimal, editorial",
  "audio_events": [
    {"time": 0.0, "type": "ambient", "content": "soft morning room tone, barely audible"}
  ],
  "resolution": "1080p",
  "aspect_ratio": "9:16",
  "negative_prompts": "AI artifacts, distortion, harsh shadows, dark background, clutter"
}
```

**Use JSON prompting when:** Running a multi-video campaign, generating scene variations from the same product/character, using Workflows 2.0, or any situation where you need scenes to feel like they belong to the same visual world.

---

## Model Selection by Content Type

| Content Type | Best Image Model | Best Video Model | Notes |
|---|---|---|---|
| Hero product shot | ImagineArt 2.0 | Seedance 2.0 or Hailuo 2.3 | Flagship quality for campaign heroes |
| Product demo video | Nano Banana Pro | Kling 3.0 or Veo 3.1 | Nano Banana locks product identity across references |
| Lifestyle / campaign visual | Seedream v4.5 | Kling 2.6 or Runway Gen-4.5 | Up to 14 reference images for consistency |
| Social ad (9:16 vertical) | ImagineArt 1.5 Pro | Sora 2 or Pixverse V5 | Native 4K, strong text rendering |
| UGC / talking head | ImagineArt 2.0 | HeyGen Avatar + Lipsync Studio | Most authentic looking synthetic UGC |
| Animated / stylized | Dreamina 3.1 or Midjourney V7 | Pixverse V5 or WAN 2.5 | Expressive fluid motion |
| Ad creative with text overlay | ChatGPT Image 2 or Ideogram v3 | Veo 3.1 (native audio + text) | ChatGPT Image 2 = 99%+ text accuracy |
| Rapid batch drafts | Nano Banana 2 or Seedream v5 Lite | Seedance Pro Fast | Speed and volume over max quality |
| Cinematic atmospheric | Midjourney V7 | Runway Aleph or Veo 4 | Rich textures, wide style range |

---

## Path 3: Workflows 2.0 — Campaign-Level Automation

**URL:** imagine.art/flow

Node-based canvas. Build it once; run it for every campaign variation.

### The Core Concept: Workflow Variables

Define a subject (product image, character reference, brand prompt) as a Variable once. Every node in the workflow pulls from that source. Change the Variable → the entire campaign regenerates with the new subject. This is the essential tool for brand consistency across a campaign series.

### Essential Nodes for Content Production

**Storyboard Node** — Generates a multi-frame grid (2×2, 2×3, 3×3) maintaining style and narrative consistency across scenes. Use this as the first node in any multi-scene campaign to establish visual coherence before committing to individual generation.

**Multiple Camera Angles Node** — Takes a single subject and generates close-up, wide, top-down, and side views simultaneously. Essential for product campaigns where you need multiple shooting angles from one reference image.

**Relight AI Node** — Adjust lighting position, color, and intensity post-generation without full regeneration. Use to create morning/evening/dramatic variations of the same product shot.

**Image Iterator** — Batch-processes multiple images through an identical pipeline. Feed in 10 product images; every node runs on all 10 in parallel.

**Text Iterator** — Runs multiple prompt variations through the same workflow simultaneously. Use for A/B testing different copy or visual angles at scale.

**Generate Music Node (ElevenLabs)** — AI music from a text prompt. Set tempo, instruments, genre. Feeds directly into the assembled video.

**Sound Effects Node (ElevenLabs)** — Custom SFX from prompts: ambient, action effects, UI audio cues.

### Basic Campaign Workflow Template

```
[Product Image Variable]
        ↓
[Storyboard Node] → 6 scene frames, consistent style
        ↓
[ImagineArt 2.0 Image Generation × 6] → full-resolution scene images
        ↓
[Seedance 2.0 / Kling 3.0 Video Generation × 6] → 5–8s clip per scene
        ↓
[Generate Music Node] → background track matching campaign tone
        ↓
[ImagineShorts assembly] → captions, narration, final edit
        ↓
[Export 9:16 MP4] → platform-ready
```

**App Builder:** Once the workflow is built, convert it to a clean no-code interface so any team member can run campaigns without touching the node structure. Define the inputs they need to fill (product image, campaign brief, tone) and they get finished content out.

---

## The AI Product Video Maker

**URL:** imagine.art/features/ai-product-video-generator

Dedicated product demo and showcase tool. Fastest path specifically for product-focused promos.

**Input:**
- Product image upload
- Scene description (where the product is, what's happening around it)
- Style selection

**What it generates:**
- Multiple video variations
- Predefined cinematic styles built for commercial content
- Dynamic camera motions (dolly, orbit, crash zoom)
- Lighting effects
- Background sound integration
- 16:9 or 9:16 output

**Best for:** E-commerce brand promos, product launch clips, hero video for ads. Faster than building a full workflow for a single product showcase.

---

## Consistent Character Video

**URL:** imagine.art/features/consistent-character-video

Maintains character, product, and scene consistency across every frame of a multi-shot video.

**Key capabilities:**
- Multi-character videos (add/remove characters while keeping identity stable)
- Character editing mid-campaign: change clothes, accessories, hairstyle, skin tone — without losing identity lock
- Works on product objects (not just people) — use for consistent product identity across varied backgrounds
- Environmental variation while locking subject identity

**Workflow integration:** Use the character image as a Workflow Variable; the Consistent Character Video feature ensures identity lock is maintained as the workflow generates scene variations.

---

## UGC-Style Content — The Authentic AI Video

UGC content (first-person, lo-fi aesthetic, direct-to-camera) consistently outperforms polished branded content for cold audiences. imagine.art can generate this format.

**Production method:**

1. **HeyGen Avatar** (`imagine.art/apps/heygen-avatar`) — Professional AI avatar. Select voice, appearance, and script. Generates a realistic talking head that holds up to close inspection.

2. **Lipsync Studio** — Sync any audio track to a video face. Use if you have a voiceover and want to add a visual speaker.

3. **ImagineArt 2.0 + UGC prompt style:**
```
[Character description], holding product toward camera, handheld phone aesthetic, slightly grainy, natural indoor light, direct eye contact, authentic casual clothing, imperfect framing — overproduced, studio lighting, professional camera, staged
```

**The UGC layering technique:**
- Generate the UGC-style video clip (lo-fi aesthetic)
- Layer in a product shot cut (0.5s of the product in clean light) between the talking head sections
- The contrast between lo-fi person and clean product shot creates cognitive dissonance that drives completion (viewers want to reconcile the aesthetic gap)

---

## The Script-to-Production Format

Every script produced by this skill should include generation prompts for each scene. Use this format:

```
SCENE [N] — [0s–5s]

[SPOKEN] "..."
[TEXT OVERLAY] "..."

GENERATION:
  Path: [ImagineShorts / Image+Video / Workflows 2.0 / Product Video Maker]
  Model: [specific model from the table above]
  Prompt: [full prompt using canonical structure or JSON]
  Aspect Ratio: [9:16 / 16:9 / 1:1]
  Duration: [seconds for video; N/A for image]
  Notes: [any special instructions — reference image needed, character lock, etc.]
```

---

## Quick-Reference: Which Tool for What Situation

| Situation | Tool to Use |
|---|---|
| "I need a 30-second TikTok promo by end of day" | ImagineShorts |
| "I need 20 product images for a campaign" | Workflows 2.0 with Image Iterator + Seedream v4.5 |
| "I need a product demo video with cinematic movement" | AI Product Video Maker |
| "I need 5 videos of the same character in different settings" | Consistent Character Video + Workflows 2.0 |
| "I need a UGC-style review video" | HeyGen Avatar + Lipsync Studio |
| "I need a product image with text overlay for an ad" | ChatGPT Image 2 or Ideogram v3 |
| "I need multiple campaign variations from one product shot" | Workflows 2.0: Multiple Camera Angles + Relight AI |
| "I need a cinematic brand film" | Workflows 2.0 Storyboard → Kling 3.0 or Runway Gen-4.5 |
| "I need to A/B test 5 different hook visuals" | Workflows 2.0 with Text Iterator |


<!-- ═══════ FILE: script-writer/references/imagine-art-context.md ═══════ -->

# imagine.art — Platform Context & Campaign Strategy

This file contains everything the skill needs to know about imagine.art as a platform, brand, and product — so every hook, script, and campaign it produces is positioned correctly.

---

## What imagine.art Is

imagine.art is an AI creative platform for generating high-quality images and videos from text prompts and reference inputs. It serves creators, brands, marketers, agencies, and companies who need visual content — fast, at scale, and at a quality level that competes with professional production.

The platform sits at the intersection of creative tools and marketing infrastructure. Users range from solo content creators to enterprise marketing teams generating hundreds of campaign assets per week.

---

## Who You're Writing For (The Audiences)

Always identify which audience segment is being addressed before writing. Each has a different awareness level, pain point, and hook that lands.

### 1. Content Creators (Individual)
- **Pain:** Creating visual content consistently is expensive and slow. Either they pay for assets or spend hours making them.
- **Dream outcome:** Unlimited, high-quality visuals that match their creative vision without a production budget.
- **Hook entry point:** Speed + quality + creative freedom. "I generated 30 variations in 10 minutes."
- **What moves them:** Seeing the creative range — wild, unexpected, beautiful outputs they couldn't have made otherwise.
- **Platform:** TikTok, Instagram, YouTube Shorts.

### 2. Social Media Managers / Marketing Teams
- **Pain:** Content demands outpace production capacity. Brief-to-asset timelines are brutal. Stock photos look like stock photos.
- **Dream outcome:** On-brand, original visuals for every post, every campaign, without a 3-day turnaround.
- **Hook entry point:** Volume + brand consistency. "We went from 2 campaign visuals a week to 40."
- **What moves them:** Workflow proof — show the URL-to-campaign-ready asset pipeline.
- **Platform:** LinkedIn, Instagram, industry content.

### 3. E-commerce Brand Owners
- **Pain:** Product photography is a $1,500–$5,000 shoot per collection. Seasonal refreshes cost the same. Lifestyle shots cost more.
- **Dream outcome:** Photorealistic product images for every SKU, every background variation, every platform format — without booking a photographer.
- **Hook entry point:** Cost destruction + quality parity. "This product shot cost $0."
- **What moves them:** The quality comparison — AI-generated vs. traditional photography, side by side.
- **Platform:** Instagram, Facebook ads, TikTok.

### 4. Agencies & Creative Studios
- **Pain:** Client briefs that require 50 visual variations by Thursday. Revision cycles that eat margins. New client categories every month.
- **Dream outcome:** Scale creative output without scaling headcount. Pitch AI-augmented production as a service differentiator.
- **Hook entry point:** Iteration speed + client ROI. "We now deliver 5x the creative variations in the same timeline."
- **What moves them:** Business case — cost per asset, time saved per campaign, client retention impact.
- **Platform:** LinkedIn, industry press, direct outreach content.

### 5. Filmmakers & Directors (Cinema Studio users)
- **Pain:** Pre-visualisation and concept development eat budget before a frame is shot. VFX costs are prohibitive for indie productions.
- **Dream outcome:** Visualise any idea before committing production resources. Generate reference shots, previs, and impossible setups.
- **Hook entry point:** Creative possibility. "I pre-visualised the entire opening sequence before we touched a camera."
- **What moves them:** Cinematic quality + camera control precision.
- **Platform:** YouTube, Vimeo, filmmaker communities.

---

## imagine.art's Core Positioning

When writing for imagine.art, every script implicitly positions around these truths — never state them mechanically, but ensure they're felt:

**Quality is the non-negotiable.** imagine.art's outputs are photorealistic, brand-consistent, and production-grade. The hook should demonstrate quality, never just claim it.

**Speed is the unlocking mechanism.** The platform doesn't just make content cheaper — it makes things possible that weren't before because of time constraints. "30 variations in 10 minutes" is not about cost; it's about creative decisions being made at machine speed.

**Creative freedom is the emotional core.** The deepest value isn't productivity — it's that the gap between having a vision and executing it has closed. A creator who couldn't afford to visualise a certain aesthetic now can. That's identity-shifting.

**Scale is the business case.** For teams and agencies, the value is measured in campaigns per week, assets per month, client retention, and new service lines.

---

## What to Avoid in imagine.art Scripts

**Never name competitors positively.** Do not cite competing AI platforms as examples of good work, hook strategies, or campaign benchmarks. If referencing what "other platforms" do, frame it as an industry pattern, not as praise for a specific competitor.

**Never make claims you can't back.** imagine.art's credibility is its output quality. Never write "the best," "the only," or "unlike anything else" without a specific, demonstrable reason.

**Avoid AI hype language.** Words like "revolutionary," "game-changing," "next-level," and "cutting-edge" are invisible in 2026. Replace every one with a specific, measurable claim.
- ❌ "Revolutionary AI image quality"
- ✓ "Photorealistic product images generated in 30 seconds"

**Don't lead with the tool.** "imagine.art is an AI platform that..." is never a hook. Lead with the output, the result, or the viewer's pain. The platform name enters mid-script, after attention is secured.

**Avoid the passive "AI made this."** Table stakes. It needs a number, a comparison, or an identity trigger attached: "AI made this — in 8 seconds, from a text prompt, for $0."

---

## imagine.art Content Pillars

When building a campaign arc or content calendar, structure content across these pillars. Each pillar serves a different audience stage and platform role.

### Pillar 1: The Output Showcase (Awareness)
Pure demonstration of what the platform can generate. No voiceover required. Let the visual do the work.
- Format: 3–8 second loops, montages, before/after reveals
- Hook type: Cold open — the output IS the first frame
- Goal: Stop the scroll, create the "how?" question
- Platform: All platforms, prioritise TikTok and Reels for discovery

### Pillar 2: The Process Reveal (Consideration)
Show the workflow — prompt in, output out. Demystify the magic and make it feel achievable.
- Format: 30–60 second walkthrough, screen recording + talking head
- Hook type: POV setup or story hook — "here's exactly what I typed"
- Goal: Convert "I wonder if that works" into "I want to try this"
- Platform: YouTube Shorts, TikTok, Instagram Reels

### Pillar 3: The Use Case Proof (Consideration → Conversion)
Real person, real brief, real outcome. One specific use case per video.
- Format: 45–90 second tutorial or testimonial
- Hook type: Identity hook or cost destruction
- Goal: Make the viewer recognise their own workflow in the content
- Platform: Instagram, LinkedIn, YouTube

### Pillar 4: The Comparison / Contrast (Conversion)
Side-by-side or before/after. AI-generated vs. traditional. Speed or cost delta made explicit.
- Format: Split screen, side-by-side, or numerical before/after
- Hook type: Contrast hook — show the delta immediately
- Goal: Remove the last objection before trial
- Platform: Paid social, YouTube pre-roll, retargeting

### Pillar 5: The Community Showcase (Retention + Social Proof)
Content made by users. Real outputs from real creators — reposted or curated.
- Format: UGC-style, community highlight
- Hook type: Social proof hook — "look what [user type] made with this"
- Goal: Build aspiration and show range; signal that real people use this
- Platform: All platforms

### Pillar 6: The Authority Angle (Brand Building)
POV content, creative philosophy, trend commentary. Positions imagine.art as a creative authority, not just a tool.
- Format: 60–90 second editorial content, talking head
- Hook type: Contrarian hook — "everyone's using AI wrong for X"
- Goal: Build brand trust and creator community
- Platform: LinkedIn, YouTube, X/Twitter

---

## Campaign-Specific Angles for imagine.art

When given a specific campaign brief, map it to one of these angles before writing:

**"Better than you think"** — For skeptical audiences who assume AI images look fake. Lead with the quality proof, let the output earn the trust.

**"What you couldn't afford before"** — Cost destruction angle. For creators and small brands priced out of professional photography or production.

**"What you couldn't do before"** — Creative freedom angle. For creators who had ideas they could never visualise. The limit was never imagination — it was execution.

**"What used to take days takes minutes"** — Speed angle. For teams and agencies where time is the real cost.

**"You don't need a [photographer / director / VFX studio] for this"** — Access angle. Reframe AI as democratised capability, not replacement.

**"The creative work is still yours"** — For audiences worried AI removes creative identity. The prompt is the creative act. The vision is still the human's.

---

## The imagine.art Voice

When writing scripts, copy, or hooks for imagine.art — or for any content creator using imagine.art — these tone principles apply:

**Direct, not corporate.** Short sentences. No passive voice. No abstract claims.

**Confident, not arrogant.** The quality speaks — you don't need to declare it. Show the output, state the number, let the viewer conclude.

**Creative-first.** The platform is a creative tool. Scripts should feel made by someone who cares about creative output, not by a marketing department.

**Specific always.** Every vague claim should become a number, a timeframe, or a named outcome. "Fast" → "30 seconds." "Great quality" → "photorealistic product shots." "Saves time" → "14-hour edit job done in 23 minutes."

**Honest about what AI is.** Don't hide the AI or be defensive about it. Own it, then demonstrate it. The script shouldn't need the viewer to not know it's AI-generated — the output should be good enough that it doesn't matter.
