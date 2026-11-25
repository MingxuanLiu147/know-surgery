---
name: add-multimodal-case
description: "Check the local images referenced by JSON or JSONL cases, then prepare their text targets and probes for a multimodal operation."
---

# Validate image-text cases

## Inputs

A JSON or JSONL file, its images and text targets, and the intended model and processor.

## Workflow

```bash
python .claude/skills/add-multimodal-case/scripts/run.py --input INPUT \
  --output artifacts/TASK/mm_validation.json
```

1. Inspect `image` or `images` in each record. Image paths can be absolute or relative to the
   directory containing the input file.
2. Run the image check and inspect diagnostics for empty input, missing files, and decoding
   failures.
3. Review the prompt and target against the image, then check processor and method
   compatibility. Prepare visual efficacy and text preservation probes and preflight the chosen
   multimodal configuration.

## Completion criteria

Return the validation report, identify usable images and remaining issues, and specify any model
or semantic checks performed separately. Keep private images out of shared reports.

[Shared workflow conventions](../_shared/references/workflow.md)
