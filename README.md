# Toolbench

Eight consolidated Claude Code skills, built to replace ~120 overlapping ones. Each "bucket" tells you which
one is active ("Using: <bucket>") and keeps tool-heavy material nested under `kits/` so it only loads when needed.

| Skill | Use it for |
|---|---|
| `design-ui` | How something looks and feels: pages, layout, type, color, motion, brand, design systems |
| `figma-master` | Design master: any Figma / FigJam / Slides work plus design craft everywhere: Awwwards references, visual direction (oil-ui, modern-frontend), motion (Emil Kowalski canon, motion-principles audits, Figma Motion), brand identity, stageshow product demos, dimensional spec drawings, reviews. Adds Laws of UX and plugin87 gates on top of the official Figma skills |
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

## Optional MCP
`figma-master` uses the Awwwards MCP for visual references. Add it once:

```bash
claude mcp add awwwards -- npx -y awwwards-mcp@1.18.0
```

On Windows use `cmd /c npx -y awwwards-mcp@1.18.0` as the command. `kits/brand-identity` needs Python with `pip install -r skills/figma-master/kits/brand-identity/requirements.txt`.
