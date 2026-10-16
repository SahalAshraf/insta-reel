# Series Production Workflow

When the user requests a multi-episode series (or the prompt implies connected episodes):

## 1. Master Research

- Run full topic research once.
- Save everything into `series/master-research.md`.
- Decide total episodes and approximate length per episode from the brief.

## 2. Episode Split

- Create `series/ep01.md`, `series/ep02.md`, … each containing:
  - Episode title
  - Specific Hook → Substance → Payoff for that episode
  - Key facts unique to this episode
  - Continuity notes (what the previous episode established)
  - Suggested visuals

## 3. Tracker JSON

Create / update `series/status.json`:

```json
{
  "series_title": "...",
  "total_episodes": 5,
  "created_at": "ISO",
  "episodes": [
    {
      "id": "ep01",
      "file": "ep01.md",
      "title": "...",
      "status": "pending",   // pending | in_progress | rendered | published
      "rendered_at": null,
      "video_path": null
    }
  ]
}
```

## 4. Production Loop

- Always read `series/status.json` first.
- Find the lowest-id episode with `status: "pending"`.
- Dispatch the **series-episode sub-agent** (see `sub-agents/series-episode.md`) with that episode’s md file.
- After successful render, mark the episode `"rendered"` and write the video path.
- User can request “next episode”, “render all remaining”, or a specific episode id.

## 5. Continuity Rules

- Each episode must stand alone (someone can start mid-series).
- Still carry forward key phrases, visual motifs, or “previously…” soft callbacks when helpful.
- Keep the same design system (`frame.md`) and voice across the entire series.
