# Mapping — OWASP LLM Top 10

**Source framework version:** _(fill in — e.g. 2025)_
**Read this first:** [`README.md`](README.md)

## Correspondence table

| OWASP LLM item | ACG Rubric criteria | Kind of correspondence | Notes |
| --- | --- | --- | --- |
| LLM01 Prompt Injection | | | |
| LLM02 Sensitive Information Disclosure | | | |
| LLM03 Supply Chain | AGENT-01, PROV-02 | Partial | ACG addresses provenance of the agent itself; OWASP addresses supply chain of models and data. |
| LLM04 Data and Model Poisoning | | | |
| LLM05 Improper Output Handling | | | |
| LLM06 Excessive Agency | AGENT-02, AGENT-03 | Partial | Close alignment on bounding agent action. |
| LLM07 System Prompt Leakage | | | |
| LLM08 Vector and Embedding Weaknesses | | | Out of ACG scope. |
| LLM09 Misinformation | | | |
| LLM10 Unbounded Consumption | | | |

_(Table to be completed against the current OWASP LLM Top 10 revision.)_

## ACG criteria not represented in OWASP LLM Top 10

Catalogued in [`unmapped.md`](unmapped.md). At minimum: HUMAN-01, HUMAN-02, EVOLVE-01, EVOLVE-02, EVOLVE-03, SPEC-01, SPEC-02, SPEC-03, PROV-01.

The ACG Rubric's focus on **the practice** — specification, human accountability, evolvability — is largely outside OWASP LLM's scope, which is application-level risk.
