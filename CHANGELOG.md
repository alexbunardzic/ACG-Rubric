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
- HUMAN-01 — Promoted to `status: active`. Rewritten as a two-part criterion (recorded AND answerable), with an explicit answerability interview step in the assessment. Closes the accountability-theater seam where a template-populated metadata field satisfies a recorded-name check while the named person cannot answer for the change. Now cites [agent-authored change](rubric/glossary.md#agent-authored-change) consistently with SPEC-03, making the substrate dependency on PROV-01 uniform across the three core criteria that require attribution.

### Removed from core set
- PROV-01 — dropped from `core: true` to `core: false` and its Practitioner disqualifier entry removed. Reason: it is `status: draft` with placeholder Meets/Does not meet; a labelled-draft criterion cannot carry binding force on a badge decision. Restoration to core follows the governance process once an evidence session anchors the examples. The dependency SPEC-03 places on PROV-01's practice is preserved via the `agent-authored change` glossary term.

### Restructured (supersedes the PROV-01 removal above)
- **PROV-01 split.** The substrate concern is now **PROV-01 — "Agent authorship is attributable from recorded evidence"** (`status: active`, `core: true`, Practitioner disqualifier). The fuller-chain requirement — reconstructability from code back to prompt, accountable human, and specification — moves to **PROV-03 — "Full provenance chain is reconstructable"** (`status: draft`, `core: false`, pending an evidence session to anchor its Meets and Does not meet). Rationale: SPEC-03, HUMAN-01, PROV-02, and PROV-03 all depend on being able to identify which changes are agent-authored; that substrate must be owned by a binding criterion, and it is a criterion that can be written now without requiring a private incident (unlike the fuller chain, which needs an anchoring "why did this ship?" archaeology story). The split closes the loophole where a team could pass SPEC-03 and HUMAN-01 by claiming no changes were agent-authored.
- Cross-references to the old PROV-01 (substrate + full chain) redirected: SPEC-03 and HUMAN-01 now reference the new PROV-01 (substrate) as their binding dependency; the archetypal full-chain examples move with the content to PROV-03.

### Policy
- **v0.1 does not issue badges.** The rubric ships as a specification pending evidence-session anchoring of the remaining draft core criteria (SPEC-01, SPEC-02, VER-01, AGENT-01, HUMAN-02) and non-core drafts (VER-02/03, AGENT-02/03, EVOLVE-01/02/03, PROV-02, PROV-03). Badge issuance begins from a rubric version in which every criterion required for any badge level is `status: active` and every Meets/Does not meet example is grounded in evidence. Notices added to README, `rubric/thresholds.md`, and `badge/criteria.md`. The launch is the [Self-Assessment Session](evidence/sessions/001-self-assessment-detent.md), not a badge issuance.

## [0.1.0] — TBD

First tagged draft. Not yet suitable for issuing badges.
