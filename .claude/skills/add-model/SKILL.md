---
name: add-model
description: "Register or validate a model configuration when adding a local or Hugging Face checkpoint to a Know-Surgery operation."
---

# Add a model configuration

## Inputs

The checkpoint and tokenizer sources, model revision and architecture, and the intended
operation and method.

## Workflow

```bash
python .claude/skills/add-model/scripts/run.py --path CONFIG_YAML \
  --output artifacts/TASK/model_validation.json
```

1. Inspect `configs/model/` and reuse the handler for the same architecture. Set the checkpoint,
   tokenizer, precision, and any method-specific target modules. Record the source, revision,
   and license.
2. Run the helper on the proposed YAML. It checks that the file contains a mapping and lists its
   keys. Inspect `model_args` and `tokenizer_args`, or the corresponding processor settings for
   a multimodal model.
3. Compose and preflight the target operation. For an authorized compatibility check, load the
   model and run a small forward pass, generation, or method-specific smoke test.

## Completion criteria

Return the model configuration and identify which stages passed for this method, from YAML
validation through loading and execution. List any assets still needed.

[Shared workflow conventions](../_shared/references/workflow.md)
