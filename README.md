# NexusAgent

NexusAgent is a local-first agent harness project for bounded, auditable software-building loops.

The public repository is intentionally small. It contains public documentation, example goals, schemas, and placeholder harness entrypoints. Private development, experiments, benchmark state, scratchpads, and internal run evidence stay outside this repository.

## Core idea

NexusAgent treats agent work as a sequence of controlled turns:

1. read the goal,
2. inspect allowed context,
3. choose one bounded action,
4. write or validate only inside an allowed boundary,
5. record evidence,
6. stop cleanly or hand off the next step.

This is meant to make long-running agent work inspectable instead of mysterious.

## Public repository layout

```text
NexusAgent/
  README.md
  LICENSE
  SECURITY.md
  CONTRIBUTING.md
  CHANGELOG.md
  .gitignore

  docs/
    architecture.md
    dev-to-publish-model.md
    safety-model.md
    harness-taxonomy.md
    local-model-runtime.md
    public-roadmap.md

  examples/
    goals/
      simple-static-site.md
      local-file-audit.md
    configs/
      openai-compatible.local.example.env

  harnesses/
    simple/
      README.md
    lite/
      README.md

  schemas/
    agent-action.schema.json
    run-ledger.schema.json
    harness-manifest.example.json
```

## What is intentionally not here

The public repo does not include private `.agent` memory, automation state, run outputs, scratchpads, logs, local endpoints, private benchmark evidence, or experimental Dev-only harnesses.

## Status

This is the public bootstrap structure for NexusAgent. Runnable code will be added only after it passes the Dev-to-Publish safety review.
