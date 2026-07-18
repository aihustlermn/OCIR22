# SOLENNE — «THE SPARK» scroll-film build state

Skill: scroll-film-studio · Lane B (Higgsfield Seedance 2.0) · resumable handoff.

## Brand
- **SOLENNE** — AI agency: marketing + website builder.
- Logo: acid-green atomic starburst (8-point star + two elliptical orbit swooshes) on black. Recreate as inline SVG.
- Palette: acid green `#C6FF16` · black `#050505` · greenish white `#F4FFE0` · muted `#8A9284`.
- Type: display **Unbounded** · body **Space Grotesk** · HUD/mono **Space Mono** (Google Fonts, vendor for prod).
- Chapters: I. IGNITION · II. THE MIND · III. THE FORGE · IV. THE LAUNCH · V. THE CONSTELLATION.
- Camera law: one continuous FORWARD push the entire film. No reversals.

## Pipeline state
- [x] Interview + concept chosen: **THE SPARK**
- [x] Opening keyframe generated — Nano Banana Pro, job `7d639995-57b0-454d-b030-303e7a6cd928`
      (2752×1536, 16:9): https://d8j0ntlcm91z4.cloudfront.net/user_34vsx3XR3W7YnkGCFxTxsQ6I7wp/hf_20260718_154324_7d639995-57b0-454d-b030-303e7a6cd928.png
- [ ] BLOCKED: container egress policy denies `d8j0ntlcm91z4.cloudfront.net` → cannot download footage.
      Waiting for user to allow `*.cloudfront.net` in environment Network access (or new session after change).
- [ ] Draft chain 5×5s @ 480p/fast (7.5 cr each = 37.5 cr, confirmed via get_cost) — NOT started, no credits spent beyond keyframe.
- [ ] Junction SSIM gates ≥0.88 · assemble (~300 frames @1280 q4) · build page · verify (jank p95/max) · user approves → master 1080p/std (45 cr × 5 = 225 cr).
- Balance at start: 5,288 cr (Max plan). generate_audio MUST be false (defaults true on seedance_2_0!).

## Chain contract (per clip)
generate_video seedance_2_0 {duration 5, resolution 480p, mode fast, generate_audio false, aspect 16:9,
medias:[{role:start_image, value:<media_id|job_id>}]} → poll job_display → download mp4 →
`ffmpeg -sseof -0.05 -i clipN.mp4 -update 1 -q:v 1 clipN-last.png` → media_upload (presigned PUT + media_confirm) → next clip.
Clip 1 start_image = keyframe job id directly. SSIM gate: `ffmpeg -i A-last.png -i B-first.png -lavfi ssim -f null -`.

## Final video prompts (draft tier — reuse verbatim for 1080p master)
CONT = "Continue the exact same shot from the reference frame, identical framing, identical colour grade. Do not change the colour grade. "

1. **IGNITION** — "Continuous forward camera move. The tiny acid-green atomic spark at the center of the black void flares, trembles, then violently explodes into a blinding starburst of electric acid-green light; sharp rays and glowing particles shoot outward past the camera as it pushes straight forward into the heart of the blast. Pure black background, single acid-green light palette, extreme contrast, cinematic, subtle film grain, no text."
2. **THE MIND** — CONT + "The camera keeps pushing straight forward; the streaking green light resolves into a vast dark space filled with an endless glowing acid-green neural network — thousands of luminous nodes connected by thin pulsing filaments of light, bright signals traveling along the threads in every direction. The camera glides forward deep through the web. Pure black background, acid-green light only, cinematic, subtle film grain."
3. **THE FORGE** — CONT + "The camera keeps moving straight forward. Ahead, the glowing filaments weave themselves into orderly wireframe rectangles of acid-green light — browser windows, buttons, cards, grids of thin luminous lines assembling in mid-air out of the threads. The camera pushes forward between the half-built glowing structures as they snap together."
4. **THE LAUNCH** — CONT + "The wireframes ahead solidify into sleek dark glass screens glowing with luminous acid-green interfaces, floating in black space and arranged into a long receding corridor. The camera flies steadily forward down the corridor of floating screens, green light reflections sweeping across their surfaces."
5. **THE CONSTELLATION** — CONT + "The camera emerges from the corridor of screens into open black space: dozens of small glowing green screens orbit a brilliant acid-green star core along thin elliptical light-trails, together forming one huge atomic starburst constellation. The camera drifts slowly forward toward the radiant core as all motion gently eases almost to a stop."

## After-film sections (plan)
Services (AI marketing / AI website builder / brand systems) · selected work grid · manifesto line · CTA "Start your spark" · contact + socials. Copy: confident, minimal, EN (confirm language with user — interview was in Mongolian).

## Resume instructions
Read this file, verify cloudfront reachable (curl the keyframe URL), then run the draft chain per contract above. Working dirs in scratchpad: spark/{keyframes,clips,frames,junctions}. Deliverable site lives at repo root (index.html + frames/ + assets/), branch `claude/feature-configuration-myx2o8`.
