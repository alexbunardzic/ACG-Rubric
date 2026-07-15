---
id: PROV-01
domain: Provenance
status: draft
core: false
since: v0.1
---

# PROV-01 — Provenance is reconstructable

## Status note

This criterion is intentionally **`status: draft` and `core: false`** in v0.1, and it will remain so until an evidence session produces a concrete "why did this ship?" archaeology story that anchors the Meets and Does not meet examples below — the same discipline that anchors [SPEC-03](../SPEC/SPEC-03.md) in the Detent finding.

The criterion is defined here in advance because other criteria (notably [SPEC-03](../SPEC/SPEC-03.md), via the [agent-authored change](../../glossary.md#agent-authored-change) definition in the glossary) already rely on the *practice* PROV-01 describes. What has not yet been earned is the right to treat PROV-01 as **binding**. Ship a badge decision on a labelled-draft criterion, and the first denied applicant will point at `status: draft` and win.

Promotion to `status: active` and `core: true` follows the process in [`../../../GOVERNANCE.md`](../../../GOVERNANCE.md) and requires (a) the anchoring incident, (b) written Meets and Does not meet grounded in that incident.

## Criterion

For any shipped [agent-authored change](../../glossary.md#agent-authored-change), the chain from shipped code back to (a) the prompt or instruction that produced it, (b) the [accountable human](../../glossary.md#accountable-human) who accepted it, and (c) the [specification](../../glossary.md#specification) it was meant to satisfy is reconstructable **from recorded evidence** — not from operator memory, not from chat history that has since expired, not from after-the-fact inference.

The chain must be reproducible **without the presence of any specific person**, and **within the time bar the team declares for its incident-response and audit obligations**. In the absence of a declared bar, "on demand" means within one business day.

## Why it matters

Provenance is what allows a team to answer "why did this ship?" after the fact. Without it, incident response degrades to archaeology — and when the operator has moved on, archaeology degrades to speculation.

The clause "without the presence of any specific person" is doing load-bearing work: the failure this criterion prevents is the one where provenance existed while a particular person was on the team and evaporated when they left. A chain that only one person can reconstruct is not a chain; it is that person's memory.

## How it's assessed

- Draw a sample of shipped agent-authored changes per the sampling policy in [`../../../assessment/method.md`](../../../assessment/method.md#sampling). The assessor draws the sample; the team does not choose.
- For each sampled change, request the full chain: shipped code → prompt or instruction → accountable human → specification.
- Confirm each link is retrieved from a durable, recorded location, not reconstructed from memory or inferred from context.
- Confirm the chain can be produced **without the presence of the operator who ran the agent**, and within the declared time bar.
- **Aggregation:** this is a binary-per-change criterion. A single failure in the sample fails the criterion; there is no partial credit against the sample size.

## Meets

_TBD — pending an incident-derived example. See the Status note above. The archetype an anchored Meets would describe: a repository where each shipped change has, in machine-readable form attached to the commit or PR, a pointer to the prompt/instruction that produced it, the reviewing human, and the specification version — and where an assessor with no prior context can retrieve the chain for a randomly sampled six-month-old change within an hour, using only what is committed to the repo and adjacent durable stores._

## Does not meet

_TBD — pending an incident-derived example. See the Status note above. The archetypal failure this criterion exists to prevent: an incident occurs, the team wants to know which prompt produced the offending change, the operator has left, the coding assistant's chat history expired after 30 days, no per-change prompt record was retained, and the reconstruction devolves into "we think it was probably the ticket about pagination." This is the story; it is not yet **the** story. Until an evidence session records a real one, this section is a placeholder, not evidence._

## Scope note

This criterion addresses whether the chain is reconstructable, not whether the specification it references is correct ([EVOLVE-02](../EVOLVE/EVOLVE-02.md)) or whether the accountable human's review was substantive ([HUMAN-02](../HUMAN/HUMAN-02.md)).

The definition of "agent-authored" is in the [glossary](../../glossary.md#agent-authored-change); this criterion is the operational check that the recorded evidence exists to make that definition applicable in practice. Other criteria depend on this definition definitionally; only this criterion depends on it for scoring.

## Mappings

- **OWASP LLM Top 10: none.** Practice-level reconstructability of AI-assisted changes is not addressed. See [`../../../mappings/unmapped.md`](../../../mappings/unmapped.md).
- **OWASP Agentic Top 10: partial** — related to agent action recording; see [`../../../mappings/owasp-agentic-top10.md`](../../../mappings/owasp-agentic-top10.md).
- **NIST AI RMF: partial** — MANAGE function, incident response.
