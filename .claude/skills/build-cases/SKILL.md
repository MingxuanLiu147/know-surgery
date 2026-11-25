---
name: build-cases
description: "Convert normalized records into editing, injection, or forget and retain cases and count the evaluation probes supplied with them."
---

# Build cases for a knowledge update

## Inputs

Normalized JSONL for one operation, including targets, roles, and any supplied paraphrases or
side-effect probes.

## Workflow

```bash
python .claude/skills/build-cases/scripts/run.py --input NORMALIZED --operation edit \
  --output artifacts/TASK/cases.jsonl
```

1. Use the same operation as in normalization. Check the targets and roles. Unlearning requires
   separate, nonempty forget and retain sets.
2. Read the case file and its `.manifest.json`. Check record counts, provenance, and coverage
   for rephrase, locality, and portability probes. For unlearning, also inspect `.forget.jsonl`
   and `.retain.jsonl`.
3. Give the case file to `plan-surgery` with `--cases PATH` to bind the inputs. Carry missing
   probes forward as missing measurements.

## Completion criteria

Return the case files and manifest with coverage counts for the supplied probes. List any
questions or reference answers that still need to be supplied for evaluation.

[Shared workflow conventions](../_shared/references/workflow.md)
