---
name: design-ui
description: >-
  Ben's design and UI bucket. Use when the request is about how something LOOKS or FEELS: designing,
  redesigning, restyling or polishing a web page, portfolio page, landing page or app screen; layout,
  typography, color, spacing, motion, icons; design systems and tokens; brand identity; banners, social
  images, logos; Figma screens; or "this looks generic / AI-made / off". Not for: making it work in code
  (build-code), broken behavior (debug), pre-launch checks (review-ship), deck or case-study wording
  (writing-present), résumé/job material (career).
---

# Design & UI

**First, tell the user: "Using: Design & UI".**

Merged from taste-skill, ui-ux-pro-max, design, design-system, ui-styling, brand, banner-design and
frontend-ui-engineering. The tool-heavy originals live intact under `kits/` (paths below are relative
to this folder: `C:\Users\bentr\.claude\skills\design-ui\`). Open a kit only when its row applies.

## 0. Ben's context

Ben is a designer. Respect existing work over defaults: his portfolio (bentrost.site), his Figma
decks (Nothing / Teenage Engineering style), Rove OS (IBM Plex, 360x414 frame). Before proposing a
direction, check the project's existing tokens, fonts and Figma file. Never overwrite a style he chose
to "improve" it; propose instead.

## 1. Pick the route

| Request | Route |
|---|---|
| Build or redesign a whole website / landing page | `kits/taste/KIT.md` full run (its `<skill>` = `kits/taste`) (Node 22 + Edge/Chrome checker). Read its House rules first. |
| Choose style, palette, fonts, UX rules for a page or app | `kits/ui-ux-pro-max` search tool (section 3) |
| Tokens, CSS variables, component states | `kits/design-system/` references + `scripts/generate-tokens.cjs`, `validate-tokens.cjs` |
| shadcn/ui or Tailwind implementation | `kits/ui-styling/references/` |
| Brand voice, guidelines, palette management | `kits/brand/references/` |
| Banner, cover, social image, ad | Section 5 here; sizes in `kits/banner-design/references/banner-sizes-and-styles.md` |
| Logo, icon set, CIP mockups (needs GEMINI_API_KEY) | `kits/design/KIT.md` |
| Figma file work (screens, components, motion, plugins/assets) | Load the `figma-master` skill; it routes to the figma:* skills and adds Laws of UX |
| A small fix (spacing, one component, a color) | Rules in section 2 only. Don't run a kit. |

Match the effort to the ask: a tweak gets a tweak, not a design system.

## 2. Core rules (always)

**Hierarchy and system**
- One system per page: one button pair, one card style, one radius scale, one link look, one heading scale.
- Spacing on a scale (4/8px steps or the project's own); no off-scale values like 13px or 2.3rem.
- Semantic tokens (`--color-primary`, `--bg-surface`), never raw hex inside components. Three layers:
  primitive → semantic → component.
- Heading levels in order; h1 once. Body ≥16px, line-height ~1.5, ≤2 typefaces.
- Equal left/right content edges; nothing hanging off one side; no horizontal scroll.

**Avoid the AI look** (taste + frontend-ui-engineering agree)
- No default violet/indigo, no gradient soup, no rounded-2xl on everything, no shadow stacks,
  no stock three-card grid, no lorem ipsum, no generic hero with a mood image.
- Real content and real assets: the actual product/work, real photographs, real logos and icons
  (never a drawn look-alike of a real logo). For a portfolio, the work IS the hero.
- No captions under images explaining or apologizing for them; credits in one footer line.
- Plain copy: headings name things, buttons are verb + object, one main action per screen.

**Accessibility (non-negotiable)**
- Contrast 4.5:1 text, 3:1 large text/UI. Never color alone to convey state.
- Every interactive element is a real `<button>`/`<a>`, keyboard reachable, visible focus ring.
- Labels on inputs; `aria-label` on icon-only buttons; alt text on meaningful images.
- Touch targets ≥44x44px with ≥8px between.
- `prefers-reduced-motion` respected; nothing hidden that only motion reveals.

**Motion**
- Quiet micro-interactions: link cards lift ~2px, photos zoom 1.02-1.03 in frame, buttons step on
  hover and press on click. 150-300ms, exit faster than enter. Animate transform/opacity only.
- No scroll-triggered fades, parallax, tilt, carousels or auto-rotating tabs by default.
  Big shader/WebGL moments only on tech/gaming subjects, and only when asked.

**Layout and responsive**
- Mobile-first. Check 390, 768, 1024, 1440. Splits stack text-first; one column at 390.
- Each section reads as one idea; the first screen says what it is plus one concrete fact.

**States** (UI components): loading (skeletons, not spinners, for content), empty, error with a way
out, success, disabled. Never a blank screen.

## 3. ui-ux-pro-max search tool

```bash
python "C:\Users\bentr\.claude\skills\design-ui\kits\ui-ux-pro-max\scripts\search.py" "<2-5 terms>" --design-system -p "Name"
python "...\search.py" "<terms>" --domain <product|style|color|typography|ux|landing|icons|gsap|chart>
python "...\search.py" "<terms>" --stack <html-tailwind|react|nextjs|astro|svelte|...>
```
- One intent per query. Retry once narrower if off-topic; if still nothing, say the advice is a
  fallback, not a database match. Never present a 0-result search as data.
- Optional dials on `--design-system`: `--variance`, `--motion`, `--density` (1-10).
- Persist with `--persist --output-dir <project root>`; never `--force` over an existing MASTER.md
  without Ben's OK.
- Full rule text: `kits/ui-ux-pro-max/references/quick-reference.md`; app pre-delivery checklist:
  `references/pro-rules.md`.

## 4. Process for anything bigger than a tweak

1. **Brief**: what it is, who it's for, the one main action, real material available (work, photos,
   logo, copy). Ask for what's missing instead of inventing it.
2. **Direction**: look at 2-3 references (Ben's own past work first). Write a short design contract:
   the screen's job, primary action, states, responsive rules, patterns to reject. Show options when
   the direction is open; don't pick by taste alone.
3. **Copy first**, then layout as screens/sections, then build with the project's tokens.
4. **Look at it**: render in a browser at 390/768/1024/1440, screenshot, compare against the
   checklist. Never call a visual done without seeing it.

## 5. Banners and social images

Exact platform size (IG post 1080x1080, story 1080x1920, LinkedIn 1584x396 / post 1200x627,
X header 1500x500, YT thumb 1280x720, site hero 1920x600-1080). Critical content in the central
70-80%. One CTA, ≤2 fonts, headline ≥32px, ads text <20%. Print: 300 DPI, CMYK, 3-5mm bleed.
Build in HTML/CSS, export PNG at exact pixels, offer 2-3 art directions side by side.

## 6. Done checklist

- [ ] Reads as made for this person/brand, not a template; nothing violet-by-default
- [ ] One system (buttons, cards, radii, type scale); spacing on scale; tokens not hex
- [ ] Contrast, focus, labels, 44px targets, reduced motion
- [ ] Rendered and screenshotted at 390 / 768 / 1024 / 1440; no overflow, nothing cut
- [ ] Loading/empty/error states where data is involved
- [ ] Ben's existing style respected; changes to it proposed, not imposed
