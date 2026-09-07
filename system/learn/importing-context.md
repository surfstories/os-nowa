# Bringing in context you already have

Most people arrive here with years of context already sitting somewhere else: in chat threads with
an assistant, and in Claude Projects. None of it is lost and none of it has to be retyped. This page
is how it gets moved across.

**You move it, by copy and paste.** OS-nowa has no access to your Claude account, your chat history
or your projects, and it never will. That is why this works with no key, no login and no permission
to grant. The cost is two paste operations per source; the benefit is that a folder that would have
started empty starts full.

## The idea

You do not summarise anything yourself. You hand the assistant that already holds your context a
prompt that asks it to write the context out, **under headings that are fixed in advance**. Fixed
headings are the whole trick: they turn filing from a judgement call into a lookup, so whatever comes
back can be put where it belongs without anybody guessing.

## From a chat with an assistant

Open the thread that knows you best. Paste this:

```
I'm setting up a personal context folder that my coding agent reads.
Write me a hand-off note about me, based on everything in this conversation.

Use exactly these headings. Under any heading you have no material for, write
"nothing here". Do not guess and do not invent - only what I actually told you.

## Who I am
## What I work on
## What I'm working toward
## How I prefer to be worked with
## Ongoing projects
## Decisions already made, and why
## Things still open

Plain markdown. No preamble, no closing remarks.
```

Copy what comes back and paste it here. Repeat for any other thread worth keeping: a second one adds
to the first, it does not replace it.

## From a Claude Project

One project at a time. Open the project and paste this into a new chat inside it, so it can see the
project instructions and the project knowledge:

```
I'm moving this project's context into a personal folder my coding agent reads.
Write it out for me, based on this project's instructions and its project knowledge.

Use exactly these headings. Under any heading with no material, write "nothing here".
Do not guess - only what is actually in this project.

## What this project is
## Who it's for
## Where it stands right now
## Decisions already made, and why
## Things still open
## Source material here (list each file by name, one line on what it holds)

Plain markdown. No preamble, no closing remarks.
```

The last heading matters more than it looks. It does not move the files, it lists them, so there is a
record of what exists and where, and you can bring the ones that turn out to matter across later
rather than all of them now.

## What happens to what you bring back

The paste is kept **exactly as it arrived**, in `imported/sources/`, and nothing edits it afterwards.
Then it is read once and its headings are filed:

| Heading | Where it goes |
|---|---|
| Who I am · How I prefer to be worked with | `me/profile.md` |
| What I work on | `me/profile.md`, and it suggests what your subject areas should be |
| What I'm working toward | `me/priorities.md` |
| Ongoing projects · What this project is · Who it's for · Where it stands | a folder under `projects/`, or a subject area |
| Decisions already made, and why | `decisions.md` |
| Things still open | `tasks.md` |
| Source material here | a note in the relevant index, naming what exists and where |

You see the plan before any of it is written, and nothing is written without a yes.

`imported/` is a holding area, not a subject. Material moves out of it into the areas it belongs to,
and the original paste stays behind as the record of where everything came from.

## Doing this later

You do not have to do it during setup and you do not have to do it all at once. Say *"I want to bring
in context from another chat"* at any time and this page runs again. A folder that has been in use
for a month is a better place to file an old project than an empty one, because by then it is obvious
which subject area the project belongs in.

## What to expect from the result

The assistant on the other side only knows what you told it. It will have gaps, it will have things
slightly wrong, and it was asked to write "nothing here" rather than fill them in. Read what comes
back before pasting it: correcting three lines now is cheaper than living with them in a file that
loads in every conversation.
