# Harness Taxonomy

NexusAgent is a family of harness patterns, not one monolithic agent.

## Simple harness

A small linear loop for bounded file-aware work.

Typical actions:

- plan,
- read allowed files,
- write one bounded file,
- validate,
- finalize.

## Lite harness

A compact harness intended for small local models and repeatable agent turns.

Typical additions:

- compact action selection,
- patch-oriented edits,
- context fetching,
- bounded child-agent requests,
- explicit validation.

## Planner harness

Turns a rough goal into ordered work packets, success criteria, and validation targets.

## Simulator harness

Predicts likely failures, missing requirements, determinism risks, and validation gaps before work begins.

## Gate harness

Reviews risky or boundary-crossing actions and converts them into mitigated next steps.

## Orchestrator harness

Coordinates larger goals by routing work through smaller bounded harnesses and shared ledgers.

## Validator harness

Checks whether generated files, commands, schemas, or visible behavior satisfy the requirement boundary.

## Public bootstrap note

This taxonomy documents the intended shape. Runnable public harness source should be added gradually after review.
