---
name: run-edit
description: "Preview, preflight, or execute a registered editing plan and check its effect on the target, paraphrases, and unrelated knowledge."
---

# Run a knowledge edit

## Inputs

A plan with `operation=edit`, its model and method, the cases, and the device and budget for
execution.

## Workflow

```bash
python .claude/skills/run-edit/scripts/run.py --plan PLAN --output artifacts/TASK/edit_trace.json
```

1. Check the case count and targets. Verify the method's layer mapping, statistics, and
   auxiliary checkpoints against the chosen model.
2. Preview the plan. Add `--method ID` to select one method from a multi-method plan. Run the
   same selection with `--preflight` and inspect the errors and `review_hash` for that method.
3. Follow the [model execution workflow](../_shared/references/execution.md) for an authorized
   run. Report missing prerequisites against the method the user selected.
4. Inspect the completed cases, predictions, and evaluation outputs. Report reliability on the
   original prompts, generalization on paraphrases, and locality on unrelated probes where the
   data and scoring protocol support them.

## Completion criteria

Return the configuration, trace, and outputs for the completed cases, or the specific blocker.
Mark unmeasured dimensions as unavailable.

[Shared workflow conventions](../_shared/references/workflow.md)
