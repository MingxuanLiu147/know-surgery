---
name: reproduce-run
description: "Recover the saved command, configuration, and environment references when inspecting or repeating a Know-Surgery run."
---

# Recover a run command

## Inputs

A run directory with a nonempty `command.txt`. To rerun, identify the requested scope and a new
output directory.

## Workflow

```bash
python .claude/skills/reproduce-run/scripts/run.py --run-dir RUN_DIR \
  --output artifacts/TASK/reproduction.json
```

1. Read the reproduction JSON. Check the recovered command and the references to
   `resolved_config.yaml` and `environment.json` when available. If the command is missing,
   report the missing file.
2. Compare the working directory, model revision, input hashes, seed, and budget against the
   recorded run.
3. For an authorized rerun, select a separate output directory, compose the configuration, and
   preflight it. Follow the [model execution workflow](../_shared/references/execution.md).
4. Compare metrics and environment differences after execution. Treat a changed input or initial
   checkpoint as a new experiment.

## Completion criteria

Return the recovered command and configuration references and identify missing inputs. If a
rerun took place, report the observed differences and both output locations.

[Shared workflow conventions](../_shared/references/workflow.md)
