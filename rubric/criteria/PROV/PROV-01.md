---
id: PROV-01
domain: Provenance
status: active
core: true
since: v0.1
---

# PROV-01 — Agent authorship is attributable from recorded evidence

## Criterion

The team can produce, on demand and **from recorded evidence**, the set of shipped changes to which an agent [materially contributed](../../glossary.md#material-contribution) in the assessment period.

"Recorded evidence" means a durable per-change record that survives the session that produced the change and can be retrieved without the presence of the person who operated the agent. Operator memory, chat history that expires with a session, and inference from code style are **not** recorded evidence.

This criterion is the **substrate** on which [SPEC-03](../SPEC/SPEC-03.md), [HUMAN-01](../HUMAN/HUMAN-01.md), [PROV-02](PROV-02.md), and [PROV-03](PROV-03.md) all depend. A team that cannot answer "which of last month's shipped changes were agent-authored?" cannot pass any criterion whose scope is agent-authored changes — those criteria would collapse into "we didn't have any" by default. Closing that loophole is what PROV-01 exists to do.

## Why it matters

Every criterion in the rubric that scopes itself to agent-authored changes assumes the team can identify those changes reliably. If they cannot, "we had none" is the trivial pass, and the rubric is defeated at the substrate level — every other assessment is built on sand.

This is why PROV-01 is the first criterion to be active and core: the rest of the rubric leans on it, and it must be sound before anything above it can be.

## How it's assessed

- Ask the team to produce the list of shipped changes from the assessment period that they consider agent-authored under their [declared material-contribution policy](../../glossary.md#material-contribution).
- Confirm the list is produced from a durable record — a per-change flag, a commit trailer, a repository log, a build attestation — not from memory, not by asking each operator individually.
- **Spot-check.** Draw a sample of shipped changes independently (per the sampling policy in [`../../../assessment/method.md`](../../../assessment/method.md#sampling)) and, for each, verify the team's list is correct about whether the change was agent-authored. If a sampled change should be on the list and is not, the substrate is not trustworthy and the criterion fails.
- **Aggregation:** binary-per-change. A single misclassification in the sample fails the criterion.

## Meets

A repository where every merge to `main` is annotated at commit time with a machine-readable flag stating whether the change was agent-authored under the team's declared policy, and the flag is set by the review workflow — not by a template default the author can leave unchanged without noticing. On a random sample of 20 changes drawn by the assessor from the last 90 days, the team's agent-authored list correctly classifies all 20.

## Does not meet

Three failure patterns, all observed:

1. **"Ask the operator."** The team can produce the list only by messaging each operator and asking them to remember which of their recent changes used the assistant. There is no durable record; the list is manufactured on demand from memory. Fails — the record is not durable, and the operator's departure would collapse the substrate entirely.

2. **Optional flag, left blank.** A per-change flag exists but is optional and defaults to "no." Half the sampled changes are unflagged despite obvious agent involvement (large blocks of code that match the assistant's characteristic patterns, referenced in the review thread as agent-produced). The record exists on paper; in practice it is not applied. Fails.

3. **Style inference.** The team has no per-change record. Asked how they would produce the list, they say they would review recent diffs and mark the ones that "look like" the assistant wrote them. This is inference, not evidence, and it makes the substrate a matter of opinion. Fails.

## Scope note

This criterion tests the **existence and reliability** of the attribution record. It does not test whether the record captures the model and version ([PROV-02](PROV-02.md)) or whether the full reconstruction chain from code to prompt to accountable human to specification is complete ([PROV-03](PROV-03.md)). PROV-01 is the substrate the other PROV criteria and the attribution-dependent criteria in SPEC and HUMAN build on.

The definition of "agent-authored" is in the [glossary](../../glossary.md#agent-authored-change).

## Mappings

- **OWASP LLM Top 10: none.** The substrate question — "can you identify which of your changes were AI-produced?" — is not addressed anywhere in the frameworks. See [`../../../mappings/unmapped.md`](../../../mappings/unmapped.md).
- **OWASP Agentic Top 10: partial** — related to agent action recording; see [`../../../mappings/owasp-agentic-top10.md`](../../../mappings/owasp-agentic-top10.md).
- **NIST AI RMF: partial** — MAP function, context establishment, but not at per-change granularity.
