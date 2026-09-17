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
  changes unless the user has explicitly chosen their replacement. When updating from a
  version before 2.1, offer to add the `## Project` block to STATUS.md in each project
  the user names; change nothing else in those projects.
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
   an upgrade. Offer to add the `## Project` block (id and root) at the top of an existing
   STATUS.md; that is the only change 2.1 needs in a project. Offer a separate
   project-instruction migration if Codex should share an existing Claude project's facts.
   Do not overwrite project-specific notes with placeholders.
7. If adding Codex beside Claude, carry preferences only when requested and prepare its
   own instruction file and skill location. A Claude preferences field does not configure Codex.

## 5. Copy the files and set up an optional project

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

## 6. Verify, then report

Re-read targets, not source drafts. Verify that personalization survived verbatim, the
shared protocol exists beside the instruction file, file references work, each of the
seven skills has a valid name and description in its opening metadata block (YAML
frontmatter), and no unrelated file changed. Confirm the five project memory files are
present, a set-up project's STATUS.md Project root is that project's folder, and all
existing project records are preserved.

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
