# lavish - the method

This is the agent-neutral method. **Claude Code** runs it via the `lavish` skill; **any other agent**
runs it by reading this file, which `AGENTS.md` points at. The content is the same either way.

## What this does

You write an HTML page, `lavish-axi` opens it in the user's own browser, the user annotates the exact
element or phrase they mean, and you read the notes back. It replaces "the third block from the top
is wrong" with a mark on the third block.

## House rules - read these before anything below them

**Provenance.** Everything from `# Lavish Editor` down is vendored from `kunchenguid/lavish-axi`,
release **0.1.62**, taken on 2026-08-30. MIT, by Kun Chen. It is upstream text and it is unmodified:
it is not addressed to this system, and it says `$ARGUMENTS` where a Claude Code skill would take an
argument. **It no longer carries the workflow**, and that is upstream's own decision: an installed
copy of a workflow goes stale, so the block below points at the CLI instead of repeating it.

**These rules override everything below them.** That is `AGENTS.md` hard rule 7: the more general
instruction wins, and these are it. Where the vendored text says otherwise, the vendored text is
wrong for this repository - and since the refresh there is exactly one place left where it does:
the version pin, on its five bare `npx` lines. Rules 2 and 7 contradict nothing on this page any
more, because it no longer mentions `share` or `setup`: they are standing rules about what the CLI
will tell you once you run it.

1. **Always pin the version: `npx -y lavish-axi@0.1.62`.** Every invocation, with no exception, and
   that now includes the three guidance commands the block below introduces: `--help`, `design` and
   `playbook <id>`. The text below writes a bare `npx -y lavish-axi` on five lines and every one of
   them is overridden. Bare means the registry decides what runs today, in a folder holding the
   user's profile and their decisions. **An unpinned guidance command is the same hole as an
   unpinned render**, and it is a door this release opened: until now, nothing had to be fetched.

2. **`share` is never run on your own initiative.** Only when the user asks for it by name, and then,
   before you run anything: say in one plain sentence that the page will be uploaded to a
   third-party website and that without a password anyone with the link can open it. Offer the
   password form first. `--private` publishes behind a password Lavish generates and hands back;
   `--password <pw>` uses one you were given. Run the public form only if they decline a password
   knowing that. When somebody asks "can I send this to someone", the answer is `export`, which
   writes them a single portable file they can send themselves.

3. **Set the host every time, and check the address that came back.** Put
   `LAVISH_AXI_HOST=127.0.0.1` in front of every `lavish-axi` call, `poll`, `end` and `export`
   included, and never point it anywhere but loopback. By default the server binds loopback and,
   when Tailscale is running, this machine's Tailscale IPv4 as well; the variable turns that second
   bind off. It is unauthenticated and it serves local files, and this folder holds the user's
   profile, their decisions and their material.

   **Setting it is not sufficient on its own.** The server is a background daemon that outlives one
   command, and the variable is read only by the invocation that starts it. Against a daemon that is
   already running it is ignored, silently, exit 0, and the page opens anyway. So:

   1. **Read the `url` the command printed.** If its host is not `127.0.0.1`, an older daemon is
      serving and the variable did nothing.
   2. Say in one line what is about to happen: another Lavish server is already running on this
      machine, it is listening beyond this computer, and you are going to stop it. Stopping it ends
      any other Lavish review open here, which is why you say it before you do it.
   3. Run `LAVISH_AXI_HOST=127.0.0.1 npx -y lavish-axi@0.1.62 stop`, render again with the variable,
      and confirm the new `url` is loopback.
   4. **Never hand the user a link whose host is not `127.0.0.1`.**

4. **Artifacts go in `.lavish/`**, which is gitignored. Never into a domain folder: a throwaway page
   sitting there reads as an owned page, and an owned page owes an index row and a log line it will
   never earn.

5. **Node is required, and this is the only part of OS_Nowa that needs anything installed.** If
   `node` is not there, say so in one line and do the thing in plain text instead. Do not offer to
   install it and do not turn the request into a troubleshooting session. **The same one line covers
   a CLI you cannot reach at all** - offline, behind a proxy, or in a sandbox where `npx -y` exits
   opaquely. The workflow is not on this page any more, so without the CLI you have these rules and
   nothing else: say so plainly, and work in plain text.

6. **A refresh from upstream overwrites this whole file, this header included.** Nothing errors when
   it happens, and the file still reads as correct: the pin, the `share` confirmation, the host rule
   and the `.lavish/` rule all disappear at once. Whoever updates the vendored text re-adds these
   rules deliberately, in the same commit. Rule 12 in `system/maintaining.md` says the same from the
   other side, so it is findable from the engine rules and not only from the file that loses it.

7. **Never run `lavish-axi setup`.** 0.1.62 ships `setup hooks`, which installs session hooks into
   Claude Code, Codex, OpenCode and GitHub Copilot CLI, and `setup plugin`, which registers the
   package as an agent plugin in VS Code, Cursor and Copilot CLI. **Both write outside this folder,
   into the user's agent configuration**, and nothing in OS_Nowa may do that. Both subcommands are
   real and `--help` does not list them, so nothing you can run will warn you they are there. That is
   why the rule is written down here rather than left to be found.

# Lavish Editor

Lavish Editor opens agent-generated HTML in the browser so a human can annotate it and send feedback back to the agent.
Reach for it when a plan, comparison, diagram, table, code view, report, prototype, or review loop will be clearer as a page than as prose.

## Current guidance lives in the CLI

Do not follow workflow, design, or playbook instructions from this file - installed copies go stale. Get the current source of truth from the CLI:

- `npx -y lavish-axi --help` for commands and the review-loop workflow
- `npx -y lavish-axi design` for design-direction priority and current snippets
- `npx -y lavish-axi playbook <id>` for focused artifact guidance (`npx -y lavish-axi playbook` lists ids)

You do not need lavish-axi installed globally - invoke it with `npx -y lavish-axi <html-file>`.
If lavish-axi output shows a follow-up command starting with `lavish-axi`, run it as `npx -y lavish-axi ...` instead.

## Request

$ARGUMENTS

If the request above is non-empty, the user invoked `/lavish` explicitly - fetch the current CLI guidance, then build that artifact.
If it is empty, infer what to visualize from the conversation.
