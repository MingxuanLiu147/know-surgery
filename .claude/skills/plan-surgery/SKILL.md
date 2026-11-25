---
name: plan-surgery
description: "Turn an injection, editing, or unlearning request into a reviewable SurgeryPlan with registered components, input bindings, and a case budget."
---

# Plan a knowledge update

## Inputs

The intended operation and modality, model, dataset, methods, and number of cases. For custom
data, supply the prepared cases file.

## Workflow

```bash
python .claude/skills/plan-surgery/scripts/run.py --intent "Edit one CounterFact fact with GPT2 and FT" \
  --output artifacts/TASK/plan.json
```

1. Choose `inject`, `edit`, or `unlearning`. Look up IDs with `inspect-repo`. Set `--operation`,
   `--modality`, `--model-id`, `--dataset-id`, `--methods`, or `--num-cases` when the request
   specifies them.
2. Use `--cases PATH` to bind custom cases. Check the role, record count, and hash of each
   input. Unlearning needs both forget and retain data. Rank-based editors such as ROME and
   MEMIT need an explicit `subject`.
3. For image-text injection, use
   `--modality multimodal --model-id Qwen2.5-VL-3B --methods MM_LoRA --dataset-id Canonical_MM_inject --cases PATH`.
   Resolve relative image paths from the directory containing the cases file.
4. Review recipe choices and warnings. For comparisons, check the sample scope, effective batch
   size, and update steps. WikiDYK counts expanded training instances, so one fact can
   contribute several instances.
5. Check each proposed evaluator against the actual evaluation data, reference model, and
   settings such as `do_eval`. Pass the plan to the corresponding run skill for a preview.

## Completion criteria

Return the plan JSON, its key settings, and any unresolved choices. The
[SurgeryPlan schema](../_shared/references/surgery-plan.schema.json) defines the output fields.

[Shared workflow conventions](../_shared/references/workflow.md)
