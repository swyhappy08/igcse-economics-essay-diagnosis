# Prompt Architecture

This document describes the evaluation pipeline at a high level.

It intentionally does not include the production system prompt, the specific rule text, or the proprietary marking thresholds — those are the actual product, refined over many iterations, and are not published here.

## Why a language model, not rules or keyword matching

Traditional automated marking tools tend to rely on keyword matching — checking whether an answer contains the "right" terms. That approach can't distinguish a term used correctly inside a complete causal chain from the same term dropped into an unconnected sentence. This project instead reconstructs the student's actual line of reasoning before judging it. A large language model makes that possible: it can recognise an incomplete or broken causal chain, not just match vocabulary against a list.

## Pipeline

1. **Question type detection** — identify whether the question is Explain, Analyse, or Discuss, and what it's actually asking about.
2. **Knowledge check** — confirm the economics terms and concepts used are correct.
3. **Chain extraction** — pull out every Cause → Behaviour → Result unit in the answer, and flag where the Behaviour step is missing, weak, or only implied.
4. **Dual-layer scoring** — score the answer twice (see [evaluation-framework.md](evaluation-framework.md)): once as a realistic exam mark, once against a stricter standard.
5. **Mistake identification** — every issue raised has to quote the exact sentence it came from and explain, in terms of the marking criteria, why it costs marks. No unattributed criticism.
6. **Student level diagnosis** — classify the answer's overall level and give one specific, prioritised next step.
7. **Output** — a structured report, not free-text commentary.

### Why chains are extracted before the answer is scored

Reasoning is reconstructed before it's evaluated, not after. Scoring first and justifying the score afterward risks rewarding a conclusion that sounds correct but isn't actually supported by complete economic logic. Extracting the chain first — step 3, before step 4 — makes that gap visible before a mark gets assigned to it.

## How this was built

The framework didn't start this way. It went through multiple rounds of debugging against real student essays — finding cases where the model was over-crediting vague answers, under-crediting realistically-marked ones, or applying Discuss's balance requirement inconsistently — and tightening the rules each time. That process started in earnest around March 2026 and is ongoing. Specific findings are being written up incrementally as the project develops.

## Why no production prompt here

Publishing the full prompt would mean publishing the actual marking logic — the part that took the most iteration and real student data to get right, and the part this project's teaching and diagnosis work depends on. What's published instead is the thinking behind it: the pipeline, the reasoning framework, and (as they're written up) the real problems found and how they were fixed.

