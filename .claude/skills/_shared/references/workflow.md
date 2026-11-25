# Shared workflow conventions

Run the skill commands from the root of a Know-Surgery checkout with the project's Python
environment. Use registered component IDs and the flags accepted by each helper's `--help`.

- Replace `TASK` with a task-specific directory name. Replace `PLAN`, `INPUT`, `RUN_DIR`, and
  `CONFIG_YAML` with actual paths and quote paths that contain spaces.
- Keep source data, starting checkpoints, and previous run outputs intact. Record the input
  versions, seed, sample and step budgets, configuration overrides, and reasons for changes.
- Treat planning, configuration preview, preflight, and model execution as distinct stages.
  Before executing or rerunning a model, follow the [model execution workflow](execution.md).
  Use the scope already authorized and ask only if required input or authorization is missing.
- Store plans, traces, and reports under `artifacts/`. For model and evaluation outputs, use the
  directory in the resolved configuration, usually under `saves/`. See the
  [artifact layout](artifact-layout.md).
- Use `planned`, `configured`, `local_validation`, `verified_smoke`, or `verified_result`
  according to the [evidence levels](evidence-levels.md). Report failures with their cause and
  next step. Preserve missing measurements as `null` or N/A.
- Before sharing an artifact, check for credentials, private input, and restricted data.
