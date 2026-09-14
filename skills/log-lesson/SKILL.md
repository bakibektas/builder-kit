---
name: log-lesson
description: Capture a correction, wrong turn or reusable discovery with a concrete prevention rule in the project's selected memory backend. Use when asked to remember a lesson or after a meaningful correction.
---

# log-lesson

A lesson changes future behavior. Record it while the particulars are still available.

1. Search related lessons first: docs/LESSONS.md for files mode, the available lesson
   search/list tools for Collective. Merge or supersede duplicates where supported.
2. Record context, what failed, what worked, a specific mitigation, date and useful tags.
   In files mode prepend an entry using the file's schema. In Collective mode use
   agent_log_lesson with the absolute repo and supported fields; inspect the result.
   Do not create a file-memory fallback if the service fails.
3. Name the trigger and action. "Be more careful" is not a mitigation. Keep it scoped to
   the actual evidence; a one-off preference does not become a universal prohibition.
4. Promote recurring, broadly applicable lessons to concise standing rules. Use
   agent_upsert_rule for managed governance, with real audience and role_scope fields.
   For standalone projects use the canonical project instruction file. Archive superseded
   file lessons without losing their history; keep the live record focused.
5. Briefly report the mitigation and whether it was successfully saved, then continue.
