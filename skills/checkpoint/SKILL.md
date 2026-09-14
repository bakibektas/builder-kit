---
name: checkpoint
description: Save a Builder task's exact resume state before context loss or a long stretch of work, then continue. Uses the project's selected file or Collective backend without closing the task.
---

# checkpoint

Use the project's declared backend; an outage does not change it.

1. Capture the current task, owner/session identity, requested outcome, decisions,
   changed files, completed checks, blockers, unfinished work and exact next step.
2. **Files:** update STATUS and prepend a JOURNAL entry tagged checkpoint. Record any
   uncaptured decisions, lessons and research in their existing records. Save substantive
   drafts in artifacts/ with draft in the filename. Preserve others' active tasks.
3. **Collective:** call agent_checkpoint_session with the real session ID, absolute repo,
   summary and handoff fields supported by the live schema. Save other records through
   their MCP tools. Inspect results before claiming they persisted. If unavailable, report
   the failure and the unsaved handoff in the response; do not create file-memory mirrors.
4. Briefly state what was saved and continue. Keep the task active and the same codename.

After compaction, fetch/read the authoritative checkpoint and inspect current files.
Reconcile intervening changes rather than assuming a snapshot outranks newer evidence.
