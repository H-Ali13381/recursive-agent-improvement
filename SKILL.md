---
name: recursive-agent-improvement
description: Use when an agent repeatedly fails at a narrow measurable subtask, the user wants a trainable specialist tool instead of more prompting, or the task needs an evaluator, reranker, classifier, detector, verifier, or small PyTorch model exposed to an agent.
---

# Recursive Agent Improvement

## Overview

Build durable agent capabilities by turning repeated LLM failures into narrow, measurable tools. Use the LLM for planning and orchestration; use specialist models or deterministic tools for perception, ranking, scoring, detection, extraction, and verification.

## When to Use

Trigger this skill on any of these signals:

- Repeated LLM failure: the agent keeps making the same bounded mistake despite clearer instructions.
- Tool-over-prompt request: the user asks to add capability through a tool, model, evaluator, scorer, verifier, or skill instead of modifying base model weights.
- Specialist architecture fit: the weak spot looks like classification, ranking, detection, scoring, extraction, calibration, anomaly detection, perception, or consistency checking.
- Measurable artifact exists: inputs, expected outputs, success metrics, and failure cases can be written down before training.
- Agent-control decision: the specialist output would change what the agent does next, such as accept/reject, rerank, abstain, ask for review, retry, or route to another tool.
- Reusable pipeline need: the user wants a template for PyTorch training, hard-negative evaluation, Optuna sweeps, model cards, or JSON tool packaging.

Good user-language triggers include:

- “LLMs are bad at X; can we build a tool for it?”
- “Train a small model/classifier/reranker/evaluator for this agent weakness.”
- “Make the agent verify/score/detect this before claiming success.”
- “Package this neural model as a Hermes tool/MCP/CLI with JSON output.”
- “Create a reusable specialist training pipeline.”

Do not use this when:

- The goal is vague, like “make the LLM smarter generally.” Narrow the failure first.
- A deterministic script, schema, regex, database query, or existing library solves the problem without training.
- There is no realistic way to collect or label data, define a baseline, or evaluate held-out performance.
- The task requires broad open-ended reasoning rather than a bounded specialist judgment.

## Core Pattern

1. Define the recurring agent failure.
2. Specify inputs, outputs, metrics, and baseline.
3. Build or collect data with train/val/test splits.
4. Add hard negatives or adversarial cases.
5. Train or implement the specialist.
6. Evaluate against the baseline and hard cases.
7. Package the result as a JSON-returning tool.
8. Write a skill explaining when to call it and how to interpret output.

## PyTorch Template

Clone the starter pipeline:

```bash
cp -a templates/pytorch-training-pipeline ~/Documents/my-specialist-tool
cd ~/Documents/my-specialist-tool
```

Fill these before implementation:

1. `docs/TASK_SPEC.md`
2. `docs/EVAL_PLAN.md`
3. `docs/DATASET_CARD.md`
4. `docs/TOOL_CONTRACT.md`
5. `docs/MODEL_CARD.md`
6. `SKILL_TEMPLATE.md` -> final `SKILL.md`

## Training Defaults

Prefer:

- real data over guesses
- explicit baselines
- hard-negative evaluation
- minimax/worst-case objectives when defaults must generalize
- quick/default mode for normal runs
- thorough/Optuna mode only when needed
- checkpoints, logs, and resumable studies
- memory-safe PyTorch defaults: `num_workers=0`, explicit cleanup, no weights in Optuna attrs

## Available Hardware

Fill this in for the machine running training:

- CPU: replace-me CPU model and thread count
- RAM: replace-me system RAM
- GPU: replace-me GPU model and VRAM
- CUDA/accelerator stack: replace-me CUDA, ROCm, MPS, CPU-only, or other runtime

Use these values to estimate feasible model size, batch size, data volume, Optuna sweep budget, and whether a task fits local training or needs cloud hardware. Keep the committed GitHub version generic; the user's agent should replace these placeholders in a local copy.

## Tool Contract

Specialist tools should return structured JSON:

```json
{
  "success": true,
  "label": null,
  "score": null,
  "confidence": null,
  "threshold": null,
  "abstained": false,
  "reasons": [],
  "recommended_action": null,
  "metadata": {}
}
```

Low confidence means abstain or verify another way. Treat the specialist result as evidence, not final truth.

## Common Mistakes

- Training before the task and eval spec are clear enough.
- Optimizing average score when one catastrophic subtask failure matters.
- Trusting confidence outside the evaluated distribution.
- Skipping leakage checks.
- Shipping a model without a tool contract or skill.
- Treating a narrow specialist as a general reasoning upgrade.

## Verification Checklist

- [ ] Task is narrow and measurable.
- [ ] Baseline exists.
- [ ] Splits and leakage checks are documented.
- [ ] Hard cases are included.
- [ ] Specialist beats baseline on held-out data.
- [ ] Tool returns structured JSON.
- [ ] Skill documents when to use, when not to use, and how to interpret output.
