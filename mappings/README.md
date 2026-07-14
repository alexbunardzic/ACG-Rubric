# Mappings — Read This First

This directory maps ACG Rubric criteria to existing frameworks: OWASP LLM Top 10, OWASP Agentic Top 10, and NIST AI RMF. The mappings exist for a specific and narrow reason. **The gaps are the point.**

## What the mappings are for

Two things, and only two:

1. **Legibility.** Teams and regulators already use these frameworks. Where an ACG criterion aligns with one, the mapping shortens the conversation.
2. **Locating the gaps.** By writing the mappings honestly, we can identify criteria in the ACG Rubric that have **no equivalent** in any established framework. Those are catalogued in [`unmapped.md`](unmapped.md).

## What the mappings are not for

- **They are not an equivalence claim.** Passing OWASP LLM Top 10 does not imply passing the ACG Rubric, and vice versa. The scopes are different: OWASP LLM addresses application-level risks of LLM-integrated systems, whereas the ACG Rubric addresses the integrity of the practice by which code is produced. There is overlap. There is not identity.
- **They are not a substitution.** A team cannot use OWASP compliance to skip ACG criteria, or vice versa. The mappings say "these are related", not "these are the same".
- **They are not a scoring conversion.** The frameworks score differently. There is no lookup table.

## How to read a mapping file

Each framework has its own file. Within it:

- **Direct correspondence.** The ACG criterion and the framework item address the same risk from the same angle. This is rare.
- **Partial correspondence.** They address related risks, but one covers ground the other does not. This is the common case, and the mapping note explains which side is broader.
- **Adversarial correspondence.** Both address the same territory but with different assumptions about what "good" looks like. Notes explain the disagreement.
- **No correspondence.** The ACG criterion has no counterpart in this framework. It is catalogued here and in [`unmapped.md`](unmapped.md).

## Why unmapped criteria matter

An ACG criterion with no counterpart in OWASP or NIST is a claim: this rubric is asserting that something matters which the established frameworks do not yet address. That claim needs to be defensible. Every entry in [`unmapped.md`](unmapped.md) links back to the evidence that justifies the criterion's existence. If the claim cannot be defended, the criterion should be removed. If it can, the gap is precisely the reason the ACG Rubric exists.

## Maintenance

Mappings are re-checked whenever a source framework releases a new version, and whenever an ACG criterion is added or changed. Version numbers of the source frameworks are recorded in each mapping file. When a framework moves, the mapping is updated; the [`CHANGELOG.md`](../CHANGELOG.md) records the update.
