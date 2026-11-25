---
name: compare-methods
description: "Compare recorded metrics and experimental conditions from existing runs to determine whether the evidence supports a method comparison."
---

# Compare methods across runs

## Inputs

At least two run directories, each containing its own configuration and evaluation outputs. Pass
the directories as positional arguments.

## Workflow

```bash
python .claude/skills/compare-methods/scripts/run.py RUN_A RUN_B \
  --output artifacts/TASK/comparison.json
```

1. Identify the target of the comparison, such as edit success, locality, or runtime. Inspect
   the saved traces and evaluation files.
2. Read `fairness`, `metric_alignment`, and `comparable` in the comparison JSON. Distinguish a
   missing identity field (`known=false`) from an observed difference.
3. Open each `resolved_config.yaml` and compare the sample scope, update steps, and effective
   batch size. Training budgets can differ even when `comparable` is `true`.
4. Check the denominator, direction, and scoring protocol for each metric. Timing comparisons
   also require matching hardware and workloads.
5. Explain which comparisons the evidence supports and identify the field or file behind each
   mismatch. Use the comparison data for a plot or ranking only when the requested comparison is
   justified.

## Completion criteria

Return the comparison JSON and a brief conclusion for each metric of interest. List any
conditions that differed or could not be verified.

[Shared workflow conventions](../_shared/references/workflow.md)
