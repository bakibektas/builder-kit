---
name: checkpoint
description: Mid-session save. Writes the current state into docs/STATUS.md, prepends a checkpoint journal entry, files decisions, lessons and research not yet recorded, and saves drafts into artifacts/, then carries on working. Use when the user says "checkpoint", when the conversation is running out of room, when a compaction is imminent, or before a long or risky stretch of work.
---

# checkpoint

A session can lose its context without warning: the conversation fills up, a compaction
rewrites it into a summary, or a long stretch of work goes wrong halfway through. This ritual
writes the state down while it is still known. It is not session-end: nothing is closed, no
task changes status, and you go straight back to work when the writing is done.

## When to run it

- The user says "checkpoint".
- The conversation is visibly running out of room.
- A compaction or summarization is imminent.
- A long or risky stretch of work is about to start.

## Steps

1. Overwrite `docs/STATUS.md` with the precise current state: what is in flight, what is
   already done but not yet recorded anywhere, and the exact next step. Write the next step
   with enough detail that a fresh session holding none of this context could continue from
   the file without asking a question.
2. Prepend one entry to `docs/JOURNAL.md`, tagged `(checkpoint)` alongside the model tier and
   your codename, or directly after the date. Same five-line shape as any other entry.
3. Append anything from this session that has not yet reached its file: decisions to
   `docs/DECISIONS.md`, lessons to `docs/LESSONS.md`, research findings with their sources and
   dates to `docs/RESEARCH.md`.
4. Save any in-progress deliverable draft into `artifacts/`, marked as a draft in its filename:
   `YYYY-MM-DD-<short-title>-draft.md`. A draft on disk survives a compaction; a draft that
   exists only in the conversation does not.
5. Report in two lines what was saved, then continue the work you were doing. Do not close
   tasks, do not write a final report, do not sign off. Keep the codename you opened with.

After any compaction, the first act is to re-read `docs/STATUS.md`. Trust that file over the
summary you were handed: it was written while the detail was still there.
