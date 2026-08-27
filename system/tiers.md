# The three tiers — why this system loads what it loads

This is the idea OS_Nowa is built on. It takes five minutes to read and it is the difference between
a folder that gets more useful over time and one that gets slower.

## The problem

An agent has a limited amount of attention per session. Everything you put in front of it competes
for that attention — and unlike a person, it does not skim. A hundred files of context does not make
an agent a hundred times better informed; it makes it slower, more expensive, and more likely to
answer from something irrelevant it happened to read.

So the question is never "what could be useful?" It is: **what has to be there before the first
question is even asked, and what can wait until it is needed?**

That question has three answers, and they are the three tiers.

## Tier 1 — always loaded

`AGENTS.md`, plus `me/profile.md`, `me/priorities.md` and `me/connections.md`.

These arrive before you type anything. They are what makes the agent *yours* rather than a generic
assistant — it knows your name, what you are working toward, and what it can reach, without being
told.

**Budget: the three `me/` files together stay under 150 lines.**

That number is not arbitrary and it is not a technical limit. It is a discipline. Tier 1 is paid on
every single session — every line you add here, you pay for forever, including in the hundreds of
sessions where it turns out to be irrelevant. The system this one is modelled on runs on 147 lines
of always-loaded personal context, and the smallness is the reason it works, not a compromise
against it.

**The test for Tier 1: would this be true in a month, and would an agent be wrong without it?**
Both, or it does not belong. Your job title belongs. This week's meeting does not.

## Tier 2 — the catalog, loaded when you enter a domain

A domain's `index.md` and `log.md`.

When a session needs something from a subject area, it reads that domain's index first — always,
before any page. The index is a catalog: one row per page, each row saying enough that you can
*choose* from it without opening anything.

That is the entire job of Tier 2: **turn "which of these forty pages matters?" into one cheap read.**
A row that says only a filename has failed at it — you still have to open the file to find out what
is in it, which is precisely the read the tier exists to prevent.

**Budget: an index row is worth about 250 characters.** Enough to say what a page holds and why you
would open it; not enough to become the page.

## Tier 3 — the content, one file at a time

Everything in `pages/` and `sources/`.

These are opened one or two at a time, chosen from the index, and never in bulk. "Read the whole
folder" is not a strategy — it is how a session runs out of room before it starts thinking.

## The tiers fail in different ways, and that changes how you check them

This is the part people get wrong.

**Tier 1 fails silently.** The file is correct on disk. It simply never reaches the agent — because
an import path was wrong, or a mechanism quietly truncated it, or the environment does not support
autoloading at all. Nothing errors. The agent just behaves as though it does not know you, and if
you are not looking for that you will read it as the agent being unhelpful.

So **the only honest test of Tier 1 is to ask a fresh session what it can already see.** Checking the
file on disk proves nothing at all. That is why `me/profile.md` carries a diagnostic token: open a new
session and ask whether there is a diagnostic token in the instructions it was given, and to quote it.
If it quotes the one in `me/profile.md`, Tier 1 is arriving. If it says there is none, something is
broken and everything else is guesswork.

**Never name the token in the question.** A prompt that contains it is answered by itself: the session
reads it back out of your question and the check passes whether or not anything was loaded. Ask
whether there is one. This is easy to get wrong precisely because whoever sets up the check usually
knows the token and helpfully includes it.

**Tiers 2 and 3 fail loudly.** They load by an explicit read, so a failure is a missing file and an
error you can see. For those, checking the disk is the right instrument.

Never test Tier 1 from the disk. Never bother interrogating a session about Tier 2.

### One measured gotcha

**HTML comments are stripped from always-loaded context.** A line written as
`<!-- like this -->` inside a Tier 1 file is on disk but does not reach the agent. Measured
2026-08-15, both directions: the same token failed inside a comment and succeeded as visible text.

So anything an agent must *act on* goes in visible text. Comments are for the human reading the file
and for checks that read the disk — never for instructions.

## Why this beats just putting everything in one big file

Three reasons, in order of how much they cost you.

1. **You pay for Tier 1 on every session, forever.** A fact that matters once a month, sitting in
   Tier 1, is paid for in the twenty-nine sessions where it is noise.
2. **Stale facts in Tier 1 are worse than missing ones.** An agent will act confidently on an
   always-loaded fact. If it changes weekly and lives in Tier 1, you have built a machine that is
   reliably wrong. Anything that churns goes to Tier 2 or 3, where it is read fresh.
3. **A big file cannot be maintained.** Three small files with clear jobs get updated. One large file
   gets appended to until nobody knows what is in it.

## What to do when Tier 1 starts growing

It will. The pressure is always toward adding.

Ask the two questions: *will this be true in a month?* and *would an agent be wrong without it?* If
the answer to either is no, it belongs in a domain page. Then check the line count. If the three
`me/` files are past that budget, something in them has become a description of your life rather
than the few facts an agent needs to start.

Cutting Tier 1 is maintenance, not loss. The content moves down a tier; it does not disappear.
