# Glossary

Terms are defined here once. Where a criterion uses one of these words, it means what this file says it means. Local redefinition is not permitted.

## agent

Any software process that produces or modifies code in response to a natural-language instruction, whether interactive (a coding assistant) or autonomous (a long-running job). The rubric treats humans and agents as distinct actors even when the human is operating the agent in real time.

## artefact

A durable, addressable file or record. A chat transcript in a proprietary UI is not an artefact unless it is exported to an addressable location. "Durable" means it survives the session that produced it.

## drift

The gap between what the specification says and what the code does. Drift is not a bug; drift is the *unmeasured possibility* of a bug. A team that can measure drift and chooses to accept it has not drifted. A team that cannot measure it has, by definition.

## material change

A change to the [practice](#practice) is **material** if it alters any of the elements recorded in the description of the practice at the time of the last assessment. Concretely, at minimum:

- the primary AI coding tool or agent framework in use;
- the identity of the [accountable human](#accountable-human) for a scope of work;
- the verification chain — test infrastructure, review workflow, or merge gates (see [VER-01](criteria/VER/VER-01.md), [VER-03](criteria/VER/VER-03.md));
- the specification workflow — where specifications live, how they are versioned, how they are protected (see [SPEC-01](criteria/SPEC/SPEC-01.md), [SPEC-02](criteria/SPEC/SPEC-02.md), [SPEC-03](criteria/SPEC/SPEC-03.md));
- the enumeration of agent permissions (see [AGENT-02](criteria/AGENT/AGENT-02.md));
- the review or accountability workflow (see [HUMAN-01](criteria/HUMAN/HUMAN-01.md), [HUMAN-02](criteria/HUMAN/HUMAN-02.md)).

A change to the codebase itself is not a material change to the practice unless it also alters one of the above.

**Who decides.** The team is expected to declare material changes at the time they occur, not at renewal. If the team and an assessor disagree about whether a change was material, the disagreement is settled against the recorded description of the practice at the time of the last assessment: a change that touches any element of that description is material; a change that does not, is not.

**Consequences.** A material change to the practice triggers renewal of any Product badge attached to that practice (see [`../badge/expiry-and-revocation.md`](../badge/expiry-and-revocation.md)). Failure to declare a material change is grounds for revocation, not merely lapse.

## material contribution

An agent's contribution to a change is **material** if any of the following is true:

- more than a trivial amount of the change's non-whitespace bytes originated from the agent;
- the agent chose the structure, name, or interface of anything that persists past the change;
- the change would not have been produced, or would have been substantially different, without the agent.

"Trivial" is not defined numerically on purpose. An assessor uses judgement; the team must be able to defend theirs.

Note that "material change" (above) and "material contribution" (here) are distinct terms. A material contribution is about an agent's role in a single change; a material change is about the practice as a whole. Do not conflate them.

## provenance

The reconstructable chain from a shipped line of code back to (a) the prompt or instruction that produced it, (b) the model and version that produced it, (c) the human who accepted it, and (d) the specification it was meant to satisfy. If any link in that chain cannot be produced on demand, provenance is broken.

## specification

A durable artefact stating what the code is supposed to do, in a form the agent can consume without paraphrase. A ticket title is not a specification. A conversation is not a specification. A specification is written down, versioned, and referenced by the change that satisfies it.

## specification surface

The complete set of specifications that apply to a given change. A change may satisfy its immediate specification while violating a broader one (e.g. an architectural constraint). An assessor evaluates the full surface, not only the nearest ticket.

## verification

An independent check that the code satisfies its specification. Independent means: not written by the same agent invocation that produced the code, not derived from the same prompt, and not evaluated only by the agent that wrote the code. A test the agent wrote and the agent ran, unreviewed, is not verification. It is a suggestion.

## accountable human

A named person — not a role, not a team, not a rotating oncall — who can be asked, six months later, "why did this ship?" and is expected to answer. Accountability is not blame; it is the presence of an answerable party.

## practice

The repeatable set of behaviours by which a team produces code with AI assistance. The rubric assesses the practice, not the individual outputs. A team without a practice — where behaviour depends on who is at the keyboard — fails on that ground alone.
