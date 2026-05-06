---
name: TODO-specialist-tool
description: Use this when TODO. Calls the trained specialist model to TODO.
---

# TODO Specialist Tool

## When to use

Use this when:

- TODO

Do not use this when:

- TODO

## Tool contract

Input:

```json
{
  "input": null,
  "options": {}
}
```

Output:

```json
{
  "success": true,
  "label": null,
  "score": null,
  "confidence": null,
  "reasons": [],
  "recommended_action": null
}
```

## Interpretation rules

- If confidence is below TODO, do not treat the result as decisive.
- If the model abstains, use TODO fallback.
- If the tool flags a high-risk issue, verify with TODO before finalizing.

## Known limitations

TODO
