# NexusAgent Architecture

NexusAgent is a local-first harness architecture for bounded agent work.

The system is built around a simple operating rule:

```text
Goal -> bounded action -> evidence -> validation -> next step or stop
```

## Core components

### Harness

A harness owns the loop rules. It decides what actions are allowed, where files may be read or written, how model output is parsed, and how evidence is recorded.

### Action

An action is one explicit operation selected by the agent. Examples include planning, reading files, writing one file, patching one file, validating, or finalizing.

### Workspace

A workspace is the allowed file boundary for a run. Agent writes should stay inside the configured workspace unless a human explicitly grants a broader boundary.

### Ledger

A ledger records what happened. A useful ledger should preserve the goal, selected action, result, validation evidence, and next step.

### Gate

A gate checks whether a step is safe enough to continue. Gates may validate paths, command allowlists, schema shape, generated files, tests, or human-visible requirements.

## Design priorities

- local-first execution,
- explicit boundaries,
- small inspectable actions,
- reproducible run evidence,
- human-readable ledgers,
- public-safe configuration,
- no hidden autonomous authority.

## Public bootstrap scope

This repository starts with documentation, examples, schemas, and harness placeholders. Private Dev artifacts, scratchpads, automation state, and run outputs are intentionally excluded.
