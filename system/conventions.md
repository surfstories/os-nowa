# Conventions — the schema every domain follows

`AGENTS.md` states the rules. This file is the detail behind them: exact formats, where a new folder
goes, and what the checks defend against. Read it once; then follow it.

## The domain scaffold

Every domain has the same shape, whatever the subject:

```
<domain>/
├── index.md     the catalog — read first, always
├── log.md       append-only ledger, newest at the bottom
├── sources/     raw material the user gave you. Read it; never edit it.
└── pages/       what you wrote. Yours to create, update and cross-link.
```

A small domain may skip `sources/` and `pages/` and keep its files flat. It always has `index.md`
and `log.md` — those two are the spine, and a folder without them is invisible to every check in
this system.

**The split between `sources/` and `pages/` is the important part.** `sources/` is what came from
outside: a document, an export, a transcript, something the user wrote elsewhere. It is evidence, and
editing it destroys the ability to check any conclusion against it. `pages/` is what you concluded.
When the two disagree, the source is what happened and the page is what needs updating.

## `index.md` — the format

A catalog, grouped by category, one row per page:

```markdown
# <Domain> — index

What this domain is for, in one or two lines, so a session knows whether it is in the right place.

## Pages
- pages/annual-review-process.md — how the yearly review runs, who signs off, the three deadlines. [updated 2026-08-15]
- pages/tooling-choices.md — which tools were chosen for this work and the reasoning. [updated 2026-08-12]

## Sources
- sources/2026-08-contract.pdf — the signed agreement. Authoritative on dates and amounts.
```

Three rules make an index worth reading:

1. **A row you cannot choose from does not count.** The path, then a dash, then four or more words on
   what is inside and why you would open it. A bare filename is not a catalog entry, it is an `ls` —
   and it forces exactly the file-opening that Tier 2 exists to prevent.
2. **The index is an output, not a chore.** It is written by whatever operation created the page, in
   the same run. Nobody sits down to maintain an index; if that is ever necessary, the rule above was
   already broken.
3. **Keep a row to the length `system/tiers.md` budgets.** Enough to choose from, not enough to
   replace the page.

## `log.md` — the format

Append-only, newest at the **bottom**, one line per entry:

```markdown
# <Domain> — log

## [2026-08-15] note | Added the annual review process page
## [2026-08-16] decision | Chose the simpler tool; reasoning in decisions.md
```

**The operation word is one of five:** `note` (something was written or updated) · `source` (raw
material came in) · `decision` (a choice was made) · `fix` (something wrong was corrected) · `done`
(a task or project finished).

Five words, chosen so that `grep 'decision' log.md` actually returns the decisions. The moment a
sixth word gets used casually, that promise breaks and nothing warns you — a search for a vocabulary
that finds nothing reports nothing wrong.

**Never edit or reorder a log entry.** If an entry was wrong, append a `fix` line saying so. A ledger
that gets retro-edited to look tidy is a ledger you cannot trust about anything.

## The spine rule — if you wrote a file, you owe it a row

Any time you land a file inside a domain, you owe **two more writes in the same run**:

1. A row in that domain's `index.md`, under the right heading, with a description worth choosing from
   and an `[updated YYYY-MM-DD]` stamp.
2. A line in that domain's `log.md`.

Not later, not "at the end of the session" — in the same run. This is the single rule that decides
whether the system compounds or silently rots, because the failure is invisible: the file is there,
the work was done, and it is simply unfindable from that day forward.

## Where a new folder goes

Ask what the folder is *for*, in this order:

- Is it a subject the user accumulates material on, and will want to look things up in later? → a
  **domain** at the top level, with the full scaffold.
- Is it something being **built** — a tool, an automation, a document with a deliverable? →
  `projects/<name>/`, with a spec.
- Is it a rule about how this system itself works? → `system/`. Almost nothing belongs here; this is
  the engine, and it is not the user's to grow.

**When in doubt, prefer fewer domains.** Two thin domains that should have been one is the more
common mistake, and it is the more expensive one — material about the same subject splits across
two indexes and neither is complete.

## What the checks defend against

`os-health` looks for four failure modes. They are worth knowing by name, because once you can name
them you start noticing them while you work.

| Mode | What it looks like | What defends against it |
|---|---|---|
| **Stale facts** | A page states something that stopped being true. The agent acts on it confidently. | Dates on rows; source-beats-page; re-reading Tier 1 every few weeks |
| **Bloat** | So much context that the relevant part is diluted. Sessions get slow and vague. | Tier 1 budget; one canonical copy of each fact |
| **Confusion** | A file exists but nothing points at it, or a pointer leads nowhere. Work gets redone. | The spine rule; routing points at indexes, never leaf files |
| **Contradiction** | Two files say different things and neither is marked as the right one. | Say which is authoritative; log the correction rather than editing quietly |

## One canonical copy

One file is the truth about a given fact. If a second file needs that fact, it points at the first
rather than restating it.

This is not tidiness. A fact written in two places will be updated in one of them, and from that
moment you have two answers and no way to tell which is current. If you catch yourself writing
something you know is already written elsewhere, link instead.

**Which file owns which fact.** These are the ones most likely to end up restated, because more than
one file needs them. The owner is the only place the value is written; everywhere else names the
owner instead.

| Fact | Owner |
|---|---|
| The Tier 1 line budget | `system/tiers.md` |
| The index row length | `system/tiers.md` |
| The list of engine paths | `AGENTS.md`, under "Engine and data" |
| The five log operation words | this file, under "`log.md` - the format" |
| The five classes of miss | `system/procedures/backtrack.md` |
| The register to speak in | `AGENTS.md`, hard rule 8 |
| The em dash ban | `AGENTS.md`, hard rule 6 |
| The autonomy scale | this file, under "The autonomy scale" |

A number that appears in four files is not four times as clear. It is three chances to disagree with
itself, and the copies read as correct right up to the day one of them changes.

Superseded versions move to `<domain>/OLD/<YYYY-MM-DD>-<what>/`. Never leave `v2` next to `v3`.

**`OLD/` and `_trash/` are two different places and neither one is a delete.** `OLD/` holds a
superseded version of something still in use, inside the domain that owns it, so the current file has
one obvious name and the history sits beside it. `_trash/<YYYY-MM-DD>/` holds anything removed at
all, and it lives at the top level because what goes in it no longer belongs to a domain. The rule
that nothing is ever deleted is hard rule 4 in `AGENTS.md`; these are the two destinations it means.

## The autonomy scale

Every skill file carries `autonomy:` in its frontmatter, and `system/procedures/level-up.md` picks a
level at its third gate. One scale, three levels:

| Level | What happens |
|---|---|
| 1 | It suggests or reports; the user decides every step |
| 2 | It drafts; the user reviews before anything is saved or sent |
| 3 | It runs; the user spot-checks |

**Level 3 is earned over real runs, never granted at design time.** Nothing that has never been run
starts there, and nothing that sends anything to another person is ever level 3, because draft-first
is a hard rule and it outranks any autonomy a skill claims for itself.

## Dates

Always `YYYY-MM-DD`, always absolute. Never "last week", "recently" or "yesterday" in a file —
those are written once and read for years, and by then they mean nothing.

## The README is bilingual, and both halves change together

`README.md` carries Russian first, then English. **Any change touches both halves in the same
commit.** A fix applied to one half only is worse than no fix: six weeks later the two contradict
each other and neither is obviously the right one.
