# explain — the method

This is the agent-neutral method. **Claude Code** runs it via the `explain` skill; **any other
agent** runs it by reading this file, which `AGENTS.md` points at. The content is the same
either way — only the trigger differs.


## What this does

Acts as the tutor for the system itself. The user learns OS_Nowa by using it, which means the
questions arrive in the middle of other work — this procedure answers them without derailing that work.

**Teach from the source, not from memory.** The material is:

- `system/tiers.md` — the three tiers, the budgets, and why a silent-failing tier needs a different
  kind of test. This is the central idea; most questions land here.
- `system/conventions.md` — the domain scaffold, the index and log formats, the spine rule, where a
  new folder goes.
- `system/learn/` — short explanations written for someone who has never seen this before.

Read the relevant one and answer from it. If the answer is not in any of them, say so — do not
invent a rule. An invented rule becomes real the moment the user follows it.

## How to answer

**Match the question's size.** "What's a domain?" is three sentences, not a lecture. Offer the deeper
version rather than delivering it: *"That's the short answer — want the reasoning behind it?"*

**Use the user's own workspace as the example.** Their domains, their priorities, their last project.
A general example about a fictional person teaches less and lands worse.

**English source, the user's language out.** Every file here is written in English so that any agent
reads it reliably. You render it into whatever language the user is speaking. Never paste the English
at them.

**Answer, then return to what they were doing.** This procedure interrupts real work; it should hand it
back.

## The limit you must state when asked about skills

When the user asks about skills — what they are, how to make one, whether they are portable — say
this plainly, without being asked twice:

> The six skills that came with OS_Nowa work in any coding agent, because they are really rules
> written in `AGENTS.md` and `system/`. **Skills you create yourself are Claude Code only.** They are
> written as files under `.claude/skills/`, which Claude Code reads and other agents do not. If you
> later open this folder in a different agent, your own skills will not fire, though everything else
> will.

Do not soften it and do not skip it because the moment feels wrong. Someone who builds five skills
and discovers this a month later has been misled by omission.

## Verification

1. The answer came from a file that was actually read this session — name it if asked.
2. Nothing was written. This procedure is read-only.
3. If the question touched skills or portability, the limit above was stated in full.
4. If the material did not cover the question, that was said, rather than filled in.

## What this procedure does not do

- **It does not change anything.** Not even an obvious typo in a file it read — it reports it instead.
- **It does not teach the user's subject matter**, only how this system works. A question about their
  own field is ordinary work, not a job for the tutor.
- **It does not replace onboarding.** If `me/profile.md` still says *Status: not yet filled in*, the
  right answer is to offer onboarding.
