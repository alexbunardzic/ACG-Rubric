---
id: VER-02
domain: Verification Integrity
status: draft
core: false
since: v0.1
---

# VER-02 — Verification is independent of the agent that produced the code

## Criterion

The verification of a change is not produced by, evaluated by, or solely reviewed by the same agent invocation that produced the change. Independence may be provided by a human reviewer, a separate agent invocation with its own context, or an out-of-band test suite the agent did not author for this change.

## Why it matters

An agent that both writes and verifies its own work verifies its own understanding of the task. This is not independent evidence. A system that self-certifies is not verified at all — it is expressed confidence.

## How it's assessed

- Trace the verification back to its author.
- Confirm the author is not the same agent invocation that produced the code under verification.
- Confirm the verification was not derived from the same prompt or context that produced the code.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: partial — related to bounded agent action.
- NIST AI RMF: partial — MEASURE function.
