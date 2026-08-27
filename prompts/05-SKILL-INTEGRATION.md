# 05 — SKILL INTEGRATION

The generation half of AdMirror (steps 11–13) must run through the operator's own
Claude Skills. This file defines how they mount and how each one is called.

## 1. Which skills, and what each owns

| Skill | Owns | Called by | Stage |
|---|---|---|---|
| `script-writer` | Hooks, beat structure, retention, emotional arc, UGC/ad copy craft | `script_director.md` | 11 SCRIPT |
| `nano-banana-prompter` | Nano Banana / Gemini image prompt grammar, identity locking, photoreal + anti-AI-look controls, in-image text | `frame_director.md` | 12 FIRST_FRAME |
| `seedance-2-prompter` | Seedance 2.0 prompt grammar, `@Image`/`@Video`/`@Audio` binding, multi-shot Shot 1..N, native audio, duration/res limits, ModelArk submit/poll API | `motion_director.md` | 13 MOTION |
| `seedance-director` *(optional, if present)* | Higher-level Seedance routing: T2V vs I2V vs ref-to-video vs V2V edit, cinema mode, realism stack | `motion_director.md` | 13 MOTION |
| `gen-media-router` *(optional)* | Model choice when a brief is ambiguous | pre-stage router | 11→13 |
| `imagine-art-navigator` *(optional)* | Driving imagine.art in a browser session | fallback provider | 12/13 |

Authoritative rule: **the skill owns prompt grammar; the backend owns orchestration.**
Do not reimplement any of the above in Python. If `seedance-2-prompter` says the
duration ceiling is 15s and 1080p is the finalize tier, that constraint comes from the
skill file at runtime — do not hard-code it in a validator that will silently go stale.

## 2. Mounting — the skills ship inside this pack

**The actual skill files are bundled in `12`–`18`.** Five skills, 101 files, 1.5 MB,
split into seven thematic markdown bundles. `19-SKILL-MANIFEST.md` carries the
provenance, the per-file SHA-256 table, and the unbundle script that reconstructs the
mountable tree byte-for-byte (verified: 101 files, zero mismatches).

```bash
python unbundle.py . backend/.claude/skills     # script is in 19-SKILL-MANIFEST.md §4
```

Vendor, never symlink to `~/.claude/skills`. A container must carry its own skills, and
a generated ad must be attributable to the exact skill bytes that produced it.

Every `scripts`, `frames` and `videos` row stores the tree hash of the skill that
produced it, so when a skill is updated you can tell exactly which outputs predate the
change.

The bundles are also readable directly. An agent that needs Gulf casting guidance, or
the Seedance camera registers, or the retention-engineering reference, can read the
relevant bundle without mounting anything — see the routing table in `README.md`.

## 3. Invoking (Claude Agent SDK, Python)

```python
from claude_agent_sdk import ClaudeSDKClient, ClaudeAgentOptions

options = ClaudeAgentOptions(
    model="claude-opus-5",
    cwd=str(SKILLS_ROOT),          # dir containing .claude/skills/ or skills/
    setting_sources=["project"],   # REQUIRED: without this, skills are not discovered
    system_prompt=load_prompt("motion_director.md"),
    allowed_tools=["Skill", "Read"],
    permission_mode="acceptEdits",
)

async with ClaudeSDKClient(options=options) as client:
    await client.query(json.dumps(stage_input))
    result = await collect_structured(client)
```

Verify these option names against the installed `claude-agent-sdk` version before
building on them — the SDK surface moves. What must not change is the behaviour:
**skills discovered from a pinned on-disk location, and a hard failure if they are not.**

### Startup assertion (build this)

On worker boot, for each required skill: confirm the directory exists, the
frontmatter parses, and the `name` matches. Refuse to start otherwise. A worker
running without its skills produces confident, plausible, wrong output — which is
worse than an outage because nobody notices.

### Per-stage assertion

Each generation agent returns `skill_used`. If the returned value does not match the
expected skill name, fail the step. Also assert the transcript contains an actual
`Skill` tool invocation. Trust the trace, not the model's self-report.

## 4. Stage contracts

### 11 SCRIPT — `script-writer`
- **In:** angle-transfer brief, brand voice + banned words, duration, aspect, platform.
- **Skill governs:** hook construction, beat order, retention shape, CTA posture, the
  three hook variants.
- **Backend validates:** word count ≤ `2.6 × duration_s`; hook ends by t=3.0s;
  on-screen cards ≤ 4 and ≤ 6 words each; zero `banned_words`; every claim maps to a
  `proof_to_use` entry.
- **Out:** `scripts` row + `first_frame_intent` handed to stage 12.

### 12 FIRST_FRAME — `nano-banana-prompter`
- **In:** `first_frame_intent`, brand palette/imagery style, aspect, product reference
  images if any.
- **Skill governs:** prompt grammar, identity locking across references, the
  photoreal / UGC / phone-shot controls, and any in-image text handling.
- **Backend validates:** aspect matches target; vision QA against `qa_checklist`;
  max 2 corrections then `fallback_prompt`; then escalate to the user.
- **Out:** accepted image in S3 + the exact prompt, both persisted.

### 13 MOTION — `seedance-2-prompter`
- **In:** accepted frame (bound as an `@Image` reference), beats, audio direction,
  duration, aspect.
- **Skill governs:** the Subject/Motion/Environment/Aesthetics/Camera/Audio ordering,
  the closing global style sentence, `@Image` binding syntax, the Shot 1..N template
  when the script exceeds one generation, identity-lock ratios, native dual-channel
  audio, and the model IDs / duration / resolution limits.
- **Backend validates:** duration and resolution are within the limits the skill
  states; the frame reference is actually bound; a global style sentence is present;
  shot count matches the script's beat grouping.
- **Out:** `videos` rows, one per shot, with `seed` captured for reproducibility.

Concatenation across shots stays in the backend (ffmpeg), not in the skill.

## 5. Provider adapters vs skills

Keep these strictly separate:

- **Skill** = what the prompt says.
- **Adapter** = where the prompt is sent.

`adapters/video/` implements `submit(prompt, refs, params) -> task_id`,
`poll(task_id) -> status`, `fetch(task_id) -> bytes`. Implement `imagine_art.py`
first (the operator's own platform), then `modelark.py`. Same for
`adapters/image/`: `imagine_art.py`, then `gemini.py`.

The skill's prompt output must be portable across adapters. If an adapter needs a
parameter the skill doesn't emit, the adapter supplies a default and records it in
the row — it never edits the prompt text.

## 6. Optional: router

If `gen-media-router` is installed, run it once per brief before stage 12 to confirm
image-then-animate is the right pipeline for this creative. Some ad concepts are
better as a static image ad or a carousel, and the router will say so. Persist its
verdict on the brief. Do not let it silently change the plan — surface it in the
generation timeline as a node the user can see.
