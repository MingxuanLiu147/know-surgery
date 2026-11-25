---
name: release-checklist
description: "Check entrypoints, configuration, installed dependencies, and skill wrappers before using or sharing a Know-Surgery checkout."
---

# Check a source checkout

## Inputs

The source checkout, its Python environment, and the components intended for use or
distribution.

## Workflow

```bash
python .claude/skills/release-checklist/scripts/run.py --output artifacts/TASK/checklist.json
```

1. Read the checklist for entrypoints, registered configurations, dependency discovery, license
   files, and skill wrappers.
2. Record failed required checks separately from optional components such as the WebUI and Codex
   discovery link.
3. For the intended workflow, check the environment and preflight the selected recipe. Record a
   bounded model run if that validation is authorized.
4. Before sharing files, review the applicable licenses, model and data permissions, and any
   private inputs or artifacts.

## Completion criteria

Return the structural checklist with any failed checks and state which compatibility,
evaluation, or licensing questions still need evidence.

[Shared workflow conventions](../_shared/references/workflow.md)
