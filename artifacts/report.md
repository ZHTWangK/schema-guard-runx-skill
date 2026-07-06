# schema-guard delivery report

## What changed

- Added the `schema-guard` runx skill package.
- The skill compares current and proposed JSON-schema-like object contracts.
- It validates supplied sample payloads against the proposed schema.
- It reports breaking changes by field path, old contract, new contract, and policy rule.
- It emits `publish_schema_proposal` only when the proposal is compatible.
- It never writes a live schema.

## Public artifacts

- Registry listing: https://runx.ai/x/zhtwangk/schema-guard@sha-7ec29f110d08
- Public source: https://github.com/ZHTWangK/schema-guard-runx-skill/tree/7ec29f110d08d1fad4e3a07c93e115238fe2432e
- Upstream PR: https://github.com/runxhq/runx/pull/234
- Raw `X.yaml`: https://raw.githubusercontent.com/ZHTWangK/runx/cf11b84f43b645093568d3d844a977f16ccb676e/skills/schema-guard/X.yaml
- Raw `SKILL.md`: https://raw.githubusercontent.com/ZHTWangK/runx/cf11b84f43b645093568d3d844a977f16ccb676e/skills/schema-guard/SKILL.md

## Verification performed

- `npx runx --version` returned `runx-cli 0.6.16`.
- Local harness passed with two cases:
  - `schema-guard-additive-compatible`
  - `schema-guard-breaking-refused`
- Local registry publish passed as `local/schema-guard@sha-d99e5d4007bc`.
- Clean local install produced `SKILL.md`, `X.yaml`, and `run.mjs`.
- Dogfood run sealed and produced `runx:receipt:sha256:371ae1c3624e1df4e9faa23a8a8da25d4d4319a88d402601cae29eae39870c5e`.
- Local receipt verification passed with `--allow-local-development-signatures`.
- GitHub account `ZHTWangK` currently stars `runxhq/runx`.

## Known limitation

The runx public registry listing is live and source provenance is verified, but
the public harness endpoint currently reports `hosted_harness_status:
not_recorded` for this URL-published listing. The local harness and local
registry publish both pass, but this packet should not be treated as a complete
Frantic #84 delivery until the hosted harness or equivalent accepted hosted
evidence is available.

## Operator value

`schema-guard` gives an operator a deterministic receipt-backed gate before an
API or data schema migration lands. It catches field removals, type changes,
enum narrowing, newly required fields, missing policy-required fields, and
sample validation failures before a publishing step can consume the proposal.
