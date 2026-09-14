# Install or update BuilderKit

For the installing agent. Read README.md, PROTOCOL.md and the chosen native entry before
writing. Install the kit's instructions, skills and optional project template only.
The user's scope and prior choices govern this workflow.

## 1. Establish the target

Determine Claude Code, Codex or both from the request and active host. Ask only for
missing material choices. Determine whether the user wants global installation, a
project setup, or both; do not invent a project path. Inspect existing instructions first.

- For standalone setup, use the paths below. Run `claude --version` or `codex --version`
  as appropriate. If absent, report that CLI validation is unavailable; file preparation
  may continue if requested, but do not claim a working CLI install or install software.
- For Codex, inspect applicable AGENTS.override.md files and report shadowing. Do not
  remove overrides or edit config.toml to force this kit to load.

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
scope per harness; do not duplicate same-named skills globally and locally. Existing
legacy Codex skill paths require an inventory, not a second automatic installation.

## 2. Prepare a reviewable change

Inventory every exact target file and same-named skill folder. Read only the named
instruction/skill targets; never inspect credential stores. Preserve the source checkout.
Prepare personalized copies in a project-local scratch directory, not by editing the kit.

For a fresh install collect any missing address, role, tone and language preferences in
one concise question. Reuse answers already given. Fill the native entry's PERSONALIZE
block. PREFERENCES.txt is optional and only for a requested browser setup.

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
  changes unless the user has explicitly chosen their replacement.
- **Custom native file:** propose a minimal merge, keep a separate adapter, or skip.
  For a separate adapter, install the personalized native template as builder-kit-entry.md
  and add one reviewed ordinary instruction to the custom native file:
  `Read builder-kit-entry.md beside this file and follow its Builder protocol.`
  This works as an explicit instruction on either host; it does not assume Claude import
  syntax on Codex. Keep the shared protocol beside the adapter. Track this as an import
  installation and update the adapter on future runs, preserving the custom native file.
- **Protected or read-only target:** leave it untouched and report the conflict. Do not
  change permissions or bypass a denied write to force the installation.

Before every changed target, make a byte-for-byte backup next to it with date, time and a
unique suffix. Use no-clobber creation; two updates in one day must not overwrite the
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
   an upgrade. Offer a separate project-instruction migration if Codex should share an
   existing Claude project's facts. Do not overwrite project-specific notes with placeholders.
7. If adding Codex beside Claude, carry preferences only when requested and prepare its
   own native entry and discovery path. A Claude preferences field does not configure Codex.

## 5. Deploy and set up an optional project

Copy the chosen native entry, shared protocol and seven SKILL.md folders. Copy only the
files reviewed for this install. No package install, network call, hook/config edit, model
selection change or permission change is part of deployment.

For an explicitly named fresh project, copy project-template/ without replacing
existing files. Keep AGENTS.md as the canonical project facts and CLAUDE.md as its reader
when both harnesses are wanted. For Claude-only setup both files are needed; for Codex-only
setup CLAUDE.md is optional. Fill project purpose, conventions and actual validation
commands. If the user chose a project-only install with no global Builder protocol, place
PROTOCOL.md as builder-protocol.md in the project and add an explicit read instruction to
project AGENTS.md. Personalization belongs there as well in that case.

Some retained file-template headers use the older Claude terminology. PROTOCOL.md is
authoritative for canonical standing-rule placement, immediate lesson capture and optional
numeric confidence. Preserve existing records; do not reinterpret that wording as a second
memory authority or rewrite historical entries during installation.

## 6. Verify, then report

Re-read targets, not source drafts. Verify that personalization survived verbatim, the
shared protocol exists beside the entry, references resolve, seven skills have valid
frontmatter, and no unrelated file changed. Confirm the five project memory files are
present and all existing project records are preserved.

Start a fresh user session for the host to discover installed instructions and skills.
Ask it to name the loaded sources and memory files and invoke session-start in the intended
project. Do not claim runtime discovery was tested merely because files exist. If a fresh
session was not run, say **files verified; runtime discovery not yet verified**.

Report exact targets, installed version, preserved preferences, backups, skipped conflicts,
validation performed and remaining steps. For browser preferences, provide the personalized
text only if requested; account settings are a separate manual/connected-app action.

To undo, restore the exact pre-install backups and remove only known kit-owned additions
after review. Keep project memory. Never erase whole configuration or skills directories.
