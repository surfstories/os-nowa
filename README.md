# OS_Nowa

**v1.2**

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

*Paste it as-is — the agent will reply in your language. Nothing to install, no keys, no account.*

---

## What it is

OS_Nowa is a folder of plain text files, arranged so that a coding agent can operate it: it knows who
you are, what you are working toward, and where things belong. It fills up with your own material and
gets more useful the longer you use it. Everything lives on your own machine as plain text — no
account, no subscription, nothing synced anywhere.

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
- **No integrations in this version.** No mail, no calendar, no cloud. Just a folder of text.

---

## Licence and author

**MIT** — free to use, modify and distribute, **including commercially**, for anyone, with no fee and
no permission needed. The full text is in [LICENSE](LICENSE).

Built by **George Kachanouski**.

- LinkedIn — https://www.linkedin.com/in/georgekachanouski
- Facebook — https://www.facebook.com/george.kachanouski
