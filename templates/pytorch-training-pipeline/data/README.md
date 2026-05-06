# Data

Local datasets live here and are ignored by git.

Expected subdirectories:

```text
raw/        immutable source data
interim/    intermediate converted data
processed/  train/val/test-ready data
external/   downloaded public datasets
```

Rules:

- Keep raw data immutable.
- Split by group/source when leakage is possible.
- Track dataset generation commands in `docs/DATASET_CARD.md`.
- Do not commit private or large generated data by default.
