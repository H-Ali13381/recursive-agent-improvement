---
name: recursive-agent-improvement
description: Use when designing agent capability extensions with specialist tools, small PyTorch models, evaluators, rerankers, classifiers, or training templates for narrow, measurable LLM weaknesses.
---

# Recursive Agent Improvement

## Overview

Build durable agent capabilities by turning repeated LLM failures into narrow, measurable tools. Use the LLM for planning and orchestration; use specialist models or deterministic tools for perception, ranking, scoring, detection, extraction, and verification.

## When to Use

Use this skill when:

- An agent repeatedly fails at a narrow task.
- The task has measurable inputs, outputs, and success criteria.
- A small model, evaluator, reranker, classifier, or detector could help.
- The result can be exposed through a tool and documented with a skill.

Do not use this for vague goals like “make the LLM smarter generally.” Narrow the task first.

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

Current local training box:

- CPU: AMD Ryzen 5 3600, 12 threads
- RAM: 15 GiB
- GPU: NVIDIA GeForce RTX 4070 SUPER, 12 GiB VRAM
- CUDA: 13.2

This is enough for small-to-medium specialist training: CNNs, compact Transformers, embedding classifiers, rerankers, audio detectors, image/layout evaluators, and LoRA/adapter-style experiments. Prefer 12 GB VRAM assumptions when estimating batch size, model size, and sweep budget.

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
