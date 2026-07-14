# ACG Rubric

A rubric for assessing the **integrity of a code-generation practice** in which AI agents materially contribute to production code.

It does not assess the model, the code, or the security posture. It asks whether the team can answer four questions on demand for any change that shipped: **what was specified, what was verified, who is accountable, and what changed.**

---

## For a CTO — what this is and why you should care

Your engineers are shipping code produced with AI assistance. When something breaks in production, you need to answer: *what was the AI told to build, who accepted its output, and how do we know it does what it was supposed to do?* If the honest answer is "let me check the chat history if it hasn't expired" — you have a practice problem, not a model problem.

The ACG Rubric assesses the practice, produces a badge if it passes, and takes the badge away if it stops passing. See **[services →](https://aicraftspeopleguild.github.io/acg-services.html)** for engagement details.

## For a practitioner — is this any good?

Read the criteria and decide. Every criterion is one file, one URL, one Git history:

- [Rubric front page](rubric/index.md) — how the six domains fit together.
- [The criteria](rubric/criteria/) — 16 checkable items across SPEC, VER, AGENT, HUMAN, EVOLVE, PROV.
- **[What the ACG Rubric says that nobody else does](mappings/unmapped.md)** — the criteria with no counterpart in OWASP LLM, OWASP Agentic, or NIST AI RMF. This is the argument for the rubric's existence.

If a criterion is wrong, [challenge it](.github/ISSUE_TEMPLATE/challenge-criterion.md). If a criterion is unassessable, [report it](.github/ISSUE_TEMPLATE/report-unassessable.md). Both are first-class issue types.

## For a skeptic — are these people serious, or is this marketing?

The authors of this rubric assessed their own codebase against it, publicly, unedited, and published where they failed:

**→ [Session 001 — Self-Assessment of ACG (to be added)](evidence/sessions/001-self-assessment-detent.md)**

A standard whose authors are exempt from it is a marketing asset. This one is not. The rules in [`badge/expiry-and-revocation.md`](badge/expiry-and-revocation.md) apply to the founders on the same terms as any other holder — see the first section of that file.

---

## The rest of the repository

- [`rubric/`](rubric/) — the rubric proper. One file per criterion; each is citable by URL and has its own git history.
- [`assessment/`](assessment/) — the method, worksheet, and report template that produce a badge.
- [`mappings/`](mappings/) — how the ACG Rubric relates to OWASP and NIST, and where it doesn't.
- [`evidence/`](evidence/) — the empirical basis of the rubric. Where every criterion came from.
- [`badge/`](badge/) — what earns a badge, what expires it, what revokes it, who currently holds one.
- [`GOVERNANCE.md`](GOVERNANCE.md) — how the rubric changes, and how capture is prevented.
- [`CONTRIBUTING.md`](CONTRIBUTING.md) — how to propose, challenge, or refute.

## Single-file build

The rubric is stored as one file per criterion (see the note in [`rubric/index.md`](rubric/index.md)). A single-file build for offline reading and audit-friendly circulation will be generated from the criteria directory; when available, it will be linked here. Both remain canonical; the per-file form is the source of truth.

## License

Rubric content is licensed under **[CC BY 4.0](LICENSE)**. Attribution is required; derivatives are welcome, including by parties who never speak to us. If a competitor assesses against this rubric, we have won — they are operating inside a frame we defined.

Any tooling (a linter, a mechanical checker) is shipped in a separate repository under a code license, not here.
