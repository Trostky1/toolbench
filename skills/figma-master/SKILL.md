---
name: figma-master
description: >-
  Ben's Figma master. Use for ANY Figma, FigJam or Figma Slides work, or a figma.com URL: designing or
  editing screens, components, variables, auto-layout, decks, motion/animation, Code Connect, design to
  code or code to design, and adding icons/images/assets ("plugin" work). Wraps the official Figma MCP
  connector and its figma:* skills, and adds Laws of UX, ui-ux-pro-max taste, plugin87 design-system
  gates, and agent-driven motion and asset recipes. Not for pure web code with no Figma (design-ui /
  build-code).
---

# Figma Master

**First, tell the user: "Using: Figma Master".**

This is a thin layer over Figma's own skills. Do NOT copy or paraphrase them. Load them, then apply
Ben's layer below. Paths are relative to `C:\Users\bentr\.claude\skills\figma-master\`.

## 1. Mandatory order (the connector's rules)
1. `create_session` with the file key before any file tool (the server requires it).
2. Skill `figma:figma-use` BEFORE every `use_figma` call. No exceptions.
3. New file: skill `figma:figma-create-new-file` before `create_new_file`.
4. Never guess node IDs or variable IDs: read them (`get_metadata`, `use_figma` reads).
5. Build in small steps, then `get_screenshot` each section to check. Motion: see section 4.

## 2. Pick the route
| Task | Load (in addition to figma-use) |
|---|---|
| Full screen / page / modal from code or a description | `figma:figma-generate-design` |
| Design system, variables, components, theming | `figma:figma-generate-library` + `kits/plugin87/tokens/` |
| Slides deck | `figma:figma-use-slides` (+ Ben's Nothing/TE deck style, see his memory notes) |
| FigJam / diagram | `figma:figma-use-figjam` or `figma:figma-generate-diagram` |
| Animation | `figma:figma-use-motion` (see `references/assets-and-plugins.md` "Motion") |
| Figma to code | `figma:figma-design-to-code`, `get_design_context`, then `design-ui`/`build-code` |
| Code Connect | `figma:figma-code-connect` |
| Icons, photos, any "plugin" job | `references/assets-and-plugins.md` |
| Choosing style, palette, fonts for a design | `design-ui` -> `kits/ui-ux-pro-max` search tool |

## 3. Ben's layer (apply to every Figma design)
1. **Respect existing work.** Check the file's variables, styles and libraries first (`get_libraries`,
   `search_design_system`). Reuse; never restyle his chosen look (Nothing/TE decks, Rove OS = IBM Plex,
   360x414 frame, bentrost.site) to "improve" it. Propose instead.
2. **Tokens, not hardcodes.** Colors, spacing, radius, type come from variables bound to nodes.
   Primitives -> Semantic -> Component collections; modes for light/dark. Token by intent (a destructive
   action uses the danger token everywhere).
3. **Eight states** for every interactive component: default, hover, focus, active, disabled, loading,
   error, selected. Cover them as variants/properties.
4. **One thing leads.** One focal point per frame; display type >= 2.5x body. No grid of four equal cards.
5. **Laws of UX pass.** After each frame, run the checklist in `references/laws-of-ux.md` (max 3 findings,
   each with a node and a concrete fix). Tap targets, proximity/grouping, Hick's, feedback timing matter most.
6. **Accessibility numbers.** Text contrast 4.5:1 (3:1 large/UI), target >= 44x44 mobile / 24x24 min,
   visible focus, no color-only status. Details: `kits/plugin87/accessibility/`.
7. **Anti-slop.** No emoji as icons, no indigo-purple gradients, no one-sided colored card borders, no
   lorem ipsum, no `#000` on `#fff`, one icon set per screen. Full list: `kits/plugin87/DOCTRINE.md`
   "Non-Negotiables" and `kits/plugin87/taste/`.
8. **Name things.** Layers named by role (`btn/primary`, `icon/search`), frames per screen, sections per flow.
9. **Complete output.** Deliver all N screens asked for; no placeholders.

## 4. Verify before claiming done
- `get_screenshot` every frame; compare against the request. Check text clipping and overflow.
- Run the Laws of UX pass and the contrast/target-size numbers above.
- Motion: `get_screenshot` shows only the resting state; use `export_video` sparingly (slow). If a motion
  API throws "not a supported API", stop and tell Ben (feature flag), never loop.
- Report what was verified and what was not.

## 5. Kits (open only when a row applies)
- `kits/plugin87/DOCTRINE.md`: full design-system doctrine and request router (MIT, plugin87/ux-ui-agent-skills).
- `kits/plugin87/rules/`: tokens-and-color, typography-and-spacing, components, accessibility.
- `kits/plugin87/tokens/`: DTCG token JSON (colors, spacing, type, motion, shadows) to seed Figma variables.
- `kits/plugin87/design-qa.md`, `critique.md`, `ux-writing.md`, `design-critic.md`: review procedures.
- Its runnable gates need a browser + Node and apply to HTML builds, not Figma files.
- `awesome-ios-ui` is only a gallery of iOS interaction patterns for inspiration; not vendored.
