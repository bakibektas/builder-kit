---
name: premortem
description: Stress-test a plan before committing to it. Produces move-by-move actions with expected signals, fork triggers and counteractions, a ledger of blocked variables with working assumptions, explicit success and abort criteria, the point of no return, and a go / go-with-changes / no-go verdict. Use when the user says "premortem", "wargame this", "stress-test this plan", "what could go wrong", or before any high-stakes or hard-to-reverse move.
---

# premortem

Assume the plan has already failed, then work out how. Confidence in a plan is not evidence
about the plan. Output the structure below, not an essay.

## 1. Frame

- Mission: what success concretely looks like, in one sentence.
- Stakes: what is lost if this goes wrong.
- Reversibility: whether this can be undone and at what cost. If it cannot be undone, say so
  in plain words here rather than burying it in a later section.

## 2. The moves

One block per move, in the order you will make them. This is the core of the exercise.

```
Move <n>: <what you do>
- Expected signal: <what you should observe if it is working>
- Fork trigger: <the observation that means it is going wrong>
- Counteraction: <what you do instead, immediately>
```

Rules for this section:

- The expected signal must be observable, not a feeling: "three of five reviewers approve",
  not "it goes well". If you cannot say how you would see it, you cannot claim it.
- Every move needs a fork trigger. A move with no failure mode has not been thought about yet.
- A counteraction must be executable without stopping to ask permission mid-flight. If it
  needs someone else's decision first, secure that decision now or make the move an abort point.

## 3. Blocked variables

What you cannot control or observe, and what you are assuming about each. This is where the
surprises come from, so be honest about how much of the plan rests here.

```
Variable: <name>
- Why blocked: <why you cannot see it or control it>
- Working assumption: <what you are assuming, stated plainly>
- If wrong: <what changes, and what you do about it>
```

## 4. Criteria

- Success: the specific conditions that mean stop, it worked.
- Abort: the specific conditions that mean stop, cut losses. Write these before starting:
  criteria written mid-crisis are always too generous, because by then you are counting what
  you have already spent.
- Point of no return: the last move after which abort is no longer possible. Name it, and say
  what you want confirmed before you cross it.

## 5. Verdict

Two lines: go, go-with-changes, or no-go, and the single biggest risk in one sentence. For
go-with-changes, list the changes as numbered edits to the moves above, not as general advice.

End with `Conf: <percentage>%` and `Weights: <top factors>`, writing the whole output in the
user's configured language.
