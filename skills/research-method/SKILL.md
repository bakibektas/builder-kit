---
name: research-method
description: Investigate a question through distinct expert lenses, verify primary evidence, and synthesize disagreements and knowledge gaps. Use for research or comparisons that benefit from multiple perspectives; supports inline work or authorized delegation.
---

# research-method

A method, not a pipeline. It works in a single chat or fanned out to subagents.

Search docs/RESEARCH.md for existing findings before doing the research again.
The user's request and host permissions govern scope; this skill does not authorize
additional workers, paid data pulls or publication.

## 1. Decompose

Restate the question in one sentence, so any misreading surfaces before the work starts. Then
pick 3 to 5 expert lenses that would genuinely disagree with each other, each written as an
inline persona: its discipline, what it optimises for, and its blind spot.

Weak decomposition is the main failure mode of this whole method. Five lenses that agree tell
you nothing you did not already believe, and they cost the same as five that do not. If your
lenses would all reach the same verdict, you have picked five names for one lens: go back and
find the disciplines that would actually fight about this.

## 2. Run each lens

Work through the lenses inline unless authorized, useful delegation is available. For
delegation, select an available suitable model and give each worker a bounded task and
ownership scope. Use the delegation tools available in the current host.
For each lens produce:

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

Use an available model suited to the reasoning required. Produce, in this order:

- Answer: the direct answer, first, in plain language. Not a summary of the process.
- Consensus: what the lenses agree on, and how strongly.
- Contradiction map: each disagreement written as `A says X / B says Y / the real dispute is
  Z`. Never average two positions into a comfortable middle: name the better-supported side
  and say what makes it better supported, or state plainly that the evidence does not settle
  it. An averaged answer hides the disagreement, which was the most useful thing you found.
- Knowledge gaps: what no lens could answer, and what specifically would close each gap.
- Recommendation: what to actually do, and the main risk in doing it.

Explain confidence using the evidence and remaining gaps; numerical confidence is optional.

## 4. Record it before you report it

Prepend a `docs/RESEARCH.md` entry using its format and save a substantive
deliverable in `artifacts/`. Verify the written files before reporting success.
Record the question, verdict, URLs, verification
dates, uncertainty and what the finding informed. Report any persistence failure honestly.

## Rules

- Sources are named and dated, or they are not sources. "Studies show" is not a source.
- Low-confidence findings stay in the output labelled as such. Never drop one quietly because
  it complicates the story: that is how a research method becomes a persuasion method.
- Resolve conflicts claim by claim, not source by source. A source being better overall does
  not make it right on this particular point.
- Use the host's available research tools and configured permissions. No particular Claude
  tool name or confirmation prompt is assumed. Respect denials and obtain any missing
  authorization before a metered data pull.

Write the output in the user's configured language, keeping the field labels above (LENS,
PLAIN VERDICT, FINDING, CONFIDENCE, SOURCES, GAPS) as they are so the format stays parseable.
