# os health — the method

This is the agent-neutral method. **Claude Code** runs it via the `os-health` skill; **any other
agent** runs it by reading this file, which `AGENTS.md` points at. The content is the same
either way — only the trigger differs.


## What this does

Reads the whole workspace and reports what has decayed, mapped to the four failure modes in
`system/conventions.md`: **stale facts, bloat, confusion, contradiction.**

It then offers a fix list. It applies nothing until the user approves each item.

## Hard rules

1. **Read-only by default.** The report is the deliverable. Fixes are a separate, opt-in step.
2. **One fix at a time, each shown as a before/after** before it is applied. Not a batch.
3. **Never delete. Move to `_trash/<YYYY-MM-DD>/`.** The install leaves a local git history, but the
   user is not committing to it — so for anything written since setup there is no `git checkout` to
   fall back on. Treat every delete as final. This is a deliberate difference from lint tools that
   live in an actively-committed repository.
4. **Re-derive every number with a command this run.** A count copied out of an `index.md` is a
   defect you introduced while looking for defects.
5. **Be honest, not generous.** "0 findings" is only believable on a small, new workspace.
6. **Report the way `me/profile.md` asked to be spoken to.** Hard rule 8 in `AGENTS.md` owns this
   rule; it is repeated here because this procedure is the one most likely to break it. Concretely:
   say what is wrong in their words and why it matters to *them*, put the file path in brackets at
   the end of the line or leave it out, and never use the failure-mode names, stale facts and bloat
   and confusion and contradiction, as headings for someone who has not been taught them. They are
   your categories for thinking, not their vocabulary. Onboarding respects this instruction and a
   report that ignores it reads as a different, colder product.

## Steps

**Step 1 — Find the domains.** Every top-level folder that is not `system/`, `.claude/`, `.cursor/`,
`me/`, `projects/` or `_trash/` is a domain. Also list any folder that is *pointed at* by an index or
by `AGENTS.md` but has **no** `index.md` or `log.md` — those are findings, not folders to skip. A
scan that silently excludes the least-catalogued folders will always report the workspace as clean.

**Step 1b - the check you cannot run yourself.** Tier 1 fails silently and cannot be tested from
disk, so this procedure cannot verify the single most important thing about the workspace: whether
the always-loaded files are reaching the agent at all. Ask the user to open one fresh session and
ask it whether there is a diagnostic token in the instructions it was given, and to quote it. **Do
not name the token when you tell them what to ask.** A prompt containing it is answered by itself
and the check passes either way; you know the token, so this is the mistake to avoid. Report what
came back, or report it as unverified with the reason. Check 4 below measures whether Tier 1 is too
big; nothing in this procedure measures whether it arrives. The reasoning is in `system/tiers.md`.

**Your own session is not that check, even when it looks like one.** You may say what you observe
about this session, and it is worth saying. You may not present it as the result, and you may not
tell the user their check is optional or not urgent because of it. You are the one party who cannot
run this: the token is in your context either way, and from the inside you cannot tell whether it
arrived by autoload or because something read the file earlier this run. An agent that certifies its
own always-loaded context has tested nothing and reported a pass.

**Step 2 — Run the checks.**

| # | Check | How | Mode |
|---|---|---|---|
| 1 | Spine | Every domain has `index.md` **and** `log.md` | Confusion |
| 2 | Index vs disk | Files in `pages/` and `sources/` with no index row; index rows pointing at no file | Confusion |
| 3 | Pointers | Every path mentioned in `AGENTS.md` and every `index.md` resolves to something real | Confusion |
| 4 | Tier 1 size | `wc -l me/profile.md me/priorities.md me/connections.md`, against the budget in `system/tiers.md`. Size only, never delivery: see Step 1b | Bloat |
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
5. Step 1b was either run by the user in a fresh session, or reported as unverified. A report that
   is silent about Tier 1 delivery reads as though it checked, and a report that answers Step 1b
   out of this session's own context has not run it at all.

## What this procedure does not do

- **It does not fix anything on its own.** Not even the obvious ones. The value of a lint the user
  trusts is that it never surprises them.
- **It does not judge content.** Whether a decision was wise is not its business; whether the file
  says two different things is.
- **It does not run on a schedule.** Nothing here does. It runs when asked — so it is worth asking,
  every few weeks and after any big batch of new material.
