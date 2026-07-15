---
id: HUMAN-01
domain: Human Accountability
status: active
core: true
since: v0.1
---

# HUMAN-01 — A named accountable human exists for every change

## Criterion

For every shipped [agent-authored change](../../glossary.md#agent-authored-change), a **named human** — not a role, not a team, not a rotating oncall — is both:

1. **recorded as accountable** in the change's metadata, from a durable source (see [PROV-01](../PROV/PROV-01.md) for the substrate that makes such recording trustworthy); and
2. **actually answerable** — meaning that when asked, within the retention window the team declares (subject to the floor below), the named person can describe **from retention rather than by re-reading the diff**: (a) what the change was meant to do, (b) why they accepted it, and (c) what verification they relied on.

Recording without answerability is accountability theater and fails this criterion. Answerability without recording is accountability that cannot survive the answerable person's departure and also fails. **Both bars must be met.**

**Retention window floor.** The declared retention window must be at least **30 days from merge**. A shorter declared window fails on its face — a 5-day window would appear stringent while making almost every sampled change unaskable, and rubber-stamp practices would systematically escape scrutiny by declaring a window shorter than any realistic assessment cadence. The 30-day floor is universal; a team's operational needs may require a longer window but cannot go below it. Changing the floor is an amendment through the governance process.

## Why it matters

Accountability is not blame; it is the presence of an answerable party. Without a named human, "the AI did it" becomes a defence rather than a description.

The distinction between *recorded-as-accountable* and *actually-answerable* is the seam this criterion exists to close, and it is the seam a badge-gaming team drives straight through. A commit template that auto-populates an "accountable: [name]" field on every merge passes a metadata check perfectly, while the named person has no idea they are accountable, never saw the change, and cannot answer a thing about it. That is the default outcome of any team that treats accountability as a field to fill rather than a responsibility to assign. The criterion requires both bars because either alone is defeatable, and the assessment tests both because either check alone is defeatable.

## How it's assessed

- Draw a sample of shipped agent-authored changes per the sampling policy in [`../../../assessment/method.md`](../../../assessment/method.md#sampling).
- **Metadata check.** For each sampled change, confirm the recorded accountable human is a person (not a role, team, or oncall rotation), and that the record exists in durable metadata sourced from the review workflow, not auto-populated from a template or branch attribute. This is the substrate check; see [PROV-01](../PROV/PROV-01.md).
- **Answerability subsampling — volume-scaled.** For each distinct accountable human named on shipped changes in the assessment period, draw an interview subsample of at least **⌈√n⌉** changes at random, where *n* is that human's total accountable-change count in the period. Draws are restricted to changes within the team's declared retention window (satisfying the 30-day floor above). The subsample is drawn independently of the main sample. Rationale: a fixed one-per-human floor catches total theater (the person who remembers nothing) but not selective recall (the person who happens to remember the one change you asked about); scaling the interview burden to the volume that generated the rubber-stamp risk is what puts the selective-recall pattern in the assessor's path.
- **Answerability check — per-question conjunctive.** For each change in each human's subsample, contact the recorded person and ask them to describe: (a) what the change was meant to do, (b) why they accepted it, (c) what verification they relied on. **Each of (a), (b), (c) is a separate pass/fail.** The answer must be produced from retention — *not* "let me look at the diff again" — and must be verifiable against the recorded artefact for that dimension: (a) against the specification, (b) against the review rationale or ticket, (c) against the verification artefact. **Failure on any one of the three fails the change**; the three are conjunctive, not averaged. A person who answers (a) and (b) confidently but is vague on (c) fails.
- **Aggregation.** This is a binary-per-change criterion. A single failure in either the metadata check or the answerability check fails HUMAN-01 for that change, and any per-change fail fails the criterion for the assessment.

## Meets

A repository where every merge to `main` requires the reviewing human to explicitly claim accountability by name — the "accountable" field is populated by the reviewer's action, not by a template default, and the review workflow blocks merge until it is set. The team's declared retention window is 60 days (comfortably above the floor). In the volume-scaled answerability subsample, each named accountable person answers (a), (b), and (c) for each of their subsampled changes from retention — none of the *"let me look at the diff again"* responses — and each answer is verifiable against the recorded specification, review rationale, and verification artefact respectively. At least one interview surfaces a change where the accountable human recalls declining an initial version and asking for revision — *"I asked for pagination to be reworked because the first pass violated the ordering constraint in `spec/list-ordering.md`"* — evidence the review was engaged rather than pro forma.

## Does not meet

Three failure patterns, all observed:

1. **Accountability theater.** A commit template auto-populates the accountable field with the branch author or the last-committer. Metadata is perfectly present. On interview, the named person says "I don't remember that PR" for four of five sampled changes. The metadata check passes; the answerability check fails. This is the pattern this criterion exists to prevent, and it is the default outcome of any large team's first pass at compliance.

2. **Role, not a person.** The accountable field contains `sre-oncall`, `platform-team`, or `@releases`. No individual is answerable — the value is a category. Fails on the metadata check alone; no interview is needed.

3. **Rubber-stamp at scale.** The named person is real, was asked honestly, and accepted 400 agent-produced changes in the last month. Under the ⌈√n⌉ subsampling rule they are interviewed on 20 changes. They answer (a) and (b) for the first change from retention and pass those; on (c) they respond truthfully: *"if it merged I approved it, but I don't remember the specifics; I'd have to look at the diff again."* Fails on (c) — the three questions are conjunctive — and fails HUMAN-01 for the assessment on that single change, without needing to reach the other 19 interviews. The volume-scaled subsampling is what put this pattern in the assessor's path: a fixed one-per-human sample would have had a 1-in-400 chance of drawing this change on the first try, and could have passed the reviewer purely by which change the assessor happened to sample.

## Scope note

This criterion tests that a named human can answer for the change. It does not test whether the answer would satisfy a specific regulator, SLA, or downstream user; it also does not test whether the accountable human's review was substantively adequate — that is [HUMAN-02](HUMAN-02.md).

The trustworthiness of the metadata that records accountability — how a named human's acceptance is established as reliable evidence rather than a template default — is the substrate concern owned by [PROV-01](../PROV/PROV-01.md). HUMAN-01 depends on PROV-01: if the metadata cannot be trusted, HUMAN-01 fails on the substrate ground before the answerability step is reached.

## Mappings

- **OWASP LLM Top 10: none.** Per-change human accountability is not addressed. See [`../../../mappings/unmapped.md`](../../../mappings/unmapped.md).
- **OWASP Agentic Top 10: none.** Not addressed.
- **NIST AI RMF: partial** — GOVERN function, accountability structures, but at organizational rather than per-change granularity, and without the answerability-vs-recording distinction.
