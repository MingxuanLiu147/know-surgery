---
name: inspect-repo
description: "Find registered models, datasets, trainers, and recipes in a Know-Surgery checkout when selecting or extending a workflow."
---

# Inspect the workbench

## Inputs

A source checkout and the operation or component you want to investigate.

## Workflow

```bash
python .claude/skills/inspect-repo/scripts/run.py --output artifacts/TASK/inventory.json
```

1. Read `registry` for model, dataset, and trainer IDs. Read `recipes` for combinations the
   workbench already describes.
2. Match the operation, model, dataset, and method to the task. Inspect the corresponding YAML
   and handler to confirm modality, required assets, and restrictions.
3. Use a matching recipe when available. If none covers the requested combination, identify what
   needs to be composed or adapted.

## Completion criteria

Return the inventory and the IDs or recipe that fit the task. Describe configuration coverage
separately from any evidence of a completed run.

[Shared workflow conventions](../_shared/references/workflow.md)
