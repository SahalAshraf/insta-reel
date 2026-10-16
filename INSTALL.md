# Install instructions

## Option A — One command (when published)

```bash
npx hyperframes skills install https://github.com/<USER>/insta-reel-skill.git
```

## Option B — Manual

```bash
git clone https://github.com/<USER>/insta-reel-skill.git
# Inside the Grok / HyperFrames agent environment:
cp -r insta-reel-skill/insta-reel /home/workdir/.grok/skills/
# or on a normal laptop that uses ~/.grok/skills:
cp -r insta-reel-skill/insta-reel ~/.grok/skills/
```

Restart the agent session or run:

```bash
npx hyperframes skills update
```

The skill is now available. Trigger it with any of:

- `/insta-reel …`
- “create a reel on …”
- “make a 59s SkillSarmaya-style reel about …”
- “start a series on …”

## First-time setup

1. Edit `/home/workdir/.grok/skills/insta-reel/templates/account.json` with your real handle, bio, hashtags.
2. Make sure the local Flux server is running on port 31415 and Kokoro-82 is available.
3. (Optional) Replace `assets/logo-pill.svg` with your own logo if you are not using the SkillSarmaya visual identity.
