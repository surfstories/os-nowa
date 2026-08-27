---
name: onboard
description: Set up OS_Nowa for the first time. Use when the folder is new, when me/profile.md still says "Status: not yet filled in", or when the user says "onboard me", "set me up", "get me started". The user may say this in any language — detect it from their first message and run the whole thing in that language. A warm, non-technical interview that fills in who the user is, builds their first real domain from their own answers, and teaches the system as it goes. Idempotent — safe to re-run.
autonomy: 1  # asks before every change; the user is the verifier
---

## What this does

Runs the first-run setup: a short, warm interview that ends with a workspace holding the user's own
material rather than an empty skeleton.

**The whole script is in `system/procedures/onboarding.md`.** Read it and follow it step by step.
This file exists so the skill can be triggered by name; the procedure is the content, and it lives
outside `.claude/` so that agents other than Claude Code can run the same flow.

**Do not restate the procedure here.** Two copies of a method is how one of them goes stale, and the
copy in `system/` is the one `AGENTS.md` points every other agent at.

## When to run

- The folder has never been set up (`me/profile.md` says **Status: not yet filled in**).
- The user asks for it by name, in any language.
- The user wants to redo a part of it — the procedure is idempotent and can be re-entered at any step.

**Do not run it** in the middle of other work just because `me/` looks thin. Offer; wait for a yes.

## Verification

The procedure carries its own verification section, at Step 7. Run it from there, and confirm you
actually opened `system/procedures/onboarding.md` this run rather than working from memory of it.

If any of its checks is false, onboarding stopped early. Say so plainly and offer to finish it,
rather than declaring it done.

## What this skill does not do

- **It does not connect anything.** OS_Nowa ships with no integrations. If the user wants a service
  connected, that is their own setup, and it earns a row in `me/connections.md` afterwards.
- **It does not fill the system with example content.** Every artifact it creates comes from the
  user's own answers. An empty domain the user has to delete is worse than no domain.
- **It does not tune the engine to the user.** See hard rule 4 of the procedure.

It does not duplicate, summarise or override `system/procedures/onboarding.md`. If this file and the
procedure ever disagree, the procedure is correct and this file is the defect.
