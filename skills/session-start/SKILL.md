---
name: session-start
description: Restore a Builder project's context and session identity from its project files. Use at the start of a working session or when asked where work left off.
---

# session-start

Read the installed Builder protocol and the project's instructions for this assistant.
The user's existing task authorization remains valid during this startup workflow.

1. Retain your codename when resuming; otherwise announce a two-word codename.
   Determine the project root and read its instructions before creating files.
2. Create only missing memory records in an authorized project.
   Read docs/STATUS.md in full and only the latest docs/JOURNAL.md entry. Search
   docs/DECISIONS.md, docs/LESSONS.md and docs/RESEARCH.md for the current task's keywords.
   Codex uses project AGENTS.md; Claude uses CLAUDE.md (which may point to the same
   AGENTS.md). Preserve existing instructions.
3. Inspect relevant task ownership and changed files. An in-progress task alone is not
   evidence of abandonment. Leave active owners alone; reconcile only your own work or
   work demonstrably abandoned and authorized for takeover.
4. Report codename, loaded sources, last checkpoint, blockers and next action.
   Record the task and owner in STATUS before edits. Continue an already requested task; if the user
   asked only for orientation, report the recommendation without inventing new work.

After the assistant shortens its conversation context (compaction), read the saved
checkpoint and current project records, then continue the same task and codename.
