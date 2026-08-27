---
name: next-task
description: Pick and start the highest-priority task from docs/STATUS.md. Cleans orphaned in-progress work first, checks the record for prior art, plans subtasks, and fans out genuinely independent work to explicitly tiered subagents. Use when the user says "next-task", "what's next", "next", "pick up a task", or asks what to work on.
---

# next-task

## Steps

1. Clean before you take. Read `docs/STATUS.md`. Any task at `doing` is an orphan from a
   session that ended badly: finish it if it is nearly done, otherwise return it to `todo`
   with a note. Never start new work while an orphan sits open. Report what you cleaned.
2. Pick one. Lowest priority number wins: P0 before P1 before P2. Within a tier, prefer the
   task that unblocks other tasks, then the one closest to the current `Focus`. Skip anything
   marked `blocked:` unless the blocker has demonstrably cleared.
3. Check the record. Search `docs/LESSONS.md`, `docs/DECISIONS.md` and `docs/RESEARCH.md` for
   the task's key terms. Do not repeat a logged mistake, reopen a settled decision, or research
   a question that is already answered.
4. Confirm the why. State the task, its priority and why it is the right one, in two lines. If
   the project's stated focus does not justify it, ask the user before starting.
5. Plan it. Break it into 3 to 6 concrete subtasks. Keep the plan in the reply, not in a new
   file. Planning may use the strongest tier; everything after this point runs on the mid tier.
6. Blast radius. If the task changes something that already exists (a script, prefab,
   component, template or document section), search for everything that references it first
   and state what could break. Re-check the scope before saving or committing.
7. Mark it. Set the task to `doing` in `docs/STATUS.md` as you begin, and close it before
   session end. `doing` may never survive a session boundary.

## Swarm discipline

Fan out when the work genuinely splits; stay sequential when it does not. Fanning out coupled
work costs more than doing it in order.

- Split only on genuine independence. Two agents on one file is a merge conflict you created
  on purpose. If two subtasks touch the same file, they are one subtask.
- Give every agent an explicit tier in the spawn call: mid tier for substantive work, light
  tier for mechanical sweeps. Never let an agent inherit a tier by default.
- Give every agent one deliverable, the exact paths it may touch, and the acceptance condition
  that tells it when it is done.
- Agents cannot see each other's work and cannot ask each other questions. Anything shared
  between them has to be in the spawn prompt.
- Verify the integration yourself when they return: read the seams where their outputs meet,
  not just each output alone. Parallel work is not done until it has been joined and checked.

## Report format

Written in the user's configured language:

- Picked: task, priority, why this one.
- Cleaned: orphans returned to `todo`, or "none".
- Prior art: anything relevant found in lessons or decisions, or "none".
- Plan: the numbered subtasks.
- Parallel: what runs concurrently and on which tier, or "sequential".
- Blast radius: what an existing thing this touches could break, or "nothing existing".
- Blocked: anything needed from the user before starting.
