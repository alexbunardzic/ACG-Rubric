# Changelog

All notable changes to the ACG Rubric are recorded here. See [`GOVERNANCE.md`](GOVERNANCE.md) for how changes are made.

Versioning follows the scheme in `GOVERNANCE.md`:

- **MAJOR** — a criterion is added, removed, or has its statement changed in a way that could alter the outcome of an assessment.
- **MINOR** — clarifications, typo fixes, and additions that do not change assessment outcomes.

## [Unreleased]

### Added
- Initial rubric structure: six criterion families (SPEC, VER, AGENT, HUMAN, EVOLVE, PROV).
- Three badge levels: Practitioner, Product, Organization.
- Assessment method, worksheet, and report template (stub).
- Mappings to OWASP LLM Top 10, OWASP Agentic Top 10, NIST AI RMF (stub).
- Glossary term `agent-authored change` — captures the requirement that agent attribution be grounded in recorded evidence, referenced by SPEC-03 and PROV-01.
- Sampling policy in `assessment/method.md`: per-badge-level sample sizes, selection procedure, and binary-vs-policy aggregation rules.

### Changed
- Glossary `material contribution` — added the discipline that teams must publish a written policy declaring which agent contributions they treat as material; assessors evaluate against the declared policy rather than making per-change judgement calls.
- SPEC-03 — Criterion trigger now cites [agent-authored change](rubric/glossary.md#agent-authored-change) rather than "materially contributes" inline, closing the attribution seam with PROV-01.
- PROV-01 — Sharpened to require reconstruction from recorded evidence, within a team-declared time bar (defaulting to one business day), and without the presence of any specific person. References the new sampling policy for aggregation.

### Removed from core set
- PROV-01 — dropped from `core: true` to `core: false` and its Practitioner disqualifier entry removed. Reason: it is `status: draft` with placeholder Meets/Does not meet; a labelled-draft criterion cannot carry binding force on a badge decision. Restoration to core follows the governance process once an evidence session anchors the examples. The dependency SPEC-03 places on PROV-01's practice is preserved via the `agent-authored change` glossary term.

## [0.1.0] — TBD

First tagged draft. Not yet suitable for issuing badges.
