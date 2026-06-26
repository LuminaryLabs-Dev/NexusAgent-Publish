# Local Model Runtime

NexusAgent should be able to talk to any OpenAI-compatible local model endpoint.

## Runtime abstraction

Harnesses should depend on environment variables rather than a specific desktop app or private machine address.

Recommended public variables:

```text
NEXUS_AGENT_BASE_URL=http://127.0.0.1:8080/v1
NEXUS_AGENT_MODEL=local-model
```

## Supported runtime shapes

### Local desktop

A user runs a local model server on their own machine and points NexusAgent at it.

### CI smoke test

A workflow downloads a small public model and starts a lightweight OpenAI-compatible server for a short validation run.

### External compatible endpoint

A user may point NexusAgent at any compatible endpoint they control.

## Public safety rule

Do not commit real endpoints, API keys, private LAN addresses, model credentials, or machine-specific paths.

Use examples only.
