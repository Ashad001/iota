# Seedance Director — operation routing, production grammar, craft

> **What this is.** seedance-director, excluding V2V. Read when choosing the Seedance operation (T2V / I2V / ref-to-video) or for shot craft: production grammar, recipes, camera and volumetrics, editing and cutting, fashion, poses and walks.

> **Bundle of 17 source files, 228,586 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `seedance-director/SKILL.md` | 33,723 |
| 2 | `seedance-director/references/model-card.md` | 7,774 |
| 3 | `seedance-director/references/production-grammar.md` | 27,792 |
| 4 | `seedance-director/references/recipes-and-operations.md` | 22,683 |
| 5 | `seedance-director/references/advanced-control.md` | 13,498 |
| 6 | `seedance-director/references/realism-and-camera.md` | 12,708 |
| 7 | `seedance-director/references/camera-depth-volumetrics.md` | 14,213 |
| 8 | `seedance-director/references/scene-craft.md` | 8,784 |
| 9 | `seedance-director/references/surfaces-and-use-cases.md` | 7,168 |
| 10 | `seedance-director/references/editing-and-cutting.md` | 21,588 |
| 11 | `seedance-director/references/editing-sources.md` | 6,632 |
| 12 | `seedance-director/references/fashion-editorial.md` | 19,187 |
| 13 | `seedance-director/references/model-poses-and-walks.md` | 12,722 |
| 14 | `seedance-director/references/pro-techniques.md` | 11,226 |
| 15 | `seedance-director/references/research/continuity.md` | 3,018 |
| 16 | `seedance-director/references/research/action-environment-composition.md` | 2,979 |
| 17 | `seedance-director/references/research/montage-and-rhythm.md` | 2,891 |

---

<!-- ═══════ FILE: seedance-director/SKILL.md ═══════ -->

---
name: seedance-director
description: "The master Seedance 2.0 director — the ONE skill in control of every Seedance job. It routes every brief to the right operation (text-to-video, image-to-video, reference-to-video, or V2V edit) and owns the grammar for each. Use whenever the user wants to make OR edit a video: clip, Reels/TikTok hook, ad film, music video, fashion film, product shot, fight or action sequence, transformation, POV, dialogue scene — or footage edits: VFX (fire, smoke, rain, creatures, destruction), environment swaps, weather changes, element add/remove/replace, repairs and extends that preserve the subject's face, performance, lip-sync and camera exactly — even without naming Seedance. The user directs (idea, story, creative calls); the skill handles all cinematography: cinema mode, scene archetype, right-sized prompt tiers, identity and composition locks, the anti-plastic realism stack, diegetic audio with lip-sync, transitions, camera replication, first/last-frame control, JSON prompts, phone-look UGC, bilingual EN+ZH."
---

# Seedance Director — the one skill for any Seedance video prompt

This is the unified Seedance 2.0 prompt director. It merges everything worth keeping from the separate Seedance systems into one self-contained skill: the less-is-more size ladder, the user-friendly "you bring the idea, I do the cinematography" translation layer, the locked ten-block production grammar with five cinema modes, the scene-archetype router and engine-rendering constraints, the realism stack that fights plastic AI output, the editor's craft layer, and the full recipe library. Everything it points to lives in `references/` beside this file.

## The deal: you direct, this skill shoots

The user is the director. They bring the idea, the story, the feeling, the creative calls — *"a lonely guy eating ramen in the rain,"* *"my product spinning on marble,"* *"two fighters, one wins."* They do **not** need to know a single cinematography term.

This skill is the cinematographer, gaffer, editor, and sound designer in one. It translates the idea into the exact technical language Seedance rewards: shot grammar, lens behavior, lighting motivation, camera psychology, composition locks, realism cues, diegetic audio, aspect, and duration. Never make the user learn jargon. Never hand back homework. Take the idea and make the best possible visual.

When the idea is missing something only the user can decide (what happens, who's in it, the emotional beat), ask — briefly, one question at a time. When it's a craft decision (lens, grade, camera move, mode), **decide it yourself** and surface it in the plan for a quick yes.

## How Seedance 2.0 works (the facts that constrain every prompt)

Seedance 2.0 (ByteDance SEED Lab, launched Feb 12 2026) is the first major **quad-modal** video model — text + image + video + audio in one pass — with **native synced audio** generated jointly with the picture. Under the hood it's a Dual-Branch Diffusion Transformer (separate visual + audio branches fused by millisecond cross-attention) on a RayFlow flow-matching engine at **24 fps** — which is *why* it nails Foley/lip-sync timing and physics. Full model card: `references/model-card.md`.

- **Variants:** **Standard** (the quality tier — sometimes surfaced as "Pro"; 2K-capable, strict prompt adherence) and **Fast** (distilled via TSCD for rapid iteration/A-B/storyboarding, cheaper). Across the ecosystem these split into ~16 endpoints (text-to-video, image-to-video, video-edit, video-extend, +turbo/spicy variants) — see `references/model-card.md`.
- **Clip length:** native **4–15 s per single generation** (24 fps), **extendable beyond 15s by chaining** (video-extend / Track Completion). **imagine.art generates up to 15s.** Plan beats to duration: 4–6s = one beat, 6–10s = 2–3, 10–15s = 3–6.
- **Resolution:** native marketing claims "up to 2K," but most surfaces expose **480p / 720p / 1080p**, and **imagine.art caps at 1080p**. **Iterate at 480p, finalize at 1080p** (720p/2K only if the surface actually exposes them).
- **Frame rate:** native **24 fps** (180° shutter = the cinematic default). "Up to 60fps" is surface marketing — unverified.
- **Native synced audio** (dialogue lip-sync at phoneme precision across 8+ languages; event-locked SFX; optional BGM and beat-synced cutting) and **native on-screen text/supers** (which garble easily — see `recipes-and-operations.md`).
- **Aspect ratios:** **16:9, 9:16, 1:1** are confirmed natively (plus "adaptive"). 21:9 / 4:3 / 3:4 appear on older Seedance surfaces — treat as **unverified** on 2.0 / imagine.art and confirm before promising them.
- **Capture the response seed** on every good render where the surface exposes it. The imagine.art app does NOT reliably expose seeds — use the 2–3-take batch protocol in `references/surfaces-and-use-cases.md`.
- **Real-face photos are blocked** by a hard platform pre-filter (tightened after a Feb-2026 deepfake controversy). Identifiable real faces are rejected; **copyrighted characters** are blocked too; every output carries a **C2PA + invisible watermark**. The workaround for a "specific person" is an AI-generated fictional portrait, which passes the filter.
- **Access note:** ByteDance suspended the **overseas direct API** on Mar 15 2026 over copyright disputes — resellers (imagine.art, Higgsfield, WaveSpeed, AtlasCloud) are the practical surfaces; verify direct API access by region before relying on it.
- **Character limit:** keep the prompt under the platform's cap (commonly ~3200 characters on the prompt field). If a production-tier prompt would exceed it, compress — see the trim order in `references/production-grammar.md`.

## THE GOLDEN RULE: right-size the prompt to the brief

This overrides everything. Seedance is a strong auto-director — given a clear mood and one arc, it handles blink timing, fabric, micro-acting, and sound design better than a prompt that micro-manages them. **Over-specification is the #1 failure mode:** a 400-word, seven-realism-layer, ten-negative prompt on a 5-second clip produces conflicting instructions, rigid acting, and jitter. The official target is **60–100 words** for a single short clip.

Pick the tier from **shot count and duration**, never from how much detail you *could* add:

| Tier | Brief | Length | Structure |
|---|---|---|---|
| **1 — Quick** (default for simple briefs) | 4–8s, single shot, t2v or i2v, UGC, hooks, social | **60–120 words** | One flowing paragraph. No section labels, no timestamps. |
| **2 — Shaped** | 8–15s, dialogue, a couple references, one or two cuts | 120–300 words | The four-section structure: **Style & Mood → Dynamic Description → Static Description → Audio**. |
| **3 — Production** | Reference-anchored characters, locked composition, multi-character blocking, hero deliverables, complex multi-shot | 280–600 words | The locked **ten-block** grammar + a cinema mode. Full rigor. → `references/production-grammar.md` |

If a draft busts its tier budget, cut adjectives and trust the model. Every word must describe something observable that the image or the model wouldn't already supply. Density is only earned when it's broken into numbered shots/timestamps — never piled into one paragraph.

## The workflow: route → ask → plan → confirm → deliver → iterate

**Step 0a — Route the brief (the director's first decision, before anything else).** This skill is in control of every Seedance job; nothing gets written until it decides which department the brief belongs to. Four operations, four grammars, never mixed:

| Operation | The user has → wants | Grammar | Department |
|---|---|---|---|
| **Text-to-video** | Only words → a new video | Tiered generation grammar (this file) | Generation |
| **Image-to-video** | A still → animated | First/Last Frame grammar | Generation |
| **Reference-to-video** | Assets lending identity/style/motion/camera → a **new** video | Role lines + generation tiers | Generation |
| **V2V edit / footage VFX** | An existing clip → the *same clip*, changed | Five-part lock grammar | Edits layer → `references/v2v-edits/` |

When a brief with an uploaded video is ambiguous between edit and reference, **ask the one discriminating question**: *"Is the result your clip with changes kept, or a brand-new video that borrows from it?"* Trap cases: "use my clip and make it look like a jungle" (edit or reference — ask); "animate this frame with rain" (that's image-to-video — the performance is not preserved from a still; say so); "make a video like this one" (reference, not edit). Mixed briefs = two prompts in two grammars, sequenced by this skill. If the route is **edit**, jump to the edits layer section below — its rules override the generation grammar. Changing the acting, blocking, dialogue delivery, or camera move of existing footage is a *re-shoot*, not an edit: route it to Generation.

**Step 0b — Ask the director (always, before any prompting).** If the user hasn't already given a clear brief, ask what they want to make. Director-level questions only — never craft questions:
- What's the idea / story / feeling? (the one question that always gets asked)
- Who or what is in it? Any reference images/videos to lock?
- Where is this going — platform/aspect, and how long should it run?

Ask one question at a time; offer a small set of options when it helps (e.g. multi-shot sequence / single hero shot / animate a still / replicate a reference's camera). Never ask about lenses, grades, modes, or camera moves — those are this skill's decisions to make and surface in the plan. Then open `references/surfaces-and-use-cases.md`: confirm the surface (defaults to the imagine.art Seedance 2.0 app) and let the matching use-case playbook pre-fill the plan.

**Step 1 — Plan + confirm.** For every **new** scene, post the tight plan below and wait for a yes before writing the full prompt. (Skip the gate only when the user is iterating on a prompt you just delivered, pre-approved a batch, or says "just give it to me.")

```
Plan:
- Idea: [one line, in plain words]
- Tier: [1 Quick / 2 Shaped / 3 Production] — [why, from shot count + duration]
- Cinema mode: [M1 Narrative / M2 Studio / M3 Action / M4 Performance / M5 Atmospheric]
- Scene archetype: [Pursuit/Duel/Impact · Journey/Atmosphere/Reveal · Confrontation/Interrogation/Negotiation]
- References: [each uploaded image by short descriptor, or "none — text only"]
- Camera: [lens + one primary move]
- Runtime + Aspect: [e.g. 8s, 9:16]

Good to shoot?
```

Always ask runtime + aspect if the user hasn't said — never assume.

**Step 2 — Deliver** the prompt for the chosen tier, with the plain-language summary block (`scene-craft.md` §11) so the director can react without reading the prompt body.

**Step 3 — Iterate on request.** When the user reports a result or asks for a change: change ONE variable per re-roll against the captured seed, using the re-prompt decision tree (`advanced-control.md` §5). Confirm what changed in one line; don't re-post the plan.

## Two lenses on every scene: the look (mode) and the structure (archetype)

These are orthogonal. The **cinema mode** sets the *look* — capture register, lens family, grade, atmosphere. The **scene archetype** sets the *structure* — camera behavior, spatial logic, and what changes over time. Pick one of each.

**Cinema modes (the look):**

| Mode | Use when the scene is… | Signature |
|---|---|---|
| **M1 Narrative** | Real-world, lived-in — streets, kitchens, cars, bars, interiors | Handheld with operator breath, anamorphic character, teal-amber film |
| **M2 Studio** | White/grey void, editorial, fashion film, product, performance-on-set | Clean spherical lens, locked tripod with slow push, saturated editorial grade |
| **M3 Action** | Combat, chase, stunts, war, mechs, debris, destruction | Handheld and shaky throughout, heavier grain, dusty haze |
| **M4 Performance** | Stage, arena, concert, festival pit, crowd + stage lights | Mixed pit-photographer + orbital, hard cuts, streak flares, sweat sheen |
| **M5 Atmospheric** | Empty/abandoned environments, landscapes, weather, mood plates | Locked-off or very slow push, environment is the subject, palette-driven |

**Fashion/editorial briefs** (fashion film, lookbook, runway, try-on, outfit-transition edit, campaign film): fashion is its own cutting grammar — read `references/fashion-editorial.md` (garment-as-protagonist cut logic, the look-shot coverage ladder, pose-hit beat-cutting, format templates, the stills-first storyboard pipeline, fabric/garment failure fixes) plus `references/model-poses-and-walks.md` (runway-walk mechanics, pose vocabulary, flow-posing movement direction) before planning.

**Scene archetypes (the structure) — full router + decision trees in `references/scene-craft.md`:**

- **Action:** *Pursuit* (distance closing/opening) · *Duel* (dominance alternates every beat — never one-sided) · *Impact* (slow build → fast hit → slow aftermath).
- **General:** *Journey* (position in space changes) · *Atmosphere* (nothing changes — mood IS the content) · *Reveal* (hidden becomes visible).
- **Dialogue:** *Confrontation* (both push, dominance trades) · *Interrogation* (one extracts, one resists) · *Negotiation* (balanced, both need something).

Default to **in medias res** — the scene is already in progress unless the user says "starts with…" or "ends with…".

## Universal craft rules (apply at every tier)

1. **One primary action per beat.** Multiple focal points = a multi-shot prompt, not a denser single beat.
2. **Separate camera motion from subject motion.** The single most common failure. *"The dancer spins; camera holds a locked medium"* — never *"spinning camera around a dancing person."*
3. **Always close with one global style/look line.** Without it Seedance defaults to its plastic house aesthetic. On Tier 1 this is one line; on Tier 3 it's the Camera Capture block.
4. **`no 3D, no cartoon, no VFX`** on any realism-priority prompt — the highest-leverage anti-slop phrase in the whole grammar.
5. **One noun phrase per subject, reused.** "A man" → "the detective" → "he" causes drift. Pick one and keep it (or one `@imageN` tag).
6. **Action = intent + named technique, not biomechanics.** ✅ "spinning back kick connects." ❌ "left forearm rotates 45° to deflect the right hook." Force and direction, not a destruction sequence.
7. **Cuts obey double contrast** — every cut changes *both* shot size *and* camera character. Re-anchor who's where and which way they face after any cut (hold the 180° line). Details in `references/scene-craft.md`.
8. **Off-screen = nonexistent; exit-frame = implicit cut.** Show a state change on camera before referencing it. Never choreograph an exit + re-entry in one continuous shot. Track ≤3 characters across cuts.
9. **Emotion as physiology, never labels.** ✅ "jaw clenches, nostrils flare, a 0.3s freeze." ❌ "looks angry / looks sad."
10. **Diegetic audio only by default** — real in-scene sound. Dialogue goes in `"double quotes"` to trigger lip-sync. No score/music unless the user asks (then it's a physical source — a radio, a busker — with distance and quality). Keep spoken lines 5–10 words (see `recipes-and-operations.md`).
11. **Avoid reflections as a hero element** (mirrors, blades) — Seedance breaks scene geometry rendering a *subject's* mirror reflection. Flat wet-puddle/pavement reflections are fine and even a strength. Use mirrors only as incidental background, or face the camera not the mirror.
12. **Cameras by behavior, not brand** in production-tier output — `wide-latitude cinema capture`, `vintage 75mm 2x anamorphic character`, not `ARRI Alexa` / `Panavision`. (Quick-tier brand-vibe anchors like `shot on iPhone 15 Pro` or `Kodak Portra 400` are fine — they pattern-match reliably. Never mix the two approaches in one prompt.)
13. **Ban antislop words.** They sound good and degrade output: *breathtaking, stunning, mesmerizing, cinematic masterpiece, masterfully, seamlessly, effortlessly, a symphony of, visual feast, epic, amazing, beautiful, high quality.* Replace with concrete lighting, lens, and composition. Full list + the dangerous-keyword table in `references/realism-and-camera.md`.
14. **The first 20–30 words rule.** The model weights the opening of the prompt most heavily. Spend it on the shot contract + subject pin (“Montage, multi-shot… / One continuous shot…” + who is in frame) — never on mood adjectives. A subject not pinned up top gets hallucinated replacements at multi-shot transitions.
15. **Declare edit vs reference for every uploaded video.** "Edit @video1" modifies that footage; "reference @video1's [camera/motion/rhythm]" extracts a quality for new content. Ambiguity produces the wrong operation. One explicit role line per asset.
16. **Write physics, not appearances.** The motion branch has a strong physics prior (Seedance 2.0 gained +31.7 pts on a physics benchmark over 1.5) — feed it interactions: "tires smoke as the car drifts 90 degrees," not "car turns." Every beat gives the engine something to simulate.
17. **A cut serves emotion first, geometry last.** Murch's priority order for any cut: emotion > story > rhythm > eye-trace > screen-plane > spatial continuity. When a cut can't satisfy all six, sacrifice from the bottom. Caveat for Seedance: still re-anchor positions after every cut — for this engine that's *reliability hygiene*, not an aesthetic ranking. → `references/editing-and-cutting.md` §1.
18. **Cut on the action; land the eye where it already rests.** Place cuts at the peak of a motion (on the moment of contact in combat), and open the next shot with the subject where the eye was already looking — center-frame in chaos, or on a colour/motion beacon. The cut the viewer never notices is the strong one. → `references/editing-and-cutting.md` §2, §10.

## Input modes are mutually exclusive — decide before writing

Seedance exposes two entry points that **cannot be combined in one render:**

- **First/Last Frame Mode** — a start image (and optional end image) + text. No other references allowed. The model interpolates motion between the frames. Identity comes from the first frame + prompt.
- **Universal Reference Mode** — up to 9 images + 3 videos + 3 audio clips (12 files), each referenced inline as `@image1`, `@video1`, `@audio1`. Locks identity/motion/style/audio, but you cannot pin a hard first/last frame.

If a brief needs both ("start from this still AND use these character refs"), do it in two passes: generate in Universal Reference Mode, screenshot the cleanest opening frame, feed it back as the first frame in a second First/Last Frame render. File limits and details in `references/recipes-and-operations.md`.

## Delivery structures by tier

**Tier 1 — Quick:** one flowing paragraph. Subject + action (one verb) + environment + camera (one move) + a closing look line + ≤3 targeted negatives. Example in `references/recipes-and-operations.md`.

**Tier 2 — Shaped** (the four-section structure, model-validated on the Higgsfield surface):

```
Style & Mood: [palette, lighting, lens character, atmosphere — never skip]
Dynamic Description: [shot-by-shot in present-tense prose — camera, movement, action; weave cuts in, no "Shot 1:" labels]
Static Description: [location, props, ambient details — establish anything referenced above]
Audio: [diegetic sound; dialogue in "double quotes" in its original language]
```

**Tier 3 — Production:** the locked ten-block grammar delivered in three parts (numbered reference list → bold title line with runtime+aspect → fenced prompt with all ten blocks). Full spec, the Capture Realism engine, the per-mode Camera Capture lines, and the silent QA pass live in `references/production-grammar.md`. **Read that file before writing any Tier-3 prompt.**

**Optional output modes** (offer when relevant, details in `references/recipes-and-operations.md`):
- **Bilingual EN + ZH** — Seedance is a ByteDance model; native Chinese prompts often render as well as or better than English on ByteDance/Higgsfield surfaces. ZH is a native rewrite (not a translation), ≤1800 chars, dialogue preserved in its original language.
- **JSON** — **only when the user explicitly asks for it; never by default.** Two distinct uses: (a) output wrapper — emit prompt(s) as a clean JSON array for programmatic/API use; (b) native JSON prompting — Seedance parses a JSON-structured prompt directly; offer it (don't switch to it) when a brief involves complex choreography or series consistency. Schema in `references/advanced-control.md` §1.

## Realism in one breath (the anti-plastic essentials)

Seedance's default look — glossy skin, even light, polished motion, soft commercial color — *is* the AI tell. The fix is a menu, not a checklist. On Tier 1 pick **one or two lines**; stack the full engine only on Tier 3.

- **Capture medium** is the highest-leverage single choice: `35mm film, heavy grain, halation, soft highlight rolloff` / `iPhone 15 Pro, native color science, no LUT` / `16mm, slight gate weave`.
- **One motivated light**, not a soft key + fill: `single window as key, deep shadow side, no fill`. Lighting is the single highest-leverage line in the whole prompt.
- **Skin/material truth:** `visible pores, peach fuzz, subsurface scattering, flyaway hairs, fabric weave and natural creases`.
- **Atmosphere with body:** `dust motes in the light`, `humidity haze`, `breath in cold air` — flat air is the headline AI tell.
- **Human-operator camera:** `handheld with organic shake tied to the operator's breath`, never `smooth glide / floating`.
- Close with `no 3D, no cartoon, no VFX` for photoreal briefs.

The full seven-layer stack, the phone-look/UGC formula, capture-medium table, and the negative-prompt discipline (≤3, positive-locks-over-prohibitions) are in `references/realism-and-camera.md`.

## The edits layer — V2V edits & footage VFX (performance is sacred)

The director routes a brief here from Step 0a when it starts from an **existing clip** the user wants changed — add VFX (fire, smoke, rain, creatures, destruction), swap the environment/background, change weather/season/time-of-day, add elements behind the subject (zombies, dinosaurs, storms), remove/replace objects, repair a glitched second, or extend. This layer's rules override the generation grammar:

- **Grammar purity (enforced by the director).** An edit prompt never carries tiers/ten-block/Style-&-Mood structure; a generation prompt never carries `@source` lock headers or keep-clauses; every asset gets exactly one role line (`edit @video1` OR `reference @video1's camera`), never both — ambiguity makes the model run the wrong operation.

- **The Prime Directive:** the subject's face, identity, wardrobe, performance, gestures, lip-sync, timing, and the camera's framing, lens, and move are never touched. Every prompt opens with a **source lock header** (`@source: [plate description]. Preserve […], unchanged throughout. Change only [X].`) and closes with a keep-clause. Changing the acting or camera = a re-shoot, not an edit — use the generation tiers instead.
- **Structure:** V2V skips the tiers and the ten-block format. One directive block, five parts: source lock → the edit (as physics, with an endpoint) → integration (relight decision, contact shadows, haze, parallax, grain/lens match) → audio (SFX + source dialogue only) → keep-clause.
- **One edit per pass**, background before subject; mid-clip changes need a visible on-screen trigger + exact second; ≤3 negatives (`no style change, no extra objects, no warping, no flicker`).
- **Real-face nuance for V2V:** the real-face upload block varies by surface — Higgsfield's Seedance 2.0 V2V runs on self-shot footage of real people (its flagship workflow), while the imagine.art app rejects identifiable real faces. If a source clip is rejected, use the split-reference workaround in `references/model-card.md`.

| Read | For |
|---|---|
| `references/v2v-edits/edit-operations.md` | Add / remove / replace / subvert / extend / repair / bridge / restyle templates, edge-heal pass, sequencing multi-edit briefs, seed & QC discipline |
| `references/v2v-edits/vfx-library.md` | Physics-first effect recipes — fire, smoke, rain, lightning, particles, destruction, staged transformations, creatures — plus the integration stack and subject-boundary rules |
| `references/v2v-edits/world-library.md` | Environment-swap grammar (relight decision, parallax, ground transform, triggers) + researched scenario looks: rainforest, Sahara desert, zombie hordes approaching, rain fights |
| `references/v2v-edits/continuity-and-detail.md` | Multi-pass/multi-shot continuity — anchor blocks, drift patterns and recovery, character detail locks, the surface-state-vs-performance boundary, the anti-CG realism stack, and CGI-scale ops (set extension, sky replacement, day-for-night, crowds, war plates) |

## When to route OUT of Seedance

Seedance only makes video. Hand off when the brief is something else:

- **Still image, poster, mockup, photo edit, key art** → an image model (e.g. `nano-banana-prompter`).
- **Animate one specific existing still with very tight camera control**, or **identity-lock a character across many separate shots** from clean portraits → consider `kling-prompter` (image-to-video and Elements are Kling's strengths).
- **Pull live web data into a visual**, or **brand-mandated pixel-perfect typography** → an image model; Seedance's native supers are good only for stylized text.
- **Chained campaign** (hero still → animate) → generate the still in an image model, lock it as the reference, then return here for the Seedance leg.

## Reference map — read the right file for the job

| Read this | When |
|---|---|
| `references/model-card.md` | The Seedance 2.0 fact sheet: architecture (Dual-Branch DiT, Temporally-Causal VAE, RayFlow, TSCD, Seedream 5.0 identity backbone), exact input limits (file counts, sizes, formats), durations + extension, the tri-layer native audio engine and its accuracy bands, the ~16 API endpoints, variants/pricing, the real-face restriction + the three sanctioned real-human workflows, and the native narrative planner. Read to confirm a hard spec. |
| `references/scene-craft.md` | Translating a raw idea or reference image into structure: reading color/grade/emotion from an image, the five directing principles, the scene-archetype router + decision trees, engine rendering constraints, cut rules (double contrast, re-anchor, inserts), dialogue compression, the plain-language summary block. |
| `references/editing-and-cutting.md` | **The editor's brain (Tier 2–3 craft).** *Why* a cut works and what it's for: Murch's Rule of Six (priority of a cut — emotion over geometry), cutting on action / on the hit, screen direction as meaning (converging = collision, diverging = escape), J/L cuts & sound bridges (audio as the edit — high-leverage given native synced audio), intercutting/parallel action, cadence & shot-length ("ramp, don't jolt"), montage-of-meaning (Kuleshov, metric vs rhythmic), environment cutting (establish→detail→re-establish, graphic match), composition grammar (thirds, lead room, depth, frame-in-frame, size↔emotion), eye-trace, and a **"what Seedance actually honors" reliability table**. |
| `references/production-grammar.md` | **Any Tier-3 production prompt.** The locked ten-block format, the five modes' Camera Capture lines, the Capture Realism engine (three-depth atmosphere, per-zone specular kill, contrast curve), three-part delivery, and the pre-delivery QA pass. |
| `references/realism-and-camera.md` | Dialing the look: the seven-layer realism stack, capture-medium table, phone-look/UGC, the camera/lens/lighting trigger vocabulary, behavior-not-brand substitutions, and negative/antislop discipline. |
| `references/camera-depth-volumetrics.md` | **Deep camera realism, framing & composition (any tier).** How physical cameras act — inertia, operator physiology, mount signatures, focus/exposure behavior, caused-not-sprinkled lens artifacts; the official `Camera: [move]+[speed]+[subject lock]+[mount]` grammar with the speed ladder and jitter/warp/zoom fixes; framing for a language-model cinematographer — shot contract first, per-shot size labels, the shot-size ladder with AI reliability, angle-as-power, POV locks, anti-centering/negative-space/occupancy habits; depth engineering (three registers, parallax, aerial perspective, DOF/occlusion); volumetric light (source+occluder+medium, backlight, the restraint rule). |
| `references/recipes-and-operations.md` | Format recipes (transformation, POV, orbs, fights, animation), multi-shot construction, native text-in-video, audio & dialogue, V2V edit operations, multimodal reference + identity-locking, the iteration loop, and the bilingual/JSON output specs. |
| `references/advanced-control.md` | Native JSON prompt schema, transition engineering (hard cut / dissolve / whip pan / match cut / morph + speed ramps + music-beat cutting), reference-video camera replication and motion capture, first/last-frame + keyframe logic, prompt-position weighting, and the re-prompt decision tree. |
| `references/surfaces-and-use-cases.md` | **Read at Step 0.** The imagine.art Seedance 2.0 app surface profile (duration/resolution caps, no-seed batch protocol, real-person rule, guidance hierarchy: ByteDance official > Higgsfield > vetted community > platform blogs), plus the use-case playbooks (UGC, product, narrative, action, ASMR, atmosphere, transformation, R2V) that pre-fill plan defaults. |
| `references/pro-techniques.md` | Official-doc patterns: edit-vs-reference intent, physics-first action writing, the Shot-Script format (named shots + timecodes), reference role taxonomy + file allocation, extension chaining for 30–90s+ long-form, in-place video editing (replace/add/delete/subvert), multi-camera coverage, sub-second micro-timing, Prohibited/Allowed constraint blocks, production design anchors, storyboard phase skeletons. |
| `references/fashion-editorial.md` | **Any fashion/editorial brief.** The fashion cut grammar (pose logic over continuity logic, jump cuts as idiom), the seven-shot coverage ladder and alternation pattern, fashion beat-cutting (pose hits, flash/strobe, match-on-pose outfit swaps, bimodal pacing), format templates (lookbook, fashion film, runway recap, 9:16 outfit-change edit, campaign stack), the stills-first storyboard→Seedance pipeline with outfit-change chaining, fabric reliability + the texture-crawl fix ladder, fashion anti-slop, and a fashion reliability table. |
| `references/model-poses-and-walks.md` | Writing what a model physically does: runway-walk mechanics by body part, walk registers (high-fashion / power / commercial / sashay / male), the end-of-runway stop–pose–pivot sequence, named pose vocabulary (contrapposto, S-curve, broken doll, garment-interaction poses, hand rules), flow posing + micro-movement menus for film, attitude registers (smize, squinch, turtle), and the movement verb bank. |
| `references/editing-sources.md` | **Background only — not on the prompt-writing path.** The evidence base behind the editing layer: key citable claims (Murch's weights, the Kuleshov effect, ASL bands, Bordwell, Pearlman) + a consolidated bibliography, and the live-source list for Seedance 2.0 facts. Read to *verify or extend* a principle, never to write a prompt. Deeper sourced notes in `references/research/`. |

## Pre-flight checklist (run before delivering any prompt)

0. **Route decided at Step 0a** — generation (t2v / i2v / r2v) or V2V edit; grammars not mixed; every asset holds exactly one role line; ambiguous video uploads resolved by asking the user.
1. **Tier chosen from shot count + duration** — not from enthusiasm.
2. **Input mode decided** — First/Last Frame *or* Universal Reference, never both.
3. **Cinema mode + scene archetype both picked.**
4. **One primary action per beat; camera and subject motion described separately.**
5. **Subject named with one consistent noun phrase / `@imageN` tag.**
6. **References = role lines only**, never re-describing what the image already shows.
7. **Cuts obey double contrast; positions re-anchored after each cut.**
8. **Closing look line present** (one line Tier 1, Camera Capture block Tier 3); `no 3D, no cartoon, no VFX` if photoreal.
9. **Diegetic audio written; dialogue in "double quotes", 5–10 words per line.**
10. **≤3 negatives, by real risk; antislop words purged.**
11. **Aspect + duration set and confirmed; within the surface cap (up to 15s on imagine.art) and the character cap.**
12. **Seed captured for iteration (or batch protocol if no seed); 480p test → 1080p final.**
13. **(Tier 2–3) Editing layer considered, not piled on** — cut chosen by emotion/story and landed on motion; *one* idea pulled from `editing-and-cutting.md`, never the whole menu.
14. **Known weak spots designed around** — no readable on-screen text relied on (two-pass it), no subject-in-mirror, no extreme hand close-up, no fast-complex-motion in one beat.
15. **(Fashion briefs)** the fashion layer applied — every cut justified by what it reveals about the garment; walk/pose written as mechanics not adjectives; ceilings respected (≤3 outfit changes per generation, 4–5 steps per walk, 4–6s shots for shimmer-prone fabric); literal "no music" if the director wants silence.


<!-- ═══════ FILE: seedance-director/references/model-card.md ═══════ -->

# Model Card — Seedance 2.0 (the fact sheet)

The hard specs and mechanics behind the prompting rules. Read this to confirm a number or understand *why* a rule exists. Everything here is Seedance 2.0 only.

---

## Identity & architecture

ByteDance Seedance 2.0 (Seed research division), launched **Feb 12 2026** — the first major **quad-modal** video model: text + image + video + audio in one pass, with **native joint audio-video generation**. Benchmarked at the top of the Artificial Analysis Arena (Elo ~1,269) for multimodal control, physics, and instruction adherence.

- **MMDiT backbone (~4.5B params)** — a Multi-Modal Diffusion Transformer replacing the legacy U-Net; treats video as interconnected 3D spatiotemporal patches (true object permanence), not flat independent frames.
- **Temporally-Causal VAE** — compresses images and video into one shared latent space; adversarial + perceptual loss preserves high-frequency detail (fabric weave, skin pores) through compression.
- **Dual-Branch Diffusion Transformer (DB-DiT)** — one branch generates the visual tokens, a second generates the audio waveform; they're fused, not layered in post.
- **TA-CrossAttn (Temporal-Audio Cross-Attention)** — synchronizes audio and video at the **millisecond level** during diffusion. This is *why* Foley and lip-sync land on the exact frame.
- **RayFlow (Rectified Flow Transformer)** — flow-matching engine; ~30% faster than 1.5, and it **penalizes physically impossible states during denoising** (the physics prior — floating hair, disjoined shadows, morphing limbs are minimized).
- **TSCD distillation** — Trajectory Segmented Consistency Distillation; ~4× faster inference, powers the **Fast** endpoints.
- **Identity backbone** — leverages the Seedream 5.0 image model to lock facial bone structure, skin texture, and wardrobe into a latent matrix held across 360° head turns and lighting shifts.
- Trained at **24 fps**; progressive training low-res → high-res; SFT + RLHF (Foundational / Motion / Aesthetic reward models); physics-weighted SeedVideoBench-2.0 data.

**Prompting implication:** because the physics and audio are *foundational*, you write **interactions** (let the engine simulate drag, weight, collision, Foley) rather than appearances, and you can lean hard on sound-led editing (J/L cuts, beat-sync).

---

## Durations

- **Single generation: 4–15 seconds**, 24 fps. **15s is the native max single-shot length.**
- **Extendable beyond 15s** two ways (see `recipes-and-operations.md` §7):
  - **video-extend** — `Extend @video1 forward by 5 seconds`; the model reads the final frames (momentum, lighting, spatial coords) and continues seamlessly. Set the requested generation duration to match the extension length.
  - **Track Completion / Fusion** — bridge up to 3 uploaded clips, **≤15s total**, generating the connective action between them.
- **imagine.art:** generates **up to 15s**. Other surfaces vary; Sora-style 20s+ single takes are a different model, not Seedance.

## Resolution & output

Native **up to 2K** on the Standard ("Pro"/quality) tier (e.g. Dreamina Studio plans unlock 2K). Most surfaces expose 480p / 720p / 1080p. **imagine.art ceiling is 1080p.** Workflow: iterate 480p → finalize at the surface ceiling. Output is MP4, with **C2PA metadata + invisible watermark** embedded on every render.

## Input limits (the 12-file quad-modal context)

Max **12 reference files total** per generation (more degrades context). Each tag is auto-numbered by upload order and must be explicitly called and role-assigned in the prompt.

| Modality | Max files | Per-file limit | Formats | Used for |
|---|---|---|---|---|
| **Images** | 9 | 30 MB each | JPEG, PNG, WEBP, BMP, TIFF, GIF | character identity, face/wardrobe, scene composition, color palette, first/last frame |
| **Videos** | 3 | 50 MB each, **15s total**, 480–720p input | MP4, MOV | motion transfer, camera choreography, rhythm/pacing, VFX replication |
| **Audio** | 3 | 15 MB each, **15s total** | MP3, WAV, AAC | emotional tone, beat-sync, voice/lip-sync match, pacing |
| **Text** | — | — | natural language | the director: narrative, role assignments, actions, constraints |

(For audio *references* specifically, MP3 is the most reliable in practice; trim to 3–8s — see `recipes-and-operations.md` §6.)

## The native audio engine (tri-layer)

Synthesized in one pass, analyzed from the visual generation:
1. **Dialogue** — phoneme-level lip-sync across **8+ languages** (EN, ZH Mandarin/Cantonese, JA, KO, ES, FR, DE, PT) with dialect accuracy (~90% delivery accuracy).
2. **Foley (action-matched)** — the physics branch tells the audio branch about impacts/friction/material; the SFX is embedded at the exact frame of contact (~82% object-interaction accuracy).
3. **Ambience** — spatial room tone / environment embedded for sonic depth of field (~75% spatial accuracy).

**Prompting implication:** prompt a **sonic hierarchy** — one "hero" audio element per shot — or the mix muddies (see `recipes-and-operations.md` §6).

## Variants & endpoints

Two tiers: **Standard** (the quality tier, sometimes surfaced as "Pro"; 2K-capable, strict multimodal adherence) and **Fast** (TSCD-distilled; rapid iteration, A/B, storyboarding). Across the ecosystem (Dreamina, Morphic, Higgsfield, WaveSpeed, EvoLink, TopView, imagine.art, etc.) these split into ~16 endpoints, including: `text-to-video` / `…-turbo`, `image-to-video` / `…-turbo`, `video-edit` / `…-turbo`, `video-extend`, and `image-to-video-spicy` (high-throughput social animation). Billing is credit-based or per-second (e.g. ~$0.09/sec for 480p on some APIs).

## The real-face restriction + sanctioned workflows

Many commercial deployments block generation of recognizable real-world human faces (anti-deepfake), and copyrighted characters are blocked. Three verified ways to proceed when you legitimately need a real person:
1. **Line-art abstraction** — convert the photo to a detailed sketch/line-art, upload that as the `@image` reference (strips the photoreal metadata that trips the filter), then prompt a photorealistic render from the geometry.
2. **API verification gateway** — enterprise/authorized-spokesperson "Face Review" modules on some APIs lift the restriction after legal authorization; one portrait then drives multi-language spokesperson video.
3. **Split-reference editing** — screenshot the face as an `@image`, blur/mask the face in the source `@video`, and prompt the model to fuse the unmasked face onto the body (edits wardrobe/lighting/environment without tripping the video-scan filter).

Default for "a specific person" with no rights: use an **AI-generated fictional portrait** — it passes the filter cleanly.

## The native narrative planner

Fed a complex narrative prompt, Seedance fragments it into a logical shot sequence (establishing → OTS medium → reaction close-up) and generates them **in one latent pass**, so facial identity, wardrobe, and lighting stay mathematically consistent across cuts. This is why structured multi-shot prompts (numbered shots / timecodes) outperform one run-on paragraph — you're feeding the planner, not fighting it. Note the caveat from `recipes-and-operations.md`: within one generation this reads as a *flowing multi-angle sequence*; for frame-accurate hard cuts, stitch.

## In-latent-space editing (NLE)

Seedance edits existing clips without full regeneration: **replace** (`Replace [element] in @video1 with [new]`), **add/remove** elements (environment physics preserved), **character/wardrobe swap** (new textures mapped onto the existing motion matrix), **extend**, and **fuse/Track-Complete**. Full templates in `recipes-and-operations.md` §7.


<!-- ═══════ FILE: seedance-director/references/production-grammar.md ═══════ -->

# Production Grammar — Tier-3 ten-block format, five cinema modes, the Capture Realism engine

**Read this before writing any Tier-3 prompt.** Tier 3 is for reference-anchored characters, locked composition, multi-character blocking, hero deliverables, and complex multi-shot work. Single-shot Tier-3 prompts run **280–400 words**; multi-shot **never over 600**. Everything below is a production document, not a beautiful sentence — every block does work, and when in doubt you trust the reference image and cut the redundant description.

> **Density rule.** Shorter renders better than longer. Camera Capture is one trimmed line at the bottom — never doubled. Subject Lock trusts the reference image for wardrobe/identity, naming only what the model cannot read (pose, gaze, state, contact points, what stays unchanged).

---

## 1. The three headline upgrades (apply by default to every Tier-3 prompt)

**Upgrade 1 — Volumetric atmosphere in every frame (three depth registers).** Flat air is the headline AI tell. Name atmosphere across three registers in *both* World Plate and Capture Realism:
- **Foreground volumetric haze** — between camera and subject, giving the closest air real physical body.
- **Midground volumetric haze** — wrapping the subject and ground, where light cones (headlights, practicals, sunlight, stage lights) cut through most densely.
- **Deep-background haze/fog** — dissolving the deepest structures into atmospheric perspective: softer, desaturated, lower-contrast than everything in front.

Verbatim trigger words: `haze density`, `particulate in the air`, `light shafts cutting through suspended haze`, `atmospheric falloff between subject and background`, `foreground volumetric haze`, `midground volumetric haze wrapping the subject`, `deep-background atmospheric perspective`. Density scales: `thin atmosphere` (clean interior), `light haze` (most exteriors), `heavy suspended mist` (pre-dawn / rain / smoke / post-apocalyptic). Never skip — even a clean studio gets `thin atmosphere`.

**Upgrade 2 — Mid-grey seamless for character builds (never pure white).** When an M2 prompt's job is to lock a character's identity (reference sheet, lookbook, 6-panel grid, locked-pose portrait that downstream shots reference), the default backdrop is **mid-grey seamless**. White seamless "gives the model nothing to anchor skin against, blows the contrast curve, and produces the plastic over-lit AI-portrait look." Default character-build World Plate language:

> *Mid-gray seamless studio backdrop, even neutral mid-gray, no seam line, no gradient. Subject relit from scratch overriding any reference lighting — one broad diffused source from camera-left and slightly above, gentle wrap, no harsh shadows, no rim light, no hair light, no kicker. Skin and fabric read matte and velvety in a low-contrast milky look, rendering at their true natural tone against the neutral gray.*

Use white seamless only on explicit request (hard-key fashion editorial, high-key product, intentional blown-out aesthetic).

**Upgrade 3 — Cameras by behavior, never brand names.** Write what the gear *does*. Substitution table:

| Stop writing (brand) | Write this (behavior) |
|---|---|
| ARRI Alexa 35 | wide-latitude cinema capture |
| Panavision Ultra Vintage 75mm anamorphic | vintage 75mm 2x anamorphic character at a wide aperture, oval bokeh, soft edge falloff |
| Cooke S4 / Master Prime | clean spherical character, even sharpness, natural round bokeh |
| Kodak Vision3 250D / 500T | color-negative daylight / tungsten film rendition |
| Pushed 800 ASA | heavier low-light grain |
| Tiffen Black Pro-Mist 1/4 | light diffusion bloom softening highlights |
| ARRI SkyPanel | soft diffused source, cool ambient quality |
| Astera Titan / practical tungsten | warm tungsten practical from a visible bulb in frame |
| Gimbal Steadicam tracking | smooth tracking shot with operator drift |
| Easyrig handheld | handheld with natural operator breath |
| Tilta Nucleus rack focus | rack focus from foreground to background |

Same logic on lighting: direction, quality, temperature in plain physical terms — no fixtures, no model numbers. (Quick/Tier-1 brand-vibe anchors like `iPhone 15 Pro` or `Kodak Portra 400` are the one sanctioned exception, and only in Tier-1 — never mix the two approaches in one prompt.)

---

## 2. Session opener — the character gate (ask once per session)

The first time the user asks for a Seedance prompt in a session, ask once:

> "Any recurring characters in this batch? If so, are they already built (reference images locked) or do we need to develop them first?"

- **Built →** ask for reference upload(s). Study and lock face, bone structure, skin tone, hair, identity markers, proportions. Mirror back the locked spec in plain language; carry it through the session.
- **Needs developing →** lock the character first in an image model (e.g. `nano-banana-prompter`), then return.
- **No recurring / one-off / pure environment →** skip the gate.

Don't ask again in the same session.

## 3. Pre-prompt confirmation (every new scene)

Post this summary and wait for a green light before writing the full prompt. References first; runtime + aspect last (right above the yes).

```
Pre-prompt check:
- References attached: [each uploaded reference by short visual descriptor, or "none — pure text composition"]
- Mode: [M1 Narrative / M2 Studio / M3 Action / M4 Performance / M5 Atmospheric]
- Scene: [one-line scene description]
- Characters: [who's in frame by visual marker; or "none / environment plate"]
- Frame Map: [one-line compositional read — where each character sits, depth layer, eyeline]
- Camera: [lens length, key movement — e.g. "55mm anamorphic, handheld with operator breath"]
- Runtime + Aspect: [Xs, 16:9 / 9:16 / etc.; single shot OR Xs, N-shot sequence]

Sound good?
```

**Skip the confirmation only** when the user is iterating on a just-delivered prompt, pre-approved a batch, or said "skip the confirm." For new scenes, confirmation is not optional. Never assume runtime or aspect — ask if unstated.

## 4. Three-part delivery (locked)

1. **Numbered bulleted list of references to attach**, in order, each with a short visual descriptor. Max 9 images (Seedance hard cap).
2. **Bold title line with runtime + aspect** — e.g. `**Seedance prompt — 10s, 9:16**`.
3. **One fenced code block** with the ten labeled blocks in exact order, `@image1`–`@image9` tags inline (tag number matches the reference list: bullet 1 → `@image1`). Output language: **English only.**

---

## 5. The ten-block output format (HARD LOCK ORDER)

Exact order, every prompt, no exceptions:

**Scene & Mood → Frame Map → Subject Lock(s) → Cross-Frame Rules → Movement → Last Frame → World Plate → Sound Bed → Capture Realism → Camera Capture**

Block scaffolding (the inner-bracket descriptions tell you what each block carries):

```
Scene & Mood: [one or two sentences — what the moment IS, dramatically. Energy, not geometry.]

Frame Map: [where each subject sits — left/center/right third, foreground/midground/background, x% where helpful, what negative space remains. Multi-shot: write Shot 1 framing, Shot 2 framing, etc.]

Subject Lock — @imageN: [one discrete block per character — identity anchor (which @imageN carries the face) + body orientation + pose + state + gaze + contact points + state-changes the image can't carry (damp, dirt, blood) + lock-down line. Trust the reference for wardrobe; don't re-describe it.]

Cross-Frame Rules: [multi-character — never swap positions, never cross center, never change depth; distance, screen sides, eyelines held. Multi-shot: name what carries across the cut.]

Movement: [four layers, flowing prose with per-beat timestamps inline — character motion, micro-motion (breath/hair/fabric), environmental motion, (camera only if not in Camera Capture). Multi-shot: "Shot 1 (0–6s)… Hard cut to Shot 2 (6–10s)…". Dialogue in "double quotes" to trigger lip-sync.]

Last Frame: [the exact closing composition at the end of runtime + the on-screen-text suppression line.]

World Plate: [location, time, weather, set dressing, atmospheric quality — anchored to @imageN if a plate is attached. Name the three haze registers here too.]

Sound Bed: [diegetic only — list the specific sounds; no music, no lyrics, no score.]

Capture Realism: [the anti-plastic engine — three-depth atmosphere, moisture-without-shine if wet, per-zone specular kill on skin, contrast curve stated three ways. See §8. Never omitted unless the user wants a glossy/clean register.]

Camera Capture: [single trimmed paragraph — body, lens, filter, movement, stock, grade, frame rate, runtime, aspect, optional seed. The ONLY camera/grade/film-stock language anywhere. Never doubled.]
```

If a block has little to say, shorten its content — never drop the label. Conditional content (the `[IF WET: …]` clause, the human-skin sentence) lives inside the block; the label still ships.

**Universal rules that govern the ten blocks:** one Subject Lock per character (never jammed together); one Camera Capture line at the bottom (no mid-body `Camera:` block); no character names (describe by hair/wardrobe/markers); no brand names (gear or product); no platform/tool names; no internal production context ("as established earlier"); diegetic audio only; cut triggers are "Hard cut to / Smash cut to / Match cut on"; no on-screen text by default (Last Frame closes with the suppression line); **positive locks over negative prohibitions**; one main idea per shot; trust the reference for wardrobe; and **the canonical reference is always attached as its own `@imageN` even when the subject is visible in the plate** — the plate carries the world, the canonical reference carries identity.

---

## 6. Frame Map spec

The floorplan of the shot — anchors every subject in screen space before motion. Horizontal: left third / center / right third (or x%, 0%=left, 100%=right). Vertical: upper/center/lower (or y%). Depth: foreground/midground/background. Occupancy: ECU/CU/MS/full body (or % of frame height). Negative space: what stays empty and what fills it (atmosphere, distant elements).

- *Single subject:* `@image1 anchored in the left third, x=30%, foreground, medium shot from waist up, occupying 55% of frame height. The right two-thirds hold wet street and distant neon signage as negative space.`
- *Two subjects:* `@image1 in the left third, x=28%, foreground. @image2 in the right third, x=72%, midground, slightly deeper. The center holds open as tense negative space. Neither crosses the central vertical axis.`
- *Multi-shot:* `Shot 1 (0–6s) — wide two-shot. @image1 left third x=32% foreground; @image2 right third x=68% midground. Shot 2 (6–10s) — low-angle close-up tight on @image1's reflection in the wet glass.`

**Skip percentages** for clear classical compositions (centered single, OTS, profile two-shot, symmetrical wide) — use film language. Coordinates earn their place when blocking is asymmetric/tight or drift would visibly break the shot.

## 7. Subject Lock spec

Pin every property that must stay stable across runtime without re-describing what the reference carries. Per character: **identity anchor** (which `@imageN`) · **body orientation** (facing camera / profile / three-quarter / back) · **pose** · **state** (described by what body/face physically do, never an abstract feeling) · **expression** (lips, eyes, brow, jaw) · **gaze direction** · **contact points** (where the body touches the world) · **state-changes the image can't carry** (damp, torn, dusty, bloodied) · **lock-down line** ("face, hair, wardrobe, and silhouette identical throughout").

Example:
> Subject Lock — @image1: Face, hair, oxblood corset, and silhouette identical throughout. Ponytail damp from the drizzle, fabric darker where rain has soaked in. Bent at the waist, torso angled toward the side window of @image3, both hands raised to her ponytail at the crown, fingers smoothing strands. Body squared to the car, weight even. Gaze locked on her own reflection in the wet glass.

Multi-character = one discrete block each (`Subject Lock — @image1:` … `Subject Lock — @image2:` …). Never jam two characters into one paragraph.

## 8. Cross-Frame Rules

For 2+ characters sharing a frame, Frame Map + Subject Lock aren't enough — relationships need explicit rules or Seedance swaps/crosses/drifts/collapses depth. Specify: no swap, no center crossing (unless action demands, with timing), no depth change, distance consistency, screen sides held, eyelines, and carry-across-the-cut.

> Cross-Frame Rules: @image1 and @image2 never swap positions, never cross center, never change depth. Distance, screen sides, eyelines, costumes, and silhouettes stay consistent across the full runtime.

When a cross is required: `At 4 seconds, @image1 steps across the central axis from the left third into the center. After 5 seconds the new blocking holds: @image1 center foreground, @image2 unchanged in the right third midground.`

## 9. Movement (four layers, never tangled)

Write in this order, in flowing prose: **(1) character motion** (per-beat timestamps) → **(2) micro-motion** (breath, hair, fabric, jewelry) → **(3) environmental motion** (rain, smoke, dust, traffic, wind) → **(4) camera motion** (usually omitted here; it lives in Camera Capture). Name each layer even when it's "no motion" — saying nothing moves is a directive; absence is not. Dialogue goes inline in `"double quotes"`, kept to 5–10 words per line.

Default = prose with hard-cut keywords. The **timeline-prompting variant** (`[0s] … [3s] … [6s] …`) is an alternate, used only when pacing precision is the whole craft choice.

## 10. Last Frame (composition target — mandatory)

The closing composition the shot lands on; Seedance reads it as a target and structures motion to deliver it. Carry the Frame Map forward: where each character sits at the close, final pose/state/gaze, what's in focus, what fills negative space, and the suppression line:

> No on-screen text, no captions, no signage typography, no rendered text in the frame.

(Skip the suppression line only when on-screen text is explicitly requested — then add the text instruction, don't substitute it. Override patterns in `recipes-and-operations.md`.)

## 11. World Plate / Sound Bed

**World Plate:** location, time of day, weather, set dressing, color palette, atmospheric quality (name the three haze registers). Anchor to `@imageN` if a plate is attached; otherwise text-build. **Sound Bed (diegetic only):** list the specific sounds the scene physically produces. Allowed: footsteps (name the surface), fabric, breath, object/body sounds, environmental ambient, mech/sci-fi diegetic, crowd, stage, weather. Never: song/artist names, lyrics, "music plays / soundtrack swells," score or genre descriptors. Three modes:
- Mode 1 (default): `Sound Bed: Diegetic only — [sounds], no music, no dialogue except what is physically spoken in frame.`
- Mode 2 (silent): `Sound Bed: NONE — fully silent capture. Audio added separately in post.` (= `generate_audio: false` at API level)
- Mode 3: `Sound Bed: Diegetic only — [sounds], no music, no dialogue, no soundtrack.`

---

## 12. The Capture Realism engine (the real-footage block — four mechanics)

Camera Capture names the *gear*; Capture Realism names the *physics*. It sits second-to-last and ships on every prompt unless the user explicitly wants a glossy/clean/commercial register. It attacks three default AI failures: flat single-plane staging, glossy/specular skin & moisture, and over-rendered contrast (clipped highlights + crushed blacks).

- **Mechanic 1 — Depth via suspended atmosphere (always on where there are planes):** atmosphere suspended *between camera, subject, and background* across the three depth registers; background renders softer, desaturated, lower-contrast than foreground. Tie to actual planes; name all three registers.
- **Mechanic 2 — Moisture without shine (only if wet/humid/sweaty):** moisture is *present but matte* — damp not beaded, wet but not glossy, mutes and saturates without a single specular hotspot. Skip entirely if bone-dry.
- **Mechanic 3 — Per-zone specular kill + flattering ceiling:** zero shine on forehead, nose bridge, cheekbones, temples, chin, collarbones (the blown nose-bridge/cheekbone hotspot is *the* AI-skin tell). Pair with biology cues (peach fuzz at jaw/hairline, soft even pore texture, true subsurface scattering, warmth preserved). **Flattering ceiling:** texture fine, soft, even — no acne, no blemishes, no enlarged/cratered pores, no clinical macro-detail. Realism never makes a face ugly; tension resolves toward flattering.
- **Mechanic 4 — Contrast curve stated three ways:** (a) tonal curve — shadows lifted gently, highlights rolled off softly, nothing clipping/crushing; (b) specular removal — all speculars surgically removed from skin/hair/fabric/surfaces, every pixel matte and diffuse; (c) grade — low-contrast, slightly desaturated, warmth preserved. Three statements hold it; one gets overridden by the model's contrast bias.

**Canonical Capture Realism block (tune every bracket):**

```
Capture Realism: [Foreground subject] sits inside real depth — [thin/light/heavy] atmosphere suspended between camera, subject, and [the far background element], the background rendered softer, desaturated, and lower-contrast than the foreground so the figure sits within the air rather than pasted on a flat plane. [IF WET: Slight moisture has settled on every surface — damp matte hair, slight moisture on skin holding fully matte with no beading and no wet sheen, [wet ground with muted reflection / damp matte fabric / car paint damp but matte not showroom], moisture that mutes and deepens without a single specular hotspot.] Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones, temples, chin, and collarbones, real peach fuzz catching light at the jaw and hairline, real soft fine even pore texture, light absorbed like true subsurface scattering, warmth preserved and natural, slightly desaturated but never pale or washed-out, never plastic, never doll-skin, never AI-rendered, and never harsh — no acne, no blemishes, no enlarged or rough pores, fine flattering texture that keeps the face looking good. Low-contrast curve — shadows lifted gently holding texture, highlights rolled off softly never clipping to white, nothing crushed to black. All specular highlights surgically removed from skin, hair, fabric, and surrounding surfaces, every pixel reading matte and diffuse. Slightly desaturated grade with warmth preserved.
```

Tuning: **dry** → delete the `[IF WET]` sentence. **No humans (M5)** → drop the skin sentence; keep mechanics 1 and 4; apply matte-not-glossy to environmental surfaces. **M2 editorial** → if the user wants a *crafted* glossy look, reduce/skip the block (M2 is the one mode where controlled highlight bloom on chrome/glass/rhinestone is intentional). This block never names gear, grade hex, frame rate, or runtime — that all lives in Camera Capture.

---

## 13. Camera Capture + the five modes

Camera Capture is one trimmed closing paragraph: body, lens, filter, movement, stock, grade, frame rate, runtime, aspect, optional `seed: [N]`. **Default energy = handheld with breath, drift, organic operator movement** — even in quiet/observational moments. **Locked-off tripod is opt-in only** (user says "locked off / tripod / static," or names a shot type that requires it). All modes default **24fps, 180° shutter**; slow-mo beats are specified inline (`intercut 96fps high-speed slow-motion at [moment] holding 180° shutter`).

**Mode-select table:**

| Mode | Use when the scene is… | Lens | Movement | Grade |
|---|---|---|---|---|
| **M1 Narrative** | Real-world, lived-in | Vintage 2x anamorphic character, 40/55/75/100mm, wide aperture — oval bokeh | Handheld with operator breath | Color-negative daylight, fine 35mm grain, teal-amber |
| **M2 Studio** | Crafted, not photographed — void, editorial, product, fashion | Clean spherical, 32/50/75/100mm — round bokeh, even sharpness | Locked tripod with optional slow push | Saturated editorial, warm-retained blacks, fine grain |
| **M3 Action** | Combat, chase, stunts, war, debris | Vintage 2x anamorphic, 40/55/75/100mm | Handheld and shaky throughout, no stabilized shots | Color-negative, heavier low-light grain, dusty haze |
| **M4 Performance** | Stage, arena, festival pit | Vintage 2x anamorphic — horizontal streak flares on stage lights | Mixed pit-photographer + orbital, hard cuts | Color-negative, fine grain, stage color cast, sweat sheen |
| **M5 Atmospheric** | Empty/abandoned, landscapes, weather, mood | Vintage 2x anamorphic, 35→85mm push range | Locked-off or extremely slow push | Color-negative, fine grain, palette-driven (specify hex) |

**Lens guide (all modes):** 32/35/40mm = wide establishing / full-body / group; 50/55mm = medium portrait / two-shot / dialogue; 75mm = tight editorial / isolation; 85/100mm = ECU (eyes, lips, jewelry, fabric). Default 55mm (M1/M3/M4) or 50mm (M2); M5 uses the wider end.

**Camera Capture template lines (fill the brackets):**

- **M1:** `Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft frame-edge falloff — light diffusion bloom softening highlights, handheld with natural operator breath, color-negative daylight film rendition with fine 35mm grain, teal-amber grade, shallow depth of field, 24fps 180° shutter, [aspect], [XX] seconds.`
- **M2:** `Camera Capture: wide-latitude cinema capture, clean spherical [XX]mm character at a wide aperture — natural round bokeh, even sharpness — mild diffusion bloom, locked tripod with optional slow push-in, saturated editorial grade, fine grain, warm-retained blacks, 24fps 180° shutter, [aspect], [XX] seconds.` (Reflective close-ups add: `intentional highlight bloom on reflective surfaces, blooming the speculars on chrome and rhinestone.`)
- **M3:** `Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft edge falloff — light diffusion bloom softening highlights, handheld and shaky throughout with no stabilized shots, color-negative film rendition with heavier low-light grain, [palette descriptor] with dusty atmospheric haze, 24fps 180° shutter, [aspect], [XX] seconds.` (Impact slow-mo append: `intercut 96fps high-speed slow-motion at the [moment] holding 180° shutter for natural motion blur.`)
- **M4:** `Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, horizontal streak flares on stage lights — light diffusion bloom softening highlights, mixed handheld pit-photographer and orbital operator energy with hard cuts between angles, color-negative film rendition with fine grain, [stage-lighting color cast], heavy volumetric haze, real sweat sheen, 24fps 180° shutter, [aspect], [XX] seconds.`
- **M5:** `Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft edge falloff — light diffusion bloom softening highlights, locked-off or extremely slow push-in only, color-negative film rendition with fine grain, palette grade [hex values], atmospheric haze, weathered material detail, 24fps 180° shutter, [aspect], [XX] seconds. No humans, environment is the subject.`

**Multi-shot / stacked modes:** write each shot's specs inline in the closing line (`Shot 1 — … 40mm …. Shot 2 — same capture register, 75mm … low-angle handheld …`). Don't blend two modes into one averaged grade — the cut between modes is the visual punch.

---

## 14. Runtime, aspect, and the cap

Total runtime + aspect appear in **three places that must all match**: title line, Frame Map (multi-shot), and Camera Capture. Always ask both — never default. Shot complexity vs duration:
- 4–6s — one strong action, single composition, 2–3 beats max.
- 6–10s — one action plus a reveal/hold, 3–4 beats max.
- 10–15s — 3–6 beats / numbered shots with hard cuts inside the prompt.
- **Beyond 15s** (the native single-generation cap; imagine.art also generates up to 15s) — split into separate prompts and stitch with video-extend / Track Completion (see `recipes-and-operations.md` §7).

Aspect quick guide: 9:16 vertical (TikTok/Reels/Shorts); 16:9 landscape (YouTube/web); 1:1 square feed. (21:9 / 4:3 / 3:4 only if the surface confirms them — see `surfaces-and-use-cases.md`.)

## 15. Negative → positive rewrites

Translate every prohibition into a positive lock; keep negatives only for sanctioned suppression lines (on-screen text, specular kill).

| Instinct (negative) | Lock (positive) |
|---|---|
| Don't change face | @image1 keeps the same face, hair, wardrobe, and silhouette throughout. |
| Don't switch positions | @image1 remains in the left third throughout; @image2 remains in the right third. Neither crosses center. |
| Don't drift | Boots stay planted on the same ground marks across the full runtime. Only breath, eyes, hair, and fabric move. |
| No extra people | The frame contains only @image1 and @image2 in their positions. No other figures enter. |
| No camera chaos | Slow controlled handheld with natural operator breath, preserving each subject's third. |
| No blur | Subjects remain sharply focused; controlled motion blur only on falling rain and distant lights. |
| No mode switching | One continuous take, no cuts, no scene change, no time jump. |

## 16. Trim order (when a prompt busts the character/word cap)

Cut in this order until it fits: redundant Subject-Lock wardrobe description (trust the reference) → Movement micro-motion adjectives → Cross-Frame Rules phrasing → World Plate set-dressing detail → Capture Realism (collapse to the canonical block, don't expand). Never cut: the ten labels, the closing Camera Capture line, the suppression line, or the canonical `@imageN` for any named subject.

## 17. Pre-delivery QA pass (silent — never narrated)

Confirm before shipping: character gate asked (first prompt of session); every reference listed + numbered + tagged inline, order matching across all three; **canonical reference attached for every named subject even if visible in the plate**; mode chosen with rationale; Frame Map pins every character; one Subject Lock per character (wardrobe not re-described); Cross-Frame Rules if 2+; Movement has all four layers + dialogue in quotes; Last Frame has the closing composition + suppression line; World Plate anchored + three haze registers; Sound Bed diegetic with specifics; Capture Realism tuned (wet clause only if wet; skin sentence dropped if no humans; contrast three ways); mid-grey seamless for any character build; zero brand names; single Camera Capture line; runtime + aspect confirmed and matching in all three places; per-shot timing sums to total; no names/brands/platform/meta; English only; all ten blocks present in locked order; negatives converted to positive locks; body within 280–400 (single) / ≤600 (multi). Repair before delivery if too poetic (rewrite Scene & Mood physically), overloaded (split to multi-shot), drift-prone (tighten Subject Lock with contact points + ground marks), or double-spec'd (collapse to one Camera Capture line).

> **Worked Tier-3 examples** (full ten-block prompts — M1 narrative single-shot, M2 product, M1 multi-shot two-character, V2V) live in `recipes-and-operations.md` §10.


<!-- ═══════ FILE: seedance-director/references/recipes-and-operations.md ═══════ -->

# Recipes & Operations — tier deliveries, format recipes, audio/text, V2V, multimodal, iteration, output modes

Everything you actually paste, plus the worked examples. Read `realism-and-camera.md` for the look, `production-grammar.md` for Tier-3 structure, `advanced-control.md` for transitions/JSON.

---

## 1. Tier 1 — Quick (the default register)

One flowing paragraph, **60–120 words**: subject + action (one verb) + environment + camera (one move) + closing look line + ≤3 targeted negatives. No timestamps, no section labels, no re-describing a reference image.

**Example — Tier-1 i2v with dialogue (4s, vertical):**
> *Vertical 9:16, 4 seconds, one continuous locked-off shot from a phone propped on the dashboard facing the driver. @image1 = her identity, wardrobe, and the foil-wrapped burrito — ignore its camera angle. A young woman cries quietly in the driver seat, mascara streaked, sun blowing out the windshield behind her. She looks into the lens and says, voice cracking: "Why am I like this?" — then takes one joyless stress-eating bite and keeps chewing through tears. Native iPhone look, real skin texture. Cabin room tone, no music. Avoid cuts, identity drift, plastic skin.*

~95 words. Start every short clip here; escalate only when the brief genuinely needs more shots.

## 2. Tier 2 — Shaped (the four-section structure)

```
Style & Mood: [palette, lighting, lens character, atmosphere — never skip]
Dynamic Description: [shot-by-shot in present-tense prose — camera, movement, action; weave cuts in, no "Shot 1:" labels]
Static Description: [location, props, ambient details — establish anything referenced above]
Audio: [diegetic sound; dialogue in "double quotes" in its original language]
```

**Example — phone-realistic UGC hook (5s, vertical):**
> *Style & Mood: late-afternoon bedroom, natural window light from camera-left mixed with a warm bedside lamp, slight green cast in shadows, native iPhone color, no grade. Dynamic Description: a young woman in a worn grey hoodie sits on the floor against an unmade bed, laptop beside her; she glances up at the phone, half-laughs, looks back at the screen; auto-exposure briefly hunts when she moves; camera shake tied to her breathing. Static Description: unmade bed, open laptop, dust motes drifting through the window light, flyaway hairs catching the light, hoodie weave visible. Audio: laptop fan hum, distant traffic through the window, a small genuine laugh. No text overlays. Avoid jitter, plastic skin, beauty filter.*

## 3. Multi-shot inside one generation

**Approach A — flowing prose with explicit cut keywords.** One paragraph; mark each cut with a camera direction: "Hard cut to a wide shot of…", "Cut to a close-up on…", "smash-cuts to a POV looking up at…", "pushes in to a tight detail on…". Soft transitions: "crossfades to", "dissolves through", "whip-pans into". To forbid them, say so at the top: *"All transitions are hard cuts; never crossfades, dissolves, or whip-pans."*

**Approach B — timeline prompting (only for 10–15s with 3+ beats).** Bracketed markers at each beat:
```
[0s] Wide shot: <subject + action>. <camera + lighting>.
[3s] <camera transition>. <new shot + beat>.
[6s] <camera transition>. <resolution shot>.
```
Pacing law: 5s → 2–3 beats; 10s → 3–4; 15s → 4–6. Each beat = one shot type + one camera instruction + one action + one atmospheric note. **Caveat:** within one generation Seedance produces a flowing multi-angle sequence, not editing-grade hard cuts. For true hard cuts, render shots separately and stitch (reuse the same global look header so they cut together).

**Locked-perspective trick — name what the camera is NOT doing:** `no cuts, no zoom, natural head movement, single continuous shot` (the single highest-leverage POV instruction). Also `locked-off, no pan, no tilt, no dolly`; `no speed-ramping, real-time throughout`.

End multi-shot prompts with a footer: `Total: 15s / 6 shots / 16:9`.

**Timecodes are a real control lever.** The text encoder (RayFlow) is deeply responsive to explicit timecodes — writing `[00:00-00:04] Shot 1: wide reveal` then `[00:04-00:08] Shot 2: close-up reaction` constrains generation to those indices and keeps actions from bleeding across cuts. Use bracketed `[mm:ss-mm:ss]` ranges (or `[Ns]`) when you need a beat to land at an exact time or to sync to an audio cue.

**The CRAFT framework (for complex multi-asset / multi-shot scenes).** When you're juggling several references and a narrative (noir, sci-fi, commercial), order the prompt as **C-R-A-F-T**:
- **Context** — scene, period, location, atmospheric density first (`In a dimly lit 1940s jazz club, smoke density from @image1`).
- **Reference** — map each `@tag` to its exact role (`@image2 for the character's appearance; @video1 only for the walking motion and pace`).
- **Action** — sequential physical beats and object interactions (one verb per beat).
- **Framing** — shot sizes, lens, angle, camera stability per beat.
- **Timing** — explicit time markers, synced to audio cues (`0-4s establishing; at 8s a door-open SFX matching @audio1`).

This is the Tier-2/3 structuring spine for reference-heavy work; it pairs with (doesn't replace) the four-section or ten-block delivery.

## 4. Format recipes (high-performing patterns)

**Transformation — 6-shot escalation (calm → threat → transformation → aftermath).** Best-performing format. Header line (`Montage, multi-shot action, don't use one camera angle or single cut, …`), one-paragraph scene, then `Shot 1:` … `Shot 6:`, then negatives + `Total: 15s / 6 shots / 16:9`. (Full worked example §10.3.)

**POV — locked perspective:** `One continuous shot, POV [role] perspective in [location], no cuts, no zoom, natural head movement, [action arc beat by beat], [sensory cues — breath, dust, footsteps], cinematic, photorealistic, motion blur on hits. Total: 15s / 1 shot / 16:9.`

**Orbs — first-person POV with powers:** open with the hyper-chaotic handheld opener (`Single continuous shot, first-person POV, the camera IS her eyes, completely unstabilized, … her hands always visible in frame, no music only raw SFX, [35mm realism stack]`), then location + enemies + power + escalation; VFX inline in brackets `[VFX: …]`.

**Fights — location + mismatch + escalation:** three required ingredients (clear location, clear power mismatch, defined escalation arc). Beat-by-beat choreography (Seedance executes literally). Speed-ramps in CAPS inline.

**Animation — timed segments with physics:** `@image1 is the first keyframe and style reference. Cinematic stylized 3D animation — [environment], stylized characters. High FPS, realistic particle physics.` then `0–3s:` … `12–15s:` beats; describe physics as precisely as character action.

**Product (i2v):** `Reference the bottle from @image1, place it on polished marble. Backlit, product sharp, background blurred. Slow pull back to reveal the full bottle and a green branch. Arc shot right-to-left, light catching the glass. Settle into a static medium, product centered. Clean studio lighting, premium softbox camera-left, slightly warm whites. Keep product shape and label stable, no new text. Avoid identity drift, jitter. Total: 6s / 4:3.`

## 5. Native text in video

Seedance renders supers itself, but **text garbles easily** ("glyph soup") — signs, screens, labels, multi-line paragraphs, and CJK are unreliable. **Default to a two-pass workflow:** generate clean (no text in frame), add real text/logos in post. Never let the model render brand logos, pricing, or legal text.

When you *do* want native text: `The text "NO PRODUCT." slams into the lower-third in white bold sans-serif on the door slam, with a slight chromatic-aberration shimmer.` Subtitles: `Subtitles appear at the bottom reading "…", synchronised with the audio rhythm.` Speech bubble: `A speech bubble appears beside the character with the dialogue text "…".` **To suppress** auto-supers: `No text overlays, no subtitles, no on-screen captions anywhere — all storytelling is visual.` / `Generate video without subtitles.` Use common Latin glyphs; render anything precision-critical in post.

## 6. Audio & dialogue (native synced audio)

Three layers generate in one pass: **dialogue** (phoneme-level lip-sync, 8+ languages), **SFX** (event-locked Foley), **BGM**. The model infers sound from visuals unless overridden.

**Dialogue rules (lip-sync that holds):**
- Put spoken lines in `"double quotes"` to trigger lip-sync.
- **Keep lines 5–10 words.** Mouth movement gets mushy past ~8s; split long lines across two generations and stitch.
- **Best sync = medium close-up + locked camera + front-facing (or slight ¾) portrait.** Profiles unreliable; wide shots lose face resolution.
- **Remove head-movement instructions during speech** ("nodding", "turning head") — they compete with the lip-sync engine and produce half-motions. Keep the camera locked while speaking.
- Tag language inline: `Character speaks in Japanese: "今日はいい天気ですね。"` Emotion/pacing cues help: `"calm, slightly amused: pause before the punchline."`

**SFX / BGM:** anchor SFX to a time (`SFX: thunder crack at 3s`); a comma-separated raw list works better than prose (`SFX: electric crackle, energy burst, metallic titan rise, lightning chain blast, snap impact`). Keep ≤3 simultaneous layers or the mix muddies. Set mix priority: `dialogue clean and prominent, music low, ambient subtle`. Add a `final 0.5s silence` to prevent abrupt cutoff. **Audio reference files: MP3 most reliable** (WAV/AAC are accepted but can fail silently), trimmed to **3–8s**. For music videos/dance, upload a track as the rhythm reference and beat-sync the cuts.

**Sonic hierarchy (the native audio engine is tri-layer — dialogue + Foley + ambience).** Because all three are generated jointly, requesting intense dialogue + explosive Foley + a sweeping score *at once* overloads the audio branch and the mix turns muddy. Assign **one "hero" audio element per shot** and sequence the rest. Example: `Slow-motion splash on impact. Deep muted city ambience. A sharp splash lands exactly at foot contact. No dialogue. Music enters after the impact, building for the reveal.` On a cut from wide to close-up, instruct the model to **maintain the room tone and music bed** so the ambience doesn't reset (which reads as artificially stitched).

**Silent generation:** `silent generation, no synthesised audio, NO MUSIC NO SFX` or `generate_audio: false` at the API level.

## 7. V2V — video editing operations

| Operation | Template |
|---|---|
| **Add element** | `At [time] + [spatial position] of @video1, add [element]. Keep everything else unchanged.` |
| **Remove element** | `Remove [element] from @video1, keep everything else unchanged.` |
| **Modify / replace** | `Replace [original] in @video1 with [new]. Hold position, lighting, and motion identical.` |
| **Extend fwd/back** | `Extend @video1 [forward/backward] by [N] seconds + [content matching the source's capture register and palette].` |
| **Track completion** (stitch ≤3 clips, ≤15s total) | `@video1 + [transition] + connect to @video2 + [transition] + connect to @video3.` |
| **Style transfer** | `Transform the source clip to [style], preserve core motion and timing, adjust palette to [palette], keep identity consistent, avoid identity drift.` |

V2V is new in 2.0 (1.5 required full regen). Keep reference videos short — trim to the key segment. V2V prompts skip the ten-block format: one short directive paragraph + a "keep everything else unchanged" clause.

## 8. Multimodal references & identity-locking (Universal Reference Mode only)

Upload up to 9 images + 3 videos + 3 audio (12 files total: images ≤30MB each; videos ≤50MB each, 480–720p, ≤15s total; audio ≤15MB each, ≤15s total). Reference inline as `@image1`, `@video1`, `@audio1`. **Order matters** — earlier references are weighted more heavily. **One short role line per reference — never re-narrate its contents:**
- `@image1 = identity and wardrobe — ignore its camera angle and background`
- `match the painted art style of @image2 throughout`
- `@audio1 = background music rhythm; time the cuts to it`

**Reference verbs Seedance reads cleanly:** `Reference`, `Extract`, `Combine`, `Follow`, `Generate from`, `using the composition from`, `maintaining consistent <feature>`.

**Identity consistency (the biggest single win):** define **5–7 identity anchors** up front (face cues, hair, wardrobe silhouette, signature accessory, skin tone, camera-distance preference, lighting direction) — *if an anchor isn't written, the model improvises it.* Use a **3-still reference pack max** (straight-on, three-quarter, profile) shot in the **same session, same lighting, neutral expression** — expression variety averages to a "midpoint face"; avoid collages, mixed warm/cool lighting, and all-crisp headshots. Reuse one consistent subject noun. Remember the mechanism: when forced to choose, **the model keeps motion and lets the face drift** — especially at transitions, fast head-turns, and when a hand crosses the face; lighting shifts act like soft identity edits. Generate in checkpoints (2 shots → QA → expand).

**Avatar-locking across renders:** (1) generate shot 1 with text-only character description, log the seed; (2) screenshot the cleanest frame; (3) upload it as `@image2` in the next render; (4) reference inline (`@image2 = face and wardrobe, identical throughout`). Step 3 puts you in Universal Reference Mode — if you also need a hard opening frame, that render must be First/Last Frame Mode instead.

## 9. Iteration loop & template management

**Four-step loop:** (1) baseline — 2–3 options at 480p; (2) single-variable adjustment — change ONE element per iteration; (3) score on continuity / instruction adherence / post-usability; (4) finalize — capture the seed, render at 1080p. Re-prompt decision tree in `advanced-control.md` §5. **Three-tier templates:** Starter (≤60 words, validate direction) · Production (80–100 words, strict camera + consistency locks) · Fallback (≤40 words, stripped down for unstable output).

---

## 10. Worked Tier-3 examples (full ten-block prompts)

### 10.1 — M1 Narrative single-shot (8s, 9:16, golden-hour cliff)
References: 1. Subject — woman in beige trench coat; 2. Plate — fog-covered cliffside at golden hour. **Title: `Seedance prompt — 8s, 9:16`**
```
Scene & Mood: A held breath at the edge of the world — a figure facing weather she does not flinch from.
Frame Map: @image1 centered, x=50%, y=55%, foreground, framed from the waist up, occupying 60% of frame height. The upper third holds sky and distant sea fog as negative space. A single seabird crosses left to right between 3s and 5s.
Subject Lock — @image1: Face, hair, beige trench coat, and silhouette identical throughout. Standing squared to the cliff edge, feet planted on damp grass, hands at her sides, slight forward lean into the wind. Gaze locked on the horizon screen-forward, lips closed on a held breath.
Cross-Frame Rules: Single subject — she holds her ground mark across the full runtime.
Movement: She holds position across the full 8 seconds, the only character motion a single slow controlled exhale at 5s read in her shoulders rather than her face. Hair whipping continuously, trench-coat hem catching wind drift. A seabird cuts across mid-distance between 3s and 5s. Fog drifts slowly screen-right to screen-left, sea-spray haze suspended in the air, distant cloud bank barely moving.
Last Frame: Hold on her in the center, gaze unchanged, hair still moving, coat hem drifting, seabird now offscreen right, the upper half filled with golden light through suspended fog. No on-screen text, no captions, no signage typography, no rendered text in the frame.
World Plate: Anchored to @image2 — cliffside overlook with wind-flattened grass and exposed rock, the drop falling into deep grey ocean, golden-hour sky from warm amber up top to cool steel grey at the horizon, distant fog bank, light atmospheric haze suspended over the water.
Sound Bed: Diegetic only — distant gull calls, low constant ocean roar, wind through the grass, fabric flap on the coat, a single quiet exhale at 5s, no music, no dialogue.
Capture Realism: The figure sits inside real depth — light haze suspended between camera, subject, and the far ocean fog bank, the background softer, desaturated, and lower-contrast than the foreground so she sits within the air rather than pasted on a flat plane. Slight sea-spray moisture on every surface — damp matte hair, slight moisture on skin holding fully matte with no beading, damp matte coat fabric, moisture that mutes and deepens without a single specular hotspot. Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones, temples, chin, collarbones, real peach fuzz at the jaw and hairline, soft fine even pore texture, light absorbed like true subsurface scattering, warmth preserved, never plastic, never harsh, no blemishes or enlarged pores. Low-contrast curve — shadows lifted gently, highlights rolled off softly never clipping to white, nothing crushed to black. All speculars surgically removed, every pixel matte and diffuse. Slightly desaturated grade with warmth preserved.
Camera Capture: wide-latitude cinema capture, vintage 40mm 2x anamorphic character at a wide aperture — oval bokeh, soft frame-edge falloff — light diffusion bloom softening highlights, handheld with natural operator breath, color-negative daylight film rendition with fine 35mm grain, warm amber highlights cooling to steel-grey shadows, shallow depth of field, 24fps 180° shutter, 9:16, 8 seconds.
```

### 10.2 — M2 Studio / Editorial (6s, 4:3, product close-up)
References: 1. Product — glass bottle, three-quarter reference. **Title: `Seedance prompt — 6s, 4:3`** (key blocks)
```
Scene & Mood: A reveal staged with the patience of a still photograph that decided to move.
Frame Map: @image1 centered, x=50%, foreground, 70% of frame height at the open; the frame widens to reveal a green branch entering screen-left at x=25% by the close.
Subject Lock — @image1: Face of the bottle squared to camera, silhouette and label identical throughout. On polished marble, no tilt, base planted dead-center at the open.
Cross-Frame Rules: Single subject — the bottle holds; only the camera moves and the branch enters.
Movement: Camera holds tight for 2s on a slow pull-back, continues a smooth dolly back from 2s–5s as the framing widens to reveal the marble and a single green branch entering screen-left, then settles into a clean static medium at 5s. Light catches the glass at different angles, refracting through the liquid. The void stays still.
Last Frame: Clean medium product composition, bottle centered at x=50%, branch at x=25%, marble in the lower third. The eye lands on the bottle's neck, lit cleanly. No on-screen text, no captions, no signage typography, no rendered text in the frame.
World Plate: Seamless soft warm-grey backdrop, polished off-white marble with subtle veining in the lower third, single backlit key from camera-right rim-lighting the bottle, soft fill camera-left, no ambient leak, thin atmosphere.
Sound Bed: Diegetic only — faint room tone, soft studio HVAC hum, no footsteps, no music, no dialogue.
Capture Realism: The bottle sits inside controlled studio depth — thin atmosphere between camera, subject, and the soft backdrop, the background slightly softer and lower-contrast. Low-contrast curve — shadows lifted holding marble texture, highlights rolled off on the glass rim, nothing clipping or crushing. Glass holds intentional controlled specular bloom on the curve and shoulder — the one mode where editorial highlight bloom is intentional, blooming the speculars without going clinical-mirror. Slightly warm-retained grade.
Camera Capture: wide-latitude cinema capture, clean spherical 75mm character at a wide aperture — natural round bokeh, even sharpness — mild diffusion bloom, slow dolly back from tight close-up to medium static, intentional highlight bloom on reflective glass, saturated editorial grade, fine grain, warm-retained blacks, 24fps 180° shutter, 4:3, 6 seconds.
```

### 10.3 — M1 Narrative multi-shot, two characters (10s, 16:9)
References: 1. Character A — woman in oxblood corset; 2. Character B — woman in cropped jacket; 3. Vehicle — white low-slung mid-engine sports car. **Title: `Seedance prompt — 10s, 16:9`.** Opens `Scene & Mood: A standoff written in glances at a rain-slicked car between two women who already know how this ends.` Two-shot Frame Map with `Shot 1 (0–6s)` / `Shot 2 (6–10s)`; two discrete Subject Lock blocks; Cross-Frame Rules `never swap positions, never cross center, never change depth`; Movement uses `Hard cut to Shot 2 (6–10s)`; Capture Realism runs the `[IF WET]` clause (`wet ground with muted reflection not mirror, car paint damp but matte not showroom`); Camera Capture writes per-shot lenses inline (`Shot 1 — … 40mm …. Shot 2 — same capture register, 75mm anamorphic character … low-angle handheld at hip height … teal-amber grade … 16:9, 10 seconds total.`).

### 10.4 — V2V edit
References: 1. Source — @video1 (existing 6s clip). **Title: `Seedance prompt — V2V add element`**
```
At 3 seconds, in the upper-right quadrant of @video1, add a single seabird crossing the frame from screen-right to screen-left in mid-distance. Match the existing motion-blur character, rain density, color grade, and 35mm grain. Keep every other element of @video1 unchanged across the full runtime — character positions, wardrobe, car position, lighting, rain, atmospheric haze all identical.
```

---

## 11. Optional output modes

**Bilingual EN + ZH.** Seedance is a ByteDance model; native Chinese prompts often render as well as or better than English on ByteDance/Higgsfield surfaces. Offer a ZH version as a native rewrite (not a literal translation), ≤1800 characters, dialogue preserved in its original language, tags `@image1`/`@视频1` consistent. Some creators report writing the *scene* in Chinese while keeping on-screen text/dialogue in English passes text-rendering better.

**JSON.** Only when explicitly asked; never by default. (a) Output wrapper — emit prompt(s) as a clean JSON array for API use. (b) Native JSON prompting — Seedance can parse a JSON-structured prompt directly; offer it for complex choreography or series consistency. Schema in `advanced-control.md` §1.


<!-- ═══════ FILE: seedance-director/references/advanced-control.md ═══════ -->

# Advanced Control

Power-user controls for Seedance 2.0 (ByteDance, launched Feb 12 2026; quad-modal text+image+video+audio; native synced audio, lip-sync, on-screen text). This file covers the techniques that go beyond the core prose formula in `scene-craft.md` and the camera/realism rules in `realism-and-camera.md`. Read `production-grammar.md` for the Subject → Action → Environment → Camera → Style → Constraints formula these examples assume.

Reminder on the two input modes (never mix them in one render):
- **First/Last Frame mode** — start image + optional end image + text. No other references.
- **Universal/Omni Reference mode** — up to 9 images + 3 videos + 3 audio (12 files max), tagged inline as `@image1`, `@video1`, `@audio1`. No hard first/last frame pin.

---

## §1 Native JSON prompting

Two distinct things share the word "JSON" here. Keep them separate.

### (a) Output wrapper — JSON as a delivery format for the user

When the user is building programmatically (calling an API, batching shots, version-controlling prompts), emit the finished prompt(s) as a clean JSON array so they can paste it into a pipeline. The *prose prompt still lives inside a field* — you are not changing how the model reads it, only how the human stores it.

Example schema (array of shot objects):

```json
[
  {
    "shot": 1,
    "subject": "a silver-haired barista in a charcoal apron",
    "action": "slowly tamps the espresso, steam curling up as she leans in",
    "camera": "slow push-in from medium to close-up",
    "style": "warm film grain, 35mm, soft window light",
    "audio": "low cafe murmur, the hiss of the steam wand, a spoon tapping ceramic",
    "duration": "8s",
    "aspect_ratio": "16:9",
    "negative": "no text overlay, no extra hands"
  }
]
```

Rules for the wrapper:
- `subject`, `action`, `camera`, `style`, `audio` are short prose fragments, not keyword soup.
- `negative` stays at or under 3 items (see negatives policy in `production-grammar.md`); prefer positive locks.
- `duration` ≤ 15s (native single-generation cap; imagine.art generates up to 15s). `aspect_ratio` is metadata, not body text.
- When the model consumes this, the fields are usually concatenated back into the official prose order. The JSON is for the human's tooling.

### (b) Native JSON prompting — JSON the model parses directly

Seedance 2.0 can ingest a JSON-structured prompt as the actual instruction. Use this only for complex choreography (multi-subject blocking, multi-shot series that must stay consistent) where prose would get tangled. The structure makes scene/subject/shot relationships explicit.

Example object the model reads as the prompt:

```json
{
  "scene": "a rain-slick neon alley at night, puddles reflecting signage",
  "subjects": [
    { "id": "runner", "look": "a courier in a wet yellow rain jacket, hood up" },
    { "id": "dog", "look": "a black shepherd keeping pace at his heel" }
  ],
  "shots": [
    {
      "t": "0:00-0:03",
      "action": "the runner sprints toward camera, dog beside him, water spraying from each footfall",
      "camera": "tracking shot moving backward, staying level with his chest"
    },
    {
      "t": "0:03-0:06",
      "action": "he plants and pivots around a corner, the dog cutting inside the turn",
      "camera": "the same tracking move arcs with him, one continuous take"
    }
  ],
  "camera": "single continuous tracking shot, no cuts",
  "lighting": "magenta and cyan neon, hard reflections, wet specular highlights",
  "audio": "rain on metal, splashing footfalls, panting, distant traffic",
  "constraints": { "prohibited": ["cuts", "extra people", "on-screen text"], "allowed": ["motion blur from speed"] }
}
```

**The rule:** prose is the default, always. Only reach for native JSON when (1) the user explicitly asks for it, or (2) the brief is genuinely multi-subject / multi-shot choreography or a series that must hold consistency across renders. Never default to JSON — it adds rigidity, can over-constrain motion, and most single-shot prompts are better as 60–100 words of prose. If you do use it, still respect every prose rule: one primary camera move per shot, rhythm words not camera specs, separated subject vs camera motion.

---

## §2 Transition engineering

Transitions are either **in-generation** (one render produces the cut) or **stitched** (you generate two clips and join them in an editor — see `editing-and-cutting.md`). Know which is which before you promise it.

| Transition | Prompt phrasing | One generation? |
|---|---|---|
| Hard cut | `cut to:` between two described beats, or split into a Shot-Script (Shot 1 … Shot 2 …) | Reliable in one render for 2 shots; for 3+ stitch. |
| Dissolve / crossfade | `slow crossfade from [shot A] into [shot B]` | Partially reliable; cleaner when stitched with a real dissolve. |
| Whip pan | `fast whip pan left, motion-blurred, revealing [new scene]` | Reliable in one render — it reads as one continuous camera move. |
| Match cut | `match cut on the round clock face to the round car wheel` (cut on shared shape) | Reliable when the shared element is explicit (shape/color/motion). |
| Morph | `the [object A] morphs continuously into [object B], shapes flowing` | In-generation only; never stitch a morph. Keep it one subject transforming. |

Match-cut anchors — be explicit about the carried element:
- **On shape:** "match cut from the full moon to a white dinner plate."
- **On color:** "match cut from the red balloon to a red brake light."
- **On motion:** "match cut from her hand swiping down to the elevator doors closing."

### Speed ramps (CAPS inline)

Write the ramp in CAPS so the timing instruction reads as a hard cue, not a mood word:

- `SLOW MOTION as the glass shatters, then SPEED UP to real time as shards hit the floor.`
- `the sprinter explodes off the blocks in SLOW MOTION, RAMP to NORMAL SPEED at full stride.`

Keep one ramp per clip. Two ramps fight each other and read as stutter. Note: bare `fast` (unqualified) is the single most quality-degrading keyword — always qualify it (`fast whip pan`, `SPEED UP`) or replace it with a rhythm word.

### Music-beat cutting

Upload an audio track as a **rhythm reference** (Omni Reference mode, `@audio1`) and time the visual beats to it:

- `@audio1 is the rhythm reference. Cut the visual hits to its beat — a new pose lands on each downbeat.`
- `time the strobe flashes and the dancer's snaps to @audio1's tempo.`

Beat-cutting is most reliable inside one continuous performance shot (poses/hits landing on beats). For a montage of *separate* clips synced to a track, generate the segments, then cut to the track in an editor — see music-beat workflow in `editing-and-cutting.md`.

---

## §3 Reference-video camera replication & motion capture

In Omni Reference mode you can hand the model a video (`@video1`) and tell it to *lift the motion* — camera path, action, or rhythm — and apply it to a new scene. This is how you reproduce a camera move you can't describe in words.

Phrasings (always name what to extract and what to ignore):

- **Camera move:** `reference @video1's camera movement and pacing; apply that same push-in and timing to [new scene]. Ignore @video1's content.`
- **Action / choreography:** `match the dance choreography and rhythm in @video1, performed by [new subject] in [new environment].`
- **Rhythm only:** `use @video1 only as a pacing reference — match its cut rhythm and energy, not its imagery.`

Operating rules:
- **Trim the reference to the key 2–8s segment.** A long clip dilutes the signal; the model averages across it. Cut to just the move you want copied.
- **Edit-vs-reference intent must be explicit.** State plainly whether `@video1` is a *style/motion reference* (you want a brand-new scene that moves like it) or an *edit target* (you want to modify that exact footage — a V2V operation, see `editing-and-cutting.md`). Ambiguity makes the model split the difference and satisfy neither.
- **One element per reference video.** Don't ask `@video1` to donate both its camera move and its lighting and its subject — assign it one job (see reference role taxonomy in `pro-techniques.md`).
- Earlier-listed references weigh more heavily, so if camera replication is the priority, list that video first.

---

## §4 First/Last-frame + keyframe logic

### When to use First/Last Frame mode

Use it when you need a **pinned, exact opening image** (a locked product hero, an approved character frame, a brand plate) — the model treats the start image as ground truth and animates outward from it. Add an end image when you also need to guarantee where the shot lands (a defined final pose, a logo lockup). The text prompt then describes the *motion between* the two frames.

### How interpolation behaves

- With **start only:** the model holds the first frame's composition and identity, then generates motion forward per the prompt. Best for "make this still move" with a guaranteed opening.
- With **start + end:** the model interpolates a believable path from the start image to the end image. Keep the two frames plausibly connected (same subject, same space) — a wild gap forces the model to invent a hard cut or a morph. Describe the *transition* in the prompt ("she turns from facing the window to facing camera"), not just the endpoints.
- A **keyframe used as a style anchor:** even a single start frame locks palette, grade, and set-dressing for the whole clip. If you want a specific look, get it into that frame.

### Two-pass workflow — combine identity refs with a locked opening frame

First/Last Frame mode forbids other references, so identity refs and a pinned first frame seem mutually exclusive. Bridge them in two passes:

1. **Pass 1 (Reference mode):** generate with your identity images (`@image1` = the character, etc.) so the subject is correct. Render a short take.
2. **Screenshot the best frame** — the cleanest frame where identity, framing, and lighting are all right.
3. **Pass 2 (First/Last Frame mode):** feed that screenshot as the **first frame** and prompt the motion. You now have the locked identity *baked into* the start image plus exact-opening control, with no reference conflict.

Use the same trick to fix a great clip that started one beat too early/late: screenshot the ideal moment, make it the first frame, regenerate the motion from there.

---

## §5 Prompt-position weighting + the re-prompt decision tree

### Position weighting

Seedance weights the **first ~20–30 words** most heavily. Spend them on the **shot contract + subject** — the things that must not drift:

- Lead with shot size + primary camera move + who/what: `Medium tracking shot of a lone cyclist in a red jacket …`
- *Then* action, environment, style, constraints.
- Don't bury the subject behind three clauses of atmosphere. If the subject keeps mutating, it's often because it arrived too late in the prompt.

### Re-prompt decision tree — change ONE variable

When a render is close but wrong, diagnose the symptom and change exactly one thing. Don't rewrite the whole prompt.

| Symptom | The ONE thing to change |
|---|---|
| Framing wrong but action is right | Rewrite the **Camera** clause only (shot size + the single move). Leave subject/action/style untouched. |
| Too shaky / unstable | Swap `handheld` ↔ `gimbal/tracking`, and set an explicit rhythm/speed (`slow, smooth`). Remove any bare `fast`. |
| Style drifting between takes | Replace scattered adjectives with **one stronger style anchor** (e.g. "shot on 35mm film"); cut the rest. |
| Subject mutating after 2 tries | Change the **reference image** (or simplify subject descriptors to the 2–3 load-bearing traits). More words won't fix identity. |
| Recurring artifact (bad hands / garbled text / lens flare) | Change the **shot size** (e.g. go wider so hands aren't featured) or **swap a constraint**, rather than adding more negatives. |
| Multiple angles / chaotic cutting you didn't ask for | Add `single tracking shot` (or `one continuous take, no cuts`) to force one camera. |
| Audio out of sync / wrong | Re-describe the audio as diegetic and specific; for lip-sync, tighten the dialogue line and the speaker tag. |
| Action too weak / floaty | Rewrite the **Action** physics-first ("tires smoke as it drifts," not "car turns") — see physics-first writing in `pro-techniques.md`. |

### The 2-reroll rule

After **2 fast re-prompts** on the same idea with no real improvement, **stop editing words — change the inputs.** Swap or upgrade the reference image, switch modes (First/Last Frame vs Reference), or simplify the subject. Words have diminishing returns fast; the lever that actually moves a stuck render is almost always the reference, the mode, or the shot size — not a fourth rewording.

Iterate one variable at a time, capture/reuse the seed when available; on imagine.art the seed may not be exposed, so run a 2–3 take batch per prompt and pick the best (batch protocol in `recipes-and-operations.md`). Iterate at 480p, finalize at 1080p.

---

See also: `production-grammar.md` (core formula, negatives), `realism-and-camera.md` (8 camera moves, realism stack), `editing-and-cutting.md` (stitching, V2V, transitions across clips), `pro-techniques.md` (reference roles, physics-first action, long-form chaining), `recipes-and-operations.md` (batch/iteration protocol), `surfaces-and-use-cases.md` (per-use-case templates).


<!-- ═══════ FILE: seedance-director/references/realism-and-camera.md ═══════ -->

# Realism & Camera — the anti-plastic stack, capture vocabulary, negative discipline

Seedance's default look — glossy skin, even lighting, polished motion, soft commercial color — *is* the AI tell. Fixing it is a **menu, not a checklist.** On Tier 1 pick **one or two lines** (capture medium + one skin/lighting truth). Stack the full seven-layer engine only on Tier 3. Over-stacking on a short clip bloats the prompt and the layers fight each other.

---

## The seven-layer realism stack

### Layer 1 — the "no 3D, no cartoon, no VFX" trick
For anything that should read as real — humans, monsters, animals, organic materials — add this exact phrase to the closing style line:

> *no 3D, no cartoon, no VFX*

This single trio forces Seedance away from rendered-looking output and toward photographed-looking output. It is the highest-leverage anti-slop instruction in the whole grammar. Use it on every realism-priority prompt unless you specifically want stylization.

### Layer 2 — capture medium (the single most important realism choice)
Name a specific stock, sensor, or device:

| Medium | Phrase |
|---|---|
| Cinematic 35mm | `strong 35mm film look, heavy film grain, Kodak Portra 400, halation on highlights, soft highlight rolloff` |
| 16mm grain | `16mm film grain, slight gate weave, organic color shifts` |
| Super 8 | `Super 8 home-movie texture, soft focus, heavy grain` |
| ARRI digital (vibe) | `ARRI ALEXA aesthetic, cinematic dynamic range` |
| Sony cine | `Sony FX3 handheld, S-Log3 graded warm, shallow depth of field` |
| iPhone | `iPhone 15 Pro footage, native iPhone color science, no LUT, no grade` |
| Older iPhone | `iPhone 6 video quality, soft sharpness, muddy shadows, compressed dynamic range` |
| DV camcorder | `DV camcorder 480p, interlaced lines, blown-out highlights, date stamp lower-right` |
| Documentary | `documentary-style, naturalistic, handheld observational` |

(Quick-tier brand-vibe anchors like the above pattern-match reliably and are fine in Tier 1–2. In **Tier 3 / production-grammar** output, switch to behavior language — `wide-latitude cinema capture`, `color-negative daylight film rendition` — and never mix the two approaches in one prompt.)

### Layer 3 — lens behavior (pick one or two)
`subtle chromatic aberration near frame edges` · `anamorphic lens flare, blue streak across highlights` · `lens breathing on focus pulls` · `noticeable focus breathing` · `sharp but imperfect focus` · `motion blur on fast actions` · `dust on lens catching backlight` · `wide-angle lens (strong distortion)` for POV · `long lens compression` for telephoto.

### Layer 4 — skin and material truth (kills the plastic look)
`visible skin pores, peach fuzz on cheeks` · `subsurface scattering in earlobes and nostrils` · `flyaway hairs catching rim light, strand-level detail not helmet hair` · `fabric weave visible, natural creases and wrinkles, not steam-pressed` · `slight oil sheen on T-zone, real human asymmetry` · `weathered hands, visible knuckle lines, slight tremor`. (In Tier 3, pair these with the per-zone specular kill + flattering ceiling from the Capture Realism engine.)

### Layer 5 — atmosphere as a participant
Empty air looks fake. `dust motes drifting through window light` · `humidity haze compressing the background` · `breath visible in cold air` · `steam curling visibly into the light shaft` · `volumetric depth haze`. Tier 3 names atmosphere in three depth registers (foreground / midground / deep-background) — see production-grammar.md.

### Layer 6 — lighting truth (one motivated source)
Lighting is the single highest-leverage element in the prompt — if you can only add one thing, add a lighting description. Seedance's default is "soft pleasant key + fill." Name a specific condition instead: `motivated only by the practical lamp on the desk — rest of the room falls into shadow` · `single window as key, no fill, deep shadow side` · `mixed color temperature — tungsten interior, daylight through window, no white-balance correction` · `overcast soft top light, flat documentary lighting` · `sodium-vapor orange on one side, blue moonlight on the other, hard color contrast` · `harsh single-source overhead, deep dramatic shadows`.

### Layer 7 — human-operator camera grammar
Realism dies when the camera floats like a drone. Tie movement to a body: `handheld with organic shake, not stabilized — micro corrections as the operator breathes` · `slight bob from walking, footsteps visible in the motion` · `operator adjusting framing mid-shot — small reframe right` · `gimbal walk but with a real subtle vertical bounce` · `tripod locked-off, but a single micro-bump as someone passes the cable`. **Avoid** `smooth glide`, `floating`, `effortless tracking` unless you want video-game smoothness; replace with `motivated`, `organic`, `tied to the operator's feet`.

### The closing realism stack — Tier 3 only
Tier 1/2 get a single line (`Native iPhone look, real skin texture` or `35mm film look, natural imperfections, no 3D, no cartoon, no VFX`). For Tier-3 renders, the production string converges on:

> *cinematic lighting, photorealistic, grounded realism, strong 35mm film look, heavy film grain, sharp but imperfect focus, noticeable focus breathing, motion blur on fast actions, halation on highlights, soft highlight rolloff, slightly desaturated tones, practical VFX feel, minimal CGI look, natural imperfections, subtle chromatic aberration near frame edges, no 3D, no cartoon, no VFX.*

(In ten-block production output this lives in the Capture Realism + Camera Capture blocks, behavior-worded — not as a brand stack.)

---

## Phone-look prompts (UGC / Reels / "shot on iPhone")

Phone realism is a *different* formula from cinematic. Lead with the device, then push toward casual imperfection. Do not borrow the cinematic stack — phones are flat, compressed, casually framed.

**Opener template:**
> *Vertical 9:16 iPhone 15 Pro handheld footage, [subject + action]. Auto-focus briefly hunting before locking, slight overexposure clipping on bright sources, native iPhone color science (slightly warm, slightly saturated), no LUT, no color grade. Subject framed slightly off-center the way someone holding a phone one-handed would frame it. Camera shake tied to the operator's breathing and footsteps. [diegetic audio cues]. No film emulation, no anamorphic, no cinematic grade.*

**Phone-specific tells:** `auto-exposure adjusting mid-shot` / `auto-focus pulse before locking` · `slight rolling-shutter wobble on quick pans` · `compressed dynamic range — bright windows blow out, shadows crush` · `one-handed framing, not perfectly centered` · `casual reframe mid-shot` · `native phone color, no LUT, no grade`.

**Lo-fi authenticity:** 2010s → `iPhone 6 video quality, soft sharpness, muddy shadows, mono speaker audio character, lower-bitrate compression artifacts in dark areas`. 2000s → `DV camcorder 480p, interlaced lines, blown-out highlights, date stamp lower-right, mini-DV tape noise`.

**Switch off phone-look** the moment the brief is cinematic — phone terms fight 35mm grain instructions and produce a muddy hybrid. Pick one mode and commit.

---

## Camera / lens / lighting vocabulary that reliably triggers

**Camera movements (one primary per shot):** `slow dolly in`, `dolly out`, `quick pan left`, `pan right`, `tracking shot (left to right)`, `tilt down/up`, `pull back reveal`, `arc shot / orbit`, `Steadicam walk`, `crane up`, `jib up`, `handheld with slight organic shake`, `locked-off`, `whip pan`, `rack focus from background to subject`. Compound moves: name the primary, then a secondary connector (`camera low tracking shot then subtle rise`). Never chain `push-in then pan then orbit then zoom` — it confuses the model.

**The 8 official camera moves Seedance is trained on:** push-in (dolly in), pull-out, pan, tracking/follow, orbit/arc, aerial/drone, handheld, fixed/locked-off.

**Rhythm vocabulary, NOT technical specs.** Seedance understands rhythm words: ✅ `slow, smooth, stable, gradual, gentle, controlled, dynamic, swift`. ❌ `24fps, f/2.8, ISO 800, 85mm, shutter 1/50`. "Describe the rhythm as if talking to an editor." Lens cues as buckets (`wide / normal / telephoto`), not exact mm — *except* in Tier-3 Camera Capture where a named focal length (40/55/75/100mm) is part of the behavior string.

**Shot types:** `extreme close-up (ECU)`, `close-up (CU)`, `medium close-up (MCU)`, `medium shot (MS)`, `wide shot (WS)`, `establishing shot`, `over-the-shoulder (OTS)`, `two-shot`, `point-of-view (POV)`.

**Lens / focus:** `shallow depth of field`, `deep focus`, `rack focus (foreground to background)`, `anamorphic lens flare`, `long-lens compression`, `wide-angle distortion`, `macro lens`, `tilt-shift`.

**Lighting:** `motivated lighting from a practical source`, `hard rim light`, `low-key`, `high-key`, `silhouette against background light`, `golden hour`, `practical tungsten`, `hard side-lighting`, `motivated neon`, `bounce fill`, `soft natural window light`, `dramatic backlighting`, `chiaroscuro`, `even overcast diffused`, `warm candlelight flickering`.

**Color / texture / atmosphere:** `color grade: teal and orange`, `bleach bypass`, `desaturated`, `high-contrast`, `cool blue tones`, `amber-tinted`, `35mm film grain`, `16mm film grain`, `fog`, `rain`, `dust particles`, `heat haze`, `halation around highlights`, `volumetric depth haze`.

**Tone:** `tense`, `melancholic`, `urgent`, `serene`, `documentary-style`, `intimate`, `observational`.

---

## Negative prompting — the `avoid X` pattern

**There is no separate negative-prompt field** — it's all one text box, and inline `avoid…`/`no…` phrases are honored *to a degree*. Seedance responds better to affirmative direction than to negative stacks. **Cap negatives at 3 per prompt** (5 absolute max on a dense Tier-3 render), chosen for the actual risk of the shot. Ten avoid-clauses dilute each other and burn word budget; saying the camera is locked once beats saying it three ways (`locked-off` alone, not `locked-off` + `avoid camera drift` + `avoid jitter`).

**The negative menu (pick ≤3 by risk):** `avoid jitter` (fast/handheld) · `avoid bent limbs` (character action) · `avoid temporal flicker` (long clips) · `avoid identity drift` (character across cuts) · `avoid plastic skin` (realism close-ups) · `avoid chaotic composition` (busy scenes).

**Realism-specific:** prefer the positive form first (`real skin texture, visible pores`); add at most 2–3 of these only when a prior render actually showed the artifact: `glossy plastic skin · airbrushed look · oversaturated commercial color · smooth airless camera glide · beauty-filter sheen · generic AI aesthetic`. WaveSpeed testing found negatives are respected *more strictly* for identity holds (`avoid dramatic head turns, avoid hair lift`).

### Dangerous keywords that LOWER quality (the antislop table)
These words sound good and degrade output:

| Avoid | Why | Replace with |
|---|---|---|
| `fast` (unqualified) | Combines with fast cuts + busy scene → jitter | One fast element only: `subject moves fast, camera holds steady` |
| `cinematic` alone | Too vague | `cinematic film tone, 35mm, warm` |
| `epic` | Model doesn't know what it means | Specific scale: `wide low-angle, towering, dust kicking up` |
| `amazing` / `beautiful` / `stunning` | No visual guidance | Specific lighting + composition |
| `lots of movement` | Causes jitter | One specific named motion |
| `high quality` / `4K` (no context) | Empty signifier | Capture medium + lens + lighting |

Also ban: *breathtaking, mesmerizing, cinematic masterpiece, masterfully, seamlessly, effortlessly, a symphony of, visual feast, visually striking.*

**The "fast" rule.** Fast camera + fast cuts + busy scene = guaranteed artifacts. If you need pace, make **only one** element fast — either the subject, or the camera, or the cuts. Never two.

---

## Speed-ramping & inline VFX

**Speed-ramp syntax** — CAPS inline signals a pacing change (read as a directive, not on-screen text):
> *…the blade arcs through the air, **RAMPS TO SLOW MOTION** as the strand of hair catches the edge and separates, **SNAPS BACK** to full speed as she drives her elbow into his chest.*

**Inline VFX brackets** — specify a power/effect without breaking the action line:
> *…fractal lightning veins explode across both forearms [VFX: branching electric circuits pulsing with white-blue current, sparks jumping between fingers], the ground trembles…*

Keep bracket content to one clause. Works for powers, energy, particles, magic, sci-fi tech, body horror.


<!-- ═══════ FILE: seedance-director/references/camera-depth-volumetrics.md ═══════ -->

# Camera Physics, Framing, Depth & Volumetrics — how real cameras act, and how to write it for Seedance 2.0

Companion to `realism-and-camera.md` (the anti-plastic stack and vocabulary) and `editing-and-cutting.md` §10 (composition grammar: thirds, lead room, frame-in-frame, size↔emotion). This file goes deeper on four things: how a *physical* camera actually behaves, how framing and composition work when the cinematographer is a language model, how to engineer depth into a frame, and how volumetric light actually works. Applies to generation and to the edits layer's integration pass alike.

## 1. Real cameras have mass, and operators have bodies

The AI tell in camera motion is *weightlessness* — moves that start and stop instantly, float without inertia, and never err. A real camera obeys physics:

- **Inertia:** a real move eases in and eases out. Write `the camera settles into a static medium` / `the dolly eases to a stop`, never instant starts. A move that begins at full speed reads as CG.
- **Operator physiology:** handheld shake is not noise — it's breath (slow ~cyclical sway), heartbeat, step cadence (bob at walking rhythm on follow shots), and micro-corrections after reframing (a real operator slightly overshoots, then corrects). The trigger phrase that captures all of it: `handheld with organic shake tied to the operator's breath`; on walking shots add `bob at step cadence`.
- **The reframe correction:** when a subject moves, a human operator lags a beat, then catches up — `the camera catches up to her move a half-beat late`. Perfectly prescient framing is a machine tell.
- **Focus behaves like a human pulled it:** racks land with a tiny settle; in doc/handheld registers a brief focus hunt is realism (`focus hunts for a beat before landing on her face`). Never on Tier-3 hero product shots.
- **Exposure adapts:** moving from dark interior to bright exterior, real cameras (and eyes) take a beat — `exposure adjusts over a beat as she steps into daylight, highlights blooming then recovering`.
- **Lens artifacts are caused, not sprinkled:** flare only when a source is in or near frame; halation blooms around bright highlights on film; vignette and edge softness at wide apertures; slight barrel distortion on ultra-wides. Ask for the *cause* (`low sun just out of frame top-left, gentle flare`) not the decal (`add lens flare`).

### Mount signatures (pick one, write its physics)

| Mount | Signature to write | Feels like |
|---|---|---|
| Locked tripod | `locked-off, rock still; only wind moves in frame` | Surveillance, patience, dread |
| Tripod + head | `slow pan on a fluid head, constant speed, eased stop` | Deliberate, observational |
| Dolly / slider | `linear dolly glide, mechanically smooth, eased in and out` | Premium, intentional |
| Gimbal | `smooth gimbal float with a slight pendulum settle after direction changes` | Modern, clean follow |
| Shoulder / handheld | `shoulder-carried bob at step rate, breath sway, micro-corrections` | Documentary, urgency |
| Drone | `aerial drift with gentle yaw corrections, slow altitude change` | Scale, geography |
| Crash / mounted | `hard-mounted, vibrating with the vehicle, horizon locked to the chassis` | Speed, POV mechanics |

One mount per shot. The mount *is* the stability instruction — Seedance stops inventing micro-moves when told `tripod stable`, and adds shake *on purpose* when told `handheld`.

## 2. The official camera grammar (what Seedance actually parses)

From the official guide and validated cheat sheets — the camera line follows:

```
Camera: [move] + [speed] + [subject lock] + [stability/mount]
```
e.g. `Camera: slow dolly in toward the watch face, maintain subject size until the final push, smooth gimbal.`

- **Eight supported move families:** push-in/dolly-in · pull-out/dolly-out · pan (lateral) · tracking/follow · orbit/arc · aerial/drone · handheld · fixed/locked-off.
- **One primary move; one optional secondary flavor** written as a sequence, not a stack: ✅ `low tracking shot, then a subtle rise` ❌ `pan + zoom + dolly + handheld` (soup).
- **Speed ladder** (rhythm words, never tech specs in the movement line): `imperceptible / barely` → `slow, gentle, gradual` → `smooth, controlled` → `dynamic, swift` (use the last sparingly; unqualified `fast` is the single most quality-degrading keyword). Capture specs (24fps, 180° shutter, grain) belong in the closing look line, not the movement line.
- **Give pans/tilts a destination:** `pan reveals the espresso machine at the end of the move` / `tilt up, start on the entrance, end on the glass facade`. Undirected moves wander.
- **Anti-gremlin patches** (validated fixes):
  - Jitter → `steady motion, tripod stable, slow` + reduce scene complexity (fast camera + fast subject + busy scene = wobble).
  - Warping lines → `straight vertical lines, architectural framing, 35mm lens, minimal distortion`; avoid aggressive handheld on interiors.
  - Zoom creep → `no zoom, maintain subject size in frame`, and keep exactly one move (zoom sneaks in when prompts crowd).

## 2b. Framing & composition when the cinematographer is a model

Film composition rules still apply (thirds, lead room, frame-in-frame, size↔emotion — `editing-and-cutting.md` §10), but an AI frames from *language*, which changes how you ask:

### The shot contract comes first

State the structural facts at the very top of the prompt — shot count, total duration, aspect ratio, and single-shot vs montage (`One continuous shot…` / `Montage, multi-shot, don't use one camera angle or single cut…`). This is the first-20-words rule applied to framing: composition instructions buried late get overridden by the model's defaults. In multi-shot prompts, give **every numbered shot its own framing label**: `Shot 1: Medium shot… Shot 2: Wide shot… Shot 5: Wide low-angle…` — a shot without a stated size gets whatever the model feels like.

### The shot-size ladder, with AI reliability

| Size | What it means emotionally | AI reliability note |
|---|---|---|
| Extreme wide | Isolation, scale, geography | Reliable; subject identity is lost at this size — fine for silhouettes, not for face continuity |
| Wide | Context, blocking, full body | Reliable; the workhorse for action and creature scale |
| Medium (waist-up) | Neutral, conversational | **The model's safe zone** — best identity + motion stability |
| Medium close-up (chest-up) | Engagement, dialogue | Reliable; the lip-sync sweet spot |
| Close-up | Intimacy, intensity | Good at high res; faces warp at low res — finalize at max |
| Extreme close-up (eyes, hands, product detail) | Maximum intensity | Riskiest frame in the system — hands especially; use inserts of objects, not fingers, when possible |

Escalate size with emotion (push closer as temperature rises), but plan the risky sizes as their own short shots rather than drifting into them mid-move.

### Angle is power — say it in plain words

`low angle looking up` = dominance, scale (the default for creature/tower reveals: `shot from a low angle, the man tiny beneath them`); `high angle looking down` = vulnerability, overview; `eye level` = neutral, documentary; `over-the-shoulder` = relationship + instant depth (a foreground shoulder is a free first register); Dutch/canted = unease — use sparingly, it amplifies warping on architecture. POV is its own contract: lock it by stating what the camera is **not** doing — `no cuts, no zoom, natural head movement` — without the negative instruction the model breaks perspective and cuts away.

### Composition habits that counter the model's defaults

- **The model centers by default.** Ask for placement explicitly: `framed on the left third, gazing into the open right two-thirds`. Tier 3 goes further — Frame Map with percentages: `x=50%, y=55%, occupying 60% of frame height`. Numbers beat adjectives ("large in frame" drifts; "60% of frame height" holds).
- **Declare negative space as content**, or the model fills it with clutter: `the upper third holds only sky and fog as negative space`.
- **State the horizon:** `level horizon` on wides — unstated horizons drift and tilt mid-shot.
- **Anchor occupancy over time.** In a moving shot, say the framing at the open *and* the close: `opens tight at 70% frame height, settles into a clean medium by 5s`. Unstated end-framing is where zoom creep lives.
- **Blocking is composition over time.** Where characters stand IS the frame; re-anchor positions and facing after every cut, keep entrances/exits to stated frame edges, and use converging/diverging movement for meaning (`editing-and-cutting.md` §3).
- **Silhouette test for staging:** if the action wouldn't read in silhouette (fighter separation, gesture clarity, creature outline), the composition isn't staged yet — separate subjects in depth or against contrasting background values.

## 3. Depth engineering — making a flat frame deep

The model composes in 2D unless the prompt builds 3D. Four tools, use two or three per shot:

1. **Three registers, always.** Foreground texture element (something within arm's reach of the lens — a shoulder, foliage, a railing, rain on glass) → midground subject → far register swallowed by atmosphere. A frame with no foreground element is a flat frame. `Frame through the rain-beaded window; she sits mid-room; the street beyond dissolves in haze.`
2. **Parallax is the depth engine on any moving camera.** Near things cross frame fast, far things barely move: `near trunks whip past; the ridge line barely drifts.` If nothing in the frame moves at a different rate, the shot reads as a painting on rails. (In edits: added environments MUST inherit the source camera's parallax — a static insert behind a moving camera is the #1 pasted-in tell.)
3. **Aerial perspective is physics, write it as physics:** with distance, contrast drops, saturation drops, edges soften, and color shifts cooler toward the sky's hue. `The far ranks go softer, desaturated, lower-contrast, cooled toward the haze.` This one line does more anti-CG work than any quality keyword.
4. **DOF is a named decision, not a default.** `shallow depth of field, background melting to soft bokeh` (intimacy, product) vs `deep focus, sharp front to back` (geography, ensembles, Atmosphere-archetype plates). Most prompts skip it; both are big levers. Occlusion beats bokeh for realism: letting a foreground object briefly cross and block the subject proves the space is 3D.

## 4. Volumetrics — light you can see needs three ingredients

Volumetric light (god rays, shafts, glowing haze) exists only when all three are present. Write all three, not the effect name:

1. **A strong source** — low sun, a window, one streetlight, a projector.
2. **An occluder that breaks the light** — canopy gaps, blinds, a window frame, smoke-stained rafters, a doorway. No occluder = glow, not rays.
3. **A medium that scatters it** — name the particulate: dust motes, humidity, smoke, fog, pollen, sea spray, breath in cold air, kicked-up flour. Empty air scatters nothing.

`Low sun breaks through the canopy gaps in warm volumetric shafts, catching drifting mist and suspended pollen` — source, occluder, medium, all present.

- **Backlight reveals atmosphere.** Rays, rain, dust, and breath read 10x stronger lit from behind or the side than from the front. If the volumetrics matter, put the source behind the subject: `backlit rim, the drizzle visible as bright streaks against the dark doorway.`
- **Atmosphere must move.** Static haze reads as a filter. Give it drift, a direction, and a driver: `fog drifts slowly screen-right to left on the sea wind`, `steam rises off the cup and curls in the window light`.
- **Density by register** (pairs with §3): thin near the lens, readable at midground, thick at distance — this is the three-depth atmosphere in `production-grammar.md`, stated as physics.
- **The restraint rule.** One atmosphere system per shot. Stacking `dust motes + god rays + light leaks + heavy fog + film grain + 8k` is prompt overloading — the output turns over-processed and chaotic. Pick the one medium the scene would really have, let the light and the register gradient do the rest.
- **Volumetrics interact:** rays dim and diffuse as the medium thickens; a figure crossing a shaft blocks it and glows at the rim; a car's headlights carve cones only in fog/rain. Writing one such interaction (`her shadow cuts the light shaft as she passes`) proves the light is in the room, not painted on.

## 5. Where each element lives in the prompt

| Element | Lives in |
|---|---|
| Move + speed + subject lock + mount | The camera line (Tier 1: one clause; Tier 3: Movement block) |
| Focus/exposure behavior, operator physiology | Camera line or Camera Capture block |
| Three registers, foreground element, occlusion | Frame Map / Static Description / the environment sentence |
| Aerial perspective, atmosphere density gradient | Capture Realism block (Tier 3) or the closing look line (Tier 1) |
| Volumetric source + occluder + medium | Environment/lighting line — never as bare effect names |
| Capture specs (film stock, grain, fps, shutter) | Closing look line / Camera Capture only |

## Sources

- Volcengine/ByteDance official Seedance 2.0 prompt guide (6-step formula, 8 camera families, rhythm-not-specs rule, speed ladder, negative checklist): volcengine.com/docs/82379/2222480 — interpreted via help.apiyi.com/en/seedance-2-0-prompt-guide-video-generation-camera-style-tips-en.html
- PromeAI — Seedance 2.0 Camera Movement Cheat Sheet (Camera: syntax, mount stability language, jitter/warp/zoom troubleshooting): promeai.pro/blog/seedance-2-0-camera-movement-cheat-sheet/
- Hailuo AI — dust & light motes guide; FreeAIPromptMaker — volumetric lighting for AI art (particulate media, scattering, prompt-overloading warning); standard cinematography references on aerial perspective and volumetric lighting.
- Higgsfield — Seedance 2.0 Complete Prompting Guide (shot-contract-first rule, per-shot framing labels, POV negative-instruction lock, low-angle scale staging): higgsfield.ai/blog/seedance-prompting-guide


<!-- ═══════ FILE: seedance-director/references/scene-craft.md ═══════ -->

# Scene Craft — idea → structure, reading references, archetypes, cut rules, the summary block

This is the translation layer: how to turn a raw idea or a reference image into a structured shot the model can execute. Section numbers are stable — the SKILL.md cites **§11** for the plain-language summary block.

---

## 1. Reading a reference image (extract by description, never by name)

When the user uploads an image, read it for what it gives you and write only what the model can't infer. Capture, silently:

- **Color & grade:** dominant palette, accent colors, warm/cool bias, contrast structure (lifted shadows vs crushed blacks), saturation level. Name it as a grade ("teal-amber, lifted blacks").
- **Light:** direction (where the key comes from), quality (hard/soft), temperature (tungsten/daylight/mixed), motivation (window, practical, sun), and what's in shadow.
- **Lens character:** apparent focal length (wide distortion vs long compression), depth of field, any flare/bloom/aberration.
- **Emotion / energy:** what the body and face physically do — read it as physiology, not a label.
- **Per character:** hair, makeup finish, wardrobe top-to-bottom, jewelry/accessories, body markers, pose — only what's visible.
- **Per environment:** location type, architecture/materials, time of day, weather, set dressing, atmosphere.

Then **trust the image** for everything it carries. In the prompt, describe only motion, emotion, camera, state-changes (damp, torn, dusty), and what stays unchanged. Never re-narrate "long brunette hair, grey tee…" that the image already shows — it wastes budget and creates text-vs-pixels drift.

## 2. The five directing principles

1. **Energy before geometry.** Decide what the moment *is* dramatically (Scene & Mood) before you decide where things sit (Frame Map).
2. **One main idea per shot** — one dominant action, one camera strategy, one lighting motivation. Extra ideas become extra shots.
3. **In medias res** — the scene is already in progress unless the user says "starts with…/ends with…". Open mid-action.
4. **Show, don't label** — emotion as physiology ("jaw clenches, a 0.3s freeze"), never "looks angry."
5. **Physics, not appearance** — feed the motion prior interactions it can simulate ("tires smoke as it drifts 90°"), not abstractions ("car turns dramatically").

## 3. The scene-archetype router (the structure layer)

The archetype sets camera behavior, spatial logic, and what changes over time. Pick one (orthogonal to the cinema mode, which sets the look).

**Action archetypes:**
- **Pursuit** — distance between two subjects closes or opens. The whole shot is about the gap. Camera tracks the gap, not a single body. *Beat logic:* establish distance → distance changes → resolution (caught / escaped).
- **Duel** — dominance alternates **every beat**; never one-sided. If A lands a hit, B answers. *Beat logic:* A presses → B answers → reversal → resolution. A one-sided duel reads as a beatdown, not a duel.
- **Impact** — slow build → fast hit → slow aftermath. The contrast in pacing *is* the impact. Use a speed-ramp on the hit.

**General archetypes:**
- **Journey** — position in space changes (a walk, a drive, a descent). Camera travels with or reveals the path.
- **Atmosphere** — nothing changes; mood IS the content. Almost no character motion; the air, light, and environment do the work. Locked or very slow push.
- **Reveal** — hidden becomes visible. Withhold, then disclose (a pull-back reveal, a rack focus, a turn).

**Dialogue archetypes:**
- **Confrontation** — both push; dominance trades. OTS or two-shot; cut on the line that turns the power.
- **Interrogation** — one extracts, one resists. Asymmetric framing (one favored, one pinned).
- **Negotiation** — balanced; both need something. Symmetric two-shot, equal headroom.

## 4. Decision trees

- **Is it one continuous action or several events?** One → single shot (Tier 1). Several → multi-shot (Tier 2/3 with cuts).
- **Does identity have to hold across cuts?** Yes → lock with a reference + one consistent noun/tag; generate in checkpoints. No → text-only is fine.
- **Is the camera a participant (POV) or an observer?** Participant → locked-perspective trick ("no cuts, no zoom, natural head movement"). Observer → pick a cinema mode's movement.
- **Does a beat need exact timing?** Yes (3+ beats on a 10–15s clip) → timeline prompting. No → flowing prose. Never timestamp-grid a 4–8s single shot.

## 5. Engine rendering constraints (design around these)

- **Off-screen = nonexistent.** Show a state change on camera before referencing it. Don't choreograph an exit + re-entry in one continuous shot (an exit-frame reads as an implicit cut).
- **Track ≤3 characters** across cuts; more and identity collapses.
- **Avoid a subject's mirror reflection** — Seedance breaks geometry rendering a mirror image of a subject (wrong content, slight delay). Flat wet-puddle/pavement reflections are fine and even a strength. Face the camera, not the mirror; plan a rescue cut if a mirror is unavoidable.
- **Readable text garbles** — two-pass it (clean render → text in post).
- **Extreme hand close-ups drift** — frame hands at medium distance.
- **Fast complex motion warps** — use medium-paced beats ("jogs three steps and stops"), not "sprints chaotically."
- **One fast element only** — subject OR camera OR cuts, never two.

## 6. Cut rules (continuity hygiene for this engine)

- **Double contrast:** every cut changes *both* shot size *and* camera character. A cut from a wide locked-off to a wide locked-off reads as a glitch.
- **Re-anchor after every cut:** restate who's where and which way they face (hold the 180° line). For Seedance this is *reliability hygiene*, not just aesthetics — the model loses positions across cuts otherwise.
- **Cut on the action; land the eye where it already rests** — cut on the peak of a motion (the moment of contact), and open the next shot where the eye was looking (center-frame in chaos, or on a color/motion beacon).
- **Inserts** (a detail cutaway) buy you a clean transition and cover a continuity jump — use one to bridge two shots that won't quite match.
- Full *why* and the reliability table → `editing-and-cutting.md`.

## 7. Dialogue compression

Spoken lines must be short to lip-sync cleanly. **5–10 words per line.** Cut filler; keep the turn that matters. If a character must say a lot, split it across beats/shots (and likely across two generations). Put the line in `"double quotes"`, name the language if not English, and don't add head-movement during the spoken beat. Emotion/pacing cue before the line helps: `"flat, almost bored: I'm not waiting anymore."`

## 8. Building the plan (what feeds Step 1 of the workflow)

From the brief, decide and surface: tier (from shot count + duration), cinema mode (the look), scene archetype (the structure), references (role lines), camera (lens + one move), runtime + aspect. Make the craft calls yourself; only ask the director about idea/who/where/how-long.

## 9. Mode × archetype quick pairings

Streets at night, someone waiting → **M1 Narrative + Atmosphere**. Two fighters → **M3 Action + Duel**. Product on marble → **M2 Studio + Reveal**. Concert drop → **M4 Performance + Impact**. Abandoned city at dawn → **M5 Atmospheric + Atmosphere**. Car chase → **M3 Action + Pursuit**. Interview/confession → **M1 Narrative + Interrogation/Confrontation**.

## 10. Common idea-translation traps

"Make it epic/cinematic/amazing" → translate to concrete lighting + lens + composition (the words themselves degrade output). "Lots happening" → split into shots. "A person looking sad" → physiology. "Camera spins around them dancing" → separate the two motions. "Photorealistic" → capture medium + `no 3D, no cartoon, no VFX`.

---

## 11. The plain-language summary block (deliver with every prompt)

So the director can react without reading the prompt body, append a short plain-language summary after the prompt. Keep it to a few lines, no jargon:

```
What this makes:
- The shot: [one sentence — who, doing what, where, how it feels]
- Look: [plain words — e.g. "warm film, handheld, golden light"]
- Camera: [plain words — e.g. "starts wide, slowly pushes in"]
- Sound: [what you'll hear]
- Length / shape: [e.g. "8 seconds, vertical, one continuous shot"]
- To change it, just tell me: [e.g. "warmer / closer / add a line of dialogue"]
```

This is the director's handle on the prompt — it invites a one-word change ("warmer", "closer", "more rain") that becomes a single-variable re-roll. Always offer it; never make the user parse the prompt body to know what they're getting.


<!-- ═══════ FILE: seedance-director/references/surfaces-and-use-cases.md ═══════ -->

# Surfaces & Use-Cases — read at Step 0

Confirm the surface first (it sets the hard caps), then let the matching use-case playbook pre-fill the plan defaults.

---

## The imagine.art Seedance 2.0 surface (the default)

imagine.art exposes Seedance 2.0 at `imagine.art/apps/seedance-2.0` and the main `/video` generator. Treat these as the operative limits unless the user is on a different surface:

- **Resolution: up to 1080p.** 480p is available. **Iterate at 480p, finalize at 1080p.** (Native 2K exists on the Standard/"Pro" tier on some surfaces — e.g. Dreamina Studio plans — but imagine.art's ceiling is 1080p; don't promise 2K here.)
- **Duration: up to 15 seconds.** Plan beats accordingly: 4–6s = one beat; 6–10s = 2–3 beats; 10–15s = 3–6 beats. To go past 15s, render segments and chain them (video-extend / Track Completion — see `recipes-and-operations.md` §7).
- **Aspect ratios:** 16:9, 9:16, 1:1 confirmed. **Do not promise 21:9 / 4:3 / 3:4 on this surface** without confirming — those appear on older Seedance versions, not the 2.0 app.
- **Frame rate:** native 24fps. "Up to 60fps" is surface marketing — don't rely on it.
- **Inputs:** full 12-asset multimodal (9 images + 3 videos ≤15s + 3 audio ≤15s) with `@AssetName` / `@image1` tagging. Preset camera moves can be dragged into the interface instead of typed. Multi-shot, native audio, lip-sync, and V2V editing are all surfaced.
- **Real-face block** is inherited from the model — identifiable real faces in reference images/videos are rejected, copyrighted characters are blocked, and every output carries a C2PA + invisible watermark. For a "specific person," use an AI-generated fictional portrait (it passes the filter).
- **Generation time:** ~60–90 s. **Pricing:** credit-based (~$10/mo tier, ~3,500+ credits). Global availability.

### Seed exposure & the no-seed batch protocol

imagine.art exposes a custom **seed in Advanced Settings** on Seedance surfaces (documented for 1.0; very likely present on 2.0 but not screenshot-confirmed). **If the seed is visible:** capture it on a good render and reuse it with a one-variable edit to isolate the change. **If the seed is NOT exposed:** you can't isolate a single variable cleanly — instead use the batch protocol:
1. Generate a **batch of 2–3 takes** of the same prompt at 480p.
2. Pick the best take; note exactly what worked and what didn't.
3. Make **one** change and run another 2–3-take batch.
4. Compare batches, not single takes — random variation between takes is large, so a single A/B is unreliable without a seed.
5. Lock the winning prompt, render the final at 1080p (run 2–3 finals and pick).

### Guidance hierarchy (whom to trust when sources conflict)

When facts disagree, weight them: **ByteDance / BytePlus / Dreamina official docs > Higgsfield prompting guide > vetted community corpora (the awesome-seedance-2-prompts repo, WaveSpeed/redreamality testing) > platform blogs (incl. imagine.art's own marketing prose).** Treat duration/resolution/fps marketing numbers as the lowest tier; treat the app's settings panel as authoritative for the surface caps.

---

## Use-case playbooks (each pre-fills the plan defaults)

Pick the playbook that matches the brief; it sets tier, mode, archetype, aspect, audio, and the realism dial.

**UGC / hook / "shot on iPhone."** Tier 1 · phone-look (not a cinema mode — see `realism-and-camera.md`) · 9:16 · 4–8s · native iPhone color, auto-exposure hunt, one-handed framing · diegetic room tone + maybe one spoken line (5–10 words, front-facing). Realism dial: phone tells, not the 35mm stack. Identity: lock with one selfie-style reference if a recurring creator.

**Product.** Tier 1–2 · **M2 Studio** · **Reveal** archetype · 1:1 or 4:3 (use 1:1 on imagine.art) · 6–8s · i2v from a clean product still (`@image1 = product, keep shape and label stable, no new text`) · pull-back or slow orbit, one move · clean motivated key + soft fill · diegetic room tone only. Keep the product label stable; don't let the model invent text.

**Narrative / dramatic.** Tier 2–3 · **M1 Narrative** · Confrontation / Interrogation / Atmosphere / Journey · 16:9 or 9:16 · 6–12s · handheld with operator breath, anamorphic character, teal-amber · one motivated light · diegetic ambient + short dialogue in quotes. The realism stack matters here — capture medium + skin truth + atmosphere.

**Action / combat / chase.** Tier 3 · **M3 Action** · Pursuit / Duel / Impact · 16:9 (or 9:16 for social) · 8–15s · handheld and shaky throughout, heavier grain, dusty haze · beat-by-beat choreography, speed-ramp the hit · diegetic impacts + SFX list. One fast element per beat; medium-paced motion to avoid warping; cut on the contact.

**ASMR / sensory / food.** Tier 1 · **M2 Studio** or **M1 Narrative** depending on setting · Atmosphere · 9:16 or 1:1 · 4–8s · macro / tight framing, slow push · soft motivated light · **audio is the point** — name the specific Foley (sizzle, crunch, pour, tap), mix priority, no music. Frame at medium distance if hands are involved (extreme hand close-ups drift).

**Atmosphere / mood plate.** Tier 1–2 · **M5 Atmospheric** · Atmosphere · 16:9 or 21:9 (if surface allows) · 6–12s · locked-off or extremely slow push, environment is the subject, palette-driven (specify hex) · heavy/medium haze in three registers · diegetic weather/ambient, often no dialogue. Almost no character motion.

**Transformation.** Tier 3 · **M3 Action** (or M1 for grounded) · Impact · 16:9 · the 6-shot escalation arc (calm → threat → transformation → aftermath) · header line + numbered shots + `Total: Ns / 6 shots / 16:9` · camera jolts on each transformation beat · diegetic SFX list. Best-performing multi-shot format; see `recipes-and-operations.md` §4.

**R2V (reference-to-video) / identity-locked.** Tier 2–3 · Universal Reference Mode · any mode · use a 3-still reference pack (straight-on / three-quarter / profile, same session, same light, neutral expression) · 5–7 identity anchors written out · generate in checkpoints (2 shots → QA → expand) · role line per `@imageN`. Remember: motion beats identity when they conflict — keep identity-critical beats free of fast head-turns and hand-across-face moments. See `recipes-and-operations.md` §8.

**Music video / dance.** Tier 2–3 · **M4 Performance** or M1 · Impact · 9:16 · upload a track as `@audio1` and beat-sync the cuts · stage color cast, streak flares, sweat sheen. Note: the audio reference is the rhythm anchor; keep it MP3, 3–8s.

---

## Surface-portability note

If the user is on a different surface (Dreamina/CapCut, Higgsfield, WaveSpeed, AtlasCloud, or the direct BytePlus API), the prompt grammar is identical — only the **caps and the seed/asset UI change**. Re-confirm duration cap, resolution ceiling, aspect options, and whether the seed is exposed before quoting any hard number. The direct overseas API was suspended Mar 15 2026 over copyright disputes, so resellers are the reliable surfaces; verify API access by region before relying on it.


<!-- ═══════ FILE: seedance-director/references/editing-and-cutting.md ═══════ -->

# Editing & Cutting — the editor's brain

This is the editor's reasoning, translated into instructions Seedance 2.0 will honor. Editing software cuts *between* renders; Seedance edits *inside* one generation — it produces a flowing multi-angle sequence, not frame-accurate hard cuts. So your job is to write the *intent* of a cut (why it works, what it's for) in language the engine respects, and to know when an effect must be achieved by rendering shots separately and stitching them in a real editor.

Use this with `production-grammar.md` (shot grammar), `realism-and-camera.md` (camera behavior vocabulary), and `recipes-and-operations.md` (stitch/V2V workflows). When a technique needs separate renders, see the reliability table at the bottom.

Two standing rules across everything below:

- **Native synced audio changes the math.** Seedance generates picture and sound jointly, including dialogue lip-sync. That makes sound-led transitions (J-cuts, L-cuts, sound bridges) unusually cheap and reliable — lean on them.
- **Re-anchor after every cut.** This engine drifts. After any angle change, restate who is where, facing which way, holding what. For Seedance this is reliability hygiene, not an aesthetic flourish — say it even when a human editor wouldn't need to.

---

## 1. Murch's Rule of Six — what a cut is *for*

Walter Murch ranks what a cut must serve, by priority weight:

| Priority | Criterion | Weight |
|---|---|---|
| 1 | **Emotion** — does the cut honor what the audience should feel? | 51% |
| 2 | **Story** — does it advance the narrative? | 23% |
| 3 | **Rhythm** — is it at the right moment, rhythmically? | 10% |
| 4 | **Eye-trace** — does it respect where the viewer is looking? | 7% |
| 5 | **Two-dimensional plane** — does it respect screen geography / the 180° line? | 5% |
| 6 | **Three-dimensional space** — is it true to the real space of the action? | 4% |

The point of the weights: when you can't satisfy all six, **sacrifice from the bottom up**. A cut that breaks 3D continuity (4%) but lands the emotion (51%) is a good cut. A cut that is spatially perfect but emotionally dead is a bad cut. Emotion plus story is 74% — get those right and small spatial errors are forgivable.

**How to write it for Seedance:** decide the dominant feeling first, then describe the moment that delivers it, *then* the angle. Lead with emotion and action; let geometry serve them. Example: "Hold on her face as the decision lands — eyes settling, jaw tightening — then the angle shifts to the door she's about to walk through." You wrote emotion (51%) and story (23%) into the instruction; the angle change is in service of those, not the reverse.

**Seedance caveat:** Murch lets you *sacrifice* 3D/2D space when emotion demands it. You should still re-anchor positions after the change — not because the aesthetics require it, but because this engine loses track of who is where. Sacrifice the *priority weight* if you must, never the *position statement*. Write the emotional cut Murch would approve, then add the spatial anchor Seedance needs.

---

## 2. Cutting on the action / cutting on the hit

A cut placed at the **peak of a motion** hides itself — the eye is busy tracking movement and doesn't register the edit. The motion started in shot A completes in shot B; continuity of action carries the viewer across the seam. In combat, the strongest cut is **on the moment of contact** — the fist landing, the blade meeting, the body hitting the ground.

Inside one Seedance generation there is no literal seam, but the principle still governs *where the angle should change*: change angle at the kinetic peak, not in a lull, so the new view feels motivated by the action.

**How to write it for Seedance:**
- "She reaches for the handle; as her hand closes on it, the view snaps to the corridor beyond." (Angle changes on the completion of the reach.)
- Combat: "The punch travels; at the instant of impact the angle cuts tight to the recoiling head, then the body falls." Put the angle change *on the hit*, never before or after.
- Phrase it as one continuous motion split across two views — "the motion begins wide, completes close" — so the engine treats it as a single action seen from two angles rather than two disconnected events.

**Takeaway:** name the kinetic peak and tie the angle change to it. "On contact," "as it lands," "at the top of the jump" are the load-bearing words.

---

## 3. Screen direction as meaning

Direction of movement *is* narrative. Two subjects on **converging paths** read as collision, confrontation, meeting; **diverging paths** read as escape, separation, loss. The **180° line** (the axis of action) keeps screen geography stable: stay on one side and a character who faces frame-right keeps facing frame-right, so cross-cutting between two people preserves the sense that they face each other. Cross the line and they appear to face the same way — spatial confusion.

**How to write it for Seedance:**
- Collision: "Two runners enter from opposite edges, closing on the center of frame." (Convergence = inevitability.)
- Escape: "She moves frame-left toward the exit; the pursuer is held frame-right, the gap widening." (Divergence = getting away.)
- Confrontation across a cut: "He faces frame-right; she faces frame-left — they hold the eyeline across the angle change." Restate the facing directions *every* time the angle changes; that is how you keep the 180° line on an engine that has no concept of it.

**Takeaway:** decide what the geometry means (toward = together, apart = away), then lock facing direction with explicit "frame-left / frame-right" anchors after each angle change. This is eye-trace and the 2D plane (Murch #4 and #5) made literal.

---

## 4. The double-contrast rule

A clean cut changes **both** shot size **and** camera character at once. Cutting from a wide static shot to a closer wide static shot reads as a jump cut (a stutter); cutting from a wide static shot to a close *moving* shot reads as a deliberate change. Vary two axes — size (wide → medium → close) and behavior (locked-off → drifting → handheld → pushing) — so each new view declares itself as a new view.

**How to write it for Seedance:**
- Weak (one axis): "Wide shot of the kitchen, then a slightly closer shot of the kitchen."
- Strong (two axes): "A still wide of the kitchen, then a close handheld push on her hands working the dough." Size changed (wide → close) *and* character changed (still → handheld push).
- Describe cameras by **behavior**, not brand: "locked-off," "slow drift," "handheld breath," "steady push-in," "whip to," "crane lift." (See `realism-and-camera.md`.)

**Takeaway:** when you change angle, change *two things* — how big and how the camera behaves. If only the size changes, the engine may render a stutter rather than a cut.

---

## 5. J-cuts, L-cuts, and sound bridges — high-leverage on Seedance

Audio and picture rarely cut at the same instant in mature editing. A **J-cut**: the sound of the next scene arrives *before* its picture (you hear the ocean while still on the bedroom). An **L-cut**: the sound of the current scene lingers *over* the next picture (a character's voice continues as we cut to who's listening). A **sound bridge** is the general case: audio spanning a visual transition, smoothing it and steering meaning.

**This is the single most underused, most reliable advanced move on Seedance** precisely because the model generates synced audio natively. The audio layer is real, joint, and lip-synced — so audio-led transitions cost you almost nothing and pay off in polish.

**How to write it for Seedance:**
- J-cut: "We hear the crowd roar and the announcer's voice a beat before the stadium appears; the picture is still on the locker room when the sound arrives."
- L-cut: "Her line continues — '…I never meant for this' — as the view moves to his stunned face; her voice finishes over his reaction."
- Sound bridge: "A single sustained tone carries across the change from the lab to the street; the visual world changes, the sound does not."
- Diegetic glue: "The kettle's whistle rises through the angle change and only cuts out once we're outside." Persistent ambience across the seam binds two views into one continuous moment.

**Takeaway:** lead or lag the picture with sound, on purpose. Say *when* the audio starts relative to the image ("a beat before," "continues over," "carries across"). Because audio is native, these read as intended, not accidental — and a long sound bridge across a *real* edit (two stitched clips) is even more powerful; layer matching audio in your editor across the cut.

---

## 6. Intercutting / parallel action (cross-cutting)

Cross-cutting alternates between two threads (the bomb and the hero racing to it; two ends of a phone call) to build tension or draw a thematic parallel. Meaning comes from the alternation itself — the audience assembles a single drama from two locations.

**Seedance limit:** true intercutting wants *clean, repeated, hard* returns to each thread — A, B, A, B — and that is exactly what a single generation does *not* do well. Within one clip you can suggest parallelism (two locations, a connecting sound, escalating pace in both), but the engine tends to flow and blend rather than snap back and forth.

**How to write it for Seedance (suggestion, within one clip):**
- "Cut between the runner pounding the platform and the train doors beginning to close, the rhythm tightening with each return." (The engine will *gesture* at this, not nail the A/B/A/B.)
- Bind the threads with a shared sound: "the same clock ticking is heard over both spaces."

**How to do it properly (stitch):** render each thread as its own clip, keep a consistent connective audio element (clock, ringtone, heartbeat), then interleave the clips in an editor and accelerate the cutting toward the convergence. Cross-cutting is a *between-clips* technique; treat it as a stitch job, not a prompt.

**Takeaway:** for real parallel action, render threads separately and intercut in post. Within a single prompt, you can only imply it — use a shared sound and a rising shared tempo.

---

## 7. Cadence & shot length — ramp, don't jolt

Pace is felt as **Average Shot Length (ASL)** — the mean seconds per shot. Genres cluster:

| Register | Typical ASL | Feel |
|---|---|---|
| Dialogue / drama / contemplative | ~6–12s | room to breathe, performance-led |
| General narrative | ~3–6s | standard storytelling rhythm |
| Action / chase / combat | ~1.5–4s | urgency, fragmentation |
| Montage / climax peak | <1.5s | overwhelm, acceleration |

The governing instinct: **ramp, don't jolt.** Pace should accelerate *toward* a climax and decompress after it; a sudden lurch from slow to frantic (or back) without a ramp reads as a mistake. Build the curve.

**How to write it for Seedance:**
- Within a clip you control pace through *how often the angle changes* and *how fast the action moves*. Drama: "long, unhurried takes; the camera lingers, angles change rarely." Action: "rapid angle changes, each beat shorter than the last, building to the impact."
- Across a stitched sequence, plan ASL deliberately: open with longer shots (set the world), shorten as tension rises, hit the climax with the shortest shots, then exhale into a held final image.
- Native single-generation cap is 15s (imagine.art also generates up to 15s) — a single dialogue beat can be one whole clip; a longer action sequence is several clips stitched.

**Takeaway:** state the *trend* of the pace ("angles change more and more frequently, building toward the crash"), not just a static speed. Match ASL to genre, and accelerate into the climax.

---

## 8. Montage of meaning — Kuleshov and Eisenstein

The **Kuleshov effect**: an audience derives emotion from the *juxtaposition* of shots, not from any single shot. The same neutral face read against a bowl of soup (hunger), a coffin (grief), or a child (tenderness) appears to change expression. Meaning is manufactured by adjacency. **Eisenstein** systematized this into a typology of montage:

- **Metric** — cuts on a fixed time interval (every N frames) regardless of content; rhythm from the clock. Drives raw intensity.
- **Rhythmic** — cut points follow the *content's* movement and tension; the action dictates the beat.
- **Tonal** — cuts follow the emotional tone / mood of shots (light, color, weight) rather than literal motion.
- (Plus overtonal and intellectual montage — combinations, and cuts that argue an idea by collision.)

**How to write it for Seedance:**
- Kuleshov within a clip: "Her unreadable face, then the empty chair where he used to sit, then back to her face." The engine renders three views; *the order* makes the meaning. Order your beats so adjacency does the emotional work.
- Metric feel: "a steady, mechanical pulse of images, each held the same brief length." Pair with a metronomic sound (audio is native — use it).
- Rhythmic: "cuts driven by the dancer's movement, the angle changing on each accent."
- Tonal: "images linked by their shared cold blue light and stillness, not by action." Lock the connective tone (color, light, weight) across views.

**Takeaway:** sequence your beats so that *what sits next to what* creates the meaning. Decide which montage type you want — clock-driven (metric), motion-driven (rhythmic), or mood-driven (tonal) — and write the connective thread accordingly. For strict metric montage, stitch (the engine won't hold an exact frame interval).

---

## 9. Environment cutting — establish, detail, re-establish; match cuts

The classic spatial rhythm: **establish → detail → re-establish.** Open wide so the audience knows *where they are*; move in for the details that carry the scene; periodically pull back to re-orient before they get lost. Re-establishing is the antidote to claustrophobia and confusion.

A **graphic match / match cut** transitions on a shared *visual property* — a shape, a color, or a direction of motion — so two unrelated spaces feel linked. The bone-to-spacecraft cut (shape + motion) is the canonical example; a spinning wheel to a spinning record (shape + motion); a red dress to a red door (color).

**How to write it for Seedance:**
- Establish/detail/re-establish in one clip: "Wide on the market at dawn; in to the vendor's hands counting coins; back out to the waking square." The arc keeps the viewer oriented.
- Match cut within a clip (the engine can carry a shape/motion through): "The full moon fills the frame, then becomes a white plate set on the table — same circle, same position, the world around it changed." Keep the matched element *the same size and screen position* across the change so the engine carries it.
- Motion match: "the wheel spins, and the spin becomes the rotor of a fan — the rotation never stops."

**How to do it properly (stitch):** a precise, frame-accurate match cut between two very different worlds is more reliable as two renders sharing an identical end/start frame, joined in an editor. Use first/last-frame control (see `advanced-control.md`) so the matched shape lands in the same spot.

**Takeaway:** keep the matched element identical in **shape, color or motion AND screen position** across the change. For a hero match cut between unrelated worlds, render both halves with shared frames and stitch.

---

## 10. Composition grammar

How the frame is arranged before anyone cuts.

- **Rule of thirds** — place key subjects on the third-lines or their intersections, not dead center, for natural balance. ("Subject framed on the left third, the empty road filling the right two-thirds.")
- **Lead room / nose room** — leave space *in front of* a moving or looking subject, in the direction of travel or gaze. ("She looks frame-right; leave the space open to her right.") Cramping the gaze feels wrong; open lead room feels alive.
- **Depth layering** — build foreground, midground, background so the frame has dimension. ("Foreground: out-of-focus foliage. Midground: the figure on the path. Background: the misted ridgeline.") Layered depth is the strongest single cue for a non-flat, cinematic image.
- **Frame-in-frame** — compose the subject inside a doorway, window, mirror, or arch to focus attention and add depth. ("Seen through the kitchen doorway, framed by the jamb.")
- **Size ↔ emotion** — shot size carries feeling. The closer the framing, the more intimate and intense; the wider, the more isolated, observed, or contextual. ("A tight close on her eyes" = intensity; "a distant wide, the figure small against the cliff" = isolation.) Push closer to raise emotional temperature; pull wider to cool it or to show consequence.

**How to write it for Seedance:** state composition in plain spatial terms — *where* in the frame, *how much* space, *what's* in fore/mid/background. Choose size for *feeling*, not just coverage. These map directly to Murch's eye-trace and 2D-plane criteria.

**Takeaway:** name placement (thirds), gaze space (lead room), depth (three layers), and choose shot size as an emotional dial — closer for intimacy/intensity, wider for isolation/context.

---

## 11. Eye-trace — guiding the viewer's eye across a cut

The viewer's eye rests somewhere in frame at the moment of a cut. A smooth cut **lands the next shot where the eye already is** — the point of interest in shot B appears near where the point of interest in shot A just was, so the eye doesn't have to hunt. A jarring cut throws the focal point to the opposite corner and forces a search, which (sometimes deliberately) registers as a jolt.

**How to write it for Seedance:**
- Smooth: "Her gaze drops to the letter in her lap; the view moves to the letter, held in the same lower-frame position." The eye was already low-frame; the new shot keeps it there.
- Hand-off: "He points off frame-right; the angle follows to what he's pointing at, entering from frame-right." The pointing finger pre-loads where the eye will go.
- Deliberate jolt (use sparingly): "cut hard from a quiet centered face to a violent motion bursting in from the edge" — the search *is* the shock.

**Takeaway:** decide where the eye rests at the change, and place the new shot's subject there. Use gaze, gesture, and motion to pre-aim the eye. This is Murch's #4, and on Seedance it doubles as a continuity aid — a led eye papers over small spatial drift.

---

## What Seedance actually honors — reliability table

Rated for what holds up *inside a single generation*. "Stitch" = render shots separately and join in an editor.

| Technique | Inside one generation | Workaround / note |
|---|---|---|
| **Emotion-first / story-first framing (Rule of Six top)** | Reliable | Lead with feeling and action; geometry serves it. |
| **Re-anchoring positions after an angle change** | Reliable | Mandatory hygiene — restate facing/position every time. |
| **Cutting on the action / on the hit** | Reliable | Tie the angle change to the kinetic peak ("on contact"). |
| **Screen direction as meaning (converge/diverge)** | Reliable | Lock frame-left/right after each change. |
| **180° line consistency** | Partial | Engine has no axis concept — restate facings or it drifts; for critical eyeline matches, stitch. |
| **Double-contrast (size + behavior)** | Reliable | Change two axes per angle or risk a stutter. |
| **J-cuts / L-cuts / sound bridges (within a clip)** | Reliable | Native audio makes these high-leverage — use freely. |
| **Long sound bridge across a real edit** | Reliable (via post) | Render clips separately; lay matching audio across the seam in your editor. |
| **Intercutting / parallel action (A/B/A/B)** | Unreliable | Engine flows instead of snapping; render threads separately and interleave in post, bound by shared audio. |
| **Pace ramp within a clip** | Partial | You influence it via angle-change frequency and action speed; precise ASL control comes from stitching. |
| **Kuleshov adjacency (order makes meaning)** | Reliable | Sequence beats deliberately within the clip. |
| **Metric montage (exact frame interval)** | Unreliable | Engine won't hold a fixed interval; stitch for true metric cutting. |
| **Rhythmic / tonal montage** | Partial→Reliable | Rhythmic (motion-led) and tonal (mood-led) hold reasonably; lock the connective thread (accent, color, light). |
| **Establish → detail → re-establish** | Reliable | Write the arc explicitly within one clip. |
| **Graphic / match cut (shape, color, motion)** | Partial | Works if the matched element keeps identical size + screen position; for hero cuts between unrelated worlds, stitch with shared frames. |
| **Composition (thirds, lead room, depth, frame-in-frame)** | Reliable | State placement in plain spatial terms. |
| **Size ↔ emotion as a dial** | Reliable | Closer = intimate/intense; wider = isolated/contextual. |
| **Eye-trace across an angle change** | Partial→Reliable | Pre-aim with gaze/gesture/motion; doubles as drift cover. |
| **True frame-accurate hard cuts** | Unreliable | The engine flows; render shots separately and stitch for any cut that must be exact. |

Bottom line: anything *audio-led* or *single-flow* is reliable; anything that requires *exact, repeated, frame-accurate snapping between distinct shots* (hard cuts, A/B intercutting, metric montage, hero match cuts) belongs in the stitch workflow. Write intent for the engine; reserve the editor for precision.


<!-- ═══════ FILE: seedance-director/references/editing-sources.md ═══════ -->

# Editing Sources — evidence base (background only, not on the prompt-writing path)

**Read this to verify or extend a principle — never to write a prompt.** The prompt-writing craft lives in `editing-and-cutting.md`, `production-grammar.md`, and the recipe files. This file exists so that a claim in those files can be traced to its origin, and so a principle can be extended responsibly without inventing authority. If you are composing a Seedance prompt, you are in the wrong file.

Citations name real, well-established works. No page numbers or ISBNs are given because they are easy to get wrong; verify against the actual edition if precision is needed. Items marked **(unverified)** could not be confirmed and should be treated as leads, not facts.

---

## (a) Key citable claims and their origin

- **The "Rule of Six" and its weights (Emotion 51% / Story 23% / Rhythm 10% / Eye-trace 7% / 2D plane of screen 5% / 3D space of action 4%), and "sacrifice from the bottom."** — Walter Murch, *In the Blink of an Eye*. Murch's central editing essay; the weighted priority list and the idea that a cut should serve emotion above spatial continuity are his.

- **The Kuleshov effect — meaning arises from the juxtaposition of shots, not from any single shot.** — Attributed to Lev Kuleshov's montage experiments (early Soviet cinema, c. 1910s–1920s), often discussed alongside Vsevolod Pudovkin. The famous "neutral face intercut with soup / coffin / child" demonstration is the standard illustration. The precise details of the original footage are debated by historians; the *principle* is solid.

- **Average Shot Length (ASL) data and the documented trend toward faster cutting in mainstream film.** — David Bordwell, *The Way Hollywood Tells It* (which develops his concept of **"intensified continuity"**); also Bordwell & Thompson, *Film Art: An Introduction* for ASL as a measurement. Empirical ASL studies (e.g., work associated with Barry Salt's statistical style analysis) underpin the numbers; treat specific genre ASL bands as *typical ranges*, not constants.

- **Montage typology — metric, rhythmic, tonal (and overtonal / intellectual) montage.** — Sergei Eisenstein, in his writings on film form and montage (collected in *Film Form* and *The Film Sense*). The categorization of montage by what governs the cut is his.

- **Editing rhythm as a craft — physical, emotional, and event rhythm; rhythm as the editor's primary material.** — Karen Pearlman, *Cutting Rhythms: Shaping the Film Edit*.

- **Foundational practical grammar of editing — continuity, the 180° rule, match-on-action, montage construction.** — Karel Reisz & Gavin Millar, *The Technique of Film Editing* (a long-standing reference text). Ken Dancyger, *The Technique of Film and Video Editing*, extends this into modern practice and theory.

- **Continuity editing system generally (establishing shots, eyeline match, the 180° rule, shot/reverse-shot).** — Treated as standard film-grammar consensus; well covered in Bordwell & Thompson, *Film Art*, and in Reisz & Millar. Not attributable to a single inventor.

---

## (b) Consolidated bibliography (de-duplicated; no fabricated page numbers or ISBNs)

- Bordwell, David. *The Way Hollywood Tells It: Story and Style in Modern Movies.*
- Bordwell, David, and Kristin Thompson. *Film Art: An Introduction.*
- Dancyger, Ken. *The Technique of Film and Video Editing: History, Theory, and Practice.*
- Eisenstein, Sergei. *Film Form: Essays in Film Theory.*
- Eisenstein, Sergei. *The Film Sense.*
- Murch, Walter. *In the Blink of an Eye: A Perspective on Film Editing.*
- Pearlman, Karen. *Cutting Rhythms: Shaping the Film Edit.*
- Reisz, Karel, and Gavin Millar. *The Technique of Film Editing.*
- Salt, Barry. *Film Style and Technology: History and Analysis* — **(use with care)** the standard source for statistical/quantitative shot-length analysis; cited here as the lineage behind ASL data.
- Pudovkin, Vsevolod. *Film Technique and Film Acting* — **(unverified exact title/edition)** associated with early montage theory alongside Kuleshov; confirm before citing specifics.

---

## (c) Live sources for Seedance 2.0 facts

Practical, product-level facts (caps, variants, reference grammar, native audio) come from these. URLs confirmed via web search June 2026 unless marked unverified. Cross-check before relying on a specific number — vendor docs change.

- **ByteDance Seed — official Seedance 2.0 model page.** Canonical source for model identity (SEED Lab, quad-modal, native synced audio). Pattern: `https://seed.bytedance.com/` → Seedance 2.0 / `seedance2_0` page. **(URL slug unverified — confirm the exact path on the Seed site.)**
- **BytePlus ModelArk — Dreamina Seedance 2.0 series prompt guide.** `https://docs.byteplus.com/en/docs/ModelArk/2222480` — vendor prompt-engineering guidance (subject+action+scene structure, positive constraints over negatives).
- **imagine.art — Seedance 2.0 app page.** `https://www.imagine.art/apps/seedance-2.0` — the default surface for this skill.
- **imagine.art — Seedance 2.0 prompt guide blog (70 ready-to-use prompts).** `https://www.imagine.art/blogs/seedance-2-0-prompt-guide`
- **imagine.art — Seedance 2.0 guide / how-to.** `https://www.imagine.art/blogs/seedance-2-0-guide` and `https://www.imagine.art/blogs/how-to-use-seedance-2-0`
- **Higgsfield — Seedance 2.0 complete prompting guide.** `https://higgsfield.ai/blog/seedance-prompting-guide` — shot-numbering, transformation/POV/orb formats, "state shots + duration + aspect ratio at top."
- **GitHub — YouMind-OpenLab/awesome-seedance-2-prompts.** `https://github.com/YouMind-OpenLab/awesome-seedance-2-prompts` — large community prompt library (cinematic, anime, UGC, ads), API guides, character-consistency tips.
- **AtlasCloud — Seedance 2.0 guides.** `https://www.atlascloud.ai/blog/guides/seedance-2.0-complete-guide` and best-prompts guide `https://www.atlascloud.ai/blog/ai-updates/best-seedance-2-0-prompts-guide` — prompt-structure breakdown and global-style-modifier behavior.

**Note on discrepancies:** this skill's house default is the **imagine.art** surface: **up to 15s per clip, up to 1080p**, Standard ("Pro"/quality) + Fast variants. Native single-generation max is **15s, extendable** by chaining; 2K exists on the Standard tier on some surfaces (e.g. Dreamina Studio) but not on imagine.art. When a third-party figure conflicts with the imagine.art surface, follow the imagine.art number and treat larger single-shot durations (e.g. 20s+) as platform/tier-dependent and unverified.


<!-- ═══════ FILE: seedance-director/references/fashion-editorial.md ═══════ -->

# Fashion & Editorial — how fashion is cut, and how Seedance shoots it

Fashion film is its own editing grammar. Read this file (with `model-poses-and-walks.md` for what the model physically does) before planning any fashion, editorial, lookbook, runway, try-on, or outfit-transition brief. It layers ON TOP of the general craft in `editing-and-cutting.md` — where the two disagree, fashion wins for fashion briefs.

---

## 1. The doctrine: the garment is the protagonist

Nick Knight (SHOWstudio, the founding voice of the genre): fashion film is **"moving fashion photography… garments in movement."** It is **non-narrative by default** — it uses the codes of fashion *photography*, not cinema. "The best way to express a garment is to watch it in motion, the way it was designed to be seen."

What this changes about every editing rule you know:

- **Pose logic replaces continuity logic.** There is no 180° pressure, no eyeline matching, no scene geography to preserve. **Jump cuts within the same setup are the native idiom**, not a violation. (For Seedance you still re-anchor the subject after each cut — that's engine hygiene, not film grammar.)
- **Every cut is justified by what it reveals about the clothes** — silhouette, drape, texture, hardware, movement. A cut that reveals nothing new about the garment is dead weight.
- **Every frame must be poster-quality.** The fashion-photography standard applied per frame: cut to where the garment *hits* — peak drape, peak swing, peak silhouette — not where performance continuity is cleanest.
- **Models, not actors.** Ruth Hogben: "My main starting point is the clothes… every single movement conveys a message and feeling." Direct movement that expresses the garment, not emotion-acting.
- **Both poles are live:** the non-narrative movement-study (Knight/Hogben) and the loose-narrative fashion film (Albert Moya: "people need stories to watch videos nowadays"). Ask the director which pole; default to non-narrative for lookbook/editorial briefs, loose-narrative for brand/campaign films.

**Mode mapping:** M2 Studio is the default fashion look (seamless, editorial grade, controlled speculars). Street-style editorial → M1 with the fashion cut grammar from this file. Runway → M4 behavior (long-lens locked "look camera" + roaming units).

---

## 2. Coverage grammar — the look-shot ladder

Fashion has a canonical shot menu. Every look gets built from these seven, and the edit alternates them:

| Shot | What it does | Prompt language |
|---|---|---|
| **Full-length / head-to-toe** | The silhouette shot — obligatory once per look | "full-body shot, head to toe in frame, the full silhouette of the coat readable against the seamless" |
| **3/4 look shot** (mid-thigh up) | Styling + proportion; the workhorse | "three-quarter shot from mid-thigh up" |
| **Beauty close-up** | Head/shoulders — hair, makeup, jewelry, attitude | "tight head-and-shoulders beauty shot, locked-off, she moves inside the frame" |
| **Detail / macro insert** | Fabric weave, stitching, hardware, buttons, heel | "extreme close-up raking across the wool weave, side-light catching the herringbone texture" — raking light sells texture |
| **Movement shot** | Fabric activated — walk, twirl, wind, swish | "she turns sharply; the coat hem flares and settles with real weight" |
| **360 turn / spin** | The garment turntable — the single most fashion-specific shot | "slow full turn on the spot, the dress rotating through the light" |
| **Environmental wide** | Model small in location; brand world | "distant wide, the figure small against the brutalist facade" |

**The base alternation pattern (the fashion edit in one line):** wide look-shot → macro detail insert → movement shot → next look. Detail inserts are the B-roll of fashion — they compress or extend a look's screen time at will and hide every reposition. Never cut look-shot to look-shot of the same look at similar size (that's the stutter `editing-and-cutting.md` §4 warns about); always pass through a detail or a movement beat.

**Runway coverage grammar** (for runway-style briefs): one locked **head-on long-lens "look camera"** at the end of the runway (compressed telephoto perspective, the canonical full walk) + roaming low-angle units for shoe/hem details + reaction cutaways. Coverage tightens as the model advances: full-length far → 3/4 mid-runway → head/shoulders at the mark. Recap structure: theme-establishing detail CUs → opening look played long → alternating walks / detail cutaways / reactions → finale procession.

---

## 3. Fashion beat-cutting — the pose is the sync point

Fashion edits are music-led. This is the standing exception to the diegetic-only default: **confirm music with the director, then drive the cut with it** — via an `@audio1` rhythm reference, a `video rhythm references @video1` line, or timestamped beats. (If the user wants no music: heel strikes, fabric snaps, and camera-shutter clicks make a diegetic rhythm track.)

- **Action-on-beat beats cut-on-beat.** The refinement that separates fashion from music-video cutting: time the *movement accent* — hair whip, fabric snap, heel strike, jump landing, head turn, **pose hit** — to land ON the beat, then cut on or just after the accent. The pose is the sync point; the cut confirms it.
- **The pose hit** is fashion's "cut on the action": the model flows through movement, locks a shape for a beat, and the angle changes on the lock. Write it: "she hits the pose on the beat — hard stop, chin up — and the angle snaps wide."
- **Hold through the phrase when the fabric is moving well.** Fashion rhythm has more dynamic range than a music video's constant 1–2s: burst-cut the details between phrases, but when the drape is performing — a twirl blooming, a coat trailing — the drape IS the solo; hold it. Slow-mo holds of 2–6s punctuated by sub-second detail bursts is the genre's signature bimodal pacing.
- **Speed ramp at the garment's peak:** normal speed → slow-mo at the twirl apex / fabric bloom → snap back. Pair with an audio swell. (Live convention: 60fps played at 24 = 2.5× — ask for "the twirl blooms in slow motion, then snaps back to real time.")
- **Flash cut / paparazzi strobe:** a burst of near-still frames or a white "camera flash" hit between looks — the most genre-native transition (it mimics the photo studio / paparazzi flash). Write: "a white flash-frame, like a camera flash firing, and she's in the next look."
- **Freeze + shutter click:** hit pose → frame freezes → camera-shutter click SFX (native audio makes this cheap) → motion resumes or cut. The conventionalized "photo moment."
- **Whip pan between looks/locations:** whip out of look A, whip into look B, cut hidden in the blur — one continuous energy line across a wardrobe change (`advanced-control.md` transitions).
- **Match-on-pose outfit swap:** identical pose, framing, lighting across two looks — the cut swaps only the outfit. Inside one generation, prompt it as a hold: "same pose, same framing; on the beat her outfit changes to the look from @image2, nothing else changes." Across renders: first/last-frame chaining (§5).
- **Downbeat vs syncopation as a style dial:** cuts on strong downbeats read commercial/high-energy; off-beat cuts and cutting in the pauses read editorial/experimental.

---

## 4. Format templates (structure by deliverable)

**A. Lookbook video** (per-look module, 60s–3min live; in Seedance, one 10–15s generation per look, stitched). Per look: full-length → 3/4 → 2–3 detail inserts → one movement beat. Looks separated by whip pan, white flash, or hard cut on beat. Constant backdrop/lighting — the looks carry the variety.

**B. Fashion film, non-narrative** (movement study): concept image → escalating movement studies → climax (fastest cutting, most abstract) → still resolution. A mood-arc, not a plot-arc.

**C. Fashion film, loose narrative:** a thin situation (arriving, waiting, leaving) carries the looks; sound design and location do the narrative work the picture refuses to do.

**D. Runway recap** (45–90s): opening detail CUs → first look long → walk/detail/reaction alternation → finale. Beats synced to stride — heel strikes on the beat.

**E. Social 9:16 outfit-change edit** (6–30s, the TikTok/Reels format): locked camera, marked floor position, identical framing; the switch lands exactly on the beat drop, masked by a movement that covers the lens or torso for one beat — jump, spin, arm sweep, hand over lens. Hook in the first 1–2s (strongest look, or open mid-transition). 3–8 outfit hits. Loopable ending. Whoosh/snap SFX on each switch.

**F. Campaign stack:** 60s hero (16:9) → 30s/15s cutdowns → 6s bumpers → 9:16/1:1 verticals. Cutdowns are *re-edited to front-load the garment*, not trimmed. Plan the hero so the garment beats survive extraction.

**The canonical outfit-cycling prompt shape** (single generation, from the Seedance community gallery): *"The girl keeps changing outfits, clothing references the styles of @image1 @image2, holding the bag from @image3, video rhythm references @video1."* — outfit refs + one rhythm reference = beat-synced look cycling in one pass.

---

## 5. Storyboard → Seedance: the stills-first pipeline

The consensus AI-fashion workflow is **stills first, then animate**. Video-first produces worse garment consistency in every tested workflow.

1. **Product asset prep.** Garment references: flat-lay, ghost-mannequin, or on-hanger — isolated, clean background, high-res, straight-on, no hands, no one wearing it (worn-garment references make placement fail).
2. **Model definition.** One identity reference set (3 stills max: straight-on / three-quarter / profile, same session, same lighting — see `recipes-and-operations.md` §identity). Real-face photos are blocked (`model-card.md`) — use an AI-generated fictional model.
3. **Generate the still lookbook** in an image model — every look, every angle you'll animate, consistent model + palette. This is the storyboard.
4. **Animate shot-by-shot:** each approved still = the first frame (or `@image` anchor) of one 4–15s Seedance clip. One look-module per generation.
5. **QA against the real garment** — logos, buttons, and unique construction details are *interpreted, not reproduced*; verify before shipping. Expect ~70–80% first-pass acceptance; regens concentrate on prints, multi-layer outfits, unusual silhouettes.
6. **Stitch** into the format template (§4), grade, add music. A final grain pass unifies seams across clips and survives platform re-encode.

**Outfit-change chaining across clips** (the AI version of the TikTok transition): generate look-1 clip → extract the final frame → image-edit the outfit swap on that frozen frame → the edited frame is the first frame of clip 2. Chain 4–8 clips at 3–4s each → a 15–30s edit. Keep camera framing, model position, and lighting identical across the chain — the seams then read as intentional beat-cuts.

**Wardrobe locking grammar** (official role assignments): `wearing the outfit from @image2` · `product details reference @image3` · plus a closing lock: "Face, hair, outfit, and silhouette fully consistent with @image1 throughout." **Also restate the key wardrobe traits in text** even with a reference — the reference carries the look, the text pins the details the model would otherwise re-decide. Anchor the palette by name ("emerald, terracotta, warm cream") or hues drift between shots.

**The hard ceilings (fashion-specific, from tested workflows):**
- **≤3 outfit changes per generation.** Three is the ceiling; more breaks continuity.
- **4–5 steps max per walk.** Long runway walks drift into the glide; break longer walks into chained clips.
- **4–6s shots for shimmer-prone fabric** (sequins, lace, sheer, fine knits); past ~8s exposure drift and texture crawl creep in.
- Feet must be visible in the identity reference if the clip contains walking — cropped feet produce invented steps.

---

## 6. Fabric, garments, and what the engine gets wrong

**Name fiber + weight + behavior, always.** The engine defaults to "average fabric" that matches no real material. Give the physics branch something to simulate: "heavy wool coat, the hem lagging a beat behind her turn" · "bias-cut silk that billows and settles" · "crisp ripstop nylon, holds its crease" · "dense denim, stiff at the seams." A motion cue activates it: "the dress billows slightly in the wind."

**Fabric reliability ranking** (tested): structured/tailored + denim = excellent · flowing (silk, chiffon, linen) = very good · outerwear = very good · knitwear = good (cable-knit gets simplified) · **sequins/lace/sheer/mesh = shimmer-prone** · **jewelry = weakest category**.

**Texture-crawl / moiré fix ladder** (for sequins, mesh, herringbone, micro-checks — apply in order until it holds):
1. Remove the trigger words: don't *name* moiré-prone patterns you don't need; cut sparkle-inviting adjectives ("glow, glimmer, glints").
2. "Even, diffuse lighting" or "single soft key 45° camera-left, steady intensity" + "soft shadows, constant exposure."
3. Negatives (this counts toward your ≤3): "no shimmer, no flicker, no pulsing."
4. Clean the reference still: upscale, denoise, even exposure — fixes texture crawl in most cases. Counterintuitive pro move: a *gentle pre-blur* on the high-frequency fabric in the reference tames crawl; sharpen in post.
5. Shorten the shot to 4–6s. Swap "warm sunlight" for "overcast daylight" if highlights breathe.

**Garment morphing / neckline drift / logo shift:** the model re-decides the subject at every transition. Lock it: "keep identity, keep outfit, no outfit changes" + restate the garment's signature detail once in text + calm backgrounds. On-garment logos/text: keep them large and centered or plan a post fix — "logo stays sharp and unchanged" helps but doesn't guarantee.

**Jewelry:** blurred clasps, warped stones, wrong metal. Mitigate: medium distance not macro, locked camera, one steady light source, slow moves, short clip. For a true jewelry hero shot, consider a stills pass instead.

**Heels + walk:** the floating glide is the #1 fashion tell. Fix with gait mechanics + audible ground contact: "heel strike to toe push-off, weight transferring with each step, arms in natural counter-swing, footsteps sharp on the concrete." Native audio is the secret weapon — **audible heel strikes force ground contact.** Full walk vocabulary: `model-poses-and-walks.md`.

**Hands on fabric:** one motion per beat — "slips it on, smooths the front, pops the collar" as separate beats, never stacked. Keep hands larger in frame; no fast finger work.

**Sheer/translucent:** give the model a light-transport instruction — "sunlight passing through the sheer sleeve" — instead of naming the fabric type alone.

**Hair–fabric:** direct it ("subtle wind lifts her hair off the collar") rather than leaving it undirected; keep hair off complex collars in the reference still.

---

## 7. Fashion anti-slop (on top of `realism-and-camera.md`)

The fashion-specific tells, beyond plastic skin: the **ghost-glide walk** · **latex sheen on every fabric** · the **generic beautiful-model face** · **slow-motion everything** · the **constant orbiting camera** · the same three poses · auto-inserted soft music (**write the literal phrase "no music"** — it outperforms "no background music").

The fixes are fashion craft, not more negatives:
- **The Copy Lab doctrine** (Copy magazine, the first AI fashion magazine): AI output is "too perfect, too beautiful, too stereotyped" — the craft is to *deconstruct toward imperfection*, the inverse of retouching. Cast character over prettiness: "gap in her front teeth, sun-freckled, hair slightly frizzed at the temples."
- **Styling specificity beats beauty adjectives.** A real stylist's eye — "oversized blazer with the sleeves pushed up, one cuff undone, vintage belt cinched high" — reads editorial; "stunning designer outfit" reads slop.
- **Editorial lighting is opinionated:** "rim light from behind, negative fill camera-right" / "one hard key, deep shadow side" / mixed temperatures for street. Never even beauty-light everything.
- **Vary the camera per shot** the way the coverage ladder (§2) demands — locked beauty shot, raking macro, one moving shot. The orbit is a garnish, not a diet.
- **Eyes need a target:** "eyes scanning past camera, then locking onto the lens for the last beat" — gaze events read as thought; the glassy stare is the tell.
- 24fps + film grain + lifted blacks for editorial; phone-look (`realism-and-camera.md`) only for deliberate UGC/street-cast registers.

---

## 8. What Seedance honors — fashion addendum

| Technique | Inside one generation | Note |
|---|---|---|
| Look-shot ladder as multi-shot sequence | Reliable | One look per generation; alternate sizes per §2 |
| Outfit cycling on rhythm reference | Reliable | ≤3 outfits; the §4 canonical prompt shape |
| Pose hit on the beat | Reliable | Name the accent + the beat; audio is native |
| Freeze + shutter click | Partial | The click is reliable; a true frame-freeze may render as a slow hold — stitch for exactness |
| White flash / strobe transition | Partial | One flash beat works; sustained strobing → stitch |
| Match-on-pose outfit swap | Partial | Best across renders via frame-edit chaining (§5) |
| Walk (4–5 steps, audible heels) | Reliable | Beyond 5 steps the glide returns |
| Twirl with fabric bloom + speed ramp | Reliable | Name fiber + weight; ramp at the apex |
| Sequins/lace/sheer held over 8s | Unreliable | 4–6s shots + the §6 fix ladder |
| Macro fabric texture with raking light | Reliable | Strongest with a clean high-res reference |
| Jewelry macro | Unreliable | Medium shot or a stills pass |
| On-garment logo fidelity | Partial | Large + centered helps; verify every render |

---

## Sources (fashion layer)

Nick Knight on fashion film (nickknight.com/press/nk-fashion-film) · Ruth Hogben, SHOWstudio profile + In Fashion interview (showstudio.com) · William Town on cutting Vogue's "Hello You" (lbbonline.com) · Uhlirova, "100 Years of the Fashion Film," *Fashion Theory* 2013 · Vashi Nedomansky, music-video ASL stats (vashivisuals.com) — nearest quantified pacing benchmark; no formal fashion-film ASL census exists · Seedance 2.0 official prompt manual, EN trans. (paralleldistribution.com) · WaveSpeed flicker/texture-crawl diagnostics (wavespeed.ai) · videoai.me Seedance fashion prompt recipes · flyne.ai reference-strategy guide · Atlas Cloud "Fashion Beat Drop" gallery prompt · Higgsfield Fashion Factory + clothing-brand prompt library (higgsfield.ai) · Flowith AI-lookbook workflow case study · Rewarx anti-plastic guide · Copy Lab / Carl-Axel Wahlström interviews (PetaPixel, Culture & Code) · eyecannndy flash-cut technique library · FlexClip/socialz TikTok outfit-transition guides. "Pose-hit" and freeze-frame conventions are practitioner vernacular, not academic literature.


<!-- ═══════ FILE: seedance-director/references/model-poses-and-walks.md ═══════ -->

# Model Poses & Walks — the movement vocabulary for fashion prompts

How models actually stand, walk, pose, and move — broken into physical language the engine can simulate. Use with `fashion-editorial.md`. Everything here is prompt-ready: lift the phrasing directly. The engine's physics branch rewards biomechanics ("heel strike, weight transfer") and punishes vibes ("walks confidently").

---

## 1. The runway walk, by body part

Write walks as mechanics, not adjectives. The full stack (pick the lines the shot needs — a 4s clip needs two of these, not all six):

- **Feet (female / classic):** each foot lands directly in front of the other on one invisible straight line, toes forward, heel striking first then rolling to the ball. The crossing stride is what *produces* the hip swing — never prompt "swinging hips" directly; prompt the footfall and the sway follows naturally.
- **Feet (male):** feet track in a slight V — inside-to-outside, never crossing the centerline — which kills hip sway and carries the walk in the shoulders and chest. Ball of the foot touching first reads as the male runway glide.
- **Stride:** long, deliberate strides from the hip, knees slightly higher than a street walk, constant tempo. "Walks like she has a destination."
- **Hips:** a byproduct, never pumped. If more sway is wanted, exaggerate the *crossing* of the feet (the sashay register), not the hips.
- **Torso/arms:** shoulders back and down and level — no bounce; body stacked in one vertical line; arms close to the body with a small natural counter-swing (opposite arm to leg), hands relaxed, fingers softly open — never fists. High-fashion variant: arms held deliberately still at the sides.
- **Head/gaze:** chin level, gaze fixed on one far point past the camera at eye level — never at the feet, never scanning. **Runway face:** neutral, lips closed and relaxed or slightly parted, no smile, held unbroken.

**The prompt-sized version (the walk stack):** *"She walks toward camera — four long strides, each foot landing in front of the other on one line, heel strike to toe push-off, weight transferring visibly with each step, arms in a small natural counter-swing, shoulders level, chin level, gaze fixed past the lens, expression neutral, lips just parted. Heel strikes sharp and audible on the concrete."*

Ceilings from `fashion-editorial.md` §5: **4–5 steps per generation**, feet visible in the reference, audible footsteps to force ground contact.

## 2. Walk registers (pick one, name its physics)

| Register | Physics to write | Reads as |
|---|---|---|
| **Classic / high-fashion** | straight line footfall, restrained sway, minimal arm swing, neutral-fierce face, steady far gaze | Chanel/Dior |
| **Power walk** | faster, wider strides, slight forward lean, arms rigid or driving, hard stare | Balenciaga/Rick Owens |
| **Editorial / couture** | slow, fluid, deliberate pauses and direction changes, arms interacting with the garment — "moving sculpture" | Viktor & Rolf |
| **Commercial** | medium natural stride, bouncier, relaxed open posture, hands may slip into pockets, warm genuine smile, eye contact | Zara/H&M |
| **Glamour / sashay** | exaggerated crossing stride and hip swing, bounce, hair movement, over-shoulder glances | Victoria's Secret |
| **Theatrical** | choreographed stops, spins, quarter-turns, sweeping arm gestures synced to the music | Mugler/Gaultier |
| **Male runway** | V-track feet, quiet hips, chest forward, walk carried in shoulders, chin parallel to floor, no smile | menswear default |

## 3. The end-of-runway sequence (a complete beat structure, free)

The choreographic unit every runway brief wants, and a ready-made 6–10s clip arc:

**walk in → slow approaching the mark → hard stop → pose #1 hits (hold 2–3s: weight onto one hip, one hand on hip) → weight-shift into pose #2 (new angle, 2–3s) → pivot turn → walk away at full energy.**

- **Pivot mechanics:** turn on the balls of both feet, lead foot pointing into the new direction, back foot pushing the rotation — and the head turns *last*: the face is the last thing to leave the camera. ("She pivots on the balls of her feet; her eyes hold the lens until the turn pulls them away.")
- **Named end-marks:** **C pose** (hand on hip, opposite toe pointed out, head turned away — body curves into a C) · **S pose** (same base, head turned the other way) · **I pose** (square to camera, torso twisted slightly, arms crossed or one hand on hip).

## 4. Pose vocabulary (each line is prompt-ready)

**Weight & spine shapes:**
- **Contrapposto** — all weight on the back leg, free leg bent, hips and shoulders tilted at opposing angles. The default fashion stance.
- **S-curve** — weight hard on one hip, ribcage shifted opposite, head tilted back the other way; elongates the body. For form-fitting garments.
- **Hip pop** — weight slammed onto one hip, hip pushed laterally, body slightly angled to camera.
- **Broken doll** — deliberately askew: hard angles, elbows akimbo, knees knocked inward, face pushed off-center. Anti-pretty, high-fashion awkwardness.
- **Power stance** — feet wider than shoulders, weight even, hands on hips or arms crossed, chin level. Square and commanding.
- **Arched back** — spine arched, chest lifted, one or both arms overhead; maximum elongation.

**Garment-interaction poses (the fashion-specific family — these double as movement beats):** lapel grip · collar pop · cuff adjust · sleeve roll (revealing a watch) · hem tug · zipping the coat halfway · popping the jacket onto the shoulders · throwing off a hood · holding a skirt edge out · jacket slung over one shoulder on two fingers. Hands relax after every adjustment.

**Head & gaze:** over-the-shoulder look-back (back to camera, torso twisted, chin lifted to stretch the neck) · chin-down-eyes-up (jawline defined, vulnerability register) · profile (90° to camera) · three-quarter (45° — the default flattering angle) · off-camera gaze with a slight head tilt (detachment).

**Standing / leaning:** one-leg-forward stand (front toe to camera, weight back) · wall lean (shoulder or back to the wall, one foot flat against it) · mid-stride toward the lens, one foot crossing, "caught in motion" · stairs walk.

**Seated / floor:** crossed legs · elbow-on-knee lean-in · knees-up hug · legs-wide seated (power) · reclining on one elbow.

**Elongation rules (bake into any pose description):** daylight between limbs and torso — arms never pressed flat to the body · asymmetry over symmetry — one shoulder up, one arm bent, weight on one leg · angles over curves for high fashion; curves for glamour · if it bends, bend it slightly; point the free foot · chin forward and slightly down (the "turtle") to carve the jawline.

**Hand rules (hands are a top failure zone — constrain them):** relaxed wrists, fingers slightly apart and gently curved · side of the hand to camera, never a flat palm · "ballet hands" — index slightly lifted, middle relaxed down · face/collarbone touches are fingertip-light, never pressing · no fists. Prompt-ready: *"hands relaxed, fingers softly curved, the side of the hand to camera."*

## 5. Directing movement for film (not stills)

Stills posing is burst posing — discrete shapes, the camera catches peaks. **Film posing is flow posing:** the model is never fully still; she flows pose→pose like slow choreography, easing in and out, **hitting** a defined shape on the beat, holding it for a beat or two, then melting into the next. Everything at half speed.

- Write the flow: *"She moves through poses like slow choreography — hits a shape on the beat, holds two counts, melts into the next."*
- **Micro-movement menu** (what "she stands there" should actually say): slow head turn toward or away from lens · gaze shift ending in eye contact — making or breaking eye contact is an *event* on camera · slow blink · visible breathing, shoulders rising · weight rocking foot to foot · slight shoulder sway · slow chin lift · hair lifting in a fan's wind.
- **Fabric-activation moves** (pair with the fiber physics in `fashion-editorial.md` §6): twirl so the skirt flares and ripples · skirt flick with one hand · sharp turn for the coat swish · fast walk so the long coat trails and billows · one arm raised for the sleeve flare · tug-and-release of the fabric. Physics cues: tulle moves as one unit; fine silk ripples; a heavy full skirt keeps waving after she stops — say "the hem keeps moving a beat after she stops."
- **Voguing flavor** (high-energy editorial): hands performance framing the face in precise shapes · duckwalk kicking forward on the beat · spin and drop (dip) on the beat · old-way hard angles held as poses. Use as seasoning, one element per clip.
- **Stride to the BPM:** match walk tempo to the track; slow the sway on slow beats; land pose holds on the beat (see `fashion-editorial.md` §3).

## 6. Attitude registers (expression as physiology — never "looks confident")

- **Aloof high-fashion:** gaze fixed on a far point past the viewer, face neutral, lips relaxed and just parted, zero smile.
- **Smize:** the smile lives only in the eyes — lower lids engaged and raised, mouth neutral.
- **Squinch:** lower eyelids narrowed a fraction, top lids barely dropped — reads intent, not squint.
- **Jaw / turtle:** neck extended, face pushed slightly toward the lens, chin tipped a touch down — carves the jawline. Male version adds a visible jaw clench.
- **Commercial:** soft genuine smile, level chin, direct eye contact, open posture.
- **Power:** chin level or lifted, hard stare or faint smirk, square shoulders.
- **Vulnerability:** chin down, eyes up, shoulders curled slightly forward, fingertips near the collarbone, lips parted.

## 7. Male model specifics

Walk: V-track feet, hips quiet, chest out, movement in the shoulders, long steady strides, only the lower arms swinging, chin parallel to the floor, lips closed, no smile. End of runway: same stop–pose–count–pivot arc; C/S/I poses; eyes may drop to meet the camera at the mark — eyes only, head stays up. Poses: feet shoulder-width or wider (grounded base) · hands in pockets, thumbs hooked out · arms crossed · adjusting watch/cuff/lapel · seated elbow-on-knee lean toward the lens · wall lean, ankles crossed. Face: jaw pushed slightly *forward* (not chin up — that shows the underside), optional clench, low level brow. Register: minimal movement, clean lines, grounded and controlled.

## 8. Verb bank (swap for "walks" and "poses")

glide · strut · stalk · prowl · sashay · saunter · pivot · hit the pose · hold · melt into · ease out of · weight-shift · sway · rock · twirl · flick · swish · billow · trail · flare · pop (the collar) · tug · adjust · drape · frame the face · cast a glance · break the gaze · lock eyes.

---

## Worked micro-examples

- **Beauty shot with life:** *"Locked-off head-and-shoulders. She turns her head slowly from three-quarter to the lens, a slow blink, then the smize — lower lids lifting, mouth neutral. Flyaway hairs move in the soft air."*
- **Garment beat:** *"Three-quarter shot. He pops the jacket onto his shoulders in one motion, straightens one lapel, hands relaxing to his sides — jaw forward, low level brow, no smile."*
- **End-of-runway unit (8s):** *"She stops on the mark on the downbeat, weight slamming onto her left hip, right hand on hip — holds two counts — weight-shifts into the S pose, head turning away — holds — then pivots on the balls of both feet, eyes leaving the lens last, and walks upstage, coat hem flaring on the turn. Heel strikes land on the beat."*
- **Flow-posing studio clip:** *"Mid-grey seamless, locked 50mm. She flows through poses like slow choreography — contrapposto, melting into an over-the-shoulder look-back, hitting the arched-back shape with one arm overhead on the beat and holding. Daylight between her arms and torso in every shape, fingers softly curved."*

## Sources

Skylar Modeling runway guides · MasterClass runway walk (Naomi Campbell) · Backstage "How to Walk Like a Model" · menstylefashion male catwalk choreography · J. Alexander coaching lineage · Brandon Andre female/male posing guides · wearview + 1x.com contrapposto/S-curve · Dis Magazine "Broken Doll" · The Lens Lounge / ExpertPhotography hand posing · Filtergrade posing for video · Dazzlerr + Dylan-in-the-Details flow posing · shunvogue/curatedsense twirl physics · Fstoppers (Hurley squinch) · Tyra Banks smize (News24) · Vogue dance — Wikipedia + Creative Edge five elements · JCasablancas male runway technique.


<!-- ═══════ FILE: seedance-director/references/pro-techniques.md ═══════ -->

# Pro Techniques — official-doc patterns

The patterns ByteDance's own docs and the strongest production users lean on with Seedance 2.0. These build on the core formula (Subject → Action → Environment → Camera → Style → Constraints, 60–100 words) in `production-grammar.md` and the camera/realism vocabulary in `realism-and-camera.md`. Everything below is copy-paste ready.

---

## Edit-vs-reference intent — one role line per asset

Every uploaded asset gets **one explicit role line** so the model knows what to take from it and what to ignore. Never let an upload sit there ambiguous; the model will guess and average.

Write it as a flat statement before the scene:

```
@image1 = the character's face and identity (use this person).
@image2 = the wardrobe (the camel coat only — ignore the background).
@image3 = the location (this cafe interior; do not copy the people in it).
@video1 = camera reference (match its slow push-in and pacing; ignore its content).
@audio1 = the dialogue / rhythm track.
```

Two failure modes this prevents: (1) the model copying a reference's background when you only wanted its subject, and (2) the model treating a *reference* video as an *edit target* (regenerating that exact footage instead of making a new scene that moves like it). If you mean "modify this clip," say `edit @video1:` — if you mean "borrow its motion," say `reference @video1's camera`. Earlier-listed references weigh more, so order them by importance. Never re-describe what an image already shows — name the role, not the pixels.

---

## Physics-first action writing

Seedance 2.0 has a strong physics prior (ByteDance reports roughly **+31.7 points over Seedance 1.5 on their physics benchmark**). Feed it interactions it can *simulate*, not abstract verbs it has to interpret.

Write the consequence, not the label:

| Weak (abstract) | Physics-first (simulatable) |
|---|---|
| the car turns | tires smoke and squeal as the car drifts 90°, weight shifting to the outside wheels |
| she pours the drink | amber liquid streams in, foam rising and settling, condensation beading on the glass |
| the wave hits | the wave slams the rocks and explodes into spray, water sheeting back down |
| he punches | his fist connects, the bag jolts back and swings, dust puffing off it |
| the fabric moves | the silk catches the wind, rippling and snapping taut, then folding back |
| the candle is lit | the flame catches, wax softening at the rim, smoke curling up when it gutters |

Anchor every action to a real-world cause and a visible reaction (impact, weight transfer, inertia, fluid flow, deformation, light interaction). This is also the fix for "floaty" or "weak" motion in the re-prompt tree (`advanced-control.md` §5): rewrite the Action clause physics-first before you touch anything else.

---

## The Shot-Script format

For multi-beat clips, name the shots with timecodes. This gives the model explicit blocking and keeps a sequence from collapsing into one mushy take.

```
Shot 1 (0:00–0:02): wide establishing — the diner exterior at dusk, neon sign buzzing on.
Shot 2 (0:02–0:05): cut to interior medium — the waitress slides a plate across the counter.
Shot 3 (0:05–0:08): close-up — the customer looks up, half-smiles, says "you remembered."
```

Rules:
- Keep total runtime ≤ 15s (native single-generation cap; imagine.art generates up to 15s). 3–6 numbered shots is the practical ceiling in one render; beyond that, stitch (see extension chaining below and `editing-and-cutting.md`).
- One primary camera move per shot — don't stack moves inside a single timecode.
- Timecodes can also anchor SFX and beats (see sub-second micro-timing).

---

## Reference role taxonomy + file allocation

Omni Reference mode gives you 12 slots: **9 images, 3 videos, 3 audio.** Spend them deliberately — every slot should have a job, and you rarely need all 12.

Typical allocation:

- **Identity (images):** 1–3 images of the hero subject (face from a couple of angles, full body if wardrobe matters). This is the highest-value spend; list it first.
- **Environment (images):** 1–2 images of the location/set. Clean, uncluttered shots.
- **Product / prop (images):** 1 image per key object, clean background.
- **Wardrobe / style plate (images):** 1 image if the outfit or art-direction needs locking.
- **Camera-style (video):** 1 video whose camera move/pacing you want copied (trim to 2–8s).
- **Action/choreography (video):** 1 video of the motion to replicate.
- **Audio (audio):** 1 dialogue/VO track, 1 music/rhythm track, 1 SFX bed — up to 3.

Asset hygiene:
- **Images ≥ 1024px**, sharp, **clean uncluttered backgrounds** (the model can't separate a subject from a busy frame reliably).
- **One element per video** — a clip should donate either its camera OR its action OR its rhythm, not all three.
- **Audio: MP3, trimmed to 3–8s** of the part that matters. Long audio dilutes the signal the same way long video does.

---

## Extension chaining for long-form (30–90s+)

A single clip caps at 15s (native and on imagine.art). To go longer, generate in **≤15s segments and chain them** so they cut together.

1. Write a **global aesthetic header** — one fixed block reused verbatim atop every segment so style/lighting/grade don't drift:
   ```
   [STYLE LOCK] 35mm film, warm tungsten grade, soft window light, shallow depth of field, gentle handheld. Same color palette throughout.
   ```
2. Below the header, write each segment's own Subject/Action/Camera. Carry the subject description identically segment to segment (or reuse the same reference image).
3. End each segment on a frame that the next can pick up from (a held pose, a clean exit) — or use the two-pass first-frame trick from `advanced-control.md` §4 to hand the last frame of segment N to segment N+1.
4. Stitch the segments with **Track Completion** (the extend-from-last-frame operation), so each new piece continues from where the prior ended. Final assembly and trimming happen in an editor — see `editing-and-cutting.md`.

For a true series (multiple scenes, same world), also lock production design (below) so episodes match.

---

## In-place video editing

You don't always need a full regen. Seedance 2.0 supports targeted edits on an existing clip — change one element, keep everything else.

- **Replace:** `edit @video1: replace the red car with a black motorcycle, keep the camera move and background.`
- **Add:** `edit @video1: add light rain and wet reflections on the street, nothing else changes.`
- **Delete:** `edit @video1: remove the person in the background, keep the foreground subject and motion.`
- **Subvert:** `edit @video1: keep the framing and pacing but change the season to winter — snow on the ground, breath fogging.`

Always state what to **keep** as well as what to change, or the edit drifts into a full regeneration. (Note this is an *edit target*, not a *reference* — make that explicit, per the intent rule above.)

---

## Multi-camera coverage

To cut a single moment from several angles (a reaction, a reveal, a hero product turn), generate **coverage** — the same beat shot multiple ways — then assemble in an editor.

```
Coverage of one moment — the toast at the dinner table:
A) wide master: the whole table raising glasses.
B) medium two-shot: the couple clinking glasses.
C) close-up insert: the glasses meeting, wine catching the light.
```

Generate each as its own clip with the **same lighting, wardrobe, and palette** (reuse the aesthetic header and the same references) so they intercut cleanly. Keep one camera move per angle. Then cut master → medium → insert in the edit (`editing-and-cutting.md`).

---

## Sub-second micro-timing

Anchor specific beats and SFX to specific seconds so audio and action land together:

```
0:00 he steps into frame (footstep SFX).
0:01.5 he sets the cup down — sharp ceramic click.
0:03 he looks up exactly as the bell over the door rings.
0:04 line: "right on time."
```

Use this for beat-synced action, lip-sync timing, and SFX hits. Pair with the audio rhythm reference (`advanced-control.md` §2) when you want hits locked to a track's tempo. Keep cues sparse — a handful of precise anchors beats a frame-by-frame script the model can't honor.

---

## Prohibited / Allowed constraint blocks

A clean way to state hard rules — separate what must NOT happen from what should. This reads more reliably than a wall of "no X, no Y":

```
PROHIBITED: cuts, extra people in frame, on-screen text, lens flare.
ALLOWED: motion blur from speed, natural film grain, shallow focus.
```

Keep PROHIBITED at or under 3 items (Seedance has no dedicated negative field; inline `avoid/no` is honored only to a degree, and overloading it backfires — see negatives policy in `production-grammar.md`). Prefer turning prohibitions into positive locks where you can: instead of `no daylight`, write `night, lit only by neon`. The ALLOWED block is the more powerful half — it tells the model what good looks like.

---

## Production design anchors

For a series or multi-shot piece, lock the design language so everything matches. Define it once, repeat it verbatim:

```
[PRODUCTION DESIGN]
Palette: rust orange, muted teal, cream.
Era: late 1970s.
Set-dressing motifs: wood paneling, warm practical lamps, analog clocks, film grain.
Wardrobe: earth tones, corduroy, no modern logos.
```

Drop this block above every shot/segment in the series (it pairs with the aesthetic header from extension chaining). Anchoring palette + era + recurring motifs is what makes separate renders read as one world rather than a grab-bag.

---

## Storyboard phase skeletons

For any multi-shot narrative, lay beats on the classic arc before writing prompts. Use it as a skeleton, then fill each beat with one Shot-Script entry:

| Phase | What it does | Example beat |
|---|---|---|
| Calm | establish world + subject in equilibrium | wide: the village at dawn, quiet, smoke from a chimney |
| Inciting | the disturbance arrives | a rider crests the hill, dust trailing |
| Escalation | stakes rise, pace tightens | villagers scatter, doors slam, camera tightens |
| Climax | peak tension / the decisive action | the confrontation in the square, one held beat |
| Resolution | release, new equilibrium | the dust settles, a door creaks open, calm returns |

For a single 10–15s clip you'll usually compress this to **calm → inciting → escalation** (a hook), or **escalation → climax** (an action beat). For long-form, give each phase its own segment and chain them (extension chaining above). Pace it so energy builds — don't spend half the runtime on Calm.

---

See also: `production-grammar.md` (core formula, negatives, camera-per-shot rule), `realism-and-camera.md` (8 official camera moves, the anti-plastic realism stack), `advanced-control.md` (native JSON, transitions, reference-video replication, first/last-frame, position weighting & the re-prompt tree), `editing-and-cutting.md` (stitching, Track Completion, V2V, multi-cam assembly), `recipes-and-operations.md` (batch/seed protocol, 480p→1080p), `surfaces-and-use-cases.md` (per-use-case templates).


<!-- ═══════ FILE: seedance-director/references/research/continuity.md ═══════ -->

# Research: Continuity editing — sourced notes

Background only. Verify or extend principles here; do not write prompts from this file. See `editing-and-cutting.md` for the prompt-facing craft and `editing-sources.md` for the full bibliography.

Continuity editing is the dominant grammar of mainstream narrative film: a system of conventions that makes a sequence of separate shots read as one continuous, legible space and time. The viewer should never have to wonder *where they are* or *who is facing whom*.

## Key claims and who established them

- **The 180° rule (axis of action).** Keep the camera on one side of an imaginary line connecting the subjects, so screen direction stays consistent — a character facing frame-right keeps facing frame-right across cuts. Crossing the line flips apparent direction and disorients the viewer. Standard continuity-system consensus; codified in Reisz & Millar, *The Technique of Film Editing*, and Bordwell & Thompson, *Film Art*.
  - **Seedance mapping:** the engine has no axis concept, so restate facing direction ("he faces frame-right, she faces frame-left") after *every* angle change. For a critical eyeline match, render shots separately and stitch.

- **Match-on-action (cutting on the action).** Cut during a continuous movement so the motion begun in shot A completes in shot B; the eye tracks the motion and the cut hides. Long-standing editing practice; documented in Reisz & Millar and Dancyger, *The Technique of Film and Video Editing*.
  - **Seedance mapping:** tie the angle change to the kinetic peak — "as her hand closes on the handle, the view shifts." On combat, change angle on the moment of contact.

- **Eyeline match.** A shot of a character looking off-screen, followed by a shot of what they see, links the two by implied gaze; the audience infers spatial relationship. Continuity-system convention; Bordwell & Thompson.
  - **Seedance mapping:** "she looks frame-right; the view moves to what she sees, entering frame-left." Pre-aim the eye with the gaze.

- **Establishing shot → re-establishing shot.** Open wide to fix the geography, move in for detail, return wide periodically to re-orient. Standard convention; Reisz & Millar.
  - **Seedance mapping:** write the arc explicitly within one clip — "wide on the room, in to the hands, back out to the room."

- **Murch's hierarchy of continuity.** In *In the Blink of an Eye*, Walter Murch ranks spatial continuity (2D plane 5%, 3D space 4%) *below* emotion (51%) and story (23%) — continuity can be sacrificed when feeling demands it.
  - **Seedance mapping:** lead with emotion and action; let continuity serve them. But still add the position anchor the engine needs — sacrifice the priority weight, never the spatial statement.

## One-line takeaway

Continuity is about preserving legible space and direction across shots; on Seedance, you preserve it by *restating* position and facing after each angle change, because the engine does not track the axis on its own.


<!-- ═══════ FILE: seedance-director/references/research/action-environment-composition.md ═══════ -->

# Research: Action cutting, environment/establishing, composition grammar — sourced notes

Background only. Verify or extend principles here; do not write prompts from this file. See `editing-and-cutting.md` for the prompt-facing craft and `editing-sources.md` for the full bibliography.

## Action cutting

- **Cut on the action / cut on the hit.** Placing the cut at the peak of a motion (and, in combat, on the moment of contact) hides the edit because the eye is tracking movement. Standard editing practice; Reisz & Millar, *The Technique of Film Editing*; Dancyger, *The Technique of Film and Video Editing*.
  - **Seedance mapping:** bind the angle change to the kinetic peak — "at the instant of impact the angle cuts tight to the recoiling head."
- **Pace ramps toward the climax.** Action sequences shorten ASL as tension rises (consistent with Bordwell's "intensified continuity"). Ramp, don't jolt — accelerate the cutting into the peak, exhale after.
  - **Seedance mapping:** state the *trend* — "angles change more and more frequently, building to the crash." For exact acceleration, stitch.

## Environment / establishing

- **Establish → detail → re-establish.** Open wide to fix geography, move in for detail, return wide to re-orient. Continuity convention; Bordwell & Thompson, *Film Art*.
  - **Seedance mapping:** write the full arc inside one clip — "wide on the market, in to the vendor's hands, back out to the square."
- **Graphic match / match cut.** Transition on a shared shape, color, or direction of motion to link two spaces (the bone-to-spacecraft cut: shape + motion). Discussed across editing literature; Eisenstein on graphic conflict, and continuity texts on the match cut.
  - **Seedance mapping:** keep the matched element identical in shape/color/motion *and* screen position across the change. Hero match cuts between unrelated worlds are more reliable rendered separately with shared end/start frames, then stitched.

## Composition grammar

- **Rule of thirds; lead room / nose room; depth layering (foreground/midground/background); frame-in-frame; size↔emotion.** Foundational framing conventions; covered in Bordwell & Thompson, *Film Art*, and standard cinematography references. Size↔emotion (closer = more intimate/intense, wider = isolated/contextual) is the long-standing intuition that shot scale carries feeling.
  - **Seedance mapping:** state placement in plain spatial terms (thirds, lead room in the gaze direction, three depth layers, subject framed through a doorway). Choose shot size as an emotional dial, not just coverage. These align with Murch's eye-trace (7%) and 2D-plane (5%) criteria.

## One-line takeaway

Action cuts land on the kinetic peak; environments establish-detail-re-establish and link via match cuts; composition is set by placement, depth, and a size-for-emotion choice — all writable into a single Seedance clip, with hero match cuts and exact pacing reserved for stitching.


<!-- ═══════ FILE: seedance-director/references/research/montage-and-rhythm.md ═══════ -->

# Research: Montage theory + rhythm/pacing — sourced notes

Background only. Verify or extend principles here; do not write prompts from this file. See `editing-and-cutting.md` for the prompt-facing craft and `editing-sources.md` for the full bibliography.

Where continuity editing hides the cut to preserve a continuous reality, montage *uses* the cut as a meaning-making tool: the collision of shots produces an idea or emotion not present in either shot alone.

## Key claims and who established them

- **The Kuleshov effect — meaning from juxtaposition.** Lev Kuleshov's montage experiments (early Soviet cinema, c. 1910s–1920s; associated also with Pudovkin) showed that the same neutral face appears to express hunger, grief, or tenderness depending on the shot it is cut against. Emotion is manufactured by adjacency, not by the single shot. Historians dispute the exact original footage; the principle is foundational.
  - **Seedance mapping:** order beats so adjacency carries the meaning — "her unreadable face, then the empty chair, then her face again." The sequence does the work.

- **Eisenstein's montage typology.** Sergei Eisenstein (*Film Form*, *The Film Sense*) classified montage by what governs the cut: **metric** (fixed time interval), **rhythmic** (driven by content's movement/tension), **tonal** (driven by emotional tone, light, color), plus **overtonal** and **intellectual** (cuts that argue an idea by collision).
  - **Seedance mapping:** rhythmic (motion-led) and tonal (mood-led) montage hold reasonably within a clip; lock the connective thread (an accent, a shared cold light). Strict metric montage needs stitching — the engine won't hold an exact frame interval.

- **Rhythm as the editor's primary material.** Karen Pearlman, *Cutting Rhythms*, frames editing rhythm as a deliberate craft built from physical, emotional, and event rhythms — the editor shapes movement and timing, not just trims.
  - **Seedance mapping:** influence rhythm within a clip via how often the angle changes and how fast the action moves; precise rhythm control comes from stitching.

- **Average Shot Length (ASL) and the trend toward faster cutting.** David Bordwell (*The Way Hollywood Tells It*) describes **"intensified continuity"** — modern mainstream film cuts faster, with tighter framings and more camera movement. ASL as a measurement appears in Bordwell & Thompson, *Film Art*; the statistical lineage traces to Barry Salt's quantitative style analysis.
  - **Seedance mapping:** treat genre ASL bands as typical ranges (drama ~6–12s, action ~1.5–4s). Plan pace to *ramp* toward a climax; for exact ASL control, stitch clips.

## One-line takeaway

Montage makes meaning from the order and rhythm of shots; on Seedance, adjacency (Kuleshov) and motion/mood-led montage work within a clip, but metric montage and precise ASL require stitching.
