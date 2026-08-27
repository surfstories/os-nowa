# level up — the method

This is the agent-neutral method. **Claude Code** runs it via the `level-up` skill; **any other
agent** runs it by reading this file, which `AGENTS.md` points at. The content is the same
either way — only the trigger differs.


## What this does

One run = **one shipped thing.** Find a piece of friction, scope it properly, build the smallest
thing that removes it. Run it every week or two and the system compounds — each pass, it knows one
more trick that fits how *this person* works.

The discipline is in the scoping. Most "automate this" ideas should not be automated, and the four
gates below are how that gets discovered before the work happens rather than after.

## Step 1 — Find the friction

Ask conversationally, one question at a time. Stop as soon as one to three real candidates surface:

1. *"Walk me through your week. What did you do three or more times?"*
2. *"What felt manual, boring, or like copy-paste?"*
3. *"What could someone else do if you wrote the steps down once?"*
4. *"If your workload doubled tomorrow, what would break first?"*

Present the candidates as a numbered menu, one line each on why it is worth doing. Ask them to pick
one.

**If nothing real surfaced, say so and stop.** Do not invent work. A ritual that manufactures a task
every time it runs teaches the user to stop running it.

## Step 2 — Scope it: four gates, in order

**Gate 1 — Eliminate, then delegate, then automate.** In that order, and the order is the point.
*"What happens if you simply stop doing this?"* If the honest answer is "nothing" — that is the best
possible outcome. Log it in `decisions.md` and finish, cheerfully. Never automate waste. If it is
judgment-heavy or different every time, a person should do it: log that and finish.

**Gate 2 — Can they describe it?** Five things, all required: what starts it · where the information
comes from · what changes · where it branches · where the output goes. If the user cannot name all
five, the answer is *"if you can't explain it to a person, you can't explain it to an automation —
sketch it and come back."* Stop there.

**Gate 3 — Pick the lowest autonomy that solves it.** The three levels are in
`system/conventions.md`, under "The autonomy scale".

Push back on level 3 for anything new. Autonomy is earned over real runs, not granted at design time.

**Gate 4 — Name the number it moves.** Time per week, mistakes avoided, how fast something gets
answered. One concrete number. If they cannot name one: *"if it doesn't move a number, why build
it?"* Stop.

## Step 3 — Build the simplest form

In this order. The user has to explicitly ask for anything further down:

1. **A saved prompt** they paste when needed. Zero moving parts, and it is the right answer more
   often than it sounds.
2. **A written procedure** in the relevant domain, that any agent can follow.
3. **A skill**, if and only if it needs to fire on a spoken trigger — via `create-skill`, and note
   its Claude Code limit to the user before building it.

Everything that is not a skill lives in the domain it belongs to, or in `projects/<name>/`. Never
loose in the root.

**Whatever gets built starts supervised.** Run it once, by hand, together, and look at the output
before trusting it.

## Verification

Every run ends with all three, or it is not finished:

1. **One entry in `decisions.md`** — the scoped spec, or the eliminate/delegate result. The exits at
   Gate 1 and Gate 2 are real outcomes and get logged the same way.
2. **One artifact**, in the right place — unless the run exited at a gate, which is a success.
3. **A three-line close**: what was scoped, what was built, and the reminder that it starts
   supervised.

## What this procedure does not do

- **It does not build more than one thing per run.** Two half-built automations are worth less than
  one that works.
- **It does not push past a gate.** An exit at Gate 1 is the most valuable result this procedure
  produces, not a failed run.
- **It does not run itself.** There is no schedule anywhere in OS_Nowa. Someone has to ask.
