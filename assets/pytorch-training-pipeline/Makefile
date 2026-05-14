# PyTorch specialist training skeleton.
# Targets are placeholders until task-specific code exists.

PYTHON ?= python
CONFIG ?= configs/defaults.yaml
SEARCH ?= configs/search_space.yaml
OUTDIR ?= artifacts/runs

.PHONY: help setup spec data baseline train-quick train-thorough evaluate package tool-test clean

help:
	@echo "Specialist training skeleton targets:"
	@echo "  make spec            # Review task/eval/data docs"
	@echo "  make setup           # Create environment once implemented"
	@echo "  make data            # Build/validate dataset once implemented"
	@echo "  make baseline        # Run dumb baseline once implemented"
	@echo "  make train-quick     # Single-run training once implemented"
	@echo "  make train-thorough  # Optuna sweep once implemented"
	@echo "  make evaluate        # Held-out evaluation once implemented"
	@echo "  make package         # Export model/tool artifacts once implemented"
	@echo "  make tool-test       # JSON wrapper smoke test once implemented"

spec:
	@echo "Read docs/TASK_SPEC.md, docs/EVAL_PLAN.md, and docs/DATASET_CARD.md"

setup:
	@echo "TODO: create venv/install deps when implementation exists"

data:
	@echo "TODO: implement dataset build/validation"

baseline:
	@echo "TODO: implement non-neural or trivial baseline"

train-quick:
	@echo "TODO: implement quick training mode using $(CONFIG)"

train-thorough:
	@echo "TODO: implement Optuna/minimax sweep using $(SEARCH)"

evaluate:
	@echo "TODO: implement held-out evaluation"

package:
	@echo "TODO: export weights/config/preprocessor/threshold/model card"

tool-test:
	@echo "TODO: run tool wrapper JSON smoke test"

clean:
	@echo "TODO: define safe cleanup rules; do not delete raw data by default"
