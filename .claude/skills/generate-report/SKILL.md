---
name: generate-report
description: "Render an aggregate, comparison, or execution trace as Markdown and JSON while preserving the evidence supplied by the run."
---

# Generate a run report

## Inputs

An existing JSON result, the desired report paths, and the question the report should answer.

## Workflow

```bash
python .claude/skills/generate-report/scripts/run.py --input INPUT_JSON \
  --markdown-output artifacts/TASK/report.md \
  --json-output artifacts/TASK/report.json
```

1. Inspect the input type, metric definitions, and source runs. Identify any results the input
   does not contain.
2. Run the renderer to produce both files. The JSON output preserves the input payload and the
   Markdown report includes it as evidence.
3. If interpretation is requested, use the recorded scope to distinguish planning, preflight,
   smoke runs, and full evaluations. Include a saved reproduction command when available.
4. Check the report for credentials, private paths, and restricted data before sharing it.

## Completion criteria

Return the Markdown and JSON paths. Tie any conclusions to the source records and leave
unmeasured values as `null` or N/A.

[Shared workflow conventions](../_shared/references/workflow.md)
