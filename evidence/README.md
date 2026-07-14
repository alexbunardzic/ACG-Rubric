# Evidence

The empirical basis of the rubric lives here. Every criterion traces to something that actually happened; those things are recorded in this directory. This is the answer to the question every serious reader will ask — *where did these criteria come from?* — and the answer is a commit log.

Two subdirectories:

- **`findings/`** — sanitized failures that produced criteria. When a criterion exists because something broke, the break lives here in a form that does not identify the party involved.
- **`sessions/`** — records of assessment sessions, chronologically numbered (`001-...`, `002-...`). Each session has a codebase, a set of assessors, verdicts by criterion, disagreements and how they resolved, and a rubric diff that resulted.

## The four session types

Sessions come in four kinds. Each has a distinct role in producing and defending the rubric.

### Scar Session — private

Practitioners with real agentic mileage in a room together. One question: *what have you personally watched an agent do that a human wouldn't have?* Not what they think good practice is — what they have seen fail. Each war story is interrogated until it yields a generalizable, checkable criterion.

Scar Sessions are **private**. War stories involve real clients and real employers, and honest ones do not get told on camera. The output is published — the sanitized criterion and the finding it traces to — the session itself is not.

The Scar Session produces v0.1 of the rubric.

### Self-Assessment Session — public

The ACG team assesses its own codebases against its own rubric, live, unedited, and publishes the failures. This is the load-bearing act in the strategy: a standard whose authors are exempt from it is a marketing asset, whereas a standard whose authors visibly fail it and then fix it is a standard.

The Self-Assessment is also the fastest way to find out which criteria are unassessable — try to apply them to code you know intimately and discover you can't.

Session 001 ([`sessions/001-self-assessment-detent.md`](sessions/001-self-assessment-detent.md)) is a Self-Assessment. It is the launch.

### Assessment Session — public

A real codebase, on screen, with the rubric on screen. A working mob of five or six practitioners renders a verdict on each criterion. Observers — including counsel — interrogate ambiguous wording. **Disagreement is kept in the recording.**

Every Assessment Session generates rubric revisions. The recording, the verdict, and the diff are published together as a triad. This is what "inter-assessor reliability" looks like in practice — measured in public, not asserted in a governance document.

### Build Session — public

Genuine agentic development in the open. The session's product isn't the feature being built; it is the discovery that a criterion doesn't catch something the agent just did. When the agent does something wrong, stop and ask: *does the rubric catch this?* If no, the session's output is a proposed criterion or amendment, filed as a PR.

## The ritual per public session

Every public session produces three artefacts, published together:

1. **The recording** — full, unedited, on YouTube, linked from the session file.
2. **The verdict** — the structured session record (this directory), with per-criterion scores and resolved disagreements.
3. **The diff** — the rubric change that resulted, as a GitHub PR with rationale in the description.

Unedited is non-negotiable. Edited footage is a demo. Unedited footage is evidence that named people with reputations at stake let themselves be watched being uncertain, being wrong, and changing their minds.

## Session file schema

Each `sessions/NNN-slug.md` records:

- **Codebase** — what was assessed. Public repos by URL; private repos by sanitized description.
- **Assessors** — mob, observers, roles.
- **Rubric version** at time of assessment.
- **Verdicts by criterion** — pass / partial / fail, one row per criterion.
- **Disagreements** — where the mob did not converge, and how it resolved.
- **Rubric diff** — the PR that resulted from the session (link).
- **Recording** — link, plus timestamped index of the interesting moments.

## Findings — the sanitization gate

Every entry in `findings/` describes a pattern, not an incident. A finding must be sanitizable enough to publish. A finding that cannot be sanitized enough to publish is summarized in the criterion proposal without being merged here.

Sanitization checklist:

- [ ] No organization names, product names, or team names.
- [ ] No personal names, handles, or identifying quotations.
- [ ] No code excerpts that would identify the source project.
- [ ] Dates generalized to month/year at coarsest useful resolution.
- [ ] Failure pattern stated in terms of the rubric, not the specifics.

Findings are reviewed by `evidence-reviewers` per [`../.github/CODEOWNERS`](../.github/CODEOWNERS) before merge.
