---
name: replace-me-specialist-tool
description: Use when replace-me-agent-failure-or-user-request; replace-me-required-input-is-available; replace-me-agent-decision-needs-this-specialist-score.
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

- User/task signal: replace-me recurring agent failure, user request, or operational decision that should trigger this specialist.
- Required input exists: replace-me artifact, text, image, audio, metadata, or structured record is available in the expected format.
- Decision impact: replace-me agent action changes based on this result, such as accept/reject, rerank, retry, abstain, escalate, or route.
- Evaluated scope: replace-me input is within the distribution and failure modes covered by `docs/EVAL_PLAN.md` and `docs/MODEL_CARD.md`.

## Do not use when

- Out of scope: replace-me adjacent task, domain, language, modality, or open-ended reasoning case this specialist was not evaluated on.
- Missing/invalid input: replace-me required artifact or field is unavailable, malformed, too large, or not preprocessed.
- No decision impact: replace-me result would not change the agent's next action.
- Low confidence/abstention: replace-me confidence, threshold, or error condition means the agent should verify another way instead.

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
