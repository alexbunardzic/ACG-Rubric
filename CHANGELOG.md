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
- HUMAN-01 — Tightened against three residual judgment-call seams: (i) **retention window floor** — the team-declared answerability window must be at least 30 days from merge, preventing gaming via short declared windows that exclude scrutiny; (ii) **per-question conjunctive aggregation** — the three interview questions (a)/(b)/(c) are separate pass/fail with any-one-fails-the-change semantics, replacing the softer "substantive specificity" grader; (iii) **volume-scaled answerability subsampling** — for each accountable human, the interview subsample is at least ⌈√n⌉ of their accountable changes, so rubber-stamp-at-scale patterns cannot hide behind a fixed one-per-human floor. Meets, Does not meet, and How-it's-assessed updated to demonstrate the new machinery. HUMAN-01 is the reference implementation for other criteria carrying the presence-vs-substance seam.
- VER-02 — Promoted to `status: active`. Rewritten to the HUMAN-01 template plus a criterion-specific values decision on the meaning of "independent":
  - **Seam A (template transfer).** Two conjunctive bars now declared in the criterion body: **independence of understanding** and **load-bearing**. Presence without load-bearing weight fails; separate invocation without separate understanding fails. Does not meet includes a rubber-stamp verification pattern shaped like HUMAN-01's rubber-stamp accountability pattern.
  - **Seam B (new work).** Deliberately picked the **middle bar** — independence of context/framing, not mere separate invocation — as the pass condition. Named the stronger bar — model diversity — as what earns *full confidence* rather than what earns pass. This is a values call: making model diversity the floor would fail most teams building today, and the middle bar closes the same-model-same-framing loophole that the previous statement (invocation-only) missed. The trade-off is on the record; changing it is an amendment through the governance process.
  - **Temporal scope note** resolves the borderline case of agent-authored prior test suites reused across changes: assessed on independence of understanding, not origin of bytes.
  - **PROV-01 directional dependency** added to the scope note, matching SPEC-03 and HUMAN-01: without attribution, VER-02's "same agent" question is unassessable and fails on the substrate ground before the independence or load-bearing bars are reached.
  - Does not meet patterns graded by which bar each fails (load-bearing, independence-of-understanding, substrate).
  - VER-02 added to the policy-and-configuration example list in `assessment/method.md`.
- VER-02 — Three residual seams closed after promotion:
  - **Capability-vs-history split fixed.** The load-bearing bar now tests configuration capability primarily, with rejection history as corroborating evidence rather than a precondition — mirroring [SPEC-03](rubric/criteria/SPEC/SPEC-03.md)'s "clean history is a pass" clause. Zero-rejections-at-scale is no longer "a signal to investigate" with unspecified resolution; it triggers a specific two-part investigation (undocumented escape path? silent override log?) with a defined pass/fail outcome. Closes the same statement-vs-assessment mismatch VER-02 had solved for Seam B, reappearing in the load-bearing bar.
  - **Worked correlated-suite Does not meet added** (pattern 4). The temporal scope note previously resolved the agent-authored-prior-suite case in principle but left assessors with a subtle "built to spec vs. built to a task-description-derived-from-the-spec" inference and no anchor. Pattern 4 walks through a concrete correlated agent-built suite, contrasts with a passing specification-anchored suite, and gives assessors an operational test to distinguish (ask what a test file is testing — spec section or ticket phrase).
  - **"Pro forma" and "routinely" removed from criterion body.** The load-bearing bullet no longer smuggles undefined thresholds; instead it points at operational signatures ("approvals show no evidence of engagement with the diff") and requires overrides to have a recorded reason (no "routinely" hedge). Does not meet #1 remains the concrete anchor.

### Removed from core set
- PROV-01 — dropped from `core: true` to `core: false` and its Practitioner disqualifier entry removed. Reason: it is `status: draft` with placeholder Meets/Does not meet; a labelled-draft criterion cannot carry binding force on a badge decision. Restoration to core follows the governance process once an evidence session anchors the examples. The dependency SPEC-03 places on PROV-01's practice is preserved via the `agent-authored change` glossary term.

### Restructured (supersedes the PROV-01 removal above)
- **PROV-01 split.** The substrate concern is now **PROV-01 — "Agent authorship is attributable from recorded evidence"** (`status: active`, `core: true`, Practitioner disqualifier). The fuller-chain requirement — reconstructability from code back to prompt, accountable human, and specification — moves to **PROV-03 — "Full provenance chain is reconstructable"** (`status: draft`, `core: false`, pending an evidence session to anchor its Meets and Does not meet). Rationale: SPEC-03, HUMAN-01, PROV-02, and PROV-03 all depend on being able to identify which changes are agent-authored; that substrate must be owned by a binding criterion, and it is a criterion that can be written now without requiring a private incident (unlike the fuller chain, which needs an anchoring "why did this ship?" archaeology story). The split closes the loophole where a team could pass SPEC-03 and HUMAN-01 by claiming no changes were agent-authored.
- Cross-references to the old PROV-01 (substrate + full chain) redirected: SPEC-03 and HUMAN-01 now reference the new PROV-01 (substrate) as their binding dependency; the archetypal full-chain examples move with the content to PROV-03.

### Policy
- **v0.1 does not issue badges.** The rubric ships as a specification pending evidence-session anchoring of the remaining draft core criteria (SPEC-01, SPEC-02, VER-01, AGENT-01, HUMAN-02) and non-core drafts (VER-02/03, AGENT-02/03, EVOLVE-01/02/03, PROV-02, PROV-03). Badge issuance begins from a rubric version in which every criterion required for any badge level is `status: active` and every Meets/Does not meet example is grounded in evidence. Notices added to README, `rubric/thresholds.md`, and `badge/criteria.md`. The launch is the [Self-Assessment Session](evidence/sessions/001-self-assessment-detent.md), not a badge issuance.

## [0.1.0] — TBD

First tagged draft. Not yet suitable for issuing badges.
