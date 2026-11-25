---
name: normalize-knowledge
description: "Convert JSON, JSONL, CSV, or TXT into records for a specific operation before importing data or building cases."
---

# Normalize knowledge records

## Inputs

The source file, operation, and any known knowledge type or role. Use the targets and provenance
supplied with the records.

## Workflow

```bash
python .claude/skills/normalize-knowledge/scripts/run.py --input INPUT --operation edit --knowledge-type fact \
  --output artifacts/TASK/normalized.jsonl
```

1. Inspect the source fields and select the operation. Injection uses the `train` role and
   editing uses `edit`. For unlearning, preserve each record's `dataset_role` or pass
   `--role forget` and `--role retain` on separate inputs.
2. Read the accepted JSONL, `.rejected.json`, and `.manifest.json`. Check the counts and
   rejection reasons, including empty input.
3. Verify that supplied IDs, source details, timestamps, conditions, and probes survive
   conversion. TXT input splits on blank lines. Resolve missing questions or targets from the
   source.

## Completion criteria

Return the normalized records, source manifest, and accepted and rejected counts. Report
unresolved fields so the user can correct the input.

[Shared workflow conventions](../_shared/references/workflow.md)
