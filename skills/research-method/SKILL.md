---
name: research-method
description: Structured multi-lens research on a question. Decomposes it into expert lenses that genuinely disagree, runs each as a mid-tier subagent producing a plain verdict plus evidence, confidence and sources, then synthesises with an explicit contradiction map, knowledge gaps and a recommendation. Use when the user says "research", "investigate", "compare options", "what does the evidence say", or asks a question needing more than one perspective.
---

# research-method

A method, not a pipeline. It works in a single chat or fanned out to subagents.

## 1. Decompose

Restate the question in one sentence, so any misreading surfaces before the work starts. Then
pick 3 to 5 expert lenses that would genuinely disagree with each other, each written as an
inline persona: its discipline, what it optimises for, and its blind spot.

Weak decomposition is the main failure mode of this whole method. Five lenses that agree tell
you nothing you did not already believe, and they cost the same as five that do not. If your
lenses would all reach the same verdict, you have picked five names for one lens: go back and
find the disciplines that would actually fight about this.

## 2. Run each lens

One mid-tier subagent per lens. Give each the question, its persona, and this required output:

```
LENS: <name>
PLAIN VERDICT: <the answer in two sentences a non-specialist understands>
FINDING: <the technical detail: mechanisms, numbers, caveats>
CONFIDENCE: <high | medium | low>: <why that level>
SOURCES: <specific: title, author or organisation, date, and what it actually says>
GAPS: <what this lens cannot see>
```

Find, then verify. Never cite something you have only seen summarised: open the source and
confirm it says what you are about to claim it says. If you cannot open it, keep the claim but
label it `unverified` so the synthesis can weigh it correctly. A confident sentence with no
checked source behind it is the most damaging thing this method can produce.

## 3. Synthesise

This is the one step that justifies the strongest tier. Produce, in this order:

- Answer: the direct answer, first, in plain language. Not a summary of the process.
- Consensus: what the lenses agree on, and how strongly.
- Contradiction map: each disagreement written as `A says X / B says Y / the real dispute is
  Z`. Never average two positions into a comfortable middle: name the better-supported side
  and say what makes it better supported, or state plainly that the evidence does not settle
  it. An averaged answer hides the disagreement, which was the most useful thing you found.
- Knowledge gaps: what no lens could answer, and what specifically would close each gap.
- Recommendation: what to actually do, and the main risk in doing it.

End with `Conf: <percentage>%` and `Weights: <top factors>`.

## 4. Record it before you report it

Condense the synthesis into one `docs/RESEARCH.md` entry in that file's format (question,
verdict, sources with URL and date marked verified or secondary, confidence, what it informed)
and append it at the top. Write the entry first, then report in chat: research that only ever
existed in a chat window gets bought a second time, by you or by whoever picks this up next.

## Rules

- Sources are named and dated, or they are not sources. "Studies show" is not a source.
- Low-confidence findings stay in the output labelled as such. Never drop one quietly because
  it complicates the story: that is how a research method becomes a persuasion method.
- Resolve conflicts claim by claim, not source by source. A source being better overall does
  not make it right on this particular point.
- Web access is confirmation-gated: use the WebFetch or WebSearch tool, expect a prompt, and
  accept a denial as the answer. Never fetch via a shell command, and never trigger a paid data
  pull without a fresh explicit OK at that moment.

Write the output in the user's configured language, keeping the field labels above (LENS,
PLAIN VERDICT, FINDING, CONFIDENCE, SOURCES, GAPS) as they are so the format stays parseable.
