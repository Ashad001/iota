# Image Core — Nano Banana grammar, realism, optics, framing

> **What this is.** nano-banana-prompter core craft. Stage 12 FIRST_FRAME starts here. Prompt grammar, the realism engine, lens/light/grain, framing and composition, in-image text, identity locking, edit routing.

> **Bundle of 20 source files, 319,970 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `nano-banana-prompter/SKILL.md` | 68,822 |
| 2 | `nano-banana-prompter/references/frameworks.md` | 4,429 |
| 3 | `nano-banana-prompter/references/structured_prompting.md` | 3,728 |
| 4 | `nano-banana-prompter/references/generation_mechanics.md` | 4,842 |
| 5 | `nano-banana-prompter/references/text_rendering.md` | 7,168 |
| 6 | `nano-banana-prompter/references/identity_lock_and_filmmaking.md` | 4,578 |
| 7 | `nano-banana-prompter/references/frame_realism_engine.md` | 32,492 |
| 8 | `nano-banana-prompter/references/realism_and_ugc.md` | 25,540 |
| 9 | `nano-banana-prompter/references/realism_physics_deep.md` | 9,690 |
| 10 | `nano-banana-prompter/references/optics_grain_and_light.md` | 18,117 |
| 11 | `nano-banana-prompter/references/lighting_craft_and_filmmaking_deep.md` | 12,362 |
| 12 | `nano-banana-prompter/references/perspective_and_lens_geometry.md` | 10,851 |
| 13 | `nano-banana-prompter/references/framing_scene_grammar_and_continuity.md` | 20,949 |
| 14 | `nano-banana-prompter/references/composition_posing_and_critique.md` | 10,685 |
| 15 | `nano-banana-prompter/references/photography_pro.md` | 3,797 |
| 16 | `nano-banana-prompter/references/creative_director_controls.md` | 8,822 |
| 17 | `nano-banana-prompter/references/worked_examples.md` | 4,877 |
| 18 | `nano-banana-prompter/references/field_findings.md` | 39,406 |
| 19 | `nano-banana-prompter/references/surgical_edits_and_higgsfield_routing.md` | 18,307 |
| 20 | `nano-banana-prompter/references/storyboard_to_seedance.md` | 10,508 |

---

<!-- ═══════ FILE: nano-banana-prompter/SKILL.md ═══════ -->

---
name: nano-banana-prompter
description: "Write Nano Banana prompts (Google Gemini Flash Image / Nano Banana, 2, Pro). IMAGE model, not video. Use for any Nano Banana or Gemini image: generation, edit/fusion/composition, style transfer, multi-image or character-consistent work, in-image typography, mockups, posters, logos, infographics, social posts. Covers photoreal/UGC/phone-shot 'doesn't look AI' briefs (anti-plastic skin, iPhone looks, identity-locking, native text rendering and localisation, multi-turn editing, lighting/lens/grade/material controls) and ethnicity-accurate casting for any heritage (skin-tone, hair-texture, traditional dress, UAE/GCC/Khaleeji, Arabic in-image text). ALSO the surgical-edit lane for ANY existing frame — 'change only the X', 'it changed too much', reverse-angle view changes, prop/product sheets — plus routing to Higgsfield Soul 2.0, AI Cast, Soul Cinema, Seedream 4.5, GPT Image 2. ALSO the image half of storyboard-to-video: 'storyboard then animate', 'shot-by-shot AI film' — frames here, motion in seedance-director."
---

# Nano Banana Prompt Builder

Nano Banana is Google's family of image generation and editing models in the Gemini stack. Three current generations are in active use:

- **Nano Banana** — `gemini-2.5-flash-image` (launched Aug 2025; legacy, 1K)
- **Nano Banana 2** — `gemini-3.1-flash-image` (GA June 2026; fast/cheap, ~$0.02–0.04/img, <2 s, 0.5K–4K) — **the default for iteration**
- **Nano Banana Pro** — `gemini-3-pro-image` (Vertex) / `gemini-3-pro-image-preview` (Gemini API) (top tier — Gemini 3 reasoning, real-time web search, 4K, premium typography, ~$0.134/img at 1K–2K and ~$0.24 at 4K, 2–5 s) — **the hero / text-heavy / final**

Model strings vary by surface — Vertex exposes `gemini-3-pro-image` / `gemini-3.1-flash-image` (GA, June 2026); the Gemini API may still carry a `-preview` suffix. Pricing and IDs shift, so **verify on `ai.google.dev/gemini-api/docs` and the Vertex model page** before relying on them — see `references/generation_mechanics.md`.

All three accept up to **14 reference images** in a single prompt and output text + image. From Nano Banana 2 onward, the model can pull **live data from web search** and render images grounded in real-time information. Outputs carry C2PA Content Credentials and a SynthID watermark. Aspect ratios include 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9 — plus 1:4, 4:1, 1:8, 8:1 on the Flash model (Nano Banana 2).

This skill captures how to write Nano Banana prompts that produce precise, controllable, photo-real output — and how to escape the traps that produce generic results.

---

## Avoiding generic AI frames (judgment, not a checklist)

If the natural framing for the brief is a straight eye-level shot, use it — don't force exotic angles, occlusions, or imperfections onto frames that don't want them. The goal is that nothing in the frame reads as a *default*: watch for the usual AI tells (the slightly-low centered hero hover, floating camera positions, every face at the same 3/4 turn, sourceless even light, spotless worlds, posed-at-lens subjects) and break them only when they'd make the frame generic. The operator-anchored angle grammar (`references/composition_posing_and_critique.md` section 4) and the real-frame override (`references/tonal_families.md`) are tools to reach for when realism matters — not mandatory ingredients.

Same judgment applies to prompt length: write the shortest prompt that fully specifies the brief. Simple subject → short prompt. Stack detail layers only when the brief calls for that control. A bloated prompt on a simple ask is its own failure mode.

## The core principle: describe scenes, not keyword piles

Nano Banana is built on Gemini's reasoning stack. It rewards **natural-language scene descriptions** and pushes back on keyword salads. The right mental model is *write a director's brief, not a search query*.

> **Wrong:** `business professional sidewalk rain morning urban determined fast`
>
> **Right:** *"A business professional in a navy raincoat strides briskly along a rain-slicked sidewalk at morning rush hour, holding a takeaway coffee and a leather portfolio, expression focused and slightly tense, the city behind her in soft focus."*

The second prompt is the same length but tells a *scene*. Nano Banana renders that scene faithfully. The first prompt makes the model guess.

---

## The five canonical frameworks

Google's own prompting guide organises Nano Banana use cases into five frameworks. Match your task to the right one.

### Framework 1 — Text-to-image generation (no references)

**Formula:**
```
[Subject] + [Action] + [Location / context] + [Composition] + [Style]
```

**Worked example:**
> *"A striking fashion model wearing a tailored brown dress, sleek boots, and holding a structured handbag. Posing with a confident, statuesque stance, slightly turned away from camera. A seamless deep cherry-red studio backdrop. Medium-full shot, centre-framed, head and lower legs touching the frame edges. Fashion-magazine editorial style, shot on medium-format analog film, pronounced grain, high saturation, cinematic lighting."*

Five clean clauses: subject · action · location · composition · style. Reproducible and editable.

### Framework 2 — Multimodal generation (with reference images)

**Formula:**
```
[Reference images] + [Relationship instruction] + [New scenario]
```

You upload reference images and tell the model how to combine them. Up to 14 references. Reference them inline — Nano Banana doesn't use Seedance's `Image 1 / Image 2` syntax; you say *"the napkin sketch I attached"* or *"the fabric sample"* in plain language and Nano Banana figures out which is which from context.

**Worked example:**
> *"Using the napkin sketch I attached as the chair's structural design and the fabric swatch as its upholstery texture, transform this into a high-fidelity 3D render of a finished armchair. Place it in a sun-drenched minimalist living room with white walls and a single tall potted fig tree."*

Three clean clauses: references named · relationship made explicit · new scenario described.

### Framework 3 — Conversational editing (no new references)

This is the multi-turn strength. After you generate an image, you can edit it by talking to Nano Banana — *"remove the man"*, *"make the sky overcast"*, *"add a stack of books on the table"*, *"keep everything else exactly the same"*.

**The critical phrase:** *"keep everything else exactly the same"*. Without it, the model sometimes re-renders adjacent regions unnecessarily.

**Worked example sequence:**
> Turn 1 (generation): *"A wide shot of a man and a woman sitting on a park bench in autumn, golden hour light, dappled shadows from the trees, Sony A7 IV aesthetic."*
>
> Turn 2 (edit): *"Remove the man from the photo. Keep everything else exactly the same — the woman, the bench, the lighting, the leaves on the ground."*
>
> Turn 3 (edit): *"Now the woman is wearing a red wool coat instead of black. Keep everything else exactly the same."*

This conversational style is Nano Banana's biggest differentiator vs. Midjourney / Imagen.

**When the edit matters, upgrade to the surgical block.** *"Keep everything else exactly the same"* is the one-line version. For anything precise — a hero frame, a client asset, an edit you've already had to redo once — use the structured CHANGE / PRESERVE EXACTLY / ONLY CHANGE template in `references/surgical_edits_and_higgsfield_routing.md`. Core law: **an edit is post-processing of the original, not a rebuild.** Minimal CHANGE, exhaustive PRESERVE, one change per pass, and every removal paired with what fills the gap (*"remove the lamppost — continuous brick wall behind"*). If the output drifted from the ask, you changed too much: lock more, change less. CAPS blocks belong in edit prompts ONLY — never in a generation prompt.

### Framework 4 — Style transfer + composition (with new references)

You bring a base image plus an additional reference (object, style, mood-board) into the same prompt and ask the model to merge them.

**Composition formula:** *"Add the [object from reference] to [the base image], placed [where], lit [how]."*

**Style transfer formula:** *"Recreate the exact content of [the base image] in the style of [reference style or named art movement]."*

**Worked examples:**
> *(base image: a portrait. reference: a Van Gogh painting.)*
> "Recreate the exact composition and subject of the portrait in the visual style of the Van Gogh reference — thick impasto brushstrokes, swirling background, saturated cobalt and yellow palette."

> *(base image: an empty office desk. reference: a sleek MacBook.)*
> "Add the MacBook from the reference to the centre-left of the desk in the base image, lid open at about 110 degrees, screen showing a subtle abstract wallpaper. Lighting and shadows should match the base image's existing key from the window on the right."

### Framework 5 — Real-time web-search-grounded generation (Nano Banana 2+)

Nano Banana 2 and Pro can pull live data from the web and visualise it.

**Formula:**
```
[Source / search request] + [Analytical task] + [Visual translation]
```

**Worked example:**
> *"Search for the current weather and date in San Francisco. Use this data to modify the scene — if it's raining, make it look overcast and rainy; if it's sunny, bright midday. Visualise the result as a tiny city-in-a-cup miniature embedded inside a modern smartphone UI mockup."*

This is unique to Nano Banana — no other major image model fetches live data inside a prompt.

---

## Best-practice principles (apply to every framework)

**Be specific.** Concrete details on subject, lighting, composition. *"A man in a coat"* is weak. *"A man in a charcoal wool overcoat with a velvet collar"* is strong.

**Use positive framing.** Describe what you want, not what you don't. *"An empty street"* beats *"a street with no cars"*. Negative framing exists but is far less reliable in Nano Banana than in diffusion-only models — with one carve-out: anti-retouching negatives (*"not airbrushed, no beauty filter, no smoothing"*) DO land. See `references/realism_and_ugc.md`.

**Control the camera.** Photographic and cinematic terms work — *low angle*, *aerial view*, *macro lens*, *shallow depth of field f/1.8*.

**Iterate conversationally.** Don't try to nail the perfect prompt in turn 1. Generate, then refine with follow-up edits.

**Start with a strong verb.** Open the prompt with what the model should do: *"Generate…"*, *"Compose…"*, *"Render…"*, *"Restyle…"*, *"Add…"*, *"Remove…"*. This tells the model the operation before the details.

---

## Native text rendering (Nano Banana's killer feature)

Nano Banana renders text inside images with quality that nothing else in the field currently matches. Multi-lingual, multiple fonts in one image, faithful kerning. Four rules:

### Rule 1 — Quote the actual text

Always wrap the literal text in quotes so the model knows what to render. Without quotes the model often paraphrases.

> *"Render a movie poster with the title 'GHOST PROTOCOL' in the centre."*

### Rule 2 — Name the typography

Describe the font style or name a recognisable font.

> *"…in a bold sans-serif font, Century Gothic style, white on black background."*

Recognisable named fonts that work: *Helvetica*, *Times New Roman*, *Century Gothic*, *Brush Script*, *Impact*, *Bodoni*, *Garamond*. Pair with weight (*bold*, *thin*, *condensed*) and texture (*matte*, *glossy*, *neon glow*, *letterpress*).

### Rule 3 — Translate and localise

Write the prompt in English, request the rendered text in another language.

> *"Render the headline 'NEW YORK' translated into Korean and Arabic, both centred below the English version."*

Nano Banana 2 / Pro support state-of-the-art rendering in 10+ languages including CJK and Arabic right-to-left.

### Rule 4 — Text-first conversational hack

For complex compositions with text, Google recommends a two-turn approach:

> Turn 1: *"Suggest three slogan options for a luxury watch ad targeting professionals 30-50."*
>
> Turn 2: *"Now render a magazine ad with the watch and slogan option 2 as a headline at the top, in a thin Bodoni Italic font."*

Letting the model think about the text first, then render, beats trying to do both in a single shot.

---

## "Prompt like a Creative Director" — four lift-the-result-from-good-to-great controls

When the output looks decent but unmemorable, the four levers are:

### 1. Design your lighting

| Lighting recipe | Use case |
|---|---|
| Three-point softbox setup | Product, beauty, corporate headshot |
| Chiaroscuro with harsh high contrast | Drama, mystery |
| Golden hour backlight creating long shadows | Lifestyle, fashion editorial |
| Single hard window key, deep shadows | Painterly, Vermeer-style portraits |
| Neon-lit, multiple colour sources | Cyberpunk, music video aesthetic |
| Candlelit close foreground only | Intimate, period drama |

### 2. Choose your camera, lens, and focus

Camera brands give the model visual DNA cues:

| Camera | Visual signature |
|---|---|
| GoPro | Distorted ultra-wide, action immersion |
| Fujifilm X-T5 | Authentic film-science colour, slight grain |
| Sony A7 IV | Clinical sharp digital |
| Disposable film camera | Raw flash, nostalgic, slight blur |
| Hasselblad medium format | Editorial elegance |
| iPhone 15 Pro | Modern phone aesthetic, slight HDR |
| Polaroid SX-70 | Square, soft, milky highlights |

Lens names also work: *24mm wide-angle*, *50mm portrait*, *85mm telephoto*, *100mm macro*, *f/1.8 shallow depth of field*, *f/16 deep focus*.

### 3. Define the color grading and film stock

| Phrase | Look |
|---|---|
| "As if shot on Kodak Portra 400" | Warm pastel skin tones, soft grain |
| "Cinematic colour grading with muted teal tones" | Modern moody |
| "As if shot on 1980s color film, slightly grainy" | Nostalgic warm with magenta tint |
| "Bleach-bypass processing" | Desaturated, high-contrast, gritty |
| "Velvia transparency film, hyper-saturated" | Travel photography classic |
| "Black and white silver gelatin print" | Documentary, archival |

### 4. Emphasise materiality and texture

Don't ask for "a suit jacket" — ask for *"navy blue tweed with subtle herringbone texture"*. Don't ask for "armor" — ask for *"ornate elven plate armor etched with silver-leaf patterns"*. Materials are where most generic outputs go wrong. Naming the material adds two minutes to the prompt and ten times the believability.

---

## Realism, anti-plastic skin, and UGC / phone-shot prompting

This is the layer that separates "a nice AI image" from "a photograph that passes." Anything where the brief involves *editorial portrait*, *UGC ad*, *dating-app shot*, *behind-the-scenes*, *candid selfie*, *iPhone shot*, *mirror selfie*, *disposable camera*, *flash-on-camera*, or anything described as needing to "look real / not look AI" — go directly to `references/realism_and_ugc.md` for the full stack. **For cinematic *film-frame* realism specifically — any brief that says "make it a real film still / shot on film / photoreal cinema / kill the AI look / doesn't look AI-generated / indistinguishable from real / realistic frame" — use `references/frame_realism_engine.md`, the film-scan enforcement layer (the ONE law of filmic restraint, the caught-not-made anti-refinement law, the grade lock, the skin-truth pillar, the A–D mode router, a physical/anatomical-consistency pass, the anti-AI-tell pass, and the verbatim skin + grade tails). `realism_and_ugc.md` is the phone/UGC register; `frame_realism_engine.md` is the cinematic film-scan register — pick one per frame.** Quick summary:

**Realism is a stack, not a keyword.** No single phrase like *"photorealistic"* or *"8K"* does the job. Stack four layers in every prompt.

### Layer 1 — Skin (anti-plastic)

Stack 2-3 cues from: *visible pores, fine vellus hair, subsurface scattering, T-zone sebum sheen, dry patches around the nostrils, faint freckling, small blemish near the jaw, uneven skin tone, faint redness on cheekbones, individual strand hair detail*. Close with: *"not airbrushed, no beauty filter, no smoothing, no AI render look."*

### Layer 2 — Light direction

Plastic skin is half a *lighting* tell. Replace "cinematic lighting" with a directional, sourced, single-key recipe — *"hard window key from camera-left, no fill, deep shadow on camera-right cheek"* — or for UGC *"harsh direct on-camera flash, hard shadow on the wall, slight overexposure on the forehead"*. Always name source + direction + quality + falloff side.

### Layer 3 — Capture medium

Name the body, lens, aperture, and processing or film stock. Phone-shot tells: *slight HDR push, f/1.78 fixed aperture, computational fill, mild over-sharpening, Apple color science green midtones, edge artifacts where portrait-mode cutout fails on the hair*. Film tells: *organic grain denser in shadows, halation on highlights, slight color shift in shadows, dust particles in corners*.

### Layer 4 — Micro-imperfection

At least two of: *slight motion blur on a non-hero element, lens distortion at the frame edges, chromatic aberration on high-contrast edges, uneven exposure, mild lens flare, dust particles in the light shaft, slight tilt, off-center framing, stray hairs, fingerprints on the phone screen, smudges on the mirror, background clutter (mail, half-empty glass, charging cable, sticky note)*.

### UGC five-stack (capture · light · composition · subject · context)

UGC is a deliberate downgrade of every dimension that makes pro photos pro. Build with:
- **Capture:** phone body + 9:16 + HDR push + over-sharpening + computational fill
- **Light:** mixed temperature, multiple bulb types, no fill
- **Composition:** arm's length, slight downward tilt, off-center, top of head almost clipping, phone visible in frame
- **Subject:** mid-laugh / mid-talk, eyes off the lens, hair out of place, worn-today wardrobe with a stain or wrinkle
- **Context:** 3-6 real-life background objects, slight clutter, steam on a mirror, mail on the counter
- **Closer:** *"not staged, not retouched, casual close-friends story vibe, looks like a real Tuesday morning."*

Full prompts, JSON template, age-specific skin language, capture-medium tells, and failure-mode fixes all live in `references/realism_and_ugc.md`.

---

## Multimodal reference workflow (up to 14 images)

You can attach up to 14 reference images to one Nano Banana prompt. They can be a mix of subject, product, environment, style mood-board, logo, font sample.

### How to reference them in the prompt body

Nano Banana uses **natural language** to refer to attached images — not a numbered `Image N` syntax. Describe what's in the image when you reference it.

**Multi-element example:**
> *"The scene is set inside the restaurant in the photo I attached. The woman from the second reference photo is wearing the dress shown in the third reference. The boy from the fourth reference walks up to her at the counter. The logo from the fifth reference is in the bottom-right corner of the final image."*

Five attachments, all referenced by their content. The model figures out which is which.

### Identity-locking workflow

Nano Banana's character consistency is best-in-class for image models. The canonical workflow:

1. Generate or upload **one strong frontal portrait** of your character.
2. In subsequent generations, attach that portrait as a reference and write *"the woman from the attached portrait reference, [in new scenario]"*.
3. The model carries face, hair, age, ethnicity, key wardrobe across generations.

For multi-character work, attach one portrait per character and reference them by role (*"the bride from the first reference"*, *"the groom from the second"*).

---

## Resolution, aspect ratio, output controls

| Capability | Nano Banana (2.5 Flash Image) | Nano Banana 2 (3.1 Flash Image) | Nano Banana Pro (3 Pro Image) |
|---|---|---|---|
| Resolutions | 1K | 0.5K, 1K, 2K, 4K | 1K, 2K, 4K |
| Standard aspect ratios | 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9 | + 1:4, 4:1, 1:8, 8:1 | Same as 2 |
| Max input images | 14 | 14 | 14 |
| Live web search | — | ✓ | ✓ |
| Knowledge cutoff | Early 2024 | Jan 2025 | Jan 2025 |
| Content credentials | C2PA + SynthID | C2PA + SynthID | C2PA + SynthID |
| Status (June 2026) | GA (legacy) | GA | GA |
| Speed · ~price/img | — | <2 s · ~$0.02–0.04 | 2–5 s · ~$0.134 (1K–2K), ~$0.24 (4K) |

**Aspect ratio in the prompt:** put it as a closing instruction — *"Output in 9:16 vertical aspect ratio."* You can also pass it as an API parameter.

**Iteration economics:** iterate on Nano Banana 2 (fast, ~2–4¢/image) at lower resolution, then switch to Nano Banana Pro for the hero / 4K / text-heavy final.

---

## Common failure modes and fixes

**Generic output.** Symptom: looks like every other AI image. Fix: add material specificity, named lighting, named lens, named film stock, and a closing style sentence.

**Plastic / airbrushed skin.** Symptom: doll-like, even, retouched. Fix: stack the four realism layers — skin texture cues, directional single-source light, named capture medium, micro-imperfection pass. Full recipe in `references/realism_and_ugc.md`.

**UGC shot looks like a styled ad.** Symptom: clean background, even light, perfect composition. Fix: remove "lifestyle photography" from prompt; add mixed-temperature practical lighting, 4+ background clutter objects, off-center composition, *"not styled, not staged, not a photoshoot"*.

**Character drifts across edits.** Symptom: the same person looks slightly different after each conversational turn. Fix: in every edit prompt, add *"keep the face, hair, and identity exactly the same as in the previous image"*. For long sessions, every 3-4 turns regenerate using a strong reference photo to re-anchor.

**Adjacent regions get re-rendered unnecessarily.** Symptom: you asked Nano Banana to add a hat, and the background also changed. Fix: *"keep everything else exactly the same"* on every edit turn. Be explicit about what should be untouched. If it keeps happening, escalate to the structured CHANGE / PRESERVE EXACTLY block in `references/surgical_edits_and_higgsfield_routing.md` and enumerate every locked element by name.

**The edit rebuilt the frame instead of touching it.** Symptom: you asked for one small change and got a recognisably different image. Two causes: the CHANGE was too broad, or the ask was never an edit in the first place. Fix: shrink the CHANGE and lengthen the PRESERVE list; if the frame genuinely needs rebuilding, regenerate it rather than editing toward it.

**A reverse angle of a location scrambles the geometry.** Symptom: you asked for the other side of the room and got a different room. Fix: spell out the NEW arrangement object by object (*"the sofa that was on the right is now on the LEFT; the doorway behind camera is now visible ahead"*) — or route the view change to GPT Image 2, which handles it natively. See `references/surgical_edits_and_higgsfield_routing.md` §3.

**Text rendered wrong.** Symptom: typos, garbled glyphs, kerning issues. Fix: quote the text literally, name the font, request English first then translate.

**Style transfer that loses content.** Symptom: applying Van Gogh style to a portrait obliterates the face. Fix: *"Recreate the exact subject and composition of the base image — preserving facial features — in the style of [reference style]."*

**Web-search prompts that ignore the search.** Symptom: Nano Banana 2 generates but doesn't seem to use real-time data. Fix: start the prompt with the search instruction explicitly as the first verb — *"Search for [X], then visualise…"* — and make the analytical task clear.

**Composition fails when too many references.** Symptom: with 10+ references, the model gets confused about priorities. Fix: be explicit about the role of each reference (*"first reference is the subject, second is the environment, third is the style"*).

**Negative-framing artefacts.** Symptom: you wrote "no cars" and the model put cars in. Fix: rewrite as positive ("empty street"). Negative framing is unreliable in Nano Banana — use sparingly. Exception: anti-retouching negatives DO land (*"not airbrushed, no beauty filter, no smoothing"*).

**Aspect ratio drift.** Symptom: the output isn't quite the ratio you asked for. Fix: include the ratio at the end as a closing instruction AND at the API level.

---

## Worked examples by use case

See `references/worked_examples.md` for ten extended worked prompts covering:

1. Product photography (with material specificity)
2. Editorial fashion portrait
3. Multi-character storyboard
4. Logo + character composition
5. Text-heavy poster with multi-language localisation
6. Style transfer (Van Gogh-style portrait)
7. Conversational multi-turn edit sequence
8. Web-search grounded visualisation
9. Architectural mockup with material reference
10. Brand mood-board to deliverable conversion

For realism / UGC / phone-shot worked examples and full JSON templates, see `references/realism_and_ugc.md`.

---

## Quick checklist before pressing Generate

1. Have you started with a strong verb (*Generate*, *Compose*, *Render*, *Remove*, *Add*)?
2. Subject + Action + Location + Composition + Style all named? (For text-to-image.)
3. References explicitly described and given a role? (For multimodal.)
4. Lighting source named (not just "cinematic lighting") — with direction and falloff side?
5. Camera / lens / film-stock named?
6. Material and texture specified for hero objects?
7. If it's a portrait: at least three skin-texture cues stacked? Anti-retouching negatives at the close?
8. If it's UGC: capture · light · composition · subject · context all downgraded toward real?
9. At least two micro-imperfection cues (motion blur, edge softness, dust, clutter, off-center framing)?
10. Text in quotes and font named?
11. Aspect ratio stated at the end?
12. "Keep everything else exactly the same" added if it's an edit — or the full CHANGE / PRESERVE EXACTLY block if the edit is precision work?
13. If it's an edit: exactly ONE change this pass, and every removal paired with a fill?
14. Iteration plan: low-res first, 4K only on the final?

---

## When NOT to use Nano Banana — switch to another skill

- **A moving clip, animation, or video** → use `seedance-2-prompter` or `kling-prompter`. Nano Banana only makes still images, not video.
- **You want a video that features the image you just generated** → keep the Nano Banana output as your hero still, then chain into `seedance-2-prompter` or `kling-prompter` for the motion. See `gen-media-router` for the recipe.
- **You want a whole video SEQUENCE built from storyboard frames** ("storyboard then animate", "shot-by-shot AI film", "make the frames then the video") → this is the shared storyboard→video pipeline. Draw the frames here following `references/storyboard_to_seedance.md` (beat plan, character-sheet identity lock, seed-quality frames, optional last frames), then hand off to `seedance-director` (`references/storyboard_from_stills.md`) to animate and stitch. Both skills own this pipeline together.
- **Animating a still you generated here** → after rendering in Nano Banana, hand off to `kling-prompter` (image-to-video) or `seedance-2-prompter`.

Still images, but a **different image surface** owns the job:

- **The same face has to survive dozens of generations** (casting sheets, a recurring character across a campaign) → **Higgsfield Soul 2.0**, where Soul ID locks identity at the platform level. Prose anchors reinforce it; they don't replace it.
- **A character reference sheet, fast** → **Cinema Studio AI Cast** builds one automatically from its own UI — no prompt needed. Offer it as the fast path; hand-build the 3-panel sheet only when full control is required.
- **A 21:9 cinemascope location plate or film still** → **Higgsfield Soul Cinema** (Soul 2.0 has no 21:9; a Soul ID character can be dropped into the scene).
- **Sloppy AI textures in an otherwise-finished frame** (plastic skin, dead fabric, flat surfaces) → **Seedream 4.5** texture pass. Never hand it a point edit.
- **One tiny local fix Nano Banana wouldn't take, or a location view change** → **GPT Image 2**, last resort: dirty across the whole frame, excellent locally.

Full routing table, escalation ladder, and the per-tool templates: `references/surgical_edits_and_higgsfield_routing.md`.

Nano Banana is the image specialist — text-to-image, image editing, multi-image composition, native typography, live-data visualisation, photoreal portraits, UGC and phone-shot realism. It is also the **first rung of every edit**: no edit starts anywhere else. The moment the brief involves motion, switch tools.

## Surgical edits, prop sheets & cross-tool routing

- **Any edit of an existing frame that has to be precise** — client asset, hero frame, or a retry after the model overshot → `references/surgical_edits_and_higgsfield_routing.md`. The CHANGE / PRESERVE EXACTLY / ONLY CHANGE block, one change per pass, removals paired with fills, and the diagnostic (drifted = you changed too much, lock more).
- **Edit escalation ladder, fixed order:** Nano Banana first, always → **Seedream 4.5** for texture-slop revival only (never point edits) → **GPT Image 2** last resort for the finest local surgery. A frame that needs rebuilding is not an edit — regenerate it.
- **Location view change / reverse angle** → same file §3. On Nano Banana you must spell out the new object arrangement object by object, or the geometry scrambles; GPT Image 2 handles view changes natively.
- **Prop sheets and product-style objects** → same file §4. Neutral backdrop, isolated subject, materials + wear state, *"plain unbranded wrapper, blank matte surface"* for no-logo (never name the brand), separate assets per state (clean / damaged / bloodied), and neutral-function wording to dodge safety flags on device props.
- **Which surface owns the brief at all** (Nano Banana vs Higgsfield Soul 2.0 / Soul Cinema / Cinema Studio AI Cast / Seedream 4.5 / GPT Image 2) → same file §5, plus the character-sheet and location-plate templates in §7–8 and the shared tech/palette blocks in §9.
- **The 4-D pass** (deconstruct → diagnose → develop → deliver) and the DETAIL-vs-BASIC operating modes — ask 2–3 targeted questions on an ambiguous high-stakes build, deliver immediately when the user says "go" — → same file §0. Never more than three questions.

## Identity locking, movies, and pro photography

- Character consistency / recurring character / "same person across images" → `references/identity_lock_and_filmmaking.md`. Identity block before scene block, enumerate facial markers, 3-6 matched references, re-anchor every 3-4 edit turns.
- Storyboards, film sequences, "make a movie" → same file: lock one production-look block (stock + grain + lens + ratio) across every frame, generate coverage (wide/medium/CU), obey the 180° rule.
- Product or professional photography → `references/photography_pro.md`. One key, named fill, contact shadows, source-consistent reflections.
- Engine questions (which model, refs, resolution, edit-chain behavior) → `references/generation_mechanics.md`. Movement-level style briefs ("make it noir", "French New Wave") and deeper DP/grade asks → `references/movements_and_masters.md`.
- Clothing/apparel design, fashion flats, e-comm garment shots, makeup/hair briefs → `references/apparel_and_beauty.md` (silhouette → fabric+weight → construction → trims → wear → behavior). Streetwear, fit-pics, Gen-Z briefs → `references/streetwear_and_genz.md` (spec the proportion ratio + tribe + wear state + sneakers).
- Stills-photography style briefs → photographer blocks in `references/photographer_styles_and_eras.md`; period briefs → lock all six era layers. Wardrobe → silhouette/fabric/wear from `references/styling_and_set_design.md`; rooms → the four-layer set dress. Ads/campaigns and beauty/car/food/architecture briefs → `references/campaign_and_specialist_genres.md`.
- Commercial/advertising FRAMES specifically — packshots, hero product angles, end-frame lockups, hand-model and demo frames, OOH/billboard framing, built sets (seamless sweeps, color-drench, plinths, water sets, surreal scale), and practical elements (splashes, pours, condensation, steam, powder bursts, levitation) → `references/commercial_framing_and_set_design.md`. Pick ONE ad-genre look block, state the product's frame-fraction, give every element a physical cause.
- Football / soccer or FIFA World Cup 2026 shots — match action keyframes (strike, header, save, tackle), celebrations, stadium crowds, tifo, and fan/audience POVs → `references/football_and_fifa_frames.md`. Choose FREEZE (1/2000s, tack-sharp peak) or PAN (1/60s, subject sharp + streaked background); cast FICTIONAL players and invented kits — no real player likenesses, crests, or sponsor logos.
- Any figure in frame → posing checklist (weight never 50/50, hands need jobs, body/gaze tension) and three-plane depth from `references/composition_posing_and_critique.md`. After generating, run the critique rubric; use the generate→audit→repair loop on anything that matters.
- Any brief that casts a person of a specified ethnicity, nationality, or heritage — modern or traditional — → `references/global_ethnicity_casting.md` (region modules for South Asia, East Asia, Southeast Asia, Sub-Saharan Africa, Black diaspora, MENA, Latin America, Europe, Central Asia, Indigenous peoples, mixed heritage; the skin-tone system with tone-lock, deep-skin lighting craft, the hair-texture chart with anti-loosening close, and heritage-dress-by-occasion rules). Core rule everywhere: specify the five casting axes independently (skin tone + features + hair + wardrobe + context) — never use an ethnicity word as a feature shortcut, and vary faces within any same-ethnicity cast.
- Indian or Pakistani subjects specifically (also Bangladeshi) → `references/south_asia_casting.md` — India by region (NW–South tone cline, Northeast East-Asian features), Pakistan's ethnic map + shalwar-kameez-daily national dress, bindi/sindoor/dastar marker rules, regional saris, lawn suits, and the cross-contamination fails (bindi on Pakistani casting, sari as Pakistani daily wear, "India lite" flattening).
- UAE/GCC briefs specifically, Emirati/Khaleeji subjects, Arab-market UGC, Gulf national dress (kandura/ghutra/abaya/shayla), Ramadan/Eid content, or any "make it look local for Dubai/Saudi" ask → `references/uae_gulf_casting_and_ugc.md`. Get the national dress signatures right per country; cast public UAE scenes to the real ~88%-expat mix.
- MENA beyond the Gulf — Levantine/Egyptian/Nubian/Maghrebi/Iraqi/Iranian subjects, Amazigh/Kurdish/Persian peoples, tatreez/djellaba/galabeya/kaftan dress, or any Arab-world/North-Africa/Iran brief → `references/mena_casting.md` (kills the generic-Arab, auto-veil, and desert-default fails; Persian/Kurdish ≠ Arab).
- Southeast Asian subjects — Indonesian/Malay/Filipino/Vietnamese/Thai/Khmer/Lao/Burmese, incl. Melanesian Papuans, and dress like batik/kebaya/barong/terno/áo dài/longyi → `references/southeast_asia_casting.md` (kills the generic-East-Asian default, the one-country-dress cliché, and lightening of Khmer/Filipino/Melanesian skin).
- Interviews, talking heads, close-ups, midshots, dialogue frames → `references/closeups_and_interviews.md`. Always: off-lens eyeline + lav mic + mid-answer mouth; restate wardrobe fully in series; CHECK eyeline direction per frame (coin-flip axis).
- "Make it look like [film]", hard grading asks, or lighting-pattern questions → `references/film_look_references.md`. Never name a film alone — paste its component block. One film register + one portrait pattern + one scene style + one grading technique per frame.
- Mood/tone briefs, "make it feel like this reference", palette decisions → `references/tonal_families.md`. Read references for tone only (hue bias, skin, contrast, saturation, texture) — never copy their subject or composition. One tonal family per image.
- Lens choice, grain, diffusion filters, flash/editorial lighting, or "what stock/grade for this look" → `references/optics_grain_and_light.md`. One light idea + one stock/grain + one grade per image; artifacts need a physical cause. For grain: it lives IN the image (clumpy, midtone-dense, absent in pure black, melting in highlights), halation is a red-orange bloom hugging blown sources only, and film grain vs digital sensor noise are different textures — never mix their language. Camera-sensor signatures (Alexa rolloff, Venice night, Super 16 gate weave) are in section 8.
- Structured / JSON prompts (variable isolation, templating, batch, A/B — change one field, hold the rest) → `references/structured_prompting.md`. Non-photoreal work — illustration, flat-vector, 3D, anime, isometric, sticker, riso, logos & brand-identity systems, accurate diagrams → `references/graphic_and_illustration_styles.md`. For the DEEP stylized layer — Pixar-class/feature-CG 3D, anime sub-styles and studio looks, western cartoon eras, hand-drawn media, fine-art movements, 3D/NPR render techniques, product-render CGI, game art, game-engine looks, retro-digital — start at the router in `references/stylized_render_and_animation_looks.md` (UNVALIDATED — validate before trusting).
- DEFAULT REGISTER IS GROUNDED: physically plausible light, rentable gear, buildable grades. Nothing otherworldly unless the brief explicitly asks.

## Realism physics, perspective geometry & DP craft (deep layer — UNVALIDATED, Round pending)

- Frame still reads AI after the standard realism stacks, or the brief demands physical accuracy (exposure behavior, bokeh physics, mixed white balance, shutter-speed motion, shadow/reflection consistency, caused clutter) → `references/realism_physics_deep.md`. Core move: state the capture decision AND its cost ("exposed for the skin, so the window blows out"), then run its 8-point audit. Sits under `references/frame_realism_engine.md` / `references/realism_and_ugc.md`.
- Any brief where geometry matters — architecture/interiors, POV, mirror shots, OTS, giant/miniature scale, drone/aerial, "wide angle", face-flattering lens choice → `references/perspective_and_lens_geometry.md`. Laws: one camera one geometry (state height + tilt + distance + FOV); horizon = camera height, always; distance drives faces, lens tokens are style hints. Kills the drone-default and inconsistent-vanishing-point tells.
- Lighting ratio/mood asks, practical-lit scenes (lamp/TV/phone/candle/neon), golden-vs-blue-hour, day-for-night, haze/shafts, night exteriors, staged three-plane cinematic frames, or genre lighting (horror/noir/romance/thriller/documentary/music-video) → `references/lighting_craft_and_filmmaking_deep.md`. Pick ONE ratio + ONE named look per frame; motivate every shaft; state source exclusivity for practicals.

## Stylized looks & animation styles (deep layer — UNVALIDATED, Round pending)

- Any stylized/non-photoreal brief — "Pixar style", anime, cartoon, hand-drawn, oil painting, clay, toy/figurine, game art, "Unreal Engine look", vaporwave — start at the keyword router in `references/stylized_render_and_animation_looks.md`. Laws: ONE register per image; name the sub-style + 3–4 concrete signatures (never "cartoon"/"anime" alone); DROP the photoreal stack (pores/grain/capture tells) except where the file says otherwise; descriptive signatures first, studio/film names optional reinforcement only; never render trademarked characters.
- Painted-texture hybrid 3D (Arcane-type painted light) → `references/style_arcane_fortiche.md`. Physically-lit feature CG (simulated GI + SSS, Big Hero 6-era reference) → `references/style_feature_cg_simulated_light.md`. These two are OPPOSITE philosophies — never mix; each file carries register police + banned words.
- NPR/render techniques (toon shader, ink outline, matcap, clay+AO, wireframe, mixed-media 2D-over-3D, cutout, rotoscope, comic-print/painterly/sketch hybrid 3D) → `references/style_npr_and_animation_techniques.md`.
- Product-render CGI (KeyShot/Octane studio, exploded view, x-ray, liquid splash, cosmetics texture pulls, jewelry caustics, automotive streaks, food CGI, inflatable type, satisfying renders) → `references/style_product_render_cgi.md` (pairs with `references/commercial_framing_and_set_design.md`).
- Anime studio deep looks (Ufotable composite, KyoAni soft-light, Trigger angular, MAPPA grit, 70s–80s retro cel, webtoon/manhwa, gacha splash, Amano, Junji Ito) → `references/style_anime_studios_deep.md`.
- Illustration & design deep (editorial, corporate Memphis, mid-century ad, Swiss/Bauhaus, psychedelic, Art Deco poster, botanical plate, tattoo styles, graffiti/street art, Frazetta, D&D, tarot, matchbox) → `references/style_illustration_and_design_deep.md`.
- Game art (splash art, toon-3D BotW/Genshin, Fortnite/hero-shooter stylized realism, souls-like, 16-bit/PS2/N64, Hades, Hollow Knight, cozy, AAA cinematic, key-art framing) → `references/style_game_art.md`.
- Fine-art movements deep (Baroque tenebrism, Vermeer, Romanticism, Pre-Raphaelite, Klimt, Expressionism, Cubism, Surrealism, AbEx, Fauvism, Rococo, Byzantine, illuminated manuscript, shan shui, Persian miniature, Constructivism, WPA) → `references/style_fine_art_movements_deep.md`.

## Framing, scene grammar & continuity (master layer)

- Any framing/composition decision — shot-size ladder with lens+distance psychology, camera-angle grammar (height/tilt/orbit), framing relationships (clean/dirty singles, OTS, POV, two-shots, inserts, reactions), the nine composition systems, blocking/power staging, headroom & look-room mechanics — → `references/framing_scene_grammar_and_continuity.md`. One frame = one shot size + one composition system + one new piece of information.
- Any MULTI-FRAME job — storyboards, carousels, dialogue pairs, ad sequences, film-strip posts — apply its CONTINUITY GRAMMAR: the 180° axis restated per frame, eyeline match + screen direction, the 30° rule, match-on-action pairs, the verbatim continuity ledger, the coverage set (master first, edit-chain the rest), and Kuleshov/match-cut pairing.
- Scene-type briefs — establishing, dialogue, confrontation, action beat, chase, montage, reveal, aftermath — and commercial structures (problem→solution, product demo, testimonial, lifestyle, hero/spectacle, comparison; end-frame packshot law) → same file, sections 7–8.
- Aspect-ratio recomposition (21:9 vs 16:9 vs 4:5 vs 9:16 — restage, never crop) → same file, section 9.

## Director styles and film frames

When the brief mentions a director or DP by name, a "movie still / film frame" look, or asks for a stronger grade than the core tables provide, go to `references/director_styles_and_film_frames.md` — paste-ready signature blocks for 12 directors (never use a director name alone; pair it with 3-4 concrete signatures), a 9-cue film-frame anatomy + skeleton, expanded stock/grade vocabulary, and a grade-only edit recipe for regrading uploaded photos.

## Building finished social posts

- Building a finished **social/marketing post** — copywriting (hooks/captions/CTAs), professional type *systems*, platform layouts & safe zones, and post formats (single, **carousel**, cover/thumbnail, text/stat card, infographic, meme) → `references/creative_posts_copy_type_layout.md`. **Engage only when the brief is to make a post / social content** — for a plain image, portrait, product shot, or standalone film frame that isn't going out as a post, stay in the core skill. The skill's other files make the *photograph*; this one assembles the *post* around it and kills the design-level AI slop (default font + purple gradient + centered cards + say-nothing headline) that survives a perfect image.
- **Default the post's hero image to a real frame from a video** — caught mid-motion, available light, found composition, frame-grab imperfection (apply the real-frame override in `references/tonal_families.md`), not a posed AI render. It's the priority image register for posts and the strongest anti-slop move. Exception: type-hero formats (quote/stat cards, infographics) don't need a video-frame image.
- The copy-hole, read-order beats, and the multi-format master live in `references/campaign_and_specialist_genres.md`; glyph mechanics (quote the text, name the font, localise) in `references/text_rendering.md`. The posts file builds on both — it does not repeat them.
- ALWAYS write the words before the image: a post is briefed copy → type system → layout/size → image → brand marks → compliance pass, not a photo with text jammed on after.

## Pakistani ads, music videos & recent trends

- Any Pakistani / Pakistan-market advertising brief — TVC-style key art, Ramadan/Eid or telecom ad frames, FMCG/food heroes, local set & prop dressing, or when a Pakistani ad director is named → `references/pakistan_ads_and_directors.md`. Cast per `references/south_asia_casting.md`; defer generic ad grammar to `references/commercial_framing_and_set_design.md`.
- Any music-video still — performance frames, narrative frames, artist key art, cover/thumbnail — or when a music-video director is named (paste 3–4 signatures, never the name alone) → `references/music_video_styles_and_directors.md`. Lock the artist with `references/identity_lock_and_filmmaking.md`.
- "What's working now / make it feel current / recent-style ad", social-native or UGC-led briefs, or when an auteur commercial director is named → `references/recent_ad_trends_and_directors.md`.

## Realistic frames, Pakistani ads, music videos & recent trends

- **Realistic / film-frame briefs** — "make it look real / film still / shot on film / photoreal / kill the AI look / not look AI-generated / realistic frame", for portraits, scenes, products, crowds, interiors, exteriors → `references/frame_realism_engine.md` (cinematic film-scan enforcement). For phone/UGC/candid-selfie realism instead → `references/realism_and_ugc.md`.
- Any Pakistani / Pakistan-market advertising brief — TVC-style key art, Ramadan/Eid or telecom ad frames, FMCG/food heroes, local set & prop dressing, or when a Pakistani ad director is named → `references/pakistan_ads_and_directors.md`. Cast per `references/south_asia_casting.md`.
- Any music-video still — performance/narrative frames, artist key art, cover/thumbnail — or when a music-video director is named (paste 3–4 signatures, never the name alone) → `references/music_video_styles_and_directors.md`. Lock the artist with `references/identity_lock_and_filmmaking.md`.
- "What's working now / make it feel current / recent-style ad", social-native or UGC-led briefs, or when an auteur commercial director is named → `references/recent_ad_trends_and_directors.md`.

## Further reading

See `references/` for deeper detail:

- `references/framing_scene_grammar_and_continuity.md` — the master framing/scene/continuity layer: full shot-size ladder (size × lens × distance × psychology), angle grammar, framing relationships, nine composition systems, blocking & power staging, the continuity rulebook for multi-frame sequences (180°/30° rules, eyeline match, screen direction, continuity ledger, coverage set, match-on-action, Kuleshov pairing), narrative + commercial scene taxonomies, aspect-ratio recomposition, failure modes, and a sequence-frame prompt skeleton
- `references/surgical_edits_and_higgsfield_routing.md` — the edit-discipline and cross-tool routing lane: the 4-D pass with DETAIL/BASIC operating modes, the CHANGE / PRESERVE EXACTLY / ONLY CHANGE surgical-edit template (minimal change, exhaustive preservation, one change per pass, removal-with-fill), the fixed escalation ladder (Nano Banana → Seedream 4.5 texture pass → GPT Image 2 local surgery), location view-change / reverse-angle rules with object-by-object re-blocking, prop-sheet and product-object templates with the no-logo and safety-flag workarounds, the Higgsfield routing table (Soul 2.0 + Soul ID, Cinema Studio AI Cast, Soul Cinema 21:9), the carried-over anti-fail rules (anti-bloat ≤1500–2000 chars, positive-over-negative, illustration-drift triggers, 60/30/10 palette derived-not-invented, tattoo/text specificity, rule-of-thirds-except-sheets), the 3-panel character-sheet and location-plate templates, shared film-grain / clean-digital tech blocks, palette wrapper, and cinematographer shorthand
- `references/frameworks.md` — full breakdown of the five canonical frameworks with extended examples
- `references/text_rendering.md` — typography, fonts, localisation, and the text-first workflow
- `references/creative_director_controls.md` — lighting, lens, film stock, and material reference tables
- `references/realism_and_ugc.md` — anti-plastic skin, texture stacking, capture-medium tells, UGC five-stack, phone-shot geometry, JSON realism template, age-specific skin language, and realism failure-mode fixes
- `references/uae_gulf_casting_and_ugc.md` — ethnicity casting without the "generic Arab" stereotype composite (five independent casting axes), UAE demographic-accurate crowd casting, Emirati vs Saudi/Kuwaiti/Omani national-dress signatures (kandura/farukhah/ghutra/agal, abaya/shayla styles), Khaleeji skin-tone spectrum and beauty register, the five local UGC layers (AC-world environment logic, local clutter ledger, UAE settings, cultural calendar & GCC compliance, bilingual Arabic), model routing (2 for casting iteration, Pro for Arabic type), worked Gulf UGC frames, and region-specific failure modes
- `references/global_ethnicity_casting.md` — the model's six documented ethnicity biases (white-default, skin lightening, hair straightening, one-face homogenization, costume-ification, Westernizing drift) and their counter-moves; the skin-tone system (descriptor + undertone + MST anchor + tone-lock clause), melanin-rich-skin lighting craft (expose for the face, specular sheen, warm fill, anti-ashy), the hair-texture chart with named protective styles and the anti-loosening close; region modules with modern registers and named heritage garments for South Asia, East Asia, Southeast Asia, Sub-Saharan Africa (West/East/Horn/Southern), the Black diaspora, MENA beyond the Gulf, Latin America, Europe, Central Asia, Indigenous peoples (nation-naming, sacred-item rules), mixed heritage, and religious dress; global failure-mode table and an 8-step build order
- `references/south_asia_casting.md` — the India + Pakistan deep module: India cast by region (seven regional registers incl. the NW–South tone cline, Bengali olive undertone, Kashmiri fair register, and the East-Asian-featured Northeast), Hindu/Sikh/Muslim marker rules (bindi, sindoor + mangalsutra, dastar + kara, gajra, nath), regional sari taxonomy (Banarasi, Kanjeevaram, kasavu, lal-paar, Nauvari) and men's registers (sherwani, bandhgala, veshti/mundu); Pakistan's ethnic casting table (Punjabi, Pashtun, Sindhi, Baloch, Muhajir, northern peoples, Hazara), shalwar-kameez-as-daily-national-dress for men and women, waistcoat/pakol/Sindhi-topi/ajrak/Peshawari-chappal kit, lawn-print culture, gharara/sharara bridal, Pashtun-turban-vs-dastar distinction, Pakistan settings and texture ledger (truck art, dhaba, charpai), a Bangladesh register, worked frames for both countries, and the cross-contamination failure-mode table
- `references/mena_casting.md` — the MENA-beyond-Gulf deep module: cast-by-sub-region table (Levant, Egypt & Nubia, Maghreb Amazigh/Arab-Andalusian/Saharan, Iraq/Kurdish, Iran/Persian) with tone/feature/hair; heritage dress by people & occasion (tatreez thobe + qabbeh, keffiyeh patterns, galabeya, djellaba/kaftan/takchita/karakou/burnous, Kurdish + Persian registers); settings ledger that kills the desert cliché; worked frames; and the generic-Arab / auto-veil / Persian-as-Arab / Nubian-lightening failure table
- `references/southeast_asia_casting.md` — the SEA deep module (maritime + mainland): cast-by-people table (Javanese/Sundanese/Balinese/Papuan-Melanesian, Malay, Filipino incl. mestizo/Moro/Aeta, Kinh, Thai/Isan, Khmer, Lao, Bamar + minorities) with the anti-East-Asian-default tone-lock; heritage dress by country (batik/kebaya, baju kurung, barong/terno, áo dài/nón lá, chut thai, sampot, sinh, longyi/thanaka); settings ledger; worked frames incl. an anti-erasure Papuan test; and the failure table
- `references/worked_examples.md` — ten extended worked prompts across genres
- `references/director_styles_and_film_frames.md` — 12 director/DP style blocks, film-frame anatomy and skeleton, expanded grade/stock vocabulary, grounded colorist grading recipes (Rec.709, print emulation, split toning, skin-tone protection), and real-crew filming technique (motivated lighting order, 180° shutter logic, exposure discipline, blocking)
- `references/identity_lock_and_filmmaking.md` — identity-lock formula and five-step pipeline (hero image → character sheet → lock test → production → audit), reference-image standards, drift diagnostics, and the making-movies-in-stills grammar (production-look block, coverage, 180° rule, multi-scene continuity)
- `references/optics_grain_and_light.md` — the deep optics catalogue: lens-by-lens character (vintage glass, Helios swirl, anamorphic, tilt-shift), focal length psychology, lens effects & diffusion filtration (Black Pro-Mist, Glimmerglass, ghosting, CA), a film-grain library by stock (Vision3, Portra, Cinestill halation, pushed B&W, Super 8, VHS, digital noise), fashion/editorial lighting registers (direct flash, ring flash, LED tubes, night practical mixes), extended grade board, and four decoded editorial looks
- `references/generation_mechanics.md` — official engine mechanics: model IDs and routing, the object-vs-character reference split with exact per-model limits, thinking levels and thought images as a free diagnostic, thought signatures (why edit chains must stay in one thread), exact API parameters, hard limitations (no transparency, semantic-only masking), and workflow implications (512/1K iterate → 4K final, brief-as-PDF, Veo keyframe pipeline)
- `references/movements_and_masters.md` — 12 film movements as style blocks (noir, German Expressionism, French New Wave, Dogme, 80s high-concept, K-thriller…), 8 more cinematographers (Willis, Storaro, Kamiński, Fraser, Young, Khondji, Nykvist…), 8 photography registers (Magnum street, Düsseldorf School, Provoke, American color road…), a second grade board, and staging grammar (depth/lateral blocking, two-temperature scenes, the reveal frame)
- `references/photographer_styles_and_eras.md` — 16 photographer style blocks (Avedon, Newton, Lindbergh, Penn, Luchford, Teller, Tyler Mitchell, Petra Collins, Roversi, Bourdin, Leibovitz, Goldin, Salgado, Parr, Eggleston) with pairing logic, plus the six-layer decade system for era-accurate frames (capture, grade, fashion, props, typography, body language) and the "nothing manufactured after [year]" sweep
- `references/apparel_and_beauty.md` — garment anatomy (necklines, collars, sleeves, construction, closures), silhouette taxonomy, print/colorway language, designing NEW garments (concept renders, technical flats, tech-pack boards, fabric swatches, colorway edits, print placement), commerce formats (on-model, ghost mannequin, flat lay, try-on), full MUA vocabulary with named makeup looks, hair/nail language, and apparel/beauty failure modes
- `references/streetwear_and_genz.md` — streetwear proportion grammar, 9 aesthetic tribe blocks (Y2K, gorpcore, blokecore, skate, streetgoth, cleanfit, athleisure, chaos styling, quiet-street), wear-state realism, fit-pic capture registers, garment graphics/type spec, Gen-Z casting notes
- `references/styling_and_set_design.md` — stylist vocabulary (silhouette→fabric behavior→wear state, fabric light/movement cheat sheet, brand-register dressing, the one-disobedient-element rule) and production design (four-layer set dress: architecture/function/inhabitant/today, class signaling, prop logic, the set checklist)
- `references/campaign_and_specialist_genres.md` — campaign craft (copy-space holes, read-order hierarchy, multi-format masters, campaign blocks, social-native rules) and specialist genres: beauty close-up (clamshell + human-skin standard), automotive (reflection streaks, dusk window, wheel rules), food (backlight law, 10-minute rule), architecture (sacred verticals, twilight balance)
- `references/commercial_framing_and_set_design.md` — 16 commercial look blocks (tech-minimal white, premium dark tech, perfume surreal, watch macro, sports grit, beverage refreshment, fast-food craveability, skincare clinical-soft…), ad framing grammar (packshot angles by job, frame-fraction scale discipline, end-frame/packshot lockup, hand-model and demo frames, lifestyle first-read rules, OOH 7-words/3-second framing), built-set systems (seamless sweep/cyclorama, color-drench monochrome, plinths, surface library, water/fabric/botanical/surreal-scale/mirror sets, 2025–26 trend registers), the practical-elements library with physics notes (crown splash, arcing pour, carbonation, glycerin-look condensation, floating ice, steam, haze, powder bursts, levitation + contact shadow, cheese pull), the high-speed capture register, and commercial failure modes (*field-validated, Round 13*)
- `references/football_and_fifa_frames.md` — football / FIFA World Cup 2026 stills: the FREEZE-vs-PAN capture decision, long-lens compression + stadium-light craft, an action keyframe library (strike/header/bicycle/tackle/save/duel/free-kick/penalty/goal-line), celebration keyframes, ten audience & POV registers (stands POV, ultras/tifo, face-paint fan, pitchside-through-the-net, net-cam, gantry, spidercam, tunnel, trophy-lift), the stadium atmosphere ledger, worked prompts, the rights/likeness guardrail (fictional players, no logos), and the failure table (clone-crowds, over-clean turf, blown floodlights, posed-at-lens)
- `references/creative_posts_copy_type_layout.md` — the post as a layered deliverable: copywriting frameworks (HVC/PAS, tension/transformation hooks, CTA menu), professional type *systems* (3-level hierarchy, scale ratio, pairing, type colour, spacing), platform layouts & safe-zone logic (IG/Stories/TikTok/LinkedIn/X/Pinterest/YouTube + one-master→reframe), post formats (carousel grammar, covers/thumbnails, quote/stat/list cards, infographics, meme/lo-fi), brand-kit/template reuse and A/B variants, a real-frame-from-video image default, the design-level AI-slop taxonomy, a compliance + accessibility checklist (C2PA/SynthID auto-labeling, FTC, contrast/alt-text), worked post examples, a pre-flight checklist, and post-specific failure modes — *Round 8 validated the real-frame hero, copy-hole, text supers & anti-slop; carousel + safe-zone still untested*
- `references/composition_posing_and_critique.md` — visual grammar (placement systems, leading lines, negative space + look-room, figure-ground, color blocking, three-plane depth), fashion posing as physical instructions (contrapposto, hand jobs, gaze tension, movement beats, expression-as-thought), and the 11-point critique rubric with hard-fail tells and the generate→audit→repair loop
- `references/closeups_and_interviews.md` — shot-size grammar with per-size lenses, the seven-step cinematic interview formula (Rembrandt key, shadow-side-to-camera, negative fill, off-lens eyeline + look-room, practical bokeh, lavalier), talkie/dialogue frames (OTS pairs, listening shots, two-temperature phone calls, walk-and-talks), vox-pop register, CU craft (near-eye focus, single catchlight, emotion-as-physical-state), 20-frame validated findings incl. the eyeline coin-flip fix
- `references/film_look_references.md` — 24 specific film look blocks (Blade Runner 2049, Godfather, In the Mood for Love, Moonlight, Mad Max, Se7en, La La Land…), 13 hard colorist techniques (ENR silver retention, color contamination, subtractive saturation, split-complementary, duotone, tinted blacks, 60-30-10 discipline), the complete lighting style index (10 portrait patterns + 16 scene styles), and the full look-sentence stack
- `references/tonal_families.md` — the editorial tone atlas: 16 named tonal families (teal-noir night, sodium amber, blue-hour flash, hard amber chiaroscuro, terracotta earth, cold chrome minimal, Scandinavian silver, old-money mocha, pastel dawn, monochrome-plus-one…), the five-variable tone model, tone×subject pairing logic, and how to read tone from a reference image without copying its scene
- `references/photography_pro.md` — real studio lighting rigs (45/45, clamshell, book light, negative fill, strip-light gradients), the six-shot product list, background conventions by category, product failure modes, and pro recipes for portrait, food, architecture, street, and landscape
- `references/structured_prompting.md` — when to use structured/JSON prompts vs prose, the key schema, edit-one-field A/B, negatives-as-array, and caveats (*field-validated, Round 15*)
- `references/graphic_and_illustration_styles.md` — non-photoreal register blocks (flat-vector, line art, 3D render, anime/manga, isometric, sticker, riso, low-poly, paper-cut, blueprint), the logo & brand-identity-system workflow, accurate diagrams/infographics, and the raster-not-vector caveat (*flat-vector/isometric validated in Round 8*)
- `references/stylized_render_and_animation_looks.md` — the stylized-looks master router: feature-animation 3D family (Pixar-soft, DreamWorks, Illumination, Spider-Verse, painted-texture), anime & manga registers, western cartoon eras, hand-drawn/traditional media, fine-art & print registers, 3D registers (clay, claymation, figurine, vinyl, octane, isometric, low-poly, voxel), game-engine registers, retro-digital, style-transfer workflows, failure table (*UNVALIDATED*)
- `references/style_arcane_fortiche.md` — Arcane/Fortiche painted-texture hybrid-3D register: hand-painted light, matte-painting backgrounds, 2D FX, Piltover/Zaun lighting worlds, register police (*UNVALIDATED*)
- `references/style_feature_cg_simulated_light.md` — physically-lit feature CG register (path-traced GI, SSS, thousands-of-practicals night city; Big Hero 6-era reference, never a prompt word) (*UNVALIDATED*)
- `references/style_npr_and_animation_techniques.md` — 12 NPR/technique registers: toon/cel shader, ink outline, matcap, clay+AO, wireframe, mixed-media 2D-over-3D, cutout, rotoscope, motion-graphics flat, comic-print 3D, painterly hybrid (Puss in Boots), sketch-doodle 3D (TMNT) (*UNVALIDATED*)
- `references/style_product_render_cgi.md` — 10 product-CGI registers: studio lighting, exploded view, x-ray/cutaway, liquid sim, cosmetics texture language, jewelry caustics, automotive streaks, food CGI, inflatable typography, satisfying renders (*UNVALIDATED*)
- `references/style_anime_studios_deep.md` — 9 deep anime registers: Ufotable, KyoAni, Trigger, MAPPA, 70s retro cel, webtoon/manhwa, gacha splash art, Amano ink-watercolor, Junji Ito horror ink (*UNVALIDATED*)
- `references/style_illustration_and_design_deep.md` — 13 illustration/design registers: editorial, corporate Memphis, mid-century, Swiss/Bauhaus, psychedelic, Deco poster, botanical, tattoo trio, graffiti trio, Frazetta, D&D, tarot, matchbox labels (*UNVALIDATED*)
- `references/style_game_art.md` — 14 game-art registers: splash art, BotW/Genshin toon-3D, Fortnite, hero-shooter, souls-like, 16-bit, PS2, N64, Hades, Hollow Knight, cozy, AAA cinematic, key-art framing (*UNVALIDATED*)
- `references/style_fine_art_movements_deep.md` — 17 fine-art movement registers with the movement-prompt skeleton, realism-creep and register-collapse failure classes, gold-leaf and poster disambiguation trios (*UNVALIDATED*)
- `references/realism_physics_deep.md` — the physics of photographic realism: dynamic range & exposure sacrifice, focus-plane/bokeh optics, mixed-illuminant color science, perceptual detection research (relational tells: shadow convergence, reflections, symmetry), shutter-speed motion in stills, environmental physics (aerial perspective, penumbra, wet surfaces, contact shadows), caused clutter/scene grammar, and an 8-point post-generation audit (*UNVALIDATED*)
- `references/perspective_and_lens_geometry.md` — the geometry layer: vanishing-point consistency, perspective-is-distance (compression math, face geometry by lens×distance), camera-height grammar & the drone-default fix, wide-angle volume/keystone craft, forced-perspective scale cues, POV/mirror/OTS geometry, interior verticals discipline, nadir-vs-oblique aerial geometry (*UNVALIDATED*)
- `references/lighting_craft_and_filmmaking_deep.md` — working-DP craft: key:fill ratios as prompt language, source size/distance physics (inverse-square pools, book light, negative fill), color-temperature mixing (moonlight convention, day-for-night, dusk-for-night), practical-driven scenes (TV/phone/candle/neon signatures), exterior magic-hour ladder, haze/shaft control, filmmaking grammar for stills (three-plane staging, implied camera movement, coverage thinking, night-exterior pools), and six genre lighting bibles (*UNVALIDATED*)
- `references/frame_realism_engine.md` — the film-frame realism enforcement layer (based on Abdullah Imtiaz's Frame Realism Engine): filmic-restraint law, caught-not-made anti-refinement law, the locked grade finish, the four-property skin-truth pillar, core DNA (tonal contract, colour science, light logic, lens, material, composition, atmosphere), A–D mode router, a researched physical/anatomical-consistency pass, the anti-AI-tell pass, aspect-ratio rules, prompt-construction order, and the verbatim skin + grade tails, plus a Nano-Banana model-context section (what the model renders real vs not, its real levers, the resolution-vs-realism rule, NB2-iterate→Pro-final routing, and the verification loop)
- `references/pakistan_ads_and_directors.md` — Pakistan-market advertising: 10 ad-genre registers (Ramadan/Eid, humor telecom, FMCG masala, family-saga, jingle-FMCG…), the local set/prop ledger, Pakistani ad-director signature blocks (Asim Raza, Jami, Ahsan Rahim, Saqib Malik…), global ad-director blocks, and YouTube/Instagram reframing
- `references/music_video_styles_and_directors.md` — music-video frames: 13 aesthetic registers (Hype-Williams gloss, neon retro-noir, Lyrical-Lemonade chaos, Afro-surreal ritual, Hiro-Murai unease…), global director signature blocks, the Pakistani Coke-Studio (Xulfi/Giraffe) register, thumbnail/cover framing, worked prompts
- `references/recent_ad_trends_and_directors.md` — what's working in 2025–26 (social-native, authenticity, brand humor, proof/verified, nostalgia, campaign systems) as prompt registers, recent campaign looks, and the auteur ad-director roster (Glazer, Gavras, Jonze ad-mode, Matsoukas, Dougal Wilson…)
- `references/pakistan_ads_and_directors.md` — Pakistan-market advertising: 10 ad-genre registers (Ramadan/Eid, humor telecom, FMCG masala, family-saga, jingle-FMCG…), the local set/prop ledger, Pakistani ad-director signature blocks (Asim Raza, Jami, Ahsan Rahim, Saqib Malik…), global ad-director blocks, and YouTube/Instagram reframing
- `references/music_video_styles_and_directors.md` — music-video frames: 13 aesthetic registers (Hype-Williams gloss, neon retro-noir, Lyrical-Lemonade chaos, Afro-surreal ritual, Hiro-Murai unease…), global director signature blocks, the Pakistani Coke-Studio (Xulfi/Giraffe) register, thumbnail/cover framing, worked prompts
- `references/recent_ad_trends_and_directors.md` — what's working in 2025–26 (social-native, authenticity, brand humor, proof/verified, nostalgia, campaign systems) as prompt registers, recent campaign looks, and the auteur ad-director roster (Glazer, Gavras, Jonze ad-mode, Matsoukas, Dougal Wilson…)

## Field-validated findings

Live test-round results — what the model actually does, scored via the critique rubric — live in `references/field_findings.md` (Rounds 1–16 to date; Round 16 field-validated `references/framing_scene_grammar_and_continuity.md`). Consult it before trusting any "validated" claim, and append a new round whenever you run one. Kept out of this file so the evidence base can grow without bloating the router.


<!-- ═══════ FILE: nano-banana-prompter/references/frameworks.md ═══════ -->

# Nano Banana — the five canonical frameworks (full breakdown)

Google organises Nano Banana use into five frameworks. Match the task to the framework first; everything else (lighting, lens, realism) layers on top.

---

## Framework 1 — Text-to-image (no references)

**Formula:** `[Subject] + [Action] + [Location/context] + [Composition] + [Style]`

Five clean clauses, each editable. Write a *scene*, not a keyword pile.

> *"A striking fashion model wearing a tailored brown dress, sleek boots, holding a structured handbag. Posing with a confident, statuesque stance, slightly turned from camera. A seamless deep cherry-red studio backdrop. Medium-full shot, centre-framed, head and lower legs touching the frame edges. Fashion-magazine editorial style, shot on medium-format analog film, pronounced grain, high saturation, cinematic lighting."*

**Extended variations** (change ONE clause at a time to iterate):
- Swap *style*: *"…shot on a disposable flash camera, raw and nostalgic."*
- Swap *composition*: *"…extreme low angle, the model towering, head clipping the top edge."*
- Swap *location*: *"…on a rain-slicked night street, neon reflections."*

## Framework 2 — Multimodal generation (with reference images)

**Formula:** `[Reference images] + [Relationship instruction] + [New scenario]`

Up to 14 references. Nano Banana uses **natural language**, not `Image 1/2` syntax — describe each reference when you name it, and assign it a role.

> *"Using the napkin sketch I attached as the chair's structural design and the fabric swatch as its upholstery texture, transform this into a high-fidelity 3D render of a finished armchair. Place it in a sun-drenched minimalist living room with white walls and a single tall potted fig tree."*

For multiple references, label roles explicitly: *"first reference = the character's face, second = the dress, third = the environment."* See `references/generation_mechanics.md` for the object-vs-character reference split.

## Framework 3 — Conversational editing (no new references)

The multi-turn strength. Generate, then refine by talking: *"remove the man," "make the sky overcast," "add books on the table."*

**The critical phrase:** *"keep everything else exactly the same"* — without it, the model re-renders adjacent regions.

> Turn 1: *"A wide shot of a man and a woman on a park bench in autumn, golden-hour light, dappled shadows, Sony A7 IV aesthetic."*
> Turn 2: *"Remove the man. Keep everything else exactly the same — the woman, the bench, the lighting, the leaves."*
> Turn 3: *"Now the woman wears a red wool coat instead of black. Keep everything else exactly the same."*

Keep an edit chain in ONE thread (thought-signature continuity — see `references/generation_mechanics.md`).

## Framework 4 — Style transfer + composition (with new references)

**Composition formula:** *"Add the [object from reference] to [the base image], placed [where], lit [how]."*
**Style-transfer formula:** *"Recreate the exact content of [the base image] in the style of [reference style / movement] — preserving subject and composition."*

> *(portrait + Van Gogh reference)* *"Recreate the exact composition and face of the portrait in the Van Gogh style — thick impasto strokes, swirling background, cobalt-and-yellow palette. Preserve the facial features."*
> *(desk + MacBook reference)* *"Add the MacBook from the reference to the centre-left of the desk, lid at ~110°, screen showing a subtle wallpaper. Match the base image's window key from the right."*

## Framework 5 — Web-search-grounded generation (Nano Banana 2 / Pro)

**Formula:** `[Search/source request] + [Analytical task] + [Visual translation]`

Unique to Nano Banana — it fetches live data and visualises it. Lead with the search as the first verb.

> *"Search for the current weather and date in San Francisco. Use that data — if raining, make it overcast and wet; if sunny, bright midday. Visualise as a tiny city-in-a-cup miniature inside a modern smartphone-UI mockup."*

Failure mode: if it ignores the data, restate the search as the opening instruction and make the analytical task explicit.

---

## Choosing & combining

Most real jobs are F1 or F2 with F3 edits to finish. Style work = F4. Data/infographics = F5. You can chain: F2 to build a character → F3 to pose them across scenes → F4 to apply a grade. One framework leads; the others refine.


<!-- ═══════ FILE: nano-banana-prompter/references/structured_prompting.md ═══════ -->

# Nano Banana — structured / JSON prompting

Nano Banana (Gemini reasoning) reads structured prompts well. Structure isolates variables so you can change ONE thing and hold the rest — useful for templating, batches, A/B, and multi-attribute control. **But prose still wins for scene *feel*** — don't JSON a simple brief.

> **Field-validated (Round 15, `field_findings.md`) — ImagineArt, 2026-07-06.** A JSON prompt was honoured field-for-field (subject, wardrobe, lighting, lens, skin, finish, negatives, aspect_ratio) confirming variable-isolation on Pro (PASS strong, 21/22). Prose still preferred for pure scene feel.

> Reported (not yet field-validated here): community guides claim structured prompts give meaningfully better control than flat text by forcing the model to categorise. Treat the *technique* as sound and the *percentage claims* as marketing — confirm in a field round (this file is **provisional**, pending Round 8 in `references/field_findings.md`).

## When to go structured vs prose

| Use STRUCTURED when | Use PROSE when (default) |
|---|---|
| templating across many variants / a batch | one-off scene where mood matters most |
| isolating variables for A/B (swap one field) | the brief is simple — structure is overkill |
| many independent attributes (subject + product + camera + grade) | the feel/atmosphere is the point |
| reproducibility / handing a spec to a team | conversational multi-turn editing (`SKILL.md` Framework 3) |

## The key schema

Fill descriptive *values* — structure organises, but each value still needs craft language (not one-word keywords):

```json
{
  "label": "launch_hero_v3",
  "tags": ["product", "real-video-frame", "editorial"],
  "subject": { "who": "a creator's hands lifting a phone", "skin": "real texture, visible knuckle creases", "wardrobe": "..." },
  "action": "caught mid-lift, slight motion blur on the moving hand",
  "scene": "warm desk, available light from camera-left",
  "madeOutOf": { "phone": "matte aluminium", "desk": "scratched oak" },
  "camera": { "lens": "35mm", "aperture": "f/2.0", "angle": "slightly above, handheld" },
  "light": { "source": "desk lamp camera-left", "consequence": "right edge of hands in shadow, cast shadow camera-right" },
  "style": "a single frame from a handheld video clip, not a posed photo",
  "text": { "headline": "'4K. No waiting.'", "font": "high-contrast didone", "placement": "low-contrast upper-left" },
  "negatives": ["airbrushed skin", "default gradient", "centered layout"],
  "aspect_ratio": "4:5",
  "resolution": "2K"
}
```

## Rules that make it work

- **Values stay descriptive** — `"light": {"source":"hard window key camera-left","consequence":"deep shadow right cheek"}` beats `"light":"dramatic"`. The validated craft rules (shadow-consequence, frame-fraction, fabric-behavior) still apply *inside* the fields.
- **Edit one field, hold the rest** — for A/B, change only `text.headline` or `light`, keep everything else identical (mirrors the conversational *"keep everything else exactly the same"*).
- **Negatives as an array** — anti-retouching negatives land (`references/realism_and_ugc.md`); most other negatives are weak in Nano Banana, so keep the list short.
- **Don't over-structure** — collapse to prose the moment the JSON stops earning its keys.

## Caveats

- Nano Banana outputs raster, reads either format; JSON is an organisational aid, not a different engine. See `references/generation_mechanics.md`.
- Render type/labels at 2K+; verify any data values you put in `text`/diagram fields.

Pair with `references/creative_director_controls.md` (what to put in `light`/`camera`/`madeOutOf`) and `references/realism_and_ugc.md` (the realism fields).


<!-- ═══════ FILE: nano-banana-prompter/references/generation_mechanics.md ═══════ -->

# Nano Banana — generation mechanics (engine, models, API, limits)

The official engine behavior behind the craft. Read this for "which model, how many references, what resolution, why did my edit chain drift." Verify volatile specifics (exact pricing, API parameter names) against `ai.google.dev/gemini-api/docs` and Google Cloud's model docs — those change; the behavior below is stable.

## Models & routing (GA, June 2026)

| Model | API ID | Speed | ~Price / image | When |
|---|---|---|---|---|
| Nano Banana | `gemini-2.5-flash-image` | fast | low | legacy / cheapest 1K |
| Nano Banana 2 | `gemini-3.1-flash-image` | <2 s | ~$0.02–0.04 | **default for iteration** — fast, cheap, 0.5K–4K |
| Nano Banana Pro | `gemini-3-pro-image` (Vertex) / `gemini-3-pro-image-preview` (Gemini API) | 2–5 s | ~$0.134 (1K–2K), ~$0.24 (4K); batch ~½ | **hero / text-heavy / 4K final** — Gemini 3 reasoning, live web search, premium typography |

Model strings vary by surface — Vertex exposes `gemini-3-pro-image` / `gemini-3.1-flash-image` (GA, June 2026), while the Gemini API may still carry a `-preview` suffix (e.g. `gemini-3-pro-image-preview`). **Verify the exact string for your surface.** Routing rule: **iterate on NB2, finalize on Pro.** Pull Pro in whenever the frame carries real typography, needs world-knowledge accuracy (diagrams, brands, places), or ships at 4K.

## Reference images — the object vs character split

Up to **14** references per prompt (6–14 depending on surface). The model treats two kinds differently:
- **Object / style references** (product, fabric, logo, mood-board) — copied as *content or look*.
- **Character / identity references** (a face) — carried as *identity*, the consistency engine.

Assign every reference an explicit role — *"first reference = the character's face, second = the jacket, third = the environment, fourth = the color grade."* Unlabeled references past ~3–4 get priority-confused. Identity refs are strongest as one clean frontal portrait (see `references/identity_lock_and_filmmaking.md`).

## Thinking levels & thought images

Pro *reasons before it renders*. On surfaces that expose it, the intermediate "thought image" is a free diagnostic — it shows how the model parsed your brief before final render. If the thought image already has the wrong composition, fix the prompt, don't reroll.

## Thought signatures — keep an edit chain in one thread

Conversational edits carry hidden state (a **thought signature** — an encrypted trace of the model's reasoning) tying each turn to the last. The API enforces it: a model part missing its `thoughtSignature` throws a 400, and the official SDKs handle it automatically only if you keep one standard chat thread. **Start a new conversation and you lose it** — identity, grade, and scene drift. Keep any multi-turn edit sequence in a single thread; if you must restart, re-anchor with the reference portrait and restate the production-look block.

## API parameters (verify exact names)

Typical controls: `aspect_ratio` (1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9; + 1:4/4:1/1:8/8:1 on Flash), `resolution` / image size (0.5K, 1K, 2K, 4K — 2K/4K need NB2 or Pro), number of candidates, and reference image inputs. State aspect ratio at the END of the prompt **and** as the API parameter — prompt-only ratios drift.

## Hard limitations (design around these)

- **Transparency / alpha is limited and evolving** — historically no true alpha cutout (generate on a flat/known background and composite externally, or use `remove_background` downstream). Newer Gemini 3 image models add some transparency and bounding-box support — verify for your model/surface rather than assuming either way.
- **Masking is semantic, not pixel.** You can't paint a mask — you describe the region (*"the jacket only"*, *"the upper-left sky"*). Be linguistically precise instead.
- **Small text blurs at 1K**, long paragraphs are unreliable — render type at 2K–4K, post-process exact wordmarks.
- **Verify any data** in diagrams/infographics — the model renders plausible-but-wrong numbers.
- **Complex blends / big relight edits can artifact**; character consistency varies edit-to-edit — re-anchor every 3–4 turns.

All outputs carry **C2PA Content Credentials + a SynthID watermark** (platforms auto-detect and label — see `references/creative_posts_copy_type_layout.md` §8).

## Workflow implications

- **512/1K to iterate → 2K/4K only on the keeper.** NB2 cheap passes, Pro final.
- **Brief-as-PDF:** for complex jobs, attach the brief as a document — the model reads layout, copy, and spec from it.
- **Veo keyframe pipeline:** a Nano Banana still makes a strong first/last keyframe for a Veo (or Seedance/Kling) clip — lock the look here, animate there (`gen-media-router`).


<!-- ═══════ FILE: nano-banana-prompter/references/text_rendering.md ═══════ -->

# Nano Banana — text rendering and typography

Nano Banana renders text inside images with quality nothing else in the field currently matches. Use these patterns.

> **Field-validated (Round 12, `field_findings.md`) — ImagineArt, 2026-07-06.** Urdu **nastaʿlīq** rendered correctly on an Eid end-frame: "دل سے دل تک" in gold flowing joined glyphs, right-to-left, with a clean English subline and an "EID MUBARAK" kicker — all legible. Urdu RTL is confirmed on Nano Banana Pro (previously only CJK, R9). Quote the exact string, name nastaʿlīq, render on Pro.

## The four rules

### 1. Quote the literal text

Always wrap the actual text you want rendered in straight or curly quotes.

> ✓ *"Render a movie poster with the title 'GHOST PROTOCOL' in the centre."*
> ✗ *Render a movie poster with the title Ghost Protocol in the centre.*

The first version locks the exact glyphs. The second invites the model to paraphrase.

### 2. Name the typography style

Describe the font in detail or name a recognisable one.

**Phrases that work:**
- *"bold sans-serif"*, *"thin serif"*, *"condensed display font"*, *"all-caps geometric sans"*
- *"Century Gothic style"*, *"Bodoni Italic"*, *"Garamond"*, *"Helvetica Bold"*, *"Impact"*
- *"hand-drawn brush-script font"*, *"vintage type writer monospace"*, *"neon-tube italic script"*

**Pair with weight + texture:**
- weight: *thin*, *light*, *regular*, *medium*, *bold*, *black*, *heavy*
- texture: *matte*, *glossy*, *embossed*, *letterpress*, *neon-glow*, *chalk-on-blackboard*, *cut-out from torn paper*

### 3. Translate and localise

Write the prompt in English, request the rendered text in another language. Nano Banana 2 / Pro support 10+ languages including CJK and Arabic right-to-left.

**Worked example:**
> *"Render a luxury beauty product hero shot of a sleek face moisturiser jar. Beside the product, three lines of text:
> Top line: 'GLOW' in a flowing elegant brush-script font.
> Middle line: '10% OFF' in a heavy blocky Impact font.
> Bottom line: 'Your First Order' in a thin minimalist Century Gothic font.
> Then provide an alternate version of all three lines translated into Korean, and another version in Arabic with right-to-left layout."*

### 4. The text-first conversational hack

For complex layouts with text, do the writing in one turn and the rendering in another.

**Turn 1:**
> *"Suggest three slogan options for a luxury watch advertisement targeting professionals aged 30-50, with a focus on craftsmanship and heritage. Each slogan max 6 words."*

**Turn 2 (after picking one):**
> *"Now render a magazine ad with the watch from the reference photo, slogan option 2 as a thin Bodoni Italic headline at the top, brand name in small Helvetica Light at the bottom. Editorial luxury watch aesthetic, deep black background with dramatic side-lighting."*

Separating "what should it say" from "how should it look" beats trying to nail both in one shot.

---

## Typography techniques that work

### Cut-out text reveal

The text acts as a window onto another image.

> *"A typographic poster with a solid black background. Bold sans-serif letters spell 'NEW YORK', filling the centre of the frame. The text acts as a cut-out window — a photograph of the New York City skyline is visible ONLY inside the letterforms."*

### Mixed-font layout

Multiple fonts in one image, each line styled differently.

> *"Generate a vintage book cover. Title 'A YEAR IN PROVENCE' in a thin elegant serif at the top. Subtitle 'Notes from a Country Garden' in a small italic Garamond below the title. Author name 'PETER MAYLE' in all-caps Futura at the very bottom. Cream paper background, light pencil sketch of a stone farmhouse in the centre. Letterpress texture."*

### Logo + tagline pairing

> *"A minimalist brand identity render. A logo combining a simple line-drawn coffee bean with the wordmark 'NORTHERLY' in bold geometric sans-serif. Below the logo, the tagline 'Slow roasted, slowly enjoyed' in a thin italic serif. All on a textured oat-coloured background. Aspect ratio 1:1, square. Modern minimalist design."*

### Hand-drawn signage

> *"Render a corner-shop chalkboard sign that reads 'TODAY: FRESH BREAD + HOMEMADE JAM' in white chalk on a dark slate background. Imperfect hand-drawn capital letters, slight chalk smudges, a small flower doodle in the corner. Photographed at slight angle in soft natural daylight."*

### Period typography

> *"A 1950s American diner menu. Cover reads 'JIMMY'S DINER' in red bold serif with a small star above each letter, and 'Since 1952' in italic script below. Yellow checkered border. Aged paper texture with slight creases. Vintage advertising aesthetic."*

---

## Multi-lingual rendering examples

### CJK

> *"Render a Tokyo neon sign at night. Vertical kanji characters spelling out '今夜は何にしますか' (What shall we have tonight?) glowing in pink neon against a wet brick wall. Heavy halation around the tubes, slight neon reflection in the puddles below."*

### Arabic (right-to-left)

> *"A modern minimalist poster. The Arabic phrase 'الحياة جميلة' (life is beautiful) in elegant cursive calligraphy, white on a deep teal background, positioned right-to-left with the text centred. Below it in small English caps, 'LIFE IS BEAUTIFUL'. Sans-serif modern aesthetic."*

### Mixed bilingual

> *"A double-language café menu cover. Top half in English: 'MORNING MENU' in a tall thin serif font. Bottom half in Mandarin: '早餐菜单' in the same proportional weight, rendered in elegant ink-brush calligraphy. Cream background, small illustration of a coffee cup with steam in the centre."*

---

## When typography fails

| Symptom | Fix |
|---|---|
| Garbled or misspelled text | Quote the literal text, name the font, use Nano Banana Pro for the highest text fidelity |
| Wrong font, looks generic | Name a specific recognisable font (Helvetica, Bodoni, etc.) |
| Letters touching or overlapping | Add *"clear letter spacing"* or *"generous kerning"* |
| Text too small / wrong placement | Specify position explicitly (*"centred in the upper third"*, *"large, filling the centre"*) |
| Multi-line text but lines look the same | Describe each line separately with different style instructions |
| Translation incorrect | Provide your own translation in the prompt instead of asking the model to translate |
| Right-to-left languages laid out left-to-right | Explicitly state *"right-to-left layout"* for Arabic / Hebrew |

---

## Brand-mandated typography — when to use post-processing instead

Nano Banana's typography is great for stylised supers, posters, hand-drawn signage, and creative compositions. It is **not great** for pixel-perfect brand wordmarks where exact kerning, custom letterforms, or proprietary fonts must be reproduced.

For brand-mandated typography:
- Render the rest of the image in Nano Banana.
- Mask out the logo / wordmark area.
- Drop the official brand asset in via Photoshop, Figma, or After Effects.

This is the same compromise that applies to Seedance video text overlays — generative text models are great for atmosphere, not for kerning a Coca-Cola wordmark.


<!-- ═══════ FILE: nano-banana-prompter/references/identity_lock_and_filmmaking.md ═══════ -->

# Nano Banana — identity lock & making films in stills

Two linked problems: keep ONE person looking like themselves across many images, and shoot a multi-frame sequence that reads as one production.

> **Field-validated (Round 12, `field_findings.md`) — ImagineArt, 2026-07-06.** A 3-frame Pakistani-ad sequence held one character (face, beard, mole, wardrobe) across a wide chai-stall establisher, a medium shop shot, and a warm end-frame, using the reference-image + restated-identity-block workflow (generate Frame 1, attach it as the img2img reference for later frames, restate the LOCKED CHARACTER block verbatim each time). Series-consistency CONFIRMED. Fine markers (a brow scar) don't always survive — the method carries the gestalt face reliably; restate the full block every frame.

---

## 1. The identity-lock formula

**Identity block BEFORE scene block.** Describe the person as a fixed spec, then drop them into the scene. Never let the scene description re-roll the face.

Enumerate the markers the model actually holds:
> *"the same woman from the attached portrait: early 30s, warm olive skin, deep-set brown eyes, thick dark brows with a small scar through the left, aquiline nose, full lips, a beauty mark below the right eye, shoulder-length black hair with a center part — keep these exact."*

The fixed-marker list (5–7 items) is what survives across generations: age, skin tone, eye shape/colour, brow shape, nose, lip fullness, one or two unique marks (scar, mole, gap teeth), hairline/part. Vague faces drift; enumerated faces hold.

## 2. The five-step pipeline

1. **Hero image** — generate or upload ONE clean, evenly-lit frontal portrait. This is the anchor.
2. **Character sheet** — from the hero, render a 3–6 view sheet (front, 3/4 L, 3/4 R, profile, maybe expression variants) on neutral seamless. Same lighting, same crop. This is your reference set.
3. **Lock test** — put the character in two unrelated scenes; confirm the face still reads. If it drifts, tighten the marker list.
4. **Production** — attach the hero (and 1–2 sheet views) to every scene prompt: *"the woman from the attached portrait reference, [new scenario]."*
5. **Audit** — run the five-point face check each frame: eye spacing, nose shape, lip fullness, jawline, the unique mark. Regenerate any frame that misses two.

## 3. Reference-image standards

Best identity refs: **frontal, neutral expression, even soft light, sharp, no heavy makeup or sunglasses, hair off the face.** A dramatic or shadowed reference teaches the model the *shadow*, not the *face*. For multi-character work, one labeled portrait per person (*"the bride = first reference, the groom = second"*).

## 4. Drift diagnostics

| Symptom | Cause | Fix |
|---|---|---|
| Face shifts every edit turn | no re-anchor; thought-signature decay | re-attach the hero every 3–4 turns; *"keep the face exactly as the previous image"* |
| Younger/older across frames | age not pinned | state age + age-skin cues every frame |
| "Sibling, not the same person" | marker list too vague | add 2 unique marks (scar, mole, gap) |
| Identity lost under hard light | dramatic reference taught the shadow | anchor with the flat frontal hero, not the moody frame |
| Ethnicity/features averaging | scene block overrides identity | identity block FIRST, scene block after |

## 5. Making films in stills (sequence grammar)

A storyboard or "movie" in stills is one production look across every frame — only the shot changes.

- **Production-look block** — lock once, paste verbatim into every frame: *"shot on [stock/sensor], [grain], [lens family], [grade], [aspect ratio]."* This is the continuity glue.
- **Coverage** — don't shoot ten of the same size. Cover the scene: wide establishing → medium → close-up → insert → reverse. Name the size each frame.
- **The 180° rule** — keep the camera on one side of the action line so screen direction stays consistent; state who faces frame-left vs frame-right and hold it.
- **Multi-scene continuity** — wardrobe, props, time-of-day, and grade carry between scenes unless you change them on purpose; restate them each frame (the model has no memory across separate generations except the edit-chain thread).
- **Eyelines match across a cut** — if A looks frame-right at B, B looks frame-left at A (see `references/closeups_and_interviews.md` for the eyeline coin-flip fix).

Pair with `references/director_styles_and_film_frames.md` for the look and `references/composition_posing_and_critique.md` for the per-frame critique.


<!-- ═══════ FILE: nano-banana-prompter/references/frame_realism_engine.md ═══════ -->

# Nano Banana — Frame Realism Engine (film-frame realism enforcement)

**Trigger this file whenever the bar is "real."** Any brief that says *make it look like a real film frame · film still · shot on film · photoreal cinema · kill the AI look · doesn't look AI-generated · indistinguishable from real · realistic frame · cinematic realism* — for portraits, scenes, products, crowds, exteriors, interiors alike. This is the realism **enforcement layer**: tonal curve, colour science, light logic, lens behaviour, skin/material truth, composition, physical consistency, and a strict anti-AI-tell pass. Do **not** use for stylised, illustrated, flat-design, or deliberately non-photographic output.

Relationship to the rest of the skill (no duplication — reach across):
- **UGC / phone-shot / "candid selfie" realism** (a different look — HDR push, over-sharpening, on-camera flash) → `references/realism_and_ugc.md`. This file is the *cinematic film-scan* register; that file is the *phone/social* register. Pick one per frame.
- **Lens character, grain-by-stock, halation physics, diffusion filters** → `references/optics_grain_and_light.md`.
- **Grade recipes & film looks** → `references/film_look_references.md` / `references/director_styles_and_film_frames.md`. **Casting** → `references/global_ethnicity_casting.md` (+ regional files).

> Based on the **Frame Realism Engine** authored by **Abdullah Imtiaz**, adapted to skill house-style and extended with a researched physical-consistency pass and practical keyword layers. The two paste-verbatim tails (skin tail, grade tail) are reproduced unchanged — append them exactly.

> **Field-validated (Round 10, `field_findings.md`) — Nano Banana, ImagineArt, 2026-07-06.** Five frames scored, all PASS (strong): MODE B skin benchmark (21/22), MODE C colour chiaroscuro (21/22), MODE E clean-register + the physical/reflection-consistency pass (20/22), plus the Pakistan Ramadan and music-video neon registers. **Confirmed:** the skin-truth pillar, the skin tail, and BOTH grade tails hold across warm / coloured / clean / night; and *realism ≠ grime* — the clean-register tail yields clean-but-real skin with no imposed grain, haze, or desaturation. **New rule:** never prompt "reserve space for a logo/text" — the model may draw a placeholder box; leave negative space and composite marks in post. **Round 11 (2026-07-06) closed MODE A (cold institutional bank) and MODE D (natural daylight rooftop, Dougal-Wilson register) — all five modes A–E are now field-validated.** Further rule from R11: for city-specific exteriors, name the exact skyline or add "no iconic landmarks" (the model defaulted to Badshahi-style minarets on a "Karachi" brief).

---

## NANO BANANA CONTEXT — what's real, what isn't, what works, when to use what

This engine runs on an **AI model**, not a camera — so know how Nano Banana (Gemini image stack) behaves, because its every default fights realism and you must instruct against each.

**The model's default is the "attractive AI" look this engine kills.** Left alone, Nano Banana renders: even beauty-lit skin, high micro-contrast + clarity, a slight HDR pop, symmetrical averaged faces, tack-sharp edge-to-edge, clean empty backgrounds, sourceless even light, and subjects posed at the lens. Every one is the opposite of filmic truth. The model will *not* drift toward "real" on its own — realism is something you actively enforce against these priors.

**What actually works on Nano Banana (its real levers):**
- **Describe recording conditions in natural language**, not keyword piles — it's a reasoning model and rewards a director's-brief scene description (subject → action → location → MODE/light → lens → skin/material → tonal contract → grain → ratio).
- **Anti-retouching negatives DO land here** (rare among image models): *"not airbrushed, no beauty filter, no smoothing, no HDR, no clarity, no oversharpening, no AI-render look."* Most *other* negatives are unreliable — prefer positive phrasing everywhere else.
- **The conversational edit chain IS the realism workflow.** Generate, then pull back the specific tell: *"keep everything exactly the same, but lift the blacks, drop the saturation ~25%, soften the focus, and add fine film grain."* Iterate toward restraint rather than nailing it in one shot. Stay in one thread so edit continuity holds.
- **Reference images (up to 14).** Attach a real film still / photograph as a **grade + texture reference** — *"match the tonal restraint, grain, softness and skin of the attached frame"* — and/or a portrait for identity lock (`identity_lock_and_filmmaking.md`). Read a reference for **tone, not subject** (`tonal_families.md`).
- **The two tails are reusable appends.** Paste the skin tail + grade tail verbatim on every generation — they're the constant that holds the finish across different scenes.

**Resolution is a realism lever (counter-intuitive rule):** *over-resolved is a tell.* Nano Banana Pro at 4K can render **too** clean and crisp to pass as film. Iterate at **1K–2K**, and keep the hero at ~2K with the grain/haze/soft-focus stack rather than a naked 4K. If 4K is required for delivery, push grain + diffusion + soft focus hard so the detail doesn't out itself. 4K is for typography/detail heroes; **film-scan realism lives at 1K–2K + grain.**

**When to use which model:**
- **Nano Banana 2** (`gemini-3.1-flash-image`) — the realism workhorse: fast, cheap (~2–4¢), 0.5K–4K. Explore mode/grade/skin, run grade-tail A/Bs, iterate the edit chain.
- **Nano Banana Pro** (`gemini-3-pro-image`) — the final hero: stronger skin topography, subsurface, and — because of its heavier reasoning — better at the **physical/anatomical/reflection consistency pass** (shadows, reflections, finger counts). Also premium typography and real-world grounding. Deliver on Pro, then re-verify the anti-AI-tell + consistency passes.
- **Legacy Nano Banana** (`gemini-2.5-flash-image`) — 1K only; quick tests, weaker skin.

**Aspect ratio on Nano Banana:** ask for **21:9** for the scope/anamorphic feel (closest native ratio to 2.39:1); **3:2** or **4:5** for stills-photography realism. State the ratio as a closing instruction (and at the API level). Never draw letterbox bars.

**Photography vs film-frame:** this engine covers both — same restraint law, just swap the capture medium (a named still camera + film stock and f-stop for photography; a cine stock + anamorphic feel for film frames). Everything else — grade lock, skin truth, consistency pass — is identical.

**The realism verification loop (run every time):** generate on NB2 → eyeball the anti-AI-tell pass **and** the physical-consistency pass → conversational edit to pull back the exact tell (*too sharp / too saturated / plastic skin / clipped highlight / wrong reflection / floating subject*) → re-anchor identity if it drifted → finalize on Pro → re-verify against the grade plates. The model will happily regress to "pretty" — audit every output.

---

## THE ONE LAW — filmic truth over impact

A real camera and film stock are **low-contrast, low-saturation recording systems** that hold detail at both ends of the curve and add weight to the middle. They record; they do not amplify. The instant you make something punchier, brighter, more saturated, sharper, or more dramatic than it physically is, you have left cinema and entered "AI render." **Restraint is the whole craft.**

## REALISM ≠ GRIME — match the subject's true state (read this before applying anything below)

Realism means the frame records **what was actually there** — and plenty of real subjects are clean, bright, new, and crisp. A just-unboxed phone, a modern white kitchen, a luxury boutique, a beauty close-up, a sunny high-key portrait, a freshly pressed shirt: the *real* version of these is not dirty, worn, hazy, heavily grained, or desaturated. **Do not impose grime, wear, clutter, milky haze, heavy desaturation, or a gritty naturalistic grade on a subject whose true state is clean.** That is just a different failure — over-styling — dressed as realism.

Separate the two kinds of "imperfection" this file talks about:
- **Anti-AI-render cues — universal, always on.** Plastic even skin, clipped highlights, crushed neutral blacks, over-sharpening/over-resolution, floating subjects, sourceless light, symmetrical averaged faces, garbled reflections, impossible anatomy/physics. These betray the *render*, so kill them on every frame regardless of subject.
- **Grunge cues — conditional, subject-driven.** Dirt, wear, decay, clutter, heavy grain, imposed haze, deep desaturation, ugly available light. These belong **only** to subjects and worlds that would truly carry them (a derelict seafront, a lived-in room, a rain-street at night). Ask of every roughness cue: *would the real version of THIS subject have this?* If not, drop it.

So the mandatory constants shrink to: **physically plausible light + falloff, true non-plastic skin, a real tonal curve (no clipping/crushing), capture texture appropriate to the medium, and physical consistency.** Grain amount, haze, wear, clutter, desaturation depth, and "available ugly light" are **dials, not laws** — set each by the subject. Clean, bright, and pristine, rendered truthfully, is still realism. A beautiful frame is only wrong when it's beautiful in the *AI* way (sculpted, plastic, over-clean in the render sense) — not when the real thing was simply clean and well-lit.

Also don't over-specify: only stack the detail layers the brief actually needs. Piling every texture, imperfection, and grade cue onto a simple frame is its own AI tell (and its own kind of over-production). Shortest prompt that fully specifies the real conditions wins.

## CAUGHT, NOT MADE — the anti-refinement law (for the naturalistic/gritty registers; scope it to the subject)

Real frames look *caught* — soft, slightly ugly, lit by whatever was in the room, cluttered with things no one chose, framed without care for beauty. **Refinement is the AI tell.** When polish fights roughness, roughness wins.

- **Softness over sharpness.** Not sharp. A gentle veil over everything; soft focus, low-contrast tonal texture, never clinical. Over-resolved/crunchy/hyper-detailed is the #1 AI tell.
- **A milky veil.** Faint haze/flare lifts blacks toward grey, mutes contrast, slightly washes the frame. Never clean, deep, or rich.
- **Flat, available, ugly light is allowed and often correct.** Overhead fluorescent, flat event ambient, sourceless front light — motivation-less "whatever was there" light reads more real than beautiful light.
- **Incidental clutter.** Signage, logos, notices, text-on-props, phones held up, bystanders facing away, merchandise, mess. AI invents clean empty worlds — fill scenes with un-chosen noise. (In-world text/signage is good; only overlaid captions/watermarks are banned.)
- **Un-designed framing.** Dull, centred, awkward, dead-space, heads-at-odd-heights all read real.
- **Life, not pose.** Mid-blink, mid-word, squint, flyaway hair, unflattering expression, slight slump.

Four "core DNA" tendencies are **options, not laws** — drop any when the scene is better served: shallow DOF (deep-focus is fine), off-centre (centred/awkward is fine), single motivated key (flat ambient is fine), single colour anchor (muted polychrome with nothing popping is fine). The only non-negotiables: **the grade lock, the skin truth, and this anti-refinement law.**

---

## FINAL GRADE LOCK — the output standard (identical on every frame)

Subject, location, era, mode, colour may change completely — **the finish never does.** One film's signature = consistent finish across wildly different content.

- **Muted, desaturated palette** — colour ~20–35% below "correct," unified, atmospheric, never vivid.
- **Low contrast; lifted, colour-holding blacks; soft-rolled highlights** — darkest point never crushes to 0 and holds shadow colour; brightest point (tube, window, sky) blooms and rolls off, never hard-clips. A gentle film S-curve with heavy midtones.
- **Protected skin** — warm, true, blood-bearing inside any grade. Never grey, plastic, or beauty-smoothed. Full pore/capillary/oil-sheen/stubble topography.
- **Colour in every shadow** — teal, green, amber, blue from the environment. No neutral or dead-black darkness.
- **One saturated anchor per frame** — a single element carries colour; everything else restrained.
- **Continuous fine organic film grain** — denser in shadows, faint halation on the brightest points, light atmospheric haze. Mandatory; it removes the digital-clean tell.
- **Shallow focus, soft atmospheric background, gentle organic bokeh** — nothing tack-sharp edge to edge.
- **Quiet, underplayed, lived-in finish** — observed, not produced.

If an output is more saturated, contrasty, sharp, clean, bright, or "impressive" than this — it missed. Pull it back until it sits inside the set unnoticed.

---

## SKIN TRUTH — the second pillar (equal weight to grade)

Real skin on film has four properties AI almost always misses. Apply all four, scaled to face size. The mechanism is **colour, sheen, and translucency — and all of it stays soft.** Present texture; never emphasise it. Over-sharpened skin is itself a tell.

1. **Uneven colour (mottling).** Never one even tone — warm flush on cheeks/nose/ears/knuckles; cool blue-grey under eyes, jaw, temples; thin yellow-green over bone; broken capillaries, blotches, razor rash, sun/age discolouration. *A face in one uniform smooth colour is the single biggest AI tell.*
2. **Specular breakup.** Oily highlights on nose bridge, forehead T-zone, tops of cheeks, lower lip; everything else matte. The highlight is fine, broken, rides the pore texture — never clean plastic gloss, never uniform sheen, never bone-dry.
3. **Subsurface scattering.** Light glows back warm — red-orange translucency in ears, nostril rims, thin eyelids, finger edges against backlight. Without it, skin reads as painted rubber even with correct texture.
4. **Surface topography, scaled to framing:**
   - **Close-up:** full topography — pores as micro-craters with shadow, wrinkles as channels, individual stubble/brow strands with root + shadow, vellus peach-fuzz catching rim light, chapped lips, wet meniscus on the lower lid.
   - **Medium:** pore texture present but soft; mottling + specular do the heavy lifting; stubble/brows read as mass, not strands; faint vellus rim.
   - **Wide/environmental:** pores will not and should not resolve — a real lens can't see them at distance. Realism = mottled uneven colour + broken specular + subsurface glow + wind/cold-flush + integrated grain. The failure at distance is a face too smooth/even/clean — kill it with colour and grain, not detail.

**Eyes, always:** wet, catching a single matched reflection of the key; faint red in the waterline/inner corner; thin wet highlight on the lower lid; irises slightly irregular — never two identical symmetric eyes.

The light and grain live **on** the skin: the surface carries the scene's colour and direction; grain sits on the skin, not floating above it.

---

## CORE DNA — every frame, every mode

**1. Tonal contract.** Lifted blacks (~3–10% luminance, never true 0, holding colour). Soft highlight rolloff (compress from ~85%; only tiny speculars may clip as points; skies/walls/windows/bulbs bloom and roll off, don't burn out). Low micro-contrast (gentle S-curve, log-like base; no HDR, no clarity, no local-contrast halos). Midtone density (weight in the middle; never thin/airy/crisp).

**2. Colour science.** Desaturate globally ~15–35%. Protect skin (warmth/blood survive a cold grade). Colour in the shadows (teal/green/blue/amber; gentle split-tone — shadows cool, skin/highlights warm, or motivated reverse). One saturated anchor (blood, garment, lamp, lips, glow) — never two competing.

**3. Light logic.** One motivated source (window, tube, lamp, sun, gel, screen, fire) — everything else falloff/bounce. No fill (let one side fall into coloured shadow; underexposure is correct). Real inverse-square falloff across subject and room. Practicals become soft dim organic bokeh, never bright hard discs.

**4. Lens & focus.** Shallow DOF default (thin plane, eyes sharpest; background atmospheric). Organic slightly-oval bokeh, never hard digital discs. Foreground occlusion where natural (shoulder, bar, railing, glass). Lens imperfection present (corner falloff, slight breathing, faint CA on hard speculars; glass is never optically perfect).

**5. Material truth.** The room is on every surface (subjects lit *by the scene*, not a clean separate key). Materials remember use (fabric weave/drape/wear, metal patina/scratches, wood grain/rot, stained aged walls; lived-in and slightly dirty).

**6. Composition.** Off-centre by default (thirds/off-axis; symmetry reserved and deliberate). Real-cinema devices (frame-within-frame, glass-reflection layering, low angle, foreground depth, motivated negative space, over-shoulder). Weighted placement with contact shadows — never floating on a backdrop.

**7. Texture & atmosphere.** Fine luminance-based grain (in shadows/midtones, finer in highlights; never a uniform digital overlay). Visible atmosphere (haze, humidity, dust, smoke, breath, depth fog; aerial-perspective falloff). Gentle halation/diffusion on the brightest highlights (warm interiors/period). Imperfection mandatory (scratch, smudge, lens fleck, slight gate weave).

---

## MODE ROUTER — select one by scene logic (all obey CORE DNA)

- **MODE A — Cold institutional / exterior.** Desaturated cyan/green/blue-grey; teal-green shadows; overhead fluorescent, overcast daylight, or cool soft window (low-drama, near-directionless but motivated). Skin cooled but warm in midtones. Use: institutional interiors, winter/overcast exteriors, alienation, dread, urban cold.
- **MODE B — Warm intimate interior.** Amber/tungsten warmth, desaturated, earthy; warm-brown-to-soft-green shadows; single warm practical/lamp/candle/window, soft directional falloff, visible halation. One warm/red anchor. Use: tenderness, intimacy, domestic/period, nostalgia, romance, warm night exteriors.
- **MODE C — Motivated colour chiaroscuro.** Near-black base + one saturated source (red, orange, sodium, green, screen-blue); deep shadows to near-black tinted by the source; one hard gelled/glowing source, extreme directionality, most of the frame in shadow. Use: tension, genre, danger, nightlife, the colour event at its limit.
- **MODE D — Natural daylight realism.** Naturalistic, only gently desaturated; true greens, true skin, held/bloomed sky; open shadows carrying cool sky-fill; real daylight (soft overcast, or hard sun with soft sky bounce as only fill); handheld immediacy. Use: daytime exteriors, action-drama, crowds, vérité — "really happened outside."
- **MODE E — Clean / high-key / commercial realism.** Bright even-to-soft light, minimal grade, low-to-no imposed grain, true (not muted) colour, pristine surfaces; soft open shadows still holding a hint of environmental colour. Still real, not rendered: true non-plastic skin with pore texture and broken specular, real softbox/daylight falloff and contact shadows, physically consistent reflections, a real tonal curve with gently held (never clipped) highlights, only the fine inherent capture texture. Use: modern clean interiors, beauty/skincare, product/tech/luxury, fashion e-comm, bright daylight portraits — any subject whose true state is clean and new. Grunge dials → near-zero; realism here comes from light physics, skin truth, and material accuracy, not from wear or haze.

---

## ANTI-AI-TELL PASS — run on every frame (eliminate each)

Symmetrical/averaged/"beautiful" faces → specific, asymmetric bone structure. Plastic/waxy/airbrushed/even skin → mottled colour + broken specular + subsurface + surface grain. Over-sharpened/crunchy/hyper-detailed → soften, low micro-contrast, no clarity. Clean/deep/rich art-directed grade → milky veil, lifted washed blacks, dirty desaturation. Sculpted single-key on everything → allow flat/ambient/overhead/ugly light. Designed hero composition → allow dull/centred/awkward/dead-space. Clean empty backgrounds → incidental clutter/signage/props/bystanders. Posed perfect expression → mid-blink/word/squint. Uniform front-to-back sharpness → only the focal plane sharp. Clipped highlights / crushed blacks → soft rolloff, lifted detail. Oversaturation/HDR/clarity halos → desaturate, flatten, kill halos. Neutral black/grey shadows → environmental colour in every dark area. Flat wraparound/beauty-dish light → one motivated direction + unlit side. Grainless atmosphere-free "digital" image → grain, haze, halation, lens imperfection. Floating/pasted subject → contact shadow, shared light, atmospheric depth. Mannequin hands / glowing-white teeth / doll eyes → correct anatomy, off-white teeth, wet asymmetric eyes with matched catchlight. Everything blooming / every surface glossy → only speculars/practicals bloom, gently. Over-rendered "epic" everything → restraint; most of the frame quiet.

If the frame looks attractive but slightly *too* clean, lit, sharp, or saturated — it's wrong. Pull it all back.

---

## PHYSICAL & ANATOMICAL CONSISTENCY PASS *(research-added)*

Beyond finish, the current generation of AI tells cluster into **physics, anatomy, and reflection consistency** (per AI-image-detection research). Add this pass on every realistic frame — these are what a viewer catches after the grade fools them:

- **Shadows agree with one light.** Every shadow falls the same direction, with matching softness/length, from the single motivated source. No sourceless shadows, no missing contact shadow under feet/objects, no two-direction shadows.
- **Reflections are consistent.** Mirrors, glasses/spectacle lenses, water, glossy floors, and **pupils** must reflect the actual scene and the actual key. Wrong/absent/garbled reflections are a top tell — state *"reflection consistent with the scene and key light."*
- **Anatomy counts.** Five fingers, correct limb joints and count, plausible teeth, ears, and hand poses (hands doing a real job, natural finger compression at contact). Watch multi-person frames for merged/extra limbs.
- **Contact & weight.** Subjects sit *in* the space — contact shadows, compressed cushions/fabric, weight on the load-bearing foot (never 50/50), objects resting not floating.
- **Material physics.** Cloth drapes and folds by gravity; liquid pours/pools plausibly; hair has weight and stray strands; smoke/steam disperses. No cloth/fluid behaving impossibly.
- **Scale & configuration.** Object sizes and spatial relationships are commonsense-plausible (door heights, cup vs hand, background architecture). No impossible object configs.
- **Text integrity.** In-world signage/labels use consistent glyphs (garbled text is a tell) — for hero type, render on Nano Banana Pro and quote the string (`references/text_rendering.md`).

Run it as a literal checklist: *shadows one-direction? reflections match? fingers/limbs correct? contact shadows present? materials obey gravity? scale sane? text legible?*

---

## PRACTICAL REALISM KEYWORD LAYERS *(research-added — stack, don't pile keywords)*

Realism is a *stack*, not the word "photorealistic." Layer, in natural language:
- **Capture medium (named).** Body + lens + aperture + stock/processing — e.g. *"shot on 35mm film, 50mm, f/2, Kodak Vision3 500T, pushed one stop, organic grain."* (Full stock library: `optics_grain_and_light.md`.)
- **Depth of field.** State f-stop and what's sharp vs soft — *"f/2 shallow, near eye sharpest, background dissolved."*
- **Micro-imperfections (≥2).** Motion blur on a non-hero element, corner lens softness, faint CA on a hard specular, dust in a light shaft, slight tilt, off-centre framing, smudge/scratch on glass.
- **Materials as tactile.** Not "a jacket" → *"weathered full-grain leather, cracked seams, visible grain."*
- **Anti-retouching negatives (these DO land in Nano Banana).** *"not airbrushed, no beauty filter, no smoothing, no HDR, no clarity, no oversharpening, no AI-render look."*
- **Motivated lighting phrase.** Name source + direction + quality + falloff side (not "cinematic lighting").

---

## ASPECT RATIO
Default **2.39:1** anamorphic scope. **1.85:1** or **~2.00:1** by scene logic. Never clean 16:9, square, or vertical unless the brief demands it. (Render 16:9 + crop if the tool won't do 2.39 natively.)

---

## PROMPT CONSTRUCTION — brief → frame

Front-load subject/action; back-load technical truth so the model treats it as recording conditions, not decoration:

`[Subject + specific asymmetric physical detail] · [action / micro-moment] · [location, lived-in, with wear] · [MODE: palette + single motivated source + direction + falloff] · [single saturated anchor, named] · [lens + shallow DOF + what's sharp / soft + foreground occlusion] · [skin/material truth] · [filmic tonal contract] · [grain + atmosphere + halation] · [aspect ratio] · clean frame, no text`

### THE SKIN TAIL — mandatory on any frame with a person (append verbatim, before the grade tail)

> *skin rendered as real skin on film, soft and low-contrast, never sharp or crunchy — uneven mottled colour with warm flush on the cheeks, nose, chin and ears, cool blue-grey under the eyes, pink-red eyelids and inner corners, broken capillaries and blotchy discolouration, never one even tone; broken slightly sweaty specular sheen with unflattering oily highlights on the nose bridge, forehead and tops of the cheeks and matte falloff elsewhere, never a uniform beauty glow; warm subsurface glow through the ears and the rim of the nose; wet asymmetric slightly reddened eyes with a single matched catchlight; film grain sitting on the skin surface; texture present but gentle and never emphasised [CLOSE/MEDIUM ONLY: soft pore texture, soft wrinkle channels, stubble and brows as soft mass not sharp strands, faint vellus rim, chapped lips] — never smooth, waxy, even-toned, sharpened, airbrushed, over-detailed or plastic.*

### THE GRADE TAIL — append verbatim to the end of every frame (constant across all outputs)

> *finished like a real film scan — soft and slightly hazy, never sharp or crunchy, low contrast with a faint milky veil lifting the blacks toward grey, muted slightly dirty desaturated palette (at most one quiet colour anchor, often none), soft highlight rolloff with no clipping, midtone density, warm true mottled skin never smooth or plastic, environmental colour in the shadows, continuous fine organic film grain denser in the shadows, faint dirty halation on the brightest points, atmospheric haze, gentle imperfect focus over an atmospheric background, available unsculpted light, incidental real-world clutter, quiet underplayed and undesigned — no HDR, no clarity, no oversharpening, no over-resolved detail, no oversaturation, no clean or art-directed look — indistinguishable from a frame pulled off a real production.*

### CLEAN-REGISTER GRADE TAIL — use INSTEAD of the above for clean/bright/new subjects (MODE E)

The default tail bakes in a "dirty film-scan" finish (milky veil, dirty desaturation, heavy grain). On a clean subject that fights the truth. Swap it for:

> *finished like a real professional photograph of a clean subject — true accurate colour (not muted or dirty), a natural tonal curve with softly held highlights and open shadows that keep detail and a hint of environmental colour, real non-plastic skin with pore-level texture and broken specular sheen, accurate lived-true material surfaces, physically consistent light, falloff, contact shadows and reflections, only the fine inherent capture texture — no heavy grain, no milky veil, no imposed haze; clean but never plastic, sharp only where the lens truly is but never over-sharpened, no HDR, no clarity halos, no beauty-smoothing, no AI-render gloss — indistinguishable from a real high-end photograph.*

Rule of thumb: **worn/night/naturalistic/gritty subject → default (film-scan) tail; clean/bright/new/product/beauty subject → clean-register tail.** Never both.

---

## WORKED EXAMPLES

**Mode C (motivated colour chiaroscuro):**
> *Teenage boy, dark curly hair, specific uneven features, faint acne texture and sweat sheen, fingertips just touching his chin · holding still, alert, half-lit · cluttered dim room, posters soft behind · MODE C: near-black base, one hard red practical raking from frame-right, left half of the face falling into deep red-black shadow, no fill · the red light is the single saturated anchor · 85mm, very shallow focus on the near eye, background dissolved into soft dim red bokeh · full skin topography, wet eyes, single red catchlight matching the source · lifted blacks holding colour, no clipped highlight, low micro-contrast · fine grain in the shadows · 2.39:1 · clean frame, no text.* [+ skin tail + grade tail]

**Mode A (cold institutional / exterior):**
> *Lean man, early 40s, thin face, real skin with stubble and pores, standing still, looking slightly off-camera · worn teal coat over a patterned shirt · empty seafront, derelict balconied buildings behind, overcast · MODE A: desaturated cyan-green grade, flat cool overcast daylight from a heavy sky as the only source, teal-green shadows · the coat's muted teal is the quiet anchor · 50mm, subject sharp, buildings soft and atmospheric with aerial-perspective falloff · skin cooled but blood present in midtones · lifted blacks, soft bloomed sky that doesn't clip, low contrast · fine grain, faint sea haze · 2.39:1 · clean frame, no text.* [+ skin tail + grade tail]

---

## OUTPUT CONTRACT
Deliver the frame only. No captions, watermarks, camera/lens names, or annotations in the image. No drawn letterbox bars (the aspect ratio is the crop). One clean still.

## EXECUTION RULE
Given any brief — a word, a name, an object, a feeling, a full scene — run the whole engine silently: select the mode, set the single motivated source, assign the one saturated anchor, apply the tonal contract and colour science, build skin and material truth, run the physical-consistency pass, compose off-centre with a real-cinema device, lay in grain and atmosphere, run the anti-AI-tell pass, append the tails. The user sees a frame that could cut into a real film without a visible seam.

---

## REFERENCE CANON (ground truth — external film stills the engine matches)
Laroy, Texas (supermarket — held fluorescent highlights, cool green cast, colour in shadow) · 28 Years Later (Highlands — daylight realism, held sky, blood as the one saturated event) · Deception (reclined, tartan — warm interior, flushed un-retouched skin, red anchor) · Deception (hands over eyes — restrained red-on-teal, full close-up topography) · Dogman (dog-show crowd — multi-subject naturalism, atmospheric falloff) · Dogman (teal coat, seafront — cold exterior, heavy teal grade) · Project Power (glowing capsule macro — near-black chiaroscuro, one colour event) · Project Power (red-gel CU — one hard motivated colour, pores/sweat intact) · Shirley (red lips, green window — vintage diffusion, halation, period softness) · The Blue Caftan (mustached CU — THE SKIN BENCHMARK) · The Goldfinch (boy behind glass — reflection layering, cool desaturated daylight) · The Goldfinch (couple smoking, night — warm practical bokeh, low-light faces).

---

## Sources
- **Frame Realism Engine** — Abdullah Imtiaz (uploaded source guide).
- [7 Prompt Keywords to Make Images Less Fake — Promptaa](https://promptaa.com/blog/prompt-key-words-to-make-images-less-fake-looking) · [Make AI Images Look Real — Upsampler](https://upsampler.com/blog/make-ai-images-look-real) · [Photorealistic AI prompts — Artsmart](https://artsmart.ai/blog/ai-image-prompts-photorealistic/)
- [Qualitative Failures of Image Generation Models (physics/anatomy tells) — arXiv 2304.06470](https://arxiv.org/pdf/2304.06470) · [Semantic Visual Anomaly Detection in AI Images — arXiv 2510.10231](https://arxiv.org/pdf/2510.10231) · [Distinguishing AI-Generated from Authentic Photographs — arXiv 2406.08651](https://arxiv.org/pdf/2406.08651)


<!-- ═══════ FILE: nano-banana-prompter/references/realism_and_ugc.md ═══════ -->

# Nano Banana — realism, anti-plastic skin & UGC

The flagship realism reference. Everything here exists to close the gap between *a nice AI image* and *a photograph that passes*. The core skill summarises this stack; this file is the full build, the templates, and the failure-mode repairs.

Cross-references, not repeated here: lens/grain/diffusion mechanics, halation, sensor signatures, and the editorial lighting registers → `references/optics_grain_and_light.md`; posing as physical instruction, three-plane depth, and the generate→audit→repair critique loop → `references/composition_posing_and_critique.md`; the real-frame override and night-physics doctrine → `references/tonal_families.md`; assembling a finished post around a realistic frame → `references/creative_posts_copy_type_layout.md`.

---

## The core thesis: realism is a stack, not a keyword

No single phrase carries realism. *"Photorealistic"*, *"8K"*, *"hyperrealistic"*, *"ultra-detailed"* — all of them produce the same over-clean AI render, because they describe a *quality target*, not a *physical scene*. The model already thinks it's being realistic; the word adds nothing.

What works is stacking four independent layers, every one of which a real camera and a real face impose on a real photograph. Miss a layer and the eye finds the tell.

1. **Skin** — texture the model wants to smooth away.
2. **Light direction** — a single sourced key with stated shadow consequences.
3. **Capture medium** — a named body, lens, aperture, and processing/stock.
4. **Micro-imperfection** — the accidents that prove a hand held a camera.

Build all four into every realism frame. The UGC five-stack (further down) is this same logic pushed harder — a deliberate downgrade of everything that makes a pro photo pro.

> **The two-sentence realism close** that anchors almost every frame in this file: *"A photograph, not a painting."* + *"not airbrushed, no beauty filter, no smoothing, no AI render look."* Both are **confirmed** to land — see the painterly-tell and anti-retouching notes below.

---

## Layer 1 — Skin (anti-plastic)

Plastic skin is the single most recognisable AI tell. The model's prior is a retouched beauty render: even tone, no pores, waxy highlight roll-off. Beat it by **stacking 2–3 concrete texture cues** — not all of them, which tips into grotesque — and closing with anti-retouching negatives.

Stack 2–3 from this menu; pick what's plausible for the face and the framing:

| Skin cue | What it fixes |
|---|---|
| **Visible pores** | the airbrushed plastic surface — the baseline cue |
| **Fine vellus hair** | the too-clean cheek/jaw edge; catches rim light realistically |
| **Subsurface scattering** | waxy, opaque skin — adds the real translucency of lit flesh |
| **T-zone sebum sheen** | the uniform matte mask; real skin is oilier down the nose/forehead |
| **Dry patches around the nostrils** | the uniform-perfect surface; a tiny real-skin flaw |
| **Faint freckling** | flat even tone — scatters the surface believably |
| **Small blemish near the jaw** | the flawless-model read; one real imperfection sells the rest |
| **Uneven skin tone** | the airbrushed colour-graded face; real skin mottles |
| **Faint redness on the cheekbones** | bloodless render skin; adds living circulation |
| **Individual strand hair detail** | helmet/merged hair; separates strands, kills the wig look |

**Close every portrait with the anti-retouching negatives:** *"not airbrushed, no beauty filter, no smoothing, no AI render look."* This is the **rare confirmed exception** to the rule that negative framing is unreliable in Nano Banana — anti-retouching negatives DO land in this model. Use them on every realism frame.

> **Paste-ready, balanced skin block:** *"visible pores across the nose and cheeks, fine vellus hair catching the light along the jaw, subsurface scattering in the ears and nostrils, a faint T-zone sheen, one small blemish near the jaw — not airbrushed, no beauty filter, no smoothing, no AI render look."*

**Don't over-stack.** All ten cues at once reads as diseased or special-effects. Two or three, chosen for the age and lighting, is the believable dose — and let Layer 3's grain do some of the texture work so you aren't asking skin to carry it alone.

---

## Layer 2 — Light direction

Plastic skin is half a *lighting* tell. *"Cinematic lighting"* is the #1 cause of generic output — it's a non-instruction the model satisfies with flat, flattering, sourceless frontal fill. Replace it with a **directional, sourced, single-key recipe**. Always name four things:

**source + direction + quality + falloff side.**

> *"Hard window key from camera-left, no fill, deep shadow on the right cheek."*
> *"Single bare bulb above and slightly behind, top-down, hard-edged, eye sockets in shadow."*
> *"Overcast north window, soft and directionless, gentle wraparound, no catchlight punch."*

### Shadow-consequence phrasing — FIELD-VALIDATED

Source-only language is not enough. The model re-keys a stated source back to its default flat frontal key unless you also state **what the shadows do**. The fix — **confirmed** in testing — is to state the source AND its shadow consequences in the same breath:

> *"Her left cheek in shadow, cast shadow running camera-left, wall brightest at the right edge."* — **confirmed** to enforce direction where source-only language failed.

Make shadow-consequence phrasing standard for **any** directional light. The pattern: name the source, then name (a) which part of the face/subject falls into shadow, (b) which direction the cast shadow travels, and (c) where the brightest point in the frame sits. Three consequences nail the direction the model otherwise discards.

| You wrote | The model did | Add this consequence |
|---|---|---|
| "hard key from camera-right" | flattering frontal key | *"the left cheek in shadow, cast shadow falling camera-left, brightest on the right jaw"* |
| "top-down hard light" | softened, lifted | *"eye sockets and under-nose in shadow, forehead and cheekbones hottest, neck dark"* |
| "backlit / rim from behind" | added a frontal fill | *"the face mostly in shadow, only a bright edge on the hair and shoulders, no front fill"* |

**High-ISO documentary night.** The most realistic night framing tested. Register: *"handheld available-light, ISO 6400, shadow noise, white balance drifting with the sources."* — **confirmed** the most convincingly real night register. Pair with the night-physics block in `references/tonal_families.md` (inverse-square falloff, rain only as backlit sparkle, a small hard blown hotspot rather than a soft glow) for any dark frame.

---

## Layer 3 — Capture medium

A real photograph was made by a specific machine. Name the **body + lens + aperture + processing/film stock** — the model carries each as a bundle of visual DNA. The deeper lens-character and grain library lives in `references/optics_grain_and_light.md`; this is the realism-critical subset.

Pick the register first — it sets which tells apply and what the whole frame should feel like:

| Register | Reach for | Reads as |
|---|---|---|
| **Phone UGC** | phone front/rear camera, ~f/1.78, HDR push, computational fill, over-sharpening | a real person's story post |
| **Pro digital** | Sony A7 IV / Fujifilm X-T5 + a named prime, stated aperture, clean profile | an editorial or commercial frame |
| **Film** | 35mm/medium format + a named stock (Portra 400, Cinestill 800T), organic grain | analog, nostalgic, warm |
| **Documentary night** | handheld available-light, ISO 6400, shadow noise, drifting white balance | photojournalism, unstaged |

### Phone-shot tells

The signature of a modern computational-photography phone — reach for these on any UGC, selfie, candid, or "shot on my phone" brief:

| Tell | Why it reads as a phone |
|---|---|
| **Slight HDR push** | the flattened-dynamic-range, everything-lifted look of phone HDR |
| **~f/1.78 fixed aperture** | phones don't stop down; the fixed fast aperture is a fingerprint |
| **Computational fill** | shadows machine-lifted, not optically filled — the giveaway of a phone, not a camera |
| **Mild over-sharpening** | the crunchy, haloed edge detail of phone processing |
| **Apple color-science green midtones** | the specific cool-green cast Apple pushes into midtones |
| **Portrait-mode cutout artifacts on hair** | the fake-bokeh edge failure where the subject mask clips stray hair |

> *"Shot on a phone front camera, ~f/1.78, slight HDR push, computational shadow fill, mild over-sharpening, Apple-green midtones, faint portrait-mode cutout artifacts on the flyaway hairs."*

### Film tells

When the brief wants analog rather than phone:

| Tell | Why it reads as film |
|---|---|
| **Organic grain, denser in shadows** | real film grain clumps in the shadows and thins in highlights — never a uniform overlay |
| **Halation on highlights** | the red-orange bloom hugging blown light sources (esp. tungsten on Cinestill) |
| **Colour shift in the shadows** | film crosstalk — shadows drift cool/green rather than staying neutral |
| **Dust in the corners** | physical dust/lint on the gate or scan, concentrated at the frame edges |

> *"Shot on 35mm film, organic grain denser in the shadows, faint halation on the window highlights, shadows drifting slightly green, a speck of dust in the corner."*

Grain lives **in** the image — clumpy, midtone-dense, absent in pure black, melting in the highlights — not a flat screen over the top. Never mix film-grain language with digital-sensor-noise language in the same frame; they're different textures (see `references/optics_grain_and_light.md` §8).

---

## Layer 4 — Micro-imperfection

The accidents that prove a fallible human held a real device. A flawless frame is an AI frame. Stack **at least two** — chosen so they fit the scene, never piled on:

- **Slight motion blur on a non-hero element** — a passing hand, hair, traffic behind; the hero stays sharp.
- **Lens distortion at the edges** — straight lines bowing toward the frame edge.
- **Chromatic aberration on high-contrast edges** — purple/green fringing where bright meets dark.
- **Uneven exposure** — a hot corner, a region clipping, not a perfectly metered frame.
- **Mild flare** — a soft veil or streak from a light just inside or outside the frame.
- **Dust in the light shaft** — motes catching a hard beam.
- **Slight tilt** — the horizon a degree or two off level.
- **Off-center framing** — the subject not centered, headroom uneven.
- **Stray hairs** — flyaways breaking the clean silhouette.
- **Fingerprints on the phone screen** — smears on a device in frame.
- **Smudges on a mirror** — streaks and water spots on a bathroom mirror.
- **Background clutter** — mail, a half-empty glass, a charging cable, a sticky note.

**Tie every flare and artifact to a physical cause.** A streak flare must come *from* a visible in-frame source; chromatic aberration sits *on* a real high-contrast edge. Detached, sourceless effects read as fake — the model will render an anamorphic streak floating in the middle of nowhere if you let it.

**Match the imperfection to the register.** A pro editorial frame earns a slight flare and edge softness, not fingerprints on a phone screen; a UGC selfie earns clutter, smudges, and a crooked frame, not a tasteful lens veil. Two well-chosen cues beat five generic ones — over-stacking imperfections is its own AI tell.

> *"A touch of motion blur on the hand reaching past, mild chromatic fringing on the window frame, the horizon tilted a degree, a charging cable and yesterday's mail on the counter behind."*

The **background-clutter ledger** is the highest-leverage imperfection for any domestic or candid frame — it does more for believability than any single skin cue. Name 3–6 specific objects that a real life leaves lying around: *"junk mail and a delivery box by the door, a half-empty water glass, a phone charger snaking across the table, a sticky note on the cabinet, a single sock on the floor."* Specific named objects beat *"some clutter"* every time.

---

## The UGC five-stack

UGC is the realism stack pushed to its conclusion: a **deliberate downgrade of every dimension that makes a pro photo pro**. The whole point is to remove competence. Build across five axes.

**FIELD-VALIDATED — fully confirmed.** In a 12-test round, the bathroom-selfie UGC test produced the **most convincingly real output of the entire round**: no-makeup skin with a visible blemish, mixed fluorescent/warm light, a full clutter ledger, steam on the mirror. The five-stack is confirmed as the highest-leverage realism recipe in the skill.

| Axis | Downgrade to |
|---|---|
| **Capture** | phone body + 9:16 + HDR push + over-sharpening + computational fill |
| **Light** | mixed temperature, multiple bulb types, no fill |
| **Composition** | arm's length, slight downward tilt, off-center, top of head almost clipping, phone visible |
| **Subject** | mid-laugh / mid-talk, eyes off the lens, hair out of place, worn-today wardrobe with a stain or wrinkle |
| **Context** | 3–6 real background objects, slight clutter, steam on a mirror, mail on the counter |

**Close with the confirmed UGC closer:** *"not staged, not retouched, casual close-friends story vibe, looks like a real Tuesday morning."*

> **Full bathroom-selfie reference prompt (the confirmed winner):**
> *"A young woman taking a selfie in a small bathroom, front camera at arm's length, no mirror in frame, 9:16, slight HDR push and mild over-sharpening. No makeup — visible pores, a small blemish near the jaw, faint redness on the cheekbones, T-zone sheen, stray hairs out of place. Mixed light: cool fluorescent overhead fighting a warm vanity bulb, no fill, uneven exposure on the forehead. She's mid-laugh, eyes just off the lens, an old worn t-shirt with a faint wrinkle. On the counter and ledge: a toothbrush, a half-squeezed tube, yesterday's mail, a hair tie; faint steam fogging the lower mirror. Not staged, not retouched, casual close-friends story vibe, looks like a real Tuesday morning. A photograph, not a painting."*

> **Mirror-selfie variant (phone visible) — different geometry, same downgrade:**
> *"Mirror selfie, phone visible held across the chest, the front camera reflected in a smudged full-length mirror, 9:16, HDR push. A man in a creased band tee and gym shorts, mid-step into frame, eyes on the phone screen not the lens, hair flat on one side. Mixed light: a warm bedside lamp behind, cool daylight from a window to the right, no fill. Mirror smudged with fingerprints and a water spot in the corner; on the floor and bed behind — a laundry pile, a charging cable, a half-open backpack, a coffee mug. Not staged, not retouched, casual close-friends story vibe. A photograph, not a painting."*

**The styled-ad trap.** The fastest way to wreck UGC is to leave any pro signal in the prompt. Strip *"lifestyle photography"*, *"clean"*, *"professional"*, *"studio"*, *"cinematic"*. If the background is tidy, the light is even, and the composition is balanced, you have a styled ad — not UGC. Add clutter, mix the colour temperatures, knock the framing off-center.

---

## Phone-shot geometry — selfie vs mirror-selfie

**FIELD-VALIDATED nuance.** *"Holding the phone at arm's length"* in a **bathroom-with-mirror context renders as a MIRROR selfie** — the model sees a mirror in the scene and assumes the shot is taken in it. Confirmed. The geometry of a front-camera selfie and a mirror selfie are completely different (where the phone is, where the eyeline goes, whether the phone is visible), so **specify it explicitly**:

| You want | Write exactly |
|---|---|
| **Front-camera selfie** (phone held out, face direct, phone not visible) | *"front camera at arm's length, no mirror in frame"* |
| **Mirror selfie** (phone visible, shooting the reflection, arm across the body) | *"mirror selfie, phone visible"* |

Both geometries are valid UGC; the failure is leaving it ambiguous in a room that has a mirror. State it every time the scene contains a reflective surface.

Two more confirmed phone-geometry cautions, carried from the night/realism rounds:
- **"Back-turned" / "facing away" sometimes flips** to facing camera. Write *"facing away, face not visible."*
- **The model invents legible background signage unprompted** (a self-labeled storefront, a deli sign). For a clean frame add *"no readable text in the background."*

---

## JSON realism template

For structured, repeatable realism briefs — or when handing a prompt to a pipeline — a keyed block keeps every layer accounted for. Nano Banana reads structured prompts well; the keys force you not to drop a layer. Fill each, then optionally flatten to prose.

```json
{
  "subject": "woman in her early 30s, seated at a kitchen table, mid-conversation, looking slightly off-lens",
  "skin": "visible pores, fine vellus hair along the jaw, subsurface scattering in the ears, faint redness on the cheekbones, one small blemish near the jaw; not airbrushed, no beauty filter, no smoothing, no AI render look",
  "light": "soft overcast window from camera-left as the single key, no fill; right cheek in shadow, cast shadow running camera-left, the wall brightest at the right edge",
  "capture": "shot on a Fujifilm X-T5, 35mm f/1.4, processed like Kodak Portra 400 — organic grain denser in the shadows, faint halation on the window highlights",
  "imperfection": "slight tilt to the horizon, off-center framing with the subject left of center, a half-empty mug and a charging cable on the table behind, mild chromatic fringing on the window frame",
  "negatives": "not airbrushed, no beauty filter, no smoothing, no AI render look; a photograph, not a painting",
  "aspect_ratio": "4:5"
}
```

Keep the keys when the brief is technical or you're iterating one variable at a time; flatten to a director's-brief paragraph when the model seems to over-literalise the structure. Either way, every one of the four layers must be present.

---

## Age-specific skin language

Skin reads true only when its cues match the age. A 20-something with deep nasolabial folds reads as wrong; a 60-year-old with poreless even skin reads as AI. Match the cues to the decade.

| Age | What reads true |
|---|---|
| **Child (3–10)** | smooth fine skin but **not** plastic — soft vellus down on the cheeks, a slight flush, maybe a scrape or freckles; rounded cheeks, no defined structure; never airbrush a child into a doll |
| **Teen (13–18)** | active sebaceous skin — T-zone shine, the odd blemish or healing spot, slightly uneven tone, faint pore visibility on the nose; smooth but alive |
| **20s** | clear, elastic, fine pores; subtle texture on the nose; no static lines, but expression lines appear *only* while expressing; even, healthy tone |
| **30s** | first fine lines at the outer eye and forehead **when expressing**, faint at rest; pores a touch more visible; early loss of the dewy plumpness; maybe faint sun freckling |
| **40s** | settled fine lines around eyes and mouth at rest, beginning nasolabial folds, slightly drier surface, uneven pigment patches, first slackening at the jaw; pores clearly visible |
| **50s** | etched expression lines, visible crow's feet, forehead creases, looser skin along the jaw and neck, age spots / sun damage on cheeks and hands, drier matte texture, thinning lip border |
| **60s+** | deep static wrinkles, crepey texture on the eyelids/neck/hands, marked elasticity loss and sagging, prominent age spots, visible veins, thinner translucent skin, sparse/grey brows |
| **Elderly (80+)** | deeply creased crepey skin, pronounced sagging and hollows, heavy mottling and liver spots, translucent papery surface over visible tendons and veins, soft sparse hair; dignity, not caricature |

Cumulative tells that scale with age: **sun damage and pigmentation** increase; **elasticity and plumpness** decrease; **surface oil** trends from oily (teen) toward dry (elderly); **static lines** (visible at rest) replace dynamic ones (visible only on expression). State the decade and pick the two or three cues that match — don't paste a 60s ledger onto a 30s face.

---

## Worked realism frames (paste-ready, by register)

Full four-layer prompts you can adapt. Each names skin + light (with shadow consequence) + capture + imperfection, and closes with the confirmed two-sentence realism block.

**Pro editorial portrait — 40s, hard window key.**
> *"A man in his mid-40s at a window, three-quarter turn toward the light. Skin: visible pores, settled fine lines at the outer eyes and forehead at rest, slightly dry matte surface, faint uneven pigment on the cheeks, stubble catching the light. Single hard window key from camera-left, no fill — the right side of his face in shadow, cast shadow running camera-right, the wall brightest at the left edge. Shot on a Sony A7 IV, 85mm f/1.4, clean profile. Mild chromatic fringing on the bright window frame, a degree of tilt, off-center to the left. Not airbrushed, no beauty filter, no smoothing, no AI render look. A photograph, not a painting."*

**Film register — golden-hour candid, 20s.**
> *"A woman in her late 20s on a stoop at golden hour, mid-laugh, looking off to the side. Skin: clear elastic skin with fine pores, a faint flush, light freckling across the nose, expression lines only where she's smiling. Warm low backlight from camera-right rimming her hair, soft bounce off the pavement filling the front — her near side in gentle shadow, long cast shadow stretching camera-left. Shot on 35mm Kodak Portra 400, organic grain denser in the shadows, faint halation on the rim light, a speck of dust in the corner. Slight motion blur on a passer-by behind. Not airbrushed, no beauty filter, no smoothing. A photograph, not a painting."*

**Documentary night — high-ISO available light.**
> *"A street vendor under a single sodium streetlamp at night, facing away, face not visible, working at the cart. Handheld available-light, ISO 6400, visible shadow noise, white balance drifting warm with the lamp and cool at the edges. The light pool ends a few meters from the lamp, the rest of the frame fully black; a small hard blown hotspot on the cart's metal with tight halation, not a wide soft glow. Broken specular streaks on the wet asphalt, not an even wash. Slight motion blur on his hands. Shot like photojournalism — a photograph, not a painting, grain and shadow noise throughout. No readable text in the background."*

---

## Realism failure-mode fixes

Symptom → Fix. The repairs not already obvious from the layers above.

| Symptom | Fix |
|---|---|
| **Plastic / airbrushed / doll skin** | Stack 2–3 Layer-1 texture cues (pores + vellus hair + subsurface scattering), close with the anti-retouching negatives, and let grain (Layer 3) carry some texture. Don't rely on a single cue. |
| **UGC looks like a styled ad** | Strip every pro signal (*"lifestyle"*, *"clean"*, *"studio"*, *"cinematic"*). Downgrade all five UGC axes — mixed-temp light, off-center frame, 3–6 clutter objects — and close with *"not staged, not retouched… real Tuesday morning."* |
| **Painterly / illustrated look** | Append *"A photograph, not a painting"* **and** grain + shadow-noise language. **Confirmed** to kill the painterly tell — include both in any realism frame. |
| **Wrong selfie geometry** (mirror selfie when you wanted a direct selfie, or vice versa) | Specify explicitly: *"front camera at arm's length, no mirror in frame"* vs *"mirror selfie, phone visible."* Never leave it ambiguous in a room with a mirror. |
| **Over-even / flat frontal light** | Replace *"cinematic lighting"* with a single sourced key, then add shadow-consequence phrasing — which cheek is in shadow, which way the cast shadow runs, where the frame is brightest. **Confirmed** as the direction fix. |
| **Flawless, accident-free frame** | Stack at least two Layer-4 micro-imperfections, each tied to a physical cause (motion blur on a non-hero element, CA on a real high-contrast edge, a tilt, real clutter). |
| **Age mismatch** (lines on a 20s face, or poreless 60s skin) | Match cues to the decade table — static lines and sun damage scale up, elasticity and oil scale down. |
| **Night frame looks painted / glowy** | Use the high-ISO documentary register + the night-physics block from `references/tonal_families.md` — inverse-square falloff, rain only as backlit sparkle, a small hard blown hotspot, not a wide soft glow. |

---

## Quick realism build order

A fast pass for any "make it look real / not look AI" brief:

1. **Pick the register** — pro photo, phone UGC, film, or documentary night.
2. **Skin** — 2–3 age-matched cues + anti-retouching negatives.
3. **Light** — one named source + direction + quality + falloff, then shadow-consequence phrasing.
4. **Capture** — body + lens + aperture + stock/processing; phone tells for UGC, film tells for analog.
5. **Imperfection** — ≥2 cues, each with a physical cause.
6. **For UGC** — downgrade all five axes, fix the selfie geometry, add the closer.
7. **Close** — *"A photograph, not a painting"* + the anti-retouching negatives.
8. **Audit → repair** — run the model-as-critic turn from `references/composition_posing_and_critique.md`, fix the top 2–3 tells, *"keep everything else exactly the same."*


<!-- ═══════ FILE: nano-banana-prompter/references/realism_physics_deep.md ═══════ -->

# Nano Banana — realism physics deep layer (why photos read as real)

> **STATUS: UNVALIDATED (researched 2026-07-09, agent research round).** Builds UNDER `references/frame_realism_engine.md` and `references/realism_and_ugc.md` — those files give the enforcement stacks; this file gives the physics that explains them and the next tier of tells. Use when a frame still reads AI after the standard stacks.
>
> **Master insight from detection research:** single-subject rendering (skin, faces) has passed the uncanny valley — humans now judge AI faces real MORE often than real faces. The remaining battleground is **global consistency**: one exposure decision, one shadow geometry, disagreeing light colors, velocity-consistent blur, caused clutter. The highest-leverage prompting move is stating the *capture decision and its cost* — "exposed for X, so Y is sacrificed" — not stacking quality adjectives.

## 1. Dynamic range & exposure behavior
**Physics:** film has a shoulder — highlights compress gradually; digital clips to white instantly at full-well. Negative film is exposed for shadows; digital for highlights. A real photo always *sacrifices* one end of the tonal range.
**AI failure:** "HDR-flat" — everything visible everywhere, midtone-heavy, window views impossibly balanced against interiors.
**Prompt:** *"single correct exposure, not HDR — exposed for the subject's skin, so the window behind blows out to featureless white with a soft bloom at the clipping edge"* · *"deep shadows crush to near-black with visible noise in the last stop"* · *"gentle film-like highlight rolloff — highlights compress and desaturate before clipping."*
**Verify:** brightest window/sky should hit near-pure white; shadows under furniture should lose detail. If you can read both the lamp filament and the dark corner, it's still AI.

## 2. Optical physics tells
**Physics:** focus is a (slightly curved) plane; blur grows nonlinearly and asymmetrically with distance from it (≈2× more DOF behind than in front). Off-axis vignetting squeezes bokeh into cat-eye ellipses that swirl at frame edges; aspherical molding leaves onion-ring texture in bokeh discs; no fast lens is corner-sharp wide open.
**AI failure:** blur-as-filter — uniform Gaussian background, circular bokeh everywhere, sharp corners at f/1.8, nose-to-ear all sharp at portrait distance.
**Prompt:** *"85mm f/1.8 — focus on the near eye, the far eye and ear drift measurably soft"* · *"background blur increases progressively with distance, midground half-melted"* · *"bokeh highlights cat-eye shaped near the frame edges, faint onion-ring texture, slight green-magenta fringing"* · *"corners softer and darker than center."*
**Verify:** round bokeh discs at the corners = fake; ellipses pointing at frame center = real. Both eyes identically sharp at a 3/4 angle at f/1.4 = impossible.

## 3. Color science
**Physics:** real scenes almost never have one illuminant — tungsten + window + fluorescent coexist, and white balance can only be right for one; the rest cast orange, blue, or green. Skin shifts waxy-green under spiky LED/fluorescent spectra, amber under tungsten, cyan in open shade. Detection studies confirm: real photos have broad smooth histograms; generated ones are peaky, over-harmonized, higher-saturation.
**AI failure:** one tasteful global grade over everything — every source the same temperature, every object's color "belonging" to the palette. Real photos have arguments between sources; AI photos have consensus.
**Prompt:** *"mixed lighting: white balance set for the window daylight on her face, so the tungsten lamp side shifts warm orange and the hallway fluorescent leaks slightly green"* · *"colors NOT harmonized — the red plastic chair clashes with the scene's palette"* · *"faint overall green cast typical of indoor phone photos, uncorrected."*
**Verify:** neutral surfaces in different parts of the frame should read different temperatures; at least one object should be chromatically rude.

## 4. Perceptual detection tells (what viewers actually use)
**Findings:** humans run ~60–64% detection accuracy; the cues used are hands/fingers, garbled text, too-smooth texture, foreground/background lighting mismatch, floating objects, excess bilateral symmetry. Forensics adds: all cast-shadow lines must intersect at one light source (AI images fail this); reflections must show the scene from the mirror's viewpoint.
**AI failure:** the residual tells are RELATIONAL — disagreeing shadow directions, reflections that don't match, text squiggles, matched earrings/collars, statistically too-clean texture.
**Prompt:** *"all shadows converge on a single sun position, low and camera-left; every object's shadow agrees"* · *"the mirror reflection shows the scene from the mirror's viewpoint, slightly darker and lower-contrast than the direct view"* · *"asymmetry everywhere: one collar point higher, one eye slightly narrower, hair parts unevenly"* · *"any visible text is short, real, legible — or absent."*
**Verify:** trace shadow tips through casters — one light? Read all text. Compare left/right earrings. Zoom on repeating texture (brick, fabric, foliage) for tiling.

## 5. Motion & time in a still
**Physics:** shutter is an integration window — each element blurs proportionally to its velocity. 1/60s: a gesturing hand smears, the room stays sharp. 1/2000s: water freezes to glass beads. Flash + dragged shutter = frozen flash-lit subject + ambient smear (party/wedding signature). Rolling shutter skews fast horizontal movers.
**AI failure:** temporally dead frames — everything frozen at infinite shutter, or decorative uniform "motion blur" painted on. A dancing crowd with every hand sharp reads synthetic.
**Prompt:** *"shot at 1/30s: her face sharp because she paused, her gesturing hand a translucent smear, a walker behind her a ghost streak; the room tack sharp"* · *"on-camera flash at 1/8s dragged shutter: subject frozen and bright, background lights smearing into warm streaks"*.
**Verify:** ask "what shutter speed was this?" — one answer must fit every element; all fast movers share one blur length, static elements have zero.

## 6. Environmental physics
**Physics:** contrast decays exponentially with distance (Koschmieder) — far objects lose contrast, shift toward sky hue/luminance. Shadow softness = source angular size; shadow edges sharpen toward the contact point and soften with distance from the caster. Every grounded object has a tight dark AO contact shadow. Wet surfaces: water fills micro-roughness → mirror speculars of actual scene lights + darker, more saturated surface.
**AI failure:** full-contrast backgrounds to the horizon; uniform shadow softness along their whole length; floating objects with no contact shadow; "wet" highlights without darkening or without reflections matching real lights.
**Prompt:** *"aerial perspective: each successive block loses contrast and shifts pale blue-grey"* · *"hard shadows razor-sharp at the foot, progressively softer toward the far end"* · *"overcast: no directional shadow edges, only dark occlusion pockets where surfaces meet"* · *"wet street darker and more saturated than dry, with elongated vertical mirror streaks of every sign and headlight, aligned to each source."*
**Verify:** foreground vs background contrast identical = fake; trace one long shadow for edge-sharpening; check under every object for the contact line; match each wet-street streak to a visible source.

## 7. Entropy & caused clutter
**Findings:** real scenes obey 1/f² spectral statistics with true high-frequency randomness; real clutter follows scene grammar — objects anchored to surfaces, clustered by activity, showing wear and mid-task history. Every placement has a *because*.
**AI failure:** decorative clutter — evenly distributed, all facing camera, nothing partially used, no occlusion stacks, near-identical repeated filler, "messy" in a suspiciously balanced way.
**Prompt:** *"the desk shows evidence of use, not staging: a half-empty mug with a ring stain, cables crossing at odd angles, papers overlapping and running off-frame, one drawer not fully closed"* · *"objects occlude each other; several items cut off by the frame edge; nothing centered or evenly spaced"* · *"clutter follows use: dense within arm's reach of the chair, sparse in corners"* · *"one thing mid-task: a jacket over the chair back, a sandwich with a bite gone."*
**Verify:** ask "who put that there and why?" of five random objects; spacing should be clumpy (clusters + gaps), not even; some objects must be partially hidden; no two near-identical mugs/plants/faces.

## Quick audit order (run after generating any realism frame)
1. Exposure sacrifice present? (something clipped or crushed)
2. One shadow geometry? (trace three shadows)
3. Two+ light temperatures arguing?
4. Blur velocity-consistent?
5. Focus a plane, bokeh vignetted at edges?
6. Contact shadows under everything?
7. Clutter caused, asymmetric, occluding?
8. Text real, hands right, symmetry broken?

*Cross-refs: `references/frame_realism_engine.md` (enforcement layer — use its tails verbatim), `references/realism_and_ugc.md` (phone/UGC register), `references/optics_grain_and_light.md` (grain/halation/lens character), `references/composition_posing_and_critique.md` (audit loop). Sources incl. Psychological Science "AI Hyperrealism" (Miller et al.), PNAS on synthetic faces, Content Authenticity Initiative shadow forensics, arXiv spectral-detection papers (CoDA, CHROMA), Koschmieder atmospheric model, SCEGRAM scene-grammar database, ASC/Photography Life exposure references.*


<!-- ═══════ FILE: nano-banana-prompter/references/optics_grain_and_light.md ═══════ -->

# Nano Banana — Optics, grain, and light (the deep catalogue)

The texture of a real image comes from physical causes: a particular lens bends light a particular way, a film stock clumps grain a particular way, a sensor clips highlights a particular way. Name the cause and the model renders the effect. Name a vague adjective (*"cinematic," "vintage," "moody"*) and it averages.

**The governing rule for this whole file:** *one light idea + one stock/grain + one grade per image* — and **every artifact needs a physical cause.** A flare must come from a source in frame. Halation must hug a blown highlight. Grain must sit in the emulsion. Stack three grades or invent a sourceless flare and the frame reads as a render.

Cross-references: tonal families and the real-frame / night-physics doctrines → `references/tonal_families.md`; named film looks and colorist techniques → `references/film_look_references.md`; the four creative-director levers and the basic stock/grade tables → `references/creative_director_controls.md`; realism stack and UGC capture tells → `references/realism_and_ugc.md`.

**Contents:** 1 Lens character · 2 Focal-length psychology · 3 Diffusion & lens effects · 4 Film-grain library · 5 Grain rules · 6 Fashion/editorial lighting · 7 The extended grade board · 8 Camera-sensor signatures · 9 Four decoded editorial looks.

---

## 1. Lens-by-lens character

Glass has a fingerprint — how it renders bokeh, flare, edges, and falloff. Name the lens *behavior*, not just the focal length.

| Lens | Signature | Paste phrase |
|---|---|---|
| Vintage glass (Super-Takumar, old Leica) | warm low-contrast rendering, gentle veiling flare, soft corners, painterly falloff | *"shot on vintage glass — warm, slightly low-contrast, soft corners, gentle veiling flare wide open"* |
| Helios 44-2 | swirly cat's-eye bokeh spinning around the subject, low contrast | *"Helios swirl bokeh — the out-of-focus background swirling around the subject, oval cat's-eye highlights, low contrast"* |
| Anamorphic | horizontal oval bokeh, a single horizontal blue streak flare, wide squeezed field | *"anamorphic look — oval vertical bokeh, a horizontal blue lens-flare streak from the in-frame light, wide cinematic field"* |
| Tilt-shift | a thin slice of focus with miniaturized blur above and below, perspective control | *"tilt-shift — a narrow plane of focus, exaggerated blur top and bottom, miniature-diorama feel"* |
| Petzval / swirl portrait | razor-sharp center, aggressively swirling edge bokeh | *"Petzval portrait lens — sharp center, dramatic swirling edge bokeh"* |
| Modern clinical prime (Zeiss Otus, Sony GM) | edge-to-edge sharpness, neutral high contrast, clean circular bokeh, no flare | *"modern clinical prime — edge-to-edge sharp, neutral contrast, clean rounded bokeh, no flare"* |
| Lensbaby / freelens | one sharp sweet-spot, the rest smeared into blur and light leak | *"freelensed — a single sharp sweet-spot, the rest smearing into blur with a light leak"* |

**Field note (Round 1):** anamorphic streak flares render but can look *detached* — always tie the streak to a visible in-frame source (*"the blue streak coming from the headlights"*). Confirmed in Round 2: the streak renders correctly when written as coming **from** the in-frame light.

---

## 2. Focal-length psychology

Focal length is a feeling, not just a field of view. It sets perspective compression, how close the camera feels, and the emotional read.

| Focal length | Perspective | Subject distance / feel |
|---|---|---|
| **16mm** | extreme wide, strong barrel distortion, everything deep-focus | very close, immersive, distorting — vertigo, chaos, environment swallows subject |
| **24mm** | wide, mild distortion, expansive | close, environmental — subject-in-world, energetic, documentary |
| **35mm** | natural-wide, slight context | the reportage standard — present but not intrusive, "you are there" |
| **50mm** | human-eye normal, no distortion | natural conversational distance — neutral, honest, classic |
| **85mm** | mild compression, flattering | a step back, intimate-but-respectful — the portrait sweet spot, soft separation |
| **135mm** | strong compression, background pulled close | far, isolating — elegant compression, creamy separation, fashion |
| **200mm** | heavy compression, flattened planes | very far, voyeuristic — stacked layers, telephoto candid, sports/paparazzi |

**The dial:** wider = closer, more distorted, more environment, more energy. Longer = farther, flatter, more isolated, more composed. *"Shot on an 85mm at f/2"* tells the model distance, compression, and separation in four words.

**Field note (Round 5):** *"fisheye + strong barrel distortion"* can produce a full **circular** fisheye porthole. For rectilinear wide coverage write *"full-frame fisheye, subtle barrel, no circular vignette."*

---

## 3. Lens effects & diffusion filtration

Diffusion filters bloom highlights and lower contrast *optically* — the cinema "glow" that isn't a soft-focus blur. Each needs naming by product or behavior.

| Effect | What it does | When / why | Paste phrase |
|---|---|---|---|
| Black Pro-Mist 1/8 | subtle highlight bloom, slightly lifted blacks, halation around lights | the default modern-cinema "expensive" texture, barely there | *"Black Pro-Mist 1/8 — gentle highlight bloom, slightly lifted blacks, a faint halo on the practicals"* |
| Black Pro-Mist 1/4 | stronger bloom and milkiness, obvious halation | heavier mood, night exteriors with practicals, dreamier | *"Black Pro-Mist 1/4 — pronounced highlight bloom and milky lifted shadows, clear halation on light sources"* |
| Glimmerglass | softens skin texture, adds a pearlescent sheen to highlights | beauty and glamour — flatters skin without killing detail | *"Glimmerglass diffusion — softened skin, a pearlescent glow on the highlights"* |
| Ghosting / internal reflection | a faint secondary image of a bright source | gritty realism, anamorphic night, lo-fi | *"faint lens ghosting — a secondary reflection of the bright sign offset from the source"* |
| Chromatic aberration | red/cyan fringing on high-contrast edges | a lens imperfection that reads as real capture; UGC and vintage | *"slight chromatic aberration — red-cyan color fringing on the high-contrast edges"* |
| Veiling flare | a low-contrast wash when a source hits the front element | sun-in-frame, backlit, nostalgic | *"veiling flare — a hazy low-contrast wash where the sun catches the lens"* |

**Why filtration, not blur:** diffusion blooms the *highlights* and lifts the *blacks* while keeping the subject sharp — soft-focus blurs the whole image. They read completely differently. Say *"diffusion,"* not *"soft."*

---

## 4. Film-grain library by stock

Grain is not one texture. Each stock clumps differently, sits in different tonal zones, and carries its own color behavior. Name the stock.

| Stock | Grain character | Color / extras |
|---|---|---|
| **Kodak Vision3 (250D / 500T)** | fine, organic, modern cinema grain, denser in shadow | clean neutral color, gentle highlight rolloff — the contemporary film-look default |
| **Kodak Portra 400** | very fine, soft grain | warm pastel skin, low contrast, forgiving — the portrait/wedding classic |
| **Cinestill 800T** | moderate grain | tungsten-balanced, and its signature: **red halation** bleeding around every bright light, cyan shadows |
| **Pushed B&W — Tri-X / Delta 3200** | coarse, gritty, chunky grain, very visible in midtones | high contrast, deep blacks — photojournalism, raw documentary |
| **Super 8** | heavy grain, visible gate weave, slight frame jitter | warm faded color, soft, light leaks — home-movie nostalgia |
| **VHS** | not film grain — scanlines, chroma bleed, tracking noise, smear | low resolution, oversaturated bleeding color, timestamp-era texture |
| **Digital sensor noise (high ISO)** | fine, even, *luminance + chroma speckle*, no clumping | colored noise in the shadows, no halation — the modern low-light look |

**The selection rule:** match the stock to the era and mood. Portra for warm flattering people; Cinestill for neon night; Tri-X pushed for gritty reportage; Super 8 for memory; Vision3 for "just looks like a movie." **One stock per frame.**

---

## 5. Grain rules (field-validated)

Grain is where AT realism quietly fails. Get these physics right and the frame stops looking rendered.

- **Grain lives IN the image, not on top of it.** It's part of the emulsion, not a transparent overlay. Write *"grain in the image, part of the photograph"* — not *"add a grain layer."*
- **Grain is clumpy and midtone-dense.** It clusters most in the midtones and shadows.
- **Grain is ABSENT in pure black.** Deep shadow has no grain because there's no exposed silver there. State *"grain absent in the pure blacks."*
- **Grain melts in the highlights.** Bright, near-blown areas wash the grain out.
- **Halation is a red-orange bloom hugging blown sources ONLY.** It rings the edges of a *blown-out* light — a streetlight, a window, a bare bulb. It does not float, and it does not appear where there's no clipped highlight. *"Red-orange halation hugging the blown highlights only."*
- **Film grain and digital sensor noise are DIFFERENT textures — never mix their language.** Film grain = clumpy, organic, silver. Digital noise = fine, even, colored speckle with no clumping and no halation. Pick one vocabulary per frame. Asking for *"film grain and digital sensor noise"* together produces an incoherent texture.

**The diagnostic:** if grain appears evenly across pure black, floats as a flat layer, or comes with halation on a source that isn't blown out — it reads as fake. Tie every grain and bloom artifact to its physical cause.

---

## 6. Fashion / editorial lighting registers

Each is a short recipe — source + quality + the look it produces. Name source, direction, quality, and falloff (the SKILL.md light rule), and remember the field finding: state direction as a **shadow consequence**, not just a source, or the model re-keys to a flattering frontal.

**Direct on-camera flash.** Hard frontal light from the lens axis — flat on the face, a hard-edged shadow stamped on the wall behind, slight overexposure on the nearest planes, fast falloff into black. *"Direct on-camera flash — flat hard frontal light, a crisp shadow on the wall behind her, hot forehead, background falling to black."* The snapshot/Terry-Richardson register.

**Ring flash.** A shadowless wraparound from a ring around the lens — a telltale **circular catchlight** in the eyes, a thin even shadow halo around the subject, glossy skin. *"Ring-flash beauty light — even shadowless wraparound, a ring catchlight in the eyes, a faint shadow halo behind."*

**LED tube / RGB practical.** A long soft source held to one side, or a colored tube laid into frame as a practical — a soft directional gradient across the subject, often two color temperatures. *"A cool LED tube from camera-left raking across her, warm practical behind — soft color-temperature split."*

**Softbox three-point.** Soft key, gentle fill, hair/rim light — the clean commercial standard (the *opposite* of the real-frame register; use deliberately). *"Soft key from camera-left, low fill, a hair light separating her from the grey seamless."*

**Night-practical mix.** Available sources only — a shop window, a sign, a passing headlight — at mixed temperatures, hard falloff, contaminated shadows. Pair with the night-physics block. *"Lit only by a sodium street lamp and a cyan shop sign, mixed temperatures, hard falloff, shadows contaminated by the sign color."*

**Hard sun + bounce.** Direct midday sun as a hard key with a single bounce filling the shadow side — high-contrast, crisp, editorial-outdoor. *"Hard noon sun as the key, one silver bounce opening the shadow side, crisp high-contrast."*

---

## 7. The extended grade board

Beyond the basics in `creative_director_controls.md`. Ten named grades — name the *technique*, not just a mood. **One grade per frame.**

| Grade | Look | Paste phrase |
|---|---|---|
| **ENR / silver retention** | retained silver in the print — desaturated color *with* dense rich blacks and metallic shadows | *"ENR silver-retention grade — muted color, very dense blacks, a metallic sheen in the shadows"* |
| **Bleach-bypass** | skipped bleach — high contrast, low saturation, gritty, crushed | *"bleach-bypass — desaturated, high-contrast, gritty, crushed shadows"* |
| **Teal-orange** | skin pushed warm orange, shadows and background pushed teal — the blockbuster look | *"teal-and-orange grade — warm orange skin against teal shadows, clear complementary separation"* |
| **Split-tone** | warm highlights, cool shadows (or the reverse) across the tonal range | *"split-tone — warm amber highlights, cool blue shadows, neutral mids"* |
| **Cross-process** | C-41-in-E6 chemistry — shifted hues, blown contrast, green/yellow cast, cyan shadows | *"cross-processed — shifted unnatural hues, high contrast, yellow-green cast, cyan shadows"* |
| **Day-for-night** | day footage graded to read as moonlit — cool blue, underexposed, desaturated | *"day-for-night — cool blue underexposed grade, desaturated, a hint of moonlight"* |
| **Technicolor 3-strip** | hyper-saturated primaries, rich reds and cyans, glossy classic-Hollywood color | *"Technicolor three-strip — hyper-saturated primaries, glossy rich reds and cyans, vintage Hollywood color"* |
| **Faded-print** | aged C-print — lifted milky blacks, faded cyan/yellow shift, low saturation | *"faded-print look — lifted milky blacks, a faded cyan-yellow shift, gentle low saturation"* |
| **Sepia / selenium toned** | monochrome warmed to brown (sepia) or cooled to plum-black (selenium) | *"selenium-toned black-and-white — cool plum-black shadows, neutral highlights"* |
| **High-key clean** | lifted, low-contrast, bright, near-shadowless — beauty/e-comm | *"high-key clean grade — bright, lifted, low-contrast, near-shadowless, true neutral whites"* |

**Field note (Round 3):** hard grading discipline is reliable **with explicit exclusion language** — for monochrome-plus-one, close with *"no other color anywhere — no skin tones, no warm cast — strictly grayscale except [element]."* The model holds the grade when you state what to exclude.

---

## 8. Camera-sensor signatures

Digital cinema bodies have fingerprints too — mostly in highlight rolloff and low-light behavior. Name the body for its *behavior*.

| Body / format | Signature | Paste phrase |
|---|---|---|
| **ARRI Alexa** | gentle, filmic highlight rolloff — bright areas compress gracefully instead of clipping hard; pleasing skin | *"ARRI Alexa rendering — gentle filmic highlight rolloff, no harsh clipping, natural skin"* |
| **Sony Venice** | exceptional low-light, clean shadows at high ISO, wide dynamic range, slightly cooler base | *"Sony Venice low-light — clean lifted shadows at high ISO, wide dynamic range, cool-neutral base"* |
| **Super 16** | visible gate weave (slight frame wobble), pronounced grain, softer resolution, vintage-cine texture | *"Super 16 — gate weave, pronounced grain, soft resolution, vintage-cinema texture"* |
| **RED (digital)** | crisp, high-resolution, slightly clinical, punchy contrast | *"RED digital — crisp high-resolution, punchy contrast, slightly clinical"* |
| **Bolex / 16mm reversal** | high contrast, saturated, heavy grain, occasional light leak | *"16mm reversal — high contrast, saturated, heavy grain, an occasional light leak"* |

**Why this matters:** "shot on Alexa" tells the model how highlights *behave* (roll off, don't clip), which is most of the difference between a video-render look and a cinema look. Highlight rolloff is the quiet tell.

---

## 9. Four decoded editorial looks

Each named look = light + lens + stock + grade. Paste the four components, don't name the look alone (the model averages a name).

**The Glossy Beauty look.** — *Light:* ring flash or clamshell, even and shadowless. *Lens:* 100mm macro, clean clinical prime. *Stock:* clean digital, no grain. *Grade:* high-key clean, true neutral whites. *"Ring-flash clamshell light, 100mm macro, clean digital, high-key neutral grade — glossy beauty editorial."*

**The Grainy Reportage look.** — *Light:* available light, hard sun or window. *Lens:* 35mm, slight veiling flare. *Stock:* Tri-X pushed, coarse midtone grain. *Grade:* high-contrast B&W, deep blacks. *"35mm available light, Tri-X pushed, coarse grain, high-contrast black-and-white — grainy reportage."*

**The Neon Night look.** — *Light:* night-practical mix, sign and street lamp, mixed temps. *Lens:* anamorphic, streak flare from the signage. *Stock:* Cinestill 800T with red halation. *Grade:* teal-noir, contaminated shadows. *"Night practicals, anamorphic streak from the sign, Cinestill 800T halation, teal-noir grade — neon night."* Pair with the night-physics block in `references/tonal_families.md`.

**The Warm Film Portrait look.** — *Light:* soft window key, shadow-side to camera, negative fill. *Lens:* 85mm at f/2, gentle vintage rendering. *Stock:* Portra 400, fine soft grain. *Grade:* warm split-tone, golden skin. *"Soft window key, 85mm f/2 vintage glass, Portra 400, warm split-tone — warm film portrait."*

---

## The closing discipline

Before you press Generate, check the three-part rule:

1. **One light idea** — a single dominating source/recipe, not three competing rigs.
2. **One stock or grain** — one emulsion vocabulary, never film-grain and digital-noise language mixed.
3. **One grade** — one named technique, not a stack.

And the hard check: **every artifact has a physical cause.** Flare from an in-frame source. Halation hugging a blown highlight. Grain in the emulsion, absent in pure black, melting in highlights. Bokeh from the named lens. If you can't name *why* an effect is there, cut it — that's the line between a photograph and a render.


<!-- ═══════ FILE: nano-banana-prompter/references/lighting_craft_and_filmmaking_deep.md ═══════ -->

# Nano Banana — lighting craft & filmmaking deep layer (working-DP grammar)

> **STATUS: UNVALIDATED (researched 2026-07-09, agent research round).** Builds UNDER `references/creative_director_controls.md` (lighting recipes), `references/film_look_references.md` (portrait patterns/scene styles), `references/optics_grain_and_light.md` and `references/director_styles_and_film_frames.md` (motivated-lighting order) — this file adds ratios, source physics, temperature mixing, practical-driven scenes, exterior timing, atmosphere control, staged-frame grammar, and genre lighting bibles.

## 1. Lighting ratios (the contrast dial)
Key:fill ratio IS the emotional register; hold it constant across a scene — changing it signals a story turn. Each doubling = one stop deeper shadow side. Models don't meter — translate ratio into shadow description:

| Ratio | Read | Prompt language |
|---|---|---|
| 1:1–2:1 | flat/honest/safe — comedy, corporate, beauty | *soft even lighting, shadow side only slightly darker, open airy contrast, gentle wraparound fill* |
| 4:1 | dimensional-natural — drama, prestige TV | *clearly defined shadow side, noticeably darker but with full detail retained, dimensional contrast* |
| 8:1 | tense, sculptural — thriller, noir | *high-contrast single-source look, shadow side falling toward black with a trace of detail, low-key* |
| 16:1+ | shadow-dominant — horror, interrogation | *shadow side fully crushed to black, a sliver of the face lit, the frame swallowed in darkness* |

**Fail→fix:** "dramatic high contrast" returns HDR-crunched global contrast → locate it on the subject: *"one side of the face brightly keyed, the other falling into soft shadow with faint detail; background moody but not clipped."*

## 2. Source size & distance physics
Big/close source = soft wrap; small/far = hard crisp shadows (the sun is huge but far = hard). Inverse-square: a close source makes a face glow while the room two feet away goes black; a far source lights evenly. Close source = intimacy/isolation; distant = institutional. Book light = double-softened directional wrap. Negative fill = black on the shadow side *subtracting* bounce to carve contrast under soft light.
**Cues:** *"lit by a single small source very close to her face, light falling off rapidly so the room dissolves into darkness within a few feet — a tight pool of light"* · *"enormous soft source close to the subject, shadow edges melting, north-window wrap"* · *"double-diffused bounced key, creamy directional softness, gentle highlight roll-off"* · *"black negative fill on the shadow side — the far cheek falls into clean deep shadow, contrast carved with darkness."*
**Fail→fix:** "soft lighting" alone = shadowless ring-light mush → pair softness with direction and subtraction: *"soft but directional key from camera-left, shadow side deepened by negative fill, clear bright-to-dark gradient across the face."*

## 3. Color temperature mixing
Balance to the window = interior goes amber; balance to the lamps = window goes blue — whichever source you neutralize, the other swings. Contamination signatures: sodium = monochromatic orange killing all other color; fluorescent = green spike; cheap LED = magenta/green shift. Movie moonlight is a CONVENTION: desaturated steel blue-grey, soft, toppy — not saturated cobalt — with warm practicals crossing against it. Day-for-night = soft backlit/overcast daylight, no sky in frame, 2–3 stops under, graded blue. Dusk-for-night = the 20 real minutes when practicals glow but the sky holds detail.
**Cues:** *"warm tungsten lamplight on the near side of her face, cool blue window daylight rimming the far side — two temperatures crossing on the skin"* · *"monochromatic orange sodium-vapor light swallowing every other color"* · *"desaturated steel-blue moonlight, silvery rather than blue, one warm window glowing across the street as counterpoint"* · *"graded day-for-night: deep blue-grey with detail held in shadows, no visible sky"* · *"last minutes of dusk — cobalt ambient sky, streetlights and windows already glowing warm."*
**Fail→fix:** "blue moonlight" overshoots to cobalt fantasy → *"pale desaturated blue-grey, almost monochrome"* + put a warm practical in frame to force blue as relative coolness.

## 4. Practical-driven scenes
The practical is the *motivation*; exposure comes from an implied matched source on the same axis. Signatures: TV = broad cool flickering wash from below eyeline, changing color with the content; phone = tiny cool source inches away, brutal falloff (face bright, chest dark), under-chin angle; fire/candle (~1800–2000K) = flickering in intensity AND position, lighting from LOW, shadows dancing upward, radius ≈ arm's length; bulb itself never clipped.
**Cues:** *"lit entirely by the table lamp in frame — warm glow plausible in angle and falloff from the lamp itself, bulb not blown out"* · *"the only light is the flickering television: cool shifting blue-white wash from below eyeline, the unseen program's colors bleeding onto the walls"* · *"face lit solely by the phone screen — cold blue underglow, light dying before it reaches the shoulders"* · *"single candle as key: warm amber flicker from below, shadows trembling upward, glow dying within arm's reach"* · *"lit by the neon sign in the window — magenta and cyan gradient across the face, wet reflections carrying the color."*
**Fail→fix:** practical in shot but scene lit by a contradictory invisible source → state exclusivity: *"no other light source; the light on the face comes from the lamp's direction, warm side toward the lamp, far side falling dark."*

## 5. Exterior craft & the magic-hour ladder
Standard: sun BEHIND the subject (rim), face keyed by bounce — never front-sun. Overcast = free giant softbox (toppy, directionless — add negative fill or an edge). The ladder: golden hour (sun 0–6° up — warm raking honey light, long shadows) → sunset → blue hour/civil twilight (sun 0–6° below — shadowless cobalt, sky luminous, practicals glowing). Harsh noon: embrace (desert brutality, shadowed eye sockets), diffuse, or back-to-sun + bounce. Window interiors by hour: morning/evening = hard warm shafts; midday = soft indirect; north light = the painter's constant.
**Cues:** *"sun behind the subject as a warm rim on hair and shoulders, face keyed by soft bounce, open-shade exposure on the skin"* · *"overcast sky as one enormous softbox, even wrap, subtle negative fill giving the face shape"* · *"low golden-hour sun raking, long shadows toward camera, honey light with cool sky fill in the shadows"* · *"civil twilight: shadowless deep-blue ambient, luminous gradient sky, windows glowing warm against the cobalt"* · *"brutal overhead noon, hard top light, eye sockets shadowed under the hat brim, bleached ground."*
**Fail→fix:** "golden hour" collapses to an orange filter over front-lit noon → specify geometry: *"sun low and BEHIND the subject, warm rim on the hair, face one stop darker lit by sky bounce, long shadows running toward camera."*

## 6. Smoke, haze & atmosphere
Light haze is invisible as smoke but lifts backgrounds, mutes contrast, and makes light visible in the air; heavy smoke is a subject. Shafts need particles AND a hard BACKLIT source — smoke reads strongest backlit, barely front-lit. Haze builds depth mechanically: each farther plane brighter, milkier, less saturated.
**Cues:** *"faint atmospheric haze — just enough to soften the distance and give the backlight a gentle glow"* · *"hard backlight cutting through visible haze, defined volumetric shafts from the window, dust motes drifting in the beams"* · *"layered atmospheric depth: foreground crisp and saturated, midground softened, background dissolving into pale luminous atmosphere"* · *"thick rolling smoke backlit into glowing silhouettes."*
**Fail→fix:** god-rays kitsch with no source logic → motivate every shaft (*"single shaft from the high window, source visible"*) and cap density (*"thin even haze, not fog — the room still reads clearly"*).

## 7. Filmmaking grammar for stills
A cinematic still is a STAGED frame: activate all three planes — foreground element cutting the frame (doorframe, shoulder, rain-streaked glass), subject in midground, background with life. Camera movement can be implied: whip-pan = lateral streaks; dolly-in = compressed urgency; handheld = tilted imperfect framing; long-lens pan = smeared background, sharp subject. Think in coverage: frame each still as one shot from an imagined scene (the wide, the dirty OTS, the insert) — forces eyeline, negative space, off-frame implication. Lighting continuity: key direction, ratio, and color persist across "cuts" — matched key side + grade sells two stills as one scene. Night exteriors: wet down the street (doubles every light), build discrete POOLS of light with true darkness between, mixed sodium/LED/neon, characters staged at pool edges.
**Cues:** *"foreground: out-of-focus shoulder and doorframe edging frame-left; midground: subject sharp mid-stride; background: blurred figures and neon still legible as life"* · *"whip-pan energy, horizontal streaks at the frame edges, subject barely held sharp"* · *"framed like a dirty over-the-shoulder from a two-scene, eyeline just off lens"* · *"same scene lighting as the previous frame: key from window camera-left, 4:1 ratio, tungsten-vs-dusk palette"* · *"rain-slicked street mirroring the neon, isolated pools of light with darkness between them, subject rim-lit at a pool's edge, breath visible."*
**Fail→fix:** everything-in-focus centered subject = catalog shot → force plane hierarchy + off-center subject with lead-room toward implied off-frame action.

## 8. Genre lighting bibles
| Genre | Law | Cue | Fail→fix |
|---|---|---|---|
| Horror | light the darkness; underlight inverts features; shadows own 70%+ | *lit from below by a single hard source, features unnaturally inverted, vast negative darkness, something unreadable in the shadow behind* | too dark to read → keep one precise detail: *a single sliver of light across the eyes* |
| Noir | one hard high-side key, no fill | *single hard key raking from high side, venetian-blind shadows barring the face, smoke in the beam, blacks crushed clean, no fill* | floating slats → *shadow pattern cast from the actual blinds at frame left, angle consistent* |
| Romance | backlight carries it, 2:1 | *soft golden backlight haloing her hair, diffusion bloom on highlights, creamy 2:1 wraparound key, warm haze* | soap-opera flat → keep the backlight 1–2 stops hotter than the key |
| Thriller | toplight, withheld eyes, 8:1 | *hard overhead toplight, eye sockets falling into black, expression unreadable, cold restrained palette* | model over-lights faces → *eyes fully in shadow, only jaw and cheekbones lit from above* |
| Documentary | available light only, honest | *available light only — office fluorescents mixing with window daylight, uncorrected cast, unflattering honest exposure, caught-not-staged* | drifts to polish → ban it: *no studio lighting, no rim light, slight underexposure, verité imperfection* |
| Music video | complementary gel systems | *hard magenta key from left crossed with cyan backlight, gels mixing to white only on highlights, haze glowing with both colors, black void* | muddy purple wash → separate spatially: *magenta strictly on the face's left, cyan strictly on rim and background* |

*Cross-refs: `references/film_look_references.md` (named looks + portrait patterns — pick ONE per frame and pair with ONE ratio from §1), `references/director_styles_and_film_frames.md` (motivated-lighting order, 180° shutter logic), `references/optics_grain_and_light.md` (editorial flash registers), `references/framing_scene_grammar_and_continuity.md` (coverage/continuity this file's §7 feeds), `references/realism_physics_deep.md` (shutter/exposure physics), `references/tonal_families.md` (one tonal family per image still applies). Sources incl. ASC (inverse-square, smoke shot-craft, terror-through-lighting), Wandering DP ratios, StudioBinder (book light, day-for-night, practicals, depth), Neil Oseman, In Depth Cine moonlight, PhotoPills magic-hour timing, No Film School night exteriors & music-video gels.*


<!-- ═══════ FILE: nano-banana-prompter/references/perspective_and_lens_geometry.md ═══════ -->

# Nano Banana — perspective & lens geometry (the geometry layer)

> **STATUS: UNVALIDATED (researched 2026-07-09, agent research round).** Builds UNDER `references/framing_scene_grammar_and_continuity.md` (shot sizes, angles, composition systems live there) — this file is the *geometry* that makes those frames physically solid.
>
> **Cheat rules for every prompt:** ONE camera, one geometry — state height + tilt + distance + FOV explicitly (*"camera at chest height, level, 3m from subject, 35mm field of view"*). **Horizon = camera height, always** — the fastest single verification on any frame. **Distance drives faces and backgrounds; lens tokens are style hints** — when face geometry matters, prompt the distance. **Cue coherence beats cue quantity** for scale.

## 1. Linear perspective mechanics
**Rule:** the horizon sits at camera height, projected across the frame. All lines parallel in 3D converge to ONE vanishing point on that horizon (one-point: camera square to a face; two-point: rotated to a corner, both VPs on the horizon; three-point: tilt adds a vertical VP). Each parallel family shares exactly one VP — that constraint makes a frame solid.
**AI failure:** window rows/floorboards/rooflines converging to different points (documented AI tell, worst in architecture); horizon height contradicting the stated camera position; verticals converging with no tilt.
**Prompt:** *"one-point perspective, camera square to the far wall, all receding lines converging to a single central vanishing point, horizon at eye level"* · *"two-point perspective on the street corner, both building faces receding to vanishing points on a shared horizon, verticals perfectly parallel"* · *"camera level, no tilt, consistent single-perspective geometry."*
**Verify:** sight along 3+ receding edges of one plane — one intersection point, on the same horizon as other VPs; horizon height must match stated camera height.

## 2. Focal length × distance (perspective is DISTANCE)
**Rule:** relative near/far sizes are set 100% by camera-to-subject distance; the lens only crops. At 0.5m the nose is ~35% bigger than the ears (24mm headshot); at 2.5m the ratio is ~5% (135mm, flat). "Compression" = you backed up, so background/subject distance ratio → 1 and the background renders huge. Dolly-zoom = subject constant, background scale changes, because only distance changed.
**AI failure:** 85mm framing with 24mm face geometry (or vice versa); "telephoto compression" with a background too small for the stated lens.
**Prompt:** *"shot from 3 meters on a 135mm telephoto — flattened facial features, ears and nose near-equal scale, background rendered large and close behind the subject"* · *"camera 40cm from the face, 24mm — exaggerated nose, receding ears, tiny distant background, confrontational closeness"* · *"85mm portrait geometry, camera ~2m away, natural proportions"* · *"vertigo dolly-zoom framing: subject at normal scale, background walls looming unnaturally large."*
**Verify:** nose-to-ear scale vs stated lens/distance; background magnification must match (tele = big close background; wide = tiny receding one). Face says 85mm but background says 24mm → regenerate.

## 3. Camera height grammar
**Rule:** whatever body part the horizon crosses on background figures IS the camera height. Eye level (~160cm) = horizon at eyes, walls dominate; chest (~120cm, interior standard) = horizon mid-torso, ceilings feel taller; waist = classic cinema hero height; ground = horizon at ankles, floors loom; overhead = no horizon.
**AI failure:** the **drone default** — a sneaky elevated ~10–15° down angle with a high horizon even when "eye level" was asked; or "low angle" with a mid-frame horizon and no vertical convergence.
**Prompt:** *"camera at eye level, horizon line crossing the subject's eyes, lens perfectly level, no downward tilt"* · *"camera at chest height, 120cm, horizon at the sternum"* · *"ground-level camera on the pavement, horizon at ankle height, foreground asphalt dominating, subject towering"* · anti-drone: *"NOT elevated, no aerial perspective, camera held by a person standing on the ground."*
**Verify:** find the horizon (extend receding lines if hidden) and read which body part it crosses.

## 4. Wide-angle craft
**Rule:** two separate effects — (a) volume anamorphosis: rectilinear projection stretches heads/columns near edges, worst past ~30° off-axis; (b) keystoning: caused by TILT, not lens — tilt up and buildings lean in. A shift lens keeps verticals parallel while framing the top: the architectural look.
**AI failure:** verticals leaning in random inconsistent directions (physically impossible); stretched edge figures on an otherwise-normal lens; "architecture photography" with amateur keystone.
**Prompt:** corrected: *"tilt-shift lens, camera perfectly level, all verticals parallel, no keystoning, formal architectural perspective"* · exploited: *"ultra-wide 16mm action POV, deliberate barrel curvature, stretched edges, dramatic keystone convergence as the camera tilts up"* · safety: *"24mm wide, all people kept in the central two-thirds, no stretched figures at the edges."*
**Verify:** verticals must be all parallel, or all converging to ONE shared point above/below. Mixed lean directions = broken.

## 5. Forced perspective & scale cues
**Rule:** scale is inferred from relative size vs known anchors (people, cars, doors), occlusion order, DOF (shallow = small, deep + haze = huge), camera height, texture falloff. Miniature faking = high oblique angle + razor-thin horizontal focus band + boosted saturation. Giant = ground camera, deep focus, haze on the subject itself, tiny anchors, the giant occluding BEHIND known-scale objects.
**AI failure:** "giant robot" reads normal-sized because shallow DOF (a smallness cue) crept in or anchors are missing; wrong occlusion order breaks scale instantly.
**Prompt:** miniature: *"tilt-shift miniature effect, high oblique 45° down, extremely shallow horizontal band of focus, blurred top and bottom, boosted saturation, toy-like"* · giant: *"ground-level camera looking up, colossal figure veiled by atmospheric haze at the shoulders, tiny cars and people at its feet, deep focus, its foot occluding a three-story building"* · always name 2 anchors at different depths.
**Verify:** all scale cues must vote the same way — DOF, haze, anchor sizes, occlusion order. One contradicting cue collapses the illusion.

## 6. POV & embodied camera
**Rule:** first-person = lens at eye height, slight down pitch, own hands entering from the BOTTOM CORNERS (foreshortened, large, slightly soft), wide FOV with barrel curve, no visible body. Mirror = the reflection is a virtual scene behind the glass at equal distance: rendered at (camera→mirror + mirror→subject) distance — smaller, flipped, showing the opposite body side; the camera appears unless angled away. OTS = camera behind/beside the foreground shoulder at the on-screen character's eye level; shoulder/head as a soft wedge in one lower corner, never showing the foreground nose.
**AI failure:** POV hands entering at impossible angles or two right hands; mirror reflections same-size, wrong-facing, wrong-outfit, or missing the camera-holder; OTS with both faces sharp (that's a two-shot).
**Prompt:** *"first-person POV, camera at standing eye height, own hands entering from the lower corners, foreshortened and slightly soft, wide action-cam field of view with mild barrel distortion, no visible body"* · *"she stands 1m from the mirror; her reflection appears smaller, at twice the distance, showing her front while we see her back; camera angled so it does not appear in the mirror"* · *"over-the-shoulder: foreground character's blurred shoulder and back of head in the lower-left third, no nose visible, camera at the facing character's eye level."*
**Verify:** POV thumbs point inward; mirror reflection smaller + flipped + opposite side; OTS has exactly one sharp face.

## 7. Interiors & architecture discipline
**Rule:** one-point (square to the far wall — calm, symmetric) or two-point (aimed at a corner — dynamic, the real-estate default); camera LEVEL at chest height; any pitch converts every doorframe into converging verticals. Ceiling line and floor line of the SAME wall must meet at the same VP.
**AI failure:** doorframes leaning different directions on one wall; floors tilting against level counters; rubber-stretched foreground furniture from an implied 10mm lens.
**Prompt:** *"one-point interior, camera square to the back wall, symmetric convergence to a single vanishing point, all verticals plumb"* · *"two-point interior aimed at the corner, level camera at chest height, verticals parallel, no downward tilt"* · *"24mm equivalent — wide but natural, no ultra-wide stretch, foreground furniture in true proportion."*
**Verify:** three-line test — verticals parallel to frame edge; each wall's ceiling+floor lines meet at one point on the shared horizon; counters horizontal or consistently converging. Bloated corner armchair = model went ultra-wide.

## 8. Aerial / drone geometry
**Rule:** altitude sets scale; gimbal tilt sets the geometry. Nadir (90° down) = quasi-orthographic map — no horizon, no VPs, buildings splaying radially from frame center, only shadows give height. Oblique (30–60°) = horizon in/just above frame, facades visible, cinematic recession.
**AI failure:** blended modes — "top-down" with a sneaky horizon and half-oblique buildings; nadir buildings leaning in random directions instead of radially; disagreeing shadow directions.
**Prompt:** *"nadir aerial, camera 90° straight down, orthographic map-like flatness, no horizon, buildings splaying radially outward from image center, one consistent shadow direction"* · *"high-oblique drone from 120m, gimbal 45° down, horizon in the top fifth, facades visible, layered depth haze"* · scale: *"cars as small rectangles, people as dots"* vs *"individual people recognizable."*
**Verify:** mode purity (no horizon in nadir; horizon height matches tilt in oblique); radial building lean; one sun direction and length everywhere; anchor sizes match claimed altitude.

*Cross-refs: `references/framing_scene_grammar_and_continuity.md` (shot grammar this file underpins), `references/optics_grain_and_light.md` (lens character), `references/closeups_and_interviews.md` (OTS/eyeline craft), `references/composition_posing_and_critique.md` (audit loop — add the horizon-height check to it), `references/realism_physics_deep.md` (shadow/reflection consistency). Sources incl. ControlVP (arXiv 2512.07504) on VP inconsistency in diffusion models, Admiring Light/Fstoppers on compression-is-distance, HDRsoft on interior camera height, SkyeBrowse on nadir vs oblique, NFI/MasterClass on OTS geometry.*


<!-- ═══════ FILE: nano-banana-prompter/references/framing_scene_grammar_and_continuity.md ═══════ -->

# Framing, Scene Grammar & Continuity — the full catalog for AI framing and composing

This file is the master framing/composition/continuity layer for Nano Banana stills and multi-frame sequences. It extends `composition_posing_and_critique.md` (visual grammar + critique), `closeups_and_interviews.md` (shot-size lenses), `identity_lock_and_filmmaking.md` (coverage + 180° basics), and `commercial_framing_and_set_design.md` (ad framing). Where those files give recipes, this one gives the **system**: the complete shot-size ladder with psychology, the angle grammar, framing relationships, staging-as-composition, the continuity rulebook for frame SEQUENCES, narrative + commercial scene taxonomies, and aspect-ratio recomposition rules.

Core translation rule: Nano Banana renders scenes, not camera moves. Every cinematography concept below is expressed as a **frozen-frame instruction** — what the camera position, lens, and staging leave visible in ONE still. For sequences, continuity lives in the *relationship between prompts*.

---

## 1. The complete shot-size ladder (size × lens × distance × psychology)

Always name the shot size explicitly — it is the strongest single framing lever the model has. Pair it with where the frame edges cut the body, the lens, and the psychological job.

| Size | Frame cuts at | Typical lens | Psychological job | Prompt phrase |
|---|---|---|---|---|
| Extreme wide (EWS) | Figure <10% of frame | 16–24mm | Insignificance, scale, world-first | "extreme wide shot, the figure tiny against…, environment dominates" |
| Wide / long (WS) | Full body + headroom | 24–35mm | Context, body language, entrance | "wide shot, full figure visible, feet in frame" |
| Medium-wide (MWS / cowboy) | Mid-thigh | 35mm | Readiness, swagger, holstered tension | "medium-wide, framed mid-thigh" |
| Medium (MS) | Waist | 35–50mm | Neutral conversation, gesture room | "medium shot, waist-up" |
| Medium close-up (MCU) | Chest | 50–75mm | Engagement, interview default | "medium close-up, chest-up" |
| Close-up (CU) | Shoulders / face | 85–100mm | Emotion, interiority | "close-up on the face, shoulders just in frame" |
| Extreme close-up (ECU) | Eyes / mouth / detail | 100mm macro | Obsession, revelation, tension spike | "extreme close-up on the eyes only" |
| Insert / detail | Object fills frame | macro | Information, plot object, product hero | "insert shot: the hand turning the key, nothing else" |

Ladder logic for sequences: **each cut down the ladder raises intimacy and stakes**. A stills sequence that goes WS → MS → CU → ECU reads as escalating tension even with no story text. Jumping two+ rungs (WS → ECU) reads as shock — use deliberately.

Distance ≠ zoom: a CU on a 24mm (camera physically near) distorts and confronts; a CU on a 135mm (far, compressed) observes coolly. Say which: *"close-up shot on a wide 24mm lens, camera inches from the face, slight distortion"* vs *"long-lens close-up from across the room, compressed, voyeuristic."*

## 2. Camera angle grammar (height + tilt + orbit)

Three independent axes — set each one:

**Height** — worm's-eye (ground, looking up: monumental, threatening), low angle (chest-height looking up: power, heroism), eye-level (neutral, honest, documentary), high angle (looking down: vulnerability, assessment), overhead/top-down 90° (god view, pattern, design — the flat-lay and the crime-scene), drone/aerial (geography, isolation).

**Tilt** — level horizon (stable); Dutch/canted 5–15° (unease, wrongness, villainy — use once per sequence at the destabilizing beat, never as decoration).

**Orbit** — frontal (confrontation, symmetry, tableau), 3/4 (the default — beware: EVERY face at 3/4 is an AI tell; vary), profile (detachment, transition, journeys), behind (mystery, follow, POV-adjacent).

Anchor every angle to an operator position with a reason: *"shot from a second-floor window across the street"*, *"camera at the child's eye height"*, *"low over the café table, as if from the empty chair"*. Sourceless floating angles are the #1 generic-AI framing tell.

## 3. Framing relationships (who shares the frame)

- **Clean single** — one subject, no part of anyone else. Isolation, formal interview.
- **Dirty single** — one subject featured, a sliver (shoulder, blurred head) of another intruding at frame edge. Instantly relational; makes dialogue frames feel inhabited. *"dirty single on the woman, the man's out-of-focus shoulder breaking the left frame edge."*
- **Two-shot** — both subjects share the frame; spacing = relationship (touching shoulders vs a table-width of negative space between them).
- **Over-the-shoulder (OTS)** — camera behind character A's shoulder onto character B. Establishes eyeline + spatial geography. Foreground shoulder should be soft and occupy 15–25% of frame.
- **POV** — the frame IS a character's eyes. Sell it with height, slight tilt, foreground hands/props, motion blur at edges, or an occluding object (doorframe, phone, windshield).
- **Reaction shot** — a face responding to something off-frame. Give the trigger: *"her eyes fixed just off-lens left, reacting to something we can't see, jaw slack."*
- **Cutaway / insert** — leave the action for a detail that comments on it (nervous hands, the clock, the untouched food). In stills sequences, one insert per 3–4 frames is the pro rhythm.
- **Group/crowd** — establish a hierarchy: one subject gets focus + light + face angle; others get progressively less. Never equal-weight everyone (AI tell: the evenly-spaced clone lineup).

## 4. Composition systems (pick ONE dominant system per frame)

1. **Rule of thirds** — subject on an intersection, horizon on a third line, look-room in the empty two-thirds. Default for naturalism.
2. **Central symmetry / planimetric tableau** — dead-center subject, frontal camera, background flat and parallel to the sensor, measured symmetry (the Wes Anderson register). Reads as designed, theatrical, ironic. Whole frame must commit: architecture centered, props mirrored, one deliberate asymmetry maximum.
3. **Frame-within-frame** — doorways, windows, mirrors, arches containing the subject. Adds depth + entrapment/voyeurism. *"seen through the kitchen doorway, the door frame cutting the left and right edges."*
4. **Negative space** — subject small against a vast empty field (sky, wall, sea). Emotion = the emptiness. Put the subject at an edge or corner, not center.
5. **Leading lines** — road, rail, corridor, cable, shadow-line converging on the subject. Say the actual line: *"the wet curb and the line of streetlights converge on him from frame-left."*
6. **Depth staging (three planes)** — a foreground occluder (soft, dark), the subject in the midground, an environment layer behind with atmospheric haze. The single strongest anti-flat, anti-AI move; works in almost every frame.
7. **Figure-ground / silhouette** — subject dark against bright (or reversed). Pure shape storytelling. Backlight required; kill fill.
8. **Color blocking** — composition by color mass, not line (a red coat as the only warm object in a teal frame).
9. **Visual weight & hierarchy** — the eye goes to: brightest → sharpest → highest contrast → faces → text. Design the read-order; whatever should be seen first must win at least two of these.

**Balance & headroom mechanics:** look-room in the gaze direction (subject looking left sits right-of-frame); headroom shrinks as shot size tightens (generous in WS, near-zero in CU — cropping the top of the head in a CU is correct, not an error); leave lead-room ahead of any implied motion.

## 5. Blocking & staging (arrangement as story)

Blocking is where bodies are; in a still, it IS the story. Levers:

- **Power staging** — dominant figure closer to camera, higher in frame, more in focus, facing camera-ward; subordinate figure smaller, lower, turned away. Negotiations, confrontations, hierarchies.
- **Distance = relationship** — intimate (<45cm), personal (~1m), social (2–3m), public (4m+). Say it in physical terms: *"they stand a full table apart"*.
- **Open vs closed body** — chest toward camera = accessible; back/shoulder = withheld. Two characters both bladed away from each other = conflict without a word.
- **Lateral vs depth staging** — subjects side-by-side on one plane (theatrical, flat, tableau) vs staggered near-to-far (cinematic, dimensional). Choose deliberately.
- **Triangle rule for 3+ people** — arrange heads on an irregular triangle at different depths and heights; never a flat row.
- **The empty chair** — absence staged as presence: an unoccupied seat, an untouched place setting, a gap in the group where someone should be.

## 6. CONTINUITY GRAMMAR — the rulebook for multi-frame sequences

This is what makes a set of stills read as one scene instead of a mood board. Apply whenever generating 2+ frames of the same moment (storyboards, carousels, ad sequences, dialogue pairs, film-strip posts).

### 6.1 The 180° rule (the axis)
Draw an imaginary line through the two subjects (or along the direction of travel). Keep the camera on ONE side of it for every frame. Practical enforcement in prompts: pick the side once and restate it every frame — *"camera on the window side of the table for all frames: the woman always faces frame-right, the man always faces frame-left."* If characters swap facing between frames, the scene breaks. Cross the line only via a declared transition: a frame ON the axis (frontal or profile), or a frame where a character physically turns.

### 6.2 Eyeline match & screen direction
- In shot-reverse-shot: if she looks off-lens LEFT in her single, he must look off-lens RIGHT in his. Heights must agree — if she's standing and he's seated, her gaze angles down, his up.
- Screen direction: a subject exiting frame-right must enter the next frame from frame-left. A journey keeps one travel direction across all frames until arrival.
- The model coin-flips eyelines (see `closeups_and_interviews.md`). CHECK every generated pair; regenerate the cheaper frame if mismatched.

### 6.3 The 30° rule
Between two frames of the same subject, move the camera at least ~30° around them or change shot size by at least one full rung. Two frames from nearly the same angle at nearly the same size read as an error (a "jump cut" in stills). Legal pair: MCU at 3/4 left → CU frontal. Illegal: MCU at 3/4 left → slightly-tighter MCU at 3/4 left.

### 6.4 Match-on-action pairs
Two frames can imply motion: frame 1 catches the action starting (hand reaching for the door handle), frame 2 catches it completing from a DIFFERENT angle/size (door swinging open, seen from inside). The action must be continuous and the direction consistent. This is the strongest way to make a stills carousel feel edited rather than assembled.

### 6.5 The continuity ledger (restate every frame)
Carry a verbatim block across all prompts in the sequence — wardrobe (full restatement, not "same outfit"), hair state, props in hand and WHICH hand, light direction + time of day, weather, set dressing anchors (the two coffee cups, the coat on the chair), the production-look block (stock/grain/lens family/grade/ratio from `identity_lock_and_filmmaking.md`), and injuries/dirt/rain-wetness state. Anything not restated will drift. Props are the worst offenders: name count and position ("the phone stays face-down beside her left hand").

### 6.6 The coverage set (what to generate for a "scene")
Standard scene coverage in stills: 1 master/establishing WS (geography + all players), singles per speaking character (MCU or CU, obeying axis + eyelines), 1–2 inserts (hands/props/details), 1 reaction shot, optionally 1 wide re-establish after the turn. Generate the master FIRST; derive every other frame's geography from it. Edit-chain each frame from the master (or use it as a reference image) rather than generating from scratch.

### 6.7 Cut grammar for sequences (what stills can borrow from editing)
- **Cut-in / cut-away rhythm**: wide → tighter → insert → reaction. Alternate information and emotion.
- **Kuleshov pairing**: face + object in consecutive frames creates meaning neither has alone (neutral face → empty crib reads grief; same face → jackpot ticket reads greed). Use for carousels/storyboards.
- **Match cut (graphic match)**: two frames rhyme by shape/composition across a scene change (ceiling fan → helicopter rotor; round teacup → full moon, same frame position). Prompt both frames with the same composition skeleton, different content.
- **J/L-cut equivalent in stills**: a caption or in-image text from the NEXT beat over the current frame.

## 7. Scene taxonomy — narrative

Name the scene TYPE in your head before prompting; each has a default framing package:

- **Establishing/arrival** — EWS/WS, environment dominates, figure small, leading lines to entry point. Time-of-day and weather do the emotional work.
- **Dialogue scene** — master two-shot + OTS pair + singles, one axis, escalating sizes as stakes rise. Dirty singles > clean for warmth.
- **Confrontation** — power staging, opposing screen directions, tighter than comfortable, one Dutch frame at the break point.
- **Action beat** — freeze at the PEAK of motion (contact, apex of jump, glass mid-shatter), wide enough to read geography, motion blur on non-hero elements, debris/hair/fabric airborne. Low angle amplifies.
- **Chase/journey** — consistent travel direction across frames, lead-room, environment streaking (panning register), map-like aerial as punctuation.
- **Montage frame** — one idea per frame, bold single-system compositions, unified grade across all.
- **Intimate/quiet scene** — long-lens compression, shallow focus, frame-within-frame, negative space, practical-light pools; nothing centered.
- **Reveal frame** — composition that hides then shows: the subject behind a foreground occluder, a mirror showing what the room hides, the turn from `movements_and_masters.md`. Stage what the viewer discovers SECOND.
- **Aftermath** — the action scene's inverse: stillness, wide, high angle, evidence of the event (overturned chair, smoke) without the event.

## 8. Scene taxonomy — commercial / advertising

A :30 spot storyboards to 8–12 frames; a stills campaign compresses the same beats. Structures (pick one, assign a framing package per beat):

- **Problem → solution**: 2–3 frames of friction (tight, cluttered, cool/desaturated, handheld register) → product intro (clean, centered or thirds-placed, warm, stable) → resolution lifestyle (wide, bright, deep) → end-frame packshot lockup. The GRADE and FRAMING flip at the product beat — that flip is the ad.
- **Product demo**: 4–6 frames, insert-heavy: hands + product macro, mechanism detail, before/after pair (identical composition, one variable changed), result hero. Same axis and light across all demo inserts.
- **Testimonial/UGC**: alternating speaker MCUs (interview grammar from `closeups_and_interviews.md`, off-lens eyeline, lav mic) and product/result cutaways. Speaker frames imperfect (UGC register); product cutaways one notch cleaner.
- **Lifestyle/brand film**: montage grammar — EWS place-setting, mediums of use-in-life, CU of texture/emotion, unified tonal family, product present but never centered until the final frame.
- **Hero/spectacle** (perfume, auto, sport): tableau symmetry or monumental low angles, built-set registers from `commercial_framing_and_set_design.md`, one practical element (splash, fabric, powder) with a physical cause.
- **Comparison/versus**: split composition or matched-pair frames — identical camera, light, and layout; only the compared variable differs (this is `structured_prompting.md` A/B as a creative device).

End-frame law: every commercial sequence terminates in a packshot/lockup frame — product at hero angle, logo + tagline in the copy hole, framing quiet (see `campaign_and_specialist_genres.md` for the copy-hole and read-order rules).

## 9. Aspect ratio drives composition (recompose, don't crop)

- **21:9** — horizontal stage: lateral staging, negative space as meaning, two subjects at opposite edges, landscape breathing. Never center a lone talking head unless the emptiness IS the point. Headroom minimal.
- **16:9** — the neutral cinematic default; thirds and depth staging both thrive.
- **3:2 / 4:3** — taller field tightens attention; 4:3 reads archival/intimate — great for portrait tension and planimetric tableaux.
- **4:5 / 1:1** — feed formats: subject larger in frame, vertical thirds, faces upper-third, tight margins. Symmetry reads especially strong in 1:1.
- **9:16** — vertical grammar: stack the composition (sky/subject/foreground as vertical layers), full-figure fashion works naturally, leading lines run vertical (stairs, poles, rain), faces sit in the upper third, leave bottom 20% clear for platform UI (safe zones in `creative_posts_copy_type_layout.md`).

The same scene needs different STAGING per ratio, not the same scene cropped: in 21:9 the couple sits at opposite ends of the bench; in 9:16 one stands behind the other, stacked in depth.

## 10. Failure modes (framing/continuity specific)

| Symptom | Fix |
|---|---|
| Every frame at eye level, subject centered, 3/4 face | Assign an operator position + one composition system per frame; vary orbit across a set |
| Sequence characters swap sides between frames | Restate the axis side + facing direction ("she always faces frame-right") in EVERY prompt |
| Eyelines don't meet in a dialogue pair | State off-lens direction AND gaze height per single; regenerate the mismatched frame |
| Two frames read as a jump cut | Enforce the 30° rule: change angle ≥30° or size ≥1 rung |
| Stills set feels like a mood board, not a scene | Generate a master first; edit-chain frames from it; carry the continuity ledger verbatim |
| Props/wardrobe drift across frames | Full verbatim restatement + count/position of props each frame |
| Dutch angle everywhere | One canted frame per sequence, only at the destabilizing beat |
| Crowd looks like clones | Hierarchy: one focused subject, varied faces/ages/postures, occlusion between figures |
| 9:16 frame is a cropped 16:9 | Recompose vertically: stacked planes, vertical leading lines, upper-third face |
| Ad sequence has no shape | Pick a named structure (problem→solution, demo, testimonial); flip grade+framing at the product beat; end on a packshot |

## 11. Prompt skeleton for a continuity-locked sequence frame

```
[SHOT] Frame N of M — [size], [angle + operator anchor], [lens], [composition system].
[SCENE] [scene type + beat]. [Subject action frozen at its peak or telling moment].
[AXIS] Camera stays [side] of the action line; [character] faces frame-[left/right]; eyeline [off-lens direction, height].
[LEDGER] (verbatim across all frames) wardrobe…, props + positions…, light direction + time…, set anchors…, [production-look block].
[STYLE] [tonal family / grade / stock — identical across the sequence]. Output in [ratio].
```

One frame = one shot size + one composition system + one new piece of information. Sequence = one axis + one ledger + one grade.

---

## 12. Field-validated (Round 16, live ImagineArt run — see `field_findings.md`)

10/10 scene-type frames usable; 8 strong. Additions from the run, now law:

- **OTS eyeline:** the featured subject's gaze must point INTO the foreground shoulder. Never write an off-lens direction that contradicts where the shoulder sits — the model follows the geometry, not your word.
- **Off-lens gaze is opt-in:** "not posing at camera" does NOT stop at-lens eyes. State the off-lens direction explicitly in every single.
- **Destruction needs nouns:** "mid-shatter" renders intact. Write "splintering, broken slats, fragments mid-air."
- **Pan streaks are weak:** background pan blur renders as bokeh unless you spell out "horizontal directional smear on every background element, 1/60s shutter" — and expect partial compliance. Peak-freeze (1/2000s) is reliable.
- **Inner-frame centering pull:** subjects gravitate to the center of doorways/windows/mirrors. Anchor them to an edge of the aperture if you want off-center.
- **Anchor leak:** operator anchors phrased as objects can appear in frame ("from a step ladder" → a ladder). Phrase as height/position, or exclude the object explicitly.
- **Hands flip:** anatomical left/right on bodies mirror-flips ~half the time. Use screen-side language ("on the frame-right side of his body").
- **Sequence identity:** the verbatim ledger holds wardrobe/props/light/set — NOT faces or hair. Lock identity with a reference image (img2img from the master frame); re-anchor rather than describe.
- **Label copy:** quote the exact text AND close with "no other text on the label" or the model fills space with gibberish.


<!-- ═══════ FILE: nano-banana-prompter/references/composition_posing_and_critique.md ═══════ -->

# Nano Banana — Composition, posing, and the critique rubric

Three layers: where things go in the frame, what bodies do in it, and how to judge the result systematically.

---

## 1. Composition — visual grammar

### Placement systems

| System | Prompt phrase | Use when |
|---|---|---|
| Rule of thirds | *"subject on the right third line, eyes on the upper third intersection"* | Default editorial balance |
| Dead center | *"perfectly centered, symmetrical surroundings"* | Power, formality, Anderson/Kubrick irony |
| Extreme off-center | *"subject pushed to the far frame edge, vast negative space in their eyeline"* | Isolation, scale, copy space |
| Golden-ratio drift | *"subject slightly off the third toward center, organic balance"* | Naturalism without grid feel |
| Low placement | *"subject in the bottom quarter, environment towering above"* | Vulnerability, awe |

### The grammar tools

- **Leading lines:** *"the railing/road/shadow line leading from the corner of frame to the subject."* Name the line and where it starts.
- **Frame-within-frame:** *"framed by the doorway/arch/window/mirror edge"* — instant depth + focus.
- **Negative space:** active emptiness — *"two-thirds of the frame empty wall, the emptiness pressing on the subject."* Look-room rule: gaze gets space in front of it (*"looking into the open side of the frame"*) — or violate it deliberately for unease (*"staring into the near edge, space stacked behind her head"*).
- **Figure-ground separation:** subject must pop by tone, color, OR focus — name which: *"dark figure against bright fog"* / *"red coat against gray street"* / *"sharp against melted bokeh."*
- **Color blocking:** *"composition built from three flat color fields — mustard wall, gray pavement, black coat."*
- **Triangles & diagonals:** *"her limbs forming a triangle, the strongest diagonal running hip to shoulder"* — diagonals energize, horizontals calm, verticals dignify.
- **Visual weight balance:** a big empty area can balance a small subject; *"the lamp's glow in the upper-left counterweighing her in the lower-right."*
- **Depth in three planes:** foreground element / subject / background — name all three every time. One-plane images read flat and AI.
- **Tangent avoidance:** *"clear separation between her head and the horizon line — no elements touching edges or each other awkwardly."*

### Compositional registers by genre

Editorial fashion: deliberate imbalance, cropped limbs OK, tension over harmony. Commercial/product: stable thirds, generous copy space, nothing clipped. Cinema frame: depth planes + look-room + headroom discipline. Documentary: imperfect framing as authenticity — slight tilt, clipped edges.

---

## 2. Posing & model direction

Write poses as physical instructions, not vibes. The model executes "weight on the back hip, chin down, eyes up" far better than "confident pose."

### The body checklist (every figure, every frame)

1. **Weight:** never 50/50. *"Weight shifted onto the left leg, right knee softened, hip popped"* — contrapposto is the spine of all fashion posing.
2. **S-curve / line:** *"body forming a long S from ankle through hip to tilted shoulder."* For high-fashion: *"deliberately awkward angular shape, elbows out, broken-doll asymmetry."*
3. **Spacing:** limbs off the torso — *"arms away from the body leaving negative space at the waist."* Pressed-in arms widen and deaden.
4. **Hands need jobs:** *"one hand hooked in the pocket by the thumb, the other loosely holding the collar."* Banned: dead flat hands, full fists, fingers facing camera straight-on. Soft fingers, edges of hands toward lens, knuckles relaxed.
5. **Head/gaze tension:** body angled one way, face returning another — *"shoulders 45° away, face turned back to camera"* or eyes off-lens entirely: *"gaze past camera-left, mid-thought."*
6. **Chin geometry:** *"chin slightly down and pushed forward"* (defines jaw); chin up = haughty editorial.
7. **Asymmetry:** every pair (eyebrows, shoulders, hands, knees) differs slightly.

### Movement beats (the in-between frames)

The strongest editorial frames are between poses. Prompt the beat, not the pose:
*"mid-turn, coat flaring"* · *"caught mid-step, back heel lifting"* · *"adjusting the earring, elbow high"* · *"hair mid-flip, eyes closing"* · *"sitting down or standing up, neither fully"* · *"laugh decaying into a smirk"* · *"pulling the jacket over a shoulder, half-in."*

### Seated, leaning, floor

Seated: *"sitting at the front edge, spine long, legs extended asymmetrically — one bent, one straight."* Never deep-seated slouch unless brief is slouch. Leaning: *"shoulder blade against the wall, hips off it, one foot crossed."* Floor: *"legs as composition — long diagonals, knees at different heights, supporting arm locked."*

### Expression direction

Name the thought, not the emotion: *"expression of someone listening to an answer they don't believe"* beats "skeptical." Mouth: *"lips parted a breath"* / *"resting closed, jaw soft."* Eyes carry it: *"heavy lids, focus pulled to mid-distance."*

### Group blocking

Vary heights (*"one standing, one seated, one leaning"*), connect points (*"hand on the seated one's shoulder"*), unify eyelines OR scatter them deliberately, keep gaps unequal.

---

## 3. The critique rubric — systematic self-judgment

Run every output through this before accepting. Score 0-2 per item; regenerate anything under 16/22. This turns iteration from taste into procedure.

### A. Light logic (the #1 giveaway)
1. Single consistent key direction — every shadow agrees
2. Every highlight has a nameable source; reflections show the actual scene
3. Falloff is physical: bright near source, dark far, no sourceless glow

### B. Anatomy & physics
4. Hands: five fingers, natural joints, doing their assigned job
5. Fabric obeys gravity — wrinkles at bends, drape follows the body, hems hang true
6. Hair interacts with light and air (strands, flyaways) — not a helmet
7. Contact logic: feet/objects ground with contact shadows; held things compress fingers

### C. Texture truth
8. Skin has pores/imperfection at the resolution shown — no plastic
9. Materials read correctly (metal speculars, matte absorption, glass refraction)
10. Grain/noise uniform across the whole frame — patches of clean = composite tell

### D. Composition & intent
11. Clear subject hierarchy — eye lands where intended, background supports

**Hard-fail items (regenerate regardless of score):** garbled text anywhere · impossible reflection · extra/merged fingers · two shadow directions from one source.

### The audit prompt (run as a Framework 3 turn)

After generating, ask the model itself:
> *"List everything in this image that would reveal it as AI-generated to a professional photographer — light logic, anatomy, fabric physics, reflections, texture. Be merciless."*
Then fix the top 2-3 in an edit turn: *"Fix [issues]. Keep everything else exactly the same."* This generate→audit→repair loop is the single highest-leverage quality technique.

### Series consistency audit

For multi-image work add: same grain density across frames · same palette discipline · same lens behavior · identity match (run the five-point face check from `identity_lock_and_filmmaking.md`).

---

## 4. Angle grammar — and killing the AI default angles

### The AI angle tells (avoid unless asked)

AI images default to a narrow family of angles that instantly read as generated:

1. **The hero hover** — slightly low, slightly centered, subject facing camera dead-on with even headroom. The single most common AI angle.
2. **The floating camera** — a viewpoint no human could occupy: 2.5m high in a room with no ladder, hovering mid-air over a table, inside a wall.
3. **The perfect 3/4 portrait** — every face at the same flattering 30° turn at eye level.
4. **Center-stage isolation** — subject centered against bare air at chest height, no foreground, no occlusion.
5. **Drone-everything** — exteriors defaulting to elevated 30° down-angles nobody shot from the street.

### The fix: anchor the camera to a HUMAN OPERATOR

Real angles come from bodies holding cameras in real spaces. State where the photographer physically is:

> *"shot by someone standing in the doorway"* · *"from a seat across the aisle"* · *"camera at waist level, tilted up slightly — waist-level finder framing"* · *"crouched at curb height"* · *"from the second-floor window opposite"* · *"over the shoulder of someone at the next table"* · *"lying on the grass beside them"*

Operator placement buys three realism wins at once: plausible height, plausible distance/lens combination, and natural foreground occlusion (door frame, table edge, shoulders, railing).

### Real-angle vocabulary (with their jobs)

| Angle | Phrase | Job |
|---|---|---|
| Eye level at SUBJECT's height | *"eye level at the child's height — adult world looming above"* | Empathy; height belongs to the subject, not a default |
| Chest/waist level | *"waist-height candid, slight up-tilt"* | Street/doc honesty (waist-finder cameras shot here for decades) |
| Knee/curb level | *"knee height, street surface dominating the lower frame"* | Urban grit, sneaker frames |
| Tabletop level | *"lens at table height, cups looming in foreground"* | Intimate interiors, diner scenes |
| Standing tilt-down at a seated subject | *"standing height looking down at the seated subject — the natural conversation angle"* | Power, interview b-roll |
| Stairwell/landing oblique | *"from half a flight above, banister cutting the corner of frame"* | Found surveillance feel |
| Through-something | *"through the gap in shelves / between heads in a crowd / past a doorframe"* | The occluded human viewpoint |
| True overhead — only when motivated | *"directly overhead, flat-lay logic"* (food, evidence, bed) — give it a reason or skip |
| Mirror/window indirect | *"the subject seen only in the café window's reflection, street ghosted over them"* | Layered, non-frontal seeing |

### Anti-default checklist (one line per prompt)

State (1) operator position, (2) camera height in physical terms, (3) one occlusion the position creates, (4) a deliberate imperfection of the position: *"slightly too low, the table edge intruding"*. And rotate subject orientation: profiles, backs, 7/8 turns away — the world's photographs are not all faces at 30°.

**Add to the critique rubric:** Could a person with a camera physically stand where this image was taken — and would they have bothered? If the angle is floating, centered, and effortless, regenerate from a named operator position.


<!-- ═══════ FILE: nano-banana-prompter/references/photography_pro.md ═══════ -->

# Nano Banana — professional photography (studio rigs & recipes)

Real studio lighting and per-genre recipes. Pair with `references/creative_director_controls.md` (the lighting menu) and `references/composition_posing_and_critique.md`.

> **Field-validated (Round 13, `field_findings.md`) — ImagineArt, 2026-07-06.** The architecture twilight recipe (parallel verticals, interior-vs-dusk balance, reflecting-pool, long-exposure) scored PASS (strong, 21/22). Round 14: the landscape recipe (three-plane depth, golden-hour raking light, aerial perspective, deep focus) also scored PASS (strong, 21/22).

---

## Studio lighting rigs (name the rig, not "studio lighting")

| Rig | Setup | Use |
|---|---|---|
| **45/45** | key 45° to the side and 45° up, weak fill opposite | classic portrait modelling, defined cheekbone |
| **Clamshell** | big soft source above the lens + reflector/fill directly below | beauty — even, flattering, twin catchlights |
| **Book light** | key bounced into diffusion, then THROUGH a second diffusion | huge, wrapping, gentle falloff — luxe skin |
| **Negative fill** | black flag on the shadow side (subtract, don't add) | deepen falloff, sculpt a flat face |
| **Strip-light gradient** | tall strip softbox raking along a surface/body | gradient falloff, edge definition, product sheen |
| **Rim / kicker** | hard light from behind ¾ | separation from background |
| **Background light** | a dedicated light on the seamless | control the grey value / pop a gradient |

State the key's **direction and its shadow consequence** (validated): *"clamshell key from above, the under-jaw softly filled, twin catchlights top and bottom."*

## The six-shot product list (the coverage a product needs)

1. **Hero** — 3/4 angle, the money shot. 2. **Front** — straight-on, e-comm. 3. **Detail macro** — texture/logo/mechanism. 4. **Scale** — in-hand or beside a known object. 5. **In-context** — lifestyle use. 6. **Range/group** — the family or colorways. Shoot the master with room to crop (see `references/campaign_and_specialist_genres.md`).

## Background conventions by category

| Category | Background |
|---|---|
| Product e-comm | pure white seamless (RGB 255) with a real contact shadow, or clean float |
| Beauty | white-out, or deep saturated colour seamless |
| Food | textured surface — weathered wood, stone, linen — warm |
| Fashion | seamless paper (bold colour) or a real location |
| Jewellery | black acrylic with managed reflections, or a graduated sweep |

## Product failure modes

| Symptom | Fix |
|---|---|
| Product floats | *"grounded with a soft contact shadow directly beneath"* |
| Reflections show studio junk / AI noise | *"reflections show only a single softbox and dark surroundings"* |
| Plastic look | name the material + micro-texture (see Lever 4 in `creative_director_controls.md`) |
| Blown metal highlights | *"controlled specular roll-off, a gradient highlight, no clipped white"* |
| Even, sourceless light | name one key rig + a falloff side |

## Pro recipes by genre

- **Portrait** — 85mm f/2, soft key + negative fill, one clean catchlight, real skin texture, near-eye focus.
- **Food** — backlight law + the 10-minute "just-plated" energy (full recipe in `references/campaign_and_specialist_genres.md`).
- **Architecture** — parallel verticals (tilt-shift discipline), twilight balance, one light direction (`campaign_and_specialist_genres.md`).
- **Street** — 35mm, available light, anchor the camera to a human operator position (`composition_posing_and_critique.md` §4).
- **Landscape** — f/11–16 deep focus, golden or blue hour, a graduated sky, a foreground anchor for depth; three planes.

Default register is grounded: physically plausible light, rentable gear, buildable grades.


<!-- ═══════ FILE: nano-banana-prompter/references/creative_director_controls.md ═══════ -->

# Nano Banana — Creative Director controls

When the output looks decent but unmemorable, four levers lift it. Use each one verbatim.

> **Field-validated (Round 15, `field_findings.md`) — ImagineArt, 2026-07-06.** The four levers read distinctly in one frame (PASS strong, 21/22): a chiaroscuro hard key, Hasselblad 100mm f/2.8, Kodak Portra 400 pastel-and-grain, and herringbone-tweed-vs-silk material.

---

## Lever 1 — Lighting

| Lighting recipe | When to use | Sample phrase |
|---|---|---|
| Three-point softbox setup | Product, beauty, corporate headshot, packshot | *"Lit by a classic three-point softbox setup — key at 45° camera-left, fill from camera-right, hair light from behind."* |
| Chiaroscuro with high contrast | Mystery, drama, Renaissance portraiture | *"Chiaroscuro lighting with harsh high-contrast key, deep crushed black shadows."* |
| Golden-hour backlight with long shadows | Lifestyle, fashion editorial, romance | *"Golden-hour backlight from a low sun, long warm shadows raking across the foreground."* |
| Single hard window key, deep shadows | Painterly, Vermeer / Wyeth, period drama | *"Single hard window key from camera-left, no fill, deep painterly shadows."* |
| Neon multi-source | Cyberpunk, music video, club | *"Neon-lit, multiple coloured sources — magenta from screen-left, cyan from screen-right, sodium-vapour amber from above."* |
| Candlelit close-foreground | Intimate, period drama, ritual | *"Candlelit from a single foreground candle, warm 1800 K narrow throw, fall-off into total darkness."* |
| Overcast soft diffuse | Documentary, editorial photojournalism, lifestyle | *"Overcast soft natural daylight, no direct sun, even ambient fill from a high cloud ceiling."* |
| Studio rim light only | High-contrast product, fashion silhouette | *"Hard rim light only from camera-right and camera-left, the subject's front in deep shadow."* |
| Coloured gel | Editorial fashion, music photography | *"Studio strobe with magenta gel from camera-left and teal gel from camera-right, no white light at all."* |
| Practical motivated lighting | Cinematic realism | *"Practical lighting motivated by visible sources in the scene — the desk lamp, the window, the open laptop screen."* |

Always **name the source**. *"Cinematic lighting"* alone is the most common cause of generic output.

---

## Lever 2 — Camera, lens, and focus

### Camera brands as visual DNA

| Camera | Signature look |
|---|---|
| GoPro / action cam | Distorted ultra-wide, action immersion, slight fisheye |
| Fujifilm X-T5 / X100 | Authentic film-science colour, organic grain |
| Sony A7 IV / A1 | Clinical sharp digital, neutral colour science |
| Canon R5 | Slightly warm digital, smooth skin tones |
| Hasselblad medium format | Editorial elegance, large-format compression |
| Leica M11 | Pure documentary, restrained colour |
| iPhone 15 Pro | Modern phone aesthetic, slight HDR push, computational fill |
| Polaroid SX-70 / OneStep | Square, soft, milky highlights, faded edges |
| Disposable film camera | Raw flash, vignetting, nostalgia |
| Vintage 1980s point-and-shoot | Slight grain, warm cast, soft focus |

### Lens specifications

| Spec | Effect |
|---|---|
| `24 mm wide-angle` | Sweeping environments, exaggerated foreground |
| `35 mm` | Documentary, street, slight distortion |
| `50 mm` | Natural perspective, portrait standard |
| `85 mm portrait` | Subject isolation, beautiful background fall-off |
| `100 mm macro` | Extreme close detail, food, jewellery |
| `135 mm telephoto` | Compressed perspective, fashion runway |
| `200 mm long lens compression` | Heavily compressed depth, magazine fashion |

### Aperture / depth of field

| Spec | Effect |
|---|---|
| `f/1.4` or `f/1.8` shallow depth of field | Strong bokeh, subject isolation |
| `f/2.8` | Standard portrait |
| `f/5.6` | Balanced, slight background blur |
| `f/8` | Deep focus, environmental |
| `f/16` | Everything in focus, landscape |
| `tilt-shift miniature plane` | Toy-like compressed focus band |

### Angles

`low angle` · `high angle` · `eye-level` · `worm's-eye view` · `bird's-eye view` · `Dutch tilt` · `over-the-shoulder` · `aerial drone view`

Examples used together:
> *"Shot on a Hasselblad medium-format with an 80 mm lens at f/2.8, low angle, the subject filling the upper two-thirds of the frame."*

---

## Lever 3 — Color grade and film stock

### Film stock references that work

| Stock | Look |
|---|---|
| `Kodak Portra 400` | Warm pastel skin tones, soft fine grain |
| `Kodak Ektar 100` | Saturated vibrant, crisp |
| `Fujifilm Velvia` | Hyper-saturated landscape, deep greens / blues |
| `Cinestill 800T` | Tungsten-balanced night, halated highlights |
| `Ilford HP5 black and white` | Classic documentary B&W, mid-contrast |
| `Ilford Delta 3200 push-processed` | High-grain low-light B&W |
| `1980s amateur color print` | Slight magenta cast, warm grain |
| `1970s Kodachrome` | Warm saturated, slight blue shadows |
| `Polaroid 600 instant` | Soft, milky highlights, faded edges |
| `Silver gelatin black and white print` | Archival, documentary, deep blacks |

### Color grades

| Grade | Look |
|---|---|
| `Teal and orange cinematic grade` | Modern Hollywood standard |
| `Bleach-bypass processing` | Desaturated, high-contrast, gritty |
| `Muted teal cinematic grade` | A24, Denis Villeneuve mood |
| `Warm shadows and cool highlights` | Classic film look |
| `Warm amber midtones with crushed blacks` | 90s music video aesthetic |
| `Cool blue tones throughout` | Cold, clinical, melancholic |
| `Pastel desaturated` | Wes Anderson |
| `Vivid neon saturation` | Cyberpunk, music video |
| `Sepia toned monochrome` | Vintage, archival, nostalgia |
| `High-key bright with lifted blacks` | Beauty, advertising, fashion |

---

## Lever 4 — Materiality and texture

This is where most generic outputs go wrong. Don't ask for "a suit jacket" — ask for the **fabric**.

### Fabric and textiles

| Generic | Specific |
|---|---|
| Suit | Navy wool tweed with subtle herringbone weave |
| Shirt | Crisp white poplin cotton with mother-of-pearl buttons |
| Dress | Emerald silk crepe with hand-rolled hem |
| Coat | Camel cashmere wrap coat with tonal stitching |
| Sweater | Cream chunky-knit aran wool with cable detail |
| Jeans | Selvedge raw denim with copper rivets |

### Metals

| Generic | Specific |
|---|---|
| Metal | Brushed stainless steel with subtle linear grain |
| Gold | 18-karat yellow gold with high polish |
| Bronze | Patinated bronze with green oxidation at edges |
| Copper | Polished rose copper, slight warm tarnish |
| Silver | Sterling silver with antique-finish recessed details |

### Stone, wood, leather

| Generic | Specific |
|---|---|
| Stone | Honed Carrara marble with delicate grey veining |
| Wood | Reclaimed oak with deep grain and knot marks |
| Leather | Saddle-tan vegetable-tanned full-grain leather, soft burnished edges |
| Plastic | Glossy ABS plastic with subtle injection-mould seam |
| Glass | Hand-blown cobalt blue glass with slight bubbles |

### Skin and hair

| Generic | Specific |
|---|---|
| Skin | Smooth porcelain skin with natural micro-imperfections, subtle subsurface scattering |
| Older skin | Weathered skin with fine sun lines around the eyes, freckling across the cheekbones |
| Hair | Loose chestnut waves with natural shine and individual strand definition |
| Beard | Three-day salt-and-pepper stubble with individual hair texture |

### Generic vs. specific in a full sentence

**Generic:**
> *A man in a suit at a desk in an office.*

**Specific:**
> *A man wearing a charcoal three-piece tweed suit with a burgundy silk tie and matching pocket-square, seated at a leather-topped mahogany desk in a warm wood-panelled study, sunlight from a tall sash window falling across the desk surface and catching the brass desk lamp.*

The second sentence renders ten times more believably because every material is named.

---

## Putting all four levers together — a full Creative-Director prompt

> *"A close-up product shot of a wrist watch with a brushed stainless-steel case and a navy leather strap with cream contrast stitching, photographed on a smooth honed Carrara marble surface with subtle grey veining. The watch face shows ten past ten. Lit by a hard rim light from camera-right and a single soft fill from above, no other sources. Shot on a Hasselblad medium-format with a 100 mm macro at f/2.8, extreme close-up on the watch face filling the lower two-thirds of the frame. Colour grade: warm shadows and cool highlights, as if shot on Kodak Portra 160. Editorial luxury watch advertising aesthetic. Output in 4:5 aspect ratio."*

Subject material + composition + named lighting + named camera + named lens + named film stock + named genre. Reproducible to the millimetre.


<!-- ═══════ FILE: nano-banana-prompter/references/worked_examples.md ═══════ -->

# Nano Banana — ten worked examples

Full paste-ready prompts across genres. Each shows the craft layers working together. Adapt; don't copy blindly.

---

## 1. Product photography (material specificity)

> *"A close-up product shot of a wristwatch — brushed stainless-steel case, navy leather strap with cream contrast stitching — on honed Carrara marble with grey veining. Face reads ten-past-ten. Hard rim light from camera-right, one soft fill from above, no other sources. Hasselblad medium-format, 100mm macro at f/2.8, extreme close-up filling the lower two-thirds. Warm shadows, cool highlights, as if Kodak Portra 160. Output 4:5."*

Demonstrates Lever 4 (materials) + named single-source light. See `references/photography_pro.md`.

## 2. Editorial fashion portrait

> *"Editorial portrait of a model in an emerald silk-crepe gown that pours and ripples with liquid speculars. Studio, deep-shadow chiaroscuro key from camera-left, the right cheek falling into shadow, cast shadow running camera-right. 85mm at f/2, head and shoulders, deliberate off-center placement. Shot on medium-format, fine grain, muted teal grade. Pores and fine vellus hair visible, not airbrushed."*

Demonstrates fabric behavior + shadow-consequence light + realism close. See `references/realism_and_ugc.md`.

## 3. Multi-character storyboard

> *"Three sequential frames, same production look (Vision3 500T, fine grain, 40mm, teal-orange, 2.39:1): (1) WIDE — a detective enters a rain-lit diner, neon through the window; (2) MEDIUM — she slides into a booth opposite a nervous informant; (3) CLOSE — his hands fidget with a coffee cup. Keep both characters consistent across frames, obey the 180° line."*

Demonstrates the production-look block + coverage. See `references/identity_lock_and_filmmaking.md`.

## 4. Logo + character composition

> *"Compose: the character from the first reference (keep the face exactly) standing in a minimalist studio; the logo from the second reference on their cap, drawn onto the fabric with realistic curvature and lighting. Soft three-point light, 50mm, clean grey seamless. Output 4:5."*

Demonstrates reference-role assignment + logo-on-surface. See `references/generation_mechanics.md`.

## 5. Text-heavy poster with localisation

> *"A travel poster. Headline 'KYOTO' in a tall thin serif, top-centre; subhead 'Autumn in the old capital' in small Garamond beneath. A misty temple in maple-red foreground. Then render an alternate version with the headline translated to Japanese '京都' in elegant vertical brush calligraphy. Render at 2K. Generous margins, one accent colour."*

Demonstrates quoted text + localisation + 2K for type. See `references/text_rendering.md`.

## 6. Style transfer (Van Gogh portrait)

> *"Recreate the exact composition and facial features of the attached portrait in the style of Van Gogh's Starry Night — thick impasto brushstrokes, swirling cobalt-and-yellow background, visible canvas texture. Preserve the subject's identity and pose."*

Demonstrates Framework 4 with content preservation.

## 7. Conversational multi-turn edit

> T1: *"A cozy reading nook by a rainy window, warm lamp light, an empty armchair, 35mm, f/2."*
> T2: *"Add a tabby cat curled on the armchair. Keep everything else exactly the same."*
> T3: *"Make it night — the window dark, the lamp warmer. Keep the cat and the room identical."*

Demonstrates Framework 3 + "keep everything else exactly the same."

## 8. Web-search-grounded visualisation

> *"Search the current top headline in tech news. Summarise its mood in one word, then render an abstract editorial cover image expressing that mood — one bold colour field, a single symbolic object, minimal. Render the chosen word small in the corner in a thin sans-serif."*

Demonstrates Framework 5 (NB2/Pro). Verify any rendered facts.

## 9. Architectural mockup with material reference

> *"Using the stone-sample reference for the façade and the wood-sample for the soffits, render a twilight exterior of a single-storey modern house — interior lights on, exposure balanced so windows glow without clipping and the sky holds blue. All verticals perfectly parallel (tilt-shift discipline), 24mm, no keystone. One book open on a chair visible through the glass."*

Demonstrates material references + architecture rules. See `references/campaign_and_specialist_genres.md`.

## 10. Brand mood-board to deliverable

> *"From the attached mood-board (palette, type pairing, texture), produce a 4:5 launch post: a real-video-frame hero of hands holding the product caught mid-motion, the brand palette only, headline 'SHIPS TODAY' in the board's display face on a low-contrast upper-left, small wordmark bottom-left. Flat, no gradient, no glow. Render at 2K."*

Demonstrates brand-kit reuse + the posts workflow. See `references/creative_posts_copy_type_layout.md`.


<!-- ═══════ FILE: nano-banana-prompter/references/field_findings.md ═══════ -->

# Nano Banana — field-validated findings (the validation log)

Live test-round results — what the model *actually* does, scored via the critique rubric (`references/composition_posing_and_critique.md`). Consult this before trusting any "validated" claim, and **append a new round whenever you run one** (this is the skill's evidence base; it's kept here, out of `SKILL.md`, so it can grow without bloating the router).

> Provenance note: Rounds 1–7 ran on Nano Banana 2 @ 1K (imagine.art, June 2026); Rounds 8–9 on Nano Banana Pro (ImagineArt, June–July 2026). Round 8 validated the posts/graphic modules; Round 9 validated the three ethnicity-casting files. Round 10 field-validated the Frame Realism Engine and the Pakistan/music-video modules (ImagineArt, July 2026). Round 11 closed MODE A/D and field-validated the recent-ad UGC + auteur registers and the dark-tech packshot register. Round 12 closed series-consistency (identity lock) and validated Urdu text + two more director blocks. Round 13 field-validated a global cross-file batch (automotive, deep-skin beauty, liquid-physics product, the interview formula, a named film-look block, architecture). Round 14 field-validated streetwear, non-photoreal anime, a named tonal family, a photographer block, landscape, and apparel commerce — leaving only three utility files. Round 15 validated the last three utility files — with Rounds 10–15, every reference in the skill now carries live scored evidence.

## Round 1 (imagine.art — Nano Banana 2 @ 1K)

Tested four recipes live. What the model actually does:

- **Era frames are the strongest recipe.** The six-layer 1974 test landed near-perfect first pass — period car, station wagon, payphone, power lines, smog sky, wardrobe, slouch, even a period license plate. *"Nothing manufactured after [year] visible"* + 3 named props is confirmed high-leverage.
- **Light DIRECTION is the weakest adherence axis.** "Hard beam from camera-right" was re-keyed to a flattering frontal key. Fix: state direction twice — as source AND as shadow consequence (*"her right cheek in shadow, the wall shadow falling camera-left"*).
- **Subject scale drifts wide in environment frames.** Always state frame fraction: *"she fills half the frame height."*
- **Product label typography is flawless** even at 1K — trust the text engine for labels.
- **Anamorphic streak flares render but can look detached** — tie the streak to a visible in-frame source.
- **Fabric needs behavior words, not names.** "Chiffon" rendered generic; add *"sheer, translucent at the hem, floats behind the motion."*
- **Atmosphere cues (steam, wet asphalt, mixed temps) execute reliably.**

## Round 2 (corrected phrasings)

- **Shadow-consequence phrasing CONFIRMED** as the light-direction fix.
- **Frame-fraction language CONFIRMED** for scale.
- **Flare-tied-to-source CONFIRMED.**
- **Exact-geometry portrait patterns drift** — "split lighting, exactly half" rendered ~70/30 Rembrandt; force it with *"the shadow half completely unlit, no detail visible."*
- **"Just out of frame" sources tend to appear IN frame** — write *"the source is outside the frame and not visible"* if it must be hidden.
- **The model invents legible signage text unprompted** — add *"no readable text in the background"* for controlled frames.
- **Director blocks with concrete signatures are reliable** (a Deakins-register frame executed fully).

## Round 3 (UGC, photographer blocks, fabric physics, grading)

- **The UGC five-stack is fully confirmed** — a bathroom-selfie test was the most convincingly real frame of twelve. Nuance: "arm's length" in a mirror context renders as a MIRROR selfie; specify *"front camera at arm's length, no mirror in frame"* vs *"mirror selfie, phone visible."*
- **Photographer style blocks work like director blocks** (Avedon register executed nearly verbatim).
- **Fabric-behavior verbs drive material physics** (charmeuse vs cashmere rendered physically distinct).
- **Monochrome-plus-one executes cleanly** with explicit exclusion language.
- **Movement beats reliably produce frozen-motion energy.**

## Rounds 4–5 (apparel, streetwear, techwear — 10 tests)

- **Proportion-ratio language is the streetwear key — confirmed.**
- **Tribe blocks render with near-costume-design fidelity** (Y2K, gorpcore landed at editorial quality, garment text included).
- **Technical flats are production-usable** — render at 2K (small label text soft at 1K).
- **Ghost mannequin works for exterior volume**; interior back-neck label view unreliable — shoot as a separate detail crop.
- **Techwear hardware macro is a hero format** (DWR beading is the top realism phrase).
- **Reflective-under-flash over-amplifies** — scope it: *"only the zipper tape reflects."*
- **"Fisheye + strong barrel" can produce a full circular porthole** — say *"full-frame fisheye, subtle barrel, no circular vignette"* for rectilinear-ish wide.

## Round 6 (real-frame doctrine — studied against real film stills)

Codified the realism doctrine in `references/tonal_families.md` (darkness courage, subject-allowed-to-be-lost, one dominating practical, murky contaminated shadows, no courtesy rim, found-not-designed composition, weather-only-against-light, palette poverty). Both doctrine frames (3am parking lot, overcast laundromat) were the most convincingly real outputs of 17 tests. **For any "looks like a real film frame / real photo" brief, append the real-frame override.** Biggest lever: let most of the frame go dark and the subject be small, back-turned, partially illegible.

## Round 7 (night-physics corrections — 10 tests)

Corrections codified in `references/tonal_families.md` ("Night physics"):
- **The night-physics block is confirmed and transformative** — inverse-square falloff, rain-only-as-backlit-sparkle, a small hard blown hotspot with tight halation, broken specular streaks.
- **"A photograph, not a painting" + grain/shadow-noise kills the painterly tell.**
- **High-ISO documentary register** (handheld, ISO 6400, shadow noise, WB drift) is the most realistic night framing tested.
- Cautions: rain over-renders with broad sources (constrain "light drizzle, sparse"); "back-turned" sometimes flips (write "facing away, face not visible").
- Single-source scenarios obey falloff once stated — the model executes light physics well when, and only when, the prompt states it explicitly.

## Round 8 (live + scored — 2026-06-17, Nano Banana Pro)

Three prompts built from the rebuilt recipes were generated live on `nano-banana-pro` (ImagineArt) to validate the provisional content:

1. **Real-frame / UGC realism** (9:16) — realism stack + real-frame-from-video priority: a candid phone-video bathroom frame with anti-retouching negatives, mixed light, clutter, and explicit selfie-not-mirror geometry.
2. **Text + post** (4:5) — `text_rendering` + the posts recipe: a real-video-frame hero with headline "4K. No waiting." + a "NEW" kicker + an "imagine.art" wordmark on a low-contrast upper-left, flat palette, no gradient/glow.
3. **Graphic register** (1:1) — `graphic_and_illustration_styles`: flat-vector isometric, no gradients/3D, limited palette.

**Scored against the critique rubric — all three PASS; the rebuilt recipes are confirmed on Pro.**

- **Test 1 (realism) — PASS (strong).** Visible acne, cheek redness, forehead sheen, flyaway hairs (no plastic); genuine mixed light (cool fluorescent + warm bulb); candid off-center mid-reach; full clutter (toothbrush cup, mail, tube). Reads as a real camcorder/phone frame. The four-layer realism stack + real-frame priority are CONFIRMED. **Nuance:** the *"front camera at arm's length, no mirror"* geometry was NOT honored — it rendered a third-person camcorder-style frame (with a "REC / TUE 10:45 AM" HUD and a mirror present). Matches the Round 3 mirror-selfie finding: selfie-vs-camcorder geometry is finicky — over-specify a true front-camera selfie, and add *"no on-screen REC/timestamp overlay"* if the video-frame phrasing's HUD is unwanted.
- **Test 2 (text + post) — PASS (strong).** "4K. No waiting." rendered perfectly in bold high-contrast Didone; "NEW" kicker and "imagine.art" wordmark legible; headline seated on the dark upper-left copy-hole; flat warm palette + one red accent; no gradient/glow; asymmetric. A genuinely usable launch post. CONFIRMS the short-super text engine, the carve-the-copy-hole-into-a-real-frame technique, the anti-slop close, and the posts layout recipe. Minor: small in-screen UI text was slightly rough — expected at 1K; render type-critical work at 2K+.
- **Test 3 (graphic) — PASS.** True flat-vector isometric: no gradients, no 3D shading, no perspective convergence, exact cream/terracotta/green palette, long flat shadow, generous negative space. CONFIRMS the graphic/illustration register blocks.

**Promoted provisional → validated:** the realism four-stack, the real-frame-from-video hero, the copy-hole-into-a-real-frame technique + text supers + anti-slop close (posts module), and the flat-vector/isometric graphic register. **Still open:** structured/JSON prompting (not directly tested); carousel template-lock and safe-zone-as-% (not tested); precise selfie-vs-camcorder geometry.

## Round 9 (ethnicity casting field validation — 2026-07-06, Nano Banana Pro, ImagineArt)

Ten tests built from `global_ethnicity_casting.md`, `south_asia_casting.md`, and `uae_gulf_casting_and_ugc.md`; nine generated (15 scored frames incl. variants — the espresso-tone-lock/locs test returned a solid black frame: generation failure, **rerun pending**). Eight of nine tested recipes PASS. The three casting files are **field-validated**.

**Per-test results:**

- **Tamil deep-tone lock (Kanjeevaram, warm tungsten) — PASS (strong, 21/22).** Deep brown tone HELD under warm hall light with true specular sheen, no lightening, no ashy cast; gajra, zari border, temple gold all accurate. The tone-lock + expose-for-the-face + specular-sheen stack is CONFIRMED against the model's strongest lightening pull. **Nuance:** the model added a small bindi + forehead mark unprompted — culturally accurate for a Hindu wedding guest, but proof that Indian celebratory contexts trigger Hindu markers by default: on Indian Muslim/Christian casting, negate explicitly (as the marker rules already require).
- **Pakistani no-bindi check (Karachi office, lawn) — PASS (strong, 21/22, both variants).** ZERO bindi/sindoor cross-contamination with the explicit negation + real markers (kajal, dupatta). Lawn print rendered as visible small florals in the weave, not solid; dupatta drape natural. The #1 cross-contamination fail did not occur — the negation clause works.
- **Northeast-Indian render (Nagaland) — PASS (20/22).** East Asian features rendered on an "Indian" brief when explicitly stated — the un-renderable-unnamed finding is confirmed in both directions. **Artifact:** "handheld phone framing" produced a literal camera-app UI overlay in one variant — extend the Round 8 HUD rule: add *"no camera interface, no on-screen HUD, no timestamp"* whenever phone-capture words could be read as a screenshot.
- **Shalwar-kameez daily (Lahore dhaba UGC) — SPLIT.** Variant A PASS (19/22): shalwar kameez + waistcoat, doodh patti glass, truck art, dusk mix all landed; a "19:45" timestamp HUD appeared (same Round 8 behavior), and the front-camera-selfie geometry was again NOT honored (third-person frame, no arm/phone) — the selfie-geometry weakness is now confirmed across Rounds 3/8/9. Variant B FAIL (14/22): register collapsed into HDR-editorial travel look — blown sunset saturation, invented legible truck text ("PAKISTAN ZINDABAD" — Round 2 signage finding recurring). **Fix codified:** UGC frames with dusk/sunset skies need the register pinned — *"muted realistic colors, no HDR glow, no saturated sunset"* — plus *"no readable text"* unless copy is quoted.
- **Pashtun register (Peshawar) — PASS with caveat.** Variant A strong (21/22): pale green eyes, weathered fair skin, full white beard, pakol correct (no dastar/keffiyeh confusion), post-Jummah crowd real. Variant B (17/22) dropped the "full white beard" to short stubble and muddied the eye color — **attribute slippage across variants of one prompt is real: every regeneration needs the full identity block restated; variants are not free.**
- **Mixed Dubai crowd (anti-homogenization) — PASS (both variants, 20/22 & 19/22).** Genuinely distinct tones, builds, and faces across South Asian, Emirati, Filipino, and European subjects — *"no two faces alike"* + named-tone-per-subject is CONFIRMED as the homogenization killer. Kandura + turban-wrapped ghutra (no agal) correct. **Caveat:** background signage invented semi-legible Arabic and a misspelled brand ("CHANIC") — crowd/retail frames need *"no readable text"* or exact quoted copy.
- **Emirati woman (shayla style honored) — PASS (strong, 21/22, both variants).** Loose shayla with hair visible rendered exactly as specified — no auto-full-coverage, no niqab default; open-front greige abaya loose, henna and table clutter all present. The state-the-actual-style rule is CONFIRMED against the auto-veiling prior.
- **Agbada deep-skin exposure (Lagos groom) — PASS (strong, 21/22).** Exposed for the face, rich specular life on cheekbones/forehead, zero ashy-grey, tone held under warm tungsten; agbada + fila embroidery accurate. The melanin-rich lighting craft is CONFIRMED.
- **Anti-same-face (Seoul trio) — PASS (strong, 21/22, both variants).** Three enumerated faces rendered genuinely distinct (eyelids, face shapes, ages, builds). Per-subject enumeration is CONFIRMED. Bonus: Korean signage (서울분식, 떡볶이) rendered correctly unprompted — CJK signage is strong on Pro.

**Promoted provisional → validated:** the five-axes casting system, tone-lock clause + deep-skin lighting craft, marker negation (bindi/sindoor), explicit-feature casting (Northeast India, Pashtun), shalwar-kameez-daily register, shayla-style specification, per-subject enumeration + "no two faces alike", and heritage-dress accuracy (Kanjeevaram, agbada/fila, kandura/ghutra, lawn prints). **New rules from this round:** (1) restate the full identity block on EVERY variant/regeneration — attributes slip between runs of the same prompt; (2) pin the UGC register on dusk/sunset frames (*"muted realistic colors, no HDR glow"*); (3) phone-capture language needs *"no camera interface, no HUD, no timestamp"*; (4) crowd/retail/vehicle frames need *"no readable text"* or exact quoted copy (Arabic especially). **Still open:** espresso tone-lock + locs anti-loosening (black-frame failure — rerun); series-consistency of a locked cast across edit turns.


## Round 10 (frame-realism engine + new modules — 2026-07-06, ImagineArt)

Five of six planned validation frames were generated live (the MODE E pastry-chef clean frame is still pending). Scored against the critique rubric. **All five PASS (strong). `frame_realism_engine.md` is field-validated; the Pakistan Ramadan and music-video neon registers are confirmed.**

- **MODE B warm interior / skin benchmark (older man, close-up) — PASS (strong, 21/22).** The skin-truth pillar landed almost perfectly: mottled uneven colour (warm cheek/nose flush, cool under-eye), broken specular (oily forehead/nose, matte elsewhere), warm subsurface glow through the ear, wet reddened asymmetric eyes with a single matched catchlight, soft pore/moustache texture reading as mass not crunchy strands. Single warm lamp camera-right, real falloff, far side in warm shadow, lamp blooms without clipping, lifted colour-holding blacks, integrated grain. Skin tail + film-scan grade tail CONFIRMED on Pro. Benchmark-grade.
- **MODE C motivated colour chiaroscuro (red-gel teen) — PASS (strong, 21/22).** Near-black base, one hard red source frame-right, far side to red-black, red as the single anchor, posters dissolved to soft red bokeh; acne/sweat topography survived the coloured light, wet eyes, matched red catchlight. Colour-in-shadow + single-anchor + motivated-hard-source CONFIRMED.
- **Physical-consistency + MODE E clean (sunglasses / mirror) — PASS (strong, 20/22).** THE correction proof: the clean-register tail produced a bright, true-colour, un-grimy frame that is still real — visible cheek redness, forehead sheen, freckles, no plastic smoothing, no imposed grain/haze/desaturation. The research-added consistency pass held: mirror reflection consistent with the scene, a small correct reflection in the sunglass lenses, a five-finger hand with natural contact at the temple. CONFIRMS *realism ≠ grime*, MODE E, the clean-register grade tail, and the reflection/anatomy pass.
- **Pakistan Ramadan iftar key art — PASS (strong, 20/22).** Three generations round the dastarkhwan, warm hanging lamp camera-left as the anchor, fairy-light bokeh, dusk window, Rooh Afza jug (red anchor), dates/pakoras/apples, steam, reaching hands; shalwar kameez + dupattas, varied Pakistani faces, ZERO bindi/sindoor. `pakistan_ads_and_directors.md` Ramadan register CONFIRMED. **Nuance:** "reserve clean space upper-right for a logo" rendered as a faint visible rectangle in-frame. Minor: the mother's skin skewed slightly more polished than the rest (acceptable for aspirational key art; restate the skin tail per subject for full mottling on all faces).
- **Music-video neon retro-noir (red-suit singer, rain) — PASS (strong, 20/22).** Magenta/cyan signage bokeh, warm tungsten practicals + a yellow-taxi headlight tied as sources, rim on the shoulders, near-black base, red suit as the single anchor, wet-asphalt reflections, rain, look-room; wet real skin. `music_video_styles_and_directors.md` neon retro-noir register CONFIRMED.

**Promoted provisional → validated:** the Frame Realism Engine (restraint finish + One Law, the skin-truth pillar, MODE B/C/E, the clean-register split so *realism ≠ grime*, and the physical/anatomical/reflection-consistency pass); the Pakistan Ramadan register; the music-video neon retro-noir register. The skin tail and BOTH grade tails (film-scan + clean-register) hold across warm, coloured, clean, and night frames.

**New rule from this round:** never prompt "reserve space for a logo/text" as a literal instruction — the model may draw a placeholder box. Leave negative space and composite marks in post.

**Still open:** MODE A (cold institutional) and MODE D (natural daylight crowd) untested; the MODE E pastry-chef clean frame (a second clean data point) pending; `recent_ad_trends_and_directors.md` untested (its registers largely reuse the realism/UGC stack validated in Rounds 3/8).


## Round 11 (ad batch — closes MODE A & D — 2026-07-06, ImagineArt)

Six ad frames (two variants each) generated live and scored. **All six PASS (strong). MODE A and MODE D are now closed — all five realism modes A–E are field-validated — and the Pakistan humor/food registers, the dark-tech packshot register, the Dougal-Wilson auteur block, and the recent-ad UGC register are confirmed.**

- **FMCG masala food hero (clean/appetising) — PASS (strong, 21/22).** Backlit steam glowing, gleaming saffron-red rice grains, oil sheen, star anise/cardamom, egg, fried onions, raita + lemon, dark-wood table with a real contact shadow; true appetising colour, clean but not plastic, no imposed grain/haze. The clean-register applied to food is CONFIRMED.
- **Humor telecom (Ufone/Jazz register) — PASS (strong, 20/22).** Uncle mid-gift-handout, relatives delighted on the left, the overlooked deadpan cousin empty-handed at the right edge — the gag reads. Bright even light, tiled floor, framed Urdu calligraphy, ceiling fan/AC, varied Pakistani faces, no bindi. Pakistan humor register CONFIRMED.
- **Premium dark-tech packshot — PASS (strong, 21/22).** Matte-black case on black glass, chrome hairline edge-light tracing the silhouette, deep-but-not-crushed reflection, dust-free, hairline chamfer speculars, consistent reflection, clean not plastic. `commercial_framing` dark-tech + clean product realism CONFIRMED (no person).
- **MODE A cold institutional (bank) — PASS (strong, 20/22) — CLOSES MODE A.** Cool fluorescent + tall daylight windows blooming without clipping, desaturated cyan-green institutional cast, teal-green shadows, skin cooled but blood-warm in the midtones, long-lens glass-architecture compression, subject the first read. MODE A CONFIRMED.
- **MODE D natural daylight, Dougal-Wilson beverage — PASS (strong, 20/22) — CLOSES MODE D.** Golden-hour rooftop, held bloomed sky, gently desaturated true colour, backlit condensation on the bottle (single anchor), city haze with aerial falloff, waist-level candid, warm human beat. MODE D + the Dougal-Wilson auteur block CONFIRMED. **Nuance:** one variant substituted Lahore Badshahi-style minarets for the stated "Karachi" skyline — name the exact skyline or add "no iconic landmarks."
- **Social-native UGC skincare (recent-ad register) — PASS (strong, 20/22).** Front-camera arm's-length 9:16, off-centre with the head near-clipping, mixed warm-bulb/cool-window light, real bedroom clutter (open wardrobe, mug, charging cable, taped poster), genuinely real skin (acne, cheek redness, forehead sheen, flyaways, no airbrush), no HUD/timestamp. `recent_ad_trends_and_directors.md` UGC register CONFIRMED; the no-HUD + anti-retouching rules held.

**Promoted provisional → validated:** all five Frame-Realism modes A–E (A and D closed this round); the Pakistan humor + FMCG-food registers; the dark-tech packshot register (`commercial_framing`); the Dougal-Wilson auteur block and the recent-ad UGC register. **With Rounds 10–11, `frame_realism_engine.md`, `pakistan_ads_and_directors.md`, `music_video_styles_and_directors.md`, and `recent_ad_trends_and_directors.md` are all field-validated.**

**New rule from this round:** for city-specific exteriors, name the exact skyline/landmark or add "no iconic landmarks, generic [city] residential rooftops" — the model defaults to famous monuments.

**Still open:** the MODE E pastry-chef clean frame (optional second clean data point); series-consistency of a locked cast across edit turns (carried from Round 9).


## Round 12 (identity lock, director blocks, Urdu text — 2026-07-06, ImagineArt)

Four concepts generated live (the identity test as a 3-frame sequence via the reference-image workflow). **All PASS (strong). Series-consistency — the last major open item — is now closed, and Urdu text plus two more director blocks are confirmed.**

- **Identity-lock ad sequence (3 frames) — PASS (strong, 20/22).** One character "Bilal" held across a wide chai-stall establisher (Frame 1), a medium fabric-shop shot (Frame 2, Frame 1 attached as img2img reference), and reused in the Eid end-frame — same face, beard, mole, brows, pale-blue shirt throughout. `identity_lock_and_filmmaking.md` + series-consistency CONFIRMED via generate-then-reference + restate-the-identity-block-verbatim. **Nuance:** fine markers (the brow scar) didn't always render; the reference image carries the gestalt face reliably but not every enumerated micro-detail — restate the full block every frame.
- **Asim Raza emotional director block — PASS (strong, 21/22).** Forehead-to-forehead mother/daughter in a sunlit courtyard, golden rake light, marigold as the single anchor, dust in the light, deeply real skin (mottled, freckled, rosacea flush). Soulful folk-warmth + polished cinematography — the block reads. Pakistani ad-director blocks CONFIRMED.
- **Hype Williams music-video block — PASS (strong, 20/22).** Fisheye barrel, electric-blue colour-drench, magenta rim, shiny metallic jacket, shades, hand-to-lens, saturated high-gloss — with real skin under the gloss. Confirms music director blocks AND that a **stylised register correctly skips the film-scan realism tails** (the don't-force-realism control). **Nuance:** the full-frame fisheye produced a circular porthole vignette (blue circle on black) — add "full-frame fisheye, no circular vignette" for a rectilinear-ish fill (matches Round 4).
- **Bilingual Urdu end-frame — PASS (strong, 20/22).** "دل سے دل تک" rendered in correct joined gold nastaʿlīq, RTL, with "From heart to heart" and an "EID MUBARAK" kicker, warm lantern/fairy-light bokeh, character reused. `text_rendering.md` for Urdu CONFIRMED on Pro (previously only CJK).

**Promoted provisional → validated:** identity lock + series-consistency (reference-image workflow); the Asim Raza director block; the Hype Williams music-director block + the stylised-register-skips-realism control; Urdu/nastaʿlīq text rendering.

**New rules from this round:** (1) the img2img reference carries the gestalt face, not every enumerated micro-marker — restate the full identity block on every frame and don't rely on a lone scar/mole to survive; (2) add "full-frame fisheye, no circular vignette" when a fisheye should fill the frame rectilinearly.

**Effectively closed:** every module and all five realism modes are now field-validated (Rounds 10–12). **Still open (minor):** consistency across CONVERSATIONAL edit turns specifically (this round used img2img references, the more reliable path); the optional MODE E pastry second data point.


## Round 13 (global cross-file batch — 2026-07-06, ImagineArt)

Six frames across six files, deliberately global and non-Pakistani. **All six PASS (strong).**

- **Automotive dusk hero (`commercial_framing`/`campaign`) — PASS (strong, 21/22).** Matte-grey EV on a wet blue-hour plaza; real reflection streaks down the body, held paint highlights with no clipped speculars, parallel tower verticals, wet-concrete mirror reflections, one warm window glow. Automotive register + reflection-streak grammar CONFIRMED.
- **Beauty clamshell, deep-skin (`apparel_and_beauty` + `global_ethnicity`) — PASS (strong, 21/22).** Deep rich-brown West African skin exposed for the face — luminous, never ashy — cheekbone/nose specular sheen, warm subsurface at the ears, real pores and natural marks, matched catchlight. Clamshell rig + expose-for-deep-skin CONFIRMED in a beauty context.
- **Beverage crown-splash, high-speed (`commercial_framing` practical elements) — PASS (strong, 20/22).** A true crown-rim of droplets with surface tension, varied droplet sizes, suspended lemon, real condensation, backlit amber glow; label text rendered cleanly ("SPARKLE LEMONADE"/"ZEST"). Liquid-physics + high-speed capture CONFIRMED.
- **Cinematic documentary interview (`closeups_and_interviews`) — PASS (strong, 21/22).** Japanese woman, soft Rembrandt key with the shadow side to camera, negative fill, lavalier mic, off-lens eyeline with look-room, warm practical bokeh, letterboxed; real aged skin. Seven-step interview formula CONFIRMED.
- **Blade Runner 2049 film-look (`film_look_references`) — PASS (strong, 21/22).** Lone coated figure dwarfed in a vast brutalist hall, single-colour amber flood, volumetric haze, hard light shaft, monumental scale, anamorphic. The paste-the-signatures-not-the-title rule CONFIRMED for a named film block.
- **Architecture twilight (`campaign`/`photography_pro`) — PASS (strong, 21/22).** Concrete-glass museum, warm interior balanced against deep-blue dusk, parallel verticals (no keystone), reflecting-pool mirror, soft figures for scale, long-exposure water. Architecture twilight-balance register CONFIRMED.

**Promoted provisional → validated:** automotive register + reflection grammar; beauty clamshell + deep-skin exposure; the liquid-physics/high-speed practical-elements library; the seven-step interview formula; named film-look blocks; the architecture twilight register. `commercial_framing_and_set_design.md`, `closeups_and_interviews.md`, `film_look_references.md`, `apparel_and_beauty.md`, `campaign_and_specialist_genres.md`, and `photography_pro.md` now all have live evidence.

**Still open (queued for R14+):** streetwear tribes, non-photoreal graphic registers (anime/3D/line-art), named tonal families, photographer style blocks, landscape, and apparel commerce formats (ghost mannequin).


## Round 14 (library sweep — 2026-07-06, ImagineArt)

Six more across six files, global. **All six PASS (strong).**

- **Streetwear cleanfit fit-pic (`streetwear_and_genz`) — PASS (strong, 21/22).** Oversized boxy ecru tee over wide-leg charcoal trousers (clear proportion ratio), white sneakers, crossbody, contrapposto with a hand in pocket, hard wall-shadow diagonal, real skin. Proportion-ratio + tribe + wear-state grammar CONFIRMED.
- **Anime/manga still (`graphic_and_illustration_styles`, non-photoreal) — PASS (strong, 20/22).** Cel-shaded schoolgirl on a dusk platform, blurred train, clean linework, painterly BG, limited palette — correctly carrying NO photoreal texture, grain, or realism. Confirms a non-photoreal register beyond flat-vector AND that non-photoreal briefs correctly skip the realism stack.
- **"Old-money mocha" tonal family (`tonal_families`) — PASS (strong, 21/22).** Camel-coat man in a wood-panelled library, warm mocha-cream palette, low saturation, tobacco shadows, window key, no vivid anchor — the named tone held independent of subject. Named-tonal-family selection CONFIRMED.
- **Gregory Crewdson tableau (`photographer_styles_and_eras`) — PASS (strong, 21/22).** Bathrobed woman on a wet suburban dusk street, porch lights + streetlamp, mist, balanced ambient/practicals, meticulous stillness, tiny off-centre figure, period cars — signatures-not-the-name CONFIRMED for photographer blocks.
- **Patagonia landscape (`photography_pro`) — PASS (strong, 21/22).** Turquoise river winding to snow peaks, golden raking light, lupins in a sharp foreground, aerial-perspective falloff, deep focus. The landscape recipe (three-plane depth) CONFIRMED.
- **Ghost-mannequin jacket (`apparel_and_beauty` commerce) — PASS (strong, 20/22).** Olive field jacket as a filled invisible-mannequin 3D shape, hollow collar and back-neck showing through, seamless white, soft even light, brass snaps, four flap pockets, topstitch, twill weave. The ghost-mannequin e-comm format CONFIRMED (note: the back-neck-through-collar rendered well here, better than the Round-4/5 interior-label caveat).

**Promoted provisional → validated:** streetwear proportion/tribe grammar; a non-photoreal anime register (+ the confirmation that non-photoreal correctly drops the realism stack); named tonal-family selection; photographer style blocks; the landscape recipe; the ghost-mannequin commerce format.

**Still open (final Round 15):** only three utility files remain untested — `styling_and_set_design.md` (four-layer set dress), `structured_prompting.md` (JSON/variable-isolation), and `creative_director_controls.md` (isolated lighting/lens/stock/material levers).


## Round 15 (final utility sweep — library complete — 2026-07-06, ImagineArt)

The three remaining utility files. **All three PASS (strong). Every reference in the skill is now field-validated.**

- **Four-layer set dress (`styling_and_set_design`) — PASS (strong, 21/22).** A watch-repairer's workshop read all four layers — architecture (cracked plaster, sash window, worn floor), function (loupe stand, screwdriver row, green mat, parts tray, angle-poise lamp), inhabitant (taped family photo, enamel mug, wall calendar, cardigan on the chair), today (a half-disassembled watch under the loupe, tweezers, cold tea, glasses on an open ledger). The room characterises its absent owner through props alone. CONFIRMED.
- **Structured / JSON prompting (`structured_prompting`) — PASS (strong, 21/22).** A JSON prompt was honoured field-for-field — a Filipino man in a velvet-collar overcoat, single frosted-window key, look-room, film-scan finish. Variable-isolation CONFIRMED on Pro; prose still preferred for pure scene feel.
- **Creative-director controls (`creative_director_controls`) — PASS (strong, 21/22).** All four isolated levers read distinctly in one frame — a chiaroscuro hard window key (deep unlit shadow side), a Hasselblad 100mm f/2.8 medium-format look, Kodak Portra 400 pastel warmth + fine grain, and herringbone-tweed-vs-cream-silk material. The model even rendered the control labels as a caption card. Each lever lands independently. CONFIRMED.

**Promoted provisional → validated:** the four-layer set-dress system; structured/JSON prompting with variable-isolation; and the isolated creative-director levers (lighting recipe / camera-lens / film stock / material).

**Library status: COMPLETE.** Across Rounds 1–15, every reference file in the skill now has live, scored evidence. No open items remain except optional extra data points and consistency across conversational edit turns specifically (the img2img reference workflow is already validated, Round 12).


## New modules pending validation (added 2026-07-06)

Two deep regional casting modules were added after Round 15 and are **not yet field-validated** — queue them for Round 16:
- `references/mena_casting.md` — MENA beyond the Gulf (Levant, Egypt/Nubia, Maghreb, Iraq, Iran; Amazigh/Kurdish/Persian/Nubian). Watch for: over-veiling, desert default, Persian-as-Arab, Nubian/Saharan lightening.
- `references/southeast_asia_casting.md` — maritime + mainland SEA incl. Melanesian Papuans. Watch for: the East-Asian-default face, one-country-dress clichés, and lightening of Khmer/Filipino/Melanesian skin.
- `references/football_and_fifa_frames.md` — football/FIFA action, crowd & POV frames. Watch for: clone-stamped crowds, over-clean turf/kit, blown floodlights, posed-at-lens players, and any real-player-likeness/logo leakage. Test a freeze header, a pan sprint, a knee-slide, a stands-POV tifo, and a face-paint fan.


## Round 16 (framing, scene grammar & continuity — 2026-07-08, ImagineArt, live Cowork session)

Validates the new `references/framing_scene_grammar_and_continuity.md`. Two batteries: a 3-frame continuity-locked commercial sequence ("KOHA" coffee, problem→solution) and 10 single frames, one per scene type / composition system. Model: nano-banana-pro, 1K.

### Battery A — 3-frame commercial sequence (continuity ledger test)

- **First pass:** grade flip (cool dawn → warm gold) at the product beat LANDED; axis + light direction held across all three frames; packshot headline + tagline rendered clean. THREE DRIFTS: hair (loose → bun) and face drift in frame 2 (text-only ledger, no reference image); countertop material drifted across all three frames; packshot label body copy rendered as lorem gibberish.
- **Repair pass:** frame 2 regenerated with frame 1 as img2img reference → identity, hair, and set all locked. Frame 3 regenerated with exact quoted label copy ("KOHA / COFFEE / Moka Blend / NET WT 250g" + "no other text on the label") → label rendered verbatim, zero gibberish.
- **CONFIRMED:** the verbatim continuity ledger holds wardrobe, props, light direction, and set anchors — but NOT faces or hair state. Identity across frames REQUIRES a reference image, not description (consistent with Round 12). Quoted-copy + "no other text" kills placeholder-gibberish labels.

### Battery B — 10 scene-type frames. 10/10 usable; 8 strong passes, 2 partial.

1. **Establishing EWS, 21:9 — PASS (strong).** Sub-10% figure on the lower-right third, post-line + causeway leading lines converge, three depth planes with fog falloff, cold grade. The full establishing package lands in one prompt.
2. **Dialogue OTS dirty single — PASS with finding.** Lamp-pool falloff, 20% foreground shoulder, mid-speech mouth all landed. FINDING: the prompt contradicted itself (shoulder frame-RIGHT but "looks off-lens LEFT") — the model resolved toward spatial logic and aimed the gaze at the shoulder. RULE: in OTS, the eyeline must point INTO the foreground shoulder; never state a direction that fights the geometry.
3. **Confrontation power staging + Dutch — PASS (strong).** Foreground dominance, subordinate small/soft/turned, ~8° cant, mixed dusk blue + tungsten practical. NOTE: her eyes landed at-lens — "no gestures at camera" does not cover gaze; always state off-lens eyeline explicitly.
4. **Action peak freeze — PARTIAL PASS.** Apex-of-vault freeze, airborne oranges with correct gravity, dust shafts, grime all landed. NOT honored: "crate mid-shatter" rendered intact (need explicit "splintering, broken slats, wood fragments mid-air"), and edge-bystander motion blur was minimal. Peak-freeze register is reliable; selective per-element blur is weak.
5. **Journey panning register, 21:9 — PARTIAL PASS.** Strict profile, left-to-right, lead-room, backlit rim: all landed, frame is beautiful. NOT honored: background rendered as shallow-DOF bokeh, not horizontal pan streaks. "Panning register / streaked background" alone is insufficient — spell out "horizontal directional smear on every background element, 1/60s shutter" and expect only partial compliance at 1K.
6. **Intimate frame-within-frame, 135mm — PASS with finding.** Doorway frame, tungsten pool, dense blacks, unaware subject: excellent. FINDING: the model CENTERED her inside the doorway despite "off-center lower-left" — subjects gravitate to the center of any inner frame. Anchor to an edge of the aperture ("seated at the left edge of the doorway opening") and accept a centering pull.
7. **Mirror reveal — PASS (strong).** Hidden-in-reflection staging read perfectly; bonus reversed door lettering. NOTE: reflection optics are narratively correct but physically approximate — stage the reveal READ, don't demand strict mirror geometry.
8. **Aftermath high-angle, 21:9 — PASS with finding.** Evidence-not-event, hierarchy via the lit intact cake, mist, footprints: all landed. FINDING: the operator anchor LEAKED — "from the top of a step ladder" put a ladder in the frame. Phrase anchors as height/position ("elevated ~2.5m at the entrance"), not as physical objects, or add "the ladder itself is not visible."
9. **Planimetric tableau, 4:3 — PASS (strong).** Dead-center figure, mirrored sconces/doors, runner leading line, deep focus, one-asymmetry (yellow suitcase). FINDING: the suitcase came out in the wrong hand — anatomical left/right on subjects mirror-flips; use screen-side language ("on the frame-right side of his body") for anything hand-specific.
10. **Silhouette figure-ground, 9:16 — PASS (strong).** Pure black shape, halation hugging the blown doorway only, volumetric dust, and the three-layer VERTICAL stack (lit floor strip / figure / heavy bag) composed correctly. Vertical recomposition grammar CONFIRMED — the model stacks planes in 9:16 when told to.

**Promoted provisional → validated:** the shot-size + composition-system + operator-anchor frame grammar; scene-type framing packages (establishing, confrontation, intimate, reveal, aftermath, tableau, silhouette); 21:9/4:3/9:16 ratio recomposition; the continuity ledger (with the identity-needs-a-reference carve-out); quoted-copy label enforcement.

**New failure modes catalogued (Round 16):** OTS eyeline-vs-shoulder contradiction; gaze-at-lens unless off-lens stated; "mid-shatter" renders intact; selective motion blur and pan-streak weakness; inner-frame centering pull; operator-anchor object leak; anatomical left/right flips.


<!-- ═══════ FILE: nano-banana-prompter/references/surgical_edits_and_higgsfield_routing.md ═══════ -->

# Surgical edits, prop sheets & the Higgsfield/Soul routing lane

*Source: the Lira prompt-optimization discipline. This file covers three things the core skill doesn't: (1) the **structured edit block** that makes Nano Banana edits behave like post-processing instead of regeneration, (2) **prop / product-object generation**, where NBP is the right tool rather than a Soul model, and (3) the **cross-tool routing lane** — when the brief belongs on Higgsfield Soul 2.0, Soul Cinema, Cinema Studio AI Cast, Seedream 4.5, or GPT Image 2 instead of (or after) Nano Banana.*

Read this whenever the brief is an **edit of an existing frame**, a **prop/product asset**, a **location view change**, or a **character-consistency job spanning many shots**.

---

## 0. The 4-D pass (run it before writing anything)

Every non-trivial build goes through four internal stages, then delivers.

1. **DECONSTRUCT** — core intent, key subjects, context. Which model and surface. Output constraints (aspect, single image vs sheet, edit vs generation). What's given vs what's missing.
2. **DIAGNOSE** — gaps in clarity: camera angle, light, palette, subject count, framing. Does the request risk a known failure mode (illustration drift, tattoo/text smear, multi-character collapse, bloated 400-word prompt)?
3. **DEVELOP** — pick technique by request type (character / location / prop / edit / texture pass / micro-edit), assign the model a role (camera, lens, cinematographer mood), layer context, impose structure.
4. **DELIVER** — construct, format to platform + complexity, add brief application notes (what to watch, what to toggle in the UI).

**Operating modes.** *DETAIL* is the default on ambiguous or high-stakes builds: gather context, ask **2–3 targeted questions max**, then optimize. *BASIC* when the user just wants the prompt now ("give me the full thing", "go", or a pasted prompt + "rewrite this") — fix the key problems, apply the core techniques, deliver immediately. Read the signal; never ask more than three questions.

**Response shape.** Lead with the prompt in a code block, then 1–3 lines of *what changed*. Complex builds: prompt first, then a short table of what was baked in and why. Before/After tables for diffs. Don't pad.

---

## 1. The surgical-edit template (the core move)

An edit is **post-processing of the original**, not a rebuild. The original is the base; you change the minimum and lock everything else. The core skill's *"keep everything else exactly the same"* is the one-line version — this is the structured version, and it's what you use when the edit matters.

```
Edit the image: [one-line goal].

CHANGE: [only the single thing that changes, described precisely].

PRESERVE EXACTLY:
- [every element that must stay identical: face, hair, wardrobe, props,
  positions, wall/floor, camera angle, all existing shadows]
- Color grade, palette, contrast, grain, falloff

ONLY CHANGE: [restate the one change]. 100% identical otherwise.
```

Rules that make it work:

- **Minimal CHANGE, exhaustive PRESERVE.** The asymmetry is the point. If the PRESERVE list feels tediously long, it's the right length.
- **One change per pass.** Two changes in one prompt is two passes.
- **Removal is legal in edits** — unlike generation prompts, *"Remove the lamppost"* works. But always pair the removal with what fills the gap: *"continuous brick wall behind"*. A removal without a fill is an invitation to hallucinate.
- **CAPS section blocks belong ONLY in edit prompts.** Never put `CHANGE:` / `PRESERVE EXACTLY:` headers in a generation prompt — generation wants flowing prose.
- **Diagnostic:** if the user says you overdid it or it drifted from the ask, you changed too much. Lock more, change less. That is always the fix.
- **A frame that needs rebuilding is not an edit.** Regenerate it from scratch (Soul model for characters/scenes, or a fresh Nano Banana generation) rather than trying to edit your way there.

---

## 2. The edit escalation ladder — fixed order

Never skip a rung. Each tool has one job.

| Rung | Tool | Job | Do NOT use it for |
|---|---|---|---|
| 1 | **Nano Banana / NBP** | **Every edit starts here.** Post-processing of the original: minimal change, everything else preserved pixel-for-pixel. Best in-frame text rendering, up to 4K, conversational — it adjusts lighting and reflections to the change on its own. | — |
| 2 | **Seedream 4.5** | **Texture pass only.** Reviving sloppy AI textures in a finished frame: skin pores, fabric weave, ground dirt, surface grime. | **Never hand it a point edit.** That is not what it does. |
| 3 | **GPT Image 2** | **Last resort** for the finest local surgery on one small element NBP wouldn't take. Dirty globally (it touches the whole frame), excellent locally. Also the default for **location view changes**. | Anything NBP can handle. The bigger the CHANGE, the worse the result. |

**Seedream 4.5 texture pass** — same template, goal = *reviving sloppy AI textures*: CHANGE names the surfaces (skin pores, fabric weave, ground dirt); PRESERVE locks composition, identity, light, grade.

**GPT Image 2** — same template, narrowest possible CHANGE, and make the PRESERVE list maximally exhaustive because the model happily repaints what it shouldn't.

---

## 3. Location view change (reverse angle / new camera position)

The single most-scrambled edit. Two routes:

- **GPT Image 2 handles view changes well** — this is its third role and the default route for a reverse angle or a new angle on the same location.
- **On Nano Banana you must FORCE the new object arrangement.** Spell out the mirrored blocking explicitly, object by object — otherwise the geometry scrambles:

> *"In the main view the sofa is on the right; in this reverse view the sofa is on the LEFT. The window that was behind the camera is now visible ahead, centre-frame. The doorway that was on the left edge is now on the RIGHT edge. The rug stays under the coffee table, now seen from its far side."*

Anchor **every major object's new position**. A vague "show the reverse angle" produces a different room.

---

## 4. Prop sheets and product-style objects

Props and product-style objects render more realistically in Nano Banana / GPT Image 2 than in cinematic character models — strong realistic product context plus exact text rendering on the object itself.

Platform parameters: 1:1 (3:4 for tall props), 2k–4k.

```
Photorealistic [top-down / three-quarter overhead] product shot of [prop] on a
[neutral grey concrete] surface, [soft directional lighting], isolated subject.
[Concrete description of the prop: materials, construction, wear state].
[Blank unbranded surfaces stated positively if no text or logos are wanted].
[Tech block].
```

- **Multiple states are separate assets.** Clean / damaged / bloodied = three generations, not one prompt.
- **Trigger-word caution.** Device and weapon props hit safety flags. Describe by neutral materials and function — *"retro industrial electronic prop assembly with a numerical readout"* — not by weapon or explosive terms.
- **"No logos" is a positive instruction.** Remove brand names from the prompt entirely and write *"plain unbranded wrapper, blank matte surface"*. Never name the brand you're trying to avoid.

---

## 5. When the brief belongs on a Higgsfield model instead

Nano Banana is the image generalist and the edit workhorse. These briefs route out:

| Brief | Route to | Why |
|---|---|---|
| Character casting sheets, portraits, UGC / fashion / editorial where **the same face must survive dozens of generations** | **Higgsfield Soul 2.0** | Soul ID is a platform-level identity lock — it holds the face generation to generation in a way prose anchors can't. Prompt anchors only reinforce it. |
| A character **reference sheet**, fast | **Cinema Studio AI Cast** | Standalone Higgsfield tool that builds a consistent cinematic character sheet **automatically** — all parameters in its UI, no prompt needed. Offer it as the fast path; hand-build the 3-panel sheet only when full control is required. |
| Locations, environments, establishing shots, film stills, concept art, **21:9 cinemascope plates** | **Higgsfield Soul Cinema** | Cinema-grade texture, natural grain, era aesthetics, and 21:9. A Soul ID character can be dropped into the scene. |
| Sloppy AI textures in an otherwise-finished frame | **Seedream 4.5** | See the ladder above. |
| One tiny local fix Nano Banana refused; a location view change | **GPT Image 2** | See the ladder above. |

**Hard constraints worth knowing on that side of the fence:**

- **Soul 2.0 has NO 21:9.** A widescreen frame with a locked character goes to Soul Cinema with the Soul ID, not Soul 2.0.
- **Soul Cinema carries film grain and texture natively** — don't over-stack grain words there; one register line is enough. (Nano Banana is the opposite: it needs the grain/stock language spelled out.)
- **Aspect ratio and resolution are UI parameters on every Higgsfield model** — never `--ar`, never "16:9" inside the prose. (Nano Banana differs: it *does* take the ratio as a closing sentence, and via API parameter.)
- **No Higgsfield model has a negative-prompt parameter.** Everything unwanted is removed by positively describing what you want instead.

---

## 6. Anti-fail rules carried over from the Lira lane

Most of these reinforce the core skill; the ones marked ★ are additions.

1. **Natural prose, not keyword stacking.** *"4k, masterpiece, trending"* does nothing. No ALL-CAPS headers in generation prompts — CAPS blocks are for edits only.
2. **Don't bloat.** ★ A tight 80–150-word prompt beats a scattered 400-word one — past a point every extra clause dilutes attention and details drop out. Target **≤1500–2000 characters**. Cut filler, keep anchors.
3. **Positive over negative in generation.** *"Clean dry skin"*, not *"no acne"*. *"Empty deserted street"*, not *"no people"*. NOT-stacks (*"not cartoon, not anime"*) inject the very concepts they ban. ★ The carve-outs: **anti-retouching negatives DO land** on Nano Banana (see `realism_and_ugc.md`), and **removal is legal in edit prompts** when paired with a fill.
4. **Technical lighting and named materials, not vague mood.** *"Single overhead key light, soft 2:1 ratio, smooth falloff"* beats *"dramatic cinematic lighting"*. Name material + finish: *"board-formed concrete"*, *"oxidized copper verdigris"*.
5. ★ **Optics and DOF language belongs on characters, not locations.** Focal length, angle, and shot size are fine everywhere; shallow-DOF talk on an establishing shot muddies it.
6. **Palette by percentage.** *"Palette of 60% warm ochre, 30% deep charcoal, 10% rust-red"* — name real hues in words, keep the 60/30/10 logic. ★ **Derive the split from the user's instructions, the scene context, or their uploaded references — never invent a palette over them.**
7. ★ **Illustration drift on photoreal work.** The phrases *"character reference sheet"* and *"painterly"* trigger concept-art looks. Say *"studio photographs"*, *"film character sheet"*, *"cinematic film still"* instead. Fix drift by **strengthening photoreal anchors** (film stock, lens, real materials) — never by NOT-stacks.
8. **Text, tattoos, real people.** Exact copy in quotes + font/weight/colour. ★ Tattoos need concrete real designs (*"classic swallow"*, *"old-school dagger"*) plus *"clean line-work"* — a vague *"tattoos"* smears. Never name a real person; translate the reference into features (face, build, energy, era). No IP or brand names anywhere.
9. ★ **Rule of thirds on everything except character sheets.** Sheets are exempt — they're flat panel layouts.
10. **Video handoff:** describe characters in action **states, not transitions** — mid-throw, mid-punch, mid-jump; not *"reaches into the bag, pulls out, winds up"*. (Full pipeline in `storyboard_to_seedance.md`.)

---

## 7. Character sheet built by prompt (when you're not using AI Cast)

Fast path first: **Cinema Studio AI Cast builds the sheet automatically.** Offer it. The template below is for when the sheet is built by prompt — in Soul 2.0 with a Soul ID, or in Nano Banana with reference images.

Platform parameters: 16:9, 2k, Soul ID if the character has one.

```
Three studio photographs of the same [person] arranged side by side on a flat
neutral mid-grey studio backdrop, a film character sheet: full-body front photo
on the left, full-body back photo in the middle, close-up portrait photo on the
right, the same real person in all three, consistent across panels. Soft
directional cinematic studio lighting from one side, gentle natural shadow
falloff, clean neutral cinematic look.

The [person]: [age, build, ethnicity-as-type, face features, hair, facial hair,
distinctive marks — describe real-people references as features, never by name].

[Wardrobe, consistent in all panels: ...]. [Distinctive props / signature items.]

On the left panel the [person] stands straight facing the camera in a neutral
pose, arms relaxed at the sides, full figure head to feet. In the middle panel
the same standing pose is seen from behind. On the right panel a close-up
head-and-shoulders portrait, [expression + key face details].

[Palette line]. [Tech block].
```

- NO *"character reference sheet"*, NO *"painterly"* — say *"film character sheet"* / *"studio photographs"*.
- NO *"rule of thirds"* — sheets are exempt.
- Consistency anchors are load-bearing: *"the same real person in all three, consistent across panels"*, and repeat *"consistent in all panels"* on the wardrobe line.
- Panels are described in **flowing prose** — no LEFT/MIDDLE/RIGHT CAPS blocks.
- Directional (not flat) light. Concrete tattoo/mark designs with clean line-work.
- Cross-shot consistency is carried by **Soul ID on Higgsfield / matched references in Nano Banana** — never by prose alone. Cast per `global_ethnicity_casting.md`; deeper identity mechanics in `identity_lock_and_filmmaking.md`.

---

## 8. Location / environment plate

Platform parameters: 21:9 for cinemascope plates (Soul Cinema only — Soul 2.0 has none), 16:9 if the frame feeds standard video.

```
[Camera anchor — the hardest part; anchor it hard]. [Location identity].
[Key architectural / natural elements]. [Light source + direction + temperature].
[Secondary elements receding into depth]. [Palette line]. [Tech block].
[Mood / cinematographer ref]. [Emptiness stated positively if the location must
be empty: "empty deserted interior, bare walls, still air"].
```

**Camera-anchor tips — the recurring pain point on locations:**

- **Simple beats abstract.** *"High angle three-quarter wide shot, camera high above the room looking diagonally down at a 45 degree angle"* works. CCTV / fisheye / extreme-corner jargon fails or over-distorts.
- Prefer **real-world equipment and genre terms** (*24mm wide, real estate interior photo*) over abstract geometry.
- For stubborn geometry (floor plank direction, etc.), **anchor it in the positive and reframe** — *"horizontal stripe pattern, no vanishing point in the floor"* — instead of fighting the word "planks".
- **Frame-within-frame** (interior→exterior through a doorway or window): foreground ruin walls as dark silhouettes around the opening, Tarkovsky *Stalker* mood.
- Keep optics/DOF language off locations.

Deeper geometry craft: `perspective_and_lens_geometry.md`. Camera-height and drone-default fixes live there too.

---

## 9. Building blocks

**Film-grain cinematic register:**
```
Photorealistic ARRI Alexa LF anamorphic Cooke S4 lens at T2.0, organic 35mm
Kodak Vision3 250D film grain, soft cinematic falloff, cinematic film still
aesthetic
```
Pair with desaturated grading + a cinematographer mood. Never *"painterly"* on photoreal character work.

**Modern clean digital register:**
```
Shot on ARRI Alexa Mini LF with ARRI Signature Prime lens, clean modern digital
cinematic capture, crisp natural detail, minimal fine grain, soft cinematic
falloff, modern cinematic film still quality, hyperrealistic photographic detail
```
With: *natural living skin tones, medium contrast, subtle cool tone in the shadows, true-to-life modern colour, no heavy desaturation.* Distinct from the film-grain register — no heavy grain, no strong desaturation.

**Palette wrapper:**
```
Refined desaturated palette: [cool/dominant tones] dominating, [warm element]
as the only warm contrast, deep crushed blacks, restrained naturalistic
grading, soft low contrast, strong cinematic chiaroscuro
```
Add *"painterly"* only on intentionally painterly environment plates — never on photoreal characters.

**Cinematographer / mood shorthand** (pair with 3–4 concrete signatures, never the name alone — see `director_styles_and_film_frames.md`): Roger Deakins (naturalistic light), Emmanuel Lubezki (natural light, wide), Hoyte van Hoytema, Christopher Blauvelt, Paweł Pawlikowski (modern melancholy in historic architecture — canonical for austere institutional interiors), Andrei Tarkovsky (frame-within-frame interior→exterior), Akira Kurosawa (quiet landscape stillness), Naomi Kawase (atmospheric rural).

Keep building blocks **consistent across a project** so generated assets match each other.

---

## 10. Pre-send checklist (edit & routing lane)

- [ ] Right rung of the ladder: edit → Nano Banana first; texture slop → Seedream 4.5; finest local fix or view change → GPT Image 2; rebuild → regenerate, don't edit
- [ ] Right surface: character consistency across many shots → Soul 2.0 / AI Cast; 21:9 cinema plate → Soul Cinema; prop/product → Nano Banana or GPT Image 2
- [ ] CAPS blocks (CHANGE / PRESERVE EXACTLY) present in edits, absent from generations
- [ ] One change per pass; every removal paired with a fill
- [ ] PRESERVE list covers face, wardrobe, props, positions, camera angle, shadows, grade
- [ ] View change: every major object's new position spelled out
- [ ] Technical lighting (key, ratio, falloff) and concrete materials (material + finish)
- [ ] 60/30/10 palette derived from the brief or references, not invented over them
- [ ] Rule of thirds present — except on character sheets
- [ ] No brands, IP, or real people's names
- [ ] Not bloated: ≤1500–2000 characters, filler cut


<!-- ═══════ FILE: nano-banana-prompter/references/storyboard_to_seedance.md ═══════ -->

# Storyboard → Seedance video (the shared image→video pipeline)

**This is the Nano Banana half of a two-skill workflow.** When the user wants a *video sequence built from storyboard frames*, this skill designs the frames and `seedance-director` animates them. Both skills own the same pipeline from opposite ends — read this file whenever a brief involves "storyboard then video," "make the frames then animate," "shot-by-shot AI film," or any request that will end in Seedance/Kling motion. The Seedance half lives at `seedance-director/references/storyboard_from_stills.md`; keep the two in sync.

Nano Banana is the **art department** here: it draws every frame the video model will later move. The single most important fact in this whole pipeline: **the still is the seed of the shot.** Every identity, wardrobe, lighting, lens, and grade decision the video inherits is decided *here*, in the image, not in the video prompt. Get the frames right and Seedance mostly just adds motion; get them wrong and no video prompt rescues them.

---

## The pipeline at a glance

```
1. Brief + beat plan     → decide shot count, one action per shot (director call)
2. Character/asset sheet → Nano Banana: lock identity BEFORE any scene frame   [this skill]
3. Storyboard frames     → Nano Banana: one still per beat, consistent look    [this skill]
4. (optional) end frames → Nano Banana: a target "last frame" per beat         [this skill]
5. Animate each beat     → Seedance i2v: still = first frame (+ optional last)  [seedance-director]
6. Chain / stitch        → Seedance: last frame of beat N seeds beat N+1        [seedance-director]
7. Assemble + audio      → cut the clips together; Seedance carries native SFX  [seedance-director]
```

Steps 2–4 are this skill. Hand off to `seedance-director` at step 5 and pass along the look block you locked (stock, grain, lens, ratio) so the video prompt matches the frames.

---

## Step 1 — Beat plan (before drawing anything)

A storyboard is one still per **beat** — one clear action, one shot size. Plan the beat count from target runtime, because each still becomes a 4–15s Seedance clip:

- **15–20s hook / ad:** 3–5 beats
- **30–45s short:** 8–14 beats (the field-standard density)
- **60–90s film:** chain in the video stage; still plan in 8–14-beat acts

Rules for the beat list, before a single frame is drawn:

- **One clear action per frame.** Two actions = two beats = two frames. (Mirrors the Seedance "one primary action per beat" law.)
- **Vary shot size beat to beat** — wide → medium → close — so the cut has rhythm. A row of identical mediums animates into a boring sequence.
- **Match the aspect ratio to the target video** *now*. Draw 9:16 frames for a Reels sequence, 16:9 for landscape. Seedance inherits the frame's composition; a cropped or letterboxed still wastes resolution and breaks framing. Set it as the closing instruction on every frame (`Output in 9:16 vertical aspect ratio`).
- **Decide continuity type per cut:** is beat N+1 a *new shot* (fresh frame, new angle) or a *continuation* of the same action (its first frame should equal beat N's last frame)? This tells you whether to draw a matching end frame in step 4.

---

## Step 2 — Lock identity FIRST (the character/asset sheet)

The #1 failure of AI storyboards is the character drifting from frame to frame. The fix is upstream: build a reference sheet **before** any scene frame, then feed it into every subsequent frame. This is the same identity-lock discipline in `references/identity_lock_and_filmmaking.md` — applied at storyboard scale.

Build, in order:

1. **Character sheet** — one generation showing the subject in **2–3 angles** (front + 3/4 + profile), *identical* hair, wardrobe, and colour palette across the angles. One sheet per recurring character.
2. **Location keyframe** — one wide shot that defines the environment, time of day, and lighting direction the whole sequence lives in.
3. **Hero-prop close-up** — if a product/object recurs, one clean close with its surface texture visible.

Then for **every** storyboard frame: attach the character sheet (and location/prop refs as needed) and write *"the woman from the attached character-sheet reference, [new action], keep facial features, hair, and wardrobe exactly the same."*

Consistency mechanics that actually move the needle (validated across current Nano Banana Pro guidance):

- **Let the reference image carry identity; keep the text description short.** Over-describing the face in every frame *reduces* consistency — the model tries to satisfy both the picture and the paragraph and drifts. Describe the *action and emotion*, not the cheekbones.
- **Cap high-fidelity references at ~6.** Nano Banana accepts 14, but structural accuracy is tightest with ≤6 strong refs. Give each a role ("first ref = the character, second = the room, third = the jacket").
- **Use one session/thread for the whole board.** Nano Banana Pro holds session memory — define the character fully in the first prompt, then later frames only need the new action. Breaking the thread loses the latent lock.
- **Re-anchor every 3–4 frames** on long boards: regenerate from the original sheet, not from the last drifted frame, so error doesn't compound.
- **Nano Banana Pro (`gemini-3-pro-image`) is the storyboard default** — its character consistency, typography, and conversational editing are the reason. Iterate cheaply on Nano Banana 2 (`gemini-3.1-flash-image`), finalize hero frames on Pro.

---

## Step 3 — Draw frames that ANIMATE well (seed-quality, not just pretty)

A storyboard frame has a second job a normal still doesn't: it has to be a good *starting point for motion*. Design for that:

- **Leave somewhere to go.** A frame frozen at the peak of an action (fist already landed, door already open) gives Seedance nowhere to move. Draw the frame *just before* or *at the start of* the beat's action — mid-stride, hand reaching, about to turn — so there's motion left to generate.
- **Compose off-center / with lead room** in the direction of movement, so the subject has room to travel inside the frame without hitting the edge.
- **Keep the pose physically plausible and weight-bearing.** Seedance's physics prior extrapolates from the frame; an impossible or floaty pose animates into a warp. (Weight never 50/50; hands doing a real job — same posing rules as `references/composition_posing_and_critique.md`.)
- **Avoid the known Seedance weak spots in the still itself:** no subject-in-a-mirror as a hero element (Seedance breaks mirror-reflection geometry when it moves), no extreme single-hand close-up, no critical readable text you need to survive motion (render text in a separate title frame, not baked into an action beat).
- **Match capture medium to the whole board.** Lock ONE look block — stock + grain + lens + grade + ratio — and apply it verbatim to every frame so the sequence cuts together. This is the block you hand to Seedance. Example lock: *"shot on Kodak Portra 400, soft grain, 50mm, warm muted grade, 16:9."*
- **Realism stack still applies** (skin texture, single motivated light, micro-imperfection) — a plastic still animates into a plastic clip.

---

## Step 4 — Optional: draw the "last frame" too (two-endpoint control)

Seedance 2.0 can take a **first frame AND a last frame** and generate the motion in between (true interpolation, not a cross-fade). This is the tightest control the pipeline offers. Draw a matching end frame when the beat has a definite target state:

- Same character sheet, same look block, **same wardrobe and lighting** — change only what the action changes (position, expression, the door now open, the product now revealed).
- Use conversational editing to make the pair: generate the start frame, then *"same shot, same everything, but now she has turned to face the window — keep face, hair, wardrobe, lighting, and framing exactly the same."* That "keep everything else exactly the same" phrasing is what keeps the two endpoints a matched pair instead of two different shots.
- **For a continuous multi-beat action, the last frame of beat N = the first frame of beat N+1.** Draw it once, use it twice. This is what makes chained clips stitch invisibly in the video stage.

If a beat is a hard cut to a new angle, you don't need an end frame — just draw the next beat's first frame.

---

## Hand-off to Seedance (what to pass, and when to stop)

When the frames are approved, this skill's job is done — switch to `seedance-director`. Hand over, per beat:

- the **first frame** (and last frame if drawn),
- the **look block** you locked (so the video prompt's closing style line matches),
- the **one action** the beat animates and any **camera move**,
- the **aspect + intended clip length**,
- whether the beat is a **new shot or a continuation** of the previous one (drives first/last-frame chaining).

Do **not** try to write the motion in Nano Banana — it makes stills only. And do not bake motion blur or "sense of movement" into a frame you intend to animate; give Seedance a clean, sharp starting state.

### Platform note (imagine.art surface)
On the imagine.art app, Nano Banana renders the stills and Seedance 2.0 animates them (up to 15s, up to 1080p, no reliably-exposed seed — so lock look in the *still* and batch 2–3 video takes). The imagine.art Seedance filter rejects identifiable **real faces**; an AI-generated fictional character sheet from Nano Banana passes cleanly and is the intended way to get a "specific person" through the pipeline. Confirm the video-side specifics in `seedance-director/references/surfaces-and-use-cases.md`.

---

## Quick checklist before handing frames to Seedance

1. Beat list written — one action per beat, shot sizes varied, count matched to runtime.
2. Aspect ratio matches the target video and is set on every frame.
3. Character sheet built and attached to every frame; identity locked, description kept short.
4. One look block (stock/grain/lens/grade/ratio) applied verbatim across all frames.
5. Each frame drawn *before/at the start* of its action, with lead room — not frozen at the peak.
6. No mirror-hero, no extreme hand CU, no motion-critical baked text.
7. Last frames drawn for continuous beats (last of N = first of N+1); skipped for hard cuts.
8. Look block, per-beat action, camera move, aspect, and clip length written down to pass to `seedance-director`.
