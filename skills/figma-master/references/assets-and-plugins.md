# Assets and "plugin" work through the Figma MCP

Claude cannot open or click community plugins (they have their own UI in the Figma app).
`use_figma` runs Plugin API JavaScript inside the file, so anything a plugin does through
the Plugin API can be done directly. Use the right-hand column; only fall back to asking
Ben to run the plugin himself where noted.

| Plugin people use | Do this instead (agent-driven) |
|---|---|
| Iconify / Lucide / Phosphor / Material Symbols | Fetch the SVG (`https://api.iconify.design/<set>/<name>.svg?color=%23hex&width=24`), then `figma.createNodeFromSvg(svg)` in `use_figma`; rename the node `icon/<name>`; bind fill/stroke to a variable. Never emoji as icons. |
| Unsplash / Pexels | Download the image URL (respect the licence; Unsplash needs attribution), then `upload_assets` or `figma.createImageAsync(url)` and apply as an IMAGE fill. Or ask Ben to run the plugin when the choice is subjective. |
| Figmotion / Jitter / Motion plugins | Use Figma's built-in Motion: `figma-use-motion` + `figma-implement-motion`. See "Motion" below. |
| Content Reel / Lorem | Write real copy. No lorem ipsum in a deliverable. |
| Stark / contrast plugins | Compute WCAG contrast yourself from the resolved variable colors (4.5:1 text, 3:1 large text/UI). |
| Tokens Studio / Variables Import | `use_figma` variables API; map tokens in `kits/plugin87/tokens/*.json` (DTCG) to Primitives -> Semantic -> Component collections with modes. |
| Autoflow / arrows | Draw connectors with `figma.createConnector()`; for flows use `generate_diagram` (FigJam). |
| Remove BG / image AI | MCP `generate_image` or Canva-side tools. Not a Figma plugin call. |
| Shader / generative plugins | MCP shader and generative-plugin tools (`create_shader`, `create_generative_plugin`). |
| Any plugin with no API route | Tell Ben which plugin and what to click; continue once the result is in the file. |

## Where assets come from (order of preference)
1. Ben's own files: `C:\PortolfioCareerAssests\` (keyboard-icons, Video & Motion, Projects). Use `upload_assets`.
2. The file's connected libraries: `get_libraries`, then `search_design_system`. Import components, do not redraw them.
3. Open icon sets via Iconify (consistent stroke/weight per screen: pick one set).
4. Open-licence photos (Unsplash/Pexels) with attribution kept in the layer name or notes.
5. Generated images (`generate_image`): last resort; label them as generated.

## Motion (built-in Figma Motion, driven by the agent)
- Load `figma-use` AND `figma-use-motion` (pass both in `skillNames`). `figma-implement-motion` is the code-side version.
- API: `node.applyManualKeyframeTrack`, `applyAnimationStyle`, `setTimelineDuration`, `figma.motion.figmaAnimationStyles()`.
- Gated by a feature flag. If any motion call throws `is not a supported API`, STOP and tell Ben motion is not enabled on his account. Do not retry.
- `get_screenshot` shows the resting frame only. To check motion use `export_video` and sample a few frames, small and low quality first; it is slow.
- Durations: UI feedback 100-300 ms, larger transitions 300-500 ms, nothing blocking over 400 ms (Doherty). Ease-out on enter, ease-in on exit. Respect reduced-motion in anything that ships to code.
- Custom animation styles cannot be authored through the API; say so rather than faking one.

### Verified on Ben's account (2026-11-05)
Motion is ENABLED. Working call shapes (tested on a scratch file):
- Field is an OBJECT, not a string: `node.applyManualKeyframeTrack({ type: 'PROPERTY', name: 'TRANSLATION_X' }, { keyframes: [...] })`.
- `SCALE_XY` needs VECTOR values: `{ type: 'VECTOR', value: { x: 1.4, y: 1.4 } }`; `TRANSLATION_X`/`SCALE_X` use FLOAT.
- Omit `baseValue` on new tracks. Easing e.g. `{ type: 'EASE_OUT' }`, `{ type: 'EASE_IN_AND_OUT' }`.
- Do not animate a top-level frame; animate its children. Default timeline is 2 s; extend with `setTimelineDuration`.
- First-party animation styles available: text_stagger, position, scale, rotation, size, opacity, path.
