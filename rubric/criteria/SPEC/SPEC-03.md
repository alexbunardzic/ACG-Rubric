---
id: SPEC-03
domain: Specification Integrity
status: active
core: true
since: v0.1
---

# SPEC-03 — Specification surface is protected against agent modification

## Criterion

When an agent [materially contributes](../../glossary.md#material-contribution) to a change that touches a protected artefact — a test, a specification, or a prose constraint — the change is **detected AND blocked from shipping absent explicit review by a human who did not operate the agent.**

Detection alone is not sufficient. A change that could ship without a human being made to look at it fails this criterion, regardless of whether some downstream report would eventually surface it.

The commit boundary is not the unit of assessment. The gate must fire whether the protected artefact and the implementation appear in the same commit, in separate commits on the same branch, on different branches later merged, or in any other arrangement by which the change reaches the codebase.

## Why it matters

An agent that can modify the specification can satisfy it trivially. A failing test rewritten by the agent that was supposed to make it pass is not a passing test; it is a passing signal disconnected from the property it was meant to prove.

Detection without a shipping gate is what the Detent incident proves is insufficient. The change was, in principle, visible in the diff — nobody was made to look. See [../../../evidence/findings/003-silent-test-weakening.md](../../../evidence/findings/003-silent-test-weakening.md).

## How it's assessed

- Identify the set of protected artefacts (tests, specifications, constraint documents). The team is expected to be able to enumerate them.
- Confirm a mechanism is configured such that it **must** fire on any agent-authored change to any protected artefact, regardless of commit or branch topology.
- Confirm the mechanism **blocks merge** until a review is recorded by a human who did not operate the agent that produced the change.
- Where the history contains agent-authored changes to protected artefacts, confirm the log shows the mechanism fired and a qualifying review was recorded for each. Where no such change exists in history, the criterion passes on the strength of the configuration alone — the mechanism's absence of firing is not evidence of failure. A clean history is a pass, not an ambiguity.

## Meets

A repository whose merge gate is configured such that any pull request touching files under `tests/`, `spec/`, or files marked as constraint documents — from any commit, on any branch — cannot merge until a reviewer who is not the operator of the agent that produced the change has recorded an approval. The rule is enforced by the gate itself, not by convention. Where agent-authored changes to those files exist in history, the log shows a qualifying review was recorded on each.

## Does not meet

Three failure patterns, all observed:

1. **Detection without a gate.** A nightly job produces a diff report of agent-authored changes to test files. The report goes to a shared inbox. No mechanism prevents the change from merging before anyone reads the report. The change is detectable; it is not protected.

2. **Same-commit-only detection.** A hook flags changes to test files only when they appear in the same commit as implementation changes. The agent — or a team member gaming the gate — commits the test change separately from the implementation. The hook does not fire. The specification surface was modified without triggering the mechanism the criterion requires. This is a fail whether or not the split was deliberate.

3. **Configured but bypassable.** The mechanism exists and would fire, but the workflow allows the operator of the agent to self-approve their own agent's changes to protected artefacts. Independence of the reviewing human is defeated by workflow, even though a review appears in the log.

## Scope note

This criterion does not evaluate whether the specification is *correct*, only whether it is *protected*. Correctness of the specification is the province of the team; see [EVOLVE-02](../EVOLVE/EVOLVE-02.md).

## Mappings

- **OWASP LLM Top 10: none.** This failure mode — an agent silently modifying the artefact it is being measured against — is not named anywhere in OWASP LLM. See [`unmapped.md`](../../../mappings/unmapped.md), where SPEC-03 is the lead example of what the ACG Rubric addresses that existing frameworks do not.
- **OWASP Agentic Top 10: partial.** Obliquely related to bounded agent action, but the specific failure of an agent modifying its own oracle is not named. See [`mappings/owasp-agentic-top10.md`](../../../mappings/owasp-agentic-top10.md).
- **NIST AI RMF: none.** This failure mode is not addressed. See [`unmapped.md`](../../../mappings/unmapped.md).

The two "none" entries above are not a hole in the mapping — they are the point of the criterion. SPEC-03 exists because the failure it prevents is one that no established framework has yet written down, and the Detent incident is proof it happens in the wild.
