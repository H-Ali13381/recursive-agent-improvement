# Artifacts

Generated model artifacts live here locally and are ignored by git.

Expected subdirectories:

```text
checkpoints/   training checkpoints
exports/       packaged models for inference/tool use
reports/       metrics, error analysis, plots
runs/          per-run logs/config snapshots
optuna/        SQLite studies and sweep exports
```

Do not commit large model weights or generated reports unless explicitly intended.
