---
name: backtrack
description: A lookup failed or an answer was wrong — work out why, and fix the cause rather than the symptom. Use when the user says "you should have found that", "that's wrong", "why didn't you know", "backtrack", or when you yourself cannot find something you believe should exist. The user may say this in any language. Retraces where you looked, classifies the miss, widens the search once, then proposes one concrete fix to the index or routing that stops it happening again.
autonomy: 1  # proposes the fix; the user approves before anything is changed
---

## What this does

Turns a bad answer into a structural improvement.

The default response to "I couldn't find it" is to apologise and try harder. That fixes today's
question and guarantees tomorrow's. This skill does the opposite: it treats the miss as evidence that
something about the workspace's organisation is wrong, and repairs *that*.

**Fire it yourself, without being asked, the moment a lookup fails.** Waiting to be corrected wastes
the most useful part of the signal.

## Step 1 — Retrace, concretely

Say exactly where you looked: which `index.md` files, which pages, which searches, which words. Not
"I searched the workspace" — the actual list.

This is not ceremony. Most of the time the cause becomes obvious here, and it is usually that a
perfectly good file was never opened because nothing pointed at it.

## Step 2 — Classify the miss

One of five. Naming it decides what the fix is:

| Class | What happened | Where the fix goes |
|---|---|---|
| **Routing** | Nothing pointed you toward the right domain | `AGENTS.md` routing table, or the domain's index preamble |
| **Indexing** | The file existed but had no index row, or a row too vague to choose from | That domain's `index.md` |
| **Placement** | The file is in the wrong domain, so no sensible search would reach it | Move it — and leave a row where it used to be |
| **Stale** | It was found, but what it said stopped being true | The page, plus a `fix` line in the log |
| **Genuine gap** | It really is not written down anywhere | Offer to capture it now, while the user has it in mind |

The last one is a real and common answer. Do not force a miss into one of the first four because a
fix feels more useful — a fabricated cause produces a fix that changes nothing.

## Step 3 — Widen the search, once

Before concluding it is a genuine gap: search the whole workspace for the term and its obvious
synonyms, and read the logs of the two most likely domains. Once — not a general hunt.

## Step 4 — Say what went wrong, in one line

Plainly, without a preamble and without over-apologising. *"It was there, but the index row said only
the filename, so I had no reason to open it."* That sentence is the deliverable.

## Step 5 — Propose exactly one fix

One concrete edit, shown in full: the row you would add, the pointer you would correct, the file you
would move. Wait for a yes.

**Then look for the pattern.** If this is the third miss of the same class, the fix is not another
row — it is a rule. Say so, and offer to write it into `decisions.md`. Three misses of one kind is
the system telling you something about its own shape.

## Verification

1. The retrace names actual files and searches, not a general description of looking.
2. The class was chosen from the five, and the fix matches the class.
3. The proposed fix is a specific edit the user could accept or reject as written.
4. Nothing was changed before they said yes.
5. If a pattern was named, it was because there were genuinely three — not because it sounded good.

## What this skill does not do

- **It does not keep a ledger of misses.** There is no log file of failures here, on purpose — one
  more file to maintain, read by nobody. The fix goes into the index or the routing, where it does
  its work; a repeated pattern goes into `decisions.md`.
- **It does not apologise at length.** One line on the cause, then the fix.
- **It does not fix the symptom only.** Finding the file the user wanted is the start of this skill,
  not the end of it.
