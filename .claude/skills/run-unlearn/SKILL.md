---
name: run-unlearn
description: "Preview, preflight, or execute an unlearning plan with explicit forget and retain sets and evaluate both scopes."
---

# Run machine unlearning

## Inputs

A plan with `operation=unlearning`, a starting checkpoint, method, separate forget and retain
data, and an update budget.

## Workflow

```bash
python .claude/skills/run-unlearn/scripts/run.py --plan PLAN \
  --output artifacts/TASK/unlearn_trace.json
```

1. Verify the starting checkpoint, the loss and evaluation settings, and the roles of the two
   datasets. Check for overlapping forget and retain examples.
2. Preview the plan, then add `--preflight` for the same selection. Inspect the method's
   `review_hash` and any blockers.
3. Follow the [model execution workflow](../_shared/references/execution.md) for the authorized
   configuration. Repeat preflight if a dataset or other reviewed input changes.
4. Inspect both forget efficacy and retained utility. Report the scope of each measurement and
   distinguish a low score from missing data, a skipped evaluation, or a failed run.

## Completion criteria

Return the trace, configuration, and measured forget and retain results. Limit conclusions about
forgetting to the behavior the probes tested, including when answer quality falls. Mark
unmeasured outcomes as unavailable.

[Shared workflow conventions](../_shared/references/workflow.md)
