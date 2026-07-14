# Expiry and Revocation

This is the load-bearing document of the badge scheme. If badges could be issued but never lost, the rubric would be a certificate mill. The value of holding a badge is proportional to the credibility of losing one.

## These rules apply to the authors identically

Before anything else: **these rules apply to Guild members, ACG core team, and the rubric's founders on the same terms as any other badge holder.** No exemption exists for the people who wrote the rubric. Any badge held by an author is subject to the same expiry, the same revocation triggers, the same public register, and the same appeal process as a badge held by a client.

This clause is what makes the whole strategy credible. It is not an aspiration; it is a rule this document enforces on itself. If the register in [`register.md`](register.md) ever shows a founder's badge protected from a rule that would apply to anyone else, the credibility of the scheme is forfeit. The founders adopted this clause while nothing was at stake, so that when something is at stake it will not be adopted.

## Every badge expires

There is no permanent badge. All three levels — Practitioner, Product, Organization — carry an expiry date at issue.

| Badge | Term | Renewal |
| --- | --- | --- |
| Practitioner | 12 months | Full reassessment |
| Product | 12 months | Full reassessment, or on any material change to the practice |
| Organization | 24 months | Full reassessment, with an interim attestation at 12 months |

A badge past its expiry date is **not valid**. It is not "grace period" valid, not "renewal pending" valid. If the register in [`register.md`](register.md) shows an expired badge, it is displayed as expired.

## Material change triggers renewal

A Product badge lapses immediately on any of the following, regardless of how much time is left on the term:

- The team changes the primary AI coding tool or agent framework.
- The team changes the accountable human without transferring the practice in a documented way.
- The verification chain (test infrastructure, review workflow, or merge gates) is materially altered.
- The specification workflow is materially altered.

"Material" is judged against the description of the practice recorded in the last assessment. The team is expected to declare material changes; failure to declare is grounds for revocation, not merely lapse.

## Revocation

A badge can be revoked before its expiry date. Grounds for revocation:

1. **Discovery that the practice does not match what was assessed.** If evidence emerges — from an incident, a whistleblower, a subsequent assessment — that the practice differed materially from what the assessor was shown, the badge is revoked.
2. **Failure to declare a material change.** See above.
3. **Undisclosed conflict of interest in the original assessment.** If it emerges that the assessor had a conflict that was not disclosed, all badges issued under that engagement are reviewed.
4. **Assessor misconduct.** If the assessor is found to have issued a badge without conducting the assessment as described in [`../assessment/method.md`](../assessment/method.md), affected badges are revoked and the assessment redone.

Revocation is a decision of the maintainers, made on the record, with reasons published. Revocations of author-held badges are decided by maintainers who did not hold the revoked badge; if all maintainers are conflicted, the decision is delegated to an external assessor named in advance in [`../GOVERNANCE.md`](../GOVERNANCE.md).

## The revocation register is public

Revocations are recorded in [`register.md`](register.md) alongside current holders. A team or individual that once held a badge and lost it is visible as such — the register does not silently delete revoked entries. This is deliberate. A badge scheme that hides its failures cannot be trusted about its successes.

Revoked entries include: the badge that was held, when it was issued, when it was revoked, and a one-line reason. The reason is factual, not editorial ("material change not declared", not "the team was careless"). Further detail lives in the incident record if one exists.

## Voluntary surrender

A holder may surrender a badge at any time by opening a PR against [`register.md`](register.md). Voluntary surrender is recorded as such and is not treated as revocation. It is not, however, invisible; the register shows the badge as surrendered.

## Appeal

A revoked party may appeal by opening an issue against the repository. The appeal is reviewed by a maintainer who was not involved in the original revocation. If the appeal succeeds, the register is corrected and the correction itself is logged. If it fails, the appeal and its outcome are recorded.

## What revocation does not do

Revocation does not blacklist a person or team from future badges. A revoked party may pursue a new assessment at any time; the previous revocation is public but is not a bar. The point is that credibility is earned each time, not once.
