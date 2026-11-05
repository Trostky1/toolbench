# Laws of UX: applied in Figma

Source: lawsofux.com (Jon Yablonski), the same 30 laws as Ben's DES 2500 poster (Iowa State, Subinay Malhotra).
Each row says what to DO in a Figma file, so the law becomes a check, not a quote.

## Perception (Gestalt): layout and grouping
| Law | In Figma |
|---|---|
| Law of Proximity | Group related things with tighter spacing than unrelated things. Use auto-layout gaps from a token scale (4/8/16/24); label-to-field gap < field-to-field gap. |
| Law of Common Region | Put related items in a shared container (card, fill, hairline border). Prefer a surface change over a heavy border. |
| Law of Similarity | Same role = same style: one component/variant per role. Different role = visibly different. |
| Law of Uniform Connectedness | Connect related items with a line, shared background or stepper track (timelines, step indicators). |
| Law of Prägnanz | Choose the simplest readable form: fewer shapes, fewer effects, flat icons at one stroke weight. |
| Von Restorff Effect | Exactly one thing per screen is visually different (the primary action or key metric). If everything pops, nothing does. |
| Selective Attention | Users filter to their goal. Keep decoration away from the task area; put banners where they will not be read as ads. |

## Cognition: how much to show
| Law | In Figma |
|---|---|
| Hick's Law | Fewer, clearer choices per screen. Progressive disclosure; one primary action. Menus > ~7 get grouped or searched. |
| Miller's Law / Working Memory | Chunk. Do not rely on "7 +/- 2" as a hard cap; do not make users remember across screens. Show prior input where it is needed. |
| Chunking | Break phone numbers, codes, long forms and lists into labelled groups. |
| Cognitive Load | Remove everything that does not help the task: extra borders, colors, copy. One idea per screen/slide. |
| Choice Overload | Default the best option, recommend one plan, limit filters. |
| Serial Position Effect | Put the most important items first and last in nav, tab bars, lists. |
| Paradox of the Active User | Nobody reads instructions. Design affordances and in-context hints, not help pages. |
| Mental Model | Match what users already believe the system does. Use familiar icons and labels. |
| Jakob's Law | Use platform and common conventions (iOS tab bar at bottom, logo top-left). Be novel only where it earns it. |
| Cognitive Bias | Note anchoring, framing, default effects when you pick defaults or pricing layouts. |

## Behaviour and motion: how it feels
| Law | In Figma |
|---|---|
| Fitts's Law | Targets are big and close to where the pointer/thumb already is. Min 44x44pt (iOS) / 48dp (Android) / 24x24 CSS px (WCAG 2.5.8). Primary actions in thumb zone on mobile. |
| Doherty Threshold | Feedback within 400 ms. Motion durations 100-300 ms for UI feedback; show a skeleton/progress for anything slower. |
| Flow | Avoid interruptions in a task: no surprise modals, keep steps continuous. |
| Goal-Gradient Effect | Show progress toward a goal (step 3 of 4, filled bar), start progress bars partly filled. |
| Zeigarnik Effect | Show unfinished state (draft, 70% profile) to pull users back; do not nag. |
| Peak-End Rule | Polish the emotional peak and the final screen (success, confirmation, empty-to-done). Keep the ending kind. |
| Aesthetic-Usability Effect | Polish raises perceived usability, but does not fix real usability problems. Do both. |

## Principles for the designer
| Law | In Figma |
|---|---|
| Occam's Razor | Of two designs that work equally, ship the one with fewer elements. |
| Pareto Principle | Design the 20% of features used 80% of the time first and make them prominent. |
| Parkinson's Law | Shorten flows (autofill, defaults) so the task takes less time, not as long as the form. |
| Tesler's Law | Some complexity cannot be removed; decide who carries it (system, not user). |
| Postel's Law | Accept messy input (spaces, formats), output clean consistent results. |

## How to use this in review
1. After building a frame, scan the four tables once and list at most 3 laws the frame violates.
2. Say which law, which node, and the fix (a concrete value: "tap target 36 -> 44").
3. Never cite a law as decoration. If it does not change a decision, leave it out.
