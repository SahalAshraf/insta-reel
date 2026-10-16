---
name: insta-reel
description: Create Instagram Reels (10s–5min) in SkillSarmaya style from a simple prompt such as “create a 59 sec reel on topic X”. Researches the topic, structures Hook-Substance-Payoff copy, builds a HyperFrames storyboard scene-by-scene, generates voice with Kokoro, images via local Flux, and outputs the final video plus Instagram caption, title and tags. Also handles multi-episode series. Use for finance education Reels, SkillSarmaya-style content, or any vertical educational short.
---

> **Always start here.** Confirm the skill is current: `npx hyperframes skills update insta-reel` (no-op when up to date).

You are the thin orchestrator for SkillSarmaya-style Instagram Reels.  
Work inside `videos/<project-slug>/`. Never invent a new visual style — the frozen design system in `references/style-guide.md` + `templates/frame.md` is law.

## Core Pipeline (single Reel)

1. **Setup**  
   - Create project folder.  
   - Copy `templates/account.json` → `account.json` (user may edit).  
   - Copy `templates/frame.md` → `frame.md`.  
   - Write `BRIEF.md` from the user prompt (duration, topic, series flag, caption preference).

2. **Research**  
   - Load deep-research / web-research capability.  
   - Produce `research.md` (facts, stats, sources, angles).  
   - Log what was done + any errors into `logs/research.md`.

3. **Copy**  
   - Apply Hook → Substance → Payoff (`references/hook-substance-payoff.md`).  
   - Run mandatory humanizer pass (short sentences, contractions, zero corporate speak).  
   - Output `copy.md` with spoken lines + on-screen text per scene.  
   - Log into `logs/copy.md`.

4. **Storyboard & Design**  
   - Build scene list from `copy.md` + style guide.  
   - Write `storyboard.md`.  
   - Ensure every scene respects the frozen 9:16 rules and text-adaptation limits in `frame.md`.

5. **Asset Generation**  
   - **Images (required for SkillSarmaya look):** Use the local Flux endpoint. Full prompt formula, file naming, and placement rules are in `references/image-and-motion.md`.  
     ```bash
     curl http://127.0.0.1:31415/v1/images/generations \
       -H "Authorization: Bearer freellmapi-75adf5bd62d4019134ed2d946603d00147fbbbcfd86ff045" \
       -H "Content-Type: application/json" \
       -d '{"model":"@cf/black-forest-labs/flux-1-schnell","prompt":"<detailed cinematic prompt matching style-guide>","width":720,"height":1280}'
     ```
   - Save images as `assets/scene-XX-name.jpg`.  
   - Voice: Kokoro-82 TTS → `audio/vo.wav` + optional SRT.  
   - SFX / VFX / overlays: search HyperFrames registry first (`hyperframes catalog` / registry skill). Prefer existing blocks (film grain, light rays, soft dust).  
   - Log every generation into `logs/assets.md`.

6. **Build Composition**  
   - Follow native HyperFrames flow (read `/hyperframes`, `/hyperframes-core`, `/hyperframes-animation`).  
   - One sub-composition per scene.  
   - Place each generated image as full-bleed background.  
   - Apply **subtle Ken-Burns** (scale 1.00 → 1.04–1.06 over the full scene duration) + optional tiny drift. See exact patterns in `references/image-and-motion.md`.  
   - Use the frozen `frame.md` tokens for colors, logo, and text hierarchy.  
   - Prefer hard cuts or 8–12 frame cross-dissolves.  
   - Preview → fix until clean.

7. **Render & Package**  
   - Final render to MP4 (9:16).  
   - Produce `instagram.md` containing:  
     - Caption (humanized)  
     - Suggested title / first line  
     - Hashtags (from `account.json` + topic)  
     - Cover suggestion  
   - Move video + `instagram.md` to `output/`.

## Series Mode

If the user asks for a series or the brief sets `series: true`:

- Follow `references/series.md` exactly.  
- Create `series/master-research.md`, `series/epXX.md` files, and `series/status.json`.  
- Dispatch the dedicated sub-agent in `sub-agents/series-episode.md` for each episode.  
- Never mix series state into a single-video project.

## Logging Convention

Every major stage writes its own markdown log under `logs/`:

- What was attempted  
- Key decisions  
- Errors encountered + how they were fixed  

This keeps context cheap for later steps and for series continuation.

## Humanizer Rule (non-negotiable)

After any copy is written, run a humanizer pass.  
Reject any line that sounds like a LinkedIn post or ChatGPT. Prefer the voice of a smart, slightly blunt older cousin who actually invests.

## Text Overflow Rule

If a card or reference layout has fewer words than the new copy:

1. Shorten the copy first.  
2. Only then allow minor scale within the ranges defined in `frame.md`.  
3. Never break the visual hierarchy or logo safe zone.

## Final Output

- `output/<slug>.mp4`  
- `output/instagram.md` (caption + title + tags)  
- All intermediate files stay inside the project for debugging and series reuse.

When in doubt, re-read `references/style-guide.md` and `frame.md`. Style consistency > novelty.
