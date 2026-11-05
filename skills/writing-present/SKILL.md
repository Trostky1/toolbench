---
name: writing-present
description: >-
  Ben's writing and presenting bucket. Use when the job is WORDS or a STORY: portfolio case-study copy,
  project write-ups, site text, slide/deck structure and narrative (Figma Slides, HTML or PowerPoint),
  README, docs, decision records, PR descriptions, explaining or teaching a concept, and editing or
  tightening any draft. Not for: how a deck or page LOOKS (design-ui), résumé / cover letter /
  job outreach (career), deciding what a project should be (plan-think).
---

# Writing & Presenting

**First, tell the user: "Using: Writing & Presenting".**

Merged from slides, writing-for-agents, documentation-and-adrs, teach and pr. Tool-heavy pieces kept
under `kits/`: `kits/slides/` (copywriting formulas, layout patterns, deck strategies, HTML template),
`kits/teach/` (multi-session teaching workspace formats). Templates in `references/`
(`pr-template.md`, `adr-template.md`). Output formats: a doc → the `anthropic-skills:docs` skill;
.pptx → `pptx`; PDF → `pdf`; Figma Slides → `figma:figma-use-slides`.

## 1. Ben's voice (default for anything published as him)

- Direct and plain. Short sentences. Concrete nouns, real numbers, named materials and methods.
- **No em dashes.** Use a period, comma or colon.
- No hype or unverifiable claims ("revolutionary", "seamless", health/speed/injury benefits he
  hasn't proven). Survey figures carry their sample size (e.g. n = 9).
- Labels honest: planned work says planned; mock UI says sample values.
- First person for his own work; credit teammates and collaborators by role.
- Never invent a fact, quote, metric, client or result. Missing info → ask or leave a clearly marked gap.

## 2. Writing any piece

1. **Who reads it and what should they do after?** (recruiter skims in 30s, professor grades, user
   installs). Write that down in one line before drafting.
2. **Lead with the point.** Headline/first line says the thing; details follow. Headings name things.
3. **Cut.** Every sentence must change what the reader knows or does. Delete throat-clearing,
   restated ideas and adjectives doing no work. When a sentence fails, delete the whole sentence.
4. **Show, don't claim:** an image, a number, a before/after beats "improved".
5. **Read it as the reader**, then tighten once more. Offer 2-3 options for headlines and taglines.

When editing Ben's draft: keep his voice and structure; fix only what's weak; show what changed and why
in a short list. Don't rewrite into your voice.

## 3. Portfolio case studies (industrial design)

Order that works: **hook image + one-line what-it-is** → problem and who it's for → research and
insight (real findings, sample size) → process (sketches, models, iterations, what failed and why)
→ final design with the key decisions → result / what's next. Images carry the story; text is
captions-length bands, not essays. Each project gets one sentence a recruiter could repeat.
Credit team roles. Keep claims inside what was tested.

## 4. Decks and presentations

- One idea per slide; the slide title states the takeaway, not the topic ("Grip test cut wrist angle",
  not "Testing").
- Story arc: context → problem → insight → solution → proof → ask/next. Alternate "what is" and
  "what could be" to keep tension.
- More image, less text. If a slide needs a paragraph, it's two slides or a speaker note.
- Copy formulas (PAS, AIDA, FAB) and layout patterns: `kits/slides/references/`. HTML decks with
  charts: `kits/slides/references/create.md` and the template there.
- Ben's decks: Figma Slides file and the PDF portfolio (see memory notes); edit those in their own
  style rather than starting fresh.

## 5. Docs, READMEs, decision records, PRs

- README: what it is, who it's for, how to run it (exact commands), one screenshot. Don't restate
  what `package.json` or `--help` already says.
- Comments and docs explain *why*, never restate the *what*.
- Decision record (when a choice would be expensive to reverse): context, decision, alternatives
  considered with why rejected, consequences. Template: `references/adr-template.md`. Match any
  existing ADR convention in the repo first.
- PR body: Summary (smallest diagram/diff/tree that shows the point) → Evidence (before/after,
  screenshots for visual changes) → Merge danger (one-way or two-way door, blast radius).
  Template: `references/pr-template.md`.
- Writing for agents (CLAUDE.md, skills, prompts): front-load the trigger words in descriptions,
  one trigger per case, state the positive target behavior instead of prohibitions, push long
  reference into separate files behind a pointer, delete lines the model already does by default.

## 6. Explaining and teaching

Explain at Ben's level, plain words first, jargon defined on first use, one concrete example. For a
real multi-session learning goal ("teach me X"), use the workspace method in `kits/teach/KIT.md`:
a mission, short single-win lessons, retrieval practice, trusted sources cited.

## 7. Done check

- [ ] Point in the first line; reader and their next action are clear
- [ ] Ben's voice: no em dashes, no hype, no unproven claims, nothing invented
- [ ] Every number/claim traceable to a source or his files
- [ ] Cut pass done; headings name things
- [ ] Right format delivered (doc / pdf / pptx / Figma) and opened to check it renders
