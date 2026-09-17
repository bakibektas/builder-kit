# The Builder Kit

Version 2.1.0 (2026-09-17).

A shared set of working instructions for **Claude Code and OpenAI Codex**: seven skills
(reusable task instructions), saved project records, checks backed by evidence, and
clear notes so the next session can continue the work.
The kit is plain text: project files, instructions and skills. It runs inside the
assistant you already use, with no additional service or background process to install.

## Start here

1. Clone `https://github.com/bakibektas/builder-kit.git`, or download and extract its ZIP.
2. Open the folder in Claude Code or Codex.
3. Say: **Install this kit for me. Follow INSTALL.md.** Name the target assistant if different
   from the one you are using, and the project folder if you want project setup too.

The assistant records the name or nickname you want it to use, your role, preferred tone
and language. It prepares the target files, preserves existing content, and verifies the
installation. Read [INSTALL.md](INSTALL.md) first: it explains which files to copy and how
to preserve existing content. Installation does not configure hooks, change permissions,
install software or connect external services.

For Codex, start a fresh session in the project and invoke `$session-start`. For Claude
Code use `/session-start` or ask for the skill by name. Then give it the task. If you
already gave a task, the assistant continues that task after reading the project records.

## Five files help the next session continue

The [project template](project-template/AGENTS.md) saves project memory as five text files
under `docs/`. STATUS holds the current focus, tasks and who is working on each task.
JOURNAL records what happened in each session. DECISIONS records why direction changed.
LESSONS records corrections and what to do differently next time. RESEARCH preserves
findings with sources and dates. Read STATUS and the latest JOURNAL entry at startup;
search the other records when relevant. Every session ends with a saved next step.
STATUS also names the project and the folder it lives in. The assistant checks that
folder before it trusts what it remembers, and writes records only in a folder set up
this way.

## Package map

| Path | Purpose |
|---|---|
| [ETHOS.md](ETHOS.md) | Why the discipline exists |
| [PROTOCOL.md](PROTOCOL.md) | Shared behavior; installed as builder-protocol.md |
| [global/CLAUDE.md](global/CLAUDE.md) | Claude instruction file and personal preferences |
| [global/AGENTS.md](global/AGENTS.md) | Codex instruction file and personal preferences |
| [project-template/](project-template/AGENTS.md) | Starter project instructions and records |
| [skills/](skills/session-start/SKILL.md) | Seven reusable workflows, each in a SKILL.md file |
| [INSTALL.md](INSTALL.md) | Install, update, conflicts and verification |
| [VALIDATION.md](VALIDATION.md) | File checks and scenarios for testing assistant behavior |
| [PREFERENCES.txt](PREFERENCES.txt) | Optional browser-chat preference text |
| [ROADMAP.md](ROADMAP.md) | Remaining work, separate from shipped features |

## Installation paths for each assistant

User instructions and skills apply across your projects. Project instructions and skills
apply within the chosen project. Pick one skill location per assistant to avoid duplicates.

| Component | Claude Code | Codex |
|---|---|---|
| User instructions | ~/.claude/CLAUDE.md | $CODEX_HOME/AGENTS.md; default ~/.codex/AGENTS.md |
| Shared protocol | builder-protocol.md beside instruction file | builder-protocol.md beside instruction file |
| User skills | ~/.claude/skills/ | ~/.agents/skills/ |
| Project skills alternative | Project .claude/skills/ | Project .agents/skills/ |
| Project instructions | CLAUDE.md reads shared AGENTS.md | AGENTS.md |
| Explicit skill | /checkpoint or name | $checkpoint or name |

For Codex, the documented portable skill path is `.agents/skills`; some deployments also
expose legacy `.codex/skills`. Check actual discovery and avoid duplicates. Respect a
custom CODEX_HOME for instructions; do not assume it relocates the documented user skill
directory. Applicable AGENTS.override.md files can take precedence over an AGENTS.md file. See the
[official instruction guide](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
and [official skills guide](https://learn.chatgpt.com/docs/build-skills).

For a manual install, follow the target mapping and conflict checks in INSTALL.md: copy
the personalized instruction file, PROTOCOL.md as builder-protocol.md, and the seven skill
folders into one chosen user or project location. Copy the project template only to a
project you choose. Keep the kit checkout unchanged as the source for future updates.

## Everyday use

| Skill | Result |
|---|---|
| session-start | Check the session is in the right project folder, read its records, identify the session and task owner, then continue requested work |
| next-task | Choose useful work that can start now and record who will do it |
| log-lesson | Capture a correction with a specific prevention rule |
| research-method | Check evidence from different expert perspectives and resolve disagreements |
| premortem | Imagine how a costly or hard-to-reverse plan could fail before acting |
| checkpoint | Save the current state and exact next step while keeping the task active |
| session-end | Update your tasks and verify that the next session's notes were saved |

The assistant must follow these instructions; no separate program enforces them. A
greeting alone proves little. Ask it to name the loaded files and last
checkpoint; then check the actual records. See [VALIDATION.md](VALIDATION.md).

For browser-only chat, personalize PREFERENCES.txt and provide the relevant project
records explicitly. Browser preferences do not install local skills, run hooks or grant
filesystem access. Copy returned file updates back yourself unless a connected tool
actually saved them. A promise to remember does not mean the information was saved.

## Updating

Update your checkout from Git, then repeat the install request. The installer carries your
PERSONALIZE block forward without changing it, gives each backup a unique name,
and preserves project memory and unrelated skills. Upgrading a 1.x imported installation
needs a reviewed migration because builder-protocol.md used to contain personalization.
See INSTALL.md before replacing anything. Existing custom instructions and project
records remain yours; updates preserve them.

## Contributing

Run the checks in VALIDATION.md. Prefer concrete reports showing which workflow failed.
Keep assistant-specific instructions in the Claude and Codex entry files and shared habits
in PROTOCOL.md. Distinguish shipped capabilities from plans. Do not add personal machine paths, credentials,
unrelated infrastructure details or frozen model tiers to the portable kit.

Licensed MIT. BuilderKit is a standalone, lightweight set of working habits for Claude
and Codex. Its scope is project memory, session skills and portable instructions.

## Version history

- 2.1.0 (2026-09-17): fixed a real failure. A user copied a project into a new folder to
  make a simplified fork, then resumed the old conversation there and ran session-start.
  The resumed conversation still described the original project. The kit told the
  assistant to load context, resume and record tasks before work, and nothing checked
  which folder it was now in. So it read the original project's files from the new
  folder and filed tasks that had nothing to do with the fork. The user stopped using
  the kit, and the defect was ours: the kit assumed one project stays in one folder.
  Two guards now apply at every start and resume. First, a location check: the assistant
  compares the current folder with the folder the conversation belongs to and with the
  project root recorded in docs/STATUS.md. If they differ or it cannot tell, it stops and
  asks whether to start fresh or switch back. Second, a write gate: tasks and records are
  written only in a registered project, one whose STATUS.md has the new `## Project`
  block naming that folder. Elsewhere, the assistant names the project it thinks it is in
  and asks first. Existing projects need that block added once; the assistant offers to
  add it. These are still instructions, not enforcement.
- 2.0.1 (2026-09-14): simplified documentation and skills around the standalone file
  workflow; clarified preferred names, installation scope, project records and checks.
- 2.0 (2026-09-14): introduced the shared protocol and separate Claude and Codex instruction
  files, with five project records used by both assistants. Added Codex installation,
  skill discovery, override checks and upgrade instructions. Added task ownership,
  verified checkpoints and guidance for choosing available models. Corrected Git commit
  argument order and explained how to commit files containing several contributors' edits.
  Skills preserve the user's existing authorization and continue requested work after startup.
- 1.5 (2026-09-02): added a session role label to the greeting used to check that instructions loaded.
- 1.4 (2026-08-24): added that greeting check and installation through an imported instruction file.
- 1.3 (2026-08-19): artifacts folder, lesson archives and checkpoint ritual.
- 1.2 (2026-08-18): research record added.
- 1.1: agent-driven installation added.
- 1.0: initial release.
