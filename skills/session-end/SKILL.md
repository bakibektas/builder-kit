---
name: session-end
description: Close owned Builder tasks, save deliverables and lessons, and write a verified handoff in the project's files. Use when wrapping up a working session.
---

# session-end

Use the project's memory files. The user controls the scope; this ritual
does not itself authorize publishing, pushing or deleting files.

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

Report what was delivered, where it lives, what was checked, limitations, any files that
could not be saved, and what remains. Distinguish local edits, committed work and published
work. Do not call the task complete merely because the session is ending.
