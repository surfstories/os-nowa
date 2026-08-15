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

## When to run

- The folder has never been set up (`me/profile.md` says **Status: not yet filled in**).
- The user asks for it by name, in any language.
- The user wants to redo a part of it — the procedure is idempotent and can be re-entered at any step.

**Do not run it** in the middle of other work just because `me/` looks thin. Offer; wait for a yes.

## Hard rules

1. **Never write to an engine path.** `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `README.md`, `LICENSE`,
   `.cursor/`, `system/**` and `.claude/**` are the product, not the user's data. Onboarding fills
   `me/`, creates the first domain, and appends to `decisions.md`. Nothing else. If onboarding edits
   the engine, the user's work can never be updated again — this is the rule that protects that.
2. **The user's language, from their first message.** Confirm it in one line and stay in it.
3. **Every choice is a numbered menu.** They answer with a number, never with a paragraph.
4. **Nothing is created without a clear yes.** Say what you are about to write, then write it.
5. **Never ask for a password, key or token.** None is needed.

## Verification

Onboarding is not finished until all four of these are true — check them, do not assume:

1. `me/profile.md` no longer contains the string `<!-- filled by onboarding -->`, and holds a real name.
2. `me/priorities.md` holds **at least three** items the user actually said.
3. **At least one domain folder exists** with both an `index.md` and a `log.md`, and the index has at
   least one row worth choosing from.
4. `decisions.md` holds **at least one** entry.

If any is false, onboarding stopped early. Say so plainly and offer to finish it, rather than
declaring it done.

## What this skill does not do

- **It does not connect anything.** OS_Nowa ships with no integrations. If the user wants a service
  connected, that is their own setup, and it earns a row in `me/connections.md` afterwards.
- **It does not fill the system with example content.** Every artifact it creates comes from the
  user's own answers. An empty domain the user has to delete is worse than no domain.
- **It does not tune the engine to the user.** See hard rule 1.
