# Onboarding — set up this workspace with the user

This is the full first-run script. **Claude Code** runs it through the `onboard` skill; **any other
agent** runs it by reading this file, which is why it lives here and not inside `.claude/`.

Follow the steps in order, one thing at a time. It is safe to re-run — if something is already
filled in, skip past it rather than asking again.

## Who you are talking to

Assume the person is **not technical** and has never used a system like this. They may have installed
a coding agent an hour ago. Be warm, plain and short. No jargon — and when a real term is unavoidable
("domain", "tier"), explain it in one sentence the first time and then use it normally.

Nothing here needs a terminal, an account, a key or an install.

## Hard rules for you, the agent

1. **Work in the user's language**, detected from their very first message. Confirm it in one short
   line *in that language* and stay in it. Translate every menu, every card, every heading you show
   them. Never paste English at someone writing to you in another language.
2. **Every choice is a numbered menu.** They answer with a number. A yes/no becomes `1` = yes,
   `2` = not now.
3. **Never create or change a file without a clear yes.** Say what you are about to write, in one
   line, then write it.
4. **Never write to an engine path.** `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `README.md`, `LICENSE`,
   `.cursor/`, `system/**`, `.claude/**`. Onboarding writes to `me/`, to one new domain folder, and
   to `decisions.md`. Nothing else, ever. If it seems useful to "adapt the instructions to this
   user", that is exactly the thing this rule forbids — it would make their workspace impossible to
   update later.
5. **Never ask for a password, an API key or a token.** None is needed for any of this.
6. **Ask one thing at a time.** A list of six questions gets one answer.
7. **If something goes wrong, solve it together.** Invite them to paste what they see. Do not abandon
   a step silently.

## The progression — five unlocks

Onboarding is a game with five ranks. **Translate the labels and lines into their language; keep the
emoji and the box exactly as shown.**

| # | Rank | Bar | Earned when |
|---|---|---|---|
| 0 | 🥚 **Rookie** | `▱▱▱▱▱ 0/5` | they begin — a light one-liner, no box |
| 1 | 🎒 **Explorer** | `▰▱▱▱▱ 1/5` | `me/profile.md` is filled in |
| 2 | 🎯 **Navigator** | `▰▰▱▱▱ 2/5` | `me/priorities.md` holds three real priorities |
| 3 | 🗂️ **Librarian** | `▰▰▰▱▱ 3/5` | their first domain exists with real content in it |
| 4 | 📌 **Decider** | `▰▰▰▰▱ 4/5` | their first entry is in `decisions.md` |
| 5 | 🏆 **Champion** | `▰▰▰▰▰ 5/5` | onboarding complete |

**Rank-up card (ranks 1–4)** — print exactly this shape, translating the three lines:

```
╔══════════════════════════╗
║  🎉  LEVEL UP!           ║
║  🎯  NAVIGATOR           ║
║  ▰▰▱▱▱   rank 2 / 5      ║
╚══════════════════════════╝
✅ <what they just did>
🔓 Unlocked: <what it now lets them do>
➡️  Next: <the next move>
```

**Finale (Step 8):**

```
╔══════════════════════════╗
║  🏆🎊  CHAMPION  🎊🏆     ║
║  ▰▰▰▰▰   5 / 5  DONE!    ║
╚══════════════════════════╝
```

The celebration must never slow the real steps. If a step is genuinely skipped, its card does not
fire and the bar shows what was actually earned — 🏆 still fires at the end.

---

## Step 0 — Check whether this has already been done

Read `me/profile.md`.

- **It says *Status: not yet filled in*** → this is a fresh workspace. Continue to Step 1.
- **It has a real name in it** → already set up. Do not re-run blindly. Say so, and offer a menu:
  `1)` update the profile · `2)` add a new domain · `3)` just get to work.

## Step 1 — Language, name, and one line of reassurance

Set the working language from their **first message** — they trigger this in the language they want.
Confirm it in one short line in that language.

Then greet them. If you can see their name from the environment, use it and confirm:
> Hi **<name>** — have I got that right?  `1)` Yes  `2)` Call me something else

If you cannot, just ask once what to call them.

Then, one line, in their language: *"Nothing here needs installing and nothing leaves your computer.
I only touch files in this folder, and I'll always ask first."*

**🥚 Start the game** — one light line telling them they are starting as 🥚 **Rookie** (`▱▱▱▱▱ 0/5`)
and you will level them up as you go. No box yet.

## Step 2 — Who they are (three questions, not an interview)

Ask these one at a time. Keep it light — this is not a form.

1. **"What do you actually spend your days on?"** Work, studies, running something, several things.
2. **"What would you most like a hand with?"** Offer a menu: `1)` keeping track of things ·
   `2)` writing and drafting · `3)` making sense of documents · `4)` planning · `5)` something else.
3. **"Is there anything about how you like to work that I should know?"** One line is fine. Some
   people want short answers; some want to be asked before anything is changed.

**Do not infer anything they did not say** — least of all gender from their name. Write the profile
so it does not need to guess ("Prefers short answers" rather than "She prefers short answers"). This
file is read in every conversation, so a wrong assumption here is one they will meet again and
again. If it genuinely matters later, ask.

**Write `me/profile.md`** from their answers — show them what you are about to write first. Keep it
under about 30 lines. Remove the line `<!-- filled by onboarding -->` and the *Status: not yet
filled in* line. **Leave the diagnostic token line in place** — it costs nothing and it is how the
system can be checked later.

**🎒 Fire the Explorer card.** ✅ *Your workspace knows who you are.* 🔓 *Unlocked: I don't have to
ask again — this loads in every conversation.* ➡️ *Next: what you're working toward.*

## Step 3 — Teach the one idea, in 60 seconds

Do this **here**, right after they have seen a file get written, because now it means something.

Tell them, in their own language, roughly this — short, no lecture:

> There are three levels of memory here. **The always-on level** is that profile you just wrote plus
> two small files — it loads in every single conversation, which is why it has to stay small. **The
> middle level** is a catalog for each subject you keep material on; I read it to work out which one
> or two files are worth opening. **The bottom level** is the material itself, opened one file at a
> time.
>
> The whole point is that I never have to read everything to answer something.

Then offer, as a menu: `1)` makes sense, keep going · `2)` tell me a bit more. On `2`, read
`system/tiers.md` and explain from it, in their language. Do not deliver that unasked.

## Step 4 — What they are working toward

*"What are the two or three things that actually matter to you over the next few months?"*

Push gently for **three**, and for real ones — "get healthier" is a wish, "walk 30 minutes before
work on weekdays" is a priority. If they give you six, ask which three matter most; a ranked list of
twelve is not ranked.

**Write `me/priorities.md`.** Ranked, dated, one or two lines each. Show it before writing it.

**🎯 Fire the Navigator card.**

## Step 5 — Their first domain (the important step)

This is where the workspace stops being empty. **Do not invent the subject** — take it from what they
already told you in Step 2.

> *"Let's set up your first area. Based on what you've said, I'd suggest one for **<subject>**. That
> gives it a home, so everything about it lands in one place."*
> `1)` yes, that one · `2)` something else — they name it

Then:

1. **Create the folder** — `<name>/` with `index.md` and `log.md`, from
   `system/templates/domain-index.md` and `system/templates/domain-log.md`. Fill every `{{...}}`
   placeholder; none may survive.
2. **Put something real in it, now.** This is the step that decides whether they come back tomorrow.
   Ask: *"What's one thing about <subject> that's in your head and not written down anywhere?"* Take
   their answer, write it as a page in `<name>/pages/`, using `system/templates/page.md`.
   It does not need to be long. It needs to be **theirs**.
3. **Add the index row and the log line** — in the same breath, and say out loud that you are doing
   it: *"And I'm adding it to the catalog, so it's findable later. Anything I write here always gets
   a catalog row — that's the one habit that keeps this from turning into a folder of lost files."*

**🗂️ Fire the Librarian card.**

## Step 6 — Their first decision

*"Last thing worth capturing: is there something you've decided recently — how you want to work, a
choice you made, a thing you've decided to stop doing?"*

If nothing comes to mind, offer the one that just happened: *"How about this one — you decided to
organise <subject> here rather than where it was before. Shall we log that?"* That is a genuine
decision and it is a fair first entry.

**Append it to `decisions.md`** in the shape that file describes: what was decided, **why**, and what
was rejected. Explain in one line why the *why* is the part that matters — in six months it is the
only thing they cannot reconstruct.

**📌 Fire the Decider card.**

## Step 7 — Check your own work

Before celebrating, verify all four, by actually looking:

1. `me/profile.md` has a real name and no `<!-- filled by onboarding -->`.
2. `me/priorities.md` holds **at least three** items.
3. **One domain folder** exists, with `index.md`, `log.md`, and at least one real page — and the
   index has a row pointing at that page.
4. `decisions.md` holds **at least one** entry.

Also check that no `{{` placeholder survives anywhere, and that the three `me/` files together are
under about 150 lines.

If any of these is false, go back and finish it. **Do not declare onboarding complete on a workspace
that is still empty** — that is the one failure this whole procedure exists to prevent.

## Step 8 — 🏆 Champion, and what happens now

Fire the finale card. Then close with a few tight lines, in their language, and **no menu**:

1. **It's yours.** Everything here is plain text on their own machine. No account, nothing synced.
2. **It compounds.** Keep working from this folder. Every subject they add, every decision they log,
   makes the next conversation start further ahead.
3. **One task, one new conversation.** Fresh chat per thing.
4. **Three things to remember they can say:**
   - *"how does this work?"* — any time, about any part of it
   - *"level up"* — once a week, to turn one repeated chore into something automatic
   - *"check my system"* — every few weeks, to catch anything that has drifted
5. **Back it up.** It is a folder. Putting it somewhere that syncs — or occasionally copying it — is
   the whole backup strategy. Offer to explain if they want.

End on one encouraging line, in their language.
