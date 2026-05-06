# Evaluation Plan

## Principle

No model is useful until it beats a baseline on a held-out test set that represents the real agent failure.

## Dataset splits

- Train:
- Validation:
- Test:
- Hard-negative/adversarial set:
- Cross-task benchmark set, if any:

Leakage prevention:

- Grouping key:
- Deduplication method:
- Near-duplicate check:

## Metrics

Primary metric:

Secondary metrics:

Operational threshold metric:

Worst-case metric:

For generalizable defaults, prefer:

```text
per_task_scores = [score_task_a, score_task_b, ...]
objective = 1 - min(per_task_scores)
```

## Acceptance gates

A trained specialist is not usable by the agent until:

- [ ] beats dumb baseline
- [ ] passes held-out test gate
- [ ] passes hard-negative/adversarial gate
- [ ] has calibrated or documented confidence behavior
- [ ] has an error-analysis report
- [ ] has a model card
- [ ] has a JSON tool smoke test

## Error analysis

For each failed example, record:

- input ID
- predicted output
- expected output
- confidence
- likely cause
- whether data, model, threshold, or tool contract should change
