# Agent Notes

This repository publishes one Agent Skill: `recursive-agent-improvement`.

Canonical files:

- `SKILL.md` is the source of truth for the skill.
- `assets/pytorch-training-pipeline/` contains the bundled specialist-training template referenced by the skill.
- `.agents/skills/recursive-agent-improvement/` is a cross-client discovery mirror containing the same `SKILL.md` and bundled assets.

When editing the skill, update the root `SKILL.md` and `assets/` first, then copy them to the mirror path so the discoverable package stays complete.

Related skill:

- `tier-1-2-3-skill-system`: https://github.com/H-Ali13381/tier-1-2-3-skill-system

Installability check:

```bash
npx skills add H-Ali13381/recursive-agent-improvement --list
```

Validation check:

```bash
npx skill-tools check .
npx skill-tools check .agents/skills
```

Do not add private paths, secrets, local debug notes, model weights, generated reports, or session-specific history to this public skill artifact.
