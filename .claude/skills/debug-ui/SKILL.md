---
name: debug-ui
description: "Check a running Know-Surgery backend and investigate the affected WebUI behavior or its agreement with the CLI."
---

# Check the WebUI backend

## Inputs

The actual backend URL, the affected feature, and any relevant logs. Replace the example address
if the service uses another port.

## Workflow

```bash
python .claude/skills/debug-ui/scripts/run.py --url http://127.0.0.1:17860 \
  --output artifacts/TASK/health.json
```

1. Run the health check against the intended backend. Read the response from `/api/v1/health` or
   the reported connection error.
2. For an interface issue, exercise the affected control in the browser. Compare its exported
   command with the CLI preview and check language, validation, and result rendering as
   relevant.
3. Use model execution only if the issue requires it and the request authorizes it. Keep
   provider keys out of logs, screenshots, and exports.

## Completion criteria

Return the health report and the evidence for the specific UI behavior inspected. Identify which
checks reached the backend and which exercised the browser.

[Shared workflow conventions](../_shared/references/workflow.md)
