# Project Breakdown — NexusAgent Publish

Timestamp: `2026-07-07T16:00:00-04:00`

Project repo: `LuminaryLabs-Dev/NexusAgent-Publish`

Ledger alias: `LuminaryLabs-Publish/NexusAgent`

Company ledger repo: `LuminaryLabs-Dev/LuminaryLabs`

Branch target: `main`

Run context: Nexus Engine/Realtime ChatGPT Project

## Selection rationale

The central repo ledger lists `LuminaryLabs-Publish/NexusAgent` as the only `LuminaryLabs-Publish` candidate in the current registry snapshot. GitHub resolves that publish candidate to the accessible public repository `LuminaryLabs-Dev/NexusAgent-Publish`. `Cavalry of Rome` was excluded by rule and was not inspected.

The previous central changelog already records a breakdown for `LuminaryLabs-Publish/ZombieOrchard`, so this run moves to the next eligible publish candidate rather than repeating that project.

## Current repo state

NexusAgent Publish is a public bootstrap/documentation repository for a local-first agent harness system. It contains documentation, schemas, example configuration/goals, and placeholder harness folders. It does not yet contain reviewed runnable public harness source.

The repo is intentionally small and public-safe. Private Dev artifacts, scratchpads, automation state, benchmark evidence, local endpoint assumptions, generated outputs, and private run evidence are intentionally excluded.

## Interaction loop

Primary loop documented by the repository:

```txt
Goal
  -> inspect allowed context
  -> choose one bounded action
  -> write or validate only inside an allowed boundary
  -> record evidence
  -> validate / gate
  -> next step or stop
```

Architecture shorthand:

```txt
Goal -> bounded action -> evidence -> validation -> next step or stop
```

Simple harness loop:

```txt
PLAN_GOAL -> READ_FILES -> WRITE_FILE -> VALIDATE -> FINALIZE
```

Lite harness loop:

```txt
PLAN_GOAL
  -> READ_FILES / FETCH_CONTEXT
  -> WRITE_FILE / PATCH_FILE
  -> VALIDATE
  -> FINALIZE
```

## Domains in use

The repo is not yet organized as executable DSK source, but it clearly expresses these conceptual domains:

| Domain | Current expression | Notes |
|---|---|---|
| Goal domain | README and examples | Captures a human-visible objective before work starts. |
| Harness domain | `docs/architecture.md`, `docs/harness-taxonomy.md`, `harnesses/simple`, `harnesses/lite` | Owns loop rules, action boundaries, parsing shape, write limits, and evidence recording. |
| Action domain | `schemas/agent-action.schema.json` | Defines explicit agent actions such as plan, read, fetch, write, patch, validate, and finalize. |
| Workspace boundary domain | Architecture docs | Defines the allowed read/write filesystem boundary for a run. |
| Ledger/evidence domain | `schemas/run-ledger.schema.json` | Records goal, action, status, evidence, workspace, and next step. |
| Gate/validation domain | Architecture and taxonomy docs | Checks path safety, command allowlists, schema shape, generated files, tests, and human-visible requirements. |
| Runtime endpoint domain | `docs/local-model-runtime.md`, example env config | Abstracts OpenAI-compatible local or external model endpoints through public-safe env vars. |
| Dev-to-publish boundary domain | `docs/dev-to-publish-model.md` | Separates private Dev lane work from sanitized publish snapshots. |
| Safety/publication domain | `SECURITY.md`, safety docs, dev-to-publish docs | Keeps secrets, scratchpads, generated runs, private endpoints, and internal evidence out of public releases. |

## Services the kits/harnesses offer

Current public services are documented rather than implemented as full runtime code:

- Goal intake and ordered action selection.
- Bounded file-aware work loops.
- Allowed-context inspection.
- Explicit action serialization through JSON schema.
- Workspace read/write boundary enforcement.
- One-file write or patch-oriented edit discipline.
- Validation command declaration.
- Evidence ledger shape for inspectable runs.
- Gate review for risky or boundary-crossing actions.
- Local-model endpoint abstraction through environment variables.
- Dev-to-publish sanitization policy.
- Public-safe harness taxonomy for simple, lite, planner, simulator, gate, orchestrator, and validator harnesses.

## Kits / harnesses identified

Because this repository is a public bootstrap, the current “kits” are best treated as harness-kit definitions and schemas rather than runnable kit packages.

| Kit / harness | Status | Offered service |
|---|---:|---|
| `simple-harness` | Placeholder docs | Smallest bounded file-aware action loop. |
| `lite-harness` | Placeholder docs | Compact local-model-friendly loop with context fetches and patch edits. |
| `planner-harness` | Taxonomy only | Converts rough goals into ordered work packets and validation targets. |
| `simulator-harness` | Taxonomy only | Predicts failures, missing requirements, determinism risks, and validation gaps. |
| `gate-harness` | Taxonomy only | Reviews risky or boundary-crossing actions and converts them into mitigated next steps. |
| `orchestrator-harness` | Taxonomy only | Routes larger goals through smaller bounded harnesses and shared ledgers. |
| `validator-harness` | Taxonomy only | Checks whether generated files, commands, schemas, or behavior satisfy requirements. |
| `agent-action-schema-kit` | JSON schema | Defines the allowed action envelope and patch shape. |
| `run-ledger-schema-kit` | JSON schema | Defines auditable run ledger entries. |
| `local-model-runtime-adapter` | Docs/env example | Describes an OpenAI-compatible local/external model endpoint boundary. |
| `dev-to-publish-sanitizer` | Docs/policy | Defines the export rule and denylist between private Dev and public Publish. |

## Gaps / risks

- Runnable public harness source is not present yet.
- `harness-manifest.example.json` is listed in README but was not surfaced during this pass; confirm whether it exists or needs to be added.
- The public repo’s `dev-to-publish-model.md` says `.agent/` should not be copied into public releases; this tracker is intentionally public-safe because the current task required root `/.agent` documentation. Future policy should clarify whether public publish mirrors should keep `.agent` notes or only central-ledger notes.
- Harness taxonomy is strong, but there is no registry/manifest that maps harness names to services, schemas, gates, and runtime expectations.
- No smoke harness proves schema examples round-trip yet.
- No examples demonstrate a full ledger entry from goal to finalize.

## Recommended next work

1. Add `schemas/harness-manifest.schema.json` and a public-safe `harness-manifest.example.json`.
2. Add minimal runnable `simple-harness` source that can perform a dry-run action selection without touching external systems.
3. Add a `lite-harness` patch planner that only emits schema-valid actions and ledger entries.
4. Add schema fixtures for `PLAN_GOAL`, `READ_FILES`, `PATCH_FILE`, `VALIDATE`, and `FINALIZE`.
5. Add a smoke script that validates example action and ledger JSON against schemas.
6. Add a public-safe “first run” example that produces one ledger entry from a sample goal.
7. Clarify the `.agent` policy for publish mirrors: either allow public-safe `.agent` tracker notes or move all agent-run docs to `LuminaryLabs-Dev/LuminaryLabs` only.
8. Add a harness registry document that names each harness, domain boundary, accepted actions, service promises, and validation responsibilities.

## Suggested DSK alignment

Map the current harness concepts into Nexus Engine/Realtime style DSK boundaries:

```txt
goal-intake-domain-kit
  -> action-selection-domain-kit
  -> workspace-boundary-domain-kit
  -> file-operation-domain-kit
  -> validation-gate-domain-kit
  -> evidence-ledger-domain-kit
  -> handoff-or-finalize-domain-kit
```

The key design move is to keep each agent step explicit and inspectable, then allow orchestrators to compose multiple bounded harnesses without giving hidden autonomous authority.

## Files reviewed

- `README.md`
- `docs/architecture.md`
- `docs/dev-to-publish-model.md`
- `docs/harness-taxonomy.md`
- `docs/local-model-runtime.md`
- `harnesses/simple/README.md`
- `harnesses/lite/README.md`
- `schemas/agent-action.schema.json`
- `schemas/run-ledger.schema.json`
