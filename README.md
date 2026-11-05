# Toolbench

Eight consolidated Claude Code skills, built to replace ~120 overlapping ones. Each "bucket" tells you which
one is active ("Using: <bucket>") and keeps tool-heavy material nested under `kits/` so it only loads when needed.

| Skill | Use it for |
|---|---|
| `design-ui` | How something looks and feels: pages, layout, type, color, motion, brand, design systems |
| `figma-master` | Any Figma / FigJam / Slides work. Wraps the official Figma MCP skills, adds Laws of UX, ui-ux-pro-max taste, design-system gates, agent-driven motion and asset recipes |
| `build-code` | Making or changing working code |
| `debug` | Something broken or wrong |
| `review-ship` | Is it good / ready: reviews, audits, pre-launch checks |
| `plan-think` | Before building: scoping, specs, stress-testing ideas |
| `writing-present` | Case studies, decks, docs, editing |
| `career` | Résumé, applications, outreach, interview prep |

## Install
Copy the folders in `skills/` into `~/.claude/skills/` (Windows: `C:\Users\<you>\.claude\skills\`).
`figma-master` expects the official Figma plugin/MCP for its `figma:*` skills.

## Notes
- Built for Ben Trost's workflow; the design-ui and figma-master skills reference his portfolio style, adjust section 0 / 3 for yours.
- Third-party material is vendored under `kits/` with its own licence. See `NOTICE.md`.
