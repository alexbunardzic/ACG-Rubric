---
id: AGENT-02
domain: Agent Boundaries
status: draft
core: false
since: v0.1
---

# AGENT-02 — Agent permissions are bounded and enumerable

## Criterion

The set of actions an agent may take — file paths it may read or write, commands it may execute, external systems it may reach — is bounded by explicit configuration and can be enumerated on demand. An agent whose permissions are "whatever the operator's shell can do" fails this criterion.

## Why it matters

An unbounded agent is an unbounded blast radius. A team that cannot list what its agent is allowed to do cannot reason about what happens when the agent misbehaves. This is the difference between "the agent behaved well" and "the agent could not have behaved otherwise."

## How it's assessed

- Ask for the enumeration of agent permissions in a durable artefact.
- Confirm the enumeration matches what the agent is actually configured to do.
- Confirm the boundary is enforced by configuration, not by convention or trust.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: partial — LLM06 Excessive Agency.
- OWASP Agentic Top 10: direct.
- NIST AI RMF: partial.
