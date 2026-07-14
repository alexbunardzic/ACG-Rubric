---
id: HUMAN-01
domain: Human Accountability
status: draft
core: true
since: v0.1
---

# HUMAN-01 — A named accountable human exists for every change

## Criterion

For every change in which an agent made a material contribution, a named human — not a role, not a team, not a rotating oncall — is recorded as accountable. That person is expected to be able to answer questions about the change after it has shipped.

## Why it matters

Accountability is not blame; it is the presence of an answerable party. Without a named human, "the AI did it" becomes a defence rather than a description. A team with no accountable human per change has, effectively, no one to ask about anything six months later.

## How it's assessed

- For a sampled change, ask "who is accountable for this?"
- Confirm the answer is a person, not a role or team.
- Confirm the answer is recorded in the change's metadata, not recovered from memory.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: partial — GOVERN function, accountability structures.
