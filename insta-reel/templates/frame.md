# frame.md — SkillSarmaya 9:16 Frozen Design System

> Generated from `references/style-guide.md`. Do not change aspect ratio or logo treatment.

## Canvas
- Width: 720
- Height: 1280
- FPS: 30
- Safe zones: top 80 px (logo), bottom 160 px (captions / CTA), left/right 40 px

## Brand
- Logo asset: `assets/logo-pill.svg` (or PNG fallback)
- Logo position: top-center, y = 36–48 px
- Logo size: 190 × 48 px fixed

## Color Tokens
```json
{
  "bg_deep": "#0B2535",
  "bg_teal": "#0F2F42",
  "highlight": "#FFD600",
  "text_primary": "#FFFFFF",
  "text_secondary": "#E8E8E8",
  "accent_green": "#2ECC71",
  "alert": "#FF5E4D",
  "card_overlay": "rgba(0,0,0,0.62)",
  "data_bg": "#F7F4ED"
}
```

## Typography
- Font family: system sans-serif heavy (Inter Black / Montserrat Black / SF Pro Display Black)
- Hierarchy:
  - punch: 96–112 px
  - headline: 52–68 px
  - body: 30–36 px
  - data-number: 88–108 px
  - caption: 26–30 px
- Yellow highlight treatment: rounded rectangle behind word OR hand-drawn underline stroke

## Text Adaptation Rules
- Prefer shorter copy over shrinking type.
- Max 2 lines for body statements.
- If text still overflows a card → rewrite via humanizer or split into next scene.
- Never let text cover faces or the logo.

## Motion Defaults
- Text entrance: scale 0.85 → 1.0 + fade, 0.35 s, ease-out
- Highlight draw: 0.25 s stroke
- Scene transition: hard cut or 8-frame cross-dissolve
- Background: gentle Ken-Burns (scale 1.0 → 1.04 over scene duration)

## Caption Skin (optional)
Use `.hyperframes/caption-skin.html` when burned-in SRT is requested. Keep white text + subtle dark pill, bottom third, never overlapping logo.
