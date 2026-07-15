---
id: VER-02
domain: Verification Integrity
status: active
core: false
since: v0.1
---

# VER-02 — Verification is independent of the agent that produced the code

## Criterion

For every [agent-authored change](../../glossary.md#agent-authored-change), the verification of that change is both:

1. **Independent of the author's understanding.** The verifier does not inherit the originating prompt, the task description handed to the code-producing agent, or the code author's framing of what "correct" means. The verifier derives its notion of correctness from the [specification](../../glossary.md#specification), or from an out-of-band source of correctness — a pre-existing test suite, a specification-derived oracle — that was formed before this change was contemplated. A separate invocation of the same agent is **not** by itself separate understanding: a fresh context window on the same model handed the same task description reconstructs substantially the same understanding, including the same blind spots.

2. **Load-bearing.** The independent verification is able to fail the change on its own, and the workflow actually permits it to do so. A review that is present but non-gating, a human co-reviewer whose approvals are pro forma, or a check whose failures are routinely overridden without record does not satisfy this bar.

**Both bars are required.** Presence without load-bearing weight is verification theater. Independence of invocation without independence of understanding is same-model self-certification with an extra process step.

**A stronger bar — full confidence rather than pass.** Verification by a source whose model of correctness was formed separately from the author's — a human reviewer, a *different* model, or a maintained out-of-band suite not derived from this task — earns full confidence and is what the criterion is ultimately trying to buy. The middle bar above is the pass condition; this stronger bar is named so that teams and assessors can distinguish "passes VER-02" from "at low residual risk," and so that a mature practice has somewhere to aim beyond compliance. Making model diversity the floor was considered and rejected as too strict for v0.1 — it would fail most teams building today, without buying enough over the middle bar to justify the cost.

## Why it matters

An agent that both writes and verifies its own work verifies its own understanding of the task. This is not independent evidence; it is expressed confidence. The two failure modes this criterion is built to prevent:

- **Verification theater.** An independent verifier exists on paper — a co-reviewer, a second-agent check, an out-of-band suite — but the workflow does not permit it to actually reject the change. The presence is real; the load-bearing role is not. Same disease as HUMAN-01's accountability theater, and the seam a well-intentioned team slides into over time.

- **Correlated evaluators.** Two runs of the same model on the same framing are not two independent judges; they are one judge asked twice. They fail together on the exact inputs where the model's understanding is wrong — which is precisely where a verifier needs to be independent to catch something. The seam a badge-gaming team drives through: separate invocations look like independence at the process level while providing none at the evaluation level.

## How it's assessed

- Draw a sample of shipped agent-authored changes per the sampling policy in [`../../../assessment/method.md`](../../../assessment/method.md#sampling).
- **Independence-of-understanding check.** For each sampled change, trace the verification back to its source. Confirm the verifier did not inherit the originating prompt or task framing. If the verifier is another agent invocation, confirm its input was the specification or an out-of-band oracle — **not** the same prompt or task description that produced the code. Same-model, same-framing, fresh-context is *not* independent for the purposes of this criterion.
- **Load-bearing check.** For the same sampled change, inspect the verification workflow. Confirm the verifier's negative outcome would block merge by default. Inspect the verifier's outcome history over the assessment period: it must show instances of the verifier actually rejecting changes and the rejections being honored. A verifier with zero rejections over a substantial history is a signal to investigate — either the verifier is rubber-stamping, the code is perfect (unlikely at scale), or the verifier's failures are being overridden invisibly.
- **Override audit.** If the workflow permits overriding the verifier, inspect the override log. Overrides must be attributable to a named human and recorded with a reason — silent overrides fail the load-bearing bar because the verifier's failures are not effectively binding.
- **Aggregation.** Policy-and-configuration criterion — assessed primarily on the team's verification workflow and configuration, spot-checked against sampled changes. A sample failure escalates to a review of the policy and configuration rather than a per-change fail. Persistent same-model-same-framing patterns, verifier-with-no-rejections patterns, or silent-override patterns across the sample fail the criterion.

## Meets

A repository where the merge gate requires two independent verification signals for every agent-authored change:

- an out-of-band test suite maintained by the team over years, not derived from any specific change, whose failure blocks merge without exception;
- a human review by someone other than the operator of the code-producing agent, whose review-thread history over the assessment period shows a distribution of outcomes — including regular rejections and requests for revision, not only approvals.

Neither signal can be overridden without a named human on record and a reason logged, and the override log is inspectable. Where a second agent is used as a verifier, it is a *different model* from the author's, and the input handed to it is the specification — not the originating prompt. This configuration passes the middle bar and reaches for the full-confidence bar.

## Does not meet

Three failure patterns, each graded by which bar it fails:

1. **Verification theater — fails the load-bearing bar.** An independent human co-reviewer is required on every merge. Inspection of the review-thread history shows the reviewer has approved 300 agent-authored changes in the last month and rejected zero, with every approval timestamped within seconds of the PR opening. The reviewer is present; the review is not load-bearing. Same shape as HUMAN-01's rubber-stamp Does not meet — the criterion requires the verifier be *able to fail the change*, not merely be listed.

2. **Correlated evaluator — fails the independence-of-understanding bar.** Verification is performed by "a separate agent invocation." Inspection reveals the second invocation is the same model, handed the same task description that produced the code, with a fresh context window. The verifier and the author are one judge asked twice. The workflow ticks the "verified" box; the criterion fails on the independence-of-understanding bar. Note: this is *not* a rubber-stamp case — the second invocation may do real, load-bearing verification work; it fails because its work is not independent in the way that matters.

3. **Substrate fail — no attribution.** The team's [PROV-01](../PROV/PROV-01.md) practice is missing: there is no reliable record of which changes were agent-authored, or of which agent invocations authored them. The assessor cannot determine whether the verifier and the author are the same agent because the authorship of both is inferred, not recorded. VER-02 is unassessable in principle and fails on the substrate ground; the independence-of-understanding and load-bearing bars are not reached.

## Scope note

**Temporal scope of "not authored for this change."** An out-of-band verification suite that pre-existed the change being verified counts as independent even if the suite was itself agent-authored — provided the suite's construction was not oriented toward the specific change under verification. An agent-built suite from last week verifying this week's agent-built code is borderline: different invocation, plausibly "not for this change," but potentially the same understanding. The independence-of-understanding bar resolves the borderline. If the same model built both suite and code from adjacent task framings, they are likely correlated and fail; if the suite was built to the specification and the code was built to a task description derived from the same specification, they can be independent. In the target population most test suites are themselves agent-built and this case is common, not exotic — the assessor evaluates the suite's independence of understanding, not the origin of its bytes.

**Substantive adequacy of the review** is out of scope for VER-02 — the criterion asks whether the verification is independent and load-bearing, not whether the review itself was thoughtful. That is analogous to the [HUMAN-01](../HUMAN/HUMAN-01.md)/[HUMAN-02](../HUMAN/HUMAN-02.md) split.

**Substrate dependency on PROV-01.** VER-02 depends on [PROV-01](../PROV/PROV-01.md) directionally: if authorship cannot be attributed under PROV-01, VER-02 cannot determine whether the verifier and the author are the same agent, and fails on the substrate ground before either the independence or the load-bearing bar is reached. Without attribution, "independent of the agent that produced the code" is literally unassessable — the criterion cannot check independence from an author it cannot identify.

## Mappings

- **OWASP LLM Top 10: none.** The specific failure of same-model self-certification with a process fig leaf is not named. See [`../../../mappings/unmapped.md`](../../../mappings/unmapped.md).
- **OWASP Agentic Top 10: partial** — related to bounded agent action.
- **NIST AI RMF: partial** — MEASURE function, but at organizational rather than per-change verification independence.
