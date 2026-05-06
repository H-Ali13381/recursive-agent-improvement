---
name: replace-me-specialist-tool
description: Use when replace-me-trigger-condition.
version: 0.1.0
author: replace-me
license: MIT
metadata:
  hermes:
    tags: [replace-me]
    related_skills: []
---

# Replace Me Specialist Tool

This is a template. Replace every `replace-me` value before using it as a real skill.

## When to use

- replace-me: concrete trigger condition
- replace-me: valid input condition
- replace-me: decision this specialist is meant to support

## Do not use when

- replace-me: out-of-scope condition
- replace-me: invalid/missing input condition
- replace-me: low-confidence or abstention condition

## Tool contract

Input:

```json
{
  "input": "replace-me",
  "options": {}
}
```

Output:

```json
{
  "success": true,
  "label": "replace-me",
  "score": 0.0,
  "confidence": 0.0,
  "threshold": 0.0,
  "abstained": false,
  "reasons": [],
  "recommended_action": "replace-me",
  "metadata": {}
}
```

Error:

```json
{
  "success": false,
  "error": "replace-me-error-code",
  "message": "replace-me human readable message",
  "metadata": {}
}
```

## Interpretation rules

- replace-me: confidence threshold rule
- replace-me: score/threshold meaning
- replace-me: abstention behavior
- replace-me: fallback or verification rule

## Failure handling

- replace-me: missing artifact behavior
- replace-me: invalid input behavior
- replace-me: tool/runtime failure behavior

## Related docs

- `docs/TASK_SPEC.md`
- `docs/EVAL_PLAN.md`
- `docs/DATASET_CARD.md`
- `docs/MODEL_CARD.md`
- `docs/TOOL_CONTRACT.md`

## Known limitations

- replace-me
