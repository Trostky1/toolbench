---
name: plan-think
description: >-
  Ben's thinking and planning bucket. Use BEFORE building, when the WHAT or HOW is still open: a fuzzy
  idea, "help me figure out / think through X", choosing between directions, "grill me / stress-test
  this / are we sure?", scoping a project, writing a spec or plan for a multi-step job (Rove OS
  features, a new site, a deck structure), or breaking big work into steps. Not for: executing an
  agreed plan (build-code / design-ui), job-search strategy (career), wording a finished piece
  (writing-present). Clear one-line requests skip this entirely.
---

# Plan & Think

**First, tell the user: "Using: Plan & Think".**

Merged from brainstorming, idea-refine, interview-me, grilling/grill-me, writing-plans,
planning-and-task-breakdown, spec-driven-development and doubt-driven-development. Ideation lenses
and rubric in `references/` (`frameworks.md`, `refinement-criteria.md`, `examples.md`).
<!-- Stance choice: brainstorming/spec skills gate ALL work behind a written, approved doc. Kept that
only for real projects; small asks get a one-line restate and go. Matches ponytail "match effort". -->

## 0. Size it first

What do I actually know about what Ben wants, and why?
- **Everything that matters is in the request** → don't run this skill's process. Do it, say what you did.
- **One thing is open** → ask that one question, with your best guess attached, then go.
- **Real project or fuzzy idea** → the modes below.

Before asking anything, look: read the files, Figma, memory notes and earlier conversation Ben
pointed at. Never ask what the project already answers or reopen what he already decided.
Offer an exit: "Or if you'd rather I just dive in, say so."

## 1. Pick the mode

| Ben's situation | Mode |
|---|---|
| Asks for X but who/why/success is missing | **Interview** (2) |
| Has a raw idea, wants it shaped or wants options | **Ideate** (3) |
| Has a plan/decision, says "grill me", "are we sure?" | **Grill** (4) |
| Knows what he wants; it's multi-step | **Spec + plan** (5) |
| A risky decision is about to stand (irreversible, unfamiliar, high stakes) | **Doubt** (6) |

## 2. Interview: find what he actually wants

- Write a one-sentence hypothesis + honest confidence %, and (if <70%) what's missing.
- Ask **one question at a time, with your guess attached**: `Q: ... / GUESS: ... because ...`.
  Reacting to a wrong guess is faster than answering from scratch. Occasionally guess in a direction
  you expect him to push back on.
- Watch for "should want" answers ("scalable", "clean", "the way most people do it"). Ask:
  *"If you didn't have to justify this to anyone, what would you actually want?"*
- Stop when you can predict his reaction to your next three questions. Then restate:
  Outcome / Who it's for / Why now / Success looks like / Constraint / **Out of scope**.
- Need an explicit yes. "Whatever you think" or "sounds good" is not yes: offer two concrete options.
- On yes: deliver the restate, offer next steps, and stop the turn.

## 3. Ideate: open up, then narrow

1. Restate as "How might we..." Ask only what you must (who, success, constraints, tried before, why now).
2. Generate **5-8 variations** with lenses: inversion, remove a constraint, different audience,
   combine with an adjacent idea, 10x simpler, 10x bigger, expert's obvious move. Ground them in
   Ben's real work and files. Quality over quantity.
3. After he reacts: cluster into 2-3 directions; stress-test each on value (painkiller or vitamin?),
   feasibility (hardest part?), difference (why would anyone care/switch?).
4. Name hidden assumptions, what could kill it, what you're choosing to ignore.
5. Be honest, not supportive. Push back on weak ideas, with kindness.
6. Output a one-pager: Problem / Recommended direction / Assumptions to test / MVP scope /
   **Not doing (and why)** / Open questions. Save only if he says so.

## 4. Grill: walk the decision tree

Map the plan as a tree of decisions. Each round, ask every question whose prerequisites are settled
(the frontier), numbered, each with your recommended answer, worded so "yes" accepts it:

```
❓ Q1 - <title>: <question, options if any>
➡️ <recommended answer>
```
Look up facts yourself (files, tools); only decisions go to Ben. Recompute the frontier after each
round. Done when no branch is left silently assumed. Don't act until he confirms shared understanding.

## 5. Spec + plan (multi-step work)

**Approaches first:** in their own message, 2-3 real ways to build it, each with its trade-off,
your recommendation and why. Ben picks. (One sensible way? Say so and why the others don't fit.)

**Spec** (short for small work, fuller for projects): objective and who it's for; success criteria
that are testable ("LCP < 2.5s", not "faster"); constraints and stack; boundaries (always / ask first /
never); assumptions listed out loud; open questions. Several independent capabilities bundled
together → propose a small capability map (module / responsibility / depends on / build order) first.
After writing a spec: summarize, ask for approval, **stop the turn**.

**Plan:** vertical slices (each one works end to end), riskiest first, dependency order.
Per task: what it does, acceptance criteria (≤3 bullets), how to verify, files touched, size.
XL tasks (8+ files, "and" in the title) get split. Checkpoint every 2-3 tasks.
Never overwrite an existing plan that still has unchecked tasks; ask.
For long multi-session work, the `planning-with-files` skill keeps task_plan.md/progress.md on disk.

## 6. Doubt: cross-examine a risky decision

Write the claim in 2-3 lines and why it matters. Extract only the artifact + the contract it must
satisfy (strip your reasoning, keep contradicting evidence). Hand that to a fresh-context subagent with
an adversarial prompt: "Find what is wrong. Assume the author is overconfident. Do not validate."
Never pass your claim. Classify each finding: contract unclear / valid → change it / valid trade-off →
document / noise. Max 3 cycles, then escalate to Ben.

## 7. Style

Plain language, one question at a time, specific to his project (build on his last answer). Show,
don't tell: a quick text sketch, or a mockup when the look is his to decide. A throwaway spike is
fine when it's the fastest way to learn; label it throwaway. Your own calls go in as proposals with
a reason, never as things he agreed to.
