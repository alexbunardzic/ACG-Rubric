---
id: PROV-02
domain: Provenance
status: draft
core: false
since: v0.1
---

# PROV-02 — Provenance includes model and version

## Criterion

The provenance record for a change identifies not only the agent that produced it, but the specific model and version. "Claude" is not sufficient. "claude-opus-4-7 on 2026-03-14" is.

## Why it matters

Model behaviour changes across versions. A team that cannot say which model produced a change cannot investigate a regression that came in with a model update, cannot reproduce a session, and cannot detect a silent tool substitution.

## How it's assessed

- For a sampled change, confirm the provenance record names the model and version.
- Confirm the record was produced at the time of the change, not backfilled.

## Meets

_TBD._

## Does not meet

_TBD._

## Scope note

This criterion presumes a provenance record exists per change; the criterion that establishes the record's existence and reliability is [PROV-01](PROV-01.md). A team that fails PROV-01 cannot pass PROV-02 — there is no record to inspect for model and version.

## Mappings

- OWASP LLM Top 10: partial — LLM03 Supply Chain.
- OWASP Agentic Top 10: partial.
- NIST AI RMF: partial.
