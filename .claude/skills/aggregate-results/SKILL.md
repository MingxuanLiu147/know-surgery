---
name: aggregate-results
description: "Collect recorded metrics from existing run directories with their sources and checkpoint locations when summarizing an experiment."
---

# Aggregate run metrics

## Inputs

One or more run directories containing the saved outputs for the runs of interest.

## Workflow

```bash
python .claude/skills/aggregate-results/scripts/run.py RUN_A RUN_B \
  --output artifacts/TASK/aggregate.json
```

1. Check the command, resolved configuration, input manifest, trace, and available metric files
   for each run.
2. Inspect the evaluator, metric name, phase, and source file in the aggregate. The helper reads
   summaries at the run root and, when `trainer_state.json` records a final `global_step`, the
   summaries in that checkpoint's `evals/` directory.
3. Verify each metric's denominator, sample scope, and evidence level. Keep unavailable values
   as `null` or N/A and distinguish smoke runs from full evaluations.
4. If the user wants a ranking, check comparability with `compare-methods` before interpreting
   the metrics.

## Completion criteria

Return the aggregate JSON with sources for the reported values. Identify missing measurements,
failed runs, and any limits on interpretation.

[Shared workflow conventions](../_shared/references/workflow.md)
