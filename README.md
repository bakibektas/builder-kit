# The Builder Kit

Version 2.0 (2026-09-14).

A portable working protocol for **Claude Code and OpenAI Codex**: seven session skills,
durable project memory, evidence-based work, and a clean handoff between sessions.
The core is plain text. No daemon, account, API key or MCP server is required for the
standalone setup. An optional adapter connects the same habits to an existing Builder
Collective deployment.

## Start here

1. Clone `https://github.com/bakibektas/builder-kit.git`, or download and extract its ZIP.
2. Open the folder in Claude Code or Codex.
3. Say: **Install this kit for me. Follow INSTALL.md.** Name the target harness if different
   from the one you are using, and the project folder if you want project setup too.

The agent personalizes your address, role, tone and language, prepares the target files,
preserves existing content, and verifies the installation. Read [INSTALL.md](INSTALL.md)
first: it is the complete file-copy contract. Installation does not configure hooks,
change permissions, install software or connect external services.

For Codex, start a fresh session in the project and invoke `$session-start`. For Claude
Code use `/session-start` or ask for the skill by name. Then give it the task. If you
already gave a task, the startup ritual continues into it.

## What changed in 2.0

- A shared [protocol](PROTOCOL.md) with native Claude and Codex entry files, avoiding two
  independent copies of the same working rules.
- Codex installation, skill discovery, override checks and upgrade instructions.
- Explicit **files** and **collective** memory modes. A lost MCP connection never silently
  redirects authoritative memory into Markdown.
- Task ownership, verified checkpoints, current model routing and tracked delegation
  translated from the Collective without requiring its infrastructure for standalone use.
- Correct Git commit argument order and guidance for files with mixed contributors' hunks.
- Skills that preserve the user's authorization and do not impose an extra startup gate.

## Choose one memory backend

| | Files: standalone | Collective: existing Builder MCP |
|---|---|---|
| Source of truth | Five small project records | Builder DB via MCP |
| Startup | STATUS + latest JOURNAL entry | Current brief + checkpoint + task board |
| Tasks | Priority, status and owner in STATUS | Plan, task registration and claim |
| Corrections | LESSONS, searchable and curated | Lesson tools; managed rule promotion |
| Deliverables | Project artifacts/ | Searchable, versioned artifact tools |
| Dependencies | Assistant with file access | Existing configured Collective services |
| On outage | Report a file write failure | Report MCP failure; retain DB authority |

The shipped [project template](project-template/AGENTS.md) declares `Memory backend: files`.
For a managed project, keep its generated instructions and follow [COLLECTIVE.md](COLLECTIVE.md).
Do not install the standalone template on top of DB-managed governance. Backend migration
requires an explicit, verified handoff; this kit does not silently import or archive data.

In files mode, STATUS holds the current focus and owned task list. JOURNAL records sessions.
DECISIONS records why direction changed. LESSONS records corrections and mitigations.
RESEARCH preserves findings with sources and dates. Read the small volatile record at
startup and search the others when relevant. Every session closes with a usable next step.

## Package map

| Path | Purpose |
|---|---|
| [ETHOS.md](ETHOS.md) | Why the discipline exists |
| [PROTOCOL.md](PROTOCOL.md) | Shared behavior; installed as builder-protocol.md |
| [global/CLAUDE.md](global/CLAUDE.md) | Claude entry and personalization |
| [global/AGENTS.md](global/AGENTS.md) | Codex entry and personalization |
| [project-template/](project-template/AGENTS.md) | Shared project facts, native entry files and file memory |
| [skills/](skills/session-start/SKILL.md) | Seven shared SKILL.md rituals |
| [COLLECTIVE.md](COLLECTIVE.md) | MCP mapping, capability boundaries and source references |
| [INSTALL.md](INSTALL.md) | Install, update, conflicts and verification |
| [VALIDATION.md](VALIDATION.md) | Package checks and behavior acceptance scenarios |
| [PREFERENCES.txt](PREFERENCES.txt) | Optional browser-chat preference text |
| [ROADMAP.md](ROADMAP.md) | Remaining work, separate from shipped features |

## Native installation paths

| Component | Claude Code | Codex |
|---|---|---|
| User instructions | ~/.claude/CLAUDE.md | $CODEX_HOME/AGENTS.md; default ~/.codex/AGENTS.md |
| Shared protocol | builder-protocol.md beside entry | builder-protocol.md beside entry |
| User skills | ~/.claude/skills/ | ~/.agents/skills/ |
| Project skills alternative | Project .claude/skills/ | Project .agents/skills/ |
| Project instructions | CLAUDE.md reads shared AGENTS.md | AGENTS.md |
| Explicit skill | /checkpoint or name | $checkpoint or name |

For Codex, the documented portable skill path is `.agents/skills`; some deployments also
expose legacy `.codex/skills`. Check actual discovery and avoid duplicates. Respect a
custom CODEX_HOME for instructions; do not assume it relocates the documented user skill
directory. Applicable AGENTS.override.md files can shadow an AGENTS.md file. See the
[official instruction guide](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
and [official skills guide](https://learn.chatgpt.com/docs/build-skills).

For a manual install, follow the target mapping and conflict checks in INSTALL.md: copy
the personalized native entry, PROTOCOL.md as builder-protocol.md, and the seven skill
folders into one chosen discovery scope. Copy the project template only to an unmanaged
project you choose. Keep the kit checkout unchanged as the source for future updates.

## Everyday use

| Skill | Result |
|---|---|
| session-start | Restore context, identity and ownership; continue requested work |
| next-task | Pick and claim useful unblocked work |
| log-lesson | Capture a correction with a specific prevention rule |
| research-method | Verify evidence through distinct lenses and resolve disagreements |
| premortem | Stress-test consequential plans before action |
| checkpoint | Persist an exact resume point without closing work |
| session-end | Close owned work and save a verified handoff |

These are instructions an agent follows, not a runtime that enforces compliance. A
greeting alone proves little. Ask it to name the loaded files, selected backend and last
checkpoint; then check the actual records. See [VALIDATION.md](VALIDATION.md).

For browser-only chat, personalize PREFERENCES.txt and provide the relevant project
records explicitly. Browser preferences do not install local skills, run hooks or grant
filesystem/MCP access. Copy returned file updates back yourself unless a connected tool
actually saved them. Never treat a promise to remember as proof of persistence.

## Updating

Update your checkout from Git, then repeat the install request. The installer carries your
PERSONALIZE block forward verbatim, backs up changed targets with collision-safe names,
and preserves project memory and unrelated skills. Upgrading a 1.x imported installation
needs a reviewed migration because builder-protocol.md used to contain personalization.
See INSTALL.md before replacing anything. Existing Collective installations update through
their management tools, not by overwriting generated local files.

## Contributing

Run the checks in VALIDATION.md. Prefer concrete reports showing which workflow failed.
Keep host-specific mechanics in adapters, shared habits in PROTOCOL.md, and shipped
capabilities separate from planned ones. Do not add personal machine paths, credentials,
private governance dumps or frozen model tiers to the portable kit.

Licensed MIT. The original kit distilled the working habits of the Builder Collective;
this version makes those habits usable across Claude and Codex without exporting the
entire private infrastructure.

## Version history

- 2.0 (2026-09-14): shared protocol, Codex adapter, backend-aware skills, Collective
  compatibility reference, ownership-safe task lifecycle and revised installation.
- 1.5 (2026-09-02): session role tag added to the greeting canary.
- 1.4 (2026-08-24): explicit greeting canary and import-style installation.
- 1.3 (2026-08-19): artifacts folder, lesson archives and checkpoint ritual.
- 1.2 (2026-08-18): research record added.
- 1.1: agent-driven installation added.
- 1.0: initial release.
