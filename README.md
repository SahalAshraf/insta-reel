# insta-reel — SkillSarmaya-style Instagram Reel Generator

A HyperFrames skill that turns a simple prompt such as

```text
create a 59 sec reel on topic emergency funds vs committee
```

into a complete vertical Reel that matches the visual language, narrative structure, and tone of [SkillSarmaya](https://www.instagram.com/skillsarmaya/).

**Final deliverables**
- 9:16 MP4 (10 s – 5 min)
- Ready-to-post Instagram caption + title + hashtags
- Optional series support (master research → episode files + status tracker)

---

## One-command install (recommended)

```bash
# From any machine that already has HyperFrames / Grok skills support
npx hyperframes skills install https://github.com/<your-username>/insta-reel-skill.git
```

Or manually:

```bash
git clone https://github.com/<your-username>/insta-reel-skill.git
cp -r insta-reel-skill/insta-reel ~/.grok/skills/   # or /home/workdir/.grok/skills/ inside the agent environment
```

After install the skill is available as `/insta-reel` (or just say “create a reel on …”).

---

## What the skill does

1. **Research** the topic (web / deep research)
2. **Structure** the content with the proven Hook → Substance → Payoff framework
3. **Humanize** every line so it never sounds robotic
4. **Generate** cinematic illustrated scenes (local Flux) + Kokoro-82 voice
5. **Build** a native HyperFrames composition scene-by-scene using a frozen 9:16 design system extracted from real SkillSarmaya videos
6. **Preview → fix → render**
7. **Package** video + Instagram caption/tags

### Frozen design system (important)

All visual decisions live in:

- `insta-reel/references/style-guide.md` — full analysis
- `insta-reel/templates/frame.md` — production tokens & rules

The canvas is **always 720×1280**. Logo size, placement, color palette, and text hierarchy ranges are locked. When new copy is longer than a reference card, the skill shortens the copy first (humanizer) rather than breaking the layout.

### Series support

```text
create a 5-episode series on “building wealth in Pakistan”, 45–60 s each
```

The skill will:

- Research once → `series/master-research.md`
- Split into `series/ep01.md` … `ep05.md`
- Track progress in `series/status.json` (`pending` / `rendered`)
- Use a dedicated sub-agent so single-video and series production never get mixed

You can render one episode per day or all at once; the tracker remembers the last finished episode.

---

## Required local services

| Service | Purpose | Endpoint / Command |
|---------|---------|--------------------|
| Flux (Black Forest Labs) | Image generation | `http://127.0.0.1:31415/v1/images/generations` |
| Kokoro-82 | Voice / TTS | Local Kokoro installation |
| HyperFrames | Composition & render | Already available in the agent environment |

Update the Bearer token inside the skill if your Flux key changes.

---

## Project layout after a run

```
videos/my-reel-slug/
├── BRIEF.md
├── account.json          ← edit once, reused
├── frame.md              ← frozen design system
├── research.md
├── copy.md
├── storyboard.md
├── logs/                 ← per-stage markdown logs
├── series/               ← only when series mode
│   ├── master-research.md
│   ├── ep01.md …
│   └── status.json
└── output/
    ├── my-reel-slug.mp4
    └── instagram.md
```

---

## Customising for your own account

Edit `templates/account.json` (or the copy inside a project):

```json
{
  "handle": "@yourhandle",
  "display_name": "Your Brand",
  "bio": "...",
  "niche": "...",
  "default_hashtags": ["#tag1", "#tag2"]
}
```

The skill reads this file on every run for captions, tags, and brand tokens.

---

## Style analysis source

The visual system was reverse-engineered from three real SkillSarmaya Reels (uploaded by the skill author). Sample frames are kept under `docs/style-analysis/` for reference. Key observed traits:

- Cinematic AI-illustrated scenes with warm window light
- Pill logo top-center
- Yellow highlight bars / hand-drawn underlines on key words
- Strong Hook → data/insight → clear Payoff structure
- Calm intimate voice + English on-screen text

---

## License & credits

Skill structure follows the HyperFrames / agentskills conventions.  
Visual style analysis is derived from public SkillSarmaya content for the purpose of consistent educational content creation.

---

## Quick start after install

```text
/insta-reel create a 45 second reel on why emergency funds beat committees
```

or

```text
create a 4-episode series on compounding for beginners, ~50s each
```

The skill will guide you through the rest.
