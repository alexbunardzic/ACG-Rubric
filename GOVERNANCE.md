# Governance

This document describes how the ACG Rubric changes, who changes it, and what a team relying on the rubric can expect from the process.

## Principles

1. **Nothing changes silently.** Every change to the rubric — a new criterion, a threshold shift, a wording clarification — is recorded in [`CHANGELOG.md`](CHANGELOG.md) with the reasoning.
2. **The rubric is defended, not sold.** Maintainers do not add criteria to satisfy a customer, and do not remove them to avoid an inconvenience. Criteria enter and leave through the process below, on the record.
3. **Failure teaches the rubric.** Every criterion is traceable to a failure — either in the wild, or in a session recorded in [`evidence/`](evidence/). A criterion without a documented reason to exist is a candidate for removal.
4. **The rules apply to the authors identically.** Rubric authors and maintainers hold badges under the same expiry and revocation rules as any other holder. See [`badge/expiry-and-revocation.md`](badge/expiry-and-revocation.md).

## Capture prevention

This document is being written while the rubric has no adoption and therefore no one is trying to influence it. The moment it has adoption, vendors will. The provisions below are enforced now, before they are politically expensive to enforce.

- **Criteria changes require multiple reviewers.** [`.github/CODEOWNERS`](.github/CODEOWNERS) enforces that changes under `rubric/criteria/` require review from the criteria owners, not from any single maintainer.
- **Conflicts of interest are disclosed in writing** on every assessment and every rubric-change PR that involves a party with a commercial relationship to the change.
- **No maintainer may vote on a revocation of their own badge.** If all sitting maintainers are conflicted, revocation decisions are delegated to an external assessor named in the register at the time of appointment.
- **The register is public and non-destructive.** Revocations are visible in [`badge/register.md`](badge/register.md) and are not silently amended. If a revocation is later overturned, the correction is a new entry, not a deletion.

## Roles

- **Maintainer.** Has commit rights on this repository. Reviews proposals, closes issues, cuts releases. Listed in [`.github/CODEOWNERS`](.github/CODEOWNERS).
- **Assessor.** Conducts assessments using the rubric. An assessor is not automatically a maintainer.
- **Badge holder.** Anyone currently holding a Practitioner, Product, or Organization badge. Holders are listed in [`badge/register.md`](badge/register.md).

## How the rubric changes

### Proposing a new criterion

Open an issue using [`.github/ISSUE_TEMPLATE/propose-criterion.md`](.github/ISSUE_TEMPLATE/propose-criterion.md). A proposal must include:

- The statement, in the form required by [`rubric/index.md`](rubric/index.md).
- The failure it is intended to prevent, with reference to a session in [`evidence/`](evidence/) or a documented incident.
- What evidence an assessor would inspect.
- Which family it belongs to, and why.

Proposals sit open for **at least 21 days** before being merged, to allow public comment.

### Challenging an existing criterion

Open an issue using [`.github/ISSUE_TEMPLATE/challenge-criterion.md`](.github/ISSUE_TEMPLATE/challenge-criterion.md). A challenge must state which criterion is being challenged, and on what grounds — the criterion is unassessable, redundant, wrong, or has been overtaken by better practice. Maintainers respond in writing on the issue. A challenge that is upheld results in a change to the criterion or its removal; the outcome is recorded in the changelog either way.

### Reporting an unassessable criterion

If, during an assessment, a criterion cannot be assessed as written — the evidence it requires cannot be produced or inspected in principle, not merely by this team — open an issue using [`.github/ISSUE_TEMPLATE/report-unassessable.md`](.github/ISSUE_TEMPLATE/report-unassessable.md). Unassessable criteria are a maintenance defect; they are prioritized.

### Changing thresholds

Threshold changes follow the same process as criterion changes and are documented in [`rubric/thresholds.md`](rubric/thresholds.md) and the changelog. Badges issued under a prior threshold remain valid until renewal; grandfathering across renewal is not offered.

## Versioning

The rubric is versioned as `MAJOR.MINOR`.

- **MAJOR** increments when a criterion is added, removed, or has its statement changed in a way that could alter the outcome of an assessment.
- **MINOR** increments for clarifications, typo fixes, and additions that do not change assessment outcomes (e.g. new failure modes appended to an existing criterion).

An assessment records the rubric version under which it was conducted.

## Conflicts of interest

An assessor may not assess a team, product, or organization in which they hold a financial interest, an employment relationship, or a close personal relationship. Assessors declare conflicts in writing before an engagement. Undisclosed conflicts are grounds for revoking any badges issued by that assessor and removing the assessor from the register.

## Disagreement with an assessment

A team that believes an assessment was conducted incorrectly may request a second assessment by a different assessor. Both reports are made available to the team. If the two reports disagree materially, the discrepancy is logged as an inter-assessor issue under [`assessment/inter-assessor.md`](assessment/inter-assessor.md), which feeds back into rubric refinement.

## What governance does not do

Governance does not adjudicate whether an individual team "deserves" a badge. It maintains the rubric under which that question is answered elsewhere.
