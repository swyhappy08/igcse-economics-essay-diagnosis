# IGCSE Economics Essay Diagnosis

An AI-powered essay diagnosis system for IGCSE Economics students. Instead of only estimating a mark, it identifies the specific reasoning gaps — missing economic mechanisms, incomplete cause-effect chains, one-sided arguments — that are actually costing marks, and explains why in terms tied to the marking criteria.

A project by Econ by Ms Soon.

## Current Status

- ✅ Evaluation framework designed
- ✅ Prompt architecture established
- 🔄 Collecting real student essays
- 🔄 Human review & prompt refinement
- ⏳ Web application (planned)

## Why this exists

Most students don't lose marks because they lack economics knowledge. They lose marks because their reasoning stops one step short of what the mark scheme actually rewards — an explanation jumps from cause straight to result, a chain never names what a firm, consumer, worker, or government actually *does*, or a Discuss answer argues one side well and never develops the other.

This project started as a marking framework used in real IGCSE Economics tutoring. It gradually evolved into an AI-assisted diagnosis system developed through continuous human review and prompt refinement, after repeated prompt refinement exposed recurring reasoning patterns across student essays — refined through many rounds of real tutoring sessions, prompt debugging, and real student essays.

## How it works (high level)

- [docs/evaluation-framework.md](docs/evaluation-framework.md) — the marking logic itself: what counts as a developed answer, how scoring works, how command words (Explain/Analyse/Discuss) are treated differently.
- [docs/prompt-architecture.md](docs/prompt-architecture.md) — the evaluation pipeline, why a language model rather than rules or keyword matching, and how it was built.
- [docs/product-principles.md](docs/product-principles.md) — the principles behind the design.

The production system prompt and specific rule thresholds are not published here — see [docs/prompt-architecture.md](docs/prompt-architecture.md) for why.

## Examples

Coming soon — real, anonymised student essays will be added here once reviewed and approved for publication.

---

The objective is not to automate marking. The objective is to make expert-quality essay diagnosis scalable while keeping the reasoning behind it transparent.

This is a public build log, not a finished product. It gets updated as real usage happens, not on a release schedule.
