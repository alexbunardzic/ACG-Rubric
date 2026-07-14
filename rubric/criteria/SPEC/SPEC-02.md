---
id: SPEC-02
domain: Specification Integrity
status: draft
core: true
since: v0.1
---

# SPEC-02 — The specification is versioned

## Criterion

The specification artefact identified in [SPEC-01](SPEC-01.md) is versioned. A change to the code and a change to its specification are distinguishable events, and the version of the specification that a given code change was produced against is recoverable after the fact.

## Why it matters

An unversioned specification can be silently rewritten to match the code it was supposed to constrain. Once that happens, drift is undetectable and provenance is broken. Versioning is the mechanism that prevents the specification from becoming a moving target.

## How it's assessed

- Confirm the specification lives in a system that tracks versions (git, a versioned wiki, or equivalent).
- For a sampled change, confirm the version-at-change of the specification is recoverable.
- Confirm changes to the specification and changes to the code are recorded as distinct events, not conflated into a single edit.

## Meets

_TBD — to be drafted from evidence sessions._

## Does not meet

_TBD — to be drafted from evidence sessions._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: none
