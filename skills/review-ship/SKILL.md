---
name: review-ship
description: >-
  Ben's review-and-ship bucket. Use when the question is "is this GOOD / READY?": review my code, PR
  or last commit, audit the repo, check before I post/deploy/send the link, pre-launch checklist,
  security check, performance or Lighthouse score, responding to review feedback, and before claiming
  any work is done. Not for: fixing a known bug (debug), building (build-code), visual redesign
  (design-ui), reviewing writing or a résumé (writing-present / career).
---

# Review & Ship

**First, tell the user: "Using: Review & Ship".**

Merged from code-review, code-review-and-quality, ponytail-review, ponytail-audit,
security-and-hardening, shipping-and-launch, verification-before-completion,
requesting-code-review, receiving-code-review and performance-optimization.
Long material in `references/`: `hardening-patterns.md` (security fixes), `optimization-patterns.md`
(perf fixes), `code-reviewer.md` (prompt for a fresh-context reviewer subagent).

## 0. Evidence before claims (applies to every bucket)

Never say done, fixed, passing or ready without running the proving command in this turn and reading
its output: build exit 0, test count, the page actually rendered, the deploy URL actually loading.
No "should work", "looks right", "probably". An agent's or tool's "success" report is checked
against the real diff or page. Partial checks prove nothing.

## 1. Reviewing a change (or "review this")

**Scope:** what Ben names; otherwise uncommitted changes, else the last commit.
**Understand first:** read the diff, then the code it touches: callers of every changed function,
what it calls, tests, README. Find the expected load (one person's portfolio vs many users) and say
which you assumed. When a signature or behavior changes, grep every caller.

**Look for, in this order:**
1. **Bug:** wrong result, crash, missed edge case (empty, zero, last item, time zones), broken caller.
2. **Risk:** security hole, data loss, secrets in code.
3. **Scale:** fine for one user, wrong for many (races, per-item queries, lists that only grow).
4. **Missing test:** risky new logic with nothing that fails when it breaks (one good test, not coverage).
5. **Speed:** real slowdowns are problems; micro-wins are suggestions.
6. **Lean:** dead code, reuse an existing helper (name the path), stdlib instead of a dependency,
   one-implementation abstractions, near-copies to merge, a function doing unrelated jobs to split.
7. **Spec:** does it do what was asked; anything added that wasn't (scope creep)?
8. For UI changes: was it looked at? Screenshots at 390 and 1440 or it's unverified.

**Check before reporting:** every finding needs a concrete case ("this input → this wrong result").
Re-read the lines to confirm. A `shortcut:` comment naming its limit is a decision, not a finding.
Propose the smallest fix; prefer fixes that delete code. No style taste, no vague worries.
Zero findings is a valid result.

**Output (plain English, reader may never have seen the code):**
- `What this change does:` 2-3 sentences.
- Findings numbered across groups so Ben can say "fix 2 and 5":
  **Must fix** (bug, security, data loss) / **Should fix** (untested risk, real slowness, duplication)
  / **Nice to have**. Each: **title** (`file:line`), what this is, problem, fix, if we skip it.
- End: `Verdict: Ship.` or `Verdict: fix 1 and 3 first.`, `Lean: -N lines possible.` if any,
  `Not checked:` one line.

**Whole-repo audit:** same lenses, map entry points and main flows first, go deep where mistakes
cost most, max 20 findings, say what you didn't read. Changes nothing.

**Fresh eyes:** for big or risky changes, dispatch a reviewer subagent with
`references/code-reviewer.md` (crafted context, not session history).

## 2. Receiving feedback (from Ben, a teammate, or a tool)

Read all of it, restate unclear items and ask before implementing any (items can be linked).
Check each suggestion against the actual code: correct here? breaks something? is the feature even
used (grep; unused → suggest removing instead)? Push back with technical reasons when it's wrong.
Implement blocking issues first, then simple, then complex, testing each. No performative
agreement; just state the fix.

## 3. Security (anything with input, auth, secrets, forms, APIs, uploads)

- Secrets only in env vars; never in code, commits, logs or client bundles. `.env*` gitignored.
  A secret that reached a remote is compromised: rotate first, then purge.
- Validate external input at the boundary with a schema; never trust client-side validation.
- Parameterize queries; no user input into SQL, shell, `eval`, or `innerHTML`.
- Auth checked per request AND authorization per resource.
- Cookies `httpOnly`, `secure`, `sameSite`; security headers (CSP, HSTS); CORS to explicit origins.
- Generic error messages to users; details only in server logs.
- Contact forms / third-party embeds: rate-limit, spam-protect, don't leak emails.
- LLM output is untrusted input. Dependencies: run the package manager's audit before release; never
  `audit fix --force` blindly. Patterns: `references/hardening-patterns.md`.

## 4. Performance (measure first)

Baseline → find the actual bottleneck → fix one thing → re-measure the same way → keep only if it
beats the noise, else revert. Targets: LCP ≤2.5s, INP ≤200ms, CLS ≤0.1.
Portfolio/site usual suspects: oversized images (use AVIF/WebP, `srcset`, width/height set,
`loading="lazy"` below the fold, `fetchpriority="high"` on the hero), unoptimized video, too many
font files, render-blocking scripts. Patterns: `references/optimization-patterns.md`.

## 5. Before shipping (deploy, publish, send the link)

- [ ] Builds clean; tests (if any) pass; no `console.log`/debug leftovers or TODOs that matter
- [ ] Looked at in a real browser at 390 / 768 / 1440; no console errors; every link and form works
- [ ] Accessibility: keyboard reachable, visible focus, contrast 4.5:1, alt text, labeled inputs
- [ ] Images/video optimized; Lighthouse performance roughly ≥90 or the gap explained
- [ ] Meta: title, description, OG image, favicon; 404 page; HTTPS
- [ ] No secrets in the repo or bundle; env vars set in the host (Vercel) not just locally
- [ ] Know how to roll back (previous deploy / git revert) before deploying
- [ ] After deploy: open the live URL, click the critical path, check the console

Bigger launches with real users: feature flag, staged rollout, monitoring, written rollback plan
(see the archived shipping-and-launch notes if needed).

## 6. Honesty

Don't rubber-stamp. Don't soften real bugs. Quantify when you can. If Ben has context and disagrees,
defer. Report outcomes faithfully, including what failed and what wasn't checked.
