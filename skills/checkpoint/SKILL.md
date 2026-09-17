---
name: checkpoint
description: Save a Builder task's exact resume state in its project files when a task is done or still in flight, then continue without closing the task. Run it on your own initiative, not only when asked.
---

# checkpoint

Use the project's memory files so the next session can retrieve the handoff.

**Do this without being asked.** Checkpoint when a task is finished, and again while a
long one is still in flight: after a step that changed something, before a risky or
wide-reaching change, and before the assistant shortens its own context. The user should
never have to remember to end a session for their work to be recorded, so do not wait for
session-end and do not wait to be told.
Before writing any project record, confirm you are still in the registered project
checked at session start: this folder's `docs/STATUS.md` Project root names this folder
(or reads `any clone of this repository`). If not, write nothing yet; follow the Builder
protocol's location check and write gate, naming the project and this folder.

1. Capture the project id and root, the current task, owner/session identity, requested
   outcome, decisions, changed files, completed checks, blockers, unfinished work and exact next step.
2. Update docs/STATUS.md and add a docs/JOURNAL.md entry at the top, marked checkpoint.
   Record any unsaved decisions, lessons and research in their existing records. Save substantive
   drafts in artifacts/ with draft in the filename. Preserve others' active tasks.
3. Verify the written files before claiming the checkpoint was saved. If a write fails,
   report the failure and provide the exact unsaved handoff in the response.
4. Briefly state what was saved, in one line, starting with `Project: <id> at <root>`,
   and continue. Keep the task active and the same codename. A checkpoint you took on your
   own initiative is worth one line, not a report.

After the assistant shortens its conversation context (compaction), run the location
check from session-start, then read the saved checkpoint and inspect current files. Account for changes made since
the checkpoint; the saved snapshot may no longer match the files.
