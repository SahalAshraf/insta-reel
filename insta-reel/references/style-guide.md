# SkillSarmaya Visual & Narrative Style Guide (Frozen 9:16)

Derived from frame-by-frame analysis of three official SkillSarmaya Reels (31s, 21s, 33s).  
**Canvas is always 720×1280 (9:16). Never change aspect ratio.**

## 1. Brand Lockup

- Logo: Pill-shaped capsule, white fill, thin green border, green dot + “SkillSarmaya” in clean sans-serif.
- Placement: Always top-center, ~40–48 px from top edge, never overlapping primary text.
- Size: Fixed ~180–200 px wide. Do not scale per scene.
- End card: Same logo centered, soft fade-in, optional short CTA line below.

## 2. Color System (strict)

| Role                  | Hex / Value          | Usage |
|-----------------------|----------------------|-------|
| Deep Teal / Navy base | `#0B2535` – `#0F2F42`| Primary backgrounds, room walls |
| Warm Amber light      | `#E8A84A` – `#F5C26B`| Window light, lamps, skin highlights |
| Highlight Yellow      | `#FFD600` / `#FFE14D`| Key-word highlights, underline strokes, CTA bars |
| Pure White            | `#FFFFFF`            | Primary body & headline text |
| Soft Coral / Alert    | `#FF5E4D`            | Negative emphasis (“FAULT”, declining lines) |
| Soft Green accent     | `#2ECC71` / `#1ABC9C`| Positive growth, “wealthy”, emergency fund |
| Dark card overlay     | `rgba(0,0,0,0.55–0.72)` | Semi-transparent list cards, comparison panels |
| Cream / Off-white grid| `#F7F4ED`            | Clean data scenes (numbers, calculations) |

Never introduce pure black or neon. Keep lighting warm and cinematic.

## 3. Typography Hierarchy (variable by intent)

All text is **sans-serif**, heavy weight for impact, clean geometric feel (think Inter / SF Pro / Montserrat Black).

- **Emotional Punch Word** (1–2 words): 92–120 px, white or outlined, sometimes with yellow hand-drawn underline or red accent.
- **Main Headline**: 48–72 px, bold, white. Yellow highlight bars or rounded yellow rectangles behind 1–3 critical words.
- **Supporting Statement** (bottom third): 28–36 px, white, selective yellow word highlights. Max 2 lines preferred.
- **Data / Number scenes**: Huge numbers 80–110 px, clean, centered. Labels 22–28 px.
- **List / Comparison cards**: 24–32 px inside dark cards.
- **Logo text**: Fixed small size inside the pill.

**Adaptation rule (critical):**  
If injected text is longer than the reference card’s word count, do **not** shrink the entire design. Instead:
1. Prefer shorter, punchier copy (humanizer pass).
2. Allow max 2 lines for body, 1 line for headlines.
3. Scale font only within the allowed range above; never go below minimum readability.
4. If still overflow → move secondary info to a later scene or drop it.

## 4. Scene Types Observed

1. **Cinematic Illustrated Story** (majority)
   - Full-frame AI-illustrated environments (bedroom at night, kitchen, shop shelves, home office).
   - Realistic-but-stylized people, strong window light, depth of field, atmospheric haze.
   - Character usually on left or lower third; text on right or bottom.

2. **Clean Data / Calculation**
   - Light cream grid or soft gradient background.
   - Huge centered numbers, simple equations, progress bars or month counters.
   - Minimal illustration.

3. **Comparison / List Cards**
   - Semi-transparent dark rounded cards over the illustrated scene.
   - Two-column or stacked “List One vs List Two”, “Then / Now”.

4. **Object Close-up + Insight**
   - Hands interacting with cash box, notebook, phone statement, etc.
   - Strong product-style lighting.

## 5. Motion & Transition Language

- Cuts are mostly hard or very short cross-dissolves (8–12 frames).
- Text appears with scale-up + fade or slide-up from bottom.
- Yellow highlight bars / underlines draw on with a quick stroke animation.
- Charts and numbers count-up or draw in.
- Subtle parallax or slow Ken-Burns on illustrated backgrounds (very gentle).
- No flashy 3D transitions, no glitch, no heavy particle systems.
- Background effects: soft light rays, subtle dust/film grain, occasional floating particles in light beams.

## 6. Narrative Structure (Hook → Substance → Payoff)

Every Reel follows this emotional arc:

1. **Hook (0–4 s)**  
   Personal, slightly painful or relatable regret.  
   Example patterns: “Remember that night you had to call someone…”, “Open your statement…”

2. **Substance (middle)**  
   Story → data → insight. Show the problem with numbers or visual contrast.  
   Use “List One vs List Two”, month-by-month charts, before/after.

3. **Payoff / CTA (last 4–6 s)**  
   Clear, actionable lesson.  
   “Build the emergency fund first.” / “Grow the second list.”  
   Soft, non-salesy close.

Voice tone: Calm, intimate, slightly urgent. Mix of conversational Hindi/Urdu + English technical terms. English on-screen text is primary for reach.

## 7. Caption / Overlay Rules

- Burned-in text is the primary communication layer (voice supports it).
- Optional SRT captions only when user requests them; style them as clean white text with black outline or subtle background pill, bottom-safe zone.
- Never cover the logo or the main character’s face with text.

## 8. Forbidden / Avoid

- Changing aspect ratio or logo position/size.
- Introducing new brand colors outside the table.
- Overly long paragraphs of text.
- Generic stock-photo look or pure abstract motion graphics.
- Loud SFX or music that fights the voice.
- Robotically formal language (run humanizer).

---

This file is the single source of truth for visual style.  
`frame.md` is generated from this guide + the active `account.json` tokens.
