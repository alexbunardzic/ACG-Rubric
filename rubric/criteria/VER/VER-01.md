---
id: VER-01
domain: Verification Integrity
status: draft
core: true
since: v0.1
---

# VER-01 — Verification exists

## Criterion

For any change in which an agent made a material contribution, a verification artefact — a test, a check, a review record — was produced and retained before merge.

## Why it matters

"The agent said it works" is not verification. This criterion establishes that some independent check exists at all; [VER-02](VER-02.md) establishes that the check is independent of the agent, and [VER-03](VER-03.md) that failing it blocks merge.

## How it's assessed

- For a sampled change, ask to see the verification artefact.
- Confirm the artefact was produced before the change was merged.
- Confirm the artefact is retained and recoverable after the change has shipped.

## Meets

_TBD — to be drafted from evidence sessions._

## Does not meet

_TBD — to be drafted from evidence sessions._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: partial — MEASURE function.
