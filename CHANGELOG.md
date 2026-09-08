# Changelog

The version lives here and nowhere else. The top entry is what you are on.

Newest first. One heading per release, and a release is whatever landed on `main` together.

## v1.5

- **Setup brings in the context you already have, before it asks you anything.** After your name, it
  asks whether you have been talking to assistants in chats, and whether you use Claude Projects. For
  each yes it hands you a prompt to paste over there, and what comes back fills in your profile, your
  priorities, your decisions and your open items. The interview that follows becomes a confirmation of
  what is already there rather than a form. Answer no to both and setup runs exactly as it did before.
- **A new page, `system/learn/importing-context.md`**, holds both prompts and where each heading gets
  filed. It can be run at any time, not only during setup, so context can be brought over in pieces.
  Nothing is automated and nothing is granted access: you move the text yourself, by copy and paste.
- **The `backtrack` command is removed**, along with its procedure and every row that pointed at it.

## v1.4

- **Install is one command.** `git clone ... && cd ... && git remote remove origin && claude`
  replaces the block of instructions that used to be pasted into an agent. Nothing has to be pasted:
  the first run is detected in `AGENTS.md`, which offers setup and answers in the user's language.
- **The README is rewritten for someone deciding whether to install this.** New opening, a folder
  tree, and tables for what to ask for, which agents it runs on, and where the documentation is. The
  five paragraphs of honest boundaries became a compatibility table and four one-line limits.
- **A hero image.** Two beavers on a log dam holding back a lake of ones and zeros, with the data
  still flowing through it.
- **The version moved into this file.** It used to sit at the top of `README.md` and say only that
  something newer existed, never what changed. `os-health` now reads the number from here.
- **The product is spelled `OS-nowa`**, matching the wordmark and the repository. It was `OS_Nowa`.
- **The README says why this was built**, in the author's own words, instead of arguing the case for
  a folder in the abstract.

## v1.3

- The three tiers, the four loops and the seven commands, as shipped.

*Entries before v1.4 are a single line because no changelog was kept at the time. The number was
carried at the top of `README.md` and said only that something newer existed, never what changed.
That is the gap this file closes; the history it cannot recover stays unrecovered rather than
invented.*
