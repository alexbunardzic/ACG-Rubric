---
id: SPEC-01
domain: Specification Integrity
status: active
core: true
since: v0.1
---

# SPEC-01 — A specification exists as a durable artefact

## Criterion

For any change in which an agent made a material contribution, a specification exists as a durable artefact that the agent was pointed at, and that is addressable after the change has shipped. A chat transcript, a ticket title, or a verbal instruction does not satisfy this criterion; the specification must be a file, a versioned document, or a record in a system that survives the session that produced the code.

## Why it matters

The most common failure mode in AI-assisted development is that the code exists but the instruction that produced it does not. When something breaks six months later, the team can read the code but cannot recover the intent — what the code does becomes, retroactively, what it was supposed to do. Drift becomes invisible because the reference against which drift could be measured has been deleted.

## How it's assessed

- Sample a change in which an agent made a material contribution; the team does not choose the sample.
- Ask to see the specification artefact the change was produced against.
- Confirm a durable link exists from the change (commit, PR, or equivalent) to the specification.

## Meets

A commit whose message references a specification file at a specific version (e.g. `spec/checkout-flow.md@a3f2c1`), where that file existed before the change and is retrievable after.

## Does not meet

A change whose only "specification" is the prompt history in a coding assistant, retained only for the duration of the session and inaccessible from outside the tool. The team can describe the intent in a meeting; they cannot produce the artefact.

## Scope note

This criterion establishes only that a specification exists and is addressable. It does not test whether the specification is versioned ([SPEC-02](SPEC-02.md)) or protected from modification ([SPEC-03](SPEC-03.md)).

## Mappings

- OWASP LLM Top 10: none
- OWASP Agentic Top 10: none
- NIST AI RMF: partial — MAP function, context establishment.
