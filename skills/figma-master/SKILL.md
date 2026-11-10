---
name: figma-master
description: >-
  Ben's design master. Use for ANY Figma, FigJam or Figma Slides work or a figma.com URL, AND for design
  craft anywhere: choosing a visual direction, design references/inspiration (Awwwards), animation and
  motion (web, React Native, Figma Motion), gestures, Apple-style polish, brand identity (logo, type,
  palette), faux product UI and demo animations, dimensional/spec drawings of products or components,
  premium/cinematic landing pages, and design reviews. Wraps the official Figma MCP skills and adds Laws of
  UX, plugin87 gates, Emil Kowalski's craft canon, oil-ui direction work, modern-frontend directions,
  stageshow, dimensional-drawing and brand-identity kits. Not for: pure logic/backend (build-code),
  broken behaviour (debug).
---

# Figma Master

**First, tell the user: "Using: Figma Master".**

One skill, one pipeline. Pick the stage(s) the request needs, open only the kits named there.
Paths are relative to `C:\Users\bentr\.claude\skills\figma-master\`. Kit entry files are `KIT.md`.

## 0. Ben's context (always)
- Ben is an industrial designer (Iowa State). Respect his existing work: bentrost.site palette + IBM Plex
  Sans, Figma decks, Rove OS (IBM Plex, 360x414). Never restyle a look he chose; propose instead.
- Facts about his projects come from his files (`C:\PortolfioCareerAssests\orchid-site\work\*.html`,
  `about.html`); never invent results, clients or availability.

## 1. The pipeline
| Stage | Use when | Open |
|---|---|---|
| **A. Reference** | Need real examples before deciding | Awwwards MCP (section 3) · `references/laws-of-ux.md` |
| **B. Direction** | "Make it look premium / pick a style / show me options" | `kits/oil-ui/KIT.md` (explore + compare page) · `kits/modern-frontend/KIT.md` (6 directions for web pages) · `design-ui` -> ui-ux-pro-max for palettes/fonts |
| **C. Build in Figma** | Screens, components, variables, decks | Figma skills (section 2) + Ben's layer (section 4) |
| **C. Build in code** | A page/component that ships | `design-ui` (taste kit) / `build-code`, with B's direction and D's motion rules |
| **D. Motion** | Anything moves | section 5 |
| **E. Brand** | Logo, type, palette, guidelines kit | `kits/brand-identity/KIT.md` (measured identity sets; Python deps installed). Voice/guideline wording: `design-ui` brand kit |
| **F. Present** | Show a product or UI | `kits/stageshow/KIT.md` (faux product UI, cursor demos, bento) · `kits/dimensional-drawing/dimensional-drawing/KIT.md` (Apple-style spec/anatomy sheet of a component or physical product) + `.../dimensional-drawing-motion/KIT.md` (10 s film of it) |
| **G. Review** | "Is this good?", before shipping | `kits/emil/review-animations`, `kits/emil/break-ui` (worst-case data), `kits/motion-principles` audit mode, Laws of UX pass, `kits/plugin87/design-qa.md` + `critique.md`, `kits/oil-ui/references/reviewer-manual.md` |

Typical full run: A -> B (recommend one direction, or a comparison page if asked) -> C -> D -> G.
For an ID portfolio or product page, add F: a dimensional drawing and a stageshow-style hero beat
generic renders on a grid.

## 2. Figma (the connector's rules, unchanged)
1. `create_session` with the file key before any file tool.
2. Skill `figma:figma-use` BEFORE every `use_figma` call; `figma:figma-generate-design` for visible
   screens; `figma:figma-generate-library` for components/variables; `figma:figma-create-new-file`
   before `create_new_file`; `figma:figma-use-slides` / `-figjam` / `-motion` as relevant.
3. Never guess node or variable IDs. Build in retry-safe batches, screenshot after composition.
4. Images: `.webp` uploads place but render BLANK. Convert to jpg/png first (Pillow:
   `C:\Users\bentr\AppData\Local\Programs\Python\Python312\python.exe`, Windows-style paths), then
   `upload_assets` with `nodeIds` and POST raw bytes.
5. Assets and "plugin" jobs (icons, photos): `references/assets-and-plugins.md`.

## 3. Awwwards MCP (reference loop)
Server `awwwards` (npx awwwards-mcp, user scope; restart Claude to load it). Tools include
`search_sites` (by tag/colour/tech/award), `get_site_details` (palette, stack, elements),
`compare_sites`, `create_design_brief` (2-5 sites -> cited brief), `search_elements` (hero, footer,
pricing...), `capture_live_site`, `analyze_page_structure`, `record_site_motion`. Use it in stage A:
pull 3-5 relevant sites, look at the screenshots, then state what you are taking from each.
Behance blocks the browser pane; Awwwards + its screenshots are the visual source instead.
If the tools are not loaded, say so and continue with the written kits.

## 4. Ben's layer (every design, Figma or code)
1. Tokens, not hardcodes: colour/spacing/radius/type bound to variables; token by intent.
2. Eight states for interactive components (default, hover, focus, active, disabled, loading, error,
   selected).
3. One thing leads per screen; display type >= 2.5x body; no grid of identical cards as the main idea.
4. Laws of UX pass after each frame (`references/laws-of-ux.md`, max 3 findings, node + concrete fix).
5. Accessibility numbers: text 4.5:1 (3:1 large), targets >= 44x44 mobile / 24x24 min, visible focus.
6. Anti-slop: no emoji icons, no indigo-purple gradients, no one-sided coloured borders, no lorem
   ipsum, one icon set per screen. Fuller list: `kits/plugin87/DOCTRINE.md`,
   `kits/modern-frontend/references/forbidden.md`, `kits/motion-principles/references/anti-checklist.md`.
7. Name layers by role; deliver all N screens; no placeholders in a deliverable.

## 5. Motion (one canon, several kits)
Decide in Emil's order: should it animate -> purpose -> property -> easing/duration -> interruption -> exit.
| Need | Open |
|---|---|
| Philosophy and polish bar | `kits/emil/emil-design-eng/KIT.md` (read first for any motion) |
| Build one animation (web) | `kits/emil/animate/` (+ `RECIPES.md`) |
| Several elements together | `kits/emil/choreograph/` |
| Drag, swipe, sheets | `kits/emil/gestures/` · Apple feel: `kits/emil/apple-design/` |
| React Native / Expo (e.g. Rove OS) | `kits/emil/animate-expo/` |
| Name a vague effect | `kits/emil/animation-vocabulary/` |
| Performance / dropped frames | `kits/emil/animation-performance/` + `kits/emil/performance-cheatsheet.md` |
| Find / remove / improve motion | `kits/emil/find-animation-opportunities/`, `remove-animations/`, `improve-animations/` |
| Audit with an HTML report | `kits/motion-principles/KIT.md` (audit workflow; Emil + Krehel + Tompkins lenses) |
| Figma timeline animation | `figma:figma-use-motion` + `references/assets-and-plugins.md` "Motion" (verified call shapes) |
| Scroll-driven cinematic pages | `kits/modern-frontend/cinematic-scroll/KIT.md` |
Defaults: UI feedback 100-300 ms, ease-out on enter, never animate keyboard-driven or high-frequency
actions, respect reduced motion.

## 6. Other kit tools
- `kits/emil/prototype/` (several live versions behind a picker; only when Ben asks to compare builds),
  `kits/emil/pick-ui-library/` (only when asked), `kits/emil/mobile-native/` (web app that should feel
  installed on a phone).
- `kits/oil-ui/` is written in Chinese; read it as-is. Its `scripts/build_explorer.py` builds the
  multi-style comparison page.
- `kits/stageshow/` and `kits/dimensional-drawing/` include runnable HTML/JS templates and node
  scripts; read each KIT.md before running anything.

## 7. Verify before claiming done
- Figma: screenshot each frame; check clipping/overflow; Laws of UX + contrast/target numbers.
- Code: open it at desktop and mobile widths and screenshot; run `break-ui` on data-driven UI.
- Motion: Figma `get_screenshot` shows only the resting frame (use `export_video` sparingly); in code,
  record or step through it.
- Say what was verified and what was not.

## 8. Kit sources (licences in each folder; see Toolbench NOTICE.md)
plugin87/ux-ui-agent-skills · emilkowalski/skills · kylezantos/design-motion-principles ·
oil-oil/oil-ui · alvinindra/modern-frontend-skills · benjitaylor/skills (stageshow) ·
enesozturk/dimensional-drawing · fatihaydost/brand-identity-skill · INSANE0777/Awwwards-mcp (MCP only).
