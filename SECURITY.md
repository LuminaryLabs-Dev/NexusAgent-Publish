# Security Policy

## Reporting a vulnerability

Please report security concerns privately through the repository owner or the Luminary Labs security contact channel rather than opening a public issue with exploit details.

Include:

- affected file or component,
- the behavior you observed,
- reproduction steps if safe to share,
- expected impact,
- suggested mitigation if known.

## Public boundary

This public repository should not contain credentials, private endpoints, `.env` files, run transcripts, scratchpads, automation state, generated artifacts, private benchmark evidence, or local machine paths.

## Agent safety model

NexusAgent harnesses should treat model output as untrusted until parsed, bounded, validated, and recorded. File writes, command execution, browser automation, network calls, and publishing actions must be explicit, scoped, and auditable.
