# Glossary

Terms are defined here once. Where a criterion uses one of these words, it means what this file says it means. Local redefinition is not permitted.

## agent

Any software process that produces or modifies code in response to a natural-language instruction, whether interactive (a coding assistant) or autonomous (a long-running job). The rubric treats humans and agents as distinct actors even when the human is operating the agent in real time.

## artefact

A durable, addressable file or record. A chat transcript in a proprietary UI is not an artefact unless it is exported to an addressable location. "Durable" means it survives the session that produced it.

## drift

The gap between what the specification says and what the code does. Drift is not a bug; drift is the *unmeasured possibility* of a bug. A team that can measure drift and chooses to accept it has not drifted. A team that cannot measure it has, by definition.

## material contribution

An agent's contribution to a change is **material** if any of the following is true:

- more than a trivial amount of the change's non-whitespace bytes originated from the agent;
- the agent chose the structure, name, or interface of anything that persists past the change;
- the change would not have been produced, or would have been substantially different, without the agent.

"Trivial" is not defined numerically on purpose. An assessor uses judgement; the team must be able to defend theirs.

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
