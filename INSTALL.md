# Install or update the Builder Kit

## If you are the person, not the assistant

You do not need this page, and you do not need to download anything. Open your AI coding
assistant and ask it about the kit first:

> **Learn about the Builder Kit at https://github.com/bakibektas/builder-kit and tell me
> what it would do if we installed it.**

It fetches the kit, reads it, and explains it back to you: what it would add, where, and
what it changes. Ask whatever you want before deciding, including *is this safe to
install?* and *how do I undo it?*. When you are ready, say **go ahead and install it**.

To update later, say **update the Builder protocol**. Nothing to re-download by hand.

The rest of this page is the recipe your assistant follows. Three things worth knowing
before you say yes:

- **It shows you the list first.** Every file it wants to write, before it writes one.
- **Nothing you already have is thrown away.** Existing instructions are kept, and
  anything it replaces is copied to a backup beside the original first.
- **It copies text files, and offers one setting.** No software is installed and nothing
  is sent anywhere. The one setting is optional: it lets your assistant keep a list of
  your projects in a small folder of its own without asking you each time. You see the
  exact line before it is written, and you can say no.

### What it will ask you, and why

Twelve questions at most, usually far fewer: it reuses anything you have already told it.
Each one is there for a reason:

| It asks | Because |
|---|---|
| What should I call you? | So it speaks to you by name, and never has to ask again. |
| What do you do, and how should I talk to you (tone, language)? | So it pitches its answers at you rather than at a programmer, in your own language. |
| One assistant in charge, or work solo? | By default it keeps the plan itself and hands routine legwork to helper assistants on smaller models, which saves your strongest model's allowance; solo means it does everything itself. |
| Which assistant is this for: Claude Code, Codex, or both? | They keep their settings in different folders, and it has to know which one to write to. |
| Everywhere, or just one project? | These habits can be your default for all your work, or stay inside a single folder; your answer decides where the files go. |
| Which project folder? | It never guesses a folder; your notes go where you say and nowhere else. |
| You already have instructions of your own here: merge, keep separate, or skip? | So it does not quietly paint over something you wrote yourself. |
| Which folders hold your older projects? | Projects set up by an older version are missing the line that tells a project apart from a copy of it, and it can only add that line to folders you point it at. |
| Which of these folders is the original? | Two folders with identical notes are usually one copied from the other, and getting this right is what stops an old chat editing the copy by mistake. |
| May I keep a list of your projects, and update it without asking each time? | So that from any project you can ask what else is going on. It needs one permission, for one small folder that holds only that list, and you see the exact line first. |
| Here is every file I want to write, go ahead? | Nothing is written before you have seen the whole list. |
| Do you also use an assistant in a browser? | So it can hand you a short personalised version of these habits to paste there, at the end. |

If it asks you something that is not on this list, it is fair to ask why before you
answer.

When it finishes it should tell you where each file went, what it backed up, and
anything it skipped. If it claims the installation "works" without having opened a new
session to check, that part is unverified: ask it to say so plainly.

---

## For the assistant doing the installation

## 0. Fetch the kit, then explain it before installing anything

The user's first message is usually a question, not an order: "learn about the Builder Kit
at `<address>` and tell me what it would do if we installed it." Treat it as a question.

**First check where you are.** If this host gives you no way to read and write files on
the user's computer (a chat window in an app or a browser, a phone app), say so in one
line and do not walk through an install you cannot perform: "I can't open folders on your
computer from here, so the kit can't be installed in this window. Open Claude Code or
Codex on your computer and ask me again there." You may still explain what the kit does.

1. Fetch the kit yourself from the repository address the user gave, with the tools this
   host actually exposes: clone it, or read its files over the network. Put the copy in a
   scratch location. The user downloads nothing, unzips nothing, and never has to open or
   work inside the kit's own folder.
2. Read README.md, INSTALL.md and PROTOCOL.md before you describe them. Describe what you
   read, not what a kit like this usually contains.
3. Answer in plain words, leading with what was asked rather than a feature list: what it
   would add, which folders it would write in, what it changes about the way you work, and
   what it does not do. Name both destinations concretely: the assistant's own settings
   folder, and the project folder the user chooses.
4. Answer "is it safe?" specifically, and do not oversell it. It is text: instructions and
   notes, with nothing to execute, so no software is installed, no service starts, no
   account is created and nothing is sent anywhere. It does write into the assistant's
   settings folder, so say that rather than "it installs nothing". It changes how you
   work, which is the point of it. It is undone by restoring the backups and deleting the
   files, and you can list them. Say what you have not verified.
5. Install nothing until the user says yes. "Tell me about it" is not a yes. Answer
   follow-up questions and offer the install again; do not press.
6. If the network fetch is unavailable or denied, say so plainly and stop. Do not
   reconstruct the kit from memory, and do not describe a version you have not read.
7. **Updating** is one sentence from the user: "update the Builder protocol." Fetch the
   current kit from the same address, compare it with what is installed, say what would
   change, and on a yes run sections 2 to 7 as an update, including section 5 for existing
   projects. The user never downloads a folder.

## 1. Establish the target

Read README.md, PROTOCOL.md and the chosen
assistant's instruction template (global/CLAUDE.md or global/AGENTS.md) before
writing. Install the kit's instructions, skills and optional project template only.
The user's scope and prior choices govern this workflow.

Determine Claude Code, Codex or both from the request and the assistant being used.
Ask only for missing choices that affect the installation, and give each question a
one-line reason as you ask it; the reasons are listed at the top of this file.
A user-wide (global) installation applies across projects; a project-only installation
applies in one chosen folder. Determine which the user wants, or whether they want both user-wide defaults and
project setup. Do not invent a project path. Inspect existing instructions first.

- For standalone setup, use the paths below. Run `claude --version` or `codex --version`
  as appropriate. If the command is unavailable, report that the command-line application
  could not be checked. File preparation may continue if requested, but do not claim
  a working application installation or install software.
- For Codex, inspect applicable AGENTS.override.md files and report if they take
  precedence over AGENTS.md. Do not remove overrides or edit config.toml to force this kit to load.

| Source | Claude destination | Codex destination |
|---|---|---|
| global/CLAUDE.md | ~/.claude/CLAUDE.md | (not used) |
| global/AGENTS.md | (not used) | $CODEX_HOME/AGENTS.md, default ~/.codex/AGENTS.md |
| PROTOCOL.md | ~/.claude/builder-protocol.md | builder-protocol.md in the same Codex home |
| Seven skills/* folders | ~/.claude/skills/ | ~/.agents/skills/ |

User instructions and skills apply across the user's projects; project instructions and
skills apply within one chosen project. The remaining targets and the invocation form:

| Component | Claude Code | Codex |
|---|---|---|
| Project skills alternative | Project .claude/skills/ | Project .agents/skills/ |
| Project instructions | CLAUDE.md reads shared AGENTS.md | AGENTS.md |
| Explicit skill | /checkpoint or name | $checkpoint or name |

For Codex, the documented portable skill path is `.agents/skills`; some deployments also
expose legacy `.codex/skills`. Check actual discovery and avoid duplicates. Respect a
custom CODEX_HOME for instructions; do not assume it relocates the documented user skill
directory. Applicable AGENTS.override.md files can take precedence over an AGENTS.md
file. See the
[official instruction guide](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
and [official skills guide](https://learn.chatgpt.com/docs/build-skills).

For a manual install, follow this target mapping and the conflict checks below: copy the
personalized instruction file, PROTOCOL.md as builder-protocol.md, and the seven skill
folders into one chosen user or project location. Copy the project template only to a
project the user chooses. Leave the fetched copy unchanged while you install from it; it
is a scratch source, not a folder the user keeps working in.

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
or nickname the user wants the assistant to use, role, tone, language, and whether the
assistant should keep one assistant in charge with helpers for the legwork (the default)
or work solo. Say in one short line what the five answers are for (they fill the block the
assistant reads at the start of every session), so the question informs rather than
interrogates. Ask about helpers once, with its one-line reason, and never more than that.
Reuse answers already given. Fill the instruction file's PERSONALIZE block. PREFERENCES.txt is optional
and only for a requested browser setup. Never ask for a project description or "what do
you want to build": a project's records are created from what the user said and filled in
as work happens.

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

1. Ask once: "Which folder or folders hold your Builder Kit projects? Projects set up by
   an older version are missing the line that tells a project apart from a copy of it,
   and I can only add it to folders you point me at. I will look for projects beneath
   them and change nothing until you confirm." Reuse folders the user
   already named. If the user declines, skip this step and say that the assistant will
   ask about the identity the first time it starts in each older project.
2. Find every `docs/STATUS.md` beneath those folders. Skip `.git`, `node_modules`, other
   dependency and build folders, and anything you cannot read. Do not follow links out of
   the named folders. A kit project's STATUS.md has `## Now` and `## Tasks` sections;
   list any other STATUS.md as "not a kit project, skipped".
3. Look for copies before you list anything. Take every found project that has no
   `## Project` block and compare its `## Tasks` section with each other one. Identical
   task lines mean one folder is probably a copy of the other; call them a **copy group**.
   Folders whose names differ only by a suffix such as `-fork`, `-copy` or `-old` are
   also a copy group. Copies are the case this step exists for: an older conversation
   resumed in the wrong one of them is how files get overwritten.
4. Show one list, one line per project folder, as absolute paths:
   - **will add:** no `## Project` block and not in a copy group. Show the block you will
     add: `Project id` = the folder's name plus today's date (`cnc-plotter-2026-09-17`),
     `Project root` = the folder's absolute path.
   - **copy group:** list its folders together and ask which one is the original. The
     original gets its own block. Every other folder in the group gets the original's
     block, unchanged: the original's id and the original's root. That is what a copy
     made after this update would carry, so the first session in each copy asks "moved
     or copy?" and registers it with a `Copied from` line when the user says "a copy".
     Do not register a copy under its own root here: in live testing a small model
     resumed old work in a copy that was registered as its own project, even with a
     `Copied from` line, and edited its files in 5 of 6 runs. If the user does not know
     which folder is the original, treat the one whose `docs/` files changed least
     recently as the original, and say so.
   - **already set:** the block exists and its root is this folder, or reads
     `any clone of this repository`. No change.
   - **moved or copied since 2.1:** the block exists but its root is another folder.
     Change nothing; the assistant asks "moved or copy?" in that folder at the next
     session start. Say so.
   - **skipped:** not a kit project, or unreadable.
5. Ask once, in one message: "Add the identity to the N projects above? For each copy
   group, which folder is the original? Getting the original right is what stops a
   later conversation editing the copy by mistake." Wait for the answer. On yes, insert only the
   block (heading, id and root) above `## Now`. Change nothing
   else in the file and nothing else in the project. The report lists every file changed,
   and a project under Git shows the lines in its diff. On no, change nothing.
6. Re-read each changed STATUS.md and confirm its root: its own folder, or for a copy,
   the original's folder.

Be honest about the limit: this step can only change the projects it was pointed at.
Tell the user: "Projects outside these folders still lack an identity. The assistant will
ask to add one, before doing anything else, the first time it starts in each of them."
That question is the backstop in PROTOCOL.md; it is not a substitute for this step.
A copy made after this step carries the original's root, so the assistant will ask
whether it was moved or copied. Do not say the projects "can no longer be mistaken for
copies": the identity makes a mistake visible to the assistant, it does not prevent one.

## 6. Copy the files and set up an optional project

Copy the chosen instruction file, shared protocol and seven skill folders, each containing
SKILL.md. Copy only the files reviewed for this install.
No package install, network call, hook edit or model selection change is part of this
installation. The only setting it touches is the one allowance for the projects list
below, and only if the user says yes to it.

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

### The projects list (optional)

Offer it once, with its reason: "May I keep a list of your projects, so that from any
project you can ask what else is going on? It is one text file in a small folder of its
own, `.builder` in your home folder. To update it without asking you each time I need one
permission, for that folder only." On no, leave `Projects list: none` in the PERSONALIZE
block and change nothing else. On yes:

1. Create `.builder/projects.md` in the user's home folder with the single line
   `# Builder projects`, unless it already exists. One list serves Claude Code and Codex.
2. Write the file's absolute path into the `Projects list` bullet of the PERSONALIZE block
   in each installed instruction file. The assistant uses the list only when that bullet
   names a path.
3. Show the exact permission line and the settings file it goes into, and add it on a
   yes. Check the host's current documentation for the exact form first; do not copy it
   from this page unchecked. At the time of writing: for Claude Code, one allow rule for
   edits in that folder, `Edit(~/.builder/**)`, under `permissions.allow` in the user
   settings file; for Codex, the folder's absolute path under `writable_roots` in the
   `[sandbox_workspace_write]` table of its config file. Back the settings file up first,
   add only that line, and leave everything else in it as it was. If the user wants the
   list but not the permission, skip this item and say what follows: the assistant will
   ask each time it updates the list.
4. Add an entry for each project that section 5 found and each project this install set
   up, in the format PROTOCOL.md gives. Take `About` and `Status` from the project's
   `docs/STATUS.md`; where it says nothing, write `not described yet`.

To undo: remove the permission line, set the bullet back to `none`, and delete the
`.builder` folder.

## 7. Verify, then report

Re-read targets, not source drafts. Verify that personalization survived verbatim, the
shared protocol exists beside the instruction file, file references work, each of the
seven skills has a valid name and description in its opening metadata block (YAML
frontmatter), and no unrelated file changed. Confirm the five project memory files are
present, a set-up project's STATUS.md Project root is that project's folder, and all
existing project records are preserved. List the projects that received an identity in
section 5, the copies that now carry their original's identity and will ask "moved or
copy?" at their next session, and the folders that were not searched. If a projects list
was set up, confirm the file exists, the bullet names its absolute path, and the
permission line is in the settings file exactly as shown to the user.

Start a fresh user session for the host to discover installed instructions and skills.
Ask it to name the loaded instruction files and project records and invoke session-start
in the intended project. The presence of files on disk does not prove the assistant found and
loaded them. If a fresh session was not run, say **files verified; loading in a fresh
assistant session not yet verified**.

Report exact targets, installed version, preserved preferences, backups, skipped conflicts,
validation performed and remaining steps.

To undo, restore the exact pre-install backups and remove only known kit-owned additions
after review. Keep project memory. Never erase whole configuration or skills directories.

## 8. Offer the browser version, once, at the end

Some of the same person's work happens in an assistant on a website rather than on their
computer. After a successful install, offer once:

"Do you also use an assistant in a browser? I can write you a short personalised version
of these habits to paste into its custom instructions."

On yes, write a plain text file into the project the user chose, named
`builder-browser-instructions.txt`, and tell them where it is. Build it from the answers
they already gave: their name, role, tone and language, then the few habits that work with
no files at all, written in the second person. Keep it short and specific to them, not a
copy of the protocol. `PREFERENCES.txt` in the kit is the longer reference to draw from;
what you hand the user is the short personalised version of it.

Be straight about the limits. A custom-instructions field holds a limited amount of text,
and how much differs by vendor and changes: do not paste pages into one, and do not state
a character limit you have not checked in that vendor's current documentation. Say that a
plain browser assistant cannot read or write their project, so anything it produces comes
back by hand, and that pasting it into the settings is theirs to do. If the user has
connected that assistant to their files, for example through GitHub or a cloud drive, say
that it may be able to keep the notes too, and that this depends on the connection and is
not something the kit sets up or has tested. On no, skip this and do
not raise it again.
