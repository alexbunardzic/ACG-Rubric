# What earns each badge

Operational companion to [`../rubric/thresholds.md`](../rubric/thresholds.md). If the two disagree, `thresholds.md` is authoritative.

## v0.1 — No badges issue

**No badges issue against v0.1.** The rubric is a specification, not a certification, in this version. See [`../rubric/thresholds.md`](../rubric/thresholds.md#v01--no-badges-issue) for the reasoning. The tables below describe what would earn a badge under a mature rubric version; they do not describe an assessment that can be performed for issuance today.

## Practitioner

Attaches to a **named individual**. Term: 12 months.

**Required** — the core set (all `core: true`):

- SPEC-01, SPEC-02, SPEC-03
- VER-01
- AGENT-01
- HUMAN-01, HUMAN-02
- PROV-01 (attribution substrate)

**Disqualifiers** (any fail disqualifies):

- HUMAN-01, SPEC-03, PROV-01

## Product

Attaches to a **named product or codebase**. Term: 12 months, or immediately on [material change](../rubric/glossary.md#material-change) to the practice.

**Required**: the core set, plus VER-02, VER-03, AGENT-02, AGENT-03, EVOLVE-01, EVOLVE-02, PROV-02, PROV-03.

**Disqualifiers**: Practitioner disqualifiers, plus AGENT-02 and VER-02.

## Organization

Attaches to a **legal entity**. Term: 24 months, with interim attestation at 12.

**Required**: every criterion with `status: active` must pass. Draft criteria are excluded — see [`../rubric/thresholds.md`](../rubric/thresholds.md).

**Disqualifiers**: Product disqualifiers, plus EVOLVE-03, plus any criterion that fails at Product level in more than one assessed product within the organization.

## See also

- [`expiry-and-revocation.md`](expiry-and-revocation.md) — how badges are lost, and the clause that says the same rules apply to the authors.
- [`register.md`](register.md) — who currently holds a badge, and who has lost one.
