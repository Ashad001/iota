# 19 — SKILL MANIFEST

Provenance, integrity hashes, and the exact procedure for turning the bundled skill
files (`12`–`18`) back into a mountable skill tree.

## 1. Bundles

| Bundle | Source files | Source bytes | Bundle SHA-256 |
|---|---|---|---|
| `12-SKILL-scriptwriting.md` | 21 | 308,962 | `f566479255bc576e…` |
| `13-SKILL-image-core.md` | 20 | 319,970 | `359bc47a8e5a8d72…` |
| `14-SKILL-image-casting-and-ads.md` | 15 | 174,358 | `0b21c98761c4ada8…` |
| `15-SKILL-image-styles.md` | 16 | 166,750 | `7c3b571996072958…` |
| `16-SKILL-video-seedance2.md` | 4 | 282,972 | `45f5955804311512…` |
| `17-SKILL-video-director.md` | 17 | 228,586 | `0f7875ac3d09f370…` |
| `18-SKILL-video-v2v-and-routing.md` | 8 | 60,895 | `60b0e6ffb70f12ff…` |

Total: **101 source files, 1,542,493 bytes** across 7 bundles.
Coverage is complete and non-overlapping — every skill file appears in exactly one
bundle, verified at build time.

## 2. Original skills

| Skill | Files | Bytes | Bundled into |
|---|---|---|---|
| `script-writer` | 21 | 308,962 | `12-SKILL-scriptwriting.md` |
| `nano-banana-prompter` | 51 | 661,078 | `13-SKILL-image-core.md`, `14-SKILL-image-casting-and-ads.md`, `15-SKILL-image-styles.md` |
| `seedance-2-prompter` | 4 | 282,972 | `16-SKILL-video-seedance2.md` |
| `seedance-director` | 21 | 267,167 | `17-SKILL-video-director.md`, `18-SKILL-video-v2v-and-routing.md` |
| `gen-media-router` | 4 | 22,314 | `18-SKILL-video-v2v-and-routing.md` |

`script-writer`, `nano-banana-prompter` and `seedance-2-prompter` are **required** —
stages 11, 12 and 13 fail loudly without them. `seedance-director` and
`gen-media-router` are optional routers; the pipeline degrades gracefully.

## 3. Provenance

Synced **2026-08-27** from `~/Downloads/claude-skills-export/01-my-skills/` (dated
2026-08-25 — the newest complete set on the machine, consistent with the copies in
`~/Downloads/jzb/skills/` and the 2026-08-20 context export).

Two things about the source worth recording:

1. `~/.claude/skills/` held only `seedance-2-prompter`, at **26 KB from 2026-06-01 with
   no `references/`** — an older, much smaller revision than the 65 KB + 3 reference
   files bundled here. The installed copy was stale; nothing here is built from it.
2. `seedance-director` has two lineages on disk. Bundled is the 2026-08-25 revision
   (21 files, 267 KB) matching the current skill set. A 2026-08-10 revision exists at
   `~/Documents/Codex/2026-08-10/por/work/selective-skill-groups/seedance-director/`
   with **47 files and 722 KB** — substantially more content, not merely restructured.
   Which is canonical was not obvious, so nothing was silently chosen: re-sync from
   that path if the older lineage is the one you want.

## 4. Unbundling

Each section inside a bundle begins with a marker line:

```
<!-- ═══════ FILE: nano-banana-prompter/references/text_rendering.md ═══════ -->
```

Splitting on those markers reconstructs every file **byte-for-byte** — verified across
all 101 files, zero mismatches.

```python
#!/usr/bin/env python3
"""Rebuild the mountable skill tree from bundles 12-18.

    python unbundle.py <pack_dir> <dest>      # dest = backend/.claude/skills
"""
import re, sys
from pathlib import Path

MARKER = re.compile(r"\n\n<!-- ═+ FILE: (.+?) ═+ -->\n\n")

def main(pack: Path, dest: Path) -> int:
    n = 0
    for bundle in sorted(pack.glob("1[2-8]-SKILL-*.md")):
        parts = MARKER.split(bundle.read_text(encoding="utf-8"))
        # parts = [preamble, path1, body1, path2, body2, ...]
        for rel, content in zip(parts[1::2], parts[2::2]):
            out = dest / rel
            out.parent.mkdir(parents=True, exist_ok=True)
            out.write_text(content, encoding="utf-8")
            n += 1
    print(f"wrote {n} files to {dest}")
    return 0

if __name__ == "__main__":
    raise SystemExit(main(Path(sys.argv[1]), Path(sys.argv[2])))
```

Verify against §6 after unbundling. A hash mismatch means a bundle was edited — the
bundles are archives, not documents to revise. Change a skill at its source and
re-bundle.

## 5. Mounting

The Agent SDK discovers project skills at `.claude/skills/` relative to the session's
`cwd`, and only when `setting_sources` includes `"project"`. Unbundle to:

```
backend/.claude/skills/script-writer/…
backend/.claude/skills/nano-banana-prompter/…
backend/.claude/skills/seedance-2-prompter/…
backend/.claude/skills/seedance-director/…      # optional
backend/.claude/skills/gen-media-router/…       # optional
```

Vendor, never symlink to `~/.claude/skills`. A container must carry its own skills, and
a generated ad must be attributable to the exact skill bytes that produced it.

### Boot and per-call guards

Three guards, all required — see `05-SKILL-INTEGRATION.md §3`:

- **`assert_skills_available()`** at worker boot: the three required skills are present,
  every `SKILL.md` frontmatter parses and self-identifies correctly, and the tree
  matches §6. Refuse to start otherwise.
- **`assert_skill_invoked(messages, expected)`** per generation stage: verify from the
  transcript that the `Skill` tool actually fired. Trust the trace, not the agent's
  `skill_used` self-report.
- **`stamp(stage)`** → persist `skill_name` + skill tree hash on every `scripts`,
  `frames` and `videos` row, so outputs stay attributable across skill updates.

**Why the guards exist.** A worker that starts without its skills answers anyway, from
the model's own defaults. The output is fluent, plausible, and silently ignores
everything the skill knows. That is worse than an outage, because an outage gets
noticed. Fail at boot, and verify per call.

## 6. File hashes

SHA-256 of every original skill file, for verification after unbundling.

| File | SHA-256 |
|---|---|
| `script-writer/SKILL.md` | `aaaf919d5d84fbdff7af39c807d071ce…` |
| `script-writer/references/ads.md` | `78e39cbf24dd8884916dfd9ac14ba481…` |
| `script-writer/references/ai-video.md` | `c2dda777037a8d382e807593c10df4d0…` |
| `script-writer/references/audio-hooks.md` | `fdafaf913b8bc7510edc21457527ea40…` |
| `script-writer/references/auteur-styles.md` | `963dc6b17cdf1f569489b0854f723045…` |
| `script-writer/references/campaign-arcs.md` | `41cee1506dff9d99bd3b172894752980…` |
| `script-writer/references/creative-ideation.md` | `93b206ae21a7a5c7f63187d8e15fea4d…` |
| `script-writer/references/emotional-arcs.md` | `c5041142f4b369a9f19464d9f0677bb6…` |
| `script-writer/references/hook-editing.md` | `aa4cbdb2ed402e95e5ecf65275ac5cab…` |
| `script-writer/references/hooks.md` | `de4909d5b5848df6b5693a46a963dc48…` |
| `script-writer/references/imagine-art-context.md` | `1b035b1fb05a97d455aa2535338f5a63…` |
| `script-writer/references/imagine-art-production.md` | `c1abf22c4c2e4e6750830b7b6e9714ad…` |
| `script-writer/references/pro-copywriting.md` | `581e9fd920c8ea64539c0902eb481934…` |
| `script-writer/references/prompt-iteration.md` | `768ce6cf9a58d274e00b45cab3554320…` |
| `script-writer/references/retention-engineering.md` | `7dbcead75585ff8b7dfe8d641075ac94…` |
| `script-writer/references/screenplay.md` | `ddd9502c7127185da6f2e9182c09a4c3…` |
| `script-writer/references/short-form.md` | `4bdafcb12968c1735bf89036bdef3255…` |
| `script-writer/references/unhinged.md` | `8054e0861f1dabd1dcaf4a3de8b98506…` |
| `script-writer/references/visual-direction.md` | `a4e8d007844816d218a63e993aad64f0…` |
| `script-writer/references/visual-language.md` | `b3ff5566381aa4c46bdf7972a4b23e2c…` |
| `script-writer/references/worked-examples.md` | `1d66b8aeab63327d0179e6b04788496d…` |
| `nano-banana-prompter/SKILL.md` | `860144ae44e9350fa6f3a776b6f3cff4…` |
| `nano-banana-prompter/references/apparel_and_beauty.md` | `af09b3a775adf65b107b458ac7368d62…` |
| `nano-banana-prompter/references/campaign_and_specialist_genres.md` | `6081feda86bec55e8a139c4126f39b94…` |
| `nano-banana-prompter/references/closeups_and_interviews.md` | `823da7d583d1ed6953581d6cd2de7f7b…` |
| `nano-banana-prompter/references/commercial_framing_and_set_design.md` | `052900464280ba5a8fd7754feaf71342…` |
| `nano-banana-prompter/references/composition_posing_and_critique.md` | `335aeeb6cdc4dca9ce23ad86e9f991c6…` |
| `nano-banana-prompter/references/creative_director_controls.md` | `6a784c36e7416e2ad41e76b5391b54f2…` |
| `nano-banana-prompter/references/creative_posts_copy_type_layout.md` | `6dfd90796451cf88a9115da542201e67…` |
| `nano-banana-prompter/references/director_styles_and_film_frames.md` | `1be9cceb50f78df1d475cf93778b5673…` |
| `nano-banana-prompter/references/field_findings.md` | `eb9b56497a0ecfd9449d93baaf09f08c…` |
| `nano-banana-prompter/references/film_look_references.md` | `ee33ecad69d395f92266e797731c1cca…` |
| `nano-banana-prompter/references/football_and_fifa_frames.md` | `8ad8de888e6e5bf4442219bd82d57f64…` |
| `nano-banana-prompter/references/frame_realism_engine.md` | `fb5830f9bfc22aa64b9868346cb1860e…` |
| `nano-banana-prompter/references/frameworks.md` | `0f81a0b7c6fbf3a812ae1a9579fec3da…` |
| `nano-banana-prompter/references/framing_scene_grammar_and_continuity.md` | `b7c14ee4d94e9b89cb9ec0e9f0c4c4eb…` |
| `nano-banana-prompter/references/generation_mechanics.md` | `c6ff12de6427f54957ee3e697aeb3205…` |
| `nano-banana-prompter/references/global_ethnicity_casting.md` | `933a6e82a178f33a995ccc98ddb694e5…` |
| `nano-banana-prompter/references/graphic_and_illustration_styles.md` | `21866ae9d798a199f59ab36cb92f4b3d…` |
| `nano-banana-prompter/references/identity_lock_and_filmmaking.md` | `2561c0a1426f5ad7bd4e6699620f4dcf…` |
| `nano-banana-prompter/references/lighting_craft_and_filmmaking_deep.md` | `d83964150996124cc0285fd23e25fb87…` |
| `nano-banana-prompter/references/mena_casting.md` | `ec6ee5aea6b2e5fb1174f3bc511d4b96…` |
| `nano-banana-prompter/references/movements_and_masters.md` | `72a9197a3039e65e0b9008f429398f5b…` |
| `nano-banana-prompter/references/music_video_styles_and_directors.md` | `2f68798fecf192a689644ecb1f057ba0…` |
| `nano-banana-prompter/references/optics_grain_and_light.md` | `ec65aae884a9dc92ab513cbb8ed13512…` |
| `nano-banana-prompter/references/pakistan_ads_and_directors.md` | `7523597f22ea5c2e5bb4ac2a46fde4af…` |
| `nano-banana-prompter/references/perspective_and_lens_geometry.md` | `2b849108d7cd705b8eb1acdb3ecff6d0…` |
| `nano-banana-prompter/references/photographer_styles_and_eras.md` | `5cac8c0734e1ed7037e7a4a4678f1abb…` |
| `nano-banana-prompter/references/photography_pro.md` | `0c752059ba411b00f7949fa69324be2a…` |
| `nano-banana-prompter/references/realism_and_ugc.md` | `1c5518088f12e4558cddde811a68d6ce…` |
| `nano-banana-prompter/references/realism_physics_deep.md` | `edc9883bce7677ea21487f5ef2e23bb5…` |
| `nano-banana-prompter/references/recent_ad_trends_and_directors.md` | `7a1e786b8df4085f9af5a2d0d9b19e95…` |
| `nano-banana-prompter/references/south_asia_casting.md` | `ca04d7ede54bb53582e97189f8f5a3d7…` |
| `nano-banana-prompter/references/southeast_asia_casting.md` | `3cb34b6ec5bd9b6209b6c6dec8019562…` |
| `nano-banana-prompter/references/storyboard_to_seedance.md` | `aa81187f8150fe5ce69766949fd2b29b…` |
| `nano-banana-prompter/references/streetwear_and_genz.md` | `19f3d21088c8e5a3f371ccdc31837d53…` |
| `nano-banana-prompter/references/structured_prompting.md` | `75fff8f633ee9be6cc110f6940995256…` |
| `nano-banana-prompter/references/style_anime_studios_deep.md` | `a2e9677acd152e379a50932c4f24a948…` |
| `nano-banana-prompter/references/style_arcane_fortiche.md` | `5105074d6ba6bae180fb6d0be382fdb0…` |
| `nano-banana-prompter/references/style_feature_cg_simulated_light.md` | `e707cdadef617a286534f5a881728025…` |
| `nano-banana-prompter/references/style_fine_art_movements_deep.md` | `07ade37c4a09a6b5864285f633d31422…` |
| `nano-banana-prompter/references/style_game_art.md` | `0feea198508be671edf5d50f93efa1af…` |
| `nano-banana-prompter/references/style_illustration_and_design_deep.md` | `bc4e2fa3ffd9914bf523636a22e289f5…` |
| `nano-banana-prompter/references/style_npr_and_animation_techniques.md` | `e01be8e6c0112b57523f1642324b5980…` |
| `nano-banana-prompter/references/style_product_render_cgi.md` | `7fd473013f2b3ccfe0e95d37a539efca…` |
| `nano-banana-prompter/references/styling_and_set_design.md` | `e793b01c83a47d1bc2682ed08845c158…` |
| `nano-banana-prompter/references/stylized_render_and_animation_looks.md` | `4ad4736aa878ea2c7c9653117900b4e1…` |
| `nano-banana-prompter/references/surgical_edits_and_higgsfield_routing.md` | `fecd42cdb7a1e35da68759822fce459f…` |
| `nano-banana-prompter/references/text_rendering.md` | `391daaa4a375d34964218179fbe8e32f…` |
| `nano-banana-prompter/references/tonal_families.md` | `e9d7c7848af84e3db3e33d695c7c853b…` |
| `nano-banana-prompter/references/uae_gulf_casting_and_ugc.md` | `47c35d823d94040ac7acd174608af8b5…` |
| `nano-banana-prompter/references/worked_examples.md` | `78b5fbc6685b57948031ed617dc1886f…` |
| `seedance-2-prompter/SKILL.md` | `9989efc09765e54afd46113389c3c2e4…` |
| `seedance-2-prompter/references/director-mode.md` | `1194c7a870b14319d88261d87f43ed74…` |
| `seedance-2-prompter/references/director-v3.md` | `45e713b1145da96708f2ba33fcbcd40e…` |
| `seedance-2-prompter/references/edm-dance-and-movement.md` | `9ecba5649353db8ac1c59b1ad83d6478…` |
| `seedance-director/SKILL.md` | `d5a088416c68fe7c65e5ea1e8c06d69a…` |
| `seedance-director/references/advanced-control.md` | `9e02936290f0f1ad365c76c3dcdb4f4f…` |
| `seedance-director/references/camera-depth-volumetrics.md` | `b1c157344b984214d42e831afb8b200b…` |
| `seedance-director/references/editing-and-cutting.md` | `9782e5dbe73cdd929e8f17feaf269991…` |
| `seedance-director/references/editing-sources.md` | `436fd6d920ce7aeaf9769d9cf0976bc4…` |
| `seedance-director/references/fashion-editorial.md` | `184b068998122ff94be596bf97f44b65…` |
| `seedance-director/references/model-card.md` | `9cd2f0ac348e438a5c6c8b93fe25e0ad…` |
| `seedance-director/references/model-poses-and-walks.md` | `7a898e99b17c70f6ad1919108285571b…` |
| `seedance-director/references/pro-techniques.md` | `9774f59f260f6364ce05613ec733dc88…` |
| `seedance-director/references/production-grammar.md` | `f819a2bac0268c030bbfb8c7b1d6be6d…` |
| `seedance-director/references/realism-and-camera.md` | `f270e9301348ccf898973408ab9dd0a5…` |
| `seedance-director/references/recipes-and-operations.md` | `c71051a1d6818db7820b818d925753dc…` |
| `seedance-director/references/research/action-environment-composition.md` | `37301539d12b2dcaba585a3bb0940ae5…` |
| `seedance-director/references/research/continuity.md` | `99b995d4125609ef1555002ba062cac5…` |
| `seedance-director/references/research/montage-and-rhythm.md` | `91b8e1e0765f3e22dd3f86d8488128ad…` |
| `seedance-director/references/scene-craft.md` | `92d8f1d9098382be8df8601b3c1a37ce…` |
| `seedance-director/references/surfaces-and-use-cases.md` | `a9d49437d50e8b9d02e7c2f563c29c83…` |
| `seedance-director/references/v2v-edits/continuity-and-detail.md` | `dce6de43d755caf7f3d989befb027ccb…` |
| `seedance-director/references/v2v-edits/edit-operations.md` | `d7fa693d3c6142c117d384ea27e27333…` |
| `seedance-director/references/v2v-edits/vfx-library.md` | `285dee0af63ff965b379188b04d7be40…` |
| `seedance-director/references/v2v-edits/world-library.md` | `d96f17113cb7bce1ec95d726e20dd019…` |
| `gen-media-router/SKILL.md` | `f1b1b26efac374f77e490015924e907d…` |
| `gen-media-router/references/chain_recipes.md` | `45602cbbe2d4f684e781a5573a8bb1b1…` |
| `gen-media-router/references/comparison_matrix.md` | `769bbd2630af827cb4bb738c976ded13…` |
| `gen-media-router/references/quick_reference.md` | `77f0ba55406fafbe837e75d53ae95b5b…` |
