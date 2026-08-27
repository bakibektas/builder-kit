# INSTALL: instructions for the installing agent

You are the agent installing this kit for the person who opened you in this folder, and what
you are installing is the way of working you should have had all along: a preferences text, a
user-level Builder protocol, a project template of five documents plus an `artifacts/` folder,
and seven session rituals. Announce a distinctive two-word codename before your first reply of
this install and keep it for the whole session, because that is the kit's own ritual and you
start as you mean to go on. Read `README.md`, then `ETHOS.md`, then `global/CLAUDE.md`, then
follow this file in order. Nothing here needs admin rights: every step is a question, a file
copy, or a check.

## 1. Check the environment

1. Identify the operating system and resolve the target folder: on Windows
   `C:\Users\<username>\.claude`, on macOS `~/.claude`. Substitute the real username, and
   create the folder only if it is missing. Change nothing else inside it yet.
2. Run `claude --version`. If it prints a version, continue.
3. If the command is not found, stop the installation. Tell the user Claude Code is not
   present on this machine, name it as the thing to install, and point at the browser-only
   path in `README.md` as the route that works meanwhile. Install nothing yourself.
4. Look for `<claude-folder>/CLAUDE.md` and for `<claude-folder>/builder-protocol.md`. Either
   one already there means this may be an update rather than a first install: go to section 2
   and settle that before anything else.

## 2. Updating an existing installation

An update is not a fresh install, and getting that wrong costs somebody their personalization.
Settle it before you deploy anything.

1. Look first for `<claude-folder>/builder-protocol.md`. If that file exists and carries a
   `Kit version` line, this machine holds an import-style installation, made by the import
   choice in section 4. Such an update replaces that imported file and nothing else, carrying
   its `PERSONALIZE` block forward verbatim as always, and leaves the user's `CLAUDE.md` alone:
   the import line already sits in it. Read `builder-protocol.md` wherever the steps below say
   `CLAUDE.md`, and skip the rest of this classification.
2. Read the target protocol file, `<claude-folder>/CLAUDE.md`. If nothing is there, this is a
   fresh install: continue at section 3.
3. If the file exists and carries a `Kit version` line, this is an update. Note the version it
   states. The version you are installing is the one at the top of this kit's `README.md`.
4. If the file exists without a `Kit version` line, compare its structure with this kit's
   `global/CLAUDE.md`: the `PERSONALIZE` comment markers in section 1 and the five numbered
   section headings are the tell. If they match, treat it as a pre-versioning installation of
   this kit and update it. If they do not match, it is a foreign file: leave the update path
   and handle it under the conflict rules in section 4.

On the update path, use the steps below in place of the interview in section 3, the deploy in
section 5 and the manual step in section 6. Sections 4, 7 and 8 apply as written.

1. Copy the content between the `PERSONALIZE` markers out of the installed file and carry it
   into this kit's `global/CLAUDE.md` verbatim, character for character, before you deploy
   anything. That block is the user's own words and an update never rewrites them.
2. Skip the interview in section 3 entirely, the language question included. Run it only if the
   installed file carries no `PERSONALIZE` block, or the block is empty.
3. Back up before replacing: copy the installed protocol next to itself as
   `<name>.backup-YYYY-MM-DD` using today's date, then write the new file over it. Everything
   outside the `PERSONALIZE` block is replaced by the new version.
4. Replace the deployed ritual folders in `<claude-folder>/skills/` wholesale. They carry no
   personal content, so they need no diff and no question.
5. Touch no project's `docs/` folder. Those five files are the user's own record, and an update
   never edits, replaces or reorders them. Anything a newer version adds, such as `RESEARCH.md`
   or the `artifacts/` folder with its `README.md`, arrives by itself the next time
   `session-start` runs its scaffold check.
6. The preferences text lives in the user's claude.ai settings rather than on this machine, so
   an update leaves it alone. Ask for a re-paste only if the new version changed the shipped
   `PREFERENCES.txt` structure. Version 1.4 did not, so say nothing about it.
7. Report as an update rather than an install: the version that was installed, the version now
   installed, the history entries between the two (they are listed at the end of `README.md`),
   the backup path, the ritual folders replaced, and one line confirming that the user's
   personalization was carried across unchanged.

## 3. Interview the user before deploying anything

Ask these four questions in one message and wait for the answers:

- How should a Builder address you at the start of every reply?
- What is your role, in one or two sentences? Include whether you write code yourself or
  commission and review the work instead.
- What tone do you want? Name what you dislike as well as what you want.
- Which language do you want to work in?

Then write the answers into this folder's own copies, before anything is copied anywhere:

- `PREFERENCES.txt`: replace the four paragraphs between `PERSONALIZE: START` and
  `PERSONALIZE: END`, keeping the same shape, then delete both marker blocks, because this
  text goes into a settings field as it stands.
- `global/CLAUDE.md`, section 1: replace the four bullets between the `PERSONALIZE` comments
  with the same content, leaving the comment markers in place so the user can see later which
  part is theirs to edit.

On language, follow what the kit already says: it governs conversation and the entries a
Builder writes, while file names, commands and the shipped instruction headers stay in
English. If the user works in another language, write their personal block in that language,
as the kit's own example shows. Change nothing outside those two blocks: the rest is the
shared protocol, and it is what makes every Builder alike.

## 4. Check before every copy

Before writing any file to a target location, test whether something is already there. If it
is, show the user what exists now and what this kit would put there (a short diff for a small
file, a summary for a large one), and ask them to choose.

A `<claude-folder>/CLAUDE.md` that is the user's own hand-grown protocol rather than this
kit's is the case worth taking slowly. Offer these four, in this order:

1. Import, and recommend it when what they already have is substantial. Deploy the personalized
   protocol as a separate file, `<claude-folder>/builder-protocol.md`, then append exactly one
   line to the end of their existing `CLAUDE.md`: `@builder-protocol.md`, preceded by one blank
   line and no comment. Spell out what that buys them: everything they wrote stays untouched
   apart from that single appended line, deleting the line uninstalls the Builder rules
   outright, and both instruction sets load together, so if one of their old rules later reads
   as a contradiction of one of ours, the fix is to ask a Builder to reconcile the two. The
   interview in section 3 still runs; its answers fill the `PERSONALIZE` block inside the
   deployed `builder-protocol.md`, never inside their file.
2. Merge, and recommend it when the user wants one unified ruleset. Propose the merged text and
   get it confirmed before writing. Put all of the user's own instructions inside the
   `PERSONALIZE` block of the merged file, because the update procedure in section 2 preserves
   exactly that block and replaces everything outside it.
3. Back up and replace. Copy the existing file next to itself as `<name>.backup-YYYY-MM-DD`
   using today's date, then write the new one over it.
4. Skip. Note it for the install report and move on.

For every other target, offer the last three of those: back up and replace, merge, or skip, on
the same terms. Never delete anything, and never overwrite a file without an answer to that
question.

## 5. Deploy

1. Copy the personalized `global/CLAUDE.md` to `<claude-folder>/CLAUDE.md`. On a machine with
   no `CLAUDE.md` at all, that is all there is to it. If the user chose import in section 4,
   the target is `<claude-folder>/builder-protocol.md` instead, plus the one appended line.
2. Copy the seven ritual folders from `skills/` into `<claude-folder>/skills/`, so the result is
   `<claude-folder>/skills/session-start/SKILL.md` and six siblings. Keep the folder names
   exactly as they are: the folder name is the skill name.
3. Apply section 4 to each of those eight targets separately. A `skills/` folder holding
   unrelated skills is not a conflict; only a same-named ritual folder is. Use ordinary file
   copies, and move nothing out of this kit folder: it stays intact as the reference copy.

## 6. Hand the one manual step to the user

Print the finished `PREFERENCES.txt` text in a clearly marked block, with the marker blocks
already removed, and tell the user in plain terms: paste this into claude.ai under Settings,
personal preferences. This is the one step you cannot do for them, because it lives in their
account rather than on this machine. The CLI ignores that field; the browser reads it.

## 7. Offer project setup

Ask whether to set up a project now. If yes, ask for the project folder, copy the contents of
`project-template/` into it, and fill in the project name where the template asks for it. If
no, tell the user that in any folder without a `docs/` folder the `session-start` ritual
scaffolds the five files itself on first run, so nothing is lost by skipping this.

## 8. Verify and report

Re-read every file you deployed from its target location, not from this folder, confirm the
contents arrived intact and personalized, then print an install report covering every file
deployed with its full target path, everything skipped or backed up with the backup path, the
manual step from section 6 and whether the user has confirmed doing it, and the suggested
first command: open a terminal in a project folder, run `claude`, and say `session-start`.
Sign the report with your codename.

## 9. Rules for you, the installer

Install only what this file names, touch nothing else on this machine, and change no setting
not listed here. Where anything is ambiguous, including which folder is a project and whether
an existing file should go, ask rather than guess: that rule is in the protocol you are
installing.
