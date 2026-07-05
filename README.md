# schema-guard runx skill

This repository carries the public source package for the `schema-guard` runx
skill submitted for Frantic bounty #84.

The canonical upstream PR is:

https://github.com/runxhq/runx/pull/234

The skill lives at `skills/schema-guard` and contains:

- `SKILL.md`: operator-facing skill contract.
- `X.yaml`: runx execution profile and harness cases.
- `run.mjs`: deterministic local runner.
- `fixtures/`: expected harness case outcomes.

Local verification used `runx-cli 0.6.16`.
