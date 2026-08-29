---
name: create-skill
description: Turn something the user repeats into a one-word command. Use when they say "make a skill", "create a skill", "turn this into a command", or describe a task they want to trigger by a phrase. The user may say this in any language. Interviews for the essentials, then writes .claude/skills/<name>/SKILL.md. Tell them up front that skills are Claude Code only — the rest of OS_Nowa works in any agent, but a skill they create here will not fire elsewhere.
autonomy: 2  # drafts the skill file; the user approves before it is written
---

## What this does

Writes a new skill: a file under `.claude/skills/<name>/SKILL.md` that fires when the user says a
particular phrase, and then tells the agent what to do.

## Say this before you build anything

The user is about to invest in something with a boundary, and they should know where it is **before**
they build, not after:

> Skills are a **Claude Code** feature. Every command OS_Nowa came with works in any coding agent,
> because each one is really a written procedure in `system/procedures/`. The single exception is
> this one, *"make this a command"*, which has no procedure and cannot have one. A skill you create
> is a file that only Claude Code reads: open this folder in a different agent and it will not fire.
>
> If that matters to you, the alternative is a **written procedure** in the relevant domain. Any
> agent can follow it; you just have to point at it rather than saying a word.

One short version of that, in their language, then continue. Do not skip it because they seem keen.

## Step 1 — Interview

Five things, and no more. Ask them together as a short list, not one at a time:

1. **What should it do?** In their words. Get concrete — "summarize my week" is not yet a task.
2. **What will they say to trigger it?** The actual phrases, in the languages they use. These matter
   more than anything else in the file; a good skill that never fires is worth nothing.
3. **What does it read, and what does it produce?** Which files, and where the output lands.
4. **What must it never do?** Send anything, overwrite anything, touch anything outside a folder.
5. **How will they know it worked?** If they cannot say, the skill is not scoped yet.

## Step 2 — Write it

Six things are required in every skill file. Nothing else is:

| # | Item | Where | The test |
|---|---|---|---|
| 1 | `name` | frontmatter | matches the folder name exactly |
| 2 | `description` | frontmatter | what it does **and** the trigger phrases. Under 600 characters |
| 3 | `autonomy` | frontmatter | 1, 2 or 3 from the scale in `system/conventions.md`, with the meaning in a trailing comment |
| 4 | `## What this does` | body, first | one paragraph |
| 5 | `## Verification` | body | a command or an observation. "Check it looks right" is not one |
| 6 | `## What this skill does not do` | body | the boundaries, and anything it must refuse |

**The description is the expensive one.** It is loaded in every session whether the skill runs or
not; the body costs nothing until it fires. So detail goes in the body — the description carries only
what is needed to *choose* this skill over another one.

**Put the trigger phrases in the description**, in every language the user works in. That is what
makes the skill findable.

## Step 3 — Show it, then save it

Show the file. Get a yes. Then write it to `.claude/skills/<name>/SKILL.md`, and offer to try it
immediately — a skill that has never fired has not been tested.

## Verification

1. All six required items are present. Check them one by one against the table.
2. `name` matches the directory name.
3. The description is under 600 characters and carries the trigger phrases.
4. The user has seen the file and said yes.
5. It has been fired once, in a fresh session, and did what they expected.

## What this skill does not do

- **It does not make skills that send things.** Anything addressed to another person is draft-first,
  always. A skill may write a draft; it may not send one.
- **It does not make skills that work outside Claude Code.** See the boundary above. If portability
  matters, write a procedure instead.
- **It does not make a skill for something done once.** Three times or it is not a pattern yet.
