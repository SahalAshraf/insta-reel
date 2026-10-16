# Real Images + Subtle Motion (Proper Local Workflow)

This is the correct way to get SkillSarmaya-quality visuals.  
**Cloud HyperFrames compose cannot reach your local Flux server.** Always run image generation + composition locally.

## 1. Generate Cinematic Stills (Local Flux)

Use the exact endpoint defined in the skill:

```bash
curl http://127.0.0.1:31415/v1/images/generations \
  -H "Authorization: Bearer freellmapi-75adf5bd62d4019134ed2d946603d00147fbbbcfd86ff045" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "@cf/black-forest-labs/flux-1-schnell",
    "prompt": "<detailed prompt>",
    "width": 720,
    "height": 1280
  }'
```

### Prompt formula (match style-guide)

```
Cinematic illustrated scene, [specific environment], warm window light, deep teal and navy tones, soft atmospheric haze, depth of field, realistic-but-stylized, SkillSarmaya aesthetic, vertical 9:16 composition, high detail, no text, no logo
```

Examples:
- “Young man sitting on bed at night looking at phone, city lights through window, deep teal room, warm amber side light, cinematic, emotional, vertical”
- “Close-up of hands opening metal cash box filled with notes, warm home lighting, wooden shelf, SkillSarmaya style illustration”

Save every generated image into the project’s `assets/` or `public/` folder with clear names:
`scene-01-hook.jpg`, `scene-02-toxic.jpg`, etc.

Log every generation in `logs/assets.md`.

## 2. Place Images in Scenes

In each scene sub-composition (or the main composition):

```html
<div class="scene clip" data-start="..." data-duration="...">
  <img 
    src="assets/scene-01-hook.jpg" 
    class="bg-image clip"
    data-start="0" 
    data-duration="..." 
    style="position:absolute; inset:0; width:100%; height:100%; object-fit:cover;"
  />
  <!-- text layers on top -->
</div>
```

Always keep the logo on a higher track so it stays above the image.

## 3. Apply Subtle Motion (Ken-Burns + Parallax)

Never leave a still image completely static. Use gentle movement:

### Recommended GSAP / HyperFrames keyframe pattern

```js
// Gentle Ken-Burns (scale only – keep it subtle)
tl.fromTo(".bg-image", 
  { scale: 1.0 }, 
  { scale: 1.05, duration: sceneDuration, ease: "none" }, 
  sceneStart
);

// Optional tiny vertical drift
tl.fromTo(".bg-image", 
  { y: 0 }, 
  { y: -12, duration: sceneDuration, ease: "none" }, 
  sceneStart
);
```

Rules for realism:
- Scale range: **1.00 → 1.04 to 1.06** maximum
- Duration = full scene length
- Ease: `"none"` or very soft power
- Never aggressive zooms or fast pans
- Optional: very light film grain or soft light-ray overlay from the HyperFrames registry

## 4. Transitions Between Image Scenes

Preferred (matches original SkillSarmaya videos):
- Hard cut
- or 8–12 frame cross-dissolve

```js
// Simple cross-dissolve
tl.to("#scene-1", { opacity: 0, duration: 0.3 }, nextSceneStart - 0.3);
tl.fromTo("#scene-2", { opacity: 0 }, { opacity: 1, duration: 0.3 }, nextSceneStart - 0.3);
```

Avoid: fancy 3D flips, glitch, heavy particles, whip pans.

## 5. Extra Atmosphere (optional but powerful)

Search the HyperFrames registry first:

```bash
npx hyperframes catalog --search "film grain"
npx hyperframes catalog --search "light rays"
npx hyperframes catalog --search "dust"
```

Add a very low-opacity grain or light-ray layer on top of the image for cinematic feel. Keep opacity ≤ 15–20%.

## 6. Checklist before render

- [ ] Every scene has a generated image (or intentional clean data background)
- [ ] Image is 9:16 (or cropped correctly)
- [ ] Subtle Ken-Burns applied
- [ ] Logo never covered
- [ ] Text hierarchy and yellow highlights follow `frame.md`
- [ ] Color grading matches deep teal + warm amber + pure yellow
- [ ] No text overflow

This workflow produces the “real” SkillSarmaya look: illustrated stills + restrained motion + strong typography.
