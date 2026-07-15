# Thresholds

Thresholds are published so that they cannot be negotiated during an assessment. If a threshold is wrong, it is changed by amending this document, in public, through the process in [`../GOVERNANCE.md`](../GOVERNANCE.md) — not by an assessor's discretion in the room.

## The three badges

| Badge | Attaches to | Renews |
| --- | --- | --- |
| **Practitioner** | A named individual | Every 12 months |
| **Product** | A named product or codebase | Every 12 months, or on any [material change](glossary.md#material-change) to the practice |
| **Organization** | A legal entity | Every 24 months, with an interim attestation at 12 |

## The core set

Every criterion carries a `core: true` or `core: false` flag in its frontmatter. **The core set is the union of all `core: true` criteria.** This is what makes the Practitioner threshold mechanically computable rather than a matter of interpretation: no reading is required; the flag either is or is not set.

Current core set (all `core: true`):

- `SPEC-01`, `SPEC-02`, `SPEC-03`
- `VER-01`
- `AGENT-01`
- `HUMAN-01`, `HUMAN-02`

**PROV-01 is intentionally not in the core set in v0.1.** It is the criterion the core set most obviously needs, but it is `status: draft` — its Meets and Does not meet examples are pending an incident-derived anchor (see the criterion file for the reasoning). A labelled-draft criterion cannot carry binding force on a badge decision without undercutting the credibility of every other criterion in the set. PROV-01's promotion to `core: true` follows the process in [`../GOVERNANCE.md`](../GOVERNANCE.md) and is expected in a future version.

The dependency is not lost: [SPEC-03](criteria/SPEC/SPEC-03.md) references the [agent-authored change](glossary.md#agent-authored-change) definition, which in turn describes PROV-01's practice. A team pursuing a Practitioner badge under v0.1 will already need PROV-01's mechanism in order to pass SPEC-03; PROV-01 is not binding on its own until anchored.

Changes to the core set — flipping a criterion's `core` flag — are amendments to the rubric and follow the process in `GOVERNANCE.md`. The core set is not adjusted per engagement.

## Passing the rubric

Each criterion is scored **pass**, **partial**, or **fail**. There is no numeric aggregate. A badge is awarded when both hold:

1. The **required set** for that badge is all `pass` (no partials, no fails).
2. No criterion in the **disqualifying set** is `fail`.

A `partial` on a required criterion is a fail for badge purposes. It is recorded as `partial` in the report so the team knows what is close.

## Practitioner

**Required set** — the core set. All `core: true` criteria must pass.

**Disqualifying set** — any `fail` disqualifies:

- `HUMAN-01` (a named accountable human exists)
- `SPEC-03` (specification surface is protected against agent modification)

`PROV-01` will join this list on promotion to `core: true`; see the core-set note above.

## Product

**Required set** — the core set, plus:

- `VER-02`, `VER-03`
- `AGENT-02`, `AGENT-03`
- `EVOLVE-01`, `EVOLVE-02`
- `PROV-02`

**Disqualifying set** — Practitioner disqualifiers, plus:

- `AGENT-02` (agent permissions are bounded and enumerable)
- `VER-02` (verification is independent of the agent that produced the code)

## Organization

**Required set** — every criterion with `status: active` must pass. Criteria with `status: draft` are excluded from the required set by design: a draft criterion is one the maintainers have told the world is not finished, and it must not have binding force on a badge until it is promoted to `active` through the governance process. Adding a criterion in `draft` status therefore does not silently change what any Organization badge requires.

**Disqualifying set** — all Product disqualifiers, plus:

- `EVOLVE-03` (the practice survives the departure of any single person)
- Any criterion that fails at the Product level in more than one assessed product within the organization.

## What thresholds do not do

Thresholds do not grade. There is no bronze, silver, gold. A team either holds a badge or does not. The [`../assessment/report-template.md`](../assessment/report-template.md) deliverable records every criterion's score so the team knows exactly where it stands, but the outside world sees only the badge, and only its current state.

## Changing thresholds

Threshold changes follow the process in [`../GOVERNANCE.md`](../GOVERNANCE.md) and are versioned in [`../CHANGELOG.md`](../CHANGELOG.md). A badge issued under a prior threshold remains valid until its next renewal; at renewal, the current threshold applies. Grandfathering across renewal is not offered.
