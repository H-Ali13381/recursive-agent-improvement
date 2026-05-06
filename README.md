# Recursive Agent Improvement

Recursive Agent Improvement is a small research/project idea about extending AI agents without modifying the base LLM. Instead of trying to make one language model good at everything, the agent can identify recurring weaknesses, build specialized tools or small machine learning models for those capabilities, and expose them back to the agent through tool calls or skills.

## Core idea

LLMs are strong planners, coders, explainers, and orchestrators. They are often weaker at narrow, measurable tasks such as perception, ranking, scoring, anomaly detection, extraction, and verification. Those gaps can be handled by specialist systems.

A recursive improvement loop looks like this:

1. Notice a recurring LLM weakness.
2. Define a narrow task with measurable success criteria.
3. Create or collect a small dataset.
4. Train a specialist model, evaluator, reranker, classifier, or other tool.
5. Wrap the specialist as an agent-accessible tool.
6. Add a skill describing when and how to use it.
7. Let the agent use the new capability in future work.

## Examples

- A screenshot evaluator that detects broken layouts, poor contrast, clipped text, or weak visual hierarchy.
- A code-change risk classifier that flags patches likely to affect unrelated behavior.
- A paper-search reranker tuned for AI safety relevance.
- An audio detector for wakewords, events, or speech activity.
- A fact-consistency checker for retrieved sources and generated summaries.
- A style-matching model for generated desktop themes, UI mockups, or visual artifacts.

## Architecture

```text
Base LLM
  -> plans, writes code, explains, orchestrates

Tools
  -> execute deterministic actions, inspect files, search, run commands

Specialist ML tools
  -> perceive, classify, rank, score, detect, verify

Skills
  -> persistent procedural memory for when and how to use tools
```

The goal is not to make the LLM magically better by prompting. The goal is to build an expanding exocortex of narrow, trainable capabilities around the agent.

## Templates

This repo includes a cloneable skeleton for building new PyTorch specialist training projects:

```bash
cp -a templates/pytorch-training-pipeline ~/Documents/my-specialist-tool
cd ~/Documents/my-specialist-tool
```

The template is intentionally implementation-free. It defines the structure, docs, configs, evaluation gates, artifact layout, and agent tool contract before task-specific PyTorch code is written.

## License

MIT
