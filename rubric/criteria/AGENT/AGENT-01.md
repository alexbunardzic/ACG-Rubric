---
id: AGENT-01
domain: Agent Boundaries
status: draft
core: true
since: v0.1
---

# AGENT-01 — The agent's identity is known per action

## Criterion

For any action taken by an agent that affects the codebase, the identity of the agent — the tool, the model, and the model version — is recorded and recoverable.

## Why it matters

Provenance requires knowing what produced a change. "An AI wrote this" is not identity; it is a category. Model behaviour changes across versions, and a team that cannot say which model produced which change cannot investigate a regression that came in with a model update.

## How it's assessed

- For a sampled agent-produced change, ask which tool, model, and version produced it.
- Confirm this information is recorded in a durable location, not reconstructed from memory.
- Confirm the record can be retrieved without the presence of the operator.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: partial — LLM03 Supply Chain.
- OWASP Agentic Top 10: partial.
- NIST AI RMF: partial — MAP and MANAGE functions.
