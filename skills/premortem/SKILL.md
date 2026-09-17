---
name: premortem
description: Test a plan by imagining how it could fail, identifying warning signs and responses, and deciding when to stop. Use for a premortem, "what could go wrong", "wargame this", or before a costly or hard-to-reverse action.
---

# premortem

Assume the plan has already failed, then work out how. Confidence in a plan is not evidence
about the plan. Output the structure below, not an essay.

Scale this to the stakes. The user's scope and existing authorization remain in force;
a proposed response to a failure is not permission to execute it. Save a substantive analysis
in artifacts/ and reference it in the project journal.
Before writing any project record, confirm you are still in the registered project
checked at session start: this folder's `docs/STATUS.md` Project root names this folder
(or reads `any clone of this repository`). If not, write nothing yet; follow the Builder
protocol's location check and write gate, naming the project and this folder.

## 1. Frame

- Mission: what success concretely looks like, in one sentence.
- Stakes: what is lost if this goes wrong.
- Reversibility: whether this can be undone and at what cost. If it cannot be undone, say so
  in plain words here rather than burying it in a later section.

## 2. Actions and warning signs

One block per move, in the order you will make them. This is the core of the exercise.

```
Move <n>: <what you do>
- Expected signal: <what you should observe if it is working>
- Warning sign: <the observation that means it is going wrong>
- Response: <what you do instead, immediately>
```

Rules for this section:

- The expected signal must be observable, not a feeling: "three of five reviewers approve",
  not "it goes well". If you cannot say how you would see it, you cannot claim it.
- Every move needs a warning sign that tells you it may be failing.
- A response must be within existing authorization. If it needs someone else's decision,
  obtain that decision before starting or stop at that point and request it.

## 3. What you cannot control or observe

What you cannot control or observe, and what you are assuming about each. This is where the
surprises come from, so be honest about how much of the plan rests here.

```
Unknown or external factor: <name>
- Limit: <why you cannot see it or control it>
- Working assumption: <what you are assuming, stated plainly>
- If wrong: <what changes, and what you do about it>
```

## 4. When to proceed or stop

- Success: the specific conditions that mean stop, it worked.
- Abort: the specific conditions that mean stop, cut losses. Write these before starting:
  criteria written mid-crisis are always too generous, because by then you are counting what
  you have already spent.
- Point of no return: the action after which the result cannot be undone. Name it, and say
  what you want confirmed before you cross it.

## 5. Verdict

Two lines: go, go-with-changes, or no-go, and the single biggest risk in one sentence. For
go-with-changes, list the changes as numbered edits to the moves above, not as general advice.

Explain confidence and its main evidence, writing in the user's configured language.
Numerical confidence is optional; distinguish observations from assumptions.
