---
name: backtrack
description: A lookup failed or an answer was wrong — work out why, and fix the cause rather than the symptom. Use when the user says "you should have found that", "that's wrong", "why didn't you know", "backtrack", or when you yourself cannot find something you believe should exist. The user may say this in any language. Retraces where you looked, classifies the miss, widens the search once, then proposes one concrete fix to the index or routing that stops it happening again.
autonomy: 1  # proposes the fix; the user approves before anything is changed
---

## What this does

Turns a failed lookup into a structural fix, so the same miss cannot happen twice.

**The method is in `system/procedures/backtrack.md`. Read it and follow it.**

This file exists only so the skill fires on a spoken trigger. The procedure itself lives outside
`.claude/` on purpose: `.claude/skills/` is read by Claude Code and by nothing else, so anything kept
only here would not exist for any other agent. Keeping the method in `system/` is what makes this
behaviour portable — the same reason `onboard` works everywhere.

**Do not restate the procedure here.** Two copies of a method is how one of them goes stale, and the
copy in `system/` is the one `AGENTS.md` points every other agent at.

## Verification

The procedure carries its own verification section. Run it from there — and confirm you actually
opened `system/procedures/backtrack.md` this run rather than working from memory of it.

## What this skill does not do

It proposes one concrete edit and changes nothing until the user says yes.

It does not duplicate, summarise or override `system/procedures/backtrack.md`. If this file and the
procedure ever disagree, the procedure is correct and this file is the defect.
