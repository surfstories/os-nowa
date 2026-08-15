---
name: level-up
description: The weekly upgrade ritual — find one thing the user did by hand three or more times, and turn it into one thing they never have to do again. Use when the user says "level up", "what should I automate", "find me some leverage", or when you have noticed them repeat the same manual task. The user may say this in any language. One run produces exactly one artifact and one entry in decisions.md. Interviews first; never invents work that is not really there.
autonomy: 2  # drafts the artifact; the user approves before it is saved
---

## What this does

Finds one thing done by hand three or more times and turns it into one thing never done again.

**The method is in `system/procedures/level-up.md`. Read it and follow it.**

This file exists only so the skill fires on a spoken trigger. The procedure itself lives outside
`.claude/` on purpose: `.claude/skills/` is read by Claude Code and by nothing else, so anything kept
only here would not exist for any other agent. Keeping the method in `system/` is what makes this
behaviour portable — the same reason `onboard` works everywhere.

**Do not restate the procedure here.** Two copies of a method is how one of them goes stale, and the
copy in `system/` is the one `AGENTS.md` points every other agent at.

## Verification

The procedure carries its own verification section. Run it from there — and confirm you actually
opened `system/procedures/level-up.md` this run rather than working from memory of it.

## What this skill does not do

One run produces exactly one artifact. An exit at a scoping gate is a success, not a failed run.

It does not duplicate, summarise or override `system/procedures/level-up.md`. If this file and the
procedure ever disagree, the procedure is correct and this file is the defect.
