---
name: session-end
description: End-of-session wrap-up. Closes in-progress tasks, updates docs/STATUS.md, prepends a journal entry, reviews every correction from the session and promotes the lessons, then gives a structured Done/Files/Blocked/Next report. Use when the user says "session-end", "close session", "wrap up", "sign off", or when a working session is ending.
---

# session-end

Nothing is remembered unless it is written. Do the writing before the final reply, not after.

## Steps

1. Close the tasks. In `docs/STATUS.md`, update every task you touched. Nothing may remain at
   `doing`: mark it `done <date>`, or return it to `todo` with a short note on exactly where
   it stopped. This rule has no exceptions.
2. Overwrite `docs/STATUS.md`. Rewrite `Focus`, `Next action` and `Blocked on` so they
   describe the present. Drop tasks completed more than a week ago: the journal has them. Keep
   the file under ~40 lines.
3. Save the deliverables. Any document produced for the user this session that is not already
   in `artifacts/` is written there now as `YYYY-MM-DD-<short-title>.md`, and the journal entry
   below names it. A deliverable that exists only in the conversation is gone when the
   conversation closes.
4. Prepend to `docs/JOURNAL.md`. One entry above the others, five lines: date with the model
   tier and your codename / Summary / Decisions / Blockers / Files-assets / Next.
5. Append to `docs/DECISIONS.md` if any decision changed direction or closed off an option.
   One line, WHY mandatory, attributed to your codename. Skip routine choices. Append to
   `docs/RESEARCH.md` too if any research happened this session and is not already recorded
   there: one entry in that file's format, sources with a URL and a date.
6. Review the corrections. Go back through the session and list every point where the user
   corrected you, including ones you already logged mid-session. For each, confirm a lesson
   exists in `docs/LESSONS.md` and that its mitigation could be followed by a future session
   holding none of this context. Rewrite any mitigation that reads like "be more careful". A
   correction that never got written down is the most expensive thing you can leave behind.
7. Promote the lessons. Capture the non-obvious insights too: a wrong path you had to back out
   of, something that worked notably better than the obvious approach, a constraint you
   discovered that was written down nowhere. Merge into a near-duplicate entry rather than
   adding a second one. If a lesson has hardened into a standing rule (it has come up more than
   once, or it applies to every task in this project), add it as a one-line entry in the
   project's `CLAUDE.md` as well: that file is read at the start of every session, so it holds
   a handful of rules and never a list.
8. Check the journal cap. If `docs/JOURNAL.md` now exceeds ~150 lines, cut the oldest entries
   and paste them into `docs/journal-archive.md`. Move the content; never delete a file, and
   never drop an entry.
9. Tidy. Remove the scratch files you created inside `.tmp/`. Leave the project clean.
10. Commit, if this is a repository. Use an explicit pathspec:
    `git commit -- docs/STATUS.md docs/JOURNAL.md <other files> -m "<message>"`. Never
    `git add -A`, never `git add .`. Show the user the exact command rather than assuming they
    want it run.

## Final report format

Written in the user's configured language:

- Done: what actually shipped. Bullets, no padding.
- Files/assets: everything created or changed, with paths.
- Lessons: what went into `docs/LESSONS.md` this session, or "none".
- Blocked: what is waiting on the user or a third party, or "nothing".
- Next: the single recommended next action for the next session.

End with `Conf: <percentage>%` and `Weights: <top factors>` if the session involved analysis
or judgement.
