---
name: TODO-specialist-tool
description: Use when TODO-specific-agent-failure needs TODO-specialist-verification.
version: 0.1.0
author: TODO
license: MIT
metadata:
  hermes:
    tags: [specialist-tool, pytorch, TODO-domain]
    related_skills: []
---

# TODO Specialist Tool

## Overview

This skill tells the agent how to use the TODO specialist model. The model is narrow: it was trained for TODO and should only be trusted inside the boundary documented in `docs/TASK_SPEC.md`, `docs/EVAL_PLAN.md`, and `docs/MODEL_CARD.md`.

## When to use

Use this tool when:

- TODO input matches `docs/TOOL_CONTRACT.md`
- the agent is making the specific decision this model was trained for
- LLM-only judgment is unreliable for this task
- specialist verification is needed before continuing

## Do not use when

Do not use this tool when:

- input is outside the documented distribution
- required preprocessing or model artifacts are missing
- the task requires broad reasoning rather than the trained narrow judgment
- confidence is below the documented threshold
- the model has not been evaluated for this case

## Tool contract

Input:

```json
{
  "input": null,
  "options": {
    "threshold": null,
    "return_reasons": true,
    "abstain_below_confidence": true
  }
}
```

Output:

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
  "metadata": {
    "model_version": null,
    "latency_ms": null
  }
}
```

Error:

```json
{
  "success": false,
  "error": "machine-readable-error-code",
  "message": "human readable explanation",
  "metadata": {}
}
```

## Interpretation rules

- Low confidence means abstain or verify another way.
- Scores only matter relative to the documented threshold.
- Reasons are diagnostic hints, not guaranteed causes.
- If the tool conflicts with direct evidence, investigate before acting.
- If the tool flags high risk, address it or explicitly explain why it is being overridden.

## Failure handling

If the tool fails, returns invalid JSON, lacks artifacts, hits device/OOM errors, or abstains:

- report the exact failure
- do not invent a specialist result
- use a fallback only if documented
- do not claim specialist verification occurred

## Related docs

- `docs/TASK_SPEC.md` — task boundary and input/output definitions
- `docs/EVAL_PLAN.md` — metrics, gates, and hard-case expectations
- `docs/DATASET_CARD.md` — data source, leakage, bias, and coverage notes
- `docs/MODEL_CARD.md` — thresholds, limitations, and trust guidance
- `docs/TOOL_CONTRACT.md` — exact callable schema

## Known limitations

TODO: summarize distribution limits, known failure cases, confidence calibration limits, and cases requiring human or secondary verification.
