# Changelog

The version lives here and nowhere else. The top entry is what you are on.

Newest first. One heading per release, and a release is whatever landed on `main` together.

## v1.5

- **The `lavish-axi` pin moved from 0.1.62 to 0.1.67.** Five upstream releases: an agent presence
  fix across overlapping polls, an attachment upload fix behind a reverse proxy, a tracked-batch
  pattern in the input playbook, and polls that return instead of hanging when the last review
  window disconnects. The one substantial release is 0.1.65, which replaced per-tab SSE with one
  WebSocket and added a reload handoff that migrates tabs opened against an older server and
  preserves queued feedback across the switch. Nothing touched host binding, `share` or `setup`.
  Three pinned invocations, the provenance release number and the taken-on date moved; the vendored
  text below the house rules was deliberately not refreshed.

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

- The three tiers, the four loops and the six commands, as shipped.

*Entries before v1.4 are a single line because no changelog was kept at the time. The number was
carried at the top of `README.md` and said only that something newer existed, never what changed.
That is the gap this file closes; the history it cannot recover stays unrecovered rather than
invented.*
