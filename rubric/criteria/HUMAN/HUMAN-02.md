---
id: HUMAN-02
domain: Human Accountability
status: draft
core: true
since: v0.1
---

# HUMAN-02 — The accountable human reviewed the change before it merged

## Criterion

The named accountable human for a change read the diff, understood the intent, and recorded acceptance before the change was merged. Rubber-stamp approval does not satisfy this criterion; the review must be traceable to specific content.

## Why it matters

Accountability without review is fiction. This criterion exists to prevent the pattern where a human's name is attached to a change they never looked at.

## How it's assessed

- Inspect the review record for a sampled change.
- Compare the size of the change against the interval between opening and approval.
- Confirm the approval was recorded by the accountable human, not by automation on their behalf.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: partial — GOVERN function.
