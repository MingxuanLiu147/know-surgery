---
name: setup-env
description: "Inspect the Python environment, dependencies, visible GPUs, and local model caches before a Know-Surgery run or when diagnosing setup."
---

# Check the runtime environment

## Inputs

The source checkout and the Python interpreter you intend to use. Supply local model or cache
paths if they are known.

## Workflow

```bash
python .claude/skills/setup-env/scripts/run.py --output artifacts/TASK/environment.json
```

1. Run the command from the checkout root with the same interpreter you will use for subsequent
   steps. Repeat `--model-cache PATH` to check more than one directory.
2. Read the package import results and `gpu_query`. Configuration planning can proceed on a CPU
   machine even when `nvidia-smi` is unavailable.
3. For a model run, inspect the checkpoint configuration, weight shards, and tokenizer files in
   the selected directory. The directory check only establishes that it exists. Install missing
   packages or download assets within the user's authorized scope.

## Completion criteria

Return the environment report and identify the interpreter, available device, and any missing
dependencies or assets for the requested run.

[Shared workflow conventions](../_shared/references/workflow.md)
