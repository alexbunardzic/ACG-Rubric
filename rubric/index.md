# The ACG Rubric

The ACG Rubric assesses the **integrity of a code-generation practice** in which one or more AI agents write, modify, or review production code. It is not a benchmark of models, an audit of code quality, or a certification of security posture.

It answers a narrower question: **when this team ships code produced with AI assistance, is it possible to say who is accountable, what was specified, what was verified, and what changed — without relying on the honour system?**

## How the rubric is structured

Six criterion families:

| Family | Question it answers |
| --- | --- |
| **SPEC** — Specification integrity | Is there a specification the agent could not silently reinterpret? |
| **VER** — Verification integrity | Is verification independent of the thing being verified? |
| **AGENT** — Agent boundaries & permissions | Is the blast radius of an agent's actions bounded and known? |
| **HUMAN** — Human accountability | Is there a named human answerable for what shipped? |
| **EVOLVE** — Evolvability | Can the artefact be safely changed six months from now by someone who was not in the room? |
| **PROV** — Provenance | Can the origin of every change be reconstructed after the fact? |

Each family contains numbered criteria (e.g. `SPEC-01`). Every criterion is one file, structured identically: statement, rationale, what evidence looks like, how it is assessed, and how it fails.

## Thresholds

Three badge levels: **Practitioner**, **Product**, **Organization**. Each has a published, non-negotiable minimum set of criteria that must pass, and a small set of criteria on which failure disqualifies regardless of overall score. See [thresholds.md](thresholds.md).

## How to read a criterion

Every criterion is a single file with frontmatter and the same section shape, no exceptions:

- **Frontmatter** — `id`, `domain`, `status` (draft / active / deprecated), `core` (whether it is in the core set required for the Practitioner badge), `since` (rubric version added), and `revised` (rubric version last changed).
- **Criterion** — the statement. What must be true. Written so a hostile reader cannot pretend to satisfy it by paraphrase.
- **Why it matters** — the rationale. Traceable to a failure in [`evidence/findings/`](../evidence/findings/) where possible.
- **How it's assessed** — what an assessor inspects.
- **Meets** — a concrete example of a repository that satisfies the criterion.
- **Does not meet** — a concrete example of a repository that fails it. This one is usually more useful than *Meets*, and the one that should be written first.
- **Scope note** — what this criterion does *not* address, to prevent it being over-claimed.
- **Mappings** — pointers to OWASP LLM Top 10, OWASP Agentic Top 10, and NIST AI RMF.

## One file per criterion

Each criterion has a permanent URL (`rubric/criteria/<DOMAIN>/<ID>.md`), its own git history, and can be referenced by ID for years without breaking. A single-file build of the whole rubric is generated from these files for readers who want the document in one piece — both are canonical, the per-file form is the source of truth.

## What this rubric is not

See [scope.md](scope.md). It is a liability boundary, not a preamble. Read it before disagreeing with the rubric.
