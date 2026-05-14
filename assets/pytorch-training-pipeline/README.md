# PyTorch Specialist Training Pipeline Template

This is a cloneable skeleton for training narrow specialist models that can be exposed to an agent as tools.

It intentionally contains no implemented Python training code yet. The goal is to give each new specialist project the same structure, decision gates, artifact layout, and evaluation discipline before model-specific code is written.

## Clone/use pattern

```bash
cp -a assets/pytorch-training-pipeline ~/Documents/my-specialist-tool
cd ~/Documents/my-specialist-tool
```

Then fill in the task-specific pieces in this order:

1. `docs/TASK_SPEC.md`
2. `docs/EVAL_PLAN.md`
3. `docs/DATASET_CARD.md`
4. `configs/defaults.yaml`
5. `configs/search_space.yaml`
6. `src/` implementation files
7. `tools/` wrapper files
8. `SKILL_TEMPLATE.md` -> final `SKILL.md` for the trained tool

## Philosophy

Do not start by writing a model. Start by defining the failure the agent keeps having.

A good specialist tool has:

- narrow scope
- measurable target
- explicit baseline
- train/validation/test split
- hard-negative or adversarial cases
- reproducible config
- resumable checkpoints
- resource-aware defaults
- callable JSON interface for agents

## Expected pipeline stages

```text
01_task_definition
  -> what recurring agent failure is this solving?

02_data
  -> collect, label, split, deduplicate, document leakage risks

03_baseline
  -> dumb baseline before neural model

04_training
  -> quick mode by default, thorough Optuna mode only when needed

05_evaluation
  -> primary metric, secondary metrics, worst-case/minimax checks

06_packaging
  -> save weights, config, preprocessors, thresholds, model card

07_tool_wrapper
  -> expose inference as JSON CLI/API/MCP/Hermes tool

08_skill
  -> document when the agent should call the tool and how to trust outputs
```

## Training modes

Use two modes by default:

- `quick`: one training run using known-good defaults
- `thorough`: limited Optuna search over only the most impactful parameters

For universal defaults, run a separate cross-task benchmark and optimize the floor, not the mean.

Preferred objective shape:

```text
score = min(per_task_scores)
objective = 1 - score
```

Average metrics can hide catastrophic failures. Worst-case performance exposes fragile settings.

## Directory map

```text
SKILL_TEMPLATE.md  starter skill for the trained specialist tool
configs/           YAML configs for defaults, sweeps, data, and runtime behavior
data/              local raw/processed/interim data; ignored by git
artifacts/         checkpoints, exported weights, thresholds, reports; ignored by git
docs/              task spec, eval plan, dataset card, model card
src/               future PyTorch implementation package; currently intentionally empty
tests/             future tests and smoke checks
tools/             future agent-facing inference wrapper
scripts/           future operational scripts
```

## Non-goals for the template

This skeleton does not decide:

- architecture
- dataset format
- loss function
- training loop implementation
- serving mechanism
- exact agent tool schema

Those choices belong to the specific specialist model.
