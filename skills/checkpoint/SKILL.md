---
name: checkpoint
description: Save a Builder task's exact resume state in its project files when a task is done or still in flight, then continue without closing the task. Run it on your own initiative, not only when asked.
---

# checkpoint

Use the project's memory files so the next session can retrieve the handoff.

**Do this without being asked, before you report.** Before any reply that reports a
finished task, a change you made, or a stop, run this checkpoint, then end that reply with
one line: `checkpoint saved`. While a long task is in flight, run it after any edit that
changes behaviour and before the assistant shortens its own context. The user should
never have to remember to end a session for their work to be recorded, so do not wait for
session-end and do not wait to be told.
Before writing any project record, confirm you are still in the registered project
checked at session start: this folder's `docs/STATUS.md` Project root names this folder
(or reads `any clone of this repository`). If not, write nothing yet; follow the Builder
protocol's location check and write gate, naming the project and this folder.

1. Capture the project id and root, the current task, owner/session identity, requested
   outcome, decisions, changed files, completed checks, blockers, unfinished work and exact next step.
2. Read docs/STATUS.md again, then update only your own lines in it (the task's state, the
   exact next step, and the `Trail` and `Parked` lines under Now while a side task or a
   parked idea exists) and add a docs/JOURNAL.md entry at the top, marked checkpoint. If
   your instruction file names a projects list, bring this project's `Status` line there
   up to date. Record any unsaved decisions, lessons (always the lesson from a correction
   the user gave) and research in their existing records. Save substantive drafts in
   artifacts/ with draft in the filename. Preserve others' active tasks.
3. Verify the written files before claiming the checkpoint was saved. If a write fails,
   report the failure and provide the exact unsaved handoff in the response.
4. Say it in one line, `checkpoint saved`, at the end of the reply, and continue. Keep the
   task active and the same codename. A checkpoint you took on your own initiative is worth
   one line, not a report.

After the assistant shortens its conversation context (compaction), run the location
check from session-start, then read the saved checkpoint and inspect current files. Account for changes made since
the checkpoint; the saved snapshot may no longer match the files.
