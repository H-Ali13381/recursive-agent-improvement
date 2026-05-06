---
name: recursive-agent-improvement
description: Use when designing or building specialist tools, small ML models, evaluators, or training templates that extend an agent's capabilities without modifying the base LLM.
version: 0.1.0
author: H-Ali13381
license: MIT
metadata:
  hermes:
    tags: [agents, tools, pytorch, specialist-models, recursive-improvement]
    related_skills: []
---

# Recursive Agent Improvement

## Overview

Use this project to turn recurring LLM weaknesses into durable agent capabilities. The base LLM plans and orchestrates; specialist tools handle narrow, measurable tasks the LLM is bad at.

## When to use

Use this approach when:

- the agent repeatedly fails at a narrow task
- success can be measured with real data
- a specialist model, evaluator, classifier, reranker, or detector would help
- the result can be exposed through a tool or skill

Do not use it for vague goals like "make the LLM smarter generally." Make the task small enough to test.

## Core loop

1. Define the recurring failure.
2. Specify inputs, outputs, and success metrics.
3. Build a baseline before training a neural model.
4. Create train/val/test splits with leakage checks.
5. Add hard negatives or adversarial cases.
6. Train with PyTorch or another appropriate stack.
7. Evaluate against the baseline and hard cases.
8. Package the model as a JSON-returning tool.
9. Write a skill telling the agent when to call it and how to interpret results.

## PyTorch template

Clone the starter pipeline with:

```bash
cp -a templates/pytorch-training-pipeline ~/Documents/my-specialist-tool
cd ~/Documents/my-specialist-tool
```

Fill docs before code:

1. `docs/TASK_SPEC.md`
2. `docs/EVAL_PLAN.md`
3. `docs/DATASET_CARD.md`
4. `docs/TOOL_CONTRACT.md`
5. `docs/MODEL_CARD.md`
6. `SKILL_TEMPLATE.md` -> final project/tool skill

## Training preferences

Prefer:

- real data over guesses
- explicit baselines
- hard-negative evaluation
- worst-case/minimax objectives when defaults must generalize
- quick/default mode for normal runs
- thorough/Optuna mode only when needed
- checkpoints, resumable studies, and logs
- memory-safe PyTorch defaults such as `num_workers=0`, explicit cleanup, and no model weights stored in Optuna attrs

## Tool output contract

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

Low confidence means abstain or verify another way. A specialist result is evidence, not final truth.

## Common pitfalls

- Training before the task/eval spec is clear.
- Optimizing average score when one catastrophic subtask failure matters.
- Trusting confidence outside the evaluated distribution.
- Forgetting leakage checks.
- Shipping a model without a tool contract or skill.
- Treating a narrow specialist as a general reasoning upgrade.

## Verification checklist

- [ ] Task is narrow and measurable.
- [ ] Baseline exists.
- [ ] Splits and leakage checks are documented.
- [ ] Hard cases are included.
- [ ] Model beats baseline on held-out data.
- [ ] Tool returns structured JSON.
- [ ] Skill documents when to use, when not to use, and how to interpret output.
