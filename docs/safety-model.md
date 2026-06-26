# Safety Model

NexusAgent treats model output as untrusted instructions until a harness verifies it.

## Safety principles

1. The model should not receive implicit authority.
2. Every action should have a type, target, and boundary.
3. File writes should be path-checked before promotion.
4. Command execution should be explicit and allowlisted.
5. Network access should be opt-in.
6. Publish/deploy/send actions should require a human-controlled gate.
7. Run evidence should be written to ledgers, not hidden in transient state.

## Unsafe by default

The following should be disabled unless a harness explicitly enables and scopes them:

- shell execution,
- file writes outside a workspace,
- browser automation,
- external network calls,
- credential access,
- deployment,
- repository pushes,
- email or message sending.

## Public repository safety boundary

The public repository should not contain real secrets, local endpoints, private logs, generated run artifacts, private memory, or internal automation state.

## Human review points

Human review is required before:

- broadening a workspace boundary,
- adding command execution,
- adding publishing workflows,
- exposing a new harness publicly,
- copying material from private Dev to public Publish.
