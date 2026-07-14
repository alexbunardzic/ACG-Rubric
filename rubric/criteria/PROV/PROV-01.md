---
id: PROV-01
domain: Provenance
status: draft
core: true
since: v0.1
---

# PROV-01 — Provenance is reconstructable

## Criterion

For any shipped change in which an agent made a material contribution, the chain from shipped code back to the prompt or instruction that produced it, the accountable human who accepted it, and the specification it was meant to satisfy is reconstructable on demand.

## Why it matters

Provenance is what allows a team to answer "why did this ship?" after the fact. Without it, incident response degrades to archaeology.

## How it's assessed

- For a sampled change, request the full chain from code back to prompt, human, and specification.
- Confirm each link is recorded, not reconstructed.
- Confirm the chain can be produced without the presence of the operator.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: partial.
- NIST AI RMF: partial — MANAGE function.
