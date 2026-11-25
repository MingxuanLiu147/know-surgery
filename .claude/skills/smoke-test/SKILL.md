---
name: smoke-test
description: "Check a plan's resolved configuration and optionally run a few cases to verify model loading and output creation before a larger run."
---

# Smoke-test a plan

## Inputs

A valid plan, selected method, local inputs, and an authorized budget for any model execution.

## Workflow

```bash
python .claude/skills/smoke-test/scripts/run.py --plan PLAN \
  --output artifacts/TASK/smoke_trace.json
```

1. Choose a separate output directory for the model run and a path for the trace. The helper
   caps the case budget at two and sets `trainer.args.max_steps=1` for injection and unlearning.
   Editing uses the selected editor's method settings.
2. Preview and preflight this bounded configuration with the same method. Use its own
   `review_hash` for the [model execution workflow](../_shared/references/execution.md).
3. If an injection or unlearning check needs a different update budget, set that budget on the
   corresponding run skill and preflight it there.
4. Inspect the actual case and step counts, model loading, generated files, and any errors. Use
   `configured` for a composed preview and `verified_smoke` only when the real run produced the
   expected evidence.

## Completion criteria

Return the trace, the cases or steps actually checked, and the files or error that establish the
outcome.

[Shared workflow conventions](../_shared/references/workflow.md)
