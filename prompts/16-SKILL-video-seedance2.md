# Seedance 2.0 — prompt grammar, director mode, motion

> **What this is.** seedance-2-prompter, complete. Stage 13 MOTION owns this. The 6-step formula, the size ladder, @Image/@Video/@Audio binding, camera registers, native audio, Tier-3 director mode, the anti-drift sixteen-slot spine, dance and movement.

> **Bundle of 4 source files, 282,972 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `seedance-2-prompter/SKILL.md` | 65,528 |
| 2 | `seedance-2-prompter/references/director-mode.md` | 98,940 |
| 3 | `seedance-2-prompter/references/director-v3.md` | 56,986 |
| 4 | `seedance-2-prompter/references/edm-dance-and-movement.md` | 61,518 |

---

<!-- ═══════ FILE: seedance-2-prompter/SKILL.md ═══════ -->

---
name: seedance-2-prompter
description: Write Seedance 2.0 / Pro / Fast video prompts (VIDEO model, not image). Use whenever the user wants a Seedance prompt or any AI video gen prompt — text-to-video, image-to-video, reference-to-video, V2V edits, multi-shot sequences, timeline prompting, or Higgsfield Marketing Studio work. Covers the official 6-step formula, the less-is-more size ladder (60–120 words; see Rule zero), motion-only i2v prompting, reference role-assignment, camera/lens/lighting vocabulary, the four camera registers, the FOV degree anchor, the atmosphere source rule, realism and phone-look stacks, native audio, the NO BGM convention, and negative patterns. For Tier-3 renders (reference-anchored characters, M1–M5 cinematography) read references/director-mode.md. For Tier-3+ renders where the enemy is drift — locked staging, ensembles, lipsync closures, strobe, heavy-mass action — read references/director-v3.md and its sixteen-slot spine. When people are dancing to electronic music, read references/edm-dance-and-movement.md.
---

# Seedance 2.0 Prompt Builder

Seedance 2.0 is ByteDance's text/image/video → video generation model exposed via ModelArk and the Higgsfield Marketing Studio. This skill captures how to write prompts that produce coherent, cinematic, multi-shot output — and how to avoid the things that make outputs drift, plastic up, or read as AI.

The model variants are **Fast**, **Standard**, and **Pro**, with clip durations **4 – 15 seconds**, output up to **2K resolution**, native synced audio, and four-modal input (text + image + video + audio). Aspect ratios: 21:9, 16:9, 4:3, 1:1, 3:4, 9:16. Iterate at 480p, finalise at 720p or 2K. Capture the response seed so you can isolate the effect of prompt edits from random variation.

---

## Rule zero — less is more (the size ladder)

**This rule overrides everything below.** Seedance is a strong auto-director: given mood + one clear arc, it handles blink timing, fabric, micro-acting, and sound design better than a prompt that micro-manages them. Over-specification causes conflicting instructions, rigid acting, and jitter. The official ByteDance guidance is **60–100 words**; the top community generations are single vivid paragraphs.

Pick the tier BEFORE writing, based on shot count and duration — never on how much detail you could add:

| Tier | Use case | Length | Grammar |
|---|---|---|---|
| **1 (default)** | 4–8 s, single shot, t2v or i2v | **60–120 words** | One flowing paragraph. No timestamps, no shot numbers. |
| **2** | 8–12 s, dialogue and/or multiple references | 120–250 words | Paragraph + short reference role lines. Timestamps only if two distinct beats must land at exact times. |
| **3** | 15 s multi-shot production (transformations, fights, montages) | 300–600 words | Numbered shots or `[Ns]` timestamps, per-shot camera + action, consistency tail. For reference-anchored production work, use **director mode** → `references/director-mode.md`. |
| **3+** | 15 s production where nothing may drift (ensembles, locked geometry, lipsync, strobe, heavy mass) | 900–1,400 words | The sixteen-slot spine, every fact in exactly one slot → **director v3** → `references/director-v3.md`. Tier 3+ is the one place a long prompt is correct: the length is all locks, no flourish. |

Tier-1 discipline:

- **One flowing action sentence**, not a beat grid. Timestamp grids on a 4–8 s clip over-constrain and read as rigid.
- **Don't choreograph micro-acting** (blink at 0.3 s, foil crinkle at 2.6 s). Give the emotional arc; the model fills the physiology.
- **One lighting line, one realism clause** — not a seven-layer stack.
- **≤3 negatives**, targeted.
- **For i2v: never re-describe what the image shows.** The image carries identity, wardrobe, and scene. The text carries motion, emotion, camera, and what changes. One short role line per reference (`@Image1 = identity and wardrobe — ignore its camera angle`), then `preserve composition and lighting` instead of re-narrating pixels.

If a draft prompt exceeds its tier budget, cut adjectives and trust the model — every word must describe something observable that the image or the model wouldn't supply on its own.

---

## Three registers — quick mode, director mode, director v3

This skill merges three prompting systems. Route by deliverable, and **never blend two grammars in one prompt.**

| Register | When | Grammar | Length |
|---|---|---|---|
| **Quick mode** (default) | Iteration, UGC, hooks, single shots, simple i2v, anything Tier 1–2 | The 6-step formula in this file, flowing paragraph | 60–250 words |
| **Director mode** | Tier-3 production: reference-anchored characters, locked composition, multi-character blocking, cinema plates, final renders | Ten labeled blocks in fixed order: Scene & Mood → Frame Map → Subject Lock(s) → Cross-Frame Rules → Movement → Last Frame → World Plate → Sound Bed → Capture Realism → Camera Capture. Five cinematography modes: M1 Narrative, M2 Studio, M3 Action, M4 Performance, M5 Atmospheric. Full grammar: `references/director-mode.md` | 280–400 single-shot, ≤600 multi-shot |
| **Director v3** (top register) | Tier 3+ maximum rigor, when the enemy is **drift**: bodies moving between cuts, geometry inverting, lipsync closures vanishing, wardrobe mixing across figures, ensembles, strobe, heavy-mass action | Sixteen slots in locked order: Header → Style Prefix → No On-Screen Text → CRITICAL blocks → Assets → Geometry Map → First Frame → Optics → Camera → Light & Colour → Atmosphere → Action Timing → Physics → Acting → Audio → Locks. Full grammar: `references/director-v3.md` | 900–1,400 words for a four-shot, four-asset sequence |

**Choosing between director mode and v3.** Reach for **director mode** when the *mode archetype* is the useful abstraction — you want M2 Studio's crafted look or M4's pit-photographer register and the ten blocks fall out of it. Reach for **v3** when specific things must not drift and you need a named lock for each one: absolute LEFT/MIDDLE/RIGHT staging with depth planes, lens locks in FOV degrees, a colour doctrine with every band nailed to a source, a physics chain scaled to stated mass, counted lip closures, ALL-CAPS CRITICAL blocks promoting whatever the model keeps dropping.

Director-mode signature moves (read the reference file before using): pre-prompt confirmation check, `@imageN` reference tags matching a numbered attach list, volumetric atmosphere in three depth registers (foreground/midground/deep-background haze — flat air is the headline AI tell), mid-grey seamless for character builds (never pure white), per-zone specular kill on skin, contrast curve stated three ways, Last Frame as a composition target, diegetic-only Sound Bed.

Director-v3 signature moves: every fact in exactly one slot and nothing stated twice · Assets as `identity + THIS SCENE action + fidelity assertion` on one line · the Geometry Map that stops bodies drifting between cuts · FOV in degrees as the snap value · the four camera registers with dutch cant in degrees and a matching cut rate · the 70/20/10 colour doctrine · atmosphere where every visible vapour has an emitter in frame · `NO BGM` as a production term · the bilabial closure count for lipsync · the strobe cadence quarantine · Locks as a positive ordered chain.

**Four deliberate disagreements between the registers.** Each is resolved in a precedence table under HOUSE RULES in `references/director-v3.md`; the summary:

**Brand names.** Quick mode allows brand-vibe anchors (`ARRI ALEXA aesthetic`, `iPhone 15 Pro footage`, `Kodak Portra 400`) because the official guide and the top community prompts use them and they reliably pattern-match. Both director registers ban brands and write camera **behavior** instead (`wide-latitude cinema capture`, `shot on large-format film`, `vintage 75mm 2x anamorphic character, oval bokeh`).

**Aspect ratio and age words.** Quick mode states the ratio in the prompt (`Vertical 9:16`, `Total: 15s / 16:9`) and uses the official exemplars' age language (`a man in his fifties`). Director v3 keeps the ratio in the UI and describes age-blind, by role, build, bearing, hair and wardrobe.

**Technical capture numbers.** The *Rhythm vocabulary* section below bans `24fps` and `shutter 1/50` alongside f-stops and ISO, and that is correct at 60–120 words where a spec displaces direction. Director v3's slot-2 Technical line is the single exception: `real-time 24fps, true 180-degree shutter with a real 1/48 second exposure, genuine photographic motion blur` is the **cadence clause**, the strongest anti-artifact instruction in that grammar. Aperture and ISO stay banned in both registers.

**Negation volume.** Quick mode caps negatives at 3 inline `avoid X` clauses. Director v3 runs many more, but structurally — each negation lives inside the slot that owns it (render quad, text block, FOV defence battery, atmosphere shape negations, closing tail) rather than floating loose as a defensive stack. The cap still applies to anything outside a slot.

Both approaches work. **Never mix two registers' rule sets in one prompt** — pick the register and take the whole thing.

---

## Input modes are mutually exclusive — First/Last Frame OR References, never both

Before writing the prompt, decide which entry point you are in. Seedance 2.0 exposes two separate modes and **they cannot be combined in the same generation**:

| Mode | What it accepts | When to use |
|---|---|---|
| **First/Last Frame Mode** | A starting image, plus an optional ending image, plus the text prompt. **No other reference images, videos, or audio clips are allowed.** | You want the literal first frame (and optionally the last frame) of the clip locked to specific image(s) and the model to interpolate the motion between them. |
| **Universal Reference Mode** (a.k.a. Omni Reference) | Up to 9 images + 3 videos + 3 audio clips (12 files total), all referenced inline as `Image 1`, `Video 1`, `Audio 1`, etc. **You cannot pin a hard first/last frame here** — references guide identity, motion, style, and audio, but the model picks the opening frame. | You're locking character identity, camera motion, scene plates, or audio rhythm using mixed assets. |

**Practical implication.** If a brief says *"start from this still and use these three other images for character consistency,"* you cannot do that in a single Seedance render. Pick one:

- Choose **First/Last Frame Mode** and accept that identity comes from the first frame only (plus the text prompt). Bake the character description into the prompt and trust the first frame to anchor the look.
- Choose **Universal Reference Mode**, drop the hard first frame, and reference the identity image as `Image 1`. The model will open on a frame it composes from your references and prompt, not on your uploaded still.

If you need both behaviours, do it in two passes: generate in Universal Reference Mode, screenshot the cleanest opening frame, then feed that frame back as the first frame in a second First/Last Frame render.

> **File limits.** Max 9 images (each <30 MB, JPEG/PNG/WebP/BMP/TIFF/GIF), 3 videos (MP4/MOV, 2–15 s each), 3 audio clips (MP3/WAV, <15 s and <15 MB each), 12 files total. **Real-face photos are blocked** — content containing identifiable real faces will be rejected by the platform pre-filter.

---

## The prompt formula

Seedance accepts flowing natural-language prose. The official ByteDance guide describes a **6-step formula** — **target length 60–100 words**. Shorter loses detail; longer accumulates conflicting instructions.

| # | Element | Status | What it carries |
|---|---|---|---|
| 1 | **Subject** | required | WHO (or what) is in the frame — specific visual features, not abstract roles |
| 2 | **Action** | required | WHAT they are doing — one primary verb, quantified intensity |
| 3 | **Environment / Scene** | strongly recommended | the world around them — location, time of day, weather, materials |
| 4 | **Camera** | strongly recommended | shot type, lens behavior, one primary movement, framing |
| 5 | **Style** | strongly recommended | the look — capture medium, palette, era, mood |
| 6 | **Audio** | optional, powerful | ambient sound, dialogue in quotes, key foley moments |
| 7 | **Constraints / Negatives** | strongly recommended | `avoid jitter`, `avoid bent limbs`, `no supers`, etc. |

**Always end with a single global style sentence** — Seedance reads it as a filter applied to the whole clip. Skipping it lets the model default to its own aesthetic, which is too clean and too plastic.

### Three non-negotiable rules

**0. Respect the size ladder.** 60–120 words unless the brief is a genuine multi-shot production. Length follows shot count, never enthusiasm.

**1. One primary action.** Seedance 2.0 performs measurably better when the prompt names one primary action with supporting environmental motion, instead of several competing focal points. Multiple things happening = a multi-shot prompt (see below), not a longer single beat.

**2. Separate camera movement from subject movement.** The single most common failure mode. Describe subject motion in one sentence, camera motion in another.

```
Good: The dancer spins slowly. Camera holds fixed framing on the medium-shot.
Bad:  Spinning camera around a dancing person.
```

Mixing them produces uncontrollable, shaky output.

---

## The realism stack — fighting AI slop and plastic skin

Without an explicit realism cue at the end, Seedance defaults to its house aesthetic: glossy skin, even lighting, polished motion, soft commercial color. That look is the AI tell.

**The layers below are a menu, not a checklist.** On Tier-1 prompts pick **one or two lines total** (capture medium + one skin/lighting truth). Stacking all seven layers belongs only in Tier-3 productions — on a short clip it bloats the prompt and fights itself.

### Layer 1 — the "no 3D, no cartoon, no VFX" trick

For anything that should read as real — humans, monsters, animals, organic materials — add this exact phrase to the closing style line:

> *no 3D, no cartoon, no VFX*

This single trio forces Seedance away from rendered-looking output and toward photographed-looking output. It is the highest-leverage anti-slop instruction in the entire prompt grammar. Use it on every realism-priority prompt unless you specifically want stylization.

### Layer 2 — capture medium

The single most important realism choice. Name a specific stock, sensor, or device:

| Medium | Phrase |
|---|---|
| Cinematic 35 mm | `strong 35mm film look, heavy film grain, Kodak Portra 400, halation on highlights, soft highlight rolloff` |
| 16 mm grain | `16mm film grain, slight gate weave, organic color shifts` |
| Super 8 | `Super 8 home-movie texture, soft focus, heavy grain` |
| ARRI digital | `ARRI ALEXA aesthetic, cinematic dynamic range` |
| Sony cine | `Sony FX3 handheld, S-Log3 graded warm, shallow depth of field` |
| iPhone | `iPhone 15 Pro footage, native iPhone color science, no LUT, no grade` |
| Older iPhone | `iPhone 6 video quality, soft sharpness, muddy shadows, compressed dynamic range` |
| DV camcorder | `DV camcorder 480p, interlaced lines, blown-out highlights, date stamp lower-right` |
| Documentary | `documentary-style, naturalistic, handheld observational` |

### Layer 3 — lens behavior

Tells the model how light hits glass. Pick one or two:

- `subtle chromatic aberration near frame edges`
- `anamorphic lens flare, blue streak across highlights`
- `lens breathing on focus pulls`
- `noticeable focus breathing`
- `sharp but imperfect focus`
- `motion blur on fast actions`
- `dust on lens catching backlight`
- `wide-angle lens (strong distortion)` for POV
- `long lens compression` for telephoto looks

### Layer 4 — skin and material truth

This kills the plastic look specifically. Use on any human-in-frame prompt:

- `visible skin pores, peach fuzz on cheeks`
- `subsurface scattering in earlobes and nostrils`
- `flyaway hairs catching rim light, strand-level detail not helmet hair`
- `fabric weave visible, natural creases and wrinkles in clothing, not steam-pressed`
- `slight oil sheen on T-zone, real human asymmetry`
- `weathered hands, visible knuckle lines, slight tremor`

### Layer 5 — atmosphere as a participant

Empty air looks fake. Give the air weight:

- `dust motes drifting through window light`
- `humidity haze compressing the background`
- `breath visible in cold air`
- `steam curling visibly into the light shaft`
- `volumetric dust storm` / `volumetric depth haze`
- `rain in foreground, shallow depth of field with bokeh streetlights`

**The source rule — the one atmosphere rule that fails loudly.** *Density* is always safe: air at real thickness, a scattering gradient from lens to horizon, blacks lifted at every depth. **Visible vapour shapes are not.** A plume, a tendril, a wisp, a swirl, a shaft of light only exists when something in frame is physically making it — a lit cigarette, a footfall blasting dust, breath condensing in cold, steam off a cup surface. Name the source and the emission, or the model supplies fog-machine texture and the shot reads staged.

With no emitter in the scene, close the atmosphere line with the shape negations: *no plumes, no banks, no tendrils, no wisps, no swirls, no fog-machine texture, no volumetric shafts, no god rays.* Naturally foggy exteriors are legitimate but are written as **uniform density and falling visibility** (`thick cold fog holding at uniform density, visibility falling off with distance`), not as shapes moving through frame — keep the shape negations even then.

**Clean air is stated just as hard as heavy air:** `the air is clean — no haze, no density, no visible beams, no suspended particulate, full clarity to the back wall`. Silence gets you the model's default, which is neither.

### Layer 6 — lighting truth (one motivated source)

Seedance's default is "soft pleasant key with fill." Name a specific condition instead:

- `motivated only by the practical lamp on the desk — rest of room falls into shadow`
- `single window as key, no fill, deep shadow side`
- `mixed color temperature — tungsten interior, daylight spilling through window, no white balance correction`
- `overcast soft top light, no shadows on the ground, flat documentary lighting`
- `streetlight sodium-vapor orange on one side, blue moonlight on the other, hard color contrast`
- `harsh single-source overhead industrial light, deep dramatic shadows`

### Layer 7 — human-operator camera grammar

Realism dies when the camera floats like a drone. Tie movement to a human body:

- `handheld with organic shake, not stabilized — micro corrections as operator breathes`
- `slight bob from walking, footsteps visible in the motion`
- `operator adjusting framing mid-shot — small reframe right`
- `gimbal walk but with a real subtle vertical bounce`
- `tripod locked-off, but with a single micro-bump as someone passes the cable`

Words that trigger video-game smoothness and should be avoided unless you want that: `smooth glide`, `floating`, `effortless tracking`. Replace with `motivated`, `organic`, `tied to operator's feet`.

**Pick one camera register and hold it.** The register governs cant, cut rate and how much of the frame is allowed to be still — and mixing two produces the averaged, characterless move that reads as AI. Deduce it from the brief; only ask if genuinely split.

| Register | Dutch cant | Cuts | Language |
|---|---|---|---|
| **Locked-off** | 0° | 1–2 shots or a oner | tripod-weighted, or an extremely slow push; stillness is the subject |
| **Gentle handheld** | 3–10° | 3–5 shots, 2.5–4s | floating, drifting, riding breath, small organic corrections; frames settle before moving on |
| **Heavy handheld** | 12–25° | 4–6 shots, 1.5–2.5s | jolting, bobbing, snapping corrections, high-frequency vibration underneath; every frame mid-move but the eye can still land |
| **Violent handheld** | 25–45° | 4–6 shots, 1.5–2s | punching in and ripping back, whip-pans, hard surges; nothing settles |

Toward locked-off and gentle: grief, memory, waiting, ritual, solitude, portrait, dialogue that matters, "quiet," "still," "slow," "elegant." Toward heavy and violent: a beat drop, choreography, a chase, a fight, a crowd, a crash, a named BPM, "chaotic," "aggressive," "go crazy."

**Every register except locked-off closes with the same clause**, and it is load-bearing — without it, violent handheld returns genuinely broken footage rather than energetic footage:

> *never locked, never stabilized, never mechanically smooth, never gimbal-glide, never floaty drone — real shoulder-mounted mass, weight shifts, breath, human over-correction, every frame mid-move but always smooth and continuous in its own travel.*

A still subject inside a violent camera is a real choice — state the split explicitly so the model doesn't average the two.

### The closing realism stack — Tier 3 only

The Higgsfield production prompts converge on a master string for 15 s cinematic productions. **Tier-1/2 prompts should NOT use this** — they get a single line like `Native iPhone look, real skin texture` or `35mm film look, natural imperfections, no 3D, no cartoon, no VFX`. For Tier-3 renders, paste verbatim and adjust:

> *cinematic lighting, photorealistic, grounded realism, strong 35mm film look, heavy film grain, sharp but imperfect focus, noticeable focus breathing, motion blur on fast actions, halation on highlights, soft highlight rolloff, slightly desaturated tones, ARRI ALEXA aesthetic, practical VFX feel, minimal CGI look, natural imperfections, subtle chromatic aberration near frame edges, no 3D, no cartoon, no VFX.*

---

## Phone-look prompts (UGC / Reels / "shot on iPhone")

Phone realism is a different formula from cinematic. Lead with the device, then push toward casual imperfection. Do not borrow the cinematic stack — phones are flat, compressed, casually framed.

### The phone-look opener template

> *Vertical 9:16 iPhone 15 Pro handheld footage, [subject + action]. Auto-focus briefly hunting before locking, slight overexposure clipping on bright sources, native iPhone color science (slightly warm, slightly saturated), no LUT, no color grade applied. Subject framed slightly off-center the way someone holding a phone one-handed would frame it. Camera shake tied to operator's breathing and footsteps. [diegetic audio cues]. No film emulation, no anamorphic, no cinematic grade.*

### Phone-specific tells to bake in

- `auto-exposure adjusting mid-shot when lighting changes` / `auto-exposure briefly hunts`
- `auto-focus pulse / hunt before locking`
- `slight rolling shutter wobble on quick pans`
- `compressed dynamic range — bright windows blow out, shadows crush`
- `one-handed framing, subject not perfectly centered`
- `casual reframe mid-shot as the operator adjusts`
- `native phone color, no LUT, no grade`
- `mono speaker audio character` (for older phone playback)

### Older phone / lo-fi authenticity

For 2010s authenticity: `iPhone 6 video quality, soft sharpness, muddy shadows, mono speaker audio character, lower bitrate compression artifacts in dark areas`.

For 2000s camcorder: `DV camcorder 480p, interlaced lines, blown-out highlights, date stamp lower-right, mini-DV tape noise`.

### When to switch off phone-look

If the brief is cinematic, never name a phone — the phone-look terms will fight the 35 mm grain instructions and you'll get a muddy hybrid. Pick one mode and commit.

---

## Multi-shot inside one generation

Seedance 2.0 handles multiple shots in one render. Two interchangeable approaches — pick the one that fits the brief.

### Approach A — flowing prose with explicit cut keywords

Write one paragraph. Mark each cut with a camera direction:

- "Hard cut to a wide shot of …"
- "The camera cuts to a close-up on …"
- "The camera smash-cuts to a POV shot looking up at …"
- "The camera pushes in to a tight detail on …"
- "Cut to:"

Soft transitions also work: *"crossfades to"*, *"dissolves through"*, *"whip-pans into"*. If you don't want them, **say so explicitly** at the top: *"All transitions between shots are hard cuts; never crossfades, dissolves, or whip-pans."*

### Approach B — timeline prompting with explicit timestamps

**Only for 10–15 s sequences with 3+ distinct beats.** A 4–8 s single shot gets one flowing action sentence — a timestamp grid on a short clip over-constrains the model and produces rigid, stagey acting. For tight pacing control on long sequences, use bracketed timestamp markers at the head of each beat:

```
[0s] Wide shot: <subject + action>. <camera + lighting>.
[3s] <Camera transition>. <New shot type and subject beat>.
[6s] <Camera transition>. <Resolution shot>.
```

For 5-second clips: 2–3 timestamps. For 10-second clips: 3–4. For 15-second clips: 4–6. Each beat = **one** shot type + **one** camera instruction + **one** action + one atmospheric note.

Between beats, add a connective cue: *"Slow push in begins"*, *"Camera begins tracking right"*, *"Rack focus from background to subject"*, *"Cut to:"*.

### Tell the camera what it is NOT doing — the locked-perspective trick

The single highest-leverage instruction for POV and locked-camera shots is to **name what the camera shouldn't do**:

> *no cuts, no zoom, natural head movement, single continuous shot*

Without this, Seedance defaults to cutting between angles and the POV illusion breaks. Apply the same trick to other constraints:

- `locked-off, no pan, no tilt, no dolly`
- `no soft transitions, every cut is hard`
- `no speed-ramping, real-time throughout`

---

## Format-specific patterns (Higgsfield production library)

These are the high-performing format recipes from real Seedance 2.0 production work. Each has a distinct structure.

### Transformations — 6-shot escalation arc

Best-performing format on Seedance. Structure: calm → threat → transformation → aftermath. Number each shot explicitly.

**Skeleton:**
```
Montage, multi-shot action Hollywood movie, don't use one camera angle or single cut,
cinematic lighting, photorealistic, 35mm film quality, professional color grading,
sharp focus, high detail texture, film grain, depth of field mastery, ARRI ALEXA aesthetic.

<one-paragraph scene description: who, where, what transforms, escalation tone>

Shot 1: <calm setup, ambient camera>
Shot 2: <threat appears, tracking camera>
Shot 3: <recognition close-up>
Shot 4: <transformation, camera jolts with each beat>
Shot 5: <climactic action, wide low-angle, camera shudders>
Shot 6: <return to baseline, calm framing>

Total: 15s / 6 shots / 16:9
```

### Orbs — single-shot first-person POV with powers

One continuous shot, hyper-chaotic handheld, 15 seconds. The camera IS the character's eyes. Specify VFX inline using brackets.

**Opener (paste verbatim):**
> *Single continuous shot, first-person POV perspective, the camera IS her eyes, hyper-chaotic handheld motion, completely unstabilized, violent raw human movement, constant micro-jitters, aggressive head swings, abrupt jerks, frequent over-rotation and harsh correction, moments of near motion blur loss, no smoothness at all, no stabilization, wide-angle lens (strong distortion), subtle chromatic aberration near frame edges, 15 seconds, her hands always visible in frame, no music only raw SFX, cinematic lighting, photorealistic, grounded realism, strong 35mm film look, heavy film grain, sharp but imperfect focus, noticeable focus breathing, motion blur on fast actions, halation on highlights, soft highlight rolloff, slightly desaturated tones, ARRI ALEXA aesthetic, practical VFX feel, minimal CGI look, natural imperfections.*

Then describe the location, the enemies, the power, and the escalation. VFX goes inline: `[VFX: branching electric circuits pulsing with white-blue current, sparks jumping between fingers]`.

### POV — locked-perspective continuous shot

Lock the perspective. Name what the camera is NOT doing. Describe one action arc.

**Pattern:**
```
One continuous shot, POV [role] perspective in [location], no cuts, no zoom, natural head movement,
<action arc beat by beat>,
<sensory cues — breath sounds, dust in the air, footsteps>,
cinematic, photorealistic, ultra detailed, motion blur on hits.
Total: 15s / 1 shot / 16:9
```

### Fights — location + mismatch + escalation

Three required ingredients: clear location, clear power mismatch, defined escalation arc. Describe choreography beat by beat — Seedance executes literally.

Use speed-ramping syntax inline in CAPS: `RAMPS TO SLOW MOTION as the blade arcs through the air — SNAPS BACK as she counters with an elbow`. The caps signal to Seedance that these are pacing directives, not literal text overlays.

### Animation — timed segments with physics

Break the 15 seconds into timestamped segments. Use a keyframe image as style reference. Describe physics (particle sim, dust, energy VFX) as precisely as you describe character actions.

**Pattern:**
```
@image is the first keyframe and style reference.
Cinematic stylized 3D animation — photorealistic <environment>, stylized characters.
Hero: <description>. Monster: <description>. Setting: <description>.
High FPS, realistic particle physics.

0–3s: <beat>
3–6s: <beat>
6–9s: <beat>
9–12s: <beat>
12–15s: <resolution>

<style line>. <aspect ratio>.
Total: 15s / 1 shot / 16:9
```

---

## Multimodal references (Universal Reference Mode only)

This section only applies in **Universal Reference Mode** — if you're in First/Last Frame Mode, none of these references are accepted alongside your start/end frames.

Upload images and videos to lock identity, action, or style. Reference them inline as **Image 1, Image 2, … Image N** and **Video 1, Video 2, … Video N**. Order matters — `Image 1` is whatever you upload first.

**One short role line per reference — never re-narrate its contents.** The model reads the pixels; your job is only to assign the role and scope:

- `@Image1 = identity and wardrobe — ignore its camera angle and background`
- `use @Image1 as starting frame` / `use @Image2 as ending frame`
- `do not use the attached image as the first frame` (identity-only lock)
- `match the painted art style of @Image2 throughout`

Re-describing the reference ("long brunette hair, grey tee, seatbelt across chest…") wastes the word budget and creates text-vs-pixels conflicts that cause drift.

### Reference verbs that work

`Reference`, `Extract`, `Combine`, `Follow`, `Generate from`, `using the composition from`, `maintaining consistent <feature>`.

### Templates

**Multi-angle subject (use when uploading 2–3 angles of the same thing):**
> *"Reference / Extract / Combine + [Image N]'s [Subject], generate [Scene Description], maintaining consistent [Subject] features."*

**Multi-image reference (different elements per image):**
> *"The scene is set inside the location from Image 4. The character from Image 1 is wearing the outfit from Image 2, doing the action from Video 1. The logo from Image 5 sits in the bottom-right corner of the screen."*

**Action / camera / effects from a reference video:**
> *"Reference [Video N]'s [action description], generate [scene], maintaining consistent action details."*

### Identity-locking workflow

When generating multiple shots of the same character across separate renders, identity drifts. Counter it:

1. Generate the first shot with text-only character descriptions.
2. Screenshot the cleanest frame of each character.
3. Upload those screenshots as `Image 2`, `Image 3`, etc. for subsequent renders.
4. Reference them inline: *"Anna (referencing Image 2) walks across the floor…"*.

Step 3 puts you in **Universal Reference Mode** — if you also need to pin the literal opening frame, that render has to be in First/Last Frame Mode instead, losing the multi-image references.

---

## Text in video (native — Seedance renders supers itself)

Seedance 2.0 generates text overlays as part of the video. **You don't need post layers** unless you want full control of font, kerning, and timing.

### Slogan / title text

Pattern:
> *"[Text content] + [Appearance timing] + [Position] + [Appearance method], [Text style (color, font)]."*

Example:
> *"The text 'NO PRODUCT.' slams in lower-third in white bold sans-serif on the door slam, with a slight chromatic-aberration shimmer."*

### Subtitles

> *"Subtitles appear at the bottom of the screen with the content '…', synchronised with the audio rhythm."*

### Speech bubbles

> *"[Character] says: '…'. A speech bubble appears around the character with the dialogue text."*

### When to ask Seedance NOT to render text

If you plan to add supers in post, say so explicitly at the top:
> *"No text overlays, no subtitles, no on-screen captions anywhere in the sequence — all storytelling is visual."*

Without this line, expect Seedance to invent some.

### Practical limit

Use common characters. Avoid rare glyphs and special symbols — they tend to render as garbled shapes. Chinese, Japanese, and other CJK text often renders poorly even when prompted natively; if precision matters, render the text in post.

---

## Audio and dialogue (Seedance 2.0 generates synced audio natively)

When dialogue is in the scene, **put it in double quotes inside the prompt body**. The quotation marks signal to the model to prioritise audio generation matching the visual.

> *Defense attorney declaring "Ladies and gentlemen, reasonable doubt isn't just a phrase," footsteps on marble, jury shifting, courtroom drama.*

For ambient / SFX, use a comma-separated raw list — this works better than a paragraph:

> *SFX: electric crackle, sphere hum surge, energy burst, crawling creature skitter, deep metallic titan rise, sharp discharge pop, lightning chain blast, slow-motion electric hum stretch, snap impact.*

For silent generation: write at the top of the prompt *"silent generation, no synthesised audio, NO MUSIC NO SFX"* or set `generate_audio: false` at the API level.

The model handles dialogue lip-sync at millisecond precision when audio generation is on.

### The NO BGM convention — when a scene must land without score

**Write `NO BGM`, expanded once as "no background music", rather than "no music".** The bare phrase reads as a weak stylistic preference and loses to the model's strong prior that generated video wants a score under it. `NO BGM` is a production term and reads as a hard spec.

**Name the specific forms it must not generate.** A bare negation leaves room for an "ambient texture" or a "tone bed" and the model considers the instruction honoured:

> *NO BGM — no background music of any kind. No score, no soundtrack, no instrumental, no underscore, no ambient musical pad, no drone, no tone bed, no swell, no sting, no humming, no whistling, no lyrics. Diegetic sound effects and room tone only. Nothing musical anywhere at any point.*

**On a scene that must land silent, put it in the opening line of the prompt, not the closing audio line.** Audio instructions carry more weight early; by the time the model reaches a closing audio clause it has already decided what the piece sounds like. Restate it at the end as the closing clause.

**Attached-track lock.** When an audio or video reference is attached and it is meant to be the whole soundtrack, say so as an exclusive: *the attached clip is the sole and complete audio source for this sequence. Generate no additional audio of any kind — no room tone, no foley, no ambience, no breath, no added dialogue, NO BGM.* The attached clip also owns all internal timing — never impose per-beat timing on top of a lipsync take.

**The unheard-track technique** lets bodies sing with nothing musical in the mix: *NO BGM in the mix — the track is not audible. Only the voices, a little off-key, singing roughly in time to the unheard 87 BPM beat: "[lyric]". Plus room tone, footfalls, sofa creak, laughter, fabric.*

**When lip closures come back mushy or absent**, the fix is phoneme-level: write the lyric verbatim, then describe where the lips seal. Bilabials — **B, M, P** — are the only closures the eye actually reads as real lipsync, and **counting them** is what makes the model hit them (`four hard lip seals across the sequence — on the M ending TIME, the M starting ME, the B starting BEEN, the B starting BEFORE`). Full protocol, including mouth-visibility locking and why strobe eats closures: `references/director-v3.md`, "The Lipsync Protocol."

---

## Video editing operations (V2V)

Seedance 2.0 also handles operations on an existing uploaded video.

| Operation | Template |
|---|---|
| **Add element** | `At [time position] + [spatial position] of [Video N], add [element].` |
| **Remove element** | `Remove [element] from [Video N], keep everything else unchanged.` |
| **Modify element** | `Replace [original element] in [Video N] with [new element].` |
| **Extend forward / backward** | `Extend [Video N] forward/backward + [description of extended content].` |
| **Track completion (stitch up to 3 clips, ≤15 s total)** | `[Video 1] + [transition description] + connect to [Video 2] + [transition] + connect to [Video 3].` |
| **Style transfer** | `Transform source clip to [style], preserve core motion and timing, adjust color palette to [palette], keep identity consistent, avoid identity drift.` |

Track Completion is how to stitch separate generations together inside Seedance itself — useful when shot-to-shot drift is small enough not to need a hard re-render.

---

## Camera / lens / lighting vocabulary that reliably triggers

Use these terms verbatim. They're cinematography vocabulary the model is trained on.

### Camera movements (one primary instruction per shot)

`slow dolly in`, `dolly out`, `quick pan left`, `pan right`, `tracking shot (left to right)`, `tilt down`, `tilt up`, `pull back reveal`, `arc shot` / `orbit`, `Steadicam walk`, `crane up`, `jib up`, `handheld with slight organic shake`, `locked-off`, `whip pan`, `rack focus from background to subject`.

**Compound moves**: name the primary, then a secondary connector. `camera low tracking shot then subtle rise` works. `push-in then pan then orbit then zoom out` will confuse the model.

### Rhythm vocabulary (NOT technical specs)

Seedance understands rhythm words, not camera specs.

```
✅ slow, smooth, stable, gradual, gentle, controlled, dynamic, swift
❌ 24fps, f/2.8, ISO 800, focal length 85mm, shutter 1/50
```

The official guide phrases it: "describe the rhythm as if you're talking to an editor."

### Shot types

`extreme close-up (ECU)`, `close-up (CU)`, `medium shot (MS)`, `medium close-up`, `wide shot (WS)`, `establishing shot`, `over-the-shoulder (OTS)`, `two-shot`, `point-of-view (POV)`.

### Lens / focus

`shallow depth of field`, `deep focus`, `rack focus (foreground to background)`, `anamorphic lens flare`, `long lens compression`, `wide-angle distortion`, `macro lens`, `tilt-shift`.

**The FOV degree anchor — director registers only.** Quick mode stays qualitative, per the official guide's warning against camera specs (see *Rhythm vocabulary* above, which bans `focal length 85mm` alongside f-stops and ISO). That warning is about **specs in place of direction**. When a shot genuinely needs a *locked* field of view held across several cuts — the case the director registers exist for — the model latches onto **degrees** as a snap value where millimetres read as a suggestion. Write the degree first, mm in parentheses, and never an off-ladder value:

| FOV | mm | Feel | Use for |
|---|---|---|---|
| 180° | fisheye | spherical bulge | POV, dream state, hallucination |
| 107° | 14–16mm | architectural ultra-wide | vast interior scale, epic establishing |
| 84° | 20–24mm | classic wide | full-body blocking, immersive action |
| 63° | 28–35mm | reportage wide | observational, walking alongside, doc feel |
| 47° | 40–50mm | eye-level neutral | universal medium, two-shot, waist-up |
| 34° | 60–70mm | short tele | compressed group, stacked depth planes |
| 29° | 75–85mm | portrait compression | isolated bust, detail on hands |
| 18° | 100–135mm | portrait tight | identity-hold close-up, held emotional beat |
| 12° | 180–200mm | tele detail | hand insert, object close, texture |
| 8° | 300–400mm | extreme long lens | anchored-far observation |

**An unusual FOV needs a defence battery**, or it averages back toward a normal: *This is a LONG lens — strong telephoto compression, flattened perspective, background pulled in close and thrown soft, only one to three faces sharp at a time, tight crop. NOT wide-angle, no fisheye, no edge distortion, no deep focus, no full-room coverage.* Same in reverse for ultra-wide. Extreme FOV across several beats drifts fastest — declare it at the top of every beat, not just once. Full grammar: `references/director-v3.md`, slot 8.

### Lighting (the highest-leverage element in the prompt)

`motivated lighting from practical source`, `hard rim light`, `low-key lighting`, `high-key lighting`, `silhouette against background light`, `golden hour`, `practical tungsten`, `hard side-lighting`, `motivated neon`, `bounce fill`, `soft natural window light`, `dramatic backlighting`, `chiaroscuro`, `even overcast diffused light`, `warm candlelight flickering`.

If you can only add one element to a prompt to improve quality, **add a lighting description**. The difference between "a person walking" and "a person walking in soft golden hour lighting" is massive.

### Colour / texture / atmosphere

`color grade: teal and orange`, `color grade: bleach bypass`, `desaturated`, `high-contrast`, `cool blue tones`, `amber-tinted`, `35 mm film grain`, `16 mm film grain`, `fog`, `rain`, `dust particles`, `heat haze`, `halation around highlights`, `volumetric depth haze`.

### Tone

`tense`, `melancholic`, `urgent`, `serene`, `cinematic 4K`, `documentary-style`, `commercial photography aesthetic`.

---

## Community-proven tricks

- **Real-world style anchors** are among the most effective single phrases: `Apple keynote style`, `Wes Anderson symmetry`, `Guy Ritchie speed-ramping`, `Snyder impact slow-motion`. One anchor sets palette, pacing, and composition at once.
- **Comedy: let the model improvise.** Write `add a visual gag in the background` and Seedance invents one — funnier than scripting it.
- **Ultra-short prompts are a legitimate tool.** `"Fight of a 3D person with 2D"` and one-sentence POV prompts produce some of the best community results. When the concept is strong, try the one-liner before engineering anything.
- **Emotion as physiology.** The top-rated character prompts never say "sad" — they write the visible signal: pupils dilate, earlobes flush, breath shortens, a 0.3 s freeze. One or two signals, not a choreography sheet.

---

## Negative prompting — the `avoid X` pattern

Seedance reads "avoid X" instructions as guidance — but it responds better to affirmative direction than to negative stacks. **Cap negatives at 3 per prompt**, chosen for the actual risk of the shot. Ten avoid-clauses dilute each other and burn word budget; saying the camera is locked once beats saying it three ways (`locked-off` + `avoid camera drift` + `avoid jitter` = one instruction, state it once).

### The negative menu (pick ≤3 by risk)

- `avoid jitter` — fast motion or handheld shots
- `avoid bent limbs` — character action
- `avoid temporal flicker` — long clips
- `avoid identity drift` — character across cuts
- `avoid plastic skin` — realism close-ups
- `avoid chaotic composition` — busy scenes

### Realism-specific negatives

Prefer the positive form first (`real skin texture, visible pores`); add at most 2–3 of these only when a prior render actually showed the artifact:

> *glossy plastic skin · airbrushed look · oversaturated commercial color · smooth airless camera glide · beauty-filter sheen · generic AI aesthetic*

### Dangerous keywords that lower quality

These words *sound* good but degrade output. The official ByteDance guide flags them:

| Avoid | Why | Replace with |
|---|---|---|
| `fast` (unqualified) | Combines with fast cuts and busy scenes to produce jitter | One fast element only, e.g. `subject moves fast, camera holds steady` |
| `cinematic` alone | Too vague | `cinematic film tone, 35mm, warm` |
| `epic` | Model doesn't know what this means | Describe specific scale: `wide low-angle, towering, dust kicking up` |
| `amazing` / `beautiful` | No visual guidance | Specific lighting and composition |
| `lots of movement` | Causes jitter | `one specific motion`, named |
| `high quality` / `4K` (without context) | Empty signifier | Capture medium + lens + lighting |

### The "fast" rule

Fast camera + fast cuts + busy scene = guaranteed artifacts. If you need pace, **make only one element fast**. Either the subject moves fast, or the camera moves fast, or the cuts are fast — never two or three.

---

## Speed-ramping and inline VFX

### Speed-ramping syntax

Use CAPS inline to signal pacing changes mid-shot:

> *…the blade arcs through the air, **RAMPS TO SLOW MOTION** as the strand of hair catches the edge and separates, drifting upward in the slow-motion wind. **SNAPS BACK** to full speed as the second warrior completes her dodge and drives her elbow into the first warrior's chest.*

The CAPS are read as pacing directives, not as text overlays.

### Inline VFX brackets

When a power or effect needs to be specified without breaking the action description, drop it in brackets:

> *…energy surges through her fingers as fractal lightning veins explode across both forearms [VFX: branching electric circuits pulsing with white-blue current, sparks jumping between fingers], the ground trembles as enemies emerge…*

This works for: powers, energy effects, particle behavior, magic, sci-fi tech, body horror. Keep the bracket content compact — one descriptive clause.

---

## Common failure modes and how to fix them

**Over-specification (the #1 failure).** A 300–400 word prompt for a 4–8 s single shot — timestamp grids, SFX cues at [2.6s], seven realism layers, 10+ negatives. The model receives conflicting instructions and the acting goes rigid. Fix: drop to the tier budget; mood + one arc + one lighting line + one realism clause.

**Re-describing the reference image.** Narrating identity/wardrobe/scene that @Image1 already shows creates text-vs-pixels conflicts and drift. Fix: one role line per reference, then describe only motion and change.

**Mixing First/Last Frame with reference uploads.** Trying to attach a first frame *and* multiple reference images/videos in a single render — Seedance silently drops one set of inputs. Fix: pick one mode.

**Overloaded single beat.** Putting a sprint + a doorway + flashing lights + a close-up + over-the-shoulder into one timestamp confuses the model. Fix: split across two timestamps with one camera instruction each.

**Vague camera language.** *"The camera moves toward the subject"* gives the model nothing concrete. Fix: *"slow dolly in"*. Cinematography vocabulary is the model's strength — use it.

**Mixing camera movement and subject movement.** *"Spinning camera around a dancing person"* is uncontrollable. Fix: *"The dancer spins slowly. Camera holds locked-off framing on the medium shot."*

**Inconsistent subject references.** Calling the subject "a man," then "the detective," then "he" produces character drift. Fix: pick one noun phrase and reuse it.

**Conflicting instructions.** *"Peaceful meditation garden with loud rock concert and quiet library atmosphere"* renders as artefacts. Fix: one mood, one palette, one sound design per beat.

**Skipping the global style line.** Without a closing style sentence, Seedance defaults to its plastic AI aesthetic. Fix: always close with capture medium + realism stack.

**Skipping `no 3D, no cartoon, no VFX` on realism briefs.** This trio is the single highest-leverage realism instruction. Always include it when you want photoreal.

**Mismatched length to beat count.** Six distinct events in five seconds doesn't work. Fix: 5 s = 2–3 beats; 10 s = 3–4 beats; 15 s = 4–6 beats.

**Prompting a dance by name.** `she dances to the drop` renders generic swaying — models produce plausible human movement without the specific dance vocabulary, and this is empirically documented across four major video models. Fix: name the tempo, the pulse the weight sits on, the initiating joint and the floor contact. See `references/edm-dance-and-movement.md`.

**Wasting the audio capability.** *"A dancer on a stage"* (silent) misses what the model is built for. Fix: *"Ballet dancer executing pirouettes, pointe shoes tapping wooden stage, orchestral music swelling, audience gasps at difficult leap."*

**Letting Seedance invent supers when you don't want them.** Without a "no supers" instruction, the model adds its own kinetic typography. Fix: state explicitly *"No text overlays, no subtitles, no on-screen captions."*

**Not locking the seed across iterations.** If you change the prompt and re-roll, you can't tell whether the change came from the edit or random variation. Fix: capture the seed; submit the same seed with the modified prompt to isolate the change.

**Using "fast" without qualifying.** Causes total chaos. Fix: make one element fast — subject OR camera OR cuts, never combinations.

**Borrowing cinematic language inside a phone-look prompt.** The 35 mm grain instructions fight the iPhone color science instructions and you get a muddy hybrid. Fix: pick one mode and commit.

---

## Worked examples

### Example 0 — Tier-1 i2v with dialogue (4 s, vertical) — the default register

> *Vertical 9:16, 4 seconds, one continuous locked-off shot from a phone propped on the dashboard facing the driver. @Image1 = her identity, wardrobe, and the foil-wrapped burrito — ignore its camera angle. A young woman cries quietly in the driver seat, mascara streaked, sun blowing out the windshield behind her. She looks into the lens and says, voice cracking on the edge of a sob: "Why am I like this?" — then takes one joyless stress-eating bite and keeps chewing through tears. Native iPhone look, real skin texture. Cabin room tone, no music. Avoid cuts, identity drift, plastic skin.*

~95 words. No timestamps, no SFX timeline, no re-description of the reference. This register should be the starting point for every short clip; only escalate when the brief genuinely needs more shots.

### Example 1 — phone-realistic UGC hook (5 s, vertical, Tier-2 ceiling)

> *Vertical 9:16, 5 seconds, iPhone 15 Pro handheld footage. A young woman in a worn grey hoodie sits on the floor of her bedroom against an unmade bed, laptop open beside her, late afternoon. She glances up at the phone camera, half-laughs, then looks back at the screen. Natural window light from camera-left, mixed with a warm bedside lamp on the right — no color correction, slight green cast in shadows. Auto-exposure briefly hunts when she moves. Skin is real — visible pores, slight flush on cheeks, flyaway hairs catching the window light, no makeup polish. The hoodie fabric weave is visible, with natural creases. Dust motes drift through the window light behind her. Camera shake is subtle and tied to the operator's breathing. Sound design: laptop fan hum, distant traffic through window, a small genuine laugh. Native iPhone color science, no LUT, no grade, no film emulation. No text overlays. Avoid jitter, avoid plastic skin, avoid beauty filter, no 3D, no cartoon, no VFX.*

### Example 2 — 35 mm cinematic realism (8 s, horizontal)

> *Locked-off wide on a working-class kitchen at 6am, 16:9. A man in his fifties stands at the stove pouring coffee, back half-turned to camera. The kitchen is lived-in — dishes in the sink, calendar on the fridge, scuffed linoleum. Single hard window light from screen-right, motivated daylight, deep shadow on the room interior side, no fill. Steam from the coffee curls visibly into the light shaft, dust suspended in the air. His hands are weathered — visible knuckle lines, slight tremor, real skin not retouched. Plaid flannel shirt with visible weave and natural creases at the elbows. Camera holds for 4 seconds, then slow handheld push-in begins — operator's footsteps tied to subtle vertical bob — closing to medium shot as he raises the cup to drink. Sound design: percolator gurgle, refrigerator hum, distant garbage truck outside, a single sip. Kodak Portra 400 on 35mm, halation on the window highlight, organic film grain, slight gate weave, color grade warm-amber with cool blue shadows. No supers, no subtitles. Avoid jitter, avoid plastic skin, no 3D, no cartoon, no VFX.*

### Example 3 — multi-shot transformation (15 s, horizontal)

> *Montage, multi-shot action Hollywood movie, don't use one camera angle or single cut, cinematic lighting, photorealistic, 35mm film quality, professional color grading, sharp focus, high detail texture, film grain, depth of field mastery, ARRI ALEXA aesthetic.*
>
> *A pink-haired girl with glasses, cream top and jeans sits on the hood of a white pickup truck under a concrete overpass at dusk, casually eating a burger. A shallow river channel stretches behind her, power lines and distant bridges framing the golden sky. A pale zombie with wet dark hair, bruised eyes and a blood-stained white shirt sprints toward her from the shadows. The girl calmly sets down the burger, her body erupts into a massive pale tusked creature, devours the zombie whole, then shrinks back to human form and picks up the burger. Handheld shake throughout, dark comedy pacing with horror undertones.*
>
> *Shot 1: Medium shot of the girl sitting cross-legged on the truck hood, chewing the burger lazily, golden dusk light catching her glasses and pink hair. Camera sways gently.*
>
> *Shot 2: Wide shot of the concrete channel as the zombie bursts from the shadows under the bridge, sprinting with jerky unnatural strides. Camera shakes tracking the approaching threat.*
>
> *Shot 3: Close-up on the girl's face as she notices the zombie, chewing slows, eyebrows rise with mild annoyance. She sets the burger down beside her.*
>
> *Shot 4: Medium shot as the girl drops off the hood and her body violently expands and twists upward into the massive pale tusked creature, spine cracking, limbs stretching, jaws splitting open wide. Camera jolts with each bone-snap.*
>
> *Shot 5: Wide low-angle as the creature lunges forward and catches the charging zombie in its enormous clawed hand, swallows it whole in one grotesque bite. Camera shudders with the impact.*
>
> *Shot 6: Medium shot as the creature rapidly shrinks back into the girl, standing calmly beside the truck. She hops back onto the hood, picks up the burger, takes another bite.*
>
> *Avoid jitter, avoid bent limbs, avoid identity drift, no 3D, no cartoon, no VFX. Total: 15s / 6 shots / 16:9.*

### Example 4 — single-shot POV (15 s, locked perspective)

> *One continuous shot, POV gladiator perspective in the Colosseum arena, no cuts, no zoom, natural head movement, 15 seconds. A furious enemy warrior sprints straight toward the camera through thick dust and sunlight, heavy footsteps shaking the ground. As he reaches close the POV character reacts — grabs him mid-charge and slams him violently onto the sand, dust explosion, no pause. Immediate chaos erupts all around: multiple gladiators fighting simultaneously, swords clashing, shields smashing, archers releasing arrows overhead, a chariot bursts through the scene. POV character fights barehanded — blocking strikes, grabbing opponents, throwing them aside, fast reactions, heavy hits. Camera shakes from impacts, breath sounds, dust in the air, dramatic sunlight beams cutting through shadows. Cinematic lighting, photorealistic, grounded realism, strong 35mm film look, heavy film grain, sharp but imperfect focus, motion blur on hits, halation on highlights, slightly desaturated tones, ARRI ALEXA aesthetic, natural imperfections, subtle chromatic aberration near frame edges. SFX: footsteps, sword clash, shield impact, body slam, dust whoosh, distant horns, crowd roar. Avoid jitter, avoid bent limbs, no 3D, no cartoon, no VFX. Total: 15s / 1 shot / 16:9.*

### Example 5 — product shot (6 s, image-to-video)

> *Reference the bottle from Image 1, place it on a polished marble surface. Backlit, product in sharp focus, background completely blurred. Slow pull back: the framing widens to reveal the full bottle and a single green branch beside it. Arc shot begins (right to left): the camera slowly orbits the product at waist height, light catching the glass at different angles. Camera settles into a medium shot, static, product centred. Commercial photography aesthetic, 4K, clean studio lighting, premium softbox from screen-left, color grade slightly warm whites, deep clean shadows. Keep product shape and label stable, no new text, no background change. Avoid identity drift, avoid jitter. Total: 6s / 4:3.*

### Example 6 — image-to-video animation (5 s)

> *Animate this image with a subtle slow zoom in, natural blinking, hair moving gently in a light breeze, soft cinematic lighting, realistic motion. Preserve composition and colors, no identity change, no extra objects, no text distortion. Camera holds — operator's breathing only. Avoid jitter, avoid temporal flicker, avoid identity drift. Total: 5s.*

---

## Iteration methodology

The official guide recommends a **four-step loop**:

1. **Baseline generation.** Generate 2–3 options using a standard prompt at 480p.
2. **Single-variable adjustment.** Change ONE element per iteration — camera angle, motion intensity, lighting, or style. Never multiple at once.
3. **Score.** Rate on continuity, instruction adherence, and post-production usability.
4. **Final selection.** Pick the highest-scoring version, capture the seed, finalize at 720p or 2K.

**Three-tier template management:**

| Tier | Purpose | Characteristics |
|---|---|---|
| **Starter** | Quick direction validation | Short, precise, 60 words |
| **Production** | Official delivery | Strict camera + consistency constraints, 80–100 words |
| **Fallback** | Downgrade for unstable output | Highly simplified, back to basics, 40 words |

---

## Quick checklist before pressing Generate

1. **Tier picked first?** Single shot 4–8 s → Tier 1, 60–120 words, one paragraph, no timestamps. Tier 3+ (nothing may drift) → the sixteen-slot spine in `references/director-v3.md`.
2. **Mode chosen?** First/Last Frame *or* Universal Reference — not both.
3. **Subject + Action present?** (required)
4. **Camera and subject motion described separately?** One primary camera move, stated once.
5. **One primary action per beat?** Multi-shot uses explicit cut keywords or `[Ns]` markers?
6. **References = role lines only?** No re-description of what the image already shows. (Universal Reference Mode only)
7. **Aspect ratio specified?** (9:16 / 16:9 / 21:9 / 4:3 / 1:1 / 3:4) — *quick mode and director mode only; director v3 keeps the ratio in the UI.*
8. **Duration matches beat count?** (5 s → 2–3 beats, 10 s → 3–4, 15 s → 4–6)
9. **Closing style line present?** One line on Tier 1 (capture medium + realism clause); full stack only on Tier 3.
10. **`no 3D, no cartoon, no VFX` if realism-priority?**
11. **≤3 negatives, picked by actual risk?** — *quick mode; director v3's slot-owned negations are uncapped.*
12. **Explicit "no supers" or "no soft transitions" if relevant?**
13. **Seed captured for iteration?** Change one variable per retry.
14. **480p for testing, 720p/2K for output?**
15. **One register only?** Quick mode, director mode, or director v3 — with that register's whole rule set on brands, aspect ratio and age language. Never two grammars in one prompt.
16. **Every visible vapour has an emitter in frame** — or the shape negations are present, or the air is declared clean?
17. **One camera register held throughout**, with the never-settles clause if it isn't locked-off?
18. **`NO BGM` written as a production term** (not "no music") if the scene must land without score?

---

## Check the surface first — 2.0 or 2.5

This skill is Seedance **2.0**: 4–15 s clips, 9 images + 3 videos + 3 audio, up to 2K. If the surface in front of the user runs **Seedance 2.5** — Jimeng AI, Doubao Pro, and now listed on imagine.art — the specs change enough to change the architecture of the prompt: 30 s native in a single clip, multi-round extension to roughly 90 s, 30 images + 10 videos + 10 audio, an audio-only reference modality, `@Clay Render` structure passes, and a **mandatory usage sentence after every `@asset`**. Route those jobs to `seedance-25-director`, which owns that grammar. Don't carry 2.0's caps onto 2.5 — a 2.0-shaped prompt leaves most of 2.5's identity budget unspent — and don't promise 2.5's runtime on a 2.0 surface.

## When NOT to use Seedance — switch to another skill

- **Still image, poster, mockup, photo edit** → use `nano-banana-prompter`. Seedance only makes video.
- **You need to animate a specific existing still with very tight camera control** → consider `kling-prompter` (image-to-video is Kling's strongest mode).
- **You need an identity-locked character across many separate video shots** → consider `kling-prompter` with its Elements feature.
- **You need to pull live web data into a visual** → use `nano-banana-prompter` (Nano Banana 2 / Pro). Seedance has no web access.
- **You want brand-mandated pixel-perfect typography in the frame** → render text in `nano-banana-prompter` or in a post editor; Seedance's native supers are good for stylised text only.

For chained workflows (e.g., generate a hero still in Nano Banana, then animate in Seedance), see `gen-media-router` for the recipes.

## Further reading

- **`references/director-mode.md`** — the full Cinema Worldbuilder director-mode grammar for Tier-3 production work: M1–M5 mode-select table with per-mode Camera Capture templates, the ten-block output format, pre-prompt confirmation workflow, Frame Map / Subject Lock / Cross-Frame Rules / Last Frame specs, Capture Realism block (three-register atmosphere, moisture-without-shine, per-zone specular kill, contrast stated three ways), Sound Bed rules, V2V grammar, and the behavior-not-brand camera substitution table. Read it whenever the deliverable is a reference-anchored production render.
- **`references/edm-dance-and-movement.md`** — the movement layer for any brief with dancing in it: BPM per subgenre and which pulse the weight sits on, the four rhythmic families, track-architecture-to-body junction by junction (breakdown, build, gap, drop), the style catalogue written as mechanics rather than names, femme movement vocabulary with joint sequences spelled out, what heels change through the whole chain, hair as a trailing mass, the authenticity stack, the documented fake-movement tells, crowd-density thresholds and setting constraints. Read it whenever the deliverable contains dancing — a style name in a prompt renders generic swaying, and this file is the reason why.
- **`references/director-v3.md`** — the top register: the locked sixteen-slot production spine. Read it when the deliverable must not drift. Contains the full slot-by-slot grammar (Header speed policy · Style Prefix with the render quad and cadence clause · the No On-Screen Text block and why it never carries an exception clause · CRITICAL-block promotion capped at four · Assets as identity + THIS SCENE + fidelity assertion · the Geometry Map · First Frame killing the empty establishing hold · the FOV degree ladder with defence batteries · the four camera registers · the 70/20/10 colour doctrine · the atmosphere source rule · timecoded Action Timing with EVERYONE IS LIVE · the seven-link physics chain · Acting with brow matched to the line · Audio under NO BGM · Locks as a positive ordered chain), plus the lipsync closure protocol, strobe grammar with the cadence quarantine, the reference-plate intake spec, the story-bible handoff map, a pre-delivery pass and a symptom → fix repair table.

## Sources

Doctrine grounded in: the official ByteDance/Volcengine Seedance 2.0 prompt guide (6-step formula, 60–100 words, one camera move, lighting as highest-leverage element, one-variable iteration), the Higgsfield Seedance 2.0 prompting guide and community library (format recipes, locked-perspective trick, `no 3D, no cartoon, no VFX`, style anchors, visual-gag improvisation), the awesome-seedance-2-prompts corpus (reference role-assignment grammar, consistency tails, failure-mode defenses), cinema-worldbuilder-pro-2.2 (director-mode grammar, merged in full), and cinema-director-v3 (the sixteen-slot production spine, FOV degree anchor, camera registers, colour doctrine, atmosphere source rule, physics chain, lipsync closure protocol, strobe grammar and the NO BGM convention, merged in full as `references/director-v3.md`). The reference-plate intake spec is adapted from the character-builder plate doctrine; the story-bible slot map from the story-bible-builder handoff spec.


<!-- ═══════ FILE: seedance-2-prompter/references/director-mode.md ═══════ -->

> **Director mode** — Tier-3 production grammar merged from cinema-worldbuilder-pro-2.2. Load this file only for production deliverables: locked composition, reference-anchored characters, ten-block output. For everything else use the quick-mode formula in SKILL.md. Where this file and SKILL.md disagree on length, this file governs director-mode prompts only (280–400 words single-shot, never over 600 multi-shot).


# Cinema Worldbuilder Pro 2.2 — Seedance Director

The locked cinematography grammar for Seedance 2.0 video prompts. Mode-aware, reference-aware, composition-aware, audio-aware. Reads what the user gives you, picks the right cinema mode, extracts wardrobe and identity from reference images by visual description, maps the frame, locks every character to a screen position and state, choreographs the motion, fixes the closing composition, and outputs a production-ready Seedance prompt with diegetic audio only.

Pro 2.1 keeps the 2.0 backbone intact (five-mode grammar, ten-block locked order, density discipline) and adds the operational layer the model itself rewards: model-variant routing, aspect-ratio specification, iteration-resolution workflow, seed capture, dialogue-in-quotes lip-sync, and the full V2V edit grammar.

Pro 2.1 is built around density discipline: shorter prompts render better than longer ones. Every block does work. Nothing is decorative. The Camera Capture spec is one trimmed line at the bottom — never doubled. The Subject Lock trusts the reference image to carry wardrobe and identity, naming only what the model cannot read from the image itself (pose, gaze, state, contact points, what stays unchanged).

---

## CORE PHILOSOPHY

No plastic. No commercial gloss. No LED-panel-rendered-on-a-soundstage energy. No Instagram-ad sharpness. No brand-name gear stacks.

Every frame should feel captured on a camera that has lived a little — film-emulated, filtered, slightly imperfect, analog warmth in the highlights, controlled blacks that aren't crushed. The grade is editorial, not commercial. The glass has character. The shadows hold detail. Real fabric, real skin, real sweat, real haze, real grain.

Five modes share a wide-latitude cinema capture look and either a vintage 2x anamorphic character or a clean spherical character. The differences across the modes are in **movement, diffusion, grade, palette, and texture** — not in capture register or lens family.

A great prompt is not a beautiful sentence. It is a production document. Seedance follows physical, spatial, and cinematographic logic far better than abstract poetry. Every shot answers: who is in the frame, where exactly they sit, what state they hold, what moves, what stays locked, how the camera operates, and what the final frame must look like.

**Density rule.** Target prompt length is 280–400 words for single-shot scenes. Multi-shot sequences may run longer but never over 600. Every word should do work. When in doubt, trust the reference image to carry visual information and cut the redundant description.

---

## THE THREE HEADLINE UPGRADES (2.2)

These are the three places the skill moved the needle hardest. Every prompt this skill writes obeys all three by default.

### 1. Volumetric atmosphere in every frame — the three-depth-register pattern

The thing that makes AI footage read as AI is flat air. Real cinematography has atmosphere — light cutting through haze, fog catching practicals, particulate in the foreground softening edges in the deep background. This skill bakes volumetric language into every prompt by default. The user does not have to remember to write it; the skill writes it.

**The pattern:** in the World Plate and Capture Realism blocks, name atmosphere across three depth registers:

- **Foreground volumetric haze** — between camera and subject, giving the closest air real physical body
- **Midground volumetric haze** — wrapping the subject and the ground, the layer where any light cones (headlights, practicals, sunlight through windows, stage lights) cut through it most densely
- **Deep-background volumetric haze and fog** — dissolving the deepest background structures into atmospheric perspective so the most distant elements are softer, desaturated, and lower-contrast than everything in front

Words to use verbatim: `haze density`, `particulate in the air`, `light shafts cutting through suspended haze`, `atmospheric falloff between subject and background`, `foreground volumetric haze`, `midground volumetric haze wrapping the subject`, `deep-background atmospheric perspective`, `suspended mist`, `air with real physical body`.

Scale density to the scene: `thin atmosphere` for a clean controlled interior, `light haze` for most exteriors, `heavy suspended mist` for pre-dawn / rain / smoke-heavy / post-apocalyptic plates. The denser the air, the stronger the depth separation. Never skip this — even a clean studio gets `thin atmosphere`. Flat air is the headline AI tell.

### 2. Mid-grey seamless for character builds — never pure white

When the user is using this skill to write a M2 Studio prompt for a **character build, reference sheet, lookbook plate, or any portrait whose primary job is to lock a character's identity for downstream shots**, the default backdrop is **mid-grey seamless** — not pure white.

White seamless gives the model nothing to anchor skin against, blows the contrast curve, and produces the plastic over-lit AI-portrait look. Mid-grey seamless gives the model a value to read skin tones against, lets shadows do real work, and the character renders with dimensionality instead of looking like a render.

**Default language for character-build World Plate:**
> *Mid-gray seamless studio backdrop, even neutral mid-gray, no seam line, no gradient. Subject relit from scratch overriding any reference lighting — one broad diffused source from camera-left and slightly above, gentle wrap, no harsh shadows, no rim light, no hair light, no kicker. Skin and fabric read matte and velvety in a low-contrast milky look, rendering at their true natural tone against the neutral gray.*

Use white seamless ONLY when the user explicitly requests it (hard-key fashion editorial, high-key product, intentional blown-out aesthetic). Otherwise default to mid-grey.

This is primarily an M2 Studio principle but also applies inside M1 if the scene is a character-build interior / reference plate.

### 3. Cameras described by behavior — never brand names

The old prompt pattern ended Camera Capture with brand stacks: *"ARRI Alexa 35, Panavision Ultra Vintage 75mm anamorphic at T2.3, Kodak Vision3 250D pushed 800 ASA."* It worked, but the model isn't rendering an Alexa — it's pattern-matching on the vibe of that gear stack. This skill cuts brand names entirely and writes the **behavior** instead.

**The substitution:**

| Stop writing this (brand) | Write this (behavior) |
|---|---|
| ARRI Alexa 35 | wide-latitude cinema capture |
| Panavision Ultra Vintage 75mm anamorphic at T2.3 | vintage 75mm 2x anamorphic character at a wide aperture, oval bokeh, soft edge falloff |
| Cooke S4 or Master Prime | clean spherical character, even sharpness, natural round bokeh |
| Kodak Vision3 250D / 500T | color-negative daylight / tungsten film rendition |
| Pushed 800 ASA, heavier grain | heavier low-light grain |
| Tiffen Black Pro-Mist 1/4 | light diffusion bloom softening highlights |
| ARRI SkyPanel S60 / SkyPanel from camera-right | soft diffused source from camera-right, cool ambient quality |
| Astera Titan / practical tungsten | warm tungsten practical from a visible bulb in frame |
| Gimbal-stabilized Steadicam tracking shot | smooth tracking shot with operator drift |
| Easyrig handheld | handheld with natural operator breath |
| Tilta Nucleus rack focus | rack focus from foreground to background |

Same logic on lighting — direction, quality, temperature in plain physical terms. No fixtures, no model numbers, no jargon the model has to translate. The Mode-Select table and the per-mode Camera Capture templates below already obey this rule — never re-introduce brand names when tuning a prompt.

**Universal Rule 11 ("No real brand names in prompt output") covers this; this upgrade names the specific anti-pattern that produced the worst failures.**

---

## SEEDANCE 2.0 MODEL & RENDER SPECS (READ ONCE, OBEY ALWAYS)

Before composing, the operational specs of the target model:

- **Variants:** Seedance 2.0 ships in **Fast**, **Standard**, and **Pro**. Pro for hero deliverables, Standard for working renders, Fast for blockouts.
- **Clip duration:** 4–15 seconds (official current spec). Plan beat count to the duration: 4–8s = one beat, 8–12s = two beats with one hard cut at most, 15s = up to 4–6 beats or 6 numbered shots.
- **Aspect ratios:** 21:9, 16:9, 4:3, 1:1, 3:4, 9:16. Always specify the aspect in the Camera Capture closer.
- **Iterate at 480p, finalize at 720p.** Burn drafts at 480p to lock framing, motion, and identity, then re-render the locked seed at 720p for the deliverable.
- **Capture the response seed.** Every great render gets its seed logged. Reusing the seed on a modified prompt isolates the effect of the prompt edit from random variation — without it, you can't tell whether a change improved the shot or just rolled different dice.

These specs go in the Camera Capture line at the bottom of every prompt. The runtime, the aspect ratio, and (when re-rolling) the seed all live there.

---

## HOW TO USE THIS SKILL

The workflow is the same every time:

**Step 1 — Upload reference material to Claude.** Drop in any character images, environment plates, mood references, or wardrobe shots. If the scene is purely environmental or you're inventing characters from scratch, no images needed.

**Step 2 — Describe the scene.** Tell Claude what the moment is: who is in the frame, what they're doing, where it's set, what's happening, how long the shot should run, and the aspect ratio. The skill picks the right cinema mode automatically (or the user can name it explicitly).

**Step 3 — Confirm the pre-prompt summary.** Claude returns a bulleted pre-prompt check listing every reference image attached (first bullet), the cinema mode, scene, characters, frame map, camera, runtime, and aspect ratio — for a quick check before writing the full prompt.

**Step 4 — Receive the three-part delivery.** Claude returns (a) a numbered bulleted list of reference images to attach in Higgsfield/Seedance in order (max 9 — Seedance hard cap), (b) a bolded English title line stating the runtime and aspect, and (c) a single fenced English code block containing the full prompt with discrete labeled blocks **always in this exact order, every prompt, no exceptions** — Scene & Mood → Frame Map → Subject Lock(s) → Cross-Frame Rules → Movement → Last Frame → World Plate → Sound Bed → Capture Realism → Camera Capture — and inline `@image1` through `@image9` tags placed wherever each reference image anchors. Numbers match the order of the bullet list at the top.

**Step 5 — Run it in Higgsfield.** Attach the reference images from the bullet list into the Seedance UI in the exact order listed (image 1 first, image 2 second, etc.), then paste the English code block into the prompt field. The `@image1`, `@image2` tags inside the prompt are functional Seedance syntax — Seedance reads them and applies the corresponding uploaded reference at each anchor point.

**Step 6 — Iterate then finalize.** Generate at 480p, log the seed, refine the prompt, re-render at the same seed to isolate changes. Move to 720p only once the framing, motion, and identity are locked.

---

## SESSION OPENER — CHARACTER GATE

The first time the user asks for a Seedance prompt in a session, ask once:

> "Any recurring characters in this batch? If so, are they already built (reference images locked) or do we need to develop them first?"

Branch on the answer:

- **Yes / built →** ask for the reference image upload(s). Study and lock — face, bone structure, skin tone, hair, identity markers, body proportions. Mirror back the locked spec in plain language for confirmation. Carry the lock through the rest of the session.
- **Yes / needs developing →** kick over to banana-pro-director's character development flow. Lock the character first, then return to the Seedance prompt request.
- **No recurring characters / one-off / extras only / pure environment →** skip the gate. Proceed normally.

Once asked, do not ask again in the same session.

---

## PRE-PROMPT CONFIRMATION RULE

Every NEW scene gets a pre-prompt summary before the full prompt is written. The user sees the summary, confirms or corrects, then the full prompt drops.

**Format: a bulleted list — references first, then scene details, then runtime + aspect as the closer.**

```
Pre-prompt check:
- **References attached:** [list every reference image the user uploaded for this scene by short visual descriptor. If none attached, write "none — pure text composition."]
- **Mode:** [M1 Narrative / M2 Studio / M3 Action / M4 Performance / M5 Atmospheric]
- **Scene:** [one-line scene description]
- **Characters:** [who's in frame, abbreviated by visual marker; or "none / environment plate"]
- **Frame Map:** [one-line compositional read — where each character sits, depth layer, eyeline]
- **Camera:** [lens length, key movement — e.g., "55mm anamorphic, handheld with operator breath"]
- **Runtime + Aspect:** [Xs, 16:9 / 9:16 / 21:9 / etc., single shot OR Xs, [N]-shot sequence with per-shot beats]

Sound good?
```

Wait for the green light. Then deliver the three-part output.

**Why references first:** the user's uploaded references are what the prompt is being composed against. Listing them first confirms back to the user that every reference is being used. If a reference was uploaded but is missing from the list, the prompt is being composed wrong, and the user catches it here before the full prompt ships.

**Why runtime + aspect as the closer:** runtime and aspect are the two most important hard specs to lock before the prompt ships. Surfacing them last keeps the user's eye on them right above "Sound good?"

**When to skip the confirmation:**

- The user is iterating on a prompt just delivered (camera tweak, time of day swap, lens push, wardrobe swap, lighting nudge, push-in addition, position shift, eyeline change)
- The user requested a prompt batch and pre-confirmed the batch as a whole
- The user explicitly said "skip the confirm, just give me the prompt"

For all new scenes: confirmation is not optional.

**Runtime + aspect asking:** if the user hasn't specified either, ask in the pre-prompt confirmation step. Never assume a default.

---

## THREE-PART DELIVERY FORMAT (LOCKED)

Every Seedance prompt is delivered in three parts, in this order:

**1. Numbered bulleted list of references to attach in Higgsfield.** Each reference gets a number and a short visual descriptor. Seedance accepts up to 9 references max — no more.

**2. Title line with runtime and aspect.** Bolded English. Example: `**Seedance prompt — 12s, 9:16**`

**3. English code block with discrete labeled blocks and `@image1` through `@image9` tags inline.** Drop the tag wherever that reference is being referred to in the prompt. The number matches the reference list — bullet 1 = `@image1`, bullet 5 = `@image5`, bullet 9 = `@image9`. Hard cap at 9.

**Block order inside the code block (every prompt):**

```
Scene & Mood: [one or two sentences setting the dramatic moment — what the moment IS, dramatically]

Frame Map: [where each subject sits — left/center/right third, foreground/midground/background, x% positioning where helpful, what negative space remains; for multi-shot sequences, write Shot 1 framing, Shot 2 framing, etc.]

Subject Lock — @imageN: [per character, one discrete block — identity anchor + body orientation + pose + state + gaze + contact points + lock-down line. Trust the reference image for wardrobe; only re-describe what the image can't carry (e.g., damp hair, dirt on the cheek, blood on the sleeve, time-of-day state change)]

Cross-Frame Rules: [for multi-character shots — never swap positions, never cross center, never change depth, distance and screen sides held. For multi-shot sequences, name what carries across the cut.]

Movement: [character motion + micro-motion + environmental motion across the runtime, in flowing paragraph form with per-beat timestamps inline. For multi-shot, name Shot 1 motion, hard cut to Shot 2 motion, etc. Dialogue, if any, in "double quotes" to trigger lip-sync.]

Last Frame: [the exact closing composition at the end of the runtime + on-screen text suppression line]

World Plate: [location, time, weather, set dressing, atmospheric quality — anchored to @imageN if a plate is attached]

Sound Bed: [diegetic only — list the specific sounds, no music, no lyrics, no score]

Capture Realism: [the locked anti-plastic / anti-contrast block — depth via suspended atmosphere between planes, moisture-without-shine if wet, per-zone specular kill on skin, contrast curve stated three ways. See the CAPTURE REALISM BLOCK section. Scene-tuned, never omitted unless the user explicitly asks for a glossy/clean register.]

Camera Capture: [single trimmed paragraph with body, lens, filter, movement, stock, grade, frame rate, runtime, aspect ratio, and optional seed. Multi-shot sequences may name Shot 1 / Shot 2 lens differences inline.]
```

---

## OUTPUT LANGUAGE (LOCKED)

**English only — locked.** All Seedance prompts are output in English inside the code block. Camera/lens/grade aesthetic descriptors stay in their plain-language English form (wide-latitude cinema capture, vintage 2x anamorphic character, soft diffusion bloom, color-negative film rendition, fine 35mm grain) — never brand names or model numbers the tool doesn't recognize. Numeric values that describe a real optical property stay as numerals (focal length in mm, 24fps, 180° shutter). M1/M2/M3/M4/M5 mode labels stay in English. The `@image1` / `@image2` / `@imageN` reference tags stay in English inside the body.

No Chinese mode. No bilingual mode. English only.

---

## UNIVERSAL PROMPT RULES (ALL MODES)

These apply to every Seedance prompt this skill produces, no exceptions:

1. **Pre-prompt confirmation on every new scene.** Bulleted list (References / Mode / Scene / Characters / Frame Map / Camera / Runtime + Aspect), references FIRST, runtime + aspect LAST. Skip only on iterations of a prompt just delivered.
2. **Three-part delivery format, in order:** (a) numbered bulleted reference list, (b) bolded English title line with runtime + aspect, (c) English code block with discrete labeled blocks and inline `@imageN` tags.
3. **`@imageN` numbering matches the bullet list order exactly.** Bullet 1 → `@image1`, bullet 2 → `@image2`, etc.
4. **Every reference in the bullet list appears at least once as an `@imageN` tag** inside the code block.
5. **Runtime + aspect baked into the closing Camera Capture line.** Always ask both; never default. The values in the title line above the code block must match the values in the Camera Capture line inside it.
6. **Per-shot timing inline in Movement** for any multi-cut sequence ("Shot 1 (0–6s): ... Hard cut to Shot 2 (6–10s): ...").
7. **Discrete labeled blocks inside the code block, in this exact order, every prompt, no exceptions — HARD LOCK:** Scene & Mood → Frame Map → Subject Lock(s) → Cross-Frame Rules → Movement → Last Frame → World Plate → Sound Bed → Capture Realism → Camera Capture. This order never changes. No block may be omitted, reordered, merged, renamed, or replaced with flowing prose. Every block ships with its label prefix (e.g. `Scene & Mood:`, `Frame Map:`, etc.). Single-shot, multi-shot, narrative, studio, action, performance, atmospheric — all ten blocks, all in this order, every time. The only conditional content is *inside* a block (the `[IF WET: ...]` clause in Capture Realism drops on dry scenes; the human-skin sentence in Capture Realism drops on M5 no-humans plates) — the block itself still ships with its label. If a block has nothing to say for the scene, the block is still present and its content is shortened, never omitted.
8. **One Subject Lock block per character.** When multiple characters share the frame, each gets its own discrete Subject Lock block — never jammed into one paragraph.
9. **One Camera Capture line at the bottom — never doubled.** The Camera Capture is the only camera/grade/film stock language anywhere in the prompt. No discrete `Camera:` block in the middle of the body.
10. **No character names in prompt output.** Describe by hair color, wardrobe, identity markers. The `@imageN` tag handles reference anchoring.
11. **No real brand names in prompt output.** Generic visual descriptors only ("white low-slung mid-engine sports car," not specific brand names). This includes camera and lighting gear — never write `ARRI Alexa`, `Panavision`, `Cooke`, `Kodak Vision3`, `Tiffen Black Pro-Mist`, `ARRI SkyPanel`, `Astera Titan`, `Easyrig`, `Tilta Nucleus`, or any other brand-name fixture or stock. Describe the **behavior** (`wide-latitude cinema capture`, `vintage 2x anamorphic character`, `light diffusion bloom`, `soft diffused source from camera-right`, `warm tungsten practical`) instead. See THE THREE HEADLINE UPGRADES section for the full substitution table.
12. **No platform/tool names in prompt output.** Never reference "Higgsfield," "Seedance," "Banana Pro," "Soul Cinema," etc. inside the prompt text.
13. **No internal production context.** No "carried through the world," no "matching the previous scene," no "as established earlier." Every prompt is standalone.
14. **Pure visual description only.** No meta-commentary. Every word describes a visible thing in the frame.
15. **Diegetic audio only** — no music, no lyrics, no song references in the Sound Bed. Dialogue physically spoken in the scene goes in `"double quotes"` inside Movement (or Sound Bed) to trigger Seedance's millisecond lip-sync.
16. **Energy over position** in the Scene & Mood block. Describe what bodies and forces are doing dramatically. Frame Map handles the geometric specifics.
17. **Cut triggers.** Use "Hard cut to," "Smash cut to," "Match cut on" to signal edits inside multi-shot prompts. Auto-edit on by default. If you want a soft transition, name it explicitly (`crossfades to`, `dissolves through`, `whip-pans into`); otherwise the model defaults to hard cuts when this skill is driving.
18. **Age-blind.** Never describe characters by age. Describe by role, hair, wardrobe, and identity markers.
19. **No on-screen text by default.** Never write captions, subtitles, slogans, signage typography, speech bubbles, UI overlays, or rendered text into a Seedance prompt unless the user has explicitly asked for on-screen text. To suppress Seedance's tendency to hallucinate text, every prompt's Last Frame block closes with: "No on-screen text, no captions, no signage typography, no rendered text in the frame." Skip the suppression only when the user has explicitly requested in-frame text (see TEXT-IN-VIDEO OVERRIDE section).
20. **Positive locks over negative prohibitions.** Translate "no drifting" into "boots stay planted on the same ground marks." Translate "don't change face" into "@image1 keeps the same face, hair, wardrobe, and silhouette throughout." Negative prompts have weaker pull than positive constraints.
21. **One main idea per shot.** One dominant action, one main camera strategy, one major lighting motivation. If a request requires more, split into a multi-shot sequence.
22. **Trust the reference image for wardrobe.** The Subject Lock block names identity anchor, body orientation, pose, state, gaze, contact points, and the lock-down line. Do not re-describe wardrobe details that are already visible in the reference. Only specify the wardrobe details that the model cannot read from the image (e.g., "damp from rain," "torn at the shoulder," "covered in dust") — text-only state information the reference image can't convey.
23. **Canonical reference always attached, never substituted by the plate.** Every named subject that appears in the scene gets its canonical reference (character reference sheet, vehicle reference, prop reference, creature reference) attached as its own `@imageN` slot — even when that subject is also visible inside the rendered environment plate. The plate carries the world (location, weather, light, set dressing, composition); the canonical reference carries identity (face, body, livery, markings, silhouette). Never let the plate stand in for a canonical reference. Subject Locks anchor to canonical reference tags (`@image1`, `@image2`, etc.); the World Plate block anchors to the plate tag (`@imageN`). Hard rule, no exceptions: if a character or vehicle appears in the plate AND has a canonical reference, the canonical reference still gets its own slot in the reference list and its own Subject Lock block in the prompt. This applies regardless of how clearly the subject reads in the plate. Identity fidelity is always anchored to the canonical reference, never to the rendered plate.

---

## READING REFERENCE IMAGES

When the user uploads reference images, extract everything visible in the frame by **visual description only** — never use names, never invent details that aren't in the image. The extracted reading is for Claude's own understanding and the pre-prompt check. The actual prompt body trusts the reference image and only restates what the image cannot carry.

**For each character in the reference, capture:**

- **Hair:** color (every nuance), length, style, texture, parting, styling, accessories
- **Makeup:** skin finish, brow shape and density, eye treatment, lashes, lip register, cheek treatment, any face jewelry, freckles or beauty marks **only if visible**
- **Wardrobe:** every garment top to bottom — fabric, color, fit, structural details, neckline, sleeve length, hem position, layering
- **Jewelry & accessories:** every piece — earring style, necklace count and material, rings, bracelets, body chains, belts, bag, sunglasses, watch
- **Body markers:** piercings, tattoos, nail length and color (only if visible)
- **Pose and energy:** body angle, weight distribution, hand position, expression register

**For each environment in the reference, capture:**

- **Location:** interior or exterior, architecture, materials, scale
- **Time of day and weather:** lighting direction, quality, color temperature, sky, atmospheric conditions
- **Set dressing:** every visible object that shapes the world
- **Color palette:** dominant tones, accent colors, contrast structure

**Reference verbs Seedance reads cleanly:** `Reference`, `Extract`, `Combine`, `Follow`, `Generate from`, `using the composition from`, `maintaining consistent <feature>`. These are the action verbs to use inline when invoking a reference. Example: *"@image1 holds the pose, @image2's outfit applied, environment from @image3, action follows @video1."*

**Naming rule (absolute lock).** NEVER use proper names in the prompt output. Refer to every character by visual description only.

**No-invention rule.** If the user gives you a reference image and asks for the same character in a new scene, do not invent wardrobe or styling details that aren't in the image or specified in the request.

**Trust-the-reference rule.** Once a character's wardrobe and identity are anchored to an `@imageN` tag, the Subject Lock block in the prompt body does NOT re-describe every garment in detail. The lock-down line ("face, hair, wardrobe, and silhouette identical throughout") closes the block. Only state-changes the image can't carry (damp, dirty, torn, wet, dusty, bloodied) get spelled out.

**Identity-locking workflow (the practical trick for character continuity across multiple renders).** When generating multiple shots of the same character across separate renders, identity drifts. Counter it: (1) generate the first shot with text-only character descriptions; (2) screenshot the cleanest frame of each character; (3) upload those screenshots as `@image2`, `@image3`, etc. for subsequent renders; (4) reference them inline in the Subject Lock blocks. This is the standard avatar-locking pattern and the reason every named subject gets its own `@imageN` slot.

**Canonical-over-plate rule (HARD LOCK).** Every named subject that appears in a Seedance scene gets its canonical reference attached as its own `@imageN` slot — even if that subject is also visible in the rendered environment plate. Characters, vehicles, props, creatures, animals — anything with locked identity that needs to hold across the cut gets its dedicated reference, no exceptions. The plate carries the world (location, weather, light, set dressing, composition); canonical references carry identity (face, body, livery, markings, silhouette). The plate is never a substitute for a canonical reference, and a subject's visible presence in the plate never reduces or removes the requirement to attach its canonical reference. If a character's reference sheet exists, attach it. If a vehicle's canonical reference exists, attach it. Subject Locks anchor to the canonical reference tag; the World Plate block anchors to the plate tag. This is the rule that prevents identity drift between the plate and the rendered Seedance output.

---

## FRAME MAP

Every Seedance prompt includes a Frame Map block that anchors every subject in screen space before motion enters the picture. Think of the Frame Map as the floorplan of the shot — where everything sits when the camera rolls.

**Treat the frame as 2D screen space:**

- **Horizontal:** left third / center / right third — or x% precision (0% = left edge, 50% = center, 100% = right edge)
- **Vertical:** upper third / center / lower third — or y% precision
- **Depth:** foreground / midground / background
- **Frame occupancy:** close-up / medium / full body / waist-up / chest-up / extreme close-up — or % of frame height
- **Negative space:** what stays empty, where the empty space sits, what fills it (atmosphere, environmental detail, distant elements)

**Single-subject example:**

> Frame Map: @image1 anchored in the left third, x=30%, foreground, medium shot from waist up, occupying 55% of frame height. The right two-thirds hold wet street and distant neon signage as negative space.

**Two-subject example:**

> Frame Map: @image1 in the left third, x=28%, foreground. @image2 in the right third, x=72%, midground, slightly deeper. The center holds open as tense negative space between them. Neither crosses the central vertical axis.

**Multi-shot example:**

> Frame Map: Shot 1 (0–6s) — wide two-shot. @image1 in the left third, x=32%, foreground, bent at the waist. @image2 in the right third, x=68%, midground, leaning against @image3. Shot 2 (6–10s) — low-angle close-up at hip height looking up at the side window, framed tight on @image1's reflection in the wet glass.

**When to skip percentages:** for clear classical compositions (centered single, OTS, profile two-shot, symmetrical wide), use film language without percentages. Coordinates earn their place when the composition is asymmetric, tightly blocked, or character drift would visibly break the shot.

---

## SUBJECT LOCK

Every character in the frame gets a Subject Lock block. The Lock pins every property that needs to stay stable across the runtime — pose, gaze, contact points, state — without re-describing what the reference image already carries.

**Properties to pin per character:**

- **Identity anchor:** which `@imageN` carries the face, hair, wardrobe, silhouette
- **Body orientation:** facing camera / profile left / profile right / three-quarter toward screen-right or screen-left / back to camera
- **Pose:** the specific physical posture (standing, kneeling, leaning, seated, walking, bent at the waist, hands raised, hand resting on X)
- **State:** emotional register described by what the body and face physically do — never abstract feelings
- **Expression:** lips, eyes, brow, jaw register
- **Gaze direction:** looking at @imageN / looking screen-left / looking screen-right / looking offscreen toward X / locked on camera (rare)
- **Contact points:** where the body physically touches the world — feet on which surface, hand on which object, body part against which surface
- **State-change details the image can't carry:** damp, dirty, torn, wet, dusty, bloodied
- **Lock-down line:** "face, hair, wardrobe, and silhouette identical throughout"

**Single-character example:**

> Subject Lock — @image1: Face, hair, oxblood corset, and silhouette identical throughout. Ponytail damp from the drizzle, fabric darker where rain has soaked in. Bent at the waist, torso angled toward the side window of @image3, both hands raised to her ponytail at the crown, fingers smoothing strands. Body squared to the car, weight even. Gaze locked on her own reflection in the wet glass.

**Multi-character example:** each character gets a discrete Subject Lock block.

> Subject Lock — @image1: [block for first character]
>
> Subject Lock — @image2: [block for second character]

Never jam multiple characters into one Subject Lock paragraph. The discrete blocks make iteration easier and give Seedance cleaner anchoring.

---

## CROSS-FRAME RULES

When two or more characters share the frame, the Frame Map and Subject Lock blocks aren't enough on their own — the relationships between characters need their own explicit rules. Otherwise Seedance will sometimes swap them, cross them, drift their distance, or collapse their depth separation as the shot runs.

**Rules to specify for every multi-character shot:**

- **No swap:** characters never trade screen positions
- **No center crossing:** characters never cross the central vertical axis (unless an action demands it, in which case state the crossing with timing)
- **No depth change:** characters hold their depth layer throughout
- **Distance consistency:** the gap between them stays constant
- **Screen sides held:** left character stays left, right character stays right
- **Eyelines:** who looks at whom, and whether the look holds or breaks
- **Carry-across-the-cut:** for multi-shot sequences, name what holds when the camera cuts

**Standard language:**

> Cross-Frame Rules: @image1 and @image2 never swap positions, never cross center, never change depth. Distance, screen sides, eyelines, costumes, and silhouettes stay consistent across the full runtime.

**Multi-shot variant:**

> Cross-Frame Rules: @image1 holds her position at the side window across the full runtime of Shot 1. @image2 holds her lean at the rear quarter panel across Shot 1. In Shot 2 only the camera changes — @image1's position holds.

**When characters do need to cross:** state the crossing explicitly with timing. "At 4 seconds, @image1 steps across the central axis from the left third into the center. After 5 seconds, the new blocking holds: @image1 in the center foreground, @image2 unchanged in the right third midground."

---

## MOVEMENT

Movement in a Seedance shot is layered, not unified. The Movement block describes what happens across the runtime in flowing paragraph form, but the four layers — character motion, micro-motion, environmental motion, camera motion — should all appear in the description.

**The four layers (write them in this order in the paragraph):**

1. **Character motion** — what the subjects physically do across the runtime, with per-beat timestamps
2. **Micro-motion** — what moves on the body while the dominant action plays out (breath, hair, fabric, jewelry)
3. **Environmental motion** — what the world does around the subjects (rain, smoke, dust, traffic, wind, particles)
4. **Camera motion** — only when not already covered in the Camera Capture line; usually omitted from the Movement block since the Camera Capture handles it

**Single-shot example:**

> Movement: She takes one slow controlled step from the curb to the street across the first two seconds, then holds for the remaining eight. Ponytail catching subtle wind drift, parachute pants fabric rustling on the step, breath visible in the cold air on a controlled exhale, fingers flexing once inside her front pockets. Light cold rain falling at moderate density, neon reflections shimmering on the wet asphalt, distant taxi headlights moving slowly through the right midground, faint steam rising from a manhole grate behind her.

**Multi-shot example:**

> Movement: Shot 1 (0–6s) — @image1 smooths her ponytail at the crown, fingers working through strands. @image2 watches her with a soft closed-lip smile across the first three seconds, exhales a short scoff at 3 seconds, then turns her head slowly away toward the horizon screen-right and holds. Rain drizzles steadily, damp hair on both catches subtle wind, faint mist off the warm hood. Hard cut to Shot 2 (6–10s) — low-angle close-up looking up at the side window. Her eyes flick down and to the side once at 7 seconds — a single controlled eye roll — then return to her reflection. Hands resume smoothing the ponytail. Rain streaks roll down the wet glass naturally across the full close-up.

**Dialogue inside Movement.** Any line physically spoken in the scene goes inline in `"double quotes"`. The quotation marks signal Seedance to prioritise lip-sync, which the model now handles at millisecond precision. Example:

> @image1 leans against the car, exhales, and says `"I'm not waiting for you anymore,"` flat and quiet on the line, holding the gaze for one full second after the words land.

**Timeline-prompting variant (use only when pacing precision is the whole craft choice).** If the user needs second-by-second pacing control rather than flowing prose, bracketed timestamp markers can drive the Movement block instead:

> Movement: [0s] Wide locked-off, figure at end of rain-slicked street, framed from behind. [3s] Slow dolly forward begins, foreground rain pulls into shallow focus. [6s] Camera at medium shot now, figure turns head slightly — profile half-readable. [8s] Rack focus pulls to background city blur, then snaps back to subject.

Prose-with-hard-cut-keywords is the default. Timeline markers are an alternate, not a replacement.

**Critical rule:** never tangle the four layers. Each one named explicitly in the paragraph, even when one layer is "no motion" or "nothing else moves in the frame." Saying nothing moves is a directive; absence is not.

---

## LAST FRAME

Every prompt closes with a Last Frame block specifying the exact composition the shot lands on at the end of the runtime. Seedance reads it as a target and structures the motion of the shot to deliver that closing image.

**What goes in the Last Frame block:**

- Where each character sits at the close (carries the Frame Map forward to the end)
- Their final pose / state / gaze
- What the camera is showing in focus
- What's in negative space at the close
- The visual punctuation — what the viewer's eye lands on
- **On-screen text suppression line:** "No on-screen text, no captions, no signage typography, no rendered text in the frame." (skip only when text is explicitly requested)

**Strong examples:**

> Last Frame: Hold on her in the left third, eyes still tracking the now-passed taxi offscreen right, ponytail settling, rain visible on her shoulders, the center of the frame filled with empty wet street and reflected neon, taxi taillights fading at the right edge. No on-screen text, no captions, no signage typography, no rendered text in the frame.

> Last Frame: The camera holds tight on her face in the right third, eyes wide and steady, lips slightly parted on a held breath. Her opponent is fully out of frame on the left, leaving the left two-thirds of the frame as soft-focus rain and distant lit windows. No on-screen text, no captions, no signage typography, no rendered text in the frame.

**Last Frame is mandatory.** Every prompt closes with this block.

---

## WORLD PLATE

The World Plate block names the location, time of day, weather, set dressing, and atmospheric quality — anchored to a reference image when one is attached, or built from text when none is.

**Properties to specify:**

- **Location:** anchored to @imageN if a plate is attached; otherwise built from text
- **Time of day and weather:** lighting direction, quality, color temperature, sky, atmospheric conditions
- **Set dressing:** specific objects that shape the world (vehicles, signage, debris, vegetation, props, crowd)
- **Color palette:** dominant tones, contrast structure
- **Atmospheric quality:** haze density, particle suspension, weather intensity

**Single-shot example:**

> World Plate: Anchored to @image4 — cliffside overlook with low grass and exposed rock at the edge, the drop falling away behind @image3, dusk sky dropping from cool blue at top into deep magenta and warm tungsten residue at the horizon, distant clouds, light atmospheric haze. @image3 parked perpendicular to the cliff edge, paint slick with rain, side windows wet, faint mist off the warm hood.

**Text-only example (no plate attached):**

> World Plate: Midtown New York City street at 3 AM — wet black asphalt, mixed neon signage in magenta and cyan reflected across the puddles, distant traffic lights cycling, sparse pedestrian foot traffic far in the background. Light cold rain at moderate density. Steam rising from grates.

---

## SOUND BED

The Sound Bed describes **only what the scene physically produces** — sounds that exist within the world of the frame. Never reference music, lyrics, song names, soundtrack cues, or score. If the user wants music in the final cut, they upload the track as a separate audio reference inside Higgsfield.

**Allowed in the Sound Bed:**

- Footsteps (specify surface — wet pavement, gravel, polished floor, wood)
- Fabric movement (rustle, swish, whip on motion)
- Breath and breathing (steady, ragged, held, sharp inhale)
- Body sounds (hand on skin, grip on metal, jewelry chime)
- Object sounds (door, glass, paper, ceramic, metal, electronics, weapon mechanisms)
- Environmental ambient (room tone, wind, rain, traffic hum, distant horns, subway rumble, bird call, water, fire crackle)
- Mech / sci-fi diegetic (servos, weapon charging hum, pulse fire impact, alien screech, debris fall)
- Crowd diegetic (cheering, screaming, gasps, light stick taps, footsteps in unison)
- Stage diegetic (laser strobe hum, microphone handling noise, in-ear monitor cable rustle, stage floor creak, haze machine hiss)
- Weather and atmosphere (rain on lens, wind through structures, distant thunder, snowfall hush)

**Never in the Sound Bed:**

- Song names, artist names, album names
- Lyrics, sung vocals tied to a track
- "Music plays," "soundtrack swells," "song builds"
- Score descriptors (orchestral, synth pad, dramatic strings)
- Specific genre cues (hip hop beat drops, rock guitar)

**Audio modes (pick one based on user intent — ask if ambiguous):**

- **Mode 1 (default) — Diegetic with SFX and ambient.** Realistic in-scene audio. `Sound Bed: Diegetic only — [list of specific sounds], no music, no dialogue except what is physically spoken in frame.`
- **Mode 2 — Silent capture.** Used only when the user explicitly says they will upload music in post AND wants NO in-camera audio fighting it. `Sound Bed: NONE — fully silent capture. The audio track will be added separately in post.`
- **Mode 3 — Diegetic with SFX, no music explicitly.** Same as Mode 1, just confirming no music will be added. `Sound Bed: Diegetic only — [list of specific sounds], no music, no dialogue, no soundtrack.`

Mode 1/3 is the default. Use Mode 2 only when the user explicitly says they're adding a music track in post AND wants the video silent. At the API level, Mode 2 corresponds to `generate_audio: false`.

**Sound Bed example:**

> Sound Bed: Diegetic only — boots on wet pavement, fabric whip on movement, sharp inhale, distant traffic hum with layered horns, faint subway rumble below grade, rain hiss against the lens, wind cutting between buildings, no music, no dialogue except what is physically spoken in frame.

---

## CAPTURE REALISM BLOCK (LOCKED — THE REAL-FOOTAGE ENGINE)

This is the block that makes a shot read as real cinema capture instead of AI video. The Camera Capture line below names the *gear*; this block names the *physics* — the four mechanics that, in practice, are what separate footage that looks photographed from footage that looks rendered. It sits second-to-last in the block order, immediately before Camera Capture, and ships on every prompt unless the user explicitly asks for a glossy, clean, or commercial register.

**Why it exists:** the most common AI-video failure isn't bad framing or wrong lens — it's the over-contrasty, over-plastic look. That look comes from three things the model does by default: it invents flat single-plane staging (no air between subject and background), it renders moisture and skin as glossy/specular, and it over-renders contrast cues into clipped highlights and crushed blacks. This block attacks all three at the source. It is the codified, repeatable version of what hand-written one-off prompts had to spell out from scratch.

**The four mechanics — every Capture Realism block tunes all four to the scene.** Mechanic 1 (depth via suspended atmosphere) is default-on in every mode that has planes to separate — M1, M3, M4, and M5 always; M2 studio when there's any depth to read. It is the primary lever against the flat, over-contrasted, plastic look and should be scaled (thin/light/heavy) rather than dropped. Mechanics 2–4 tune or drop per scene as noted below.

**1. Depth via suspended atmosphere between planes — the three-depth-register pattern.** This is the single biggest lever for real-camera depth and the headline upgrade in 2.2. State that atmosphere — haze, mist, air density, particulate — is *suspended in the air between the camera, the subject, and the background*, layered explicitly across **three depth registers**: (a) foreground volumetric haze between camera and subject giving the closest air real physical body; (b) midground volumetric haze wrapping the subject and the ground, the layer where any light cones cut through it most densely; (c) deep-background volumetric haze and fog dissolving the deepest background structures into atmospheric perspective. The background renders softer, desaturated, and lower-contrast than the foreground. This is what makes a subject sit *inside* the depth of the frame rather than pasted onto a flat backdrop. Always tie it to the actual planes in this shot. Flat air is the headline AI tell — name the three registers every time.

**2. Moisture without shine (only if the scene is wet/humid/sweaty).** The default AI failure on any wet scene is glossy beads and specular sheen, which instantly reads CGI. If the scene has moisture of any kind, state it as *present but matte* — surfaces are damp, not beaded; wet but not glossy; moisture that mutes and saturates without producing a single specular hotspot. Damp matte hair, slight moisture on skin that stays matte, wet ground with muted (not mirror) reflection, wet paint that stays matte not showroom. If the scene is bone-dry, skip this mechanic entirely.

**3. Per-zone specular kill on skin — and the flattering ceiling.** "Matte skin" is too vague to hold. Name the zones individually: zero shine on forehead, zero shine on nose bridge, zero shine on cheekbones, zero shine on temples, zero shine on chin, zero shine on collarbones. The blown specular hotspot on a nose bridge or cheekbone is *the* AI-skin tell — naming each zone kills each hotspot. Pair it with the biology cues: real peach fuzz at jaw and hairline, real soft pore texture, light absorbed like true subsurface scattering, warmth preserved (slightly desaturated is fine, washed-out/pale/cool-shifted is not). **The flattering ceiling is locked on every face:** the texture is fine, soft, and even — never harsh, severe, or unflattering. No acne, no blemishes, no prominent spots, no scarring, no enlarged/cratered/rough pores, no brutal clinical macro-detail. Realism never makes a face look ugly. Matte carries the anti-plastic; fine-and-even carries the flattering; both run together, and any tension resolves toward flattering.

**4. Contrast curve stated three ways.** Over-contrast is the headline complaint, so attack it from three angles in the same block: (a) the tonal curve — shadows lifted gently, highlights rolled off softly, nothing clipping to pure white or crushing to pure black; (b) specular removal — all specular highlights surgically removed from skin, hair, fabric, and surfaces, every pixel reading matte and diffuse; (c) the grade — low-contrast, slightly desaturated, warmth preserved. Three statements of the same intent is what holds it; one statement gets overridden by the model's default contrast bias.

**Canonical Capture Realism block (tune every bracket to the scene):**

```
Capture Realism: [Foreground subject] sits inside real depth — [thin/light/heavy] atmosphere suspended in the air between camera, subject, and [the far background element], the background rendered softer, desaturated, and lower-contrast than the foreground so the figure sits within the air rather than pasted on a flat plane. [IF WET: Slight moisture has settled on every surface — damp matte hair, slight moisture on skin holding fully matte with no beading and no wet sheen, [wet ground with muted reflection / damp matte fabric / car paint damp but matte not showroom], moisture that mutes and deepens without a single specular hotspot.] Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones, temples, chin, and collarbones, real peach fuzz catching light at the jaw and hairline, real soft fine even pore texture, light absorbed like true subsurface scattering, warmth preserved and natural, slightly desaturated but never pale or washed-out or cool-shifted, never plastic, never doll-skin, never AI-rendered, and never harsh — no acne, no blemishes, no enlarged or rough pores, fine flattering texture that keeps the face looking good. Low-contrast curve — shadows lifted gently holding texture, highlights rolled off softly never clipping to white, nothing crushed to black. All specular highlights surgically removed from skin, hair, fabric, and surrounding surfaces, every pixel reading matte and diffuse. Slightly desaturated grade with warmth preserved.
```

**Tuning notes:**
- **Dry scenes:** delete the entire `[IF WET: ...]` sentence. Don't force moisture into a dry environment.
- **No humans (M5 / pure environment plates):** drop the skin sentence entirely. Keep mechanics 1 and 4 (atmosphere-between-planes and the contrast curve), and apply the matte-not-glossy logic to environmental surfaces (wet concrete, metal, glass) instead of skin.
- **Studio / M2 editorial:** if the user wants the *crafted* glossy editorial look, this block is reduced or skipped — M2 is the one mode where controlled specular (intentional highlight bloom on chrome/rhinestone) is intentional. Use judgment; ask if unsure.
- **Atmosphere density** scales with the scene: "thin atmosphere" for a clear interior, "light haze" for most exteriors, "heavy suspended mist" for a moody pre-dawn or a destroyed-city plate. The denser the air, the stronger the depth separation.
- **This block does not name gear, grade hex, frame rate, or runtime** — that all stays in Camera Capture. No overlap. Capture Realism is physics; Camera Capture is hardware.

**Relationship to the negative→positive rule:** this block leans positive ("reads matte," "lifted gently," "warmth preserved") rather than piling negatives, but the specular-kill and the anti-plastic clauses are the sanctioned exception — like the on-screen-text suppression, the "no shine / no plastic / no beading" phrasings are known-failure-mode suppressions that earn their place. Keep them tight; don't let the block balloon into a wall of negatives.

---

## CAMERA CAPTURE

The Camera Capture is the single closing line of every Seedance prompt. It contains body, lens, filter, movement, stock, grade, frame rate, runtime, aspect ratio, and optional seed — all in one trimmed paragraph.

**This is the only camera/grade/film stock language anywhere in the prompt.** No discrete `Camera:` block in the middle of the body. No double specification. The Camera Capture line carries it all.

**Default camera energy is handheld with breath, drift, and organic operator movement** — even in editorial / quiet / observational moments. The lived-in operator presence is part of the cinema register.

**Locked-off tripod is OPT-IN ONLY** — used only when the user explicitly requests "locked off," "tripod," "no camera movement," "static," "still camera," or names a specific shot type that requires it (overhead surveillance plate, surgical observation, security cam aesthetic, formal portrait studio plate).

**Seed line.** When iterating on a specific render to isolate the effect of prompt edits, append `seed: [N]` at the end of the Camera Capture line. On the first render of a new scene, omit the seed; on every subsequent re-roll where the seed should hold, append it.

---

## MODE-SELECT TABLE

| Mode | Use when scene is... | Capture | Lens | Movement | Diffusion | Grade |
|---|---|---|---|---|---|---|
| **M1 — Narrative** | Real-world dramatic — streets, kitchens, cars, bars, interiors, exterior locations. Anywhere lived-in. | Wide-latitude cinema capture | Vintage 2x anamorphic character, 40/55/75/100mm, wide aperture — oval bokeh, soft frame-edge falloff | Handheld with operator breath | Light diffusion bloom softening highlights | Color-negative daylight film rendition, fine 35mm grain, teal-amber |
| **M2 — Studio / Editorial** | White void, clean studio, hyperpop saturated set, fashion film, editorial portrait, performance-on-set | Wide-latitude cinema capture | Clean spherical character, 32/50/75/100mm, wide aperture — natural round bokeh, even sharpness | Locked tripod with optional slow push | Mild diffusion bloom; intentional highlight bloom on chrome/rhinestone | Saturated editorial, warm-retained blacks, fine grain |
| **M3 — Action / Combat** | Combat, chase, stunts, war, mech battles, alien encounters, debris, smoke, dust | Wide-latitude cinema capture | Vintage 2x anamorphic character, 40/55/75/100mm, wide aperture — oval bokeh, soft edge falloff | Handheld and shaky throughout, no stabilized shots | Light diffusion bloom softening highlights | Color-negative film rendition, heavier low-light grain, palette per scene, dusty haze |
| **M4 — Performance / Concert** | Stadium, arena, stage, jumbotron, lightstick crowd, festival pit | Wide-latitude cinema capture | Vintage 2x anamorphic character, 40/55/75/100mm, wide aperture — oval bokeh, horizontal streak flares on stage lights | Mixed handheld pit-photographer and orbital, hard cuts | Light diffusion bloom softening highlights | Color-negative film rendition, fine grain, desaturated cool with warm bloom, stage color cast |
| **M5 — Atmospheric / Empty** | Abandoned environments, no-humans plates, landscapes, weather pieces, mood/world establishing shots | Wide-latitude cinema capture | Vintage 2x anamorphic character, 35→85mm push range, wide aperture — oval bokeh, soft edge falloff | Locked-off or extremely slow push-in / pull-back | Light diffusion bloom softening highlights | Color-negative film rendition, fine grain, palette-driven (specify hex per scene) |

---

## MODE 1 — NARRATIVE (Real-World, Lived-In)

**When to use:** Real-world dramatic scenes. Streets, apartments, kitchens, cars, bars, diners, locker rooms, exterior locations, anywhere someone could plausibly walk into and shoot.

**Camera Capture line (drop in at end of any M1 prompt):**

```
Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft frame-edge falloff — light diffusion bloom softening highlights, handheld with natural operator breath, color-negative daylight film rendition with fine 35mm grain, teal-amber grade, shallow depth of field, 24fps 180° shutter, [aspect], [XX] seconds.
```

Replace `[XX]` with lens length (40mm wide, 55mm medium, 75mm tight, 100mm close-up), `[aspect]` with the ratio (9:16, 16:9, 21:9, 4:3, 1:1, 3:4), and the runtime.

**Multi-shot variant:**

```
Camera Capture: Shot 1 — wide-latitude cinema capture, vintage 40mm 2x anamorphic character at a wide aperture, light diffusion bloom softening highlights, handheld with natural operator breath. Shot 2 — same capture register, 75mm anamorphic character at a wide aperture, low-angle handheld at hip height, tight operator breath. Color-negative daylight film rendition with fine 35mm grain, teal-amber grade, shallow depth of field, 24fps 180° shutter, [aspect], [XX] seconds total.
```

---

## MODE 2 — STUDIO / EDITORIAL (Crafted, Not Photographed)

**When to use:** White void, clean studio sets, editorial portraits, hyperpop saturated worlds, fashion film, performance-on-set, any scene that is *crafted* rather than *photographed.*

**Character-build default — mid-grey seamless.** When the M2 prompt's primary job is to lock a character's identity (reference sheet, lookbook plate, 6-panel character grid, locked-pose portrait that downstream shots will reference), default the World Plate to **mid-grey seamless**, not pure white. See THE THREE HEADLINE UPGRADES section for the full reasoning and the canonical language. Only use white seamless when the user explicitly requests it (hard-key fashion editorial, high-key product, intentional blown-out aesthetic).

**Lens guide:**
- 32mm — full-body wide on the void / group framing
- 50mm — medium portrait
- 75mm — tight editorial face cuts
- 100mm — extreme close-ups (lips, eyes, jewelry, fabric)

**Camera Capture line:**

```
Camera Capture: wide-latitude cinema capture, clean spherical [XX]mm character at a wide aperture — natural round bokeh, even sharpness — mild diffusion bloom, locked tripod with optional slow push-in, saturated editorial grade, fine grain, warm-retained blacks, 24fps 180° shutter, [aspect], [XX] seconds.
```

For rhinestone, chrome, or surface-detail close-ups, add: `intentional highlight bloom on reflective surfaces, blooming the speculars on chrome and rhinestone.`

---

## MODE 3 — ACTION / COMBAT (Documentary-Sci-Fi)

**When to use:** Combat, chase, stunts, war, mech battles, alien encounters, fight choreography, any high-physicality scene with debris, smoke, dust, or destruction.

**Camera Capture line:**

```
Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft edge falloff — light diffusion bloom softening highlights, handheld and shaky throughout with no stabilized shots, color-negative film rendition with heavier low-light grain, [palette descriptor] with dusty atmospheric haze, 24fps 180° shutter, [aspect], [XX] seconds.
```

Replace `[palette descriptor]` with scene-appropriate language (e.g., "daylight overcast palette," "golden hour warm palette," "blue-hour cool palette," "stormy desaturated palette").

For impact slow-motion: append `intercut 96fps high-speed slow-motion at the [moment] holding 180° shutter for natural motion blur.`

---

## MODE 4 — PERFORMANCE / CONCERT (Pit-Photographer Documentary)

**When to use:** Stadium and arena performance shots, festival pits, concert footage, jumbotron-and-lightstick worlds, anywhere a performer is on stage with a crowd and stage lighting.

**Camera Capture line:**

```
Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, horizontal streak flares on stage lights — light diffusion bloom softening highlights, mixed handheld pit-photographer and orbital operator energy with hard cuts between angles, color-negative film rendition with fine grain, [stage-lighting color cast], heavy volumetric haze, real sweat sheen, 24fps 180° shutter, [aspect], [XX] seconds.
```

Replace `[stage-lighting color cast]` with scene-specific language (e.g., "magenta-red color cast from the LED cube above," "amber and ultraviolet wash from side rigs," "cyan and white strobe punching through warm tungsten").

---

## MODE 5 — ATMOSPHERIC / EMPTY (Environment & Mood)

**When to use:** Abandoned cityscapes, no-humans environment plates, landscapes, weather pieces, slow-burn mood shots, world-establishing footage where the environment is the subject.

Also use for: "no humans," "abandoned," "empty," "ghost city," "deserted," "weather plate," "establishing wide" requests.

**Camera Capture line:**

```
Camera Capture: wide-latitude cinema capture, vintage [XX]mm 2x anamorphic character at a wide aperture — oval bokeh, soft edge falloff — light diffusion bloom softening highlights, locked-off or extremely slow push-in only, color-negative film rendition with fine grain, palette grade [hex values], atmospheric haze, weathered material detail, 24fps 180° shutter, [aspect], [XX] seconds. No humans, environment is the subject.
```

Replace `[hex values]` with actual color codes for the scene's palette (e.g., "#2A3540, #4A5560, #6B7280, #8B7355, #A89178").

---

## STACKING MODES (Multi-World Sequences)

If a single Seedance sequence cuts between two worlds — for example, a music video that intercuts a white void (M2) with a kitchen (M1), or action footage (M3) intercut with performance footage (M4) — write each shot's Camera Capture specs inline in the closing line. Don't blend modes into one averaged grade. The cut between modes is the visual punch; collapsing them kills the contrast.

For multi-shot sequences in the same mode, you can compose one continuous prompt with hard-cut triggers in Movement and a single Camera Capture line with per-shot lens differences inline.

---

## LENS LENGTH GUIDE (across all modes)

- **32mm / 35mm / 40mm:** Wide establishing, full-body, group framing, environmental context
- **50mm / 55mm:** Medium portrait, two-shot, waist-up, dialogue framing
- **75mm:** Tight editorial portrait, single-character isolation, performance close-up
- **85mm / 100mm:** Extreme close-up — eyes, lips, jewelry, fabric texture, surface detail

When in doubt, default to 55mm (M1 / M3 / M4) or 50mm (M2) for medium framing. M5 typically uses the wider end (35→55mm) for environmental reach.

---

## FRAME RATE NOTES

All five modes default to **24fps with 180° shutter** for cinema-standard motion blur.

Slow-motion beats (impact, hair whip, fabric on a hit, water splash, weapon recoil): specify inside the Camera Capture line — `intercut 96fps high-speed slow-motion at [moment] holding 180° shutter.` Keep the base frame rate at 24fps.

---

## RUNTIME, ASPECT & PER-SHOT TIMING

**Total runtime + aspect** are stated in three places: title line above the code block, Frame Map block (for multi-shot sequences with per-shot timing), and the closing Camera Capture line. All three must match.

**Always ask runtime + aspect — never default.** If the user hasn't specified either, ask in the pre-prompt confirmation step.

**Shot complexity guidance (Seedance 2.0 hard cap is 12s per render):**
- **4–6 seconds** — one strong character action, single locked composition, 2–3 beats max
- **6–10 seconds** — one action plus reveal or hold, optional micro-shift in composition, 3–4 beats max
- **10–12 seconds** — 2–3 simple beats with hard cuts inside the prompt
- **Beyond 12 seconds** — split into separate prompts and stitch with Track Completion (see V2V appendix)

**Per-shot timing for multi-cut sequences:** when a single Seedance prompt contains more than one shot stitched with hard cuts, label each shot inline in the Frame Map and Movement blocks with its time range. The per-shot timing must add up to the total runtime stated in Camera Capture and the title.

**Aspect quick guide:**
- **9:16** — vertical for TikTok / Reels / Shorts / Stories
- **16:9** — landscape standard for YouTube / web / TV
- **21:9** — anamorphic widescreen for cinematic deliverables
- **4:3** — vintage television / lookbook / editorial
- **1:1** — square feed
- **3:4** — vertical photo / editorial portrait

---

## TEXT-IN-VIDEO OVERRIDE (when user explicitly requests on-screen text)

Default is no on-screen text. When the user explicitly requests text, slogans, titles, subtitles, or speech bubbles, replace the suppression line in Last Frame with one of these patterns:

**Slogan / title:**
> The text "[CONTENT]" enters lower-third at [Ns] in [color] [font weight] [font family], [appearance method — slams, fades, types in], [optional effect — chromatic aberration shimmer, slight glitch, soft glow]. Holds for the remaining runtime.

**Subtitles:**
> Subtitles appear at the bottom of the frame reading "[CONTENT]", synchronised with the dialogue rhythm, in white sans-serif with a subtle drop shadow.

**Speech bubble:**
> A speech bubble appears beside @image1 at [Ns] with the dialogue text "[CONTENT]", hand-drawn outline in black on white.

**Limit:** use common Latin or CJK characters. Rare glyphs and special symbols render as garbled shapes — keep typography clean.

When text is in the prompt, the Last Frame still names the closing composition; the text instruction is added, not substituted.

---

## NEGATIVE → POSITIVE REWRITES

Seedance responds far better to positive locks than to negative prohibitions.

| Instinct (negative) | Lock (positive) |
|---|---|
| Don't change face | @image1 keeps the same face, hair, wardrobe, and silhouette throughout. |
| Don't switch positions | @image1 remains in the left third throughout; @image2 remains in the right third throughout. Neither crosses the center line. |
| Don't drift | Boots stay planted on the same ground marks across the full runtime. Only breath, eyes, hair, and fabric move subtly. |
| Don't change costume | Wardrobe identical across the runtime. |
| No extra people | The frame contains only @image1 and @image2 in their specified positions. No other figures enter or pass through. |
| No on-screen text | No on-screen text, no captions, no signage typography, no rendered text in the frame. |
| No camera chaos | Slow controlled handheld with natural operator breath, preserving @image1 in the left third and @image2 in the right third throughout. |
| No blur | Subjects remain sharply focused; controlled cinematic motion blur appears only on falling rain and distant background light sources. |
| Don't blink mid-action | Gaze stays locked on @image2 across the full runtime, eyes steady, no break in eye contact. |
| No mode switching | The shot runs as one continuous take with no cuts, no scene change, no time jump. |

**Always prefer the positive form.** Negative phrasing belongs only in the explicit suppression lines for known Seedance failure modes (the on-screen text suppression is the canonical example).

---

## MULTIMODAL REFERENCE TEMPLATES

When references are uploaded, these are the inline patterns Seedance reads cleanly. Use them as drop-ins inside Subject Lock, Frame Map, World Plate, or Movement.

**Multi-angle subject (when uploading 2–3 angles of the same character or product):**
> *Reference / Extract / Combine the subject from @image1 and @image2, generate [scene description], maintaining consistent face, hair, wardrobe, and silhouette across the runtime.*

**Multi-image reference (different elements per image — character / outfit / location / prop / logo):**
> *The scene is set inside the location from @image4. The character from @image1 is wearing the outfit from @image2, performing the action shown in @video1. The prop from @image5 sits on the surface at x=70%.*

**Action / camera energy / FX from a reference video:**
> *Reference @video1's action and camera energy, generate the same beat in [new scene description], maintaining consistent motion detail and operator handheld feel.*

**Identity lock across multiple renders (the avatar-locking pattern):**
> Render 1 — generate with text-only character description, log the seed.
> Render 2+ — screenshot the cleanest frame of each character from Render 1, upload as `@image2`, `@image3`, etc. Reference inline in Subject Lock blocks: *"Subject Lock — @image2: face, hair, wardrobe, and silhouette identical to reference throughout."*

These templates layer on top of the ten-block format — they don't replace it. The Subject Lock still names pose, gaze, contact points, lock-down line.

---

## CAMERA / LENS / LIGHTING VOCABULARY (RELIABLE TRIGGER TERMS)

Use these terms verbatim inside the Camera Capture line or, where called out by name, inside Movement. They are cinematography vocabulary the model is trained on and they trigger reliably.

**Camera movement:** slow dolly in, dolly out, quick pan left, pan right, tracking shot (left to right), tilt down, tilt up, pull back reveal, arc shot / orbit, Steadicam walk, crane up, jib up, handheld with slight organic shake, locked-off, whip pan, rack focus from background to subject.

**Shot type:** extreme close-up (ECU), close-up (CU), medium close-up (MCU), medium shot (MS), wide shot (WS), establishing shot, over-the-shoulder (OTS), two-shot, point-of-view (POV).

**Lens / focus:** shallow depth of field, deep focus, rack focus (foreground to background), anamorphic lens flare, long-lens compression, wide-angle distortion, macro lens, tilt-shift.

**Lighting:** motivated lighting from practical source, hard rim light, low-key lighting, high-key lighting, silhouette against background light, golden hour, practical tungsten, hard side-lighting, motivated neon, bounce fill.

**Color / texture / atmosphere:** color grade: teal and orange, color grade: bleach bypass, desaturated, high-contrast, cool blue tones, amber-tinted, 35mm film grain, 16mm film grain, fog, rain, dust particles, heat haze, halation around highlights.

**Tone descriptors (use sparingly — Scene & Mood block, not Camera Capture):** tense, melancholic, urgent, serene, observational, intimate, documentary-style, commercial photography aesthetic, cinematic 4K.

These overlap with the mode-specific Camera Capture templates — use them inside the per-mode line when the default needs tuning (e.g., adding `rack focus from background to subject` inside an M1 Camera Capture, or `intercut 96fps high-speed slow-motion at the impact` inside an M3 Camera Capture).

---

## V2V APPENDIX — VIDEO EDIT OPERATIONS

Seedance 2.0 handles operations on an existing uploaded video. When the user wants to modify an existing render rather than generate from scratch, use these templates inside a single-block prompt (no Frame Map / Subject Lock structure — the original video carries the composition).

| Operation | Template |
|---|---|
| **Add element** | `At [time position] + [spatial position] of @video1, add [element]. Keep everything else unchanged.` |
| **Remove element** | `Remove [element] from @video1, keep everything else unchanged across the full runtime.` |
| **Modify / replace element** | `Replace [original element] in @video1 with [new element]. Hold position, lighting, and motion identical.` |
| **Extend forward / backward** | `Extend @video1 [forward / backward] by [N] seconds + [description of extended content, matching capture register and palette of the source].` |
| **Track completion (stitch up to 3 clips, ≤15s total)** | `@video1 + [transition description] + connect to @video2 + [transition] + connect to @video3.` |

Track Completion is the way to stitch separate Seedance generations together inside the model itself — useful when shot-to-shot identity drift is small enough not to need a hard re-render.

V2V prompts skip the ten-block format. They go in a single short directive paragraph with the operation template, the affected element, and a "keep everything else unchanged" clause.

---

## COMMON FAILURE MODES (Pre-Delivery Sanity Pass)

The headline failures that the QA pass is hunting for:

1. **Overloaded single beat.** Sprint + doorway + flashing lights + close-up + over-the-shoulder in one timestamp confuses the model. Fix: split across two timestamps with one camera instruction each.
2. **Vague camera language.** "The camera moves toward the subject" gives the model nothing concrete. Fix: "slow dolly in." Cinematography vocabulary is the model's strength.
3. **Inconsistent subject references.** Calling the subject "a man," then "the detective," then "he" produces character drift. Fix: pick one noun phrase or one `@imageN` tag and reuse it.
4. **Conflicting instructions.** "Peaceful meditation garden with loud rock concert and quiet library atmosphere" renders as artefacts. Fix: one mood, one palette, one sound design per beat.
5. **Skipping the global style line.** Without a closing style sentence (the Camera Capture line), Seedance defaults to its own aesthetic and you lose control of the look.
6. **Mismatched length to beat count.** Six distinct events in five seconds doesn't work. Fix: 4–6s = 2–3 beats; 10–12s = 3–4 beats.
7. **Wasting the audio capability.** "A dancer on a stage" (silent) misses what the model is built for. Fix: name the diegetic Sound Bed with specifics — pointe shoes tapping wood, audience gasp on a leap.
8. **Letting Seedance invent supers when you don't want them.** Without the suppression line, the model adds its own kinetic typography. Fix: keep the Last Frame suppression line on by default.
9. **Not locking the seed across iterations.** If you change the prompt and re-roll without the seed, you can't tell whether the change in output came from the prompt edit or random variation. Fix: capture the seed from the best generation and re-submit with edits.
10. **Plate substituted for canonical reference.** When the subject's identity holds only in the plate render, it drifts across re-rolls. Fix: always attach the canonical reference as its own `@imageN` slot, regardless of plate visibility.

---

## PRE-DELIVERY PASS (Silent QA — Run Before Every Delivery)

Before delivering the full prompt to the user, silently run this pass. If anything fails the check, fix it before the prompt ships. Do not narrate this pass — it happens internally.

**The pass:**

- [ ] Character gate asked (if first prompt of session) and answer carried
- [ ] Every uploaded reference image identified and listed by short visual descriptor — first bullet of the pre-prompt check, numbered bullet list at top of delivery, and inline `@imageN` tag. Order matches across all three.
- [ ] **Canonical reference attached for every named subject that appears in the scene, even when that subject is also visible in the rendered plate** — characters, vehicles, props, creatures. Plate carries the world; canonical reference carries identity. No exceptions. Subject Lock for every canonical-referenced subject anchored to its own `@imageN`.
- [ ] Mode selected (M1 / M2 / M3 / M4 / M5) with rationale
- [ ] Frame Map block written — every character pinned to a screen position, depth layer, frame occupancy
- [ ] Subject Lock block written for every character — identity / orientation / pose / state / gaze / contact points / state-changes / lock-down line. Wardrobe NOT re-described from reference image — only state-changes the image can't carry.
- [ ] Cross-Frame Rules written if 2+ characters in frame — no swap, no center cross, no depth change, distance held, screen sides held
- [ ] Movement block written — four layers present (character / micro / environmental / camera) in paragraph form, per-beat timestamps where the action demands. Dialogue in `"double quotes"`.
- [ ] Last Frame block written — exact closing composition stated, on-screen text suppression line included (unless user requested in-frame text via the TEXT-IN-VIDEO OVERRIDE)
- [ ] World Plate written — location, time, weather, set dressing, anchored to plate ref if attached
- [ ] Sound Bed written — diegetic mode chosen, specific sounds listed, no music referenced
- [ ] Capture Realism block written and tuned to the scene — depth-via-suspended-atmosphere named across the **three depth registers** (foreground / midground / deep-background); moisture-without-shine ONLY if the scene is wet (deleted if dry); per-zone specular kill on skin (dropped if no humans); contrast curve stated three ways. Not duplicating any gear/grade/frame-rate language from Camera Capture. Reduced or skipped only if the user explicitly asked for a glossy/clean/editorial register.
- [ ] Volumetric atmosphere named in the World Plate too (not only in Capture Realism) — the three-depth-register pattern surfaces in both blocks
- [ ] Mid-grey seamless used as the default for any character-build / reference-sheet / lookbook prompt — never pure white unless explicitly requested
- [ ] Zero brand-name gear stacks in Camera Capture — no ARRI, no Panavision, no Cooke, no Kodak, no Tiffen, no SkyPanel, no Astera, no Easyrig, no Tilta. Behavior language only.
- [ ] Camera Capture line at the bottom — single trimmed paragraph, body / lens / filter / movement / stock / grade / frame rate / aspect / runtime / optional seed, no double camera spec
- [ ] Lens length chosen for the framing
- [ ] Runtime + aspect confirmed with the user (never assumed). Values in title match values in Camera Capture.
- [ ] Per-shot timing planned for multi-cut sequences, summing to total runtime
- [ ] No character names in prompt output
- [ ] No real brand names in prompt output
- [ ] No platform/tool names in prompt output
- [ ] No internal production context, no meta-commentary, no abstract emotional intent
- [ ] No music, no lyrics, no song references in Sound Bed
- [ ] Output language locked to English inside the code block
- [ ] Three-part delivery format: (1) numbered bulleted reference list, (2) bolded English title with runtime + aspect, (3) English code block with labeled blocks and `@imageN` tags
- [ ] All ten labeled blocks present in the code block, in exact locked order: Scene & Mood → Frame Map → Subject Lock(s) → Cross-Frame Rules → Movement → Last Frame → World Plate → Sound Bed → Capture Realism → Camera Capture. None missing, none reordered, none merged, none renamed.
- [ ] Every reference in the bullet list appears at least once as an `@imageN` tag inside the code block, numbering matches exactly
- [ ] Negative prohibitions translated to positive locks throughout
- [ ] Total prompt body word count within target range (280–400 single shot, up to 600 multi-shot)

**Repair pass — if any of these conditions are detected, fix before delivery:**

- **Too poetic or abstract** → rewrite Scene & Mood as physical visual instructions
- **Overloaded with action** → split into a multi-shot sequence
- **Character might drift** → tighten Subject Lock with contact points and ground marks
- **Characters might swap positions** → tighten Cross-Frame Rules
- **Wardrobe re-described from the image** → cut redundant description, trust the reference
- **Double camera spec detected** → collapse to single Camera Capture line at the bottom
- **Mode register conflict** → keep one cinema mode dominant per shot
- **Action too complex** → keep one dominant character motion, push the rest into the next shot
- **Last Frame missing or vague** → write a specific closing composition
- **Prompt word count over target** → trim Subject Lock and Movement first, then Cross-Frame Rules
- **Aspect ratio missing from Camera Capture** → add it before delivery
- **Seed expected but missing on a re-roll** → append `seed: [N]` to Camera Capture

---

## WORKED EXAMPLES (TEN-BLOCK FORMAT)

These are full production-ready prompts in the locked ten-block format, written for the four most common briefs.

### Example 1 — M1 Narrative single-shot (8s, 9:16, golden-hour cliff)

References:
1. Subject — woman in beige trench coat, mid-shot reference
2. Plate — fog-covered cliffside at golden hour

**Seedance prompt — 8s, 9:16**

```
Scene & Mood: A held breath at the edge of the world — a figure facing weather she does not flinch from.

Frame Map: @image1 centered, x=50%, y=55%, foreground, full-body framed from waist up, occupying 60% of frame height. The upper third holds sky and distant sea fog as negative space. A single seabird crosses from left to right at 4s, passing through x=20% to x=80% at y=30%.

Subject Lock — @image1: Face, hair, beige trench coat, and silhouette identical throughout. Standing squared to the cliff edge, feet planted shoulder-width on damp grass, hands at her sides, hair whipping in the wind. Body weight even, slight forward lean into the wind. Gaze locked on the horizon screen-forward, eyes steady, lips closed on a held breath.

Cross-Frame Rules: Single subject — no swap or cross applies. Subject holds her ground mark across the full runtime.

Movement: She holds her position across the full 8 seconds, the only character motion a single slow controlled exhale at 5s that you read in her shoulders rather than her face. Hair whipping continuously, trench coat hem catching wind drift, fabric rippling on the legs of the coat. A single seabird cuts across frame from left to right between 3s and 5s, passing in mid-distance. Fog drifts slowly across the cliffside from screen-right to screen-left, sea spray haze suspended in the air, distant cloud bank moving almost imperceptibly.

Last Frame: Hold on her in the center, gaze unchanged on the horizon, hair still moving, coat hem still drifting, the seabird now offscreen right, the upper half of the frame filled with golden light cutting through suspended fog, the lower third holding cliff grass and the drop. No on-screen text, no captions, no signage typography, no rendered text in the frame.

World Plate: Anchored to @image2 — cliffside overlook with low wind-flattened grass and exposed rock at the edge, the drop falling away into deep grey ocean, golden hour sky in warm amber up top dropping to cool steel grey at the horizon, distant fog bank, light atmospheric haze suspended over the water.

Sound Bed: Diegetic only — distant gull calls, low constant ocean roar from below the cliff, wind cutting steadily through the grass, fabric flap on the trench coat, a single quiet exhale at 5s, no music, no dialogue.

Capture Realism: The figure sits inside real depth — light haze suspended in the air between camera, subject, and the far ocean fog bank, the background rendered softer, desaturated, and lower-contrast than the foreground so the figure sits within the air rather than pasted on a flat plane. Slight moisture has settled on every surface from the sea spray — damp matte hair, slight moisture on skin holding fully matte with no beading and no wet sheen, damp matte trench coat fabric, moisture that mutes and deepens without a single specular hotspot. Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones, temples, chin, and collarbones, real peach fuzz catching light at the jaw and hairline, real soft fine even pore texture, light absorbed like true subsurface scattering, warmth preserved and natural, slightly desaturated but never pale or washed-out or cool-shifted, never plastic, never doll-skin, never AI-rendered, and never harsh — no acne, no blemishes, no enlarged or rough pores, fine flattering texture that keeps the face looking good. Low-contrast curve — shadows lifted gently holding texture, highlights rolled off softly never clipping to white, nothing crushed to black. All specular highlights surgically removed from skin, hair, fabric, and surrounding surfaces, every pixel reading matte and diffuse. Slightly desaturated grade with warmth preserved.

Camera Capture: wide-latitude cinema capture, vintage 40mm 2x anamorphic character at a wide aperture — oval bokeh, soft frame-edge falloff — light diffusion bloom softening highlights, handheld with natural operator breath, color-negative daylight film rendition with fine 35mm grain, warm amber highlights cooling to steel grey shadows, shallow depth of field, 24fps 180° shutter, 9:16, 8 seconds.
```

### Example 2 — M2 Studio / Editorial single-shot (6s, 4:3, product close-up)

References:
1. Product — glass bottle, three-quarter reference

**Seedance prompt — 6s, 4:3**

```
Scene & Mood: A reveal staged with the patience of a still photograph that decided to move.

Frame Map: @image1 centered, x=50%, foreground, occupying 70% of frame height at the open of the shot. The frame opens tight on the bottle and widens to reveal a single green branch entering from screen-left at x=25% by the close.

Subject Lock — @image1: Face of the bottle squared to camera, silhouette and label identical to reference throughout. Standing on a polished marble surface, no tilt, no drift, base planted dead-center at the open.

Cross-Frame Rules: Single subject — no swap applies. The bottle holds its position; only the camera moves and the branch enters.

Movement: The camera holds tight on the bottle across the first 2 seconds, the only motion a slow controlled pull-back. From 2s to 5s the camera continues a smooth dolly back as the framing widens, revealing the surrounding marble surface and a single green branch entering from screen-left. At 5s the camera settles into a clean medium product shot, static. Single light catches the glass at different angles across the pull-back, refracting through the liquid inside. No environmental motion in the background — the void stays still.

Last Frame: A clean medium product composition. Bottle centered at x=50%, green branch entering from screen-left at x=25%, polished marble surface holding the lower third, soft seamless background behind. The eye lands on the bottle's neck, lit cleanly. No on-screen text, no captions, no signage typography, no rendered text in the frame.

World Plate: Seamless soft warm-grey studio backdrop, polished off-white marble surface with subtle veining holding the lower third, single backlit key from camera-right rim-lighting the bottle, soft fill from camera-left, completely controlled environment, no ambient light leak.

Sound Bed: Diegetic only — faint room tone, soft mechanical hum of the studio HVAC, no footsteps, no music, no dialogue.

Capture Realism: The bottle sits inside controlled studio depth — thin atmosphere suspended in the air between camera, subject, and the soft backdrop, the background rendered slightly softer and lower-contrast than the foreground so the bottle sits within the air rather than pasted on a flat plane. Low-contrast curve — shadows lifted gently holding marble texture, highlights rolled off softly on the glass rim, nothing clipping to pure white, nothing crushed to pure black. Glass surfaces hold intentional controlled specular bloom on the bottle's curve and shoulder — this is the one mode where editorial highlight bloom is intentional, blooming the speculars on the glass without going to clinical mirror. Slightly warm-retained grade.

Camera Capture: wide-latitude cinema capture, clean spherical 75mm character at a wide aperture — natural round bokeh, even sharpness — mild diffusion bloom, slow dolly back from tight close-up to medium static, intentional highlight bloom on reflective glass surfaces, saturated editorial grade, fine grain, warm-retained blacks, 24fps 180° shutter, 4:3, 6 seconds.
```

### Example 3 — M1 Narrative multi-shot prose (10s, 16:9, rain-slicked street, two characters)

References:
1. Character A — woman in oxblood corset, three-quarter reference
2. Character B — woman in cropped jacket, three-quarter reference
3. Vehicle — white low-slung mid-engine sports car, three-quarter exterior reference

**Seedance prompt — 10s, 16:9**

```
Scene & Mood: A standoff written in glances at a rain-slicked car between two women who already know how this ends.

Frame Map: Shot 1 (0–6s) — wide two-shot. @image1 in the left third, x=30%, foreground, bent at the waist toward the side window of @image3. @image2 in the right third, x=70%, midground, leaning against the rear quarter panel of @image3. The car @image3 sits across the lower two-thirds, slick with rain, framed parallel to the road. Shot 2 (6–10s) — low-angle close-up at hip height looking up at the side window, framed tight on @image1's reflection in the wet glass.

Subject Lock — @image1: Face, hair, oxblood corset, and silhouette identical throughout. Ponytail damp from the drizzle, fabric darker where rain has soaked into the corset shoulders. Bent at the waist, torso angled toward the side window of @image3, both hands raised to her ponytail at the crown, fingers smoothing strands. Body squared to the car, weight even on planted boots. Gaze locked on her own reflection in the wet glass.

Subject Lock — @image2: Face, hair, cropped jacket, and silhouette identical throughout. Hair damp at the ends from the drizzle. Leaning on the rear quarter panel of @image3, right shoulder resting on the metal, left hand in the pocket of her jacket. Body angled three-quarter toward camera but eyes on @image1. Closed-lip soft smile across the first three seconds, jaw relaxed, eyes amused but quiet.

Cross-Frame Rules: @image1 and @image2 never swap positions, never cross center, never change depth. Distance, screen sides, eyelines, costumes, and silhouettes stay consistent across the full runtime. In Shot 2 only the camera changes — @image1's position holds.

Movement: Shot 1 (0–6s) — @image1 smooths her ponytail at the crown, fingers working through damp strands across the full six seconds. @image2 watches her with the soft closed-lip smile across the first three seconds, exhales a short scoff at 3s, then turns her head slowly away toward the horizon screen-right and holds. Rain drizzles steadily, damp hair on both catches subtle wind, faint mist rising off the warm hood of @image3, distant traffic moving slowly through the deep background. Hard cut to Shot 2 (6–10s) — low-angle close-up looking up at the side window. Her eyes flick down and to the side once at 7s — a single controlled eye roll — then return to her reflection. Hands resume smoothing the ponytail. Rain streaks roll down the wet glass naturally across the full close-up.

Last Frame: Hold on the tight reflection of @image1 in the wet side window, eyes back on herself, hands still working through the ponytail, rain streaks rolling down the glass, the city background visible as soft-focus blur behind the reflection. No on-screen text, no captions, no signage typography, no rendered text in the frame.

World Plate: Midtown street at 3 AM — wet black asphalt, mixed neon signage in magenta and cyan reflected across the puddles, distant traffic lights cycling through the deep background, sparse pedestrian foot traffic far in the background. Light cold rain at moderate density. Steam rising from grates. @image3 parked parallel to the curb, paint slick with rain, side windows wet, faint mist off the warm hood.

Sound Bed: Diegetic only — light rain on metal and pavement, fabric whip on @image1's hand movement, the short scoff from @image2 at 3s, distant traffic hum with layered horns, faint subway rumble below grade, rain hiss on the camera lens, no music, no dialogue except the scoff.

Capture Realism: Both figures sit inside real depth — light haze suspended in the air between camera, subjects, and the deep city background, the background rendered softer, desaturated, and lower-contrast than the foreground so the figures sit within the air rather than pasted on a flat plane. Slight moisture has settled on every surface — damp matte hair on both, slight moisture on skin holding fully matte with no beading and no wet sheen, wet ground with muted reflection not mirror, car paint on @image3 damp but matte not showroom, moisture that mutes and deepens without a single specular hotspot. Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones, temples, chin, and collarbones, real peach fuzz catching light at the jaw and hairline, real soft fine even pore texture, light absorbed like true subsurface scattering, warmth preserved and natural, slightly desaturated but never pale or washed-out or cool-shifted, never plastic, never doll-skin, never AI-rendered, and never harsh — no acne, no blemishes, no enlarged or rough pores, fine flattering texture that keeps both faces looking good. Low-contrast curve — shadows lifted gently holding texture, highlights rolled off softly never clipping to white, nothing crushed to black. All specular highlights surgically removed from skin, hair, fabric, and surrounding surfaces, every pixel reading matte and diffuse. Slightly desaturated grade with warmth preserved.

Camera Capture: Shot 1 — wide-latitude cinema capture, vintage 40mm 2x anamorphic character at a wide aperture, light diffusion bloom softening highlights, handheld with natural operator breath. Shot 2 — same capture register, 75mm anamorphic character at a wide aperture, low-angle handheld at hip height, tight operator breath. Color-negative daylight film rendition with fine 35mm grain, teal-amber grade, shallow depth of field, 24fps 180° shutter, 16:9, 10 seconds total.
```

### Example 4 — V2V edit on existing footage

References:
1. Source video — @video1 (existing 6s clip of two characters at a car)

**Seedance prompt — V2V add element**

```
At 3 seconds, in the upper-right quadrant of @video1, add a single seabird crossing the frame from screen-right to screen-left in mid-distance. Match the existing motion blur character, the existing rain density, the existing color grade, and the existing 35mm grain. Keep every other element of @video1 unchanged across the full runtime — character positions, wardrobe, car position, lighting, rain, atmospheric haze all identical.
```

V2V prompts skip the ten-block format and ship as a single directive paragraph.

---

## WHEN NOT TO USE THIS SKILL — HANDOFFS

This skill is for Seedance 2.0 video prompts. Hand off when the brief is something else:

- **Still image, poster, mockup, photo edit** → use `nano-banana-prompter`. Seedance only makes video.
- **Animate a specific existing still with very tight camera control** → consider `kling-prompter`. Image-to-video is Kling's strongest mode.
- **Identity-locked character across many separate video shots when 2–3 clean portraits already exist** → consider `kling-prompter` with its Elements feature.
- **Pull live web data into a visual** → use `nano-banana-prompter` (Nano Banana 2 / Pro). Seedance has no web access.
- **Brand-mandated pixel-perfect typography in the frame** → render text in `nano-banana-prompter` or a post editor. Seedance's native supers are good for stylised text only.
- **Chained workflow** (e.g., generate hero still in Nano Banana, then animate in Seedance) → use `gen-media-router` to pick the recipe, then return to this skill for the Seedance leg.

---

## OPTIONAL HANDOFF — BANANA PRO DIRECTOR

If the user mentions they have a Banana Pro plate for the environment, want camera grammar to match an existing plate, or are pairing a Seedance prompt with a still they already built in Banana Pro, ask which cinema mode the plate used and lock the matching camera grammar in the Seedance prompt. The two skills share the same five-mode framework — when paired, the still and the video share visual DNA.

Otherwise, do not bring this up. Cinema-worldbuilder operates standalone unless the user invokes the pairing.

---

## CHANGELOG

**2.2 (this version)** — Folded in three headline upgrades from the field-tested OUR TURN pipeline: (1) **Volumetric atmosphere in every frame** — promoted to a top-of-skill principle with the explicit three-depth-register pattern (foreground / midground / deep-background), added the canonical haze-density vocabulary, expanded Capture Realism mechanic 1 to enforce the three registers, added QA item to surface volumetric atmosphere in the World Plate too (not only Capture Realism). (2) **Mid-grey seamless default for character builds** — added to M2 Studio mode and to the headline-upgrades section, with the canonical "even neutral mid-gray, no seam line, no gradient" backdrop language and the relight-from-scratch one-source pattern. (3) **Cameras described by behavior, not brand names** — expanded Universal Rule 11 with the explicit list of banned brand stacks (ARRI Alexa, Panavision, Cooke, Kodak Vision3, Tiffen Black Pro-Mist, ARRI SkyPanel, Astera Titan, Easyrig, Tilta Nucleus), added the full brand→behavior substitution table, added QA item to catch any brand-name leak. Bumped name to `cinema-worldbuilder-pro-2.2`.

**2.1** — Full merge with the seedance-2-prompter base skill. Added Seedance 2.0 model & render specs section (Fast/Standard/Pro variants, 4–12s durations, aspect ratios, 480p iterate / 720p finalize, seed capture). Added aspect ratio as a required field in pre-prompt confirmation and Camera Capture. Added dialogue-in-`"double quotes"` lip-sync pattern in Movement. Added timeline-prompting variant (bracketed `[Ns]` markers) as alternate to default prose-with-hard-cuts. Added reference verb vocabulary (`Reference`, `Extract`, `Combine`, `Follow`, `Generate from`). Added MULTIMODAL REFERENCE TEMPLATES section (multi-angle subject, multi-image reference, action-from-video, identity-lock workflow). Added CAMERA/LENS/LIGHTING VOCABULARY section with reliable trigger lists (camera movement, shot type, lens/focus, lighting, color/texture, tone). Added TEXT-IN-VIDEO OVERRIDE section for explicit user-requested on-screen text. Added V2V APPENDIX with add/remove/modify/extend/track-completion operation templates. Added COMMON FAILURE MODES sanity list. Added WORKED EXAMPLES section with four full ten-block prompts (M1 single-shot, M2 product, M1 multi-shot two-character, V2V edit). Added WHEN NOT TO USE THIS SKILL handoff section (nano-banana, kling, gen-media-router routing). Expanded RUNTIME section with aspect quick guide and Seedance hard caps. Seed line added to Camera Capture.

**2.0** — Original cinema-worldbuilder framework: five-mode grammar (M1–M5), ten-block locked order, Frame Map / Subject Lock / Cross-Frame Rules / Capture Realism, density discipline, English-only output, three-part delivery format.


<!-- ═══════ FILE: seedance-2-prompter/references/director-v3.md ═══════ -->

# Director v3 — the locked 16-slot production spine (Seedance 2.0)

> **When to read this file.** This is the **top register** of `seedance-2-prompter` — Tier 3+ production deliverables where nothing may drift: locked spatial geometry, ensembles, lipsync, strobe, heavy-mass action, multi-shot sequences that must hold identity and light across every cut. It supersedes `references/director-mode.md` for those jobs.
>
> **Route between the three registers like this:**
>
> | Register | Read | Use for |
> |---|---|---|
> | **Quick mode** | `SKILL.md` — the 6-step formula | Tier 1–2. Iteration, UGC, hooks, single shots, simple i2v. 60–250 words. |
> | **Director mode (10-block)** | `references/director-mode.md` | Tier 3. Reference-anchored production with the M1–M5 cinematography modes, Frame Map / Subject Lock / World Plate grammar. Reach for it when the *mode archetype* is the useful abstraction. |
> | **Director v3 (16-slot)** | **this file** | Tier 3+. Maximum rigor. Reach for it when the failure you are defending against is **drift** — bodies moving between cuts, geometry inverting, lip closures vanishing, wardrobe mixing, air turning into fog-machine smoke. |
>
> **Never blend two registers in one prompt.** Pick one grammar and hold it.
>
> **This file is scoped to Seedance 2.0 — 9 image references, 15 second ceiling.** If the surface in front of you runs **2.5** (50 assets, 30 s native, `@Image N` binding sentences), the equivalent file is `seedance-25-director/references/production-spine.md`. Do not carry 2.0's caps onto 2.5 or 2.5's asset load onto 2.0.

Every prompt is a production document. Who is in frame, what they look like, where they stand in depth, what they do, how gravity acts on them, how it is filmed, what the air does, what is heard, and what must not drift.

**The model is a physics engine, not a mood board.** It renders what it can see, count, and weigh. Mood words evaporate.

**If a word does not produce a visible pixel or an audible sound, cut it.**

---

## STEP ZERO — CONFIRM THE CEILINGS

Two hard caps on Seedance 2.0 shape the architecture of the prompt, not just its trim:

| | Seedance 2.0 |
|---|---|
| **Image references** | 9 maximum (plus 3 video, 3 audio; 12 files total) |
| **Maximum runtime** | 15 seconds |

**Reference slots are scarce, so every slot is contested.** The ordering is a rationing scheme: characters first in narrative order, then one shared group wardrobe sheet, then props, then the environment plate, then video or audio last. Collapse where you must — a prop that only needs to read approximately can live inside a character's Asset description instead of taking a slot. Anything past 15 seconds splits into two prompts.

**Universal Reference Mode only.** The 9-image budget exists in Universal Reference Mode. If the brief needs a hard first or last frame, that render is in First/Last Frame Mode and takes **no other references at all** — see SKILL.md, "Input modes are mutually exclusive." A v3 prompt with an Assets block is a Universal Reference Mode prompt by construction.

**More references is not automatically better.** Every reference must do distinct work. Near-duplicate references blend and produce an averaged face, and a cluttered reference set drifts worse than a tight one. If two references would teach the model the same thing, ship one.

**Runtime available is not runtime required.** A 15-second ceiling does not mean 15-second prompts. Two camera vantages on the same action are still two prompts — that split is about coverage, not about the cap.

**If the user is on a surface running Seedance 2.5**, stop and switch to `seedance-25-director/references/production-spine.md`: 50 assets, 30 s native, multi-round extension to ~90 s, and a mandatory per-asset binding sentence. A 2.0-shaped prompt on 2.5 leaves most of the identity budget unspent.

---

## WRITE THE VISIBLE

| Instead of | Write |
|---|---|
| she looks stressed | shoulders lift, jaw locks, exhales through the nose, eyes fix on the door |
| the alley feels dangerous | one buzzing bulb 30 metres back, wet brick, standing water, no other figures |
| fast chase | carves through traffic at 110 km/h, leg dragging outside the lane line on turn-in |
| she looks tall next to him | she stands 183cm to his 168cm |
| heavy mech | five-ton mass, cratering the ground on landing |

**Measurables the model reads:** speed in km/h · height in cm · mass in kg or tons · atmosphere as density plus named depth planes · direction as screen-relative or character-relative (always labelled) · emotion rendered in muscle · contact rendered as deformation.

---

## LENGTH DISCIPLINE

A four-shot sequence with four assets lands at **900–1,400 words**. Past that the CRITICAL blocks lose weight against the descriptive body. Every line is a lock, not a flourish.

**Every fact lives in exactly one slot.** Wardrobe lives in Assets and is never re-described in Action Timing — Action Timing names a garment only when it is doing something visible (a hem swinging, hair whipping clear). Light lives in slot 10. Atmosphere lives in slot 11. A prompt that repeats itself reads long without reading specific, and the duplicate dilutes the original.

---

## DELIVERY

Three parts, nothing else:

1. **Bolded title with runtime** — `**Underground garage — entry walk — 8s**`
2. **Numbered reference list** in attach order — max 9 images, plus video and audio slots (12 files total)
3. **One fenced code block** containing the whole prompt, English only

No preamble, no post-amble. Flag a conflict in one or two lines above the title if one exists.

**A NEGATIVE PROMPT block ships as an optional second code block** — but only **where the surface actually exposes a negative-prompt field.** Seedance 2.0 through ModelArk and the Higgsfield Studio is prompted inline; if there is no field, fold the negations into the slot that owns them rather than shipping a block nobody can paste. Where the field does exist, use it only for known drift risk (mixed character designs, locked spatial geometry, identity swaps) or on request, grouped by failure category, comma-separated, no sentences.

**Iterations deliver directly.** Any tweak to an approved prompt — palette, framing, pose, lens, lighting, wardrobe, staging, duration — ships as the revised full prompt, no confirmation bullets. Re-check only on full scope change: new scene, new character set, new capture family.

**Always ship the full prompt.** Never partial swaps or "replace this line" unless a targeted patch is requested.

**Split rather than overload.** Two camera vantages on the same action are two prompts. Anything past the 15-second ceiling is two prompts. Say so and deliver both.

---

## THE SPINE (LOCKED ORDER)

```
1.  HEADER              shot count · runtime · timecodes · cut policy · speed policy
2.  STYLE PREFIX        the invariants — style, operating style, texture, skin, technical
3.  NO ON-SCREEN TEXT   mandatory, always here, never lower
4.  CRITICAL BLOCKS     scene-specific, cap 4
5.  ASSETS              @tag = identity + THIS SCENE action + fidelity assertion
6.  GEOMETRY MAP        absolute frame position and depth planes
7.  FIRST FRAME         what is already happening at frame one
8.  OPTICS              lens lock in FOV degrees, per shot
9.  CAMERA              physicality register and behaviour
10. LIGHT & COLOUR      direction, quality, temperature + the percentage doctrine
11. ATMOSPHERE          air density, depth planes, source-bound vapor
12. ACTION TIMING       timecoded beats, hard cuts inline
13. PHYSICS             mass, deformation, rebound, lag, contact
14. ACTING              face, eyes, brow, liveness
15. AUDIO               diegetic default, or attached-track sole source
16. LOCKS               positive ordered chain of what must hold
```

No mode label. No prose between blocks. No aspect ratio.

---

## SLOT 1 — HEADER

```
4 shots. Total 8 seconds — shot 1 runs 0.0–2.0s, shot 2 runs 2.0–4.0s, shot 3 runs 4.0–6.0s, shot 4 runs 6.0–8.0s. Hard cuts between them, no transitions, no dissolves. All shots real-time, no slow motion, no overcranking, no ramping, no speed change anywhere in this sequence.
```

Single take: `1 continuous shot. Total 10 seconds, no cuts, no transitions. Real-time throughout.`

Timings sum exactly. **Maximum 15 seconds.**

Runtime guide: 1.5–2.5s per shot for high-energy cutting · 2.5–4s for narrative and dialogue beats · 4–7s for a held lipsync line · 8–15s for a continuous take.

**Past about 10 seconds the header also declares the shot budget** so the model does not compress the whole sequence into the first third: `6 shots across 14 seconds` reads very differently from `14 seconds`. Long sequences hold better when built as a chain of 2.5–4s beats than as one unbroken take.

**Slow-motion accents are carved out explicitly**, both where they land and in the closing clause: `Brief slow motion on the impact only, 2.0–2.5s. All other footage real-time.`

If cuts must never land mid-word: `the cuts fall between words and never inside a word.`

---

## SLOT 2 — STYLE PREFIX

The invariant capture stack. Labelled lines, front-loaded, never restated later.

```
Style: 8K, photorealism, real organic film grain and halation, high dynamic range, shot on large-format film. NOT a 3D render, NOT a game engine, NOT a game-cutscene aesthetic, NOT a cartoon, NOT anime cel-shading.

Operating style: large-scale realism with intimate handheld closeness, immersive in-camera feel, tactile textures, shallow depth of field on the face, documentary framing, photochemical look.

Texture: matte non-reflective surfaces, lived-in worn materials, organic 65mm film grain, no digital gloss, no plastic sheen.

Skin: pore-level realism — visible pores, fine vellus hair, natural asymmetry, no smoothing, no retouching. Half the face often falls into shadow.

Technical: 8K, real-time 24fps, true 180-degree shutter with a real 1/48 second exposure on every frame, genuine photographic motion blur, each frame blending smoothly into the next. Smooth stable motion, no flicker, no warping, no morphing, no frame interpolation, no frame blending, no ghosting, no double-imaging, no high-shutter video crispness.
```

**The render quad is mandatory and always four items:** `NOT a 3D render, NOT a game engine, NOT a game-cutscene aesthetic, NOT a cartoon.` Add `NOT anime cel-shading` when the material is stylized enough to invite it.

**The cadence clause lives in Technical and nowhere else.** It is the single most important anti-artifact instruction in the prompt, which is why the Style Prefix sits second.

**Strobe quarantine.** When the scene contains strobe or hard flashing light, append to Technical:

```
The stepped, stuttering quality of this sequence comes entirely from the strobe lighting described below — from bodies revealed only in discrete flashes — and never from broken or choppy footage. The camera motion between flashes stays continuous and smooth even while bodies appear to jump between positions.
```

Without the quarantine the model returns genuinely broken footage.

**Named-DP shorthand is permitted and efficient.** `Operating style — HOYTE VAN HOYTEMA:` carries large-format realism, intimate handheld, in-camera feel, atmospheric depth and photochemical rendition in three words. Use a DP whose signature actually matches the scene; never stack two.

---

## SLOT 3 — NO ON-SCREEN TEXT

Mandatory in every prompt, always in this position. Overlay text is generated early in the frame, so the instruction sits early.

```
NO ON-SCREEN TEXT — CRITICAL: no on-screen text of any kind anywhere in frame at any point. No captions, no subtitles, no burned-in dialogue, no auto-captions, no karaoke text, no lower thirds, no titles, no title cards, no credits, no watermarks, no logos, no timecode, no UI overlays, no social-media overlays, no interface elements, no Chinese characters, no Korean characters. The frame is clean of all overlay graphics from first frame to last.
```

**Never carve out in-world text inside this block.** No "other than," no "except for." An exception clause reopens the door and captions return. Physical text that genuinely exists in the scene — garment prints, packaging, signage, a split-flap board — is described separately in Assets or Geometry Map as a physical object with shape, colour, placement and legibility.

Weight it hardest on phone, selfie and talking-head prompts, which pull captions straight from social training data.

---

## SLOT 4 — CRITICAL BLOCKS

Any element the model routinely drops, softens or gets wrong is promoted out of the descriptive body into its own ALL-CAPS named block here.

Format: `THE [THING] — CRITICAL:` followed by one exhaustive paragraph.

| Block | Use when |
|---|---|
| `THE SINGING` | any lipsync — first block, top content priority |
| `THE MOUTH IS ALWAYS VISIBLE` | any lipsync, paired with the above |
| `THE GEOMETRY` | a spatial relationship must not invert (above/below, inside/outside) |
| `THE STAGING` | who stands where must not drift |
| `THE STROBE` / `THE LIGHT CHANGE` | flashing, pulsing, or lighting that shifts mid-take |
| `TWO DISTINCT DESIGNS` | two similar objects or characters that must never merge |
| `NOBODY ELSE IS IN THE FRAME` | any scene that must be empty of extras |
| `EVERYONE IS LIVE` | dialogue or group scenes where backgrounded bodies freeze |
| `THE TONE` | comedic or emotionally specific scenes that could be misread |
| `THE LANGUAGE` | foreign-language dialogue |
| `THE BEAT` | the dramatic point of the shot is a specific reversal |

**Cap at four.** Past that they compete and all of them dilute. Order by importance — early text carries more weight.

Each block is exhaustive within itself. Never split one idea across two. **The block is the instruction; downstream slots only apply it.** Never restate a CRITICAL block in full further down.

---

## SLOT 5 — ASSETS

Every asset is one line: **tag, permanent identity, THIS SCENE action, fidelity assertion.** This merges what used to be a separate identity lock and per-shot action line into a single non-repeating unit.

```
@Image 3 = 177cm, dark bob with blonde balayage ends, centre part, warm fair skin. Navy short-sleeve polo, grey micro-shorts, olive suede wide belt, barefoot. Clean clear face, no beauty marks, no facial markings. Voice strict and focused, mezzo-soprano. THIS SCENE: seated centre of the sofa, speaking, irritation sliding into teasing surprise. 100% match to the reference.
```

**Target 60–110 words per character asset.** Tight enough that five assets don't swamp the prompt.

**Identity components, in order:** height in cm · build and skin · face and bone structure · hair colour, length, styling · permanent markers · makeup · clean-face negations · wardrobe head to toe, one clause per garment · jewellery and nails · voice descriptor · THIS SCENE · fidelity assertion.

**Wardrobe is restated every prompt but written economically.** One clause per garment: colour, fabric, cut, how it sits.

- ❌ *a long-sleeved charcoal-grey cropped top in soft washed matte jersey with a faded mineral-dyed finish, high round neckline, long slim sleeves fitted to the wrist, hem sitting just below the ribcage, the back left open*
- ✅ *a cropped charcoal washed-jersey long-sleeve, high round neck, open back, hem just under the ribcage*

**Permanent features are declared permanent** — `the blunt bangs are permanent and present in every frame`.

**State-conditional identity is declared with its state and its reason** — `no horns in this scene, omit them entirely for continuity, horns are battle-state only`. This prevents the model splitting the difference.

**Known-drift attributes get an inline anti-drift negation** — `BROWN eyes, never blue, never green`.

**Clean-face negations are explicit.** The model invents facial detail otherwise.

**Skin lock:** warm fair or as specified, `rendering true and natural, never cool-shifted, never pale porcelain, never tan`.

**Reference scoping.** State what a reference governs and what it does not:

```
@Image 1 = the location — high-walled ruined city canyon, decayed grey towers, collapsed slabs, debris-littered ground. Controls geography, materials, atmosphere and light direction only.
```

**Group and crew assets** get one shared block: the full uniform, the permitted variation range (`some wear a sheer mesh layer, some have bare arms`), and the anonymity lock (`every masked face identical in styling, no dancer ever unmasked`).

**Prop assets** carry material, scale relative to a hand or body, hardware, finish, how it is held. Scale is the one that fails: `a 20cm combat knife, noticeably shorter than the mech's 40cm forearm — it reads short, not a sword`.

**Reference ordering:** characters first in narrative order, then group wardrobe sheet, then props, then environment plate, then video/audio last. Every character gets its own slot even if visible inside the environment plate — the plate carries world, the sheet carries identity. Renumber cleanly if a reference is added; never leave a stale index.

**The ordering is a rationing scheme, not just a reading order** — nine slots, so collapse anything that only needs to read approximately into a neighbouring Asset line rather than spending a slot on it. Keep the sequence fixed so the numbering stays predictable across a series of prompts.

---

## SLOT 6 — GEOMETRY MAP

Where everything sits in the frame and in depth. **This is the block that stops bodies drifting between cuts.**

```
GEOMETRY MAP: on the dark-green L-sofa — the woman with the black hair and brown eyes on the LEFT, the woman with the dark bob in the MIDDLE, the woman with the ashy-blonde shag on the RIGHT. A beanbag pouffe front-right, in front of the blonde. Windows and corkboard on the wall behind, thrown soft. Depth planes: sofa foreground, standing figure mid-ground, window wall background.
```

**Three things every geometry map states:**

1. **Absolute lateral position** — LEFT, MIDDLE, RIGHT, and what is off-frame in which direction
2. **Depth plane per subject** — foreground, mid-ground, background, and which planes are sharp and which fall soft
3. **Vertical relationship where it matters** — ABOVE, BELOW, inverted, suspended, and never let it invert

**Screen-relative and character-relative direction are always labelled.** `she turns to her OWN right` is not `screen-left`. Pick one per instruction and name it; unlabelled direction inverts about half the time.

**Naming who the frame favours resolves ambiguous framing** — `three-quarter angle, off-centre, favouring the woman in the middle`.

**A locked spatial relationship gets promoted to a CRITICAL block** — and defended in the negative-prompt field if the surface has one. Vertical inversions and above/below pairs are the most drift-prone geometry there is.

**Scatter over lines.** When several figures share a frame, place them at different depths rather than side by side: `scattered at different depths, NOT in a row`. Line-ups read as posed group photos.

---

## SLOT 7 — FIRST FRAME

One or two lines. What is already happening at frame one.

```
FIRST FRAME: already mid-sprint toward the first creature, blade in hand, the others spread around at different depths. No empty establishing frame, no static hold before the action starts.
```

The empty establishing frame is a default the model volunteers and it costs half a second of an eight-second clip. Kill it explicitly. When the reference image is the intended opening composition, say so: `open on the composition of @Image 1 exactly, already in motion`.

---

## SLOT 8 — OPTICS

**The house default is spherical large-format.** Clean glass — natural halation around highlights, creamy focus falloff, subtle lens breathing, natural 180-degree motion blur. **No anamorphic streak flares, no oval bokeh, no artificial flares, no fisheye** unless the user asks for anamorphic by name.

Anamorphic is opt-in per prompt. When requested, state it once here and let the closing Locks carry it.

### FOV degree anchor

The model latches onto **degrees** as a snap value; millimetres read as suggestion. Write the degree first, mm in parentheses. Never use an off-ladder value.

| FOV | mm | Feel | Use for |
|---|---|---|---|
| 180° | fisheye | spherical bulge | POV, dream state, hallucination |
| 107° | 14–16mm | architectural ultra-wide | vast interior scale, epic establishing |
| 84° | 20–24mm | classic wide | full-body blocking, immersive action, environmental establish |
| 63° | 28–35mm | reportage wide | observational, walking alongside, doc feel |
| 47° | 40–50mm | eye-level neutral | universal medium, two-shot, waist-up |
| 34° | 60–70mm | short tele | compressed group, stacked depth planes |
| 29° | 75–85mm | portrait compression | isolated bust, detail on hands, tight coverage |
| 18° | 100–135mm | portrait tight | identity-hold close-up, held emotional beat |
| 12° | 180–200mm | tele detail | hand insert, object close, jewellery, texture |
| 8° | 300–400mm | extreme long lens | anchored-far observation, watchtower |

### Lens lock per segment

```
LENS LOCK SHOT 1 = 84° (22mm) classic wide, low, the sprint immersive.
LENS LOCK SHOT 2 = 29° (80mm) short telephoto, detail on the hands.
LENS LOCK SHOT 3 = 47° (50mm) standard normal, side angle, the swing readable.
No focal drift mid-shot.
```

**Unusual FOVs need a defense battery.** A long lens will be averaged back toward a normal unless you name what it is not:

```
This is a LONG lens — strong telephoto compression, flattened perspective, background pulled in close and thrown soft, only one to three faces sharp at a time, tight crop. NOT wide-angle, NOT large-format coverage, no fisheye, no edge distortion, no deep focus, no full-room coverage.
```

Same in reverse for ultra-wide. **Extreme FOV across several beats drifts fastest** — declare the FOV at the top of every beat, repeat it in Locks, and hold one anchor reference across every beat.

---

## SLOT 9 — CAMERA

Pick one register and hold it. Register governs cant, cut rate, and how much of the frame is allowed to be still.

| Register | Cant | Cuts | Language | Frame |
|---|---|---|---|---|
| **Locked-off** | 0° | 1–2 shots or a oner | tripod-weighted, or an extremely slow push | long held frames, stillness is the subject |
| **Gentle handheld** | 3–10° | 3–5 shots, 2.5–4s | floating, drifting, riding breath, small organic corrections | frames settle and hold before moving on |
| **Heavy handheld** | 12–25° | 4–6 shots, 1.5–2.5s | jolting, bobbing, lurching, snapping corrections, high-frequency vibration underneath | every frame mid-move, the eye can still land |
| **Violent handheld** | 25–45° | 4–6 shots, 1.5–2s | punching in and ripping back, whip-pans, hard surges, violent corrections | nothing settles, the frame never lands |

**Deduce the register from the description; ask only if genuinely split.** Toward locked-off and gentle: grief, memory, waiting, ritual, solitude, portrait, dialogue that matters, "quiet," "still," "slow," "elegant." Toward heavy and violent: a beat drop, choreography, a chase, a fight, a crowd, a crash, a named BPM, "chaotic," "aggressive," "hard," "go crazy."

**Every register except locked-off closes with:**

```
never locked, never stabilized, never mechanically smooth, never gimbal-glide, never floaty drone — real shoulder-mounted mass, weight shifts, breath, human over-correction, every frame mid-move but always smooth and continuous in its own travel.
```

That last clause is load-bearing. Without it, violent handheld returns broken footage rather than energetic footage.

**Dutch cant is a swinging range in degrees** plus `never passing through level, never settling square`.

**Roaming coverage** — a camera that physically travels between subjects — is stated as an explicit behaviour with what it snaps to: `roams between them and zooms onto details, snapping to a singing mouth, a jumping pair of legs, flailing hands, a laughing face, then drifting to the next`.

**A Tier 1 subject inside a Tier 4 camera is a real choice** — a still figure while the camera tears around her. State the split explicitly so the model does not average the two.

---

## SLOT 10 — LIGHT & COLOUR

**Light is described by direction, quality and temperature. Never by fixture name.** No named lamps, no stock codes, no LogC4, no IRE.

```
LIGHT: motivated natural light, one soft key from camera-side and above, soft roll-off, faithful skin tones, no heavy grade. Cool daylight counter-note from the windows behind. Half-faces rolling through shadow as they move.
```

### The colour accent doctrine

Percentages, each nailed to a physical source. This allocates frame area, which a bare palette list does not.

```
COLOUR: ~70% desaturated green-grey room tone and raw concrete; ~20% warm orange-yellow accent from warm daylight and the warm ceiling wash through the netting; ~10% cool daylight blue as a counter-note from the windows.
```

Three bands, roughly 70 / 20 / 10. **Every band names its source.** A colour with no source in frame will not render.

State where blacks sit, what blooms, what flares specular, what holds saturation. Attach every colour to a fabric, a surface or a light source.

---

## SLOT 11 — ATMOSPHERE

**Air is always present. Vapor is always source-bound.**

Real air at real density, filling the entire frame including the foreground — a continuous scattering gradient from lens to horizon, blacks lifted at every depth, high micro-contrast inside the lift.

```
ATMOSPHERE: the air carries real density at every depth — a continuous scattering gradient from the lens to the far wall, blacks lifted at every plane, depth reading in clearly separated layers: [name the actual planes of this shot, nearest to furthest, and how each softens]. Razor skin and fabric texture up close, heavy grain inside the lifted shadows, natural bloom at point light sources. Low macro contrast, high micro contrast. Bodies pass through the air without disturbing it, leaving no wakes and no trails.
```

### The source rule

**Visible vapor shapes only exist when something in frame is physically making them.** Named source, named emission, and nothing anywhere else.

- ✅ *a lit cigarette in her left hand, a thin ribbon of smoke rising off the ember and dissipating within 30cm*
- ✅ *every footfall and impact blasts up dust that blooms and streams off in the wind*
- ✅ *breath condensing in the cold, visible on the exhale only*
- ✅ *steam lifting off the cup surface*

Without a source in frame, close the block:

```
No plumes, no banks, no tendrils, no wisps, no swirls, no rolling, no fog-machine texture, no smoke shapes, no volumetric shafts, no god rays. Nothing in the air is emitted by anything.
```

Naturally foggy exteriors are legitimate — cold morning fog, coastal haze, mist in a ruined city — and read as **uniform density and reduced visibility with distance**, not as shapes moving through frame. Write it as `thick cold fog holding at uniform density, visibility falling off with distance` and keep the shape negations.

**Clean-air scenes state it just as hard:** `the air is clean — no haze, no density, no visible beams, no suspended particulate, full clarity to the back wall`.

**Always name the actual depth planes of the actual shot.** Atmosphere is for depth separation, never for mood.

---

## SLOT 12 — ACTION TIMING

Timecoded beats. Hard cuts on their own line. Every visible body accounted for in every beat.

```
0.0–1.5s (SHOT 1, low charge-leap): sprints at 60 km/h toward the first creature and leaps, rising and driving down, blade in hand, dust torn up beneath.
1.5s HARD CUT
1.5–3.0s (SHOT 2, stomp): comes down and stomps one clawed foot onto the creature's head, crushing it into the ground — skull plate shattering, ichor bursting under the foot, rubble cratering, dust blasting up. Brief slow motion on the impact only, 2.0–2.5s.
3.0s HARD CUT
```

**Silence about a body means it drifts.** Every figure in frame gets an action in every beat, even if the action is small: `in the foreground she shifts and reacts, a small head turn, breathing, listening`.

**EVERYONE IS LIVE.** Backgrounded and foregrounded bodies freeze by default in dialogue scenes. State the counter explicitly: `nobody sits frozen, everyone is reacting throughout`.

**Each figure on her own clock.** For group energy: `each moves differently at her own random timing, deliberately messy, never moving as one`.

**Dialogue is written verbatim in quotes**, with the emotional arc and the physical beat tied to the stressed word:

```
speaks to the woman beside her, lightly teasing without malice: "We've got HER, though." — clear stress on HER — and ON THAT WORD she turns her gaze to her OWN RIGHT and looks and nods directly toward the figure off-camera to her right, a pointed "right there — her" beat.
```

**Synchronized choreography** needs the unison lock plus the anti-mannequin clause: `every dancer hits the same shape at the same moment while carrying her own micro-timing, head angle and limb height inside the count, so the group never reads as identical mannequins`.

**Name four motion layers, always**, even when one is "nothing else moves": character motion · micro-motion (breath, hair, fabric, jewellery) · environmental motion (water, particles, dust) · camera motion, which lives in slot 9.

**Hair and fabric as motion** is first-class on high-energy shots — hair whipping across faces and being pushed clear, fabric lifting and settling, chains swinging with real momentum. It reads as physical truth more than any body description.

---

## SLOT 13 — PHYSICS

True gravity. **The chain is always the same, scaled to the mass in play.**

```
1. Stated mass          — kg, tons, or bodyweight
2. Contact event        — foot lands, body hits, hand grips
3. Deformation          — the receiving surface gives: cushions compress, ground craters, fabric bunches
4. Rebound / recovery   — the surface returns, knees absorb, the body recovers
5. Secondary lag        — hair, loose fabric, cables, hydraulics trail the primary motion
6. Contact shadow       — where the body meets the surface, grounded
7. Closing negation     — nothing floats, nothing slides, nothing teleports
```

Bodyweight scale:

```
PHYSICS: real gravity, inertia and mass — weighted body movement, jumping with real impact and recovery, sofa cushions compressing and rebounding under the jumps, knees absorbing the landings, hair and loose fabric whipping with the motion, accurate contact shadows where feet meet floor and cushion. Nothing floats, nothing slides.
```

Heavy scale:

```
PHYSICS: real five-ton mass — the leap and stomp crush the head with crushing weight, cratering the ground; the swing carries weight into the carapace; the throw follows a true arc with the body's weight; kicks land with heavy follow-through. Hydraulic and cable elements lag the motion. Inside the cockpit the pilot's body and hair jolt with each strike. Bodies tumble with gravity, plates crack and splinter. Nothing floats, nothing teleports.
```

**Effort is physics.** Strain, exhaustion and struggle are rendered in the body, not asserted: `shaking arms, slipping grips, hands slip and catch, the body trembles, boots scrabbling for purchase, hard breathing`.

**Resistance is physics.** A thing that dies or yields does so over time: `it does not die instantly — it thrashes and resists, limbs clawing, before it finally goes limp`.

**Falling debris obeys gravity and is declared harmless** when it should be: `a scatter of pebbles and grit falls past her with real gravity; she is unharmed and keeps climbing`.

**Structures that must hold are declared to hold:** `the rig holds, no fall, no free fall, no snapping cable`.

---

## SLOT 14 — ACTING

```
ACTING: natural eye blinking throughout, active forehead and brow micro-expression, no frozen mask-face, no dead eyes. Forehead and eyebrow movement precisely matches the emotion of each line — brows up on the surprised peaks, scrunching down on the hard belts, foreheads alive throughout.
```

**Brow and forehead matched to the line is the single highest-yield acting instruction.** Faces go slack and generic without it.

**Eyelines are stated as targets** — `they look at each other, never into the lens`. Looking at camera is a strong default and must be suppressed explicitly in observational and documentary work.

**Emotional arcs inside a beat** are written as a slide, not a state: `first slightly irritated, then sliding into teasing surprise`.

**Physical performance negations** where relevant: no mouthed words, no singing, no teeth-baring, unless the scene calls for them.

---

## SLOT 15 — AUDIO

**Default: diegetic only.** Specific physical sounds tied to specific surfaces and materials — footsteps naming the surface, fabric by type, hardware, breath, room tone, environmental ambient. Close with `NO BGM — no background music, no lyrics, no score, no subtitles`.

### The NO BGM convention

**Write `NO BGM` — expanded once as "no background music" — rather than "no music".** The bare phrase "no music" reads as a weak stylistic preference and gets overridden by the model's strong prior that generated video wants a score under it. `NO BGM` is a production term and reads as a hard spec.

Expand it on first use in a prompt so the term is unambiguous, then let the abbreviation carry:

```
NO BGM — no background music of any kind. No score, no soundtrack, no instrumental, no underscore, no ambient musical pad, no drone, no tone bed, no swell, no sting, no humming, no singing, no whistling, no lyrics. Diegetic sound effects and room tone only. Nothing musical anywhere at any point.
```

**On a scene that must land silent, NO BGM is promoted to the header block**, alongside the shot count and the cut policy, not left to slot 15. Audio instructions carry more weight early, and by the time the model reaches the closing audio block it has already decided what the piece sounds like. Restate it in slot 15 as the closing clause.

**Name the specific musical forms it must not generate.** A bare negation leaves the model room to supply an "ambient texture" or a "tone bed" and consider the instruction honoured. The list above is the working set: score, soundtrack, instrumental, underscore, ambient pad, drone, tone bed, swell, sting, humming, singing, whistling, lyrics.

Never write song references, lyrics, or track-tied dialogue. Music is uploaded separately as an audio reference.

**Attached-track lock — HARD.** When an audio or video track is attached it is the sole and complete audio source:

```
AUDIO: the attached clip @Video 1 is the sole and complete audio source for this sequence. Generate no additional audio of any kind — no room tone, no foley, no ambience, no breath, no added dialogue, NO BGM.
```

The attached clip also owns all internal timing. Never impose per-beat timing on a lipsync take.

**The unheard-track technique** lets bodies sing with NO BGM in the mix:

```
AUDIO: NO BGM in the mix — no background music, the track is not audible. Only the voices, loud and a little off-key, singing roughly in time to the unheard 87 BPM beat: "[lyric]". Plus room tone, footfalls, sofa creak, laughter, fabric. No track, no instrumental.
```

**Spoken dialogue is allowed** when a scene has real speech. Line verbatim in quotes, plus delivery physics: mic distance, reverberation, compression, pitch level, accent.

**Non-verbal scenes** state it: `environmental sound and non-verbal effort sounds only — strained grips, hard breathing, an exertion grunt. No spoken words, no dialogue.`

**Slow-motion beats** get their own audio treatment: `slow-motion accents drop ambient under a low pressurized tone`.

---

## SLOT 16 — LOCKS

A positive ordered chain of what must hold. **Not a summary of the prompt** — only what could drift between cuts, phrased as what happens rather than what does not.

```
LOCKS: the sequence runs in order — sprint and leap, stomp the first creature's head into the ground, switch the blade from normal to reverse grip, side-swing kill of a second creature that struggles before dying, throw that body into another, kicks and a blade finish on the rest. Same identity, same blade, same geography and same creature design continuous across all cuts. It reads as genuinely heavy yet fast and brutal. Every shot a different angle and height. Wardrobe identical to each tagged reference, one look per figure, no mixing. Light direction and colour temperature identical across all shots. The air holds uniform density throughout.
```

Standard contents, one line each: **ordered action chain · identity continuity · staging and geometry holds · wardrobe identical to references · permanent markers restated as a short list · environment identical across shots · every shot a different angle and height · light and colour temperature consistent · atmosphere uniform · skin protection.**

**The no-restatement rule.** If a CRITICAL block already locked it, Locks does not repeat it — one clause pointing at it, not a rewrite.

**Skin protection closes the block:**

```
Skin reads true cinematic matte — zero shine on forehead, nose bridge, cheekbones and collarbones, real fine even pore texture, real peach fuzz at the jaw and hairline, real lip surface texture, light absorbed like true subsurface scattering, skin protected and rendering true and natural, never plastic, never doll-skin — no acne, no blemishes, no enlarged or rough pores, fine flattering texture that keeps every face looking good.
```

**The flattering ceiling is locked.** Realism never makes a face look ugly. Where matte-realism and flattering conflict, resolve toward flattering.

**Closing negation tail**, tuned to the scene:

```
No CGI, no rendered look, no digital cleanliness, no plastic surfaces, no AI smoothness, no skin smoothing, no glow, no stiffness, no frozen posing, no stabilized camera, no gimbal glide, no video-look high-shutter crispness, no frame interpolation, no frame blending, no dropped frames.
```

---

## THE LIPSYNC PROTOCOL

Lipsync fails for four diagnosable reasons: the lyric was stated abstractly instead of as a score; the mouth got obscured; too many cuts forced per-shot mouth re-initialization; other CRITICAL blocks out-competed the singing instruction.

**1. Promote the singing to the first CRITICAL block.**

```
THE SINGING IS THE PRIMARY SUBJECT — CRITICAL: every other element is secondary. [Description by hair and wardrobe] sings out loud, full voice, mouth open and working hard, for all [X] seconds without stopping. She is a singer delivering a vocal, not a performer mouthing along. Her mouth is the focus of every shot.
```

**2. Write the lyric verbatim, then the mouth mechanics word by word.** Bilabials — **B, M, P** — get maximum emphasis. A visible lip seal is what the eye reads as real lipsync.

```
"TIME" — the tongue taps up behind the teeth on the T, the mouth opens wide on a broad AH travelling into an EE, then BOTH LIPS PRESS FULLY AND VISIBLY TOGETHER AND SEAL SHUT on the M — a complete, unmistakable, hard lip closure with upper and lower lips meeting flat and pressing together, held a beat before releasing.
```

Non-bilabial words still get formation: where the tongue goes, how far the jaw opens, whether lips round or spread, whether teeth touch lip.

**3. State the closure count.** Scan the line for B, M, P — those are the hard seals. F and V are teeth-on-lip, described but not counted. Sustained final vowels are declared held open.

```
THE PATTERN OF CLOSURES: four hard lip seals across the sequence — on the M ending TIME, the M starting ME, the B starting BEEN, the B starting BEFORE — plus a smaller visible closure on the P of UP. Every one of the four is complete, fully visible and unmissable. The mouth is never lazily half-open and never mumbling between them.
```

**4. Lock mouth visibility in its own CRITICAL block.**

```
THE MOUTH IS ALWAYS VISIBLE AND ALWAYS READABLE — CRITICAL: her face is turned toward the lens, her mouth unobstructed, frontal and clearly readable in every single frame of every shot, and it stays readable through the camera movement, through the cant and through every flicker of the light. Nothing ever covers it — no hand, no hair, no arm, no other body.
```

**5. Hand timing to the clip and minimize cuts.** Prefer one continuous take. If cutting, cut between lyric lines or in breaths, never mid-word, and state it in the header.

**Strobe fights lipsync** — hard flash-to-black eats roughly half the closures. When both are wanted, flag it and soften the strobe on the singer only, a fast bright flicker that never drops her face fully to black, while background bodies keep the full treatment.

---

## STROBE GRAMMAR

```
THE STROBE IS THE DEFINING FEATURE — CRITICAL: the space is lit by hard white strobe flashes firing relentlessly on a fast [BPM] pulse. The rhythm is flash, black, flash, black — hard on, hard off, with occasional double and triple stutter runs. Each flash is instantaneous and brilliant, revealing the scene crisply frozen mid-motion, hard-edged and contrasty. Each black interval drops the frame to near-total darkness. No fade in, no fade out, every transition a hard snap. Because the bodies move continuously but are visible only during the flashes, every figure appears to jump between discrete frozen positions. Nothing sits at a comfortable normal exposure at any point.
```

Always pair with: a **secondary light** holding a dim constant glow between hits so forms stay readable in the black · the **cadence quarantine** in Style Prefix · a **continuous-motion clause**: `nothing is ever frozen, held or static between flashes — every body is in continuous motion at all times, it is only the light that stops them`.

**Per-beat light pulsing causes perceived choppiness.** On a report of choppy output, soften the pulse to a slow continuous swell first; if it persists, kill the pulse and go constant.

---

## HOUSE RULES

**No character names anywhere in the prompt body.** Visual descriptors only — hair colour and style, wardrobe, identity markers. Applies universally including staging, geometry and camera lines. Semantic reference tags may alias to a name in the numbered list above the code block, never inside it.

**No aspect ratio.** Set in the UI.

**No internal production context.** No "carried through from the previous scene," no "matching the earlier plate." Every prompt is standalone with everything restated fresh.

**No platform or tool names** in the prompt body.

**No meta-commentary.** Every word describes something visible or audible.

**Age-blind.** Describe by role, hair, wardrobe, identity markers.

**English only inside the code block.** No Simplified Chinese, no bilingual mode.

**Brand names, text and graphics are written verbatim** and described physically alongside — shape, colour, placement, legibility. Naming the thing renders the thing; a paraphrase renders a vague approximation.

**Lighting by direction, quality and temperature only.** Never a fixture name.

### Precedence — where these house rules disagree with quick mode

`SKILL.md` quick mode and this file take opposite positions on three things. Both work. **Never mix the two approaches inside one prompt** — pick the register and take its whole rule set.

| | Quick mode (`SKILL.md`) | Director v3 (this file) |
|---|---|---|
| **Brand-vibe anchors** — `ARRI ALEXA aesthetic`, `Kodak Portra 400`, `iPhone 15 Pro footage` | Allowed and encouraged; they pattern-match reliably and the official guide uses them | Banned. Write camera and stock **behaviour** instead — `shot on large-format film`, `real organic film grain and halation`, `wide-latitude cinema capture`. Named-DP shorthand in Style Prefix is the one permitted shortcut |
| **Aspect ratio in the prompt** | Stated (`Vertical 9:16`, `Total: 15s / 16:9`) | Never. Set in the UI |
| **Age words** | The official exemplars use them (`a man in his fifties`) | Age-blind — role, build, bearing, hair, wardrobe, identity markers only |
| **Technical capture numbers** — fps, shutter angle, exposure time | Banned. `SKILL.md`'s *Rhythm vocabulary* section lists `24fps`, `shutter 1/50`, `f/2.8`, `ISO 800` as specs that degrade output, and it is right: on a 60–120 word prompt a spec displaces direction | The Technical line in slot 2 is the **one exception**, and it is load-bearing. `real-time 24fps, true 180-degree shutter with a real 1/48 second exposure on every frame, genuine photographic motion blur, each frame blending smoothly into the next` is the cadence clause — the single strongest anti-artifact instruction in the prompt, and the reason the Style Prefix sits second. It is not a spec standing in for direction; it is the instruction that stops frame interpolation, ghosting and video-look crispness. **Aperture and ISO stay banned in both registers** — they buy nothing |
| **Negation volume** | Capped at 3 inline `avoid X` clauses, picked by actual risk. Ten avoid-clauses dilute each other and burn the word budget | Uncapped, because the negations here are **structural rather than defensive**: each one lives inside the slot that owns it and defines a boundary rather than patching a symptom — the render quad in slot 2, the text block in slot 3, the FOV defence battery in slot 8, the atmosphere shape negations in slot 11, the closing tail in slot 16. The quick-mode cap still applies to anything that would be a loose `avoid X` floating outside a slot |

Everything else — one primary action per beat, camera motion in its own clause, `no 3D, no cartoon, no VFX` on realism briefs, emotion as physiology, dialogue in `"double quotes"`, capture the seed and change one variable per re-roll — holds identically in both registers.

**Arriving here from director mode?** Two rules flip: `references/director-mode.md` states the aspect ratio inside Camera Capture and this file keeps it in the UI, and director mode's ten-block order is replaced wholesale rather than extended. Everything else in director mode — three-register atmosphere, moisture-without-shine, per-zone specular kill — is compatible and worth carrying across as slot 2 and slot 11 material.

---

## REFERENCE PLATE INTAKE — WHAT A GOOD @IMAGE LOOKS LIKE

Nine slots, and a bad plate poisons every frame it touches. The Assets block can only lock what the plate actually shows cleanly.

**The two axes, and why they get tangled.** A character plate needs **biological realism fully on** — pore texture, peach fuzz at the jaw and hairline, subsurface scattering, hair strand by strand with flyaways, real fabric weave and drape, real metal surface on jewellery. It needs **photographic capture behaviour fully off** — no key direction, no shadow side, no cast or contact shadow, no falloff on the background, no spill, no bokeh, no vignette, no flare, no haze. "Photorealistic" sounds like it means both. It doesn't, and asking for both is what ruins a reference.

**Why capture behaviour is the problem.** Any lighting baked into a plate — a cheek triangle, a nose shadow, a contact shadow under the feet, a warm bleed on the backdrop — is inherited and amplified by every generation that reads it, and it fights whatever Light & Colour the actual scene wants. The plate carries zero lighting. Slot 10 does all the lighting.

**The plate spec, in order of how often it fails:**

1. **Flat mid-gray field, not a photographed backdrop.** One uniform value at every pixel, no seam, no gradient, no hotspot, no vignette. No surface, no floor, no wall, no corner, no plane the figure stands on. Mid-gray rather than white or black because models amplify errors hardest at high-contrast edges — that is where halo, edge breathing and contour instability get baked in, and a plate on white hands all of that to the video model.
2. **Zero shadow and zero light bleed outside the subject.** No cast, contact, drop or occlusion shadow, no halo, no edge darkening, no glow or reflected colour thrown onto the field.
3. **Shadowless illumination on the subject** — matched fill on all four sides, no key-and-fill ratio, no rim, no hair light, no kicker. Form is described by bone structure, hair and fabric folds, not by light.
4. **True colour through the neutral ground.** The gray must not cool-shift the subject — skin at its true tone, wardrobe at its true colour, exactly as under neutral daylight.
5. **One subject per plate, one view per plate.** Never a composited multi-angle grid — the model renders the grid. Separate files per angle.
6. **Identity-pure wardrobe on the face plate** — a plain black camisole or ribbed tank, no jewellery, no logos, no graphics — so the plate reads as identity and nothing else, and every outfit build starts from neutral.
7. **Even sharpness edge to edge.** No depth-of-field falloff, no background blur, no lens distortion, no chromatic aberration, no atmospheric haze.

**Which slot a plate governs, stated in Assets.** A plate that carries identity should not also be asked to carry the environment. Scope it explicitly — `Controls geography, materials, atmosphere and light direction only` — and the plate stops leaking.

**Version the locks.** When a character's canonical plate is rebuilt — new hair colour, new cut, a new facial marking — both plates continue to exist and describe different states. Name them so the distinction survives (`lock-01`, `lock-02-red-hair`) and confirm which one is attached before writing Assets. A prompt built on the wrong lock reads as identity drift when it is actually a filing error.

**When the plates don't exist yet, don't force a text-only render.** That is where slop comes from. Route to `nano-banana-prompter` (or a character-plate skill if one is installed) to build identity-locked, one-subject-per-clean-frame plates first, then come back here and bind them in Assets.

---

## STORY BIBLE HANDOFF

When a story bible or canon skill is active, **it is the identity and context source and this file is the cinematography grammar.** The bible answers *who and what world*. This file answers *how it is shot*.

A reference image can show wardrobe, hair and bone structure. It cannot show voice, movement quality, stillness, which era's aesthetic applies, or which traits are locked forever. Those come from the bible, and they map onto specific slots:

| Bible field | Slot it feeds |
|---|---|
| Visual lock — permanent traits and their `never` clauses | 5 ASSETS, and the permanent-markers line in 16 LOCKS |
| Movement signature and combat style | 12 ACTION TIMING, 13 PHYSICS |
| Stillness register — what they do when not moving | 14 ACTING, and the per-beat small action that stops a body drifting |
| Speech pattern, register, cadence, signature phrases | 15 AUDIO — delivery physics and verbatim lines |
| Aesthetic era — palette, lighting quality, texture, grain | 2 STYLE PREFIX, 10 LIGHT & COLOUR |
| Ensemble dynamics — who leads, who watches, who fills silence | 6 GEOMETRY MAP, and the CRITICAL staging block when it must not drift |
| Production rules the user has hard-earned | Layer on top of House Rules, taking precedence where they conflict |

**Locks exclude as much as they include.** The most useful thing a bible carries is the wrong-answer clause. `warm fair skin` drifts; `warm fair skin, never pale porcelain, never tan` holds. When a bible states a trait without its negation, write the negation into Assets — this is the single highest-yield transfer from canon into a prompt.

**Never let bible material leak in as lore or backstory** — only as observable physical behaviour. A prompt that says "still carrying what happened in the tunnel" renders nothing. Operate standalone when no bible is present.

---

## PRE-DELIVERY PASS

- [ ] **Surface confirmed as 2.0** — if it runs 2.5, this is the wrong file
- [ ] Universal Reference Mode, not First/Last Frame Mode; ≤ 9 images, ≤ 3 video, ≤ 3 audio, **and ≤ 12 files in total** — the per-type caps sum to 15, so the total is the one that bites
- [ ] Bolded title with runtime, numbered reference list in attach order, one code block
- [ ] Header timings sum exactly, total ≤ 15s, speed policy stated
- [ ] Past ~10s, shot budget declared and anti-drift weight added (anchor ref, per-beat lens lock)
- [ ] Style Prefix second, render quad present, cadence clause inside Technical
- [ ] NO ON-SCREEN TEXT third, no carve-out clause inside it
- [ ] CRITICAL blocks capped at four, ordered by importance
- [ ] Every character has its own reference slot and its own Asset line with THIS SCENE
- [ ] Fidelity assertion on every asset, reference scoping on the environment plate
- [ ] Geometry Map states lateral position, depth planes, and vertical relationship
- [ ] Direction labelled screen-relative or character-relative
- [ ] First Frame kills the empty establishing hold
- [ ] Lens lock per shot in FOV degrees with mm, unusual FOVs defended
- [ ] Camera register consistent with cut rate and cant, never-settles clause present
- [ ] Colour doctrine in three bands, every band sourced
- [ ] Atmosphere names the actual depth planes; every visible vapor has a source in frame
- [ ] Physics runs the full chain at the right scale, closes with nothing floats
- [ ] Every visible body has an action in every beat
- [ ] Brow and forehead matched to the emotion, eyeline target stated
- [ ] Audio diegetic, or the attached-track sole-source lock
- [ ] Locks is an ordered positive chain, no restatement of CRITICAL blocks
- [ ] Skin protection and negation tail close the prompt
- [ ] No character names, no aspect ratio, no tool names, no mode label
- [ ] No brand-vibe anchors — camera and stock written as behaviour, not product names
- [ ] Every attached plate is flat-field with no baked lighting, one subject, one view, no composited grid
- [ ] The correct version of each character lock is attached, confirmed by name
- [ ] Where a bible is active: every locked trait carries its `never` clause, and no lore leaked in as backstory
- [ ] Nothing stated twice anywhere

**Repair pass:**

| Symptom | Fix |
|---|---|
| Wardrobe drifting | restate every garment in the Asset, not just the changed one |
| Choppy output | check the cadence clause sits in Style Prefix, then soften or kill any per-beat light pulse |
| Bodies drifting between cuts | tighten Geometry Map, add depth planes and a favours-line |
| Geometry inverting | promote it to a CRITICAL block; a Geometry Map mention alone is not enough |
| Air reading as fog machine | a vapor has no source in frame — bind it or cut it |
| Figures floating or sliding | the physics chain is missing deformation or contact shadow |
| Background bodies frozen | add EVERYONE IS LIVE and give each an action per beat |
| Lens averaging back to normal | add the not-the-other-thing defense battery |
| Lipsync closures missing | check mouth-visibility block, cut count, and whether strobe is eating the face |
| Extras appearing | add the population lock as its own CRITICAL block |
| Slow motion appearing unbidden | add the explicit no-speed-change line to the header |
| Captions appearing | the text block drifted down, or a carve-out crept into it |
| Long but vague | something is stated twice — find the duplicate and delete the later copy |
| Over the runtime ceiling or overloaded | split into two prompts by camera or by beat |
| References silently dropped | count exceeds 9 images / 3 video / 3 audio, or the render is in First/Last Frame Mode, which accepts no other references |
| Faces averaging or blending | two references are teaching the same thing — cut one |
| Long take compressing into the first third | declare the shot budget in the header, rebuild as 2.5–4s beats |
| Identity drifting late in a long take (12–15s) | add an anchor reference named in every beat, repeat the lens lock per beat |
| A plate's own lighting showing up in the render | the plate has capture behaviour baked in — rebuild it flat, or scope it in Assets to construction only |
| The reference's background bleeding into the scene | scope the plate explicitly, or swap in a clean-field version |
| A multi-angle grid rendering as a grid | a composited reference was attached — split it into one file per angle |
| Identity "drifting" between two prompts that both look right | the wrong version of the character lock was attached — check the plate name |


<!-- ═══════ FILE: seedance-2-prompter/references/edm-dance-and-movement.md ═══════ -->

# EDM dance and movement — a research reference for dance prompts

> **What this file is.** A movement reference for any brief involving people dancing to electronic music — club, warehouse, festival, music video, UGC hook, fashion film. It carries what the styles actually *do* mechanically, where the weight lands against the tempo, what makes movement read as real, and the documented tells of fake movement.
>
> **Read it when the deliverable contains dancing.** It is not a prompt grammar — `SKILL.md` and the director registers own that. This file supplies the *content* of the movement description that goes into those slots.

## How this binds into the Seedance 2.0 grammar

| This file gives you | It goes here |
|---|---|
| BPM and which pulse the weight sits on | The action sentence in quick mode; **slot 12 ACTION TIMING** in `references/director-v3.md` |
| The joint sequence and initiating joint | Same — and it is the one thing that must not be paraphrased |
| Track-junction responses (breakdown, build, gap, drop) | Timecoded beats — this table is the most directly convertible section in the file |
| Floor contact, deformation, recovery, secondary lag | **Slot 13 PHYSICS** in director v3; the realism clause in quick mode |
| Gaze targets, breath, accumulating exertion | **Slot 14 ACTING** |
| Crowd density and setting constraints | **Slot 6 GEOMETRY MAP** — density decides whether travel is even possible |
| The fake-movement negations | ≤3 inline `avoid X` clauses in quick mode; the slot-owned negations in director v3 |
| Unison-versus-individuation for groups | **Slot 12**, with the anti-mannequin clause |

**Three Seedance 2.0 constraints that shape every dance prompt:**

**The "fast" rule bites hardest here.** Fast camera plus fast cuts plus a busy scene is a guaranteed artefact, and a dancefloor is already a busy scene at a high BPM. **Make exactly one element fast.** Either the subject moves fast, or the camera does, or the cuts do — never two. A 174 BPM drum-and-bass floor with violent handheld and 1.5-second cuts will render as noise.

**Pick the camera register from the music, then hold it.** The register table in `SKILL.md` maps directly onto track structure: locked-off or gentle handheld for a breakdown or a minimal techno floor; heavy or violent handheld for a beat drop, choreography or a crowd. A still dancer inside a violent camera is a legitimate and striking choice — but it has to be stated explicitly or the model averages the two.

**Audio: use the unheard-track technique.** Bodies can dance in perfect time to music that isn't in the mix. `NO BGM in the mix — the track is not audible. Bodies moving in time to an unheard 128 BPM four-on-the-floor` gives you a beat-locked performance with a clean audio bed you can score in post — which is almost always what a music-video or ad deliverable actually needs. Full convention in `SKILL.md` under *The NO BGM convention*.

**Size discipline still applies.** A 4–8 second dance clip is Tier 1: 60–120 words, one flowing action sentence. Do not paste a joint sequence, a track-junction table and six authenticity clauses into a 5-second hook. **Pick the two or three mechanics that define the movement and spend the words there.** The long-form material in this file is for Tier 3 and Tier 3+ multi-shot work.

---

## RULE ZERO — "DANCING" IS NOT A DESCRIPTION

The single empirical finding that should govern every dance prompt: **generative video models produce convincingly human-like generic movement without the specific dance vocabulary.** The Markup / CalMatters tested 36 clips across four models (Sora 2, Veo 3.1, Kling 2.5, Hailuo 2.3) over nine dance styles in January 2026. **None of the 36 produced the dance that was asked for.** One returned no dancing at all. 31% showed structural failure — clothing and hair changing mid-shot, heads rotating on an axis separate from the body, limbs liquefying and reconstituting. A choreographer called one output "staggeringly lifelike" while noting it did not contain the requested movement.

So the failure is not *bad motion*. It is **plausible motion, wrong dance** — and the fix is not more adjectives on "dancing." It is:

1. **Name the style, or name the mechanics.** `she dances to the drop` renders a generic sway. `deep squat, feet wider than hips, knees tracking out, glutes driving a fast bounce with the lower back held long` renders twerk mechanics.
2. **Name the tempo and where the weight lands on it.** The model has no idea whether it is rendering 113 BPM or 174 BPM unless you say so, and the weight timing is completely different.
3. **Name the initiating joint and the sequence.** Almost every style is identifiable by *what moves first*. A movement in which everything initiates at once has no style — that is precisely what a model defaults to.
4. **Name the floor contact.** Weightlessness is the headline tell. Every accent needs a load path to the ground or to another body.
5. **Ask for less, in more detail.** One correctly-specified groove for four seconds beats a named-style medley that renders as four seconds of nothing in particular.

**Do not ask for a named social dance and expect the model to know it.** Break it into the mechanics below and prompt those. A style name is useful as an *anchor next to* the mechanics, never instead of them.

---

## TEMPO — PUT THE BPM IN THE PROMPT

Measured medians across 440,000+ tracks (Mixgraph, half-time corrected) unless noted. **The BPM figure changes the whole render** — cadence, weight frequency, how much the hair travels, whether the body reads grounded or airborne.

| Genre | Range | Median | Felt pulse if different |
|---|---|---|---|
| Amapiano | 108–115 | 113 | split — kick at 113, log drum syncopated against it |
| Deep house | 118–125 | 124 | |
| Afro house | 118–126 | 122 | |
| House | 120–128 | 125 | |
| Progressive house | 122–130 | 123 | |
| Cutting-shapes house (future / bass / tech) | 122–129 | — | |
| Tech house | 122–130 | 126 | |
| Minimal techno | 124–130 | 127 | |
| Techno | 130–140 | 133 | |
| Trance | 130–145 | 138 | |
| Dubstep | 138–142 | — | **~70 felt** (half-time) |
| Hands-up | 138–155 | — | off-beat bass against the kick |
| Psytrance | 138–148 | 142 | |
| Jumpstyle | 140–150 | — | |
| Hard techno | 140–160 | 146 | |
| Hardstyle | 148–155 | 155 | off-beat bass against the kick |
| Detroit jit | ~150 | — | |
| Chicago footwork | **160, fixed** | — | **~80 felt** — feet at 160, body at 80 |
| Hardcore / gabber | 160–200 | — | hakken "easily reaches 190" |
| Jungle | 160–180 | 172 | ~86 felt (half-time bass) |
| Drum & bass | 170–180 | 174 | **~87 felt** |

Two dataset inconsistencies to know about: dubstep's listed median (145) sits above its own range, and gabber's (155) below its floor — both look like half-time-correction artefacts. Use the ranges. Practitioner figures — dubstep 140, gabber 180–200 — are safer.

**Hard techno has been getting faster on a documented curve:** 130–135 before 2020, 140–145 standard by 2020–21, 145 described as the floor by 2023 with DJs pushing past 160 (Mixmag). If a brief says "hard techno," ask which era it means, because 133 and 158 are different films.

---

## WHERE THE WEIGHT LANDS — THE FOUR RHYTHMIC FAMILIES

This is the highest-leverage paragraph in the file. Get it wrong and the dancer is technically moving and musically nowhere.

**Four-on-the-floor — house, techno, trance, hardstyle, hard techno, afro house.** Kick on every quarter. **The weight drops *with* the kick** — knee flexion and foot contact coincide with the kick transient, and the rebound happens between kicks. This is why house and afro-house bounce read as a *down* bounce: the accent is the descent, not the rise. Prompt it that way. Off-beat elements — the open hi-hat on the eighths, the off-beat bass in hardstyle and hands-up — get taken by a **different body part**, usually hips, shoulders or arms, and that split is what produces the visible polyrhythm between lower and upper body. The practitioner formulation: internalise the 4/4 with feet and hips, then track the track's other textures with arms and fingers.

**Breakbeat — jungle, drum & bass, footwork, breaks.** There is no steady kick to fall onto. Dancers lock the **weight** to the half-time bassline or the snare backbeat — roughly 87 at 174 — and let the **feet** articulate the break's syncopations at two or four times that. Chasing the snare rolls is the documented amateur failure: "you can't dance to 180 BPM without looking like you are getting electrocuted." A prompt that says `dancing fast to 174 BPM drum and bass` will render exactly that electrocution. Say `weight settling on a slow ~87 pulse while the feet subdivide against it`.

**Half-time — dubstep, riddim, footwork's sparse mode.** Grid at 140, snare at a broad midpoint of the bar rather than on 2 and 4, so the felt pulse is around 70. **The body drops on that slow accent** — which is why dubstep headbanging is heavy and slow, not fast. The 140-grid hats, ghost notes and bass modulation get answered by faster, smaller articulations in the hands, head and ribcage layered over the slow weight. Chicago footwork inverts the same trick: the bass drum is used sparingly against a 160 grid, producing a half-tempo effect, so the **feet run at 160 while the body sits at 80.**

**Amapiano's split pulse.** ~113 BPM four-on-the-floor kick plus a syncopated log drum. Two simultaneously danceable pulses: heavy and on-beat, taken by heels and knees; springy and off-beat, taken by hips and ribcage. That is exactly why amapiano movement reads as grounded and floaty at the same time, and it is prompt-able as two clauses. Uncle Waffles on the log drum: it "imitates the heartbeat."

**Half-timing and double-timing the same track** is the strongest single authenticity signal available. A track offers a metric hierarchy — bar, beat, eighth, sixteenth, triplet — and a skilled dancer chooses which level carries the weight and which gets decorated, then **switches levels at phrase boundaries**: eight bars on the beat, then eight bars half-timed with double-time hands. The Caribbean wining lexicon names it outright — *slow wine* is defined as "a wine to a slow song, **or on every other beat**."

---

## TRACK ARCHITECTURE → BODY, JUNCTION BY JUNCTION

EDM arrangement is deliberately predictable, in 8, 16 and 32-bar sections: **intro → main/groove → breakdown → build → drop → second drop → outro.** Because it's predictable, the body's response is predictable too, which makes this table directly convertible into timecoded beats.

The build's mechanics are empirically documented. Solberg's *Dancecult* study ("Waiting for the Bass to Drop," 2014) measured heart rate and galvanic skin response against production technique and identified five that correlate with peak emotional response: **uplifters** (synths pitched progressively higher), the **drum-roll effect** (a snare pattern subdivided ever finer — quarter to eighth to sixteenth to thirty-second, creating a tempo illusion without changing BPM), **large frequency changes**, **bass removal and reintroduction** — the floor literally taken away and given back — and a **contrasting sparse breakdown** before the build. Solberg frames the whole thing as a gravity metaphor: the crowd anticipates that ascending tension must descend.

| Track event | What the body does |
|---|---|
| **Intro / DJ mix section** | Minimal commitment. Weight small and central, feet marking time, gaze often toward the booth. |
| **Main / groove section** | A settled loop. Movement becomes repetitive and economical — **this is where a real dancer's idiosyncrasies live**, and where a generated dancer looks most obviously generic. |
| **Breakdown** — bass and percussion stripped, sometimes near silence | Weight **rises**; the body decouples from the floor. Arms open, torso extends, eyes go up or close, hands sometimes to the head or hair. Travel and turning happen here because there is no kick to obey. **Critically: no vertical accent, because there is nothing to accent.** A body still bouncing through a breakdown has weight events with no cause — one of the loudest fake tells there is. |
| **Build / snare roll** | The subdividing snare pulls the articulation faster and faster while the **weight rises rather than drops**. Arms go up progressively. The crowd is loading. |
| **The gap — a bar of silence or a stripped bar before the drop** | A held, suspended shape. Breath in. Nothing moves, or one small held tremor. |
| **The drop** | Maximum weight release, timed to the returning low end. Knees flex, spine flexes forward, arms come down or punch out. In bass music this is the headbang; in hardstyle the stomp; in house a jack that finally lands. **The drop is the only moment where a whole crowd's weight synchronises.** |
| **Post-drop** | Individuation returns immediately. Half the floor half-times, half double-times. |
| **Bar 8 / 16 / 32 boundaries** | Dancers change **material**, not just accent — new step, new level, new direction of travel. Movement that ignores phrase boundaries reads as amateur or synthetic. |

**How to use this in a timecoded prompt.** Pick the junction, then write the body's response as physical fact rather than as energy. `0.0–2.0s (breakdown): weight rises, no vertical accent anywhere, arms opening overhead, chin lifting, eyes closing` then `2.0s the low end returns — knees fold, spine flexes forward, both arms drive down, weight lands hard on the flat of both feet`. That is a drop. `she gets more energetic` is not.

---

## THE STYLE CATALOGUE — WRITTEN AS MECHANICS

Use these as the body of the movement description. The style name goes in as an anchor beside them, never instead of them.

### Rave footwork — feet as the instrument

| Style | Tempo / genre | Prompt-ready mechanics |
|---|---|---|
| **Melbourne shuffle** | 125–150, hardstyle / hard trance | A **T-step** — heel-and-ball pivots that rock the body laterally and travel across the floor — fused with a **running man**. Feet shuffle inward and outward; arms move up-down or side-to-side on the beat. **Weight lives on the balls of the feet with the knees holding a constant slight bounce; that bounce is what produces the float.** Travels in patterns rather than holding place. Advanced: 360 spins, jumps, slides. |
| **Running man** (the engine) | 110–120 to learn, then faster | Two motions: stand with one knee lifted high, then jump and land with the legs in a triangle as the lifted leg drives forward and the planted leg slides back. Alternate legs. Ball-of-foot weight throughout. |
| **Cutting shapes / UK shuffle** | 122–129, future / deep / tech / bass house | **Heel-toe mechanics — scissors, twists, swivels** — with hopping and jumping transitions, primarily on the balls of the feet, and **dynamic weight shifts rather than planted steps.** Performed largely **in place**, unlike Melbourne's travel. |
| **Jumpstyle** | 140–150 | Energetic jumps, fast kicks, rotational footwork. **Relatively stiff upper body — nearly all the expression is in the legs.** |
| **Hakken (gabber)** | up to ~190, hardcore | Steps following each other rapidly on the bass drum, and critically **landing on the heel** (the name is Dutch for *heels*). Everything below the pelvis is the instrument; arms and torso are secondary, often a loose forward-leaning hunch. **Rendering hakken on the toes is wrong.** |
| **Hardstyle stomp / hands-up** | 148–155 | The genre is named for the gesture. Heavy vertical stamp marking the kick, arms punching or pumping on the **off-beat** bassline — the split is the whole look. |
| **Rebolation / free step** | psytrance, electro house | A heel-pivot walk: pivot on the back heel while the front foot turns inward around its own heel, sliding across the floor. Arms deliberately loose, reading as if the dancer lacks full directional control. Flat sneakers. |
| **Skanking (into jungle/DnB)** | DnB 170–180 | Original ska form: running-man legs plus alternating bent-elbow fist punches, left and right. **DnB skanking / x-stepping is a different animal** — fast technical foot crossing, deployed at drops. |
| **Chicago footwork** | **160 fixed** | Blindingly fast footwork stringing twists and turns together with seamless transitions, danced **in a battle circle**. Feet at 160 against a body sitting at 80. Foundational steps: Erk N Jerkz, the Ghost. |
| **Detroit jit** | ~150 | Rapid foot strikes **through the air rather than against the floor**; minimal upper body; explosive. Routines last about a minute before the body gives out — useful, because it licenses visible exhaustion. |

### Upper-body, prop and illusion styles

**Popping family** — Fresno, late 1960s–70s. **Popping is sudden tensing and releasing of muscles — "hitting" — arriving exactly on the transient.** Sub-styles are separable and worth naming precisely: *animation* (abrupt tensing producing a stop-motion, frame-by-frame illusion), *boogaloo* (loose fluid isolated circular rolls, "boneless"), *strobing* (quick stop-start), *ticking* (hits broken into small increments), *waving* (a fluid ocean-wave motion travelling through the body), *gliding / floating* (smooth footwork illusions), *tutting* (**right angles held at every joint** — wrist, elbow, shoulder — boxes built and re-broken).

**Liquid dancing and digits** — continuous unbroken fluid motion through arms, hands and body, sharing vocabulary with popping and waving: arm circles, wrist rolls, and "passes" where one hand appears to move the other. Digits is the same logic at finger scale.

**Gloving** — fingertip LEDs accentuating hand patterns, borrowing liquid, finger-tutting and popping wholesale. Delivered as a close-range "light show" to a single viewer. Note for framing: this is an intimate, one-to-one form, not a crowd-facing one.

**Flow arts / poi** — props orbit the body **in planes**. Longer poi hold a plane longer; shorter poi change planes easily; lighter poi move faster. The prop's own inertia is the whole read — a poi's plane persists because of the head's mass. *The full technical taxonomy (wall and wheel planes, in-spin and anti-spin, flowers, same-time and split-time) is community-standard but lives in video tutorials, not citable text — treat named figures as unverified.*

### House, club and ballroom lineages

**House dance** — NYC loft parties after Studio 54 closed, early 1980s, fusing ballet, tap, jazz, breaking, hip-hop, capoeira, Jamaican skanking and above all African dance; dancers themselves cite "the footwork, the movements of the torso, and the polyrhythms." Around 120–125 BPM. The named components:

- **The Jack** — Chicago-born, "a movement of the torso in an almost rippling effect": a contract-and-release wave through spine and chest riding the kick. **Chest leads, hips absorb.**
- **Footwork** — heel-toe steps borrowed from Jamaican skanking; travelling patterns, stomps, shuffles.
- **The Farmer** — bouncing vertically while stomping the foot.
- **Lofting** — floorwork emphasising fluidity, entered from and exited straight back into footwork and jacking. **In house, floorwork is a passage, not a destination.**
- **Skating, the Train, Loose Legs** — East Coast vocabulary. Baby powder for spins and slides, still used.

Regional split worth naming: Chicago and Detroit jack harder; East Coast is hip-hop-inflected; West Coast is b-boy-inflected.

**Waacking** — 1970s LA gay clubs, out of *punking*, danced to disco and post-disco often **sped up** to raise floor energy. Defined by **rotational arm movements around the shoulder joint, executed over the head** — a true humeral circumduction where the whole limb orbits and the elbow stays relatively fixed relative to the upper arm — plus sharp striking arm and hand movements synced to the music, resolving into exaggerated held poses. The speed is generated **proximally at the shoulder and expressed distally at the wrist**, which is why the hand appears to lag and snap. Over four-on-the-floor EDM this is an import rather than a native form: waackers ride the disco-derived pulse, hitting on 1 and 3 with the arm accents landing on the snare or clap. Tyrone "The Bone" Proctor: "if you don't understand the music, you will never understand the dance."

**Vogue** — Harlem ballroom culture, 1970s–80s. Five elements, and they are separable in a prompt:
- **Catwalk** — back arched, sitting into the hips, **walking on the balls of the feet**, hands used to compel the audience.
- **Duckwalk** — a bouncing shuffle in a deep squat, hands tapping the shoulders, back arched upright for balance.
- **Hand performance** — rapid windmilling arms. Leiomy Maldonado names **wrist mobility** as the priority.
- **Floor performance** — inventive rolls and leg work with seamless transitions to and from the ground.
- **Spins and dips** — a one-legged drop to the floor. **The term is *dip*, not "death drop"** (Maldonado); beginners build it from a grand plié.

**Techno's minimal register** — poorly documented in writing and worth flagging as observed convention rather than sourced fact, but real and consistent: near-static weight shift, eyes closed or downcast, a tiny sternum-led pulse, hands low. The one documented technique note describes an "Italian stomp" — hips swaying first, then feet stomping in patterns (left-right-left-right, then doubled or tripled: left-left-right, left-right-right) to build polyrhythm against a constant kick, with the upper body then decoupling into fist pumps, wrist flicks and snaky arms.

### African, Afro-diasporic and Caribbean grooves

**Amapiano** — Johannesburg and Pretoria townships, mid-2010s; the **log drum** is a wide electronic percussive bassline. ~113 BPM. Slick footwork, fluid body movement, coordinated group routines. Mechanically: heels and knees take the on-beat kick, hips and ribcage take the off-beat log drum. Uncle Waffles' own performance vocabulary — "grinds, twerks, pop-locks... head locking to the exact beat" — is a usable description in itself.

**Bacardi** — Pretoria, early 2000s: hypnotic body rolls, hip isolations, rhythmic sway, organic and improvisational, with dancers **mirroring the drum pattern** rather than executing set counts.

**Gwara gwara** — feet shoulder-width; **weight leans onto one foot while the other lifts slightly off the ground; the arms circle following the movement of the lifting knee**, with shoulder involvement for fluidity; pauses and arm variations for dynamics. The knee-drives-the-arm coupling is the identifying feature and is exactly the kind of thing a model will not invent.

**Azonto** (Accra, early 2010s) — knee bends and hip movement **miming everyday activities**; the miming layer is intrinsic, not decorative. **Shaku shaku** (Lagos) — exaggerated arm swings, crossed forearms, knees knocking inward. **Zanku / legwork** — a hop-and-kick where the working leg extends while the standing knee absorbs. **Vosho** — deep squat with kicking legs; *mechanics documented in video only, flagged.*

**Afro house** — 118–126, median 122. The register sits between house dance and amapiano: grounded, knee-driven bounce on the kick, tribal percussion picked up by shoulders and ribcage, arms often low and driving rather than raised. *Poorly documented mechanically — flagged.*

**Passinho** — Jacarezinho, Rio, 2007. A blur of light-speed footwork and body moves, described by practitioners as a patois of samba, freestyle and frevo: rapid low-to-ground foot patterns with fast weight exchange and torso counter-rotation. Battle culture from 2011.

**Twerking** — West and Central African antecedents (Ivorian *mapouka*) into the New Orleans **bounce** scene of the late 80s and early 90s; earliest recorded use of the word on DJ Jubilee's "Do the Jubilee All," 1993. Cognate forms with the same pelvic emphasis: Colombian *mapalé*, *batuque*, *candombe*. Full biomechanics below in the femme section. Big Freedia on bounce: "the more your butt is moving, the better," with lyrics kept simple to "leave room for the bass and the boom and the knock."

**Wining** — Trinidad Carnival and Jamaican dancehall, crossing into afro house and amapiano sets. The folk taxonomy is precise and prompt-usable: *wine up* (vigorous), *wine down* (wining while lowering the bottom toward the floor in a squat), *wine around* (circular, or circling while wining), *slow wine* (to a slow song, **or on every other beat**), *hard wine*, *rough wine*, *small wine*, *social wine* (restrained), *dollar wine* (thrust left, right, back, front in sequence), *walk and wine*, *wine back* (reciprocating).

**Dancehall named steps** — Bogle, Log On, Butterfly, Gully Creeper, Pon di River, Willy Bounce, Bruk It Dung, Gi Dem a Run (gliding while stationary), Genna Bounce, World Dance, Row the Boat. **Dutty Wine** is the extreme case: sustained rapid cervical rotation combined with winding, legs moving "like a bird," simultaneous rotation of wrists, neck and posterior. It carries a documented injury reputation — muscle trauma and ligament damage — which is worth knowing before writing it as a casual beat.

**Perreo / sandungueo** — Puerto Rico, late 1980s. Front-to-back pelvic motion with a continuous swivel of the hips and pelvis; **the legs work in a downward-and-upward pulse** directly comparable to the knee action of salsa and merengue. The partnered form has the front dancer bent forward, knees flexed, grinding back. **Solo perreo concentrates almost entirely on hip articulation.**

### Bass-music behaviours

**Dubstep headbanging** — head and torso hinge forward on the half-time backbeat. Because the felt pulse is ~70, **the neck flexion is slow and heavy, not fast** — this is the most commonly mis-rendered movement in the whole file. Knees bend on the accent; one arm often extended or "revving."

The **bass face** deserves a note, because it bears directly on authenticity. Spencer's academic treatment (Routledge, 2022) argues it is **not** a naive physiological reflex but a gesture "routed through its online depiction," shaped by dancers' awareness of how the moment circulates on social media. Useful two ways: it is a real and specific facial event worth prompting, and it is a reminder that even the most apparently involuntary club gesture is performed.

---

## FEMME MOVEMENT VOCABULARY — JOINT SEQUENCES

This is a technique section. The vocabulary below is the best-documented material available on hip, torso and spinal isolation, drawn from belly-dance (raqs sharqi) pedagogy, twerk biomechanics workshops, ballroom, heels-dance instruction and Afro-diasporic scene documentation. It transfers across bacardi, dancehall wining, perreo, afrobeats and heels work, because they share the same isolations.

**Why it matters for prompting:** these movements are defined by *what stays still*. An isolation is "the skill of moving one part of the body while keeping the rest still or minimising motion," and it requires body awareness, core engagement and controlled weight transfer. A model's default is whole-body motion, so **the held part has to be named explicitly or the isolation renders as a wobble.**

### Hip isolations

The most mechanically precise taxonomy available, with the knees, weight and feet spelled out per move:

| Move | Pelvis | Knees | Weight | Feet |
|---|---|---|---|---|
| **Hip lift** | one hip raises sharply upward | loose, bent | entirely on the opposite leg | grounded foot plants; **the lifting side's heel rises off the floor** |
| **Hip drop** | hip lifts slightly, then drops **below** neutral, heavily — "use your hip as a hammer" | bent on the dropping side | on the opposite leg | dropping side's heel raised first, then kicks forward |
| **Hip circle** | traces a horizontal circle on the ground plane | soft bend throughout | shifts continuously right → forward → left → back | both grounded; deepening the knee bend adds a vertical component |
| **Horizontal figure-8 (Turkish)** | draws a figure eight on the ground by shifting weight hip to hip | soft | alternates hip to hip | grounded |
| **Internal figure-8 (Egyptian)** | each hip traces a diagonal **downward** circle toward centre | bent on the weight-bearing side | shifts left↔right | grounded |
| **External figure-8 (Maya)** | each hip traces a diagonal **upward** circle away from centre | soft | alternates | heels can stay grounded |
| **Shimmy** | fast side-to-side hip pop | **one knee bends while the other straightens, rapidly alternating** | shifts to the bent-knee side | both grounded, no stepping |
| **Hip piston / pop** | one hip drives sharply sideways | loose; one bends, the other straightens | onto the straightened-leg side | both grounded |

**The instruction that separates a controlled isolation from a whole-body wobble:** the hip lift comes "mostly using your side abdominal muscles rather than the muscles of your leg." **Obliques, not quads.** Write it that way — `driven from the obliques with the ribcage held quiet` — and the render changes.

**The three distinctions worth keeping straight**, because they look similar and are mechanically different:
- **Pelvic tilt** is *sagittal* — anterior/posterior rotation of the pelvis around a left-right axis, driven by lower abdominals and glutes, spine flexing and extending at L4–L5. **No lateral travel.**
- **Hip sway / slide** is *lateral translation* — the pelvis moves sideways in space over the feet with the ribcage staying put. Requires an actual weight shift.
- **Hip circle** combines both in a continuous loop with continuous weight redistribution around the base of support. A **figure-8** is two circles of opposite handedness stitched together, and the direction of each half-circle — up-and-out versus down-and-in — is what distinguishes Maya from Egyptian.

### Twerk biomechanics

From dance-educator workshop material, which is far more precise than any general source:

- **Prime movers are the glutes.** They should drive the movement **rather than the lower back.**
- **The near-universal error is attempting it from the lower back**, which produces fatigue and lumbar strain. This is also exactly what a model renders by default — a mobile lumbar spine with quiet glutes — so **name the glutes and name the long spine.**
- Requirements: pelvic articulation and controlled tilt; hip stabilisers governing adduction and abduction; engaged pelvic floor; abdominal engagement for pelvic control; and **hip-flexor flexibility**, which is the actual limiting factor on the tilt.
- **Five separable techniques.** Prompt one, not all five: *tilt / pop-lock-and-drop* (needs flexible hip flexors plus abdominal engagement) · *contraction / booty bounce* (glute isolation with independent left/right control) · *femoral rotation / booty clap* — **leg-initiated, from external and internal rotation at the femur, not from the buttocks themselves** · *vibration / shake* (extreme muscular tension with rapid muscle firing) · *hip mobility* (overall range and fluidity).
- Standard stance: a low squat, feet wider than the hips, knees tracking outward, **spine long**, chest angled forward and often supported on the thighs or the floor at low levels.

### Body waves and body rolls — the sequence

A roll reads as real because it is a **successive** movement, not a simultaneous one: segments arrive in order with a small lag between each. If all segments move in phase it becomes a whole-body bob. The teaching instruction is blunt about it — "each individual part has its position and a stop," otherwise "you just look like you're just flopping around."

**Forward, descending, cervical-led:**
1. **Cervical flexion** — chin drops toward the sternum. Head leads.
2. **Upper-thoracic flexion** — sternum draws back, shoulders round forward.
3. **Mid and lower-thoracic flexion** — ribcage closes, the chest collapse.
4. **Lumbar flexion** — abdominals contract, navel draws to spine.
5. **Posterior pelvic tilt** — pubic bone lifts, tailbone tucks.
6. **Knee flexion absorbs** — the weight sinks. Then the chain **reverses in the same order** to unroll upward, which is what makes it continuous rather than a single sit-down.

**Reverse, ascending, pelvis-led:** anterior pelvic tilt → lumbar extension → thoracic extension, chest opening forward and up → cervical extension, **chin lifting last.** The head arriving last is the tell. Hair follows a further beat behind the head.

**Standing lateral wave:** the same chain rotated 90° — cervical side-bend → thoracic lateral flexion → lumbar lateral flexion → hip hike, sequenced so no two segments reach maximum simultaneously.

*The joint sequence above is a reconstruction from teaching material plus general spinal kinematics; no dance-science source describes it anatomically. Reliable, but not citable.*

### Torso, rib and shoulder isolation

- **Chest pop / pump** — *anterior translation* of the ribcage over a fixed pelvis: thoracic extension plus scapular retraction, sharply initiated and sharply arrested. **The pelvis must not travel**; if it does, the pop reads as a bounce.
- **Rib slide** — *lateral translation* of the ribcage over a stationary pelvis, from the obliques and quadratus lumborum. Distinct from a side-bend, which rotates rather than translates.
- **Shoulder isolation** — scapulothoracic motion only: elevation, depression, protraction, retraction, circumduction, with the ribcage held. A shoulder shimmy is rapid alternating protraction and retraction.
- In popping proper, all of these arrive as **hits** — sudden tense-and-release, the shape arriving and stopping on the transient.

### Arms and hands

- **Waacking arms** — rotation around the shoulder joint, over the head, with the speed generated proximally and expressed distally. Sharp strikes resolving into held poses.
- **Vogue hand performance** — rapid windmilling arms with wrist mobility as the priority; the hand appears to lag and snap because the drive is at the shoulder.
- **Wrist flicks** appear even in the casual techno register, alongside fist pumps and snaky arms.
- **Hands tracing the body, hand over hair** — the mechanism worth prompting is that the hand supplies **tactile contact and self-orientation**: it gives the movement a surface to work against and directs the viewer's eye along the body's line. *Observed convention, undocumented in writing.*
- **Arms driven by a lower-body event** is a distinctive and rarely-rendered pattern — gwara gwara's arms circle *following the lifting knee*. Worth naming explicitly when you want it.
- **Hands in the air** is what the hands-up genre is literally named for. And there is a documented, useful correlation: under a phone ban, a venue's director reports "there are arms in the air, rather than phones." **Phone presence and arm posture are causally linked** — a prompt that puts phones in the crowd should not also put arms overhead.

### Heels — the change that runs through the whole body

**This is the single highest-leverage mechanical variable in femme movement, and the axis on which the femme register genuinely differs from the shuffle and stomp register.** Frank Gatson Jr.: "when a woman puts on heels, she acts different, she stands different **because she has to hold on, she has to pull up**."

Mechanically, what heels do:
- The ankle is held in **plantarflexion**, so the shock-absorbing dorsiflexion range is gone.
- The base of support shrinks to the forefoot plus a small heel tip, so **balance is managed by the pelvis and ribcage rather than by the ankle.**
- The centre of mass moves forward, so the lumbar curve deepens and the pelvis tips anteriorly — which is why heels **automatically** produce the arched-back, hip-sat silhouette. Calves stay loaded continuously.

Consequences for the movement, all directly prompt-able: **travel gets shorter and more deliberate**; weight transfers happen with a distinct "set" onto the standing leg; heel-first strikes are replaced by toe-then-heel or forefoot-only contact; the **bevel** — working foot turned out and lifted onto its inside edge, ankles crossed — becomes a resting position. Teaching emphasis falls on strong lines and held poses, and on maintaining the exaggerated curvature of the body while standing on the heel's bevel.

**The asymmetry that makes this a render-quality issue:** barefoot or sneaker movement can be sloppy in the ankle and still read as good. **Heels cannot** — the ankle is fixed, so every error surfaces at the hip and ribcage. This is why heels dance looks more held and more posed than club freestyle even with identical vocabulary, and why a generated dancer wearing heels while dorsiflexing and heel-striking reads instantly wrong.

One notable pedagogy datum: a leading heels choreographer **teaches without counts** — "I learn choreography when I connect to the music based on what sound effect I'm hitting." That timbre-tracking rather than metre-tracking approach produces a recognisably different musicality, and it's promptable: `accents landing on the track's sound-design events rather than on the count`.

### Hair as movement

- **The whip sequence:** drop the **chin toward the chest** → hinge forward at the hips with the torso following → **snap the torso back** → bring the chin up off the chest → **the hair arrives last**, whipping toward the back. So: chin leads down, torso follows, torso reverses, chin lifts, hair trails.
- Hair volume matters less than the read: the effect comes from the head and spine action, not from the amount of hair.
- **Head roll** is a slow circumduction of the cervical spine — flexion, lateral flexion, extension, lateral flexion — typically over 2 or 4 beats, hair trailing a fraction behind throughout.
- **The eye detail that sells it.** Spotting — fixing the gaze on a point to control rotation and suppress dizziness — is the counter-technique to a whip, and the two are mutually exclusive. A whip **deliberately abandons the spot**, so the eyes lose focus for its duration and re-find it on the recovery. **That loss-and-recovery is a strong authenticity marker** and almost never appears in generated movement.
- *How hair whips read on camera is undocumented in the sources — treat framing choices as craft, not fact.*

### The two registers, side by side

| | Shuffle / stomp / hakken / jumpstyle | Femme club register — heels, dancehall, bacardi, perreo, heels-adjacent freestyle |
|---|---|---|
| **Primary articulator** | feet and ankles | pelvis and ribcage |
| **Upper body** | relatively stiff; arms are metronomes | fully articulate; ribcage and shoulders carry their own rhythmic line |
| **Foot contact** | ball of foot, high frequency, sliding | forefoot in heels, heel-planted in flats; low frequency, deliberate |
| **Vertical axis** | constant bounce oscillating with the kick | pelvis descends and rises through squat range — **levels** rather than bounce |
| **Travel** | travels in patterns, or holds place | small footprint, rotation on the spot, level change instead of travel |
| **Where the accent lands** | underfoot — the floor is the instrument | **inside the body** — an internal isolation, often with no floor event at all |
| **Sequencing** | simultaneous, whole-limb | **successive** — segments arrive in order with lag |
| **Endurance profile** | aerobic, sustained, high foot cadence | intermittent, with held shapes and recovery breaths between phrases |

**This is a mechanical distinction, not a gendered one.** Both registers appear on the same floor and often in the same body, and the shuffle scene is substantially female-led at the instructional and content level. Don't use the table to cast; use it to pick a movement vocabulary.

---

## THE AUTHENTICITY STACK — WHAT MAKES DANCE READ AS REAL

Every item here is a promptable clause. On a short clip, pick three or four that fit the movement; on a long take, more.

**Weight and gravity**

1. **Weight actually transfers.** Full transfer means the centre of gravity is vertically projected over the new support, freeing the other foot; partial transfer leaves it between two supports, as in a ball change. The teaching test is exact: **if the free foot can lift with no effort, the weight is genuinely on the other one.** A real dancer is continuously moving the centre of mass outside the base of support and re-establishing a new base, and the visible signature is a small, ceaseless negotiation at the ankles and hips — **no position is truly static.**
2. **Contact events are the loudest thing in the movement.** A heel strike sends impact up the skeleton, and the ribcage and hair register it **a beat later.**
3. **Recovery follows every big move.** Knees bend on landing to cushion and gradually arrest. No landing without absorption.

**Timing and sequencing**

4. **Anticipation exists** — a preparatory movement in the opposite direction before the main action: crouching before jumping, pulling back before a kick. In club terms, a beat or half-beat of counter-loading before every accent. **A movement with no preparation reads as teleported.**
5. **Overlapping action.** Secondary masses lag the central mass through momentum — hair, loose fabric, jewellery, sometimes head and arms trailing a few frames behind. In a body roll, adjacent spinal segments arrive in sequence, never in phase.
6. **Secondary action** is present and *voluntary* — a flick of the head, a wiggle of the fingers layered on the primary movement. Distinguishable from momentum-driven overlap because it is expressive rather than physical.
7. **Movement is either hitting or floating, and the dancer chooses.** Hitting arrives exactly on the transient; floating fills the space between transients with no arrival. Real dancers alternate deliberately, usually switching at 8- or 16-bar boundaries.
8. **Material changes at phrase boundaries**, not just accents — new step, new level, new direction at bar 8, 16, 32.
9. **Half-time and double-time switching** against a constant tempo.
10. **The build is answered by rising, not dropping.** Through a subdividing snare roll the articulation accelerates while the weight *rises*; the drop is the release. A body that keeps dropping through a build has no relationship to the arrangement.

**Contact**

11. **Floor contact is load-bearing and visibly so** — feet deform against the surface, heels compress, the sole flexes, slides have friction.
12. **Self-contact presses.** Hands land on hips, thighs, hair, shoulders — the vogue duckwalk literally taps the shoulders — and **pressure deforms flesh and clothing.** A hand hovering near the body is a tell.
13. **Other-dancer contact displaces.** Grinding, wining on someone, passing in a crowd — bodies move each other.
14. **Props obey their own inertia.** A poi's plane persists because of the head's mass.

**Gaze, breath, exertion**

15. **The eyes go somewhere specific, and it changes.** This is empirically grounded: a motion-capture silent-disco study (Bamford, Burger & Toiviainen, *Music & Science*, 2023) put 24 pairs in three conditions — same music, 5% tempo-shifted, quarter-beat phase-shifted — and found interaction quality rated significantly higher under synchrony (p<0.01) with **lower head divergence**, meaning participants looked at each other more. **Synchrony produces mutual gaze; desynchrony produces averted gaze.** Per-context: in breakdowns the eyes go up or close; in footwork down to the feet; in vogue and waacking out to the judge or audience, holding a pose's line; in a hair whip they lose focus and re-find it.
16. **Breath is phrase-linked** — inhale on the build or preparation, exhale on the accent, recovery breaths between phrases. *Inference from general dance pedagogy; no source on breath in club dancing specifically.*
17. **Exertion accumulates.** Jit routines last about a minute before the body gives out. Hakken at 190, footwork at 160, hard techno at 145–160+ — and Mixmag documents older ravers struggling with the tempo. Render it: sweat, reddened skin, heavier breathing, hair sticking to the neck, **phrases getting shorter late in a set.**
18. **Errors and recoveries.** Real floors contain near-losses of balance, adjustments, laughter, a step that doesn't land. A flawless take is a tell.

**Initiation order**

19. **One joint leads, and which one is consistent within a style.** Belly-dance hip work initiates at the obliques with the ribcage quiet — hips lead, torso passive. House jacking is a torso ripple, so the chest leads and the hips absorb. Gwara gwara has the knee leading and the arms following. Reverse body rolls are pelvis-led; forward rolls are head-led. **A movement where everything initiates at once has no style** — and that is the model's default.

---

## THE FAKE-MOVEMENT NEGATION LIST

Grounded in The Markup's 36-clip test across four models and corroborated by industry failure-mode documentation. Use these as targeted negations — **pick the two or three that match the actual risk of the shot**, and prefer the positive form from the authenticity stack first.

| Tell | Why it's wrong |
|---|---|
| Feet skim, slide or float without deforming against the floor | no load path to the ground; the weight is never on either foot |
| Movement starts from stillness at full speed | no anticipation, no counter-load before the accent |
| A big move ends abruptly with no absorption | missing follow-through |
| Every segment moves in phase — a whole-body bob instead of a roll | missing successive sequencing |
| Hair early, rigid, or moving independently of the head | hair is a trailing mass; it must lag the cervical action |
| Perfect bilateral symmetry; crowd members identical | real bodies are asymmetrical and real crowds stay individuated even when synchronised |
| The whole crowd accenting together for the entire track | **only the drop synchronises a real floor** |
| Accents landing on non-events, or on nothing | the movement isn't driven by the arrangement |
| No change of material at bar 8 / 16 / 32 | no phrase awareness |
| A body still bouncing through a breakdown that has no kick | weight events with no cause |
| Constant exertion with no accumulation — no sweat, no shortening phrases | physiology not modelled |
| Eyes generically unfocused, or locked to lens throughout | real gaze has targets and changes with synchrony state |
| No self-contact, or hands hovering without pressing | contact must deform |
| Joints past anatomical limits; head rotating on a separate axis; limbs liquefying and reconstituting | structural failure — 31% of the tested clips |
| Clothing, hair or limb structure changing mid-shot | temporal identity breakdown |
| Heels worn but the ankle behaving as if barefoot — dorsiflexing, heel-striking | heels lock plantarflexion; the compensation must appear at pelvis and ribcage |
| Deep-squat twerk with a mobile lower back and quiet glutes | inverts the prime movers — the documented beginner error, and the model's default |
| Running man executed flat-footed or with locked knees | requires ball-of-foot weight plus a knee bounce |
| Hakken performed on the toes | named for landing on the heel |
| Dubstep headbanging at full tempo | the felt pulse is ~70; the neck flexion is slow and heavy |
| "Club dancing" that is front-facing, waist-up, non-travelling and arm-led | **that is camera-native content choreography, not club dance** — see below |

---

## CONTENT DANCE IS NOT CLUB DANCE

The most common failure in generated "club dancing" is that it renders content choreography instead, and the divergence is documented rather than aesthetic. Vertical framing reshapes the movement itself: because the legs are usually out of frame, "there is almost less coordination involved," and the recurring vocabulary is arm- and hand-led — body rolls, hip and booty rolls, claps, arm rolls. The orientation differs in kind too: social dance is battle-facing or group-facing, while short-form dances are "designed for the sole purpose of posting," replacing co-present people with an imagined viewer and prioritising personality, facial expression and style over technical precision.

**Two different physical products:**

| | Camera-native content dance | Club dance |
|---|---|---|
| Facing | front, to lens | any direction; often away |
| Frame | waist-up | whole body |
| Travel | none | travels, or changes level |
| Symmetry | symmetrical | asymmetrical |
| Drive | arm-led | weight-led |
| Gaze | locked to lens | unfocused, or peer-directed |

Pick one deliberately and say which. A brief that wants "a girl dancing in a club" and gets a front-facing waist-up arm-led performance to camera has received content dance — and if that is actually what the brief wanted, prompt it as such and it will render much better.

---

## SETTING — CROWD DENSITY IS THE MASTER VARIABLE

And it is quantified, which makes it directly usable:

| Density | Movement available |
|---|---|
| **≤2 people/m²** — comfortable outdoor-festival holding capacity | attendees can dance and move slowly without constant body contact. **Travel possible, level change possible, arms extendable** |
| **3–4 people/m²** — unstable, shoulder to shoulder | **no travel.** Movement collapses to a vertical bounce, small hip motion, arms straight up. Crowd-crush risk rises sharply |
| **≥5 people/m²** — crush threshold | people lose the ability to move independently and the crowd behaves as a single mass. **Not dancing — involuntary swaying.** Compressive asphyxia risk |

| Setting | Physical constraints → movement register |
|---|---|
| **Club — small, low ceiling, dark, dense** | 2–4/m². Small footprint, no travel, movement in the vertical and sagittal planes only, arms low or straight up because lateral space is taken. **A low ceiling caps overhead extension and jumping.** Darkness reduces the payoff for shapes that read visually and increases the payoff for internal, felt movement — isolations, weight shifts, micro-timing. Eye contact is close-range. This is where the minimal techno register lives. |
| **Warehouse — large volume, hard reflective surfaces, low light** | Density varies wildly with distance from the sound system: dense at the front, near-empty at the edges. **The perimeter is where travelling styles happen** — shuffling, footwork, cutting shapes, flow arts, all of which need a radius. Concrete rewards slides and stomps and punishes knees; kneework needs pads. Boomy reverberant sound blurs transients and pushes dancers toward the kick rather than fine subdivisions. |
| **Festival mainstage** | Front rail is maximum density, 3–5/m² — arms up only, phones up, faces to stage. Mid-field around 2/m² allows actual dancing. **The edges and the grass are where shuffle circles and full-body dancing occur.** Daylight means movement is being seen, which biases toward legible outward camera-aware shapes. A stage invites travel; a crowd forbids it. |
| **Beach / outdoor day party** | **Sand destroys foot mechanics** — no slides, no pivots, no heel strikes, no shuffle. Weight sinks, so movement rises into the hips and torso. Barefoot returns ankle mobility. Heat shortens phrases. |
| **Afters — small flat, low volume, 6–20 people** | Density low but usable floor tiny, and furniture in the way. Movement is small, conversational, frequently stopping, lots of leaning and floor-sitting. Long duration, very low energy amplitude. |
| **Bedroom / studio — mirror, phone on a tripod** | Unlimited floor, no crowd, full travel and level change available, and a **fixed frontal camera** — which is the physical origin of the front-facing, waist-up, symmetrical, arm-led vocabulary. The mirror puts the gaze on self. Floorwork is possible because the floor is clean. |
| **Ballroom / battle circle** | Circular sightlines, judges or crowd on all sides, one performer at a time in the centre, spectators clapping and vocalising. Invites maximum extension, floor drops, dips, and travel along a runway line. Vogue, footwork, jit, passinho and waacking all assume this geometry — **rendering them in a dense crowd is a geometry error.** |
| **Filmed set with the crowd around the booth** | Cameras at head height in the crowd, audience behind and around the DJ. Produces hyper-aware performance dancing directed at both the DJ and the lens. |

---

## FLOORWORK AND LOW-LEVEL MOVEMENT

Floorwork is "using the floor as an extension of your body," and two named registers are worth distinguishing because they render differently: **strip plastic** — sensual and fluid, melting into the floor with smooth silky movement — and **frame up** — sharp and precise, strong deliberate movement and unique shapes, with more emphasis on musicality and rhythmic timing. Platform heels create distinctive shapes and lines while on the floor. Kneepads are standard equipment, which is a wardrobe detail worth getting right.

In **vogue**, floor performance is judged on seamless transitions to and from the ground plus inventive rolls and leg work. In **house**, lofting is entered from and exited straight back into footwork and jacking — **floorwork is a passage, not a destination**, and 1980s NYC loft parties already included it alongside partnering and baby powder for spins. So floorwork is native to house rather than an import from heels culture.

*Floorwork mechanics — how weight distributes across knee, shin, hip and forearm, how a knee loads and unloads, the specific descent and ascent pathways — are transmitted in studio and on video, and I could not find an authoritative written breakdown. Treat descriptions as craft.*

---

## SOURCES AND CONFIDENCE

**Where the evidence is strong.** The diasporic styles are richly documented by educators and scholars: house, vogue, waacking, dancehall, footwork, twerk, perreo, and belly-dance hip vocabulary. So is the arrangement-to-body relationship (Solberg 2014, empirical), synchrony and gaze (Bamford et al. 2023, motion capture), the bass face as mediated gesture (Spencer 2022), crowd-density thresholds (industry standards, quantified), and AI dance failure modes (The Markup / CalMatters, January 2026 — 36 clips, four models).

**Where it is weak, and flagged in place above.** Rave and club movement is badly under-documented academically — a York University thesis on raving concedes outright that "musical and performance analysis is totally absent" from existing rave scholarship. Specifically unverified: the Berlin minimal-movement register (real and widely observed, no citable documentation); DnB two-step and x-stepping mechanics (video only); vosho mechanics; poi's full plane and spin taxonomy; floorwork biomechanics; breath in club dancing; and how hair whips read on camera. The body-roll joint sequence in this file is a reconstruction from teaching material plus spinal kinematics, not a cited anatomical description.

**One terminology warning.** "Two-step" collides across UK garage (a music genre), country two-step, nightclub two-step, hip-hop two-step and DnB two-step. There is no authoritative single "EDM two-step." If a brief says it, ask which lineage — or specify the mechanics and skip the name.

**Key sources.** Solberg, "Waiting for the Bass to Drop," *Dancecult* 6(1) 2014 · Spencer, "Music to Vomit to," in *Cultural Approaches to Disgust and the Visceral*, Routledge 2022 · Bamford, Burger & Toiviainen, "Turning Heads on the Dance Floor," *Music & Science* 2023 · The Era Footwork Collective · ISTD on waacking and voguing · Dance Spirit on vogue fem (Leiomy Maldonado) · Dance Magazine on heels dance · 5 Magazine, "Spin, Slide and Jack: A History of House Dancing" · London Belly Dance on hip movements (the most mechanically precise source in the set) · Violet Flame Studios, Booty Bio-Mechanix · SF Conservatory of Dance on body isolation · STEEZY on popping and on hair whips · Caribbean Beat, "Wining Words" (Lisa Allen-Agostini) · NYU Latinx Project on perreo feminista · NPR on Chicago footwork and on bounce · Mixmag on BPM escalation · Vice on why short-form dances look alike · Dazed on phone-free clubs · Ticket Fairy on crowd-density calculation · Mixgraph EDM BPM chart · The Markup, "How we tested AI-generated dance videos."
---

## WORKED FRAGMENTS

### Tier 1 — a 5-second club hook (~95 words)

> *Vertical 9:16, 5 seconds, one continuous shot, gentle handheld at chest height. A woman with a dark bob dances alone in a low-ceilinged dark club at 124 BPM deep house — weight dropping with the kick onto the flat of both feet, knees soft, hips carrying a horizontal figure-8 driven from the obliques with the ribcage held quiet, shoulders loose above it. Small footprint, no travel, the crowd tight around her. Eyes half-closed, not on the lens. Sweat at the hairline, hair sticking to the neck. 35mm film look, natural imperfections, no 3D, no cartoon, no VFX. Avoid feet sliding without weight, avoid identity drift.*

Note what does the work: the BPM, "weight dropping *with* the kick," the named isolation with its driver muscle and its held part, the density implied by "small footprint, no travel," and one gaze target. No style name needed.

### Tier 1 — a breakdown beat (~70 words)

> *4 seconds, 16:9, locked-off medium on a woman in a warehouse as the track drops to a breakdown — bass and percussion gone. No vertical accent anywhere: the weight rises, the chest opens, both arms drift up and open, chin lifting last, eyes closing. Hair trails a beat behind the head. Hard reflective concrete, low light, haze from the smoke machine at the back wall only. Room tone and a distant unheard pulse, NO BGM. Avoid bouncing, avoid jitter.*

The single most valuable line here is **"no vertical accent anywhere"** — it kills the model's default bounce, which has no cause in a breakdown.

### Tier 3+ — a drop, in director v3 Action Timing

```
0.0–1.6s (SHOT 1, the gap): held suspended shape, one arm high, breath in, nothing else moving.
The crowd behind her also held, phones down, arms up.
1.6s HARD CUT
1.6–3.2s (SHOT 2, the drop): the low end returns — knees fold, spine flexes forward, both arms drive
down and out, weight lands hard on the flat of both feet, the floor taking it. Hair whips forward past
her face and is pushed clear. Behind her the whole crowd's weight lands on the same frame — the only
moment in the sequence where they synchronise.
3.2s HARD CUT
3.2–5.0s (SHOT 3, post-drop): individuation returns immediately — she half-times the weight while her
hands double-time, and no two figures behind her are on the same subdivision any more. Each moves at
her own random timing, deliberately messy, never as one.
```

---

## DANCE REPAIR TABLE

| Symptom | Fix |
|---|---|
| Generic swaying instead of the requested style | the style name was doing the work — replace it with the mechanics: initiating joint, sequence, weight timing |
| Feet sliding, floating, not deforming against the floor | the physics chain has no contact event or deformation link |
| Movement not on the beat, or on nothing | the BPM isn't in the prompt, or the pulse the weight sits on isn't named |
| Frantic, electrocuted-looking movement on a fast track | the weight was put on every event — name the half-time pulse and let the feet subdivide against it |
| Dubstep headbang at full tempo | the felt pulse is ~70, not 140 — say slow and heavy |
| Body bouncing through a breakdown | add `no vertical accent anywhere`, weight rises |
| Whole-body bob where a body roll was wanted | segments are in phase — write the joint sequence in order with the lag stated |
| Hair moving early, rigidly, or on its own | say it trails the head and arrives last |
| Crowd moving as one identical mass for the whole clip | only the drop synchronises — add per-figure random timing and the anti-mannequin clause |
| Twerk reading as a mobile lower back | name the glutes as the driver and the spine as long |
| Heels but the ankle heel-striking | state plantarflexion, forefoot contact, and the compensation at pelvis and ribcage |
| Everything initiates simultaneously — no style | name which joint leads |
| Movement never changes across the clip | material must change at phrase boundaries, not just accent |
| Reads as a TikTok performance instead of a club | front-facing, waist-up, arm-led, gaze-to-lens — decide which product you want and prompt it |
| Jitter and artefacts on a high-BPM floor | two or three elements are fast at once — make exactly one fast |
| Crowd travelling in a dense frame | density above 3/m² forbids travel; fix the geometry, not the movement |

---

## SEE ALSO

| For | Read |
|---|---|
| Prompt sizing, the 6-step formula, the camera registers, the NO BGM convention | `SKILL.md` |
| The M1–M5 cinematography modes, Sound Bed, Capture Realism | `references/director-mode.md` |
| Timecoded Action Timing, the physics chain, Geometry Map, Acting, the lipsync closure protocol for a singing performer | `references/director-v3.md` |
