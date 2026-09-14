---
name: checkpoint
description: Save a Builder task's exact resume state in its project files before context loss or a long stretch of work, then continue without closing the task.
---

# checkpoint

Use the project's memory files so the next session can retrieve the handoff.

1. Capture the current task, owner/session identity, requested outcome, decisions,
   changed files, completed checks, blockers, unfinished work and exact next step.
2. Update docs/STATUS.md and add a docs/JOURNAL.md entry at the top, marked checkpoint.
   Record any unsaved decisions, lessons and research in their existing records. Save substantive
   drafts in artifacts/ with draft in the filename. Preserve others' active tasks.
3. Verify the written files before claiming the checkpoint was saved. If a write fails,
   report the failure and provide the exact unsaved handoff in the response.
4. Briefly state what was saved and continue. Keep the task active and the same codename.

After the assistant shortens its conversation context (compaction), read the saved
checkpoint and inspect current files. Account for changes made since the checkpoint;
the saved snapshot may no longer match the files.
