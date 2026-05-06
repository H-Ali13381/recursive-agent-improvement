# Task Specification

## Specialist name

TODO

## Agent weakness this fixes

Describe the recurring failure pattern in concrete terms.

Bad:
- "Make the agent better at vision."

Good:
- "Given a screenshot of a generated desktop theme, detect clipped text, unreadable contrast, and layout overflow before the agent claims the theme is finished."

## Inputs

- Type:
- Shape/format:
- Required preprocessing:
- Invalid input behavior:

## Outputs

The model/tool should return agent-usable JSON, not vague prose.

Suggested fields:

```json
{
  "label": null,
  "score": null,
  "confidence": null,
  "threshold": null,
  "reasons": [],
  "recommended_action": null
}
```

## Success metric

Primary metric:

Secondary metrics:

Minimum acceptable performance:

## Baseline

Define the dumb baseline before training a neural model.

Examples:
- majority class
- logistic regression on embeddings
- rule-based heuristic
- existing library/model

## Failure modes

List cases the specialist should catch and cases it is allowed to abstain on.

## Tool integration target

- CLI:
- Python function:
- MCP server:
- Hermes tool:
- Skill name:
