---
name: log-lesson
description: Record a lesson in docs/LESSONS.md. Use immediately after the user corrects you, after a mistake or wrong turn, after something works better than expected, or when the user says "log lesson", "remember this", "note that for next time".
---

# log-lesson

Automatic working memory already catches things loosely. This is the deliberate act: recording
a lesson in `docs/LESSONS.md`, which is committed, shared and inherited by every session that
follows. A lesson is a rule that changes future behaviour. If it would not change what someone
does next time, it is not a lesson and does not belong here.

## When to write one

- The user corrects you. Every correction becomes a lesson, without exception. Capture it
  before continuing the work, not at session end: by then the specifics have gone, and the
  specifics are the whole value. A correction is the highest-signal input this project gets,
  because unlike any instruction written in advance it was earned against reality.
- You went down a wrong path and had to back out.
- Something worked notably better than the obvious approach.
- You discovered a constraint that was written down nowhere.

## Steps

1. Search `docs/LESSONS.md` for the key terms first. If a near-duplicate exists, merge into it
   and sharpen its mitigation rather than adding a second entry.
2. Otherwise append a new entry at the top of the file, in the user's configured language:

```
### <short imperative title>: YYYY-MM-DD
- **Context:** <the situation, one line>
- **What failed:** <what went wrong, or "n/a">
- **What worked:** <what actually helped>
- **Mitigation:** <the rule to follow next time: must be actionable>
- **Tags:** <comma, separated, tags>
```

3. If the lesson has hardened into a standing rule (it has come up more than once, or it
   applies to every task in this project), add it as a one-line entry in the project's
   `CLAUDE.md` as well. That file is read at the start of every session, so it holds a handful
   of rules and never a list.
4. Tell the user in one line that you logged it, and what the mitigation is.

## Quality bar

- The title is an instruction, not a topic: "Agree the frame before synthesising", not
  "Synthesis issues".
- The mitigation must be followable by a future session that has none of this context. "Be
  more careful" is not a mitigation; it names no action. Ask what you would have needed to
  read, at the start, to have got it right, and write that.
- Name the trigger. A future session has to recognise the situation before it can apply the
  rule, so say when the rule fires, not only what it says.
- Refer to people by role, never by name.
- Never archive this file. It is kept small by merging duplicates, not by moving entries out.
