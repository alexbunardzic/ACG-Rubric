---
id: VER-03
domain: Verification Integrity
status: draft
core: false
since: v0.1
---

# VER-03 — Failing verification blocks merge

## Criterion

Verification is enforcing, not advisory. A change whose verification fails cannot be merged into the codebase absent an explicit, recorded override by a named human.

## Why it matters

Verification that can be silently skipped is not verification. This criterion ensures the check has teeth: an override is possible, but never invisible.

## How it's assessed

- Inspect the merge gates configured on the codebase.
- Confirm failing verification blocks merge by default.
- Confirm any override is recorded with a named human and a reason.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: none
