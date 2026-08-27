---
name: session-start
description: Start-of-session check-in. Announces the session codename, verifies the docs/ convention is deployed (scaffolding it in a fresh project), reads docs/STATUS.md and the latest journal entry, cleans orphaned in-progress tasks, and recommends the next action. Use when the user says "session-start", "start session", "check in", "where were we", or at the beginning of any working session on a project.
---

# session-start

Run this before any other work. Reading and reporting rather than judgement: a light or mid
tier is enough.

## Steps

0. Announce the codename. Pick a distinctive two-word codename ("Iron Moose", "Phase Forge",
   "Quiet Anvil") and open your reply with it. Keep it for the whole session, and sign every
   journal entry, decision entry and commit message with it. Do not reuse the codename on the
   most recent journal entry: a new session takes a new name, and that is what makes the
   record attributable afterwards.
1. Setup check. If the project `CLAUDE.md` or any of the five `docs/` files is missing, this
   is a fresh project: create the missing files now, with their instruction headers and empty
   skeletons, as defined in section 3 of the working protocol. Then read `docs/STATUS.md` in
   full.
2. Read the top entry of `docs/JOURNAL.md` only. Not the whole file. Take its `Next:` line and
   any unresolved `Blockers:` as your starting picture.
3. Search, do not read, the other three. If the task ahead is already named, search
   `docs/LESSONS.md`, `docs/DECISIONS.md` and `docs/RESEARCH.md` for its keywords, so you
   neither repeat a logged mistake, reopen a settled question, nor redo settled research.
   If no task is named yet, skip this step.
4. Clean orphans. Any task at `doing` is an orphan from a session that ended badly. Return
   each to `todo` with `(returned from doing on <date>)` and say what you changed.
5. Check the blockers. For each `blocked:` task, judge whether the blocker has since cleared.
   Say which are still genuinely blocked.
6. Check for half-finished work. Look at the files or assets named in the last journal entry
   and flag anything that looks abandoned mid-edit.

## Report back

Under 15 lines, written in the user's configured language:

- Codename: the two words you are working under this session.
- Scaffolded: the files you created if this was a fresh project; omit the line otherwise.
- Where we left off: last session's summary in one line, with its date.
- Open: the current P0 and P1 tasks, one line each.
- Orphans cleaned: what you returned to `todo`, or "none".
- Blocked: anything waiting on the user or a third party, or "nothing".
- Recommended next: one concrete action, and why that one.

Then stop and wait. Do not start work until the user confirms: they may have a priority that
never reached the file.
