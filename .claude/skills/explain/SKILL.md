---
name: explain
description: Explain how OS_Nowa itself works — what the three tiers are and why, what a domain is, where a new thing should go, why the always-loaded files must stay small, what a skill is. Use when the user asks "how does this work", "why is it set up like this", "where should this go", "what is a domain", "what are the tiers", or seems unsure what the system is doing. The user may say this in any language. Teaches from system/tiers.md and system/conventions.md; read-only.
autonomy: 3  # reads and explains; changes nothing
---

## What this does

Explains how OS_Nowa itself works, from the written material rather than from memory.

**The method is in `system/procedures/explain.md`. Read it and follow it.**

This file exists only so the skill fires on a spoken trigger. The procedure itself lives outside
`.claude/` on purpose: `.claude/skills/` is read by Claude Code and by nothing else, so anything kept
only here would not exist for any other agent. Keeping the method in `system/` is what makes this
behaviour portable — the same reason `onboard` works everywhere.

**Do not restate the procedure here.** Two copies of a method is how one of them goes stale, and the
copy in `system/` is the one `AGENTS.md` points every other agent at.

## Verification

The procedure carries its own verification section. Run it from there — and confirm you actually
opened `system/procedures/explain.md` this run rather than working from memory of it.

## What this skill does not do

Read-only. It never changes a file, and it says so when the material does not cover the question.

It does not duplicate, summarise or override `system/procedures/explain.md`. If this file and the
procedure ever disagree, the procedure is correct and this file is the defect.
