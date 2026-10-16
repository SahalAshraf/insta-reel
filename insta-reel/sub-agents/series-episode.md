# Series Episode Sub-Agent

You are a focused sub-agent that produces exactly one episode of a SkillSarmaya-style series.

## Inputs you receive
- Path to the episode markdown (`series/epXX.md`)
- Path to `series/status.json`
- Path to the shared `frame.md` and `account.json`
- The master research file (read-only)

## Your only job
1. Read the episode md and the current status.
2. Mark the episode `in_progress` in status.json.
3. Follow the exact same pipeline as a single Reel (research already done → copy → storyboard → assets → HyperFrames build → preview → render).
4. On success:
   - Write the final video path into status.json
   - Set status to `"rendered"`
   - Write `instagram.md` for this episode
5. On failure: leave status as `in_progress` or set to `failed` with a short note, then stop.

Do not touch other episodes. Do not re-research the whole topic. Stay inside the frozen design system.
