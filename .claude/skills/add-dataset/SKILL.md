---
name: add-dataset
description: "Map a custom dataset to a supported data contract and register its configuration for use through the Know-Surgery CLI."
---

# Add a dataset

## Inputs

The data file, source, version, split, fields, and intended operation. Identify which records or
probes evaluation will need.

## Workflow

```bash
python .claude/skills/add-dataset/scripts/run.py --path CONFIG_YAML \
  --output artifacts/TASK/dataset_validation.json
```

1. Inspect `src/data/` and `configs/data/datasets/`. Reuse a handler when the records match its
   schema. For example, `Canonical_edit` accepts prepared editing cases.
2. Create or select the dataset YAML under `configs/data/datasets/`. Register a new handler only
   if the existing ones cannot represent the records.
3. Run the helper to validate the YAML mapping. Load a few records with the actual handler and
   inspect targets, probes, and roles.
4. Compose the public CLI configuration and run preflight. If a small model run was requested
   and authorized, record its inputs, split, and results.

## Completion criteria

Return the selectable configuration, evidence from loading sample records, and any requested run
or evaluation results. State which checks were completed.

[Shared workflow conventions](../_shared/references/workflow.md)
