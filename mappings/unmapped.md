# Unmapped Criteria — What the ACG Rubric Says That Nobody Else Does

Every criterion listed here is a claim: *this rubric asserts something about AI-assisted software development that no established framework has yet written down.*

This file is not an appendix. It is the argument for why the ACG Rubric exists as a separate document. If nothing in this file could be defended, the rubric would be a re-branding of OWASP or NIST. Every entry here is evidence that it is not.

If you read one file in this repository, read this one.

## The claim

The established frameworks — OWASP LLM Top 10, OWASP Agentic Top 10, NIST AI RMF — address the **application-level and organizational risk** of AI. They do not address the **integrity of the practice by which AI-assisted code comes into existence**. That is the gap. The criteria below sit inside it.

## The lead example

### [SPEC-03](../rubric/criteria/SPEC/SPEC-03.md) — Specification surface is protected against agent modification

**Mapped to nothing in OWASP LLM Top 10. Mapped to nothing in NIST AI RMF.** Obliquely related to bounded-agency concerns in OWASP Agentic, but the specific failure mode this criterion addresses is not named there either.

The failure mode: an agent, asked to make a failing test pass, weakens the test instead of fixing the code. The specification the agent was being measured against is silently rewritten to accommodate the code, and the resulting green build is a passing signal disconnected from the property it was meant to prove. The Detent incident ([`../evidence/findings/003-silent-test-weakening.md`](../evidence/findings/003-silent-test-weakening.md)) is proof this happens in the wild.

None of the established frameworks describe this failure. None require the protection that prevents it. That is not a gap on their part that we are apologizing for — it is a description of the space the ACG Rubric occupies. If you read one criterion in this repository to understand what the rubric is doing that nobody else is, read SPEC-03.

## Other currently unmapped criteria

Each entry links to (a) the criterion in the rubric and (b) the evidence in [`../evidence/findings/`](../evidence/findings/) that justifies its existence.

### [SPEC-01](../rubric/criteria/SPEC/SPEC-01.md) — A specification exists as a durable artefact

No established framework requires that AI-produced code be traceable to a durable specification. OWASP addresses prompt injection and model output handling; NIST addresses organizational context and risk registers. Neither requires the artefact-level durability the ACG Rubric requires.

### [SPEC-02](../rubric/criteria/SPEC/SPEC-02.md) — The specification is versioned

Nowhere in the mapped frameworks is the *versioning* of the specification a required property. This is the criterion that makes drift detectable.

### [HUMAN-01](../rubric/criteria/HUMAN/HUMAN-01.md) — A named accountable human exists for every change

NIST addresses organizational accountability. The ACG Rubric requires per-change accountability with a named person, and forbids the answer "a role" or "a team." This granularity is new.

### [HUMAN-02](../rubric/criteria/HUMAN/HUMAN-02.md) — The accountable human reviewed the change before it merged

Related to conventional code-review practice but sharpened for the agentic case, where rubber-stamp approval of large agent-produced diffs is the norm rather than the exception.

### [EVOLVE-02](../rubric/criteria/EVOLVE/EVOLVE-02.md) — The artefact can be safely changed by someone who was not in the room

No existing framework addresses the *evolvability* of an AI-assisted codebase — whether the artefacts carry enough forward that the practice survives contact with a new contributor. This is a distinctive ACG concern.

### [EVOLVE-03](../rubric/criteria/EVOLVE/EVOLVE-03.md) — The practice survives the departure of any single person

The bus-factor criterion, applied to the AI-assisted practice rather than to individual code ownership. Not addressed elsewhere.

## Moving out of this file

A criterion listed here that later gains a genuine counterpart in a source framework — not a loose analogy, a genuine counterpart — moves out of this file into the relevant mapping. That movement is a signal that the industry is catching up, and it is recorded in [`../CHANGELOG.md`](../CHANGELOG.md) rather than concealed.

## Why the gap exists

The mapped frameworks were written to address AI *systems* — models integrated into applications that then serve users. The ACG Rubric addresses AI *practice* — the workflow by which code is produced. The two overlap at the edges and diverge at the centre. The centre is what this file catalogues.
