---
name: os-health
description: Check whether this workspace is still healthy — broken pointers, files nothing points at, domains missing their index or log, an always-loaded tier that has grown too big, facts stated twice with different values. Use when the user says "os health", "check my system", "is anything broken", "tidy up", or after a big batch of new material. The user may say this in any language. READ-ONLY by default — it reports, and never changes a file without a specific yes.
autonomy: 1  # reports only; every fix is shown as a diff and applied one at a time on confirmation
---

## What this does

Checks whether the workspace is still healthy and reports what has drifted.

**The method is in `system/procedures/os-health.md`. Read it and follow it.**

This file exists only so the skill fires on a spoken trigger. The procedure itself lives outside
`.claude/` on purpose: `.claude/skills/` is read by Claude Code and by nothing else, so anything kept
only here would not exist for any other agent. Keeping the method in `system/` is what makes this
behaviour portable — the same reason `onboard` works everywhere.

**Do not restate the procedure here.** Two copies of a method is how one of them goes stale, and the
copy in `system/` is the one `AGENTS.md` points every other agent at.

## Verification

The procedure carries its own verification section. Run it from there — and confirm you actually
opened `system/procedures/os-health.md` this run rather than working from memory of it.

## What this skill does not do

It never changes a file without a specific yes, and it never deletes — anything removed goes to `_trash/`.

It does not duplicate, summarise or override `system/procedures/os-health.md`. If this file and the
procedure ever disagree, the procedure is correct and this file is the defect.
