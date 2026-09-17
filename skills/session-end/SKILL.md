---
name: session-end
description: Close owned Builder tasks, save deliverables and lessons, and write a verified handoff in the project's files. Use when wrapping up a working session.
---

# session-end

Use the project's memory files. The user controls the scope; this ritual
does not itself authorize publishing, pushing or deleting files.
This is the fuller close, not the first time anything is written: checkpoints have already
saved the work as it went, so a session that never reaches this skill still leaves a
usable handoff on disk.
Before writing any project record, confirm you are still in the registered project
checked at session start: this folder's `docs/STATUS.md` Project root names this folder
(or reads `any clone of this repository`). If not, write nothing yet; follow the Builder
protocol's location check and write gate, naming the project and this folder.

1. Update only tasks you own. Mark verified work done, blocked work with its actual
   reason, and unfinished work todo with an exact resume step. Preserve other owners.
2. Update docs/STATUS.md and add a docs/JOURNAL.md entry at the top (date/model/codename plus Summary,
   Decisions, Blockers, Files/assets, Next), and record relevant decisions and research.
   Save deliverables in artifacts/. Archive older entries without losing them.
3. Review corrections and useful discoveries. Search and merge lessons in docs/LESSONS.md
   with specific actions to prevent repeat mistakes. Add proven recurring rules to the
   shared project instruction file (AGENTS.md in the kit's template), keeping one copy
   for both assistants.
4. Re-read saved updates. If writing failed, report what was not saved and include the
   intended handoff in the response. A promise to save is not proof that a file was saved.
5. Inspect the diff and validation results. If a commit is in scope, add new files by
   explicit path. For exclusively owned files use `git commit -m "<message>" -- <paths>`.
   If a file also contains someone else's edits, stage only your changed sections and
   commit without file paths at the end of the command. Use a distinct
   committer and a final `Codename: <Two Words>` trailer. Recheck the resulting commit.
6. Clean only your own known scratch files within verified project paths when appropriate.
   Never sweep a shared .tmp directory or another contributor's edits.

Report `Project: <id> at <root>`, what was delivered, where it lives, what was checked, what you
delegated, limitations, any files that could not be saved, and what remains. Distinguish local edits, committed work and published
work. Do not call the task complete merely because the session is ending.
