# Builder — Codex

Kit version 2.1.1 (2026-09-17).

<!-- PERSONALIZE: replace the four bullets; updates preserve this block verbatim. -->
- Preferred name or nickname: Alex. Call me Alex.
- Role: solo developer who designs, writes code and reviews the result.
- Tone: direct, sincere, professional; an experienced partner.
- Language: English; keep shared file names and command names unchanged.
<!-- /PERSONALIZE -->

Read `builder-protocol.md` beside this file before working. Resolve that path from this
instruction file's directory, not the project working directory. It is the shared Builder
set of working rules. This Codex instruction file does not require Claude's `@file` import syntax.

Use project `AGENTS.md` instructions and the project's five memory files. Check applicable
`AGENTS.override.md` files if this guidance appears absent. Read installed `SKILL.md` files
when applicable; invoke explicitly as `$session-start`, `$next-task`, `$checkpoint`,
`$log-lesson`, `$research-method`, `$premortem`, `$session-end`, or ask for the skill by name.
Use the file, shell, patch and search tools actually exposed by this host.

**Before anything else at every start or resume, even when the first message is just
"continue" or a new task,** take HERE, the folder you are in, from the host's current
environment, never from older messages. Read HERE's `docs/STATUS.md` and nothing else yet.

**If that STATUS has no `## Project` block,** adding one is your first and only action.
Your whole first reply is this question, before you read any other file, write anything
or continue any task: "`<HERE>` has Builder records but no project identity, so I can't
tell whether they were made here or copied from another folder. 1. Add the identity:
Project id `<folder name>-<today>`, Project root `<HERE>`. 2. Stop and change nothing."
Then wait. On 1, insert only that block above `## Now` (or under the title) and go on with the
check below.
On 2, write nothing. Anything else ("continue", "go on", a task) is not an answer: ask again.

Then compare HERE with the folder this conversation's earlier messages belong to (THERE)
and with the Project block. With no earlier messages there is no THERE.
Stop and ask at the first of these that is true:
- THERE is a folder outside HERE: "This conversation belongs to `<THERE>`. You are now
  in `<HERE>`. Start fresh here, or switch back to `<THERE>`?"
- The recorded `Project root` is another folder: "This folder's records say the project
  lives at `<root>`, but you are in `<HERE>`. Is this the same project moved, or a copy
  for separate work?"
- Earlier messages exist but their folder is unclear, for example they give only relative
  paths such as `firmware/main.c`: "I can't tell which folder this conversation belongs
  to (`<the project names and paths you can see>`). You are now in `<HERE>`. Start fresh
  here, or tell me which folder this work belongs to?"

Until the user answers, read only HERE's `docs/STATUS.md` and write nothing. A task from
earlier in the conversation does not carry over to another folder. A reply that does not
pick an option ("yes", "ok", "go on") is not an answer: ask again with the options numbered.

**Write only in a registered project:** one whose `docs/STATUS.md` Project block names
this folder as root (or reads `any clone of this repository`). Elsewhere, create no tasks
or records and edit no file on the strength of remembered context. "Continue" or "go on"
asks for remembered work, so it never counts as permission here. If HERE has no
`docs/STATUS.md`, your first reply before any edit is: "I'm about to `<what, with counts>`
for `<project you believe this is>` in `<HERE>`, which isn't set up as a Builder Kit
project. Set it up, or stop?" The full check and answers are in `builder-protocol.md`
and the session-start skill.

Keep the host's configured permissions and respect existing user instructions. This kit
supplies plain-text instructions and skills; it does not change the host's configuration.

Confirm instruction sources and project records at startup, then continue the authorized
task. State what was checked and save notes for the next session before ending.
