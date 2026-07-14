---
id: EVOLVE-02
domain: Evolvability
status: draft
core: false
since: v0.1
---

# EVOLVE-02 — The artefact can be safely changed by someone who was not in the room

## Criterion

A new contributor, six months after a change was made, can determine what the change was supposed to do, what verified it, and where its constraints came from — without interviewing the original author or replaying the AI session.

## Why it matters

Code that requires its original author to interpret it is not evolvable. This criterion tests whether the artefacts produced by the practice — specification, tests, provenance records — carry enough information forward that the practice survives the departure of the people who created it.

## How it's assessed

- Pick a change from at least six months ago.
- Ask a contributor who was not involved in it to reconstruct what it was supposed to do, from artefacts alone.
- Note where they had to guess.

## Meets

_TBD._

## Does not meet

_TBD._

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: none
