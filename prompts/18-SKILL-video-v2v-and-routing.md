# V2V Edits & Model Routing — footage edits, model choice

> **What this is.** seedance-director V2V edits plus gen-media-router. Read when editing existing footage (VFX, environment swaps, add/remove/replace with identity preserved), or when the brief hasn't named a model and you must choose between video and image.

> **Bundle of 8 source files, 60,895 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `seedance-director/references/v2v-edits/edit-operations.md` | 9,148 |
| 2 | `seedance-director/references/v2v-edits/vfx-library.md` | 8,326 |
| 3 | `seedance-director/references/v2v-edits/continuity-and-detail.md` | 10,167 |
| 4 | `seedance-director/references/v2v-edits/world-library.md` | 10,940 |
| 5 | `gen-media-router/SKILL.md` | 10,929 |
| 6 | `gen-media-router/references/comparison_matrix.md` | 3,138 |
| 7 | `gen-media-router/references/chain_recipes.md` | 6,303 |
| 8 | `gen-media-router/references/quick_reference.md` | 1,944 |

---

<!-- ═══════ FILE: seedance-director/references/v2v-edits/edit-operations.md ═══════ -->

# Edit Operations — the V2V operation templates

Every operation below uses the five-part structure from SKILL.md (source lock → the edit → integration → audio → keep-clause). These are the operation-specific patterns. V2V is native to Seedance 2.0 (1.5 required full regen). Keep reference videos trimmed to the key segment.

## Operation table

| Operation | Core template |
|---|---|
| **Add element** | `At [second] + [spatial position] of @video1, add [element]. Keep everything else unchanged.` |
| **Remove element** | `Remove [element] from @video1, keep everything else unchanged.` |
| **Replace element** | `Replace [original] in @video1 with [new]. Hold position, lighting, and motion identical.` |
| **Subvert** (weather / season / time-of-day) | `Edit @video1: keep the framing, performance and pacing but change [the season to winter / the time to night] — [2–3 concrete consequences].` |
| **Extend fwd/back** | `Extend @video1 [forward/backward] by [1–2]s + [content matching the source's capture register and palette].` |
| **Repair** (fix a glitched 1–2s) | Bug-report style — see below. |
| **Bridge / track completion** | `@video1 + [transition] + connect to @video2 (+ @video3)` — ≤3 clips, ≤15s total input. |
| **Restyle / style transfer** | `Transform @video1 to [style], preserve core motion and timing, adjust palette to [palette], keep identity consistent, avoid identity drift.` |

## Add element

Spatial + temporal precision beats description volume. Name the second, the quadrant/depth, the direction of travel, and match the source's optical character:

```
At 3 seconds, in the upper-right quadrant of @video1, add a single seabird crossing
the frame from screen-right to screen-left in mid-distance. Match the existing
motion-blur character, rain density, color grade, and 35mm grain. Keep every other
element of @video1 unchanged across the full runtime — character positions, wardrobe,
lighting, atmosphere all identical.
```

For a *specific* thing (a creature, a product, a vehicle), don't describe it — show it. Generate a still in an image model, upload it as an element, and scope its role: `@LIZARD: appearance, scale-texture and color reference only; ignore the photo's background and lighting, do not use it for the environment.`

Elements added *behind* the subject on an ongoing basis (a horde, climbing creatures, a storm building) should accumulate: `more of them crawling into frame for the rest of the shot` — a one-time appearance reads as a glitch.

## Remove element

Name what fills the hole. Removal without a fill instruction invites reinterpretation:

```
Remove the person in the background of @video1. The sidewalk and storefront behind
them continue naturally. Keep the foreground subject, their motion, the camera move,
lighting and grain unchanged.
```

## Replace element

Three stability rules, in priority order:

1. **Background before subject.** If both need replacing, do the background pass first — subject-first passes cause the model to reinterpret the background uninvited.
2. **Declare the protected region in writing:** `Keep the subject exactly the same — silhouette, scale, position, color, reflections.`
3. **Match the physical seat of the new object:** scale, contact shadows, reflections, and the existing grade and grain.

```
Replace ONLY the background of @video1 with [dusk city skyline]. Keep the subject
exactly the same (shape, size, position, color, reflections). Match existing lighting
direction and intensity. Preserve camera angle and lens perspective. Keep edges clean — no halos.
```

```
Replace ONLY the [red car] in @video1 with [a black motorcycle]. Keep the background
unchanged. Match scale, contact shadows, and reflections. Maintain the same color grade and grain.
```

Tiny text and logos don't survive replacement passes reliably — replace the environment in Seedance, comp labels/logos in an editor.

### Edge-heal pass (second pass, when edges halo or shimmer)

```
Refine boundary edges between subject and background in @video1. Remove halos and
shimmer. Preserve fine details, identity, motion and grade. Change nothing else.
```

## Subvert — weather, season, time-of-day

A subversion is a *world-state* edit: same performance, same camera, different physics. Always write 2–3 concrete consequences of the new state, or the model paints a filter instead of changing the world:

```
Edit @video1: keep the framing, the performance and the pacing but change the season
to winter — snow banked on the ground, breath fogging on every exhale, flat grey
skylight replacing the warm sun. Relight the subject for overcast: soft toplight,
no hard shadows. Keep everything else unchanged.
```

Time-of-day changes are relighting jobs first — see rule 4 in SKILL.md and the environment-swap grammar in `world-library.md`.

## Extend forward / backward

Extends drift; treat them as *continuation of camera + lighting + texture*, never "generate more."

1. Anchor on the last good frame (grab a still of it as reference where the surface allows).
2. Describe the camera like an operator: `slow dolly forward, slight parallax, shallow depth of field` — not "keep going."
3. Lock the look by naming materials + lighting + capture: lens, grain, color grade.
4. **1–2 seconds per pass.** Chain passes for more.
5. Ban new ideas explicitly: `Do not introduce new elements — only continue existing motion.`

```
Continue @video1 seamlessly from the last frame. Keep the same visual style, lens,
grain, and color grade. Camera motion: [slow dolly forward]. Lighting: [warm studio
key + subtle fill], shadows consistent. Subject: [one sentence], preserve exact shape
and textures. Background unchanged, no new objects. Motion: only natural
micro-movement. Negatives: no style change, no extra objects, no flicker.
```

The model handles the overlap region itself — the source isn't repeated verbatim. Backward extends work the same way: `Extend @video1 backward. Start with [shot description] before the current scene begins.`

## Repair — fix the cursed second

The clip is perfect except one moment: a warped hand, a bent logo, a flicker. Don't regenerate — repair.

1. **Feed the tight segment** — the broken 1–2s plus ~0.5s handles each side, not the whole clip.
2. **Describe the error like a bug report:** `Between 2.0s and 3.5s the right hand deforms as it lifts the phone.`
3. **Describe correct:** `five fingers, natural anatomy, the phone edges stay straight, logo stays flat and readable.`
4. **Demand continuity:** `Match the style, color grade, grain, motion cadence, and motion blur of the surrounding frames so the repair fits back in.`

```
Repair only the selected segment of @video1. Keep the same style, color grade, grain,
and motion cadence as the surrounding frames. Fix: [precise issue + timeframe].
Constraints: [straight lines stay straight / correct hand anatomy / logo stays planar].
Preserve: subject identity, wardrobe, materials, lighting direction. No new objects.
```

If the repair "pops" at the boundary: shrink the window, or run two lighter repair passes instead of one heavy one, and add `match motion blur and shutter look to adjacent frames`.

## Bridge / track completion

Stitch up to 3 clips (≤15s total input) with generated transition material:

```
Video 1: a leaf falls to the ground. A burst of golden particles rises on impact,
a gust of wind sweeps across the frame, then transition into video 2.
```

The bridge content must obey both plates: name what carries across (palette, subject, motion direction). For pure hard-cut assembly, cut in an editor instead — bridging is for when you need connective tissue that doesn't exist.

## Restyle / style transfer

The one operation where the *look* changes globally — motion and identity still don't:

```
Transform @video1 to [hand-painted watercolor animation]. Preserve core motion and
timing exactly. Adjust palette to [muted earth tones]. Keep the subject's identity
consistent throughout — avoid identity drift. Keep the source edit and cuts.
```

## Sequencing multi-edit briefs

The user wants three changes? Three passes, stability order:

1. Environment / background swap (biggest, most stable first)
2. Weather / atmosphere / relight
3. Added elements (creatures, objects, effects)
4. Removals and repairs (last — on near-final footage)

Each pass takes the previous pass's output as its new `@video1`. Re-run QC between passes.

## Seed & QC discipline

- Reuse one project seed where the surface exposes it (imagine.art may not — use 2–3-take batches and pick).
- Iterate at low res; run the final at the surface max (faces and lip-sync hold at high res, warp at low).
- **QC scrub before delivering:** frame-by-frame around every edit boundary (flicker, texture pop), edges at 200% (halos), straight lines (bending), materials (glass stays glass, metal doesn't go plastic), shadow direction continuity, first/last frame match if it loops.
- Standard negative set — pick ≤3 by real risk: `no style change, no extra objects, no warping, no text artifacts, no flicker`.


<!-- ═══════ FILE: seedance-director/references/v2v-edits/vfx-library.md ═══════ -->

# VFX Library — physics-first effects on existing footage

Every effect obeys the **effects contract**: it has a **source** (where it starts), a **material** (what it's made of), a **motion path** (how it travels), an **interaction with light** (what it illuminates or occludes), an **interaction with objects** (what it touches, wets, chars, ripples), a **dissipation**, and an **endpoint** (settle, fade, evaporate, collapse, glow out, leave residue). If any of these is unwritten, the model improvises it — usually as a noisy perpetual overlay.

Write complex effects as `forms → travels → dissipates` with real seconds. One hero effect per clip. Never bare "magical", "explosive", "epic", "cinematic" — translate wonder into particles, fluids, smoke, light, debris, deformation, or energy behavior.

## The integration stack (attach to every effect)

The difference between VFX and *footage* is that footage is lit by its world. Every added effect must:

- **Cast its light.** Fire, neon, lava, lightning, energy = light sources. Write what they illuminate: `strong warm firelight rakes down his face, neck and collar and spills onto the hood behind him, pulsing on the glossy paint.` An effect that doesn't relight its surroundings reads as a sticker.
- **Sit in the air.** Matching atmospheric haze and aerial perspective — distant effects go softer, lower-contrast, cooler.
- **Touch the ground.** Real soft-edged contact shadows; puddle ripples; scorch or residue where physics demands it.
- **Match the capture.** `Match the source's exposure, color temperature, lens character, depth of field, motion blur and film grain` — one line, every effect prompt.
- **End the phrase with the anti-tell:** `…so it sits in the plate and never reads as pasted-in CG.`

## Effects near the subject — the boundary rules

The performance is untouchable, so effects live *around* it:

- Place the effect adjacent to faces/hands/wardrobe and let only its **light** touch the subject.
- If the subject is the effect's anchor (hair on fire, glowing hands), protect the anatomy: `the hair burns but holds its shape and silhouette, never charring away`; `face and identity unchanged`.
- Wardrobe that must survive gets a hard-boundary block: `the shirt does not move, lift, ripple, tear, bulge, wrinkle, glow, change color or change shape in any frame. No effect detail appears on, under, through, beside or behind the fabric at any point.`
- The subject's *reaction* comes from the source performance only — `completely unfazed, performance and timing identical` or `his existing recoil at 2.5s now reads as reaction to the blast`. Repurpose what's there; never direct new acting.

## Effect recipes

### Fire

Source and spread first, then light, then consequence:
```
Flames catch at [source] and race [direction] until [end state]. A corona of flame
flickers and trails in the breeze. Embers stream off in a constant shower, glowing
orange and dying in the air. Heat-haze shimmer warps the [background] behind it.
The fire reads as a light source — warm firelight rakes [subject/surfaces], pulsing.
```
Audio: `a low whoomph as it catches, then a steady flame roar and crackle, constant ember snaps.`

### Smoke / fog / vapor

Density + direction + temperature behavior: `cold white vapor rolls over the rim, sinks down the glass, and thins near the tabletop.` Hot smoke rises and disperses; cold vapor sinks and pools. Give it an endpoint (`thins to nothing by 6s`) or it becomes a permanent filter.

### Rain (added to existing footage)

Rain reads on camera only when lit — real crews backlight it. Write the light with the water:
```
Steady rain sheets through the frame, backlit by [the streetlight / the low sun /
each lightning flash] so the drops read as bright streaks. Rain beads and streams
on [wardrobe/surfaces]; puddles form and ripple outward from each footfall; wet
asphalt holds muted flat reflections of the lights above.
```
Tie the weather to surfaces — untouched dry ground under heavy rain is an instant fail. Flat puddle/pavement reflections are a Seedance strength; keep them `muted reflection, not mirror`. Audio: `rain drumming on [specific surfaces — leaves, hood, mud], dripping water, rain hiss on asphalt.` Full storm-and-fight staging: `world-library.md`.

### Lightning / storm

Lightning is an exposure event, not a decoration: `a stark forked bolt cracks down off to one side, for an instant lighting the rain streaks and a wedge of churning foam before the dark closes back in.` Sync sound to sight: `deep rolling thunder with sharp cracks on each flash.` Keep the base exposure low-key so the flash has somewhere to go.

### Particles / energy

Anchor to a source object and keep it attached: `thin blue electrical arcs crawl along the cable, briefly illuminating fingerprints on the plug` / `gold dust particles spiral from behind the logo, catch the backlight, then settle on the table.` Free-floating unanchored particles = screensaver. Endpoint mandatory (settle / fade / discharge).

### Destruction / debris

Impact structure: slow build → fast hit → slow aftermath. Write force and consequence, not choreography: `the tentacle whips across the deck, splintering timber; planks cartwheel into the sea; the rail sags where it struck.` Mass sells it — `heavy`, `ground-shaking`, `with real weight`, debris that *arcs and lands* rather than floats.

### Transformation (object or body-part; never the face)

The strongest pattern is **discrete sequential stages with hard boundaries** — no continuous creep:

- Break the transformation into 3–6 numbered stages with rough second ranges.
- Each stage **fully completes before the next begins**: `at any moment there is a clear boundary — everything below the current stage is finished, everything above is untouched.`
- **Completed stages stay completed:** `by the end of the shot, the Stage-1 result must still look as it did at 2s, not re-rendered.`
- Name where the transformation **stops, hard** (`the very last plate locks flush exactly at the sleeve line. Nothing above it is touched, shown, hinted at or transformed.`)
- Per-stage audio beats (clicks, hisses, locks) sell the mechanics.

### Creatures (added to real footage)

The documentary-realism stack — creatures fail as "clean CGI" and succeed as *filmed animals*:

- **Hide like a wet elephant or rhino:** `deeply wrinkled, cracked, sagging, asymmetric, mud-caked and matte — never smooth, glossy or inflated.` Eyes `alive and wet with catchlights, blinking.`
- **Never show the whole creature crisp.** `Veiled by drifting mist and partly hidden behind [trees/structures], shot as if on a telephoto lens with shallow depth of field, grain, rain and mist between camera and animal.` Full-body hero shots of an added creature are where CG breaks.
- **Motion is slow, heavy, minimal:** `neck sway, blink, nostril flare, breathing, weighty footfalls, real mass — nothing fast, floaty, rubbery or looping.`
- **Scale via anchors:** the trees, the subject, the buildings — `necks rising above the treeline, legs like tree trunks, the man tiny beneath them.`
- **Integration:** same key and grade as the plate, contact shadows where feet/claws grip, aerial perspective so farther individuals go hazier, `never lit differently, never pasted, never crisper or a different color temp than the fog.`
- **NON-IP guard:** `NON-IP — generic [sauropod/kraken/monitor lizard], not based on any franchise creature.`
- For a *specific* creature design, generate a still first and feed it as a named element (`@CREATURE: appearance reference only`).
- Interaction beat: time the creature's one big move to a beat in the source performance — `exactly as he turns at 2.5s, one leans in toward camera, delivering the scare; his existing recoil reads as the reaction.`

### Zombie hordes

A creature-add special case with its own staging — full treatment in `world-library.md`.

## Audio design for effects

Diegetic SFX + source dialogue only, unless the user asks for music. New elements bring their own sound, synced to what's on screen: `SFX and source dialogue only: his original speech throughout; [effect sounds tied to effect beats]; [world ambience].` Keep ≤3 simultaneous layers; one hero sound per beat; source dialogue stays dominant.


<!-- ═══════ FILE: seedance-director/references/v2v-edits/continuity-and-detail.md ═══════ -->

# Continuity & Detail — multi-shot, multi-pass, character locks, and the realism stack for added elements

Edits rarely live alone. A clip has cuts inside it; a project has several clips; a brief needs several passes. Everything added must stay *the same thing* across all of them — and every detail on the subject must survive every pass. This file is that discipline.

## 1. The anchor block — one paragraph you never change

Drift happens because the model treats unwritten details as flexible. The counter is a **master anchor block**: a compact paragraph of non-negotiables, pasted **unchanged** into every pass, every shot, every re-roll. Each pass then adds one short line for what changes.

Build one anchor block per tracked thing:

- **Subject anchor** (the preserved performer) — 3–7 crisp, near-measurable identifiers: `late 20s, short curly dark hair, small mole on left cheek, gold hoop earring in right ear, navy blazer with thin silver zipper pull, left-handed`. Small distinctive marks (piercings, tattoos, scars, rings) erode *first* — name them or lose them.
- **Element anchor** (the thing you added — creature, horde, object). Once an added element survives one pass, it becomes a character: re-anchor it identically in every subsequent pass. `the same sauropods — small domed heads, wrinkled olive-grey hide with ochre lichen mottling, pale throat` — never "the dinosaurs from before."
- **World anchor** (the swapped environment) — 2–3 set anchors + light: `black basalt road, glowing orange fissures both sides, smoke-darkened sky, warm under-light from the lava`. Same flooring, same signature element, same color temperature, every pass.

Same noun phrase every time — "the courier" stays "the courier," never rotating with "the man / he / the rider." Alternating descriptors is self-inflicted drift.

## 2. The four drift patterns (and their negative anchors)

Watch for these between shots and between passes:

1. **Feature erosion** — accessories and marks quietly vanish (the nose ring goes first). Fix: name them in the anchor block + negative anchor: `no missing piercings, no missing rings`.
2. **Pose flip** — hands, dominant side, or gaze mirror between generations. Fix: state handedness/facing in the anchor + `no mirrored features`.
3. **Stylization shift** — photoreal slides toward cartoon, line weight or saturation creeps. Fix: repeat the capture line (grain, lens, grade) in every pass; it is part of the anchor, not decoration.
4. **Identity blend** — two references average into a hybrid face. Fix: reference hygiene below.

## 3. Reference hygiene (when the edit uses reference images)

Fewer, cleaner references beat more: **2 images max per identity**, same angle family, same lighting temperature, same wardrobe. Mixing warm indoor + cool outdoor refs makes eye color and skin speculars alternate across frames. Mixing a frontal with a profile makes the model invent the in-between. For added creatures/objects, one clean still (generated in an image model) with a scoped role line beats three inconsistent ones.

## 4. Multi-shot clips and multi-clip sequences

- **Edits on clips that contain cuts:** the source edit and cuts are part of the lock (`preserve the source edit and cuts; do not re-cut`). The added element must obey continuity across those cuts — re-state its position and screen direction for each shot: `the horde stays screen-left of him in both shots, closing from the same direction`. Hold the 180° line: an element approaching from frame-right keeps approaching from frame-right after the cut.
- **Sequences of separately edited clips:** paste the same anchor blocks into every clip's edit prompt; keep light temperature and time-of-day identical in words, not vibes (`soft overcast noon` in clip 1 must be `soft overcast noon` in clip 4).
- **Anchor-and-Extend:** the highest-continuity way to grow an edited scene — take the final frame of the approved edit as the anchor and *extend* rather than re-generate; the environment carries at effectively 100% because it's inherited, not re-described.
- **Directionality is continuity:** if the storm rolls in from screen-left in shot 2, it cannot be overhead in shot 3 without time passing on screen.

## 5. Edit-pass continuity (chained passes on one clip)

Each pass inherits everything the previous passes did — say so: `@video1 already contains [the desert swap from pass 1]; keep it exactly, including [anchors]. This pass adds only [X].` Run the drift scan between passes (below) and fix drift *before* stacking the next edit — drift compounds.

**Drift scan between passes (2–4 minutes):**
- Anchor audit — every anchor still present? (beanie, ring, handedness, the creature's markings)
- Feature scan — scrub for lost accessories, flipped poses, lighting jumps at cut points
- Cross-shot light loop — play the shots in a loop; watch for sudden specular or temperature shifts
- Micro-expression check — does the face still react like the same person? (If the *performance* changed at all, the pass failed — reject it regardless of how good the edit looks.)

**Recovery when drift already happened:** (a) **recut** — hide a single-shot mismatch with a trim or cutaway; (b) **composite** — a missing earring or small mark is faster fixed in post than re-rendered; (c) **regenerate** with the anchor block tightened and the seed locked. Rule of thumb: if the fix takes less time than the re-render, composite.

## 6. Surface state vs performance — the boundary that makes weather edits legal

The performance is untouchable, but a real world *marks* the subject. Distinguish:

- **Surface state (required, allowed):** rain wets their hair and beads on their jacket; dust coats their shoulders in the desert; snow gathers on the hood; sweat sheen in the jungle heat; firelight and neon relight the face; wind moves hair and loose fabric. A subject standing bone-dry in a downpour is a broken edit. Write it: `his hair and shoulders darken with rain, drops beading and streaming on the slicker; skin holds a wet sheen, fully matte, no beading gloss.`
- **Performance (forbidden):** gait, gesture timing, expression changes, blinks re-timed, head turns added, lip movement altered, blocking moved. If realism seems to demand a *reaction* ("he'd flinch"), the answer is to reuse an existing beat of the source performance (`his existing glance at 2s now reads as…`) or accept `completely unfazed` — never to synthesize new acting.

Wardrobe sits on the line: its **state** may change (wet, dusty, wind-blown); its **identity** may not (color, cut, layers, logos identical). Say both.

## 7. The detail & realism stack for added elements (anti-CG checklist)

Everything added must pass the same realism bar the source footage passes for free. The seven tells that expose CG, and the line that kills each:

| CG tell | Kill line |
|---|---|
| Too clean | `weathered, asymmetric, mud-caked/dust-worn, micro-scratches and wear at contact points` |
| Too crisp for its depth | `farther elements go hazier, softer, desaturated and lower-contrast — aerial perspective` |
| Wrong color temperature | `same color temperature as the source plate, never warmer or cooler than the fog/haze around it` |
| No motion blur | `matching the source's motion-blur character and shutter look` |
| Floating (no contact) | `real soft-edged contact shadow; ground deforms/splashes/ripples at every contact` |
| Uniform skin/surface | `visible pores, subsurface scattering, wrinkled sagging hide, fabric weave and natural creases` |
| Perfect symmetry/loops | `asymmetric, non-repeating motion; nothing floaty, rubbery or looping` |

Close photoreal edits with `no 3D, no cartoon, no VFX` — on an edit prompt this reads as "no *visible* VFX," the exact goal.

## 8. CGI-scale operations (blockbuster edits)

These are still five-part edit prompts — just bigger subjects. Face/dialogue close-ups remain the weakest AI register, so keep heavy CG action in wides and mediums; the preserved performance carries the close-ups.

- **Set extension:** the source frame continues past its edges or depth — `extend the street beyond the source's far corner into [a harbor at dusk]; the source's architecture style, brick color and lamp spacing continue seamlessly; join line invisible; source framing unchanged.` Anchor the join: name the last real element and the first generated one.
- **Sky replacement:** the classic invisible edit — `Replace ONLY the sky with [towering storm cells at dusk]. Horizon line unchanged. Relight the scene for the new sky: [cooler ambient, no hard sun]. Ground shadows soften to match. Everything below the horizon unchanged.` The relight clause is what separates a sky *replacement* from a sky *sticker*.
- **Day-for-night / time-of-day:** a full relight, not a filter — name the new sources: `night falls: sky deep blue-black, streetlamps and windows become the only sources, pools of warm light with true darkness between them, subject relit by the nearest lamp from screen-right, deep shadows, no daylight ambient.`
- **Crowds / armies / hordes:** stage in depth registers (readable near rank → half-lit mid → silhouettes far), give the mass one collective motion verb (`advancing`, `fleeing`, `swarming`) plus 2–3 individualizing details near camera, and let atmosphere swallow the far ranks — the fog is doing your rendering budget's job. `No two figures identical, no synchronized loops.`
- **War / destruction plates:** impact grammar at scale — slow build → hit → aftermath; every explosion throws debris that *arcs and lands*; smoke columns join the wind direction the source establishes; new light sources (fires, muzzle flashes) rake the preserved subject. Keep the subject's choreography sacred; the war happens around it.

## 9. When to stack this file

Read this file whenever an edit brief involves: more than one pass, more than one clip, a clip with internal cuts, an added element that recurs, weather that should mark the subject, or any CGI-scale operation. For single-pass single-element edits, SKILL.md + the operation template is enough.


<!-- ═══════ FILE: seedance-director/references/v2v-edits/world-library.md ═══════ -->

# World Library — environment swaps + researched scenario looks

## Part 1 — Environment swap grammar

Swapping the world around a preserved performance is the flagship V2V edit. The grammar:

### Full swap vs partial

- **Full swap:** `The environment is fully replaced: [new world].` Everything but the subject (and named props — the car, the rig) becomes new.
- **Partial / reskin:** each source element maps to a counterpart: `the overhead ladder rig becomes a row of rusted iron rungs bolted into a cracked stone ceiling, the grey concrete becomes weathered moss-covered carved stone.` Mapping element-by-element keeps the subject's physical interactions (grips, footfalls) valid — this is why reskins survive action footage.
- **The ground transforms too:** `the stone underfoot has become rippled wind-sculpted sand.` A subject standing on the old floor in a new world is a classic fail.

### The trigger (mid-clip swaps)

World flips need a visible on-screen cause and an exact second: `At about 2.2 seconds, on his finger snap, the backlit sun blooms into a white flare that washes across the frame; as the bloom falls off, the city is gone and he is in open desert.` The flash/bloom covers the transition. Before the trigger: `For the first beat keep the real [plaza] exactly as shot.`

### The relight decision (make it explicitly, every swap)

- **Hold the key** when the new world can share the source's light: `Keep the sun as the key from screen-left exactly as before so his face and the light on him barely change; add a faint warm sand bounce from below and a touch of the desert's hazy distance over him.` Cheapest, most stable.
- **Relight deliberately** when the world demands it (day→night, interior→lava field): `Relight the driver for night — magenta and cyan neon spill washing over his face from the sides, a cool rim edging his hair and shoulder, skin kept readable against the dark.` Name direction, color, and what stays readable.
- **Blend** when partially compatible: `Blend his original warm low-sun key with the lava under-light so his skin tone holds.`

### Motion & depth (moving cameras)

- **Parallax:** `dunes roll to the horizon, a thin veil of blown sand streaming past at ground level with the same rightward parallax as the camera move` / `neon storefronts streaking past in long light trails with strong parallax.`
- **Three-register depth:** foreground detail (texture, spray, debris) → midground subject → far register hazed: `aerial perspective so the distance goes softer, desaturated and lower-contrast.`
- **One look over everything:** `Light the whole frame under one look — the man, the [vehicle] and the terrain sharing the same [key] — match exposure, color temperature, lens character, bloom, film grain and depth of field across the whole frame so nothing reads pasted, crisper or a different color temp than the haze.`

### The world brings its sound

Every swap replaces the ambience: `then warm desert wind, fine hiss of blowing sand and a wide empty-space tone` — source dialogue preserved on top.

---

## Part 2 — Scenario look library (researched)

Prompt-ready visual DNA for four requested worlds. Pull the relevant block, adapt, attach the integration stack.

### Rainforest / jungle

**How it actually looks:** only ~10% of light reaches the forest floor — a rainforest is *dark* at ground level, lit by shafts. God rays pierce canopy gaps; early mornings are misty, mist clinging to the canopy. Palette: layered emerald greens; shift toward teal for a cooler, mistier mood, or warm it for golden-hour shafts. The air has *body*: humidity haze, drifting mist, suspended pollen and dust in the light shafts, constant dripping.

**Prompt block:**
```
Dense rainforest, dark at ground level — thin golden shafts of sunlight pierce gaps
in the canopy, catching drifting mist and suspended pollen. Layered emerald greens
graded toward teal in the shadows, moss-covered trunks, hanging vines, dripping
ferns, wet leaf litter underfoot. Humidity haze thickens with distance so the deep
forest fades soft and blue-green. Everything glistens — wet foliage, beaded moss.
```
Audio: `dense insect drone, layered birdsong, water dripping leaf to leaf, distant unseen calls, humid air tone.`
Adventure variant: crumbling carved stone, worn glyphs, toppled pillars under the vines; add `metallic creak of old iron, pebbles falling away into a chasm, echoing drips in stone`. Grade: teal-and-amber — warm golden pools where beams land against cool teal shadow.

### Sahara desert

**How it actually looks:** rippled wind-sculpted sand in the foreground; dunes rolling unbroken to a far horizon; **heat shimmer rising off the crests**; a thin veil of blown sand streaming at ground level (this sells wind + scale + parallax in one line). Light: low golden sun = long raking shadows that carve every ripple; harsh noon = washed-out, almost white, stark surreal contrast. Palette: rich golds and browns against muted blue sky (the Lawrence of Arabia axis). Distance: mirage wobble on the horizon — a telephoto, compressed-perspective feel makes far figures swim in the haze.

**Prompt block:**
```
Open desert — rippled wind-sculpted sand in the foreground, dunes rolling unbroken
to a far horizon under a low golden sun. Long raking shadows carve every sand ripple.
Heat shimmer rises off the dune crests; a thin veil of blown sand streams past at
ground level. Rich golds and warm browns against a muted pale-blue sky, distant
horizon wobbling in mirage haze.
```
Audio: `warm desert wind, fine hiss of blowing sand, a wide empty-space tone.`
Noon variant: `vertical white sun, colors bleached toward bone, short hard shadows, heavier mirage boil on the horizon.`

### Zombies approaching (added behind/around a preserved subject)

**How they move:** the classic register is the *shamble* — uneven gait, one foot dragging, arms reaching forward, head lolling, weight lurching side to side; no two alike. The modern register is the *sprint* — full-speed, feral, crashing through obstacles. Pick one register per clip and say it; mixed speeds read as an error unless staged as fresh-vs-old.

**How a horde is staged:** in depth layers. Nearest figures readable, mid-layer half-lit, far layer silhouettes emerging from fog/smoke — and the count *grows*: `more figures emerging into frame throughout.` Approach = distance closing over the runtime. Never let them reach the subject unless the source performance contains the reaction.

**How they look:** desaturated, cold, overcast grade; grey-green dead skin, dark dried blood, torn stained clothing, milky clouded eyes, slack jaws. Documentary realism rules apply (see creatures, `vfx-library.md`): matte decayed skin, never rubber-mask smooth; veiled by fog and distance; nothing floaty or looping.

**Prompt block:**
```
Behind him, a horde of the undead emerges from the fog and advances — staggered in
depth, the nearest a dozen paces back, dozens more resolving as silhouettes further
in. Uneven shambling gaits, no two alike — one drags a stiff leg, another lurches
shoulder-first, arms reaching forward, heads lolling. Grey-green decayed skin,
matte and torn, dark dried blood, milky clouded eyes, ripped stained clothing.
They close distance slowly across the full runtime, more emerging into frame.
Cold desaturated overcast grade; fog thickens with depth so the far ranks are
silhouettes. His performance unchanged — [unfazed / his existing glance back at 2s
now reads as checking the distance].
```
Audio: `layered low moans and wet rasps, shuffling and dragging footsteps growing
closer, a distant scream, flies.` Sprinter variant: `full-sprint, feral, crashing
through [obstacle]` + `pounding footfalls, snarling, ragged breathing closing fast.`

### Rain fight (rain added to existing fight footage)

**Hard rule first:** the choreography, timing, and camera are the source's. Rain wraps the fight; it never re-times it. Don't add slow-motion unless the source already has it.

**How it's really shot:** movie rain only reads when **backlit** — crews rig lights behind the rain so every drop catches; wet ground is a light amplifier. So write the light with the water: name the source (streetlight, neon, a lightning flash, headlights) *behind* the action.

**What sells it:** water as a consequence of the fight — spray whipping off a hook, droplets flying off hair on the snap of a turn, water sheeting off shoulders between exchanges, splashes under every footfall, puddles rippling from impacts. Wet fabric goes heavy and clinging; skin sheens matte-wet, not gloss.

**Prompt block:**
```
Heavy rain sheets through the frame, backlit by [the streetlight behind them] so
every drop reads as a bright streak against the dark. The fight is unchanged —
every strike, block and footfall exactly as in the source — but the world answers
it: spray whips off each punch, droplets fly from hair on every sharp turn, water
sheets off their shoulders between exchanges, every footfall splashes, puddles
ripple outward from impacts. Wet clothing clings and swings heavy. The ground is
rain-slicked, holding muted flat reflections of the light — reflection, not mirror.
Cool desaturated grade, deep blacks, the backlight carving silhouettes.
```
Audio: `driving rain on asphalt, splashing footwork, wet impacts landing heavier,
water dripping off them in the pauses` (+ `a thunder roll under the exchange` for a storm).
Lightning variant: strobe the peaks — `a lightning flash freezes the frame at the
moment of contact, thunder cracking behind it` — flashes land on the source's own
impact beats, never re-timed.

---

## Sources (research base)

- Higgsfield — "AI VFX Just Got Insane — Seedance 2.0 in 4K" (footage-VFX lock-header patterns, environment swaps, creature integration): higgsfield.ai/blog/vfx_4k
- HeyMarmot — Seedance 2.0 Prompting Guide (official-guide editing patterns, reference assignment): heymarmot.com/blog/seedance-2-prompting-guide
- PromeAI — Edit Seedance 2.0 Videos: Extend, Replace & Repair (continuity recipes, repair workflow, QC): promeai.pro/blog/seedance-2-0-video-editing-extend-replace/
- Emily2040 seedance-vfx (effects contract, timing/dissipation): github.com/Emily2040/seedance-2.0
- Nature TTL / ItsJustLight (rainforest light behavior); Lawrence of Arabia & Dune cinematography analyses (desert palette, mirage/telephoto); TV Tropes "Zombie Gait" + genre histories (movement registers); ASC "Normal" + filmmaking guides on rain rigs and backlighting (rain fights).
- PromeAI — Multi-Shot Consistency: Planning & Anchors (anchor blocks, drift failures/fixes, continuity checklist): promeai.pro/blog/seedance-2-0-multi-shot-consistency-planning/
- CrePal — Character Consistency: Stopping Identity Drift (drift patterns, reference hygiene, recovery plan): crepal.ai/blog/aivideo/blog-seedance-2-0-character-consistency/


<!-- ═══════ FILE: gen-media-router/SKILL.md ═══════ -->

---
name: gen-media-router
description: Pick the right AI media model for a brief, then route to the correct specialist prompt skill (seedance-2-prompter, kling-prompter, or nano-banana-prompter). Use this skill PROACTIVELY whenever the user describes a generative-media task without naming the model — phrases like make a video, generate an image, create a clip, design a poster, animate this, build a storyboard, render a mockup, make a Reels hook, do a product shot, edit this photo, create AI imagery. Also use when the user names a model the assistant has a dedicated skill for, to load that skill cleanly. Covers a clear video-vs-image decision table, Seedance-vs-Kling tradeoffs, chained workflows like still-in-Nano-Banana then animate-in-Seedance, identity-locking patterns across tools, and common model-mismatch traps. The job is to keep video work in video models and image work in image models, every time.
---

# Gen Media Router

The single most common failure in AI media work is reaching for the wrong tool — using a video model to make a still, or an image model to make a clip. This skill is the first stop. Read the brief, pick the right tool, then load the specialist skill that handles the actual prompt.

---

## The decision in three questions

Ask the user (or extract from context) three things. The answer to **all three** locks the choice:

1. **What's the deliverable — a still image or a video?**
2. **Do they have a model already in mind, or should I recommend one?**
3. **Are they chaining (e.g., a Nano Banana still that then animates in Seedance), or generating in one tool only?**

If you can't tell from context, ASK using the AskUserQuestion tool. Don't guess. Guessing is what produces the "you used a video model for a poster" error.

---

## Decision table — deliverable → model → specialist skill

| Deliverable | Model family | Specialist skill to load |
|---|---|---|
| Still image, poster, mockup, key art, storyboard panel, product packshot, character portrait, brand graphic, IG feed post | **Nano Banana** (Gemini Flash Image / Pro Image) | `nano-banana-prompter` |
| Image edit — remove/add/modify elements, style transfer, conversational refinement of an existing still | **Nano Banana** | `nano-banana-prompter` |
| Short video clip 5-10 s, cinematic style, single render with optional multi-shot, native audio | **Seedance 2.0** | `seedance-2-prompter` |
| Short video clip 5-10 s, fast-motion or sports action, very precise camera control, Elements identity lock | **Kling** (2.6 Pro / 3.0) | `kling-prompter` |
| Animating a still image with controlled motion | Either video model — **Kling** is often better for tight motion control via image-to-video; Seedance better for natural-language motion description | `kling-prompter` or `seedance-2-prompter` |
| Multi-shot video sequence inside one render | **Seedance 2.0** (timeline prompting or natural-prose multi-cut) | `seedance-2-prompter` |
| Multi-shot video sequence via separate generations + end-frame chaining | **Kling** | `kling-prompter` |
| Live-data / web-search visual (e.g., "search current weather and render it as…") | **Nano Banana 2 / Pro** | `nano-banana-prompter` |
| Synced dialogue + lip-sync video | **Seedance 2.0** (native audio + lip-sync) | `seedance-2-prompter` |
| Brand wordmark / proprietary typography in image | **Nano Banana** stylised supers + post-processing for exact kerning | `nano-banana-prompter` |

---

## Seedance vs Kling — when to pick which (both are video)

Both are excellent. Pick on these axes:

| Axis | Lean Seedance | Lean Kling |
|---|---|---|
| Natural-language prompt fluency | ✓ Seedance reads loose prose well | Kling rewards structured prompts |
| Multi-shot inside one generation | ✓ Seedance does this natively | Kling needs end-frame chaining |
| Camera control precision | Both excellent | ✓ Kling has marginally tighter camera obedience |
| Image-to-video animation | Good | ✓ Kling 2.6 Pro / 3.0 is best-in-class here |
| Identity locking across multiple shots | Reference Image N inline | ✓ Kling Elements feature is more constrained but cleaner UX |
| Native synced audio (dialogue + foley) | ✓ Seedance 2.0 has this | Kling does not (silent video, add audio in post) |
| Text overlays inside the frame | ✓ Seedance renders supers natively | Kling typically needs post-processing |
| Cost per second of output (approximate) | Slightly cheaper | Slightly higher at Pro tier |
| Generation speed | Faster | Slower especially at 1080p |
| Aspect ratio range | 21:9, 16:9, 4:3, 1:1, 3:4, 9:16 | 16:9, 9:16, 1:1 mostly |
| Duration range | 4-12 s | 5 s or 10 s |

**Quick rule of thumb:**
- *Sound-on social cutdowns with text on screen* → Seedance.
- *Cinematic image-to-video with precise camera control* → Kling.
- *Multi-shot one-render hook* → Seedance.
- *Long-form story chained from clean keyframes* → Kling.

If genuinely ambiguous, **default to Seedance for speed of iteration** and switch to Kling if motion is wonky or you need image-to-video precision.

---

## Chained workflows (the real-world recipes)

Most production work isn't one model — it's a chain. Here are the canonical chains.

### Chain 1 — Identity-locked character video

```
Nano Banana                Kling (or Seedance)
[generate clean portrait] → [upload as Elements reference] → [animate]
```

Use when you need a specific face to appear consistently across multiple video clips. The Nano Banana portrait carries the face; Kling Elements (or Seedance Image N) locks it through the video.

### Chain 2 — Product-locked video ad

```
Nano Banana                       Seedance / Kling
[generate hero product photo] → [upload as Image 1] → [generate ad-style videos]
```

Use when you need to feature a specific product (mask, bottle, watch) consistently. Pre-render the product still cleanly in Nano Banana, then attach to every video generation.

### Chain 3 — Storyboard then animate

```
Nano Banana                        Kling I2V                    Editor
[storyboard panels, one per beat] → [animate each as 5s] → [cut together]
```

Use when the brief needs hard control over composition and framing per shot. Storyboard the whole thing in Nano Banana with consistent style, then turn each frame into 5 seconds of motion via Kling I2V.

### Chain 4 — Live data → visual → animated

```
Nano Banana 2                   Seedance / Kling
[web-search-grounded image] → [animate the result]
```

Use when the visual depends on real-time information. Only Nano Banana 2 / Pro can fetch live data, so the still has to come from there.

### Chain 5 — Poster + motion teaser

```
Nano Banana                            Seedance with text
[hero poster at 4K with typography] → [extract still as ref, generate motion teaser with matching style]
```

Use for campaign launches that need both a static asset and a moving asset that share visual DNA.

---

## Identity-locking patterns across tools

A character or product needs to look the same across many generations. Three workflows, ordered by reliability:

### Workflow A — single high-quality reference (most reliable)

1. Render one strong portrait in Nano Banana at 4K. Lock the face exactly as wanted.
2. Save that image. Reference it as `Image 1` (Seedance), upload to Elements (Kling), or attach (Nano Banana subsequent edits).
3. Generate downstream work referencing that single anchor.

### Workflow B — multi-angle reference (best for video)

1. Render 3 still portraits in Nano Banana — front, profile, ¾-view, same outfit and lighting.
2. Upload all three to Kling Elements (or as multiple Image refs in Seedance).
3. Generate downstream video.

### Workflow C — conversational chain (Nano Banana only)

1. Render an image of the character.
2. Use Nano Banana conversational editing to put them in new scenes — *"the same woman, now in a coffee shop at golden hour"*.
3. After 3-4 turns, re-anchor by re-uploading the original portrait as a fresh reference, because identity drifts.

---

## Model-mismatch traps to avoid

**Don't ask Nano Banana for a video.** It's an image model. The output will be a still.

**Don't ask Seedance for a poster with brand-mandated wordmark kerning.** Seedance's text rendering is good for atmospheric supers, not for pixel-perfect wordmarks. Pre-render in Nano Banana or do typography in post.

**Don't ask Kling for native synced dialogue.** Kling video is silent. Add audio in post, or switch to Seedance if synced dialogue is the brief.

**Don't ask Seedance for live web-search grounding.** Seedance has no web access. Use Nano Banana 2 / Pro for live-data visuals, then animate downstream.

**Don't chain text-heavy Nano Banana output into a video model expecting the text to stay sharp.** Video models often re-interpolate frames around the text and degrade legibility. For sharp typography in video, render text in Nano Banana, but composite as a post-layer in the editor, not inside the video model.

**Don't try to generate a 13-shot 60-second video in one Seedance render.** Multi-shot inside one render works well up to ~10 seconds and ~4 cuts. Longer than that, chain generations.

---

## How this skill behaves at runtime

When this skill triggers, follow this sequence:

1. **Read the brief** the user gave. Identify deliverable type (still vs video), any model already named, and any chaining needs.
2. **If anything is unclear, use the AskUserQuestion tool** to clarify model, deliverable type, length, and aspect ratio. Don't write a prompt until those are nailed.
3. **Pick the specialist skill** from the decision table.
4. **Hand off to the specialist skill** — load its SKILL.md and follow its prompting conventions.
5. **If the brief requires chaining**, name the chain explicitly and walk the user through each step in order, switching specialist skills as needed.

This skill never writes a model-specific prompt on its own. It picks the tool and routes — the specialists do the writing.

---

## Specialist skills this router hands off to

- **seedance-2-prompter** — Seedance 2.0 / Pro / Fast and Higgsfield Marketing Studio prompting. Video.
- **kling-prompter** — Kling 1.6 → 3.0 (Kling O3) prompting. Video.
- **nano-banana-prompter** — Gemini 2.5 / 3.1 Flash Image and Gemini 3 Pro Image prompting. Image and image editing.

If a future tool appears (Veo 3, Sora 2, Runway Gen-4, Midjourney v7, Imagen 4, Pika, etc.) and there's no specialist skill for it yet, recommend the closest match from the existing three and flag that a dedicated skill could be built.

---

## See also

- `references/quick_reference.md` — single-page summary card for fast lookup
- `references/comparison_matrix.md` — feature-by-feature matrix across Seedance / Kling / Nano Banana
- `references/chain_recipes.md` — worked examples of the five canonical chained workflows


<!-- ═══════ FILE: gen-media-router/references/comparison_matrix.md ═══════ -->

# Feature-by-feature comparison — Seedance vs Kling vs Nano Banana

A single matrix you can scan to pick the right tool for a specific brief.

| Feature | Seedance 2.0 | Kling 2.6+ | Nano Banana 2 / Pro |
|---|---|---|---|
| **Output type** | Video | Video | Image |
| **Standard duration** | 4-12 seconds | 5 or 10 seconds | n/a (single image) |
| **Max output resolution** | 720p | 1080p Pro / 4K O3 | 4K |
| **Aspect ratios** | 21:9, 16:9, 4:3, 1:1, 3:4, 9:16 | 16:9, 9:16, 1:1 mostly | 21:9, 16:9, 4:3, 1:1, 3:4, 4:5, 5:4, 9:16, 1:4, 4:1, 1:8, 8:1 (Pro) |
| **Native synced audio** | ✓ (1.5 Pro / 2.0) | ✗ | n/a |
| **Native text rendering in output** | ✓ (good for stylised supers) | ✗ (add in post) | ✓ best-in-class typography |
| **Multi-shot inside one render** | ✓ natural prose or `[Ns]` timeline | ✗ (chain via end-frame) | ✓ multi-panel storyboard in a single image |
| **Multi-shot via chaining** | ✓ (Track Completion ≤15s) | ✓ (end-frame to next I2V) | n/a |
| **Image-to-video** | ✓ | ✓ best in class | n/a |
| **Reference-to-video** | ✓ (up to 14 image / video refs) | ✓ Elements feature (2-4) | n/a |
| **Identity locking** | inline `Image N` references | Elements feature | inline multimodal references |
| **Max input refs** | 14 | 4 | 14 |
| **Conversational editing** | ✗ (one-shot) | ✗ (one-shot) | ✓ killer feature, multi-turn |
| **Web search grounding** | ✗ | ✗ | ✓ (Nano Banana 2 / Pro only) |
| **Dialogue + lip-sync** | ✓ (quoted dialogue in prompt) | ✗ | n/a |
| **Camera-language obedience** | High | Highest | High (still photography terms) |
| **Prompt style** | Loose natural prose | Structured 5-7 element formula | Natural-language scene description |
| **Negative prompts** | Accepted but not critical | Critical, always include | Less reliable, prefer positive framing |
| **Emphasis syntax** | None native | `++weight++` | None native |
| **Content credentials** | depends on provider | depends on provider | C2PA + SynthID always |
| **Knowledge cutoff (live data)** | n/a (no search) | n/a | January 2025 + live search (Pro) |
| **Approximate cost per output** | $$ | $$$ at Pro | $ for Flash, $$ for Pro |
| **Approximate speed (5s clip / 1 image)** | 30-45 s | 60-90 s | 5-15 s |
| **Best for** | Multi-shot social cuts with supers and audio | Cinematic image-to-video, identity-locked hero shots | All still imagery, edits, storyboards, posters |
| **Worst for** | Pixel-perfect brand typography | Multi-shot single render | Anything moving |

## Tradeoff summary in one paragraph

Seedance is the fastest and the most versatile — multi-shot in one render, native audio, native supers, broad aspect ratios. Kling is the most cinematic for single-shot work, especially when animating a known still or locking identity through Elements, but it can't multi-shot in one render and has no native audio. Nano Banana is the image specialist — text-to-image, image edits, conversational refinement, identity-locking via multi-reference, native typography, and web-search grounding on Pro. Real-world projects usually need at least two of the three.


<!-- ═══════ FILE: gen-media-router/references/chain_recipes.md ═══════ -->

# Chained workflow recipes — real-world tool chains

Five canonical chains. Each one solves a specific production problem that no single model can handle alone.

---

## Recipe 1 — Identity-locked character video

**Problem:** the same character has to appear, recognisably the same, across multiple video shots.

**Why this needs a chain:** video models drift faces across renders. The fix is to nail the face once, in a still, then carry that still as a reference into every video call.

**Steps:**

1. **Nano Banana** — generate a clean, high-resolution portrait of the character. Use Framework 1 (text-to-image) with specific material, lighting, and lens details. Render at 4K.
2. **Nano Banana (optional)** — generate two additional angles (profile and ¾-view) of the same character using conversational editing to maintain identity. Save all three.
3. **Kling** (preferred for I2V identity locking) — upload all three portraits to the **Elements** feature. Write the new-scenario prompt that doesn't re-describe the character. Generate.
4. **Or Seedance** — attach each portrait as `Image 1`, `Image 2`, `Image 3`. Reference inline: *"Anna (referencing Image 1, Image 2, Image 3) walks across the soundstage…"*. Generate.

**Output:** a video clip where the character looks identical to the Nano Banana portrait.

---

## Recipe 2 — Product-locked video ad

**Problem:** an ad campaign needs a specific real-world product to appear consistently across many video assets (different ad styles, different scenes).

**Steps:**

1. **Nano Banana** — render the hero product photo. Use specific material descriptions (brushed steel, navy leather, etc.) and named lighting (three-point softbox). Render at 4K, 1:1 or 4:5 aspect ratio.
2. **Nano Banana** — optionally generate a 3-view product reference sheet via conversational editing: *"now show the same product from the right profile"*, *"now from the back"*. Combine all three into a single reference sheet.
3. **Seedance** — attach the reference sheet as `Image 1` in every video generation. Reference the product inline: *"the wristwatch from Image 1, maintaining consistent metal finish and dial layout"*. Generate ad-style videos.
4. **Loop** — for each ad style (sports, fashion, OOH, viral, etc.), re-run step 3 with a different prompt context.

**Output:** N ad-style videos all featuring the exact same product geometry.

---

## Recipe 3 — Storyboard-then-animate

**Problem:** a complex sequence needs precise per-shot composition before any motion is committed. You want to see the framing of every beat first.

**Why this needs a chain:** prompting motion in video models can be unpredictable — you don't always know exactly what the first frame will look like. Storyboarding in image space gives you complete framing control.

**Steps:**

1. **Nano Banana** — render each storyboard beat as a still image, in the same aspect ratio and style. Use Framework 1 or 2. Lock identity across panels via either conversational editing (Workflow A) or multi-reference (Workflow B). Output 8-13 panels.
2. **Kling I2V** — for each panel, run an image-to-video generation with a motion-direction prompt. *"Camera slowly tracks right. Subject takes one slow step forward. Subtle wind in foreground."* Generate one 5-second clip per panel.
3. **Editor (Premiere / DaVinci / CapCut)** — cut all the 5-second clips together at the beats. Add transitions, supers, audio, music in post.

**Output:** a fully storyboarded video with hard control of composition at every cut.

---

## Recipe 4 — Live-data visual then animate

**Problem:** the visual must reflect real-world current information — weather, news, sports scores, time of day at a specific location.

**Why this needs a chain:** only Nano Banana 2 / Pro can pull live data via web search. Video models cannot.

**Steps:**

1. **Nano Banana 2** — use Framework 5 (web-search-grounded). Start the prompt with *"Search for [X]…"*, then *"Use this data to determine…"*, then *"Visualise the result as…"*. Render the still.
2. **Seedance or Kling** — take that still as the input to an image-to-video generation. Add motion-direction text. Generate.

**Output:** a video clip whose visual content reflects live real-world data, with animation.

**Note:** the moment the still is rendered, it's locked. The video animates a snapshot of the world at the moment Nano Banana fetched the data — it doesn't continue updating.

---

## Recipe 5 — Poster + motion teaser pair

**Problem:** a campaign launch needs both a static hero (poster, IG feed, OOH) and a short motion teaser (Reels, TikTok) that share visual DNA.

**Steps:**

1. **Nano Banana Pro** — render the hero poster at 4K. Include the campaign typography, the hero subject, the brand identity. This is the visual North Star for the campaign.
2. **Nano Banana** — render 2-3 alternate still variants for different aspect ratios (1:1 for IG feed, 9:16 for Stories, 21:9 for OOH).
3. **Seedance** — generate the motion teaser. Reference the hero poster as the style anchor (*"matching the look and grade of the attached hero still"*) and the hero subject as the identity anchor.
4. **Editor** — assemble the motion teaser with supers added in post (so brand typography matches the poster exactly).

**Output:** a static-and-motion campaign suite with consistent visual DNA across formats.

---

## How to talk through a chain with the user

When you've picked a chain, walk the user through it step-by-step before generating:

> *"For this brief I'd chain two tools — Nano Banana to render a clean portrait of the character first, then Kling I2V to animate that portrait inside the alley scene. Step one takes about 20 seconds in Nano Banana; step two takes about 60-90 seconds in Kling. Want me to start with the Nano Banana still?"*

This makes the workflow legible and gives them a stop-point if they want to reroute.

---

## When NOT to chain

If the brief is simple — *"a 5-second clip of waves on a beach"* — don't chain. One Seedance generation does it.

If the chain adds steps without adding value, drop it.

Chains earn their complexity when they solve a specific drift, consistency, or feature-gap problem. Otherwise, single-tool generation is faster and cheaper.


<!-- ═══════ FILE: gen-media-router/references/quick_reference.md ═══════ -->

# Quick reference — which model, in one card

## Image vs video — the only question that matters first

| If the deliverable is… | Use |
|---|---|
| Still image, poster, mockup, key art, storyboard panel, product packshot, IG feed post, edit of a photo | **Nano Banana** (image) |
| Video clip, motion teaser, animated still, Reels hook, ad film, music video | **Seedance** or **Kling** (video) |

If both — chain. Generate the still in Nano Banana first, then animate.

## Seedance vs Kling — the second question (only if it's video)

| Pick Seedance when… | Pick Kling when… |
|---|---|
| You want multi-shot in one render | You want very precise camera control |
| You want native dialogue + lip-sync | You're animating a specific still (I2V) |
| You want native on-screen supers | You want Elements identity lock |
| You want loose natural-language prompting | You want a strict prompt structure |
| You want fastest iteration | You want highest-end cinematic look |

## Default routing

- Brief says "image" / "still" / "poster" / "edit photo" → `nano-banana-prompter`
- Brief says "video" / "clip" / "Reels hook" / "ad film" → `seedance-2-prompter`
- Brief says "animate this still" / "image-to-video" → `kling-prompter`
- Brief says "make a campaign" with both still + video → chain Nano Banana → Seedance/Kling
- Brief says "I want it to feature a specific character/product" → start with Nano Banana hero still, lock as reference, then video model

## Identity-locking pattern

Always works:
1. Generate the strongest possible reference still in Nano Banana.
2. Use that still as the identity anchor for every downstream video generation.
3. Keep style/lighting/color terms identical across all calls.

## When the brief is ambiguous

Use `AskUserQuestion` to clarify:
- Image or video?
- Which model do you want me to use, or should I pick?
- Duration / aspect ratio?
- Are you chaining tools?

Never guess.
