# Preview, preflight, and run a model

Use this procedure for `run-edit`, `run-inject`, `run-unlearn`, `smoke-test`, and any authorized
rerun.

## Preview the plan

Confirm the operation, modality, registered model and method, input files, checkpoint, device,
and budget. Reuse a matching recipe and record any overrides. Run the chosen skill with
`--plan PLAN` to inspect the composed configuration. Use the same method selection in the
following steps.

## Check prerequisites

Add `--preflight` to the preview command. Read the report for each selected method, including
input identities, method parameters, evaluation settings, and `review_hash`. Resolve any
reported blockers before execution.

## Execute the reviewed configuration

Once the user's authorization covers the reviewed configuration and inputs, replace
`--preflight` with `--execute --reviewed-config METHOD=HASH` on the skill wrapper. Substitute
the method ID and its `review_hash`. Repeat `--reviewed-config` for each selected method.
`--cuda` and `--timeout` are optional. For direct invocation of `know-surgery` or
`python src/surgery.py`, pass `--reviewed-config HASH` with the same Hydra overrides.

The hash identifies what was reviewed. Check authorization separately and reuse it when it
already covers the run. Repeat preflight after changing the configuration, model, method assets,
or inputs. Review a smoke run at its own budget. The helper caps the case budget at two and sets
`trainer.args.max_steps=1` for injection and unlearning. Use the operation's run skill for
another budget.

## Verify the outcome

Inspect the exit status, command, resolved configuration, input manifest, trace, and result
files. Check the actual sample and step counts. Verify that evaluation ran, then report the
measured target effect, generalization, locality, or retained utility under the applicable
protocol. Mark missing values as `null` or N/A and identify the scope of the evidence.
