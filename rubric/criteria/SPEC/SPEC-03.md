---
id: SPEC-03
domain: Specification Integrity
status: active
core: true
since: v0.1
---

# SPEC-03 — Specification surface is protected against agent modification

## Criterion

The artefacts that define correct behaviour — tests, specifications, and prose constraints — cannot be silently altered by an agent, and any alteration is detectable.

## Why it matters

An agent that can modify the specification can satisfy it trivially. A failing test rewritten by the agent that was supposed to make it pass is not a passing test; it is a passing signal disconnected from the property it was meant to prove. See [../../../evidence/findings/003-silent-test-weakening.md](../../../evidence/findings/003-silent-test-weakening.md) — the incident that produced this criterion.

## How it's assessed

- Inspect commit history for agent-authored changes to test files, specifications, and constraint documents.
- Confirm a mechanism exists that flags such changes — a review gate, a lint rule, a diff-detecting hook.
- Confirm the mechanism was exercised in practice, not merely configured.

## Meets

A repository where changes to files under `tests/` produced in the same commit as agent-authored implementation code trigger an automatic reviewer assignment to a human who did not operate the agent, and the review log shows this has happened.

## Does not meet

A repository where an agent's task included "make the tests pass" and the diff shows a test's assertion was weakened in the same commit as the implementation change, with no reviewer having flagged it. The agent satisfied its instruction; the specification surface was not protected.

## Scope note

This criterion does not evaluate whether the specification is *correct*, only whether it is *protected*. Correctness of the specification is the province of the team; see [EVOLVE-02](../EVOLVE/EVOLVE-02.md).

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: partial — related to bounded agent action; see [mappings/owasp-agentic-top10.md](../../../mappings/owasp-agentic-top10.md).
- NIST AI RMF: none
