# OS_Nowa

**v1.3**

**A personal productivity operating system any coding agent can run.**

---

## Install

Open Claude Code (or another coding agent) and paste this in as one message:

```
Set up OS_Nowa for me.

1. Ask where to put it. Default: a folder called "os-nowa" in my home directory.
2. Get it there, then disconnect it — the workspace is mine, the local git history is my undo:
       git clone https://github.com/surfstories/os-nowa.git os-nowa
       cd os-nowa && git remote remove origin
   If that fails, tell me what failed. Don't guess.
3. Work from that folder: read AGENTS.md, then follow system/procedures/onboarding.md.

Talk to me in the language I write to you in, from your very first reply.
```

*Paste it as-is. The agent will reply in your language. There is no account to make and no key to
paste.*

---

## What it is

OS_Nowa is a folder of plain text files, arranged so that a coding agent can operate it: it knows who
you are, what you are working toward, and where things belong. It fills up with your own material and
gets more useful the longer you use it. Everything lives on your own machine as plain text, with no
account and no subscription, and nothing leaves it unless you ask for that by name.

## What happens after you install it

The agent walks you through setup — about ten minutes, as a conversation, with no commands to type.
It asks what you do and what matters to you right now, and together you create your first subject
area and log your first decision. You finish with a workspace holding your own content, not an empty
skeleton.

## What is inside

- **Three levels of memory.** A small always-loaded layer — who you are, what matters. A catalog per
  subject. And the material itself, opened one file at a time. The point is that the agent never has
  to read everything to answer something.
- **Four working loops.** Knowledge (by subject, catalogued), tasks (one file, open items only),
  projects (spec before build) and decisions (append-only, never rewritten).
- **What you can ask for.** You just say them in ordinary words. There is nothing to type in a
  special way, no slash, no menu:
  - *"set me up"* — first-time setup (`onboard`)
  - *"how does this work?"* — explains any part of it, at any moment (`explain`)
  - *"check my system"* — tells you whether anything has drifted (`os-health`)
  - *"level up"* — turns one weekly chore into something automatic (`level-up`)
  - *"make this a command"* — creates a new one of these (`create-skill`)
  - *"why didn't you find that?"* — when something was missed, fixes the cause rather than the
    symptom (`backtrack`)
  - *"show me this visually"* turns whatever you are looking at into a page in your browser, where
    you can mark up the part that is wrong and send the note straight back (`lavish`)

  The short name in brackets works too, if you prefer typing one word.

## Honest boundaries

- **Tested** in Claude Code — install and setup run end to end, from a cold paste to a finished
  workspace.
- **The structure and the rules travel to other agents.** Everything here is plain markdown, and
  `AGENTS.md` is the file coding agents read by convention. Measured in **Codex** (v0.146.0): a fresh
  session asked "what should I focus on today" opened the three `me/` files on its own and answered
  from them, three runs out of three. **Cursor and Gemini follow the same convention but have not been
  measured** — treat them as likely, not proven.
- **Every command works in any agent except one.** Each is a written procedure in
  `system/procedures/`, which `AGENTS.md` points any agent at. The exception is *"make this a
  command"*: it writes a Claude Code skill file, so it only means anything in Claude Code, and **any
  command you create yourself is likewise Claude Code only.** Everything else travels: who you are,
  what you are working toward, the four loops, the filing rules and the rest of the commands.
- **One part needs Node installed. Nothing else needs anything.** Everything here is plain markdown
  that a coding agent reads. The exception is *"show me this visually"*, which opens the page in
  your browser through `lavish-axi`, an MIT tool by Kun Chen that runs on Node. Without Node every
  other part works exactly the same and that one step is skipped. Still no mail, no calendar and no
  cloud.
- **Nothing leaves your machine unless you ask for it by name.** That page is served locally. It can
  also be published to a third-party site, which puts it behind a link anyone can open unless you
  set a password, and the agent will never do that on its own initiative.

---

## Licence and author

**MIT** — free to use, modify and distribute, **including commercially**, for anyone, with no fee and
no permission needed. The full text is in [LICENSE](LICENSE).

Built by **George Kachanouski**.

- LinkedIn — https://www.linkedin.com/in/georgekachanouski
- Facebook — https://www.facebook.com/george.kachanouski
