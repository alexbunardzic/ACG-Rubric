---
id: AGENT-03
domain: Agent Boundaries
status: draft
core: false
since: v0.1
---

# AGENT-03 — Destructive or irreversible actions require human confirmation

## Criterion

Actions with destructive, irreversible, or shared-state consequences — deleting files or branches, force-pushing, dropping database objects, sending outbound messages, publishing to package registries — require an explicit confirmation from a named human before execution. Blanket standing approval does not satisfy this criterion.

## Why it matters

Reversible mistakes are cheap; irreversible ones are not. This criterion establishes that the cost/reversibility asymmetry is respected in configuration, not merely in aspiration.

## How it's assessed

- Enumerate the destructive actions the agent could take.
- For each, confirm a per-action confirmation gate exists.
- Confirm the gate is not routinely bypassed by standing approvals.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: partial — LLM06 Excessive Agency.
- OWASP Agentic Top 10: direct.
- NIST AI RMF: partial.
