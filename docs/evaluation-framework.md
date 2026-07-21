# Evaluation Framework

This describes how essays are evaluated, without exposing the underlying prompt engineering or the specific rule thresholds used in production. See [prompt-architecture.md](prompt-architecture.md) for why.

## The core unit: Cause → Behaviour → Result

Every accepted line of reasoning in an IGCSE Economics answer has three parts:

- **Cause** — the trigger stated in the question or introduced by the student (e.g. "government increases spending")
- **Behaviour** — what an actual economic actor (a firm, a consumer, a worker, the government) *does* in response
- **Result** — the economic outcome that follows

The most common reason students lose marks isn't missing knowledge — it's skipping the middle step. "Government spending increases → GDP rises" states a cause and a result, but never says what anyone actually *did* in between. The diagnosis engine's main job is finding exactly where that middle step is missing, weak, or only implied, and pointing to it with a quote from the student's own answer, not a generic comment.

## Why Behaviour matters

Students skip the Behaviour step for an understandable reason: it's the step that requires naming a specific actor and a specific action, rather than just stating what obviously happened next. "Government spending increases → GDP rises" reads as a complete thought because the ending is correct — but it never says who did what in between, which is exactly the part that shows whether a student understands the mechanism or has just memorised the outcome.

In practice, well-implied behaviour is often credited by examiners — if the missing step is obvious enough, the meaning still comes through on a single read. That's a reasonable standard for marking one exam script once. It's a poor standard to train toward: a student who only ever writes the implied version never has to prove they know the mechanism. Requiring it to be explicit removes the benefit of the doubt and surfaces the gap immediately, instead of letting it hide behind a plausible-sounding sentence.

Behaviour is also the hardest part to identify using simple keyword matching, because it is defined by the relationship between actions rather than by individual words.

## Two ways of reading the same answer

Reading an answer as a single exam script and reading it as a training sample lead to different judgements about the exact same sentence, for the reason above. So every answer is scored twice:

- **Cambridge Score** — a realistic exam-reality estimate, where a well-implied action is often still credited
- **A\* Strict Score** — a stricter standard that requires the behaviour to be explicit

Where the two scores diverge, that gap *is* the diagnosis — it shows a student exactly what separates "passing" from "top band," instead of just a single number.

## Command-word-specific structure

Explain, Analyse, and Discuss are marked differently, because Cambridge weights them differently:

- **Explain** questions need two independent reasons, each carried through to a developed point. One strong chain, repeated in different words, does not substitute for two separate reasons.
- **Analyse** questions are scored on distinct causal chains, not on volume — repeating the same mechanism in different wording doesn't add marks.
- **Discuss** questions are marked by level, not by counting points. An answer that only argues one side of the question is capped, no matter how well-developed that one side is. Reaching the top band requires both sides to be genuinely developed, not just mentioned in passing.

## Student level diagnosis

Beyond a mark, every answer is classified against what a D, C, B, or A-level response typically looks like — based on whether behaviour is present and explicit, whether chains are complete, and (for Discuss questions) whether both sides of the argument are actually developed. This is paired with one specific, prioritised next step, not a generic "write more" or "add more detail."

## What's not here

The specific rule text, thresholds, and edge-case handling that implement this framework are not published — see [prompt-architecture.md](prompt-architecture.md).

