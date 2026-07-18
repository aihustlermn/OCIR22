# SOLENNE — «THE SPARK» scroll-film build state

Skill: scroll-film-studio · resumable handoff. **Site v1 SHIPPED on Lane A (pure-code).**
Lane B (Seedance footage) remains blocked by egress policy — see below.

## v2 — Mongolian localization (SHIPPED)
- Rebrand: **AISOLENNE.MN** (wordmark Unbounded latin; `.MN` in acid). All copy Mongolian.
- Type change (Cyrillic Ө/Ү support — Unbounded/Space Grotesk/Space Mono have none):
  display **Tektur** · body **Golos Text** · mono **JetBrains Mono** (latin+cyr+cyr-ext
  subsets vendored with unicode-range; Unbounded kept latin-only for the wordmark).
- Services ×4: AI Видео · AI Фото · AI Маркетинг · 3D Вэбсайт. Work grid reframed as
  capabilities (no fictional case studies).
- New #cred section: Higgsfield Academy credential card — The AI Filmmaking Pipeline /
  Cinema Studio Pro Guide / Ai Hustler / HFA-2026-5KUVESXALFDL / 2026.07.17.
- Contacts: CTA + finale + footer → https://www.instagram.com/aisolenne.mn/ ; tel +976 9636-9633.
- Verified (screens + jank p95 17ms, same profile). Artifact preview:
  https://claude.ai/code/artifact/edb47b25-1621-4c4e-9cc0-05325ef67e02

## Brand
- **SOLENNE** — AI agency: marketing + website builder. (v2: public name AISOLENNE.MN)
- Logo: acid-green atomic starburst (8-point star + two elliptical orbit swooshes) on black — built as inline SVG in `index.html` (header, footer, work tile) and mirrored in canvas (`drawStarburst`).
- Palette: acid green `#C6FF16` · black `#050505` · greenish white `#F4FFE0` · muted `#8A9284`.
- Type: display **Unbounded** · body **Space Grotesk** · HUD/mono **Space Mono** — vendored woff2 in `assets/fonts/` (variable files for Unbounded + Space Grotesk).
- Chapters: I. IGNITION · II. THE MIND · III. THE FORGE · IV. THE LAUNCH · V. THE CONSTELLATION.
- Camera law: one continuous FORWARD push the entire film. No reversals.

## What shipped (branch `claude/solenne-spark-scroll-film-13tpty`)
- `index.html` — the full site, self-contained: 900vh film driver + CSS-sticky stage,
  live canvas renderer (no footage) playing all 5 chapters as ONE continuous forward push:
  spark→blast (radial rays + blink flash) → endless neural web fly-through → wireframe UI
  assembling (partial-perimeter stroke draw) → corridor of glass screens (fake-3D trapezoids,
  light sweeps) → orbiting-screens constellation easing to rest around the canvas starburst.
  Warp-streak particle layer runs the whole film as connective tissue; lerped progress (0.14).
- Beat overlays with data-in/peak/out envelopes; hero char-reveal; finale bottom-anchored
  (canvas star is the hero of that frame).
- HUD: chapter readout + progress bar (Space Mono), hides after the film.
- After-film: services ×3 (clip-path reveals) · work grid ×4 (inline-SVG generative covers) ·
  light manifesto (word-reveal; header flips via `.on-light` ScrollTrigger) · CTA marquee
  (velocity-skew) · footer with real X/Instagram/LinkedIn SVGs. Copy: EN (state-file plan;
  interview was in Mongolian — offer a MN copy pass to the user).
- Vendored `assets/vendor/{gsap,ScrollTrigger,lenis}.min.js` (npm, no CDN).
- Dev contract implemented: `?jump=<y>` force-settled landing, `window.__ready`,
  `__jankReport()`, glyph-atlas warm-up at boot, `prefers-reduced-motion` static-poster mode.

## Verification (headless system Chromium /opt/pw-browsers/chromium, software raster, 1440×900)
- Screenshots via skill verify.js at every beat + content section: all pass art direction.
- Jank sweep (13px/frame full page): p95 = 17ms every run; max varies 43–69ms with 0–3
  isolated >50ms frames at first-paint of sections (positions non-deterministic — scheduler
  noise of the GPU-less rasterizer; one run fully clean). Judged sound for real hardware.

## Higgsfield hosting deploy — BLOCKED (egress), website already created
- User chose Higgsfield hosting. `create_website` succeeded:
  website_id `5bd453bf-4131-412b-aeb4-314ac8c6172a`, slug `aisolenne`, type website
  (category param required by server; "other" accepted). Live URL will be `aisolenne.<host>`.
- `git clone https://apps-repos.higgsfield.ai/...` → CONNECT 403: **apps-repos.higgsfield.ai
  denied by egress policy** (same class as cloudfront). Do not retry; policy change needed.
- To unblock: allow `*.higgsfield.ai` (and ideally `*.cloudfront.net`) in the environment's
  Network access, then: website_repo_access (fresh token) → clone → port index.html into the
  TanStack Start app per get_website_creation_instructions flow (read references/website-flow.md
  + scroll-scrub*.md; our GSAP/canvas film can be embedded) → app-meta.json cover+metadata
  (references/app-cover.md) → commit/push → deploy_website → website_status for live URL.

## Lane B — still BLOCKED (unchanged)
- Egress policy denies `d8j0ntlcm91z4.cloudfront.net` (403 CONNECT; also higgsfield.ai,
  jsdelivr, unpkg). Google Fonts + npm registry ARE allowed. Do not retry policy denials.
- Opening keyframe exists: Nano Banana Pro job `7d639995-57b0-454d-b030-303e7a6cd928`
  (2752×1536): https://d8j0ntlcm91z4.cloudfront.net/user_34vsx3XR3W7YnkGCFxTxsQ6I7wp/hf_20260718_154324_7d639995-57b0-454d-b030-303e7a6cd928.png
- Draft chain 5×5s @480p/fast (7.5 cr each) NOT started; no credits spent beyond keyframe.
  Balance at last check: 5,288 cr (Max plan). generate_audio MUST be false (seedance_2_0 defaults true!).
- To unblock: user allows `*.cloudfront.net` in the environment's Network access settings
  (new session may be needed after the change). Verify with:
  `curl -sS -o /dev/null -w "%{http_code}" <keyframe URL>` → expect 200.

## Lane B resume plan (when unblocked)
1. Run the draft chain per contract below; junction SSIM gates ≥0.88.
2. Assemble ~300 frames @1280 q4 → `frames/`; swap the canvas renderer for the skill's
   ImageBitmap scrub engine (engine.md §Scrub-engine) inside the SAME stage/beat/HUD shell —
   the page structure, beats, HUD, content sections all stay.
3. Verify (beats + junctions + jank), user approves drafts → master 1080p/std (45 cr × 5 = 225 cr).

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

## Open items for the user
- Allow `*.cloudfront.net` egress to unlock the Seedance footage film (Lane B).
- Confirm copy language (currently EN) — MN version on request.
- Replace placeholder contact (`hello@solenne.agency`) + social URLs with real ones.
- Optional: deploy (Vercel or any static host — the site is a single `index.html` + `assets/`).
