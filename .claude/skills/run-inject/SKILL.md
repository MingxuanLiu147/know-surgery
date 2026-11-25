---
name: run-inject
description: "Preview, preflight, or execute an injection plan and verify how acquisition, generalization, and retention will be measured."
---

# Run knowledge injection

## Inputs

A plan with `operation=inject`, a model, method, training data, device, and update budget.

## Workflow

```bash
python .claude/skills/run-inject/scripts/run.py --plan PLAN \
  --output artifacts/TASK/inject_trace.json
```

1. Check the recipe, model, adapter, training inputs, and budget. For image-text injection, set
   `modality=multimodal`. Bound cases populate `data.train_path`. Set the `data.retain_path` key
   in the plan's `overrides` mapping for separate retention probes.
2. Preview the plan and repeat the same selection with `--preflight`. Inspect the method's
   `review_hash` and resolve any missing inputs.
3. Check the evaluation entrypoint, enabled evaluators, and their data. For WikiDYK, check the
   acquisition and generalization questions, the locality set, and the reference predictions
   used for retention.
4. Follow the [model execution workflow](../_shared/references/execution.md) when authorized.
   Select `--method`, `--cuda`, or `--timeout` as needed.
5. Read the actual step count, sample scope, output directory, and evaluation results. Identify
   which measurements used held-out data and which used training examples.

## Completion criteria

Return the run status, configuration, trace, and measured target and side-effect metrics. Mark
missing measurements as unavailable.

[Shared workflow conventions](../_shared/references/workflow.md)
