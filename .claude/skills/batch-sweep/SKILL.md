---
name: batch-sweep
description: "Expand a plan into pending commands for each method and distinct random seed so the user can review a batch before running it."
---

# Plan a method and seed sweep

## Inputs

A plan, a list of seeds, an output path, and the total experiment budget.

## Workflow

```bash
python .claude/skills/batch-sweep/scripts/run.py --plan PLAN --seeds 42,43,44 \
  --output artifacts/TASK/sweep.json
```

1. Check the registered components, shared inputs, methods, and budget. The helper deduplicates
   repeated seeds.
2. Inspect the sweep manifest. Each method and seed pair should have its own task name, command,
   and run hash. Check the output directories for collisions.
3. Verify sample coverage and update steps, then preflight and smoke-test a representative
   configuration before scheduling an authorized sweep through the usual run entrypoint.

## Completion criteria

Return the manifest of `pending` commands and summarize the variations and expected cost. Record
failures and unfinished runs if the sweep is later executed.

[Shared workflow conventions](../_shared/references/workflow.md)
