# Scope — What This Rubric Is Not

This document is a **liability boundary**, not a preamble. It states, in the public rubric itself, what an ACG Rubric assessment is not — so that the gap between what a client assumes and what an assessor delivered cannot be re-litigated afterward on the basis that the boundary was hidden.

It goes here, not only in an engagement letter, because the rubric is the public document. When a dispute arises, the operative question is: **what did the ACG Rubric hold itself out as doing?** The answer is whatever this file says.

## What an ACG Rubric assessment is not

An ACG Rubric assessment is **not**:

### Not a penetration test

The rubric does not attempt to break into the system, exploit vulnerabilities, or evaluate resistance to attack. No adversarial testing is performed. Passing the rubric implies nothing about whether the system can be broken.

### Not a vulnerability assessment

The rubric does not scan for known vulnerabilities, evaluate dependencies for CVEs, or produce a vulnerability inventory. Passing the rubric implies nothing about the presence or absence of known weaknesses in the code, its libraries, or its runtime.

### Not a compliance certification

The rubric is not a substitute for compliance with any regulatory framework — SOC 2, ISO 27001, HIPAA, GDPR, EU AI Act, or any other. Passing the rubric does not satisfy any regulator by itself. Where the rubric overlaps with a compliance regime, the mapping in [`../mappings/`](../mappings/) states so explicitly and narrowly.

### Not a claim that the software is secure

The rubric assesses the **integrity of the practice** by which code was produced, not the security of the resulting artefact. Code produced under an assessed practice can still be insecure. The rubric addresses whether the team can answer questions about how the code came to exist; it does not address whether the code is safe to run.

### Not a claim that the software is correct

The rubric does not verify that the code does what the specification says it does. It verifies that a specification exists, is versioned, is protected, and is linked to the change — not that the code satisfies it. Correctness is the province of the team's own verification, which [VER-01](criteria/VER/VER-01.md) and [VER-02](criteria/VER/VER-02.md) address only at the level of *did verification occur and was it independent*, not *did it succeed*.

### Not a judgement of any individual

A Practitioner badge attaches to a named person. It reflects the practice they can be shown to follow, not their skill, seniority, or worth. Failure to hold or retain a badge is a statement about practice, not character. See [`../badge/expiry-and-revocation.md`](../badge/expiry-and-revocation.md).

### Not a warranty or guarantee

Nothing in an ACG Rubric assessment constitutes a warranty of any kind. An assessor's report describes evidence observed under a defined method at a defined point in time. It does not warrant that the practice will continue as observed, that the code will function as intended, or that the team will remain competent.

## What the rubric does assess

For clarity, and only for clarity — the affirmative scope is defined in [`index.md`](index.md), not here — the rubric assesses whether the team can answer four questions on demand, for any change in which an agent made a material contribution:

1. What was specified?
2. What was verified?
3. Who is accountable?
4. What changed, and where did it come from?

Everything else is out of scope.

## The boundary case: hand-written code

The rubric applies whenever AI agents materially contribute to code that ships. "Materially" is defined in [`glossary.md`](glossary.md). Code written entirely by a human, with AI used only for search or explanation, is out of scope — and does not need a badge.
