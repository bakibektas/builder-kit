# Install or update BuilderKit

For the assistant doing the installation. Read README.md, PROTOCOL.md and the chosen
assistant's instruction template (global/CLAUDE.md or global/AGENTS.md) before
writing. Install the kit's instructions, skills and optional project template only.
The user's scope and prior choices govern this workflow.

## 1. Establish the target

Determine Claude Code, Codex or both from the request and the assistant being used.
Ask only for missing choices that affect the installation. A user-wide (global)
installation applies across projects; a project-only installation applies in one chosen
folder. Determine which the user wants, or whether they want both user-wide defaults and
project setup. Do not invent a project path. Inspect existing instructions first.

- For standalone setup, use the paths below. Run `claude --version` or `codex --version`
  as appropriate. If the command is unavailable, report that the command-line application
  could not be checked. File preparation may continue if requested, but do not claim
  a working application installation or install software.
- For Codex, inspect applicable AGENTS.override.md files and report if they take
  precedence over AGENTS.md. Do not remove overrides or edit config.toml to force this kit to load.

| Source | Claude destination | Codex destination |
|---|---|---|
| global/CLAUDE.md | ~/.claude/CLAUDE.md | — |
| global/AGENTS.md | — | $CODEX_HOME/AGENTS.md, default ~/.codex/AGENTS.md |
| PROTOCOL.md | ~/.claude/builder-protocol.md | builder-protocol.md in the same Codex home |
| Seven skills/* folders | ~/.claude/skills/ | ~/.agents/skills/ |

On Windows resolve `~` from the user's profile directory. Use PowerShell literal paths;
do not repurpose HOME, CODEX_HOME or another system variable. Honor an existing custom
Claude configuration directory if the environment supplies one. For project-only skills,
use the target project's .claude/skills or .agents/skills instead. Choose one discovery
location per assistant, either user-wide or project-only; do not duplicate same-named
skills in both. Check any older Codex skill locations before adding another copy.

## 2. Prepare a reviewable change

List every exact target file and same-named skill folder. Read only the named
instruction/skill targets; never inspect credential stores. Preserve the source checkout.
Prepare personalized copies in a project-local scratch directory, not by editing the kit.

For a fresh install, collect any missing preferences in one concise question: the name
or nickname the user wants the assistant to use, role, tone and language. Reuse answers
already given. Fill the instruction file's PERSONALIZE block. PREFERENCES.txt is optional
and only for a requested browser setup.

For an existing installation, recognize the `Kit version` line and PERSONALIZE markers.
Capture the entire existing block verbatim before transforming anything. If markers are
missing or malformed, treat the file as custom: show a proposed merge, do not guess the
boundary or erase user text. Preserve existing personal rules, not just the four fields.

Show a concise target list and diffs for conflicts. If authorization already covers an
exact replacement or merge, apply it. Otherwise ask once for the concrete unresolved
conflict. Routine copying into an empty, requested target needs no repeated confirmation.

## 3. Handle existing content

- **Already identical:** leave it alone and report no change. A repeat install should
  create no duplicate loading lines, redundant copies or unnecessary backups.
- **Kit-owned update:** preserve personalization and review any other local edits. The
  version marker alone does not prove all text is replaceable. Preserve local skill
  changes unless the user has explicitly chosen their replacement. Every update also
  runs section 5 for the user's existing projects.
- **Existing custom instruction file:** propose a small merge, use a separate BuilderKit
  entry file, or skip. For a separate entry file, install the personalized instruction
  template as builder-kit-entry.md and add one reviewed read instruction to the custom file:
  `Read builder-kit-entry.md beside this file and follow its Builder protocol.`
  This is an explicit instruction for either assistant; it does not rely on Claude import
  syntax in Codex. Keep the shared protocol beside builder-kit-entry.md. Record that the
  custom instruction file loads this separate entry, and update the entry on future runs.
  Preserve the custom instruction file.
- **Protected or read-only target:** leave it untouched and report the conflict. Do not
  change permissions or bypass a denied write to force the installation.

Before changing an existing target, make an exact backup next to it with date, time and a
unique suffix. Create the backup only if its path is unused; two updates in one day must not overwrite the
first backup. Back up modified skill files too. Never replace an entire skill directory
blindly: it may contain personal resources. Preserve unrelated files and folders.

## 4. Upgrade a 1.x installation

1. Detect whether the old personalized protocol is CLAUDE.md or builder-protocol.md.
   The latter was loaded by a custom CLAUDE.md using `@builder-protocol.md`.
2. Capture its PERSONALIZE block verbatim and inspect local edits outside that block.
3. For the direct case, prepare the current Claude entry with that block, plus PROTOCOL.md as
   builder-protocol.md. Back up old content before the reviewed replacement.
4. For the old import case, prepare builder-kit-entry.md with the preserved block and
   PROTOCOL.md as builder-protocol.md. Propose replacing only the old import line in the
   custom CLAUDE.md with the ordinary read instruction from section 3. Leave all other
   custom content untouched. Apply only once the concrete migration is authorized.
5. Copy changed skill files under the same names after handling local modifications.
6. Never replace project STATUS, JOURNAL, DECISIONS, LESSONS, RESEARCH or artifacts during
   an upgrade. Section 5 adds the `## Project` block; that is the only change 2.1 needs in
   a project. Offer a separate
   project-instruction migration if Codex should share an existing Claude project's facts.
   Do not overwrite project-specific notes with placeholders.
7. If adding Codex beside Claude, carry preferences only when requested and prepare its
   own instruction file and skill location. A Claude preferences field does not configure Codex.

## 5. Give existing projects an identity (every update)

From 2.1 a project's `docs/STATUS.md` carries a `## Project` block: its id and the folder
it lives in. Projects set up by an older kit do not have one. Without it the assistant
cannot tell a project from a copy of it, and in live testing a small model resumed old
work in a copied folder and overwrote files there. This step closes that for every
project you are shown. Run it on every update, including an update from 2.1.0, and
after a 1.x upgrade.

1. Ask once: "Which folder or folders hold your Builder Kit projects? I will look for
   projects beneath them and change nothing until you confirm." Reuse folders the user
   already named. If the user declines, skip this step and say that the assistant will
   ask about the identity the first time it starts in each older project.
2. Find every `docs/STATUS.md` beneath those folders. Skip `.git`, `node_modules`, other
   dependency and build folders, and anything you cannot read. Do not follow links out of
   the named folders. A kit project's STATUS.md has `## Now` and `## Tasks` sections;
   list any other STATUS.md as "not a kit project, skipped".
3. Show one list, one line per project folder, as absolute paths:
   - **will add:** no `## Project` block. Show the block you will add:
     `Project id` = the folder's name plus today's date (`cnc-plotter-2026-09-17`),
     `Project root` = the folder's absolute path.
   - **already set:** the block exists and its root is this folder, or reads
     `any clone of this repository`. No change.
   - **needs a decision:** the block exists but its root is another folder (a moved or
     copied project), or two found projects have the same focus and tasks (one may be a
     copy of the other). Change nothing for these; the assistant asks in that folder at
     the next session start. Say so.
   - **skipped:** not a kit project, or unreadable.
4. Ask once: "Add the identity to the N projects marked 'will add'?" On yes, insert only
   the two-line block under a `## Project` heading, above `## Now`. Change nothing else in
   the file and nothing else in the project. The report lists every file changed, and a
   project under Git shows the two lines in its diff. On no, change nothing.
5. Re-read each changed STATUS.md and confirm its root is its own folder.

Be honest about the limit: this step can only change the projects it was pointed at.
Tell the user: "Projects outside these folders still lack an identity. The assistant will
ask to add one, before doing anything else, the first time it starts in each of them."
That question is the backstop in PROTOCOL.md; it is not a substitute for this step.
A copy made after this step carries the original's root, so the assistant will ask
whether it was moved or copied.

## 6. Copy the files and set up an optional project

Copy the chosen instruction file, shared protocol and seven skill folders, each containing
SKILL.md. Copy only the files reviewed for this install.
No package install, network call, hook/config edit, model
selection change or permission change is part of this installation.

For an explicitly named fresh project, copy project-template/ without replacing
existing files. Fill the `## Project` block in docs/STATUS.md: a new Project id and the
project folder's absolute path as Project root. Without that block the folder is not a
registered project and the assistant asks before writing records there. Keep shared
project facts in AGENTS.md and use CLAUDE.md to read it when both assistants are wanted.
For Claude-only setup both files are needed; for Codex-only setup CLAUDE.md is optional. Fill project purpose, conventions and actual build or test
commands. If the user chose a project-only install with no global Builder protocol, place
PROTOCOL.md as builder-protocol.md in the project and add an explicit read instruction to
project AGENTS.md. Personalization belongs there as well in that case.

Some retained template headers use older guidance: save lessons only at session end,
put project rules in CLAUDE.md or always give a confidence percentage. Follow PROTOCOL.md:
save corrections promptly, keep shared project rules in AGENTS.md when both assistants
use it, and explain confidence through evidence; percentages are optional. Preserve
existing records and do not rewrite historical entries during installation.

## 7. Verify, then report

Re-read targets, not source drafts. Verify that personalization survived verbatim, the
shared protocol exists beside the instruction file, file references work, each of the
seven skills has a valid name and description in its opening metadata block (YAML
frontmatter), and no unrelated file changed. Confirm the five project memory files are
present, a set-up project's STATUS.md Project root is that project's folder, and all
existing project records are preserved. List the projects that received an identity in
section 5, the ones that need a decision, and the folders that were not searched.

Start a fresh user session for the host to discover installed instructions and skills.
Ask it to name the loaded instruction files and project records and invoke session-start
in the intended project. The presence of files on disk does not prove the assistant found and
loaded them. If a fresh session was not run, say **files verified; loading in a fresh
assistant session not yet verified**.

Report exact targets, installed version, preserved preferences, backups, skipped conflicts,
validation performed and remaining steps. For browser preferences, provide the personalized
text only if requested; account settings are a separate manual/connected-app action.

To undo, restore the exact pre-install backups and remove only known kit-owned additions
after review. Keep project memory. Never erase whole configuration or skills directories.
