# Assessment Method

*(Structured stub — expand before conducting real assessments.)*

## Overview

An assessment is conducted by a single assessor against a single subject (individual, product, or organization). The assessor produces a report using [`report-template.md`](report-template.md), backed by observations recorded live in [`worksheet.md`](worksheet.md).

## Phases

1. **Engagement setup.** Assessor confirms scope, declares conflicts of interest (see [`../GOVERNANCE.md`](../GOVERNANCE.md)), and records the rubric version under which the assessment will be conducted.
2. **Practice interview.** Assessor is briefed on the team's practice. This is context, not evidence.
3. **Sampling.** Assessor selects, at random from qualifying changes, the sample to be inspected. The team does not choose the sample.
4. **Evidence inspection.** For each sampled change, the assessor requests the evidence required by each applicable criterion.
5. **Scoring.** Each criterion is marked pass, partial, or fail based on evidence, not testimony.
6. **Report.** Assessor produces the report and issues (or does not issue) the badge.

## Sampling

Assessment is evidence-based per change. For any criterion whose assessment is per-change (rather than per-policy), the assessor draws a **sample** of shipped changes from the assessment period and evaluates the criterion on each.

### Sample size by badge level

- **Practitioner** — 5 [agent-authored changes](../rubric/glossary.md#agent-authored-change) from the last 90 days.
- **Product** — 15 changes, or 10% of qualifying changes in the assessment period, whichever is greater. Minimum 15.
- **Organization** — Product-level sampling repeated per assessed product, plus 5 cross-cutting changes selected to test consistency of the practice across products.

### Selection

Selection is random from the set of agent-authored changes in the assessment period. **The assessor performs the selection; the team does not.**

If the team disputes a specific change's inclusion in the sample (typically because they do not consider the agent's contribution material under their [declared policy](../rubric/glossary.md#material-contribution)), the dispute is recorded and the change is either replaced or retained based on the team's own policy — not on the assessor's independent judgement.

### Treatment of changes the team cannot locate

A change the team cannot produce evidence for is a **fail** on any criterion that required the evidence. It is not a re-roll of the sample.

### Aggregation

Criteria fall into two categories for sample aggregation:

- **Binary-per-change** (e.g. [PROV-01](../rubric/criteria/PROV/PROV-01.md), [PROV-03](../rubric/criteria/PROV/PROV-03.md), [HUMAN-01](../rubric/criteria/HUMAN/HUMAN-01.md)) — any single failure in the sample fails the criterion. There is no percentage-passing threshold; the sample is not averaged.
- **Policy-and-configuration** (e.g. [AGENT-02](../rubric/criteria/AGENT/AGENT-02.md), [VER-03](../rubric/criteria/VER/VER-03.md), [SPEC-03](../rubric/criteria/SPEC/SPEC-03.md)) — the criterion is assessed on the team's declared policy and merge-gate configuration. The sample is a **spot-check** that the policy is applied; sample failures on these criteria escalate to a review of the policy and configuration rather than a straight fail.

Each criterion's `How it's assessed` section states which category it falls into.

## Handling ambiguity

If a criterion cannot be assessed as written for principled reasons, the assessor files a report using [`../.github/ISSUE_TEMPLATE/report-unassessable.md`](../.github/ISSUE_TEMPLATE/report-unassessable.md). The criterion is scored based on the best available evidence and flagged; it does not silently pass.

## Duration

*(To be drafted.)*
