---
name: os-health
description: Check whether this workspace is still healthy — broken pointers, files nothing points at, domains missing their index or log, an always-loaded tier that has grown too big, facts stated twice with different values. Use when the user says "os health", "check my system", "is anything broken", "tidy up", or after a big batch of new material. The user may say this in any language. READ-ONLY by default — it reports, and never changes a file without a specific yes.
autonomy: 1  # reports only; every fix is shown as a diff and applied one at a time on confirmation
---

## What this does

Reads the whole workspace and reports what has decayed, mapped to the four failure modes in
`system/conventions.md`: **stale facts, bloat, confusion, contradiction.**

It then offers a fix list. It applies nothing until the user approves each item.

## Hard rules

1. **Read-only by default.** The report is the deliverable. Fixes are a separate, opt-in step.
2. **One fix at a time, each shown as a before/after** before it is applied. Not a batch.
3. **Never delete. Move to `_trash/<YYYY-MM-DD>/`.** This workspace is not under version control by
   default, so a delete is final and there is no undo. This is a deliberate difference from lint
   tools that live in a git repository, where `git checkout` is always available. Here it is not.
4. **Re-derive every number with a command this run.** A count copied out of an `index.md` is a
   defect you introduced while looking for defects.
5. **Be honest, not generous.** "0 findings" is only believable on a small, new workspace.
6. **Read `me/profile.md` first and report the way that person asked to be spoken to.** It is already
   in your context and it usually says something like "plain English, no jargon" — and this skill is
   the one most likely to ignore it. Say what is wrong in their words and why it matters to *them*;
   put the file path in brackets at the end of the line, or leave it out. Never open with one.
   Never use `file.md:30` as the subject of a sentence, and never use the failure-mode names —
   stale facts, bloat, confusion, contradiction — as headings to someone who has not been taught
   them; they are your categories for thinking, not their vocabulary. Onboarding respects this
   instruction and a report that ignores it reads as a different, colder product.

## Steps

**Step 1 — Find the domains.** Every top-level folder that is not `system/`, `.claude/`, `.cursor/`,
`me/`, `projects/` or `_trash/` is a domain. Also list any folder that is *pointed at* by an index or
by `AGENTS.md` but has **no** `index.md` or `log.md` — those are findings, not folders to skip. A
scan that silently excludes the least-catalogued folders will always report the workspace as clean.

**Step 2 — Run the checks.**

| # | Check | How | Mode |
|---|---|---|---|
| 1 | Spine | Every domain has `index.md` **and** `log.md` | Confusion |
| 2 | Index vs disk | Files in `pages/` and `sources/` with no index row; index rows pointing at no file | Confusion |
| 3 | Pointers | Every path mentioned in `AGENTS.md` and every `index.md` resolves to something real | Confusion |
| 4 | Tier 1 budget | `wc -l me/profile.md me/priorities.md me/connections.md` — over ~150 total is a finding | Bloat |
| 5 | Row quality | Share of index rows a reader could choose from without opening the file. Read them; do not count dashes | Confusion |
| 6 | Duplication | The same fact stated in two places with no pointer between them | Bloat |
| 7 | Contradiction | The same fact with two different values. Say which file should win and why | Contradiction |
| 8 | Stale | Pages whose `updated:` is far behind the material they describe; `status: draft` presented in an index as though settled | Stale facts |
| 9 | Log format | Headings match `## [YYYY-MM-DD] <op> | <title>`, op is one of the five, **dates ascend** | Confusion |
| 10 | Hygiene | `.DS_Store`, `v2` sitting next to `v3`, stray temp files | Bloat |

**Step 3 — Rank by leverage.** A broken pointer or a contradiction on something the user acts on
ranks far above a lone orphan page. Report in that order, not check order.

**Step 4 — Report in chat**, most important first, each finding with the concrete fix underneath it.
Then ask, as a numbered menu, which fixes to apply — if any.

Write each finding as **one plain sentence naming the consequence to them**, then the fix. *"Your
task list is empty, but you told me the bakery is still waiting on their figures"* — not *"Confusion:
`tasks.md` has 0 open items."* Group by what it means to them, not by failure mode. Hard rule 6
governs this step above everything else in it.

**Step 5 — Apply only what was approved**, one at a time, showing each change. Then append one line
to the affected domain's `log.md`: `## [<date>] fix | os-health: <n> found / <m> fixed`.

**That last line records what was *fixed*, not what was *found*, and the ordering matters.** A ledger
line written at report time says the same thing whether the fixes happened or not, and three weeks
later nobody can tell. Report, then approve, then fix, then log — never log first.

## Verification

1. Every count in the report was produced by a command in this run, and the command can be quoted.
2. The log line, if one was written, names fixes that were actually applied — and was written after
   they were applied.
3. Nothing was deleted. Anything removed is sitting in `_trash/<date>/` and the report says so.
4. Anything that could not be checked is listed as unverified, with the reason. An explicit "I could
   not check this" is a useful answer; a silent omission is not.

## What this skill does not do

- **It does not fix anything on its own.** Not even the obvious ones. The value of a lint the user
  trusts is that it never surprises them.
- **It does not judge content.** Whether a decision was wise is not its business; whether the file
  says two different things is.
- **It does not run on a schedule.** Nothing here does. It runs when asked — so it is worth asking,
  every few weeks and after any big batch of new material.
