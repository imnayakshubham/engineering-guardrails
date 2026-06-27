# engineering-guardrails — Detailed Checklists

Load and apply these before major decisions, during implementation, before security review, and before completion.

---

## Security Validation

Every implementation must be evaluated for:

**Input Security** — validation, sanitization, type safety, boundary checking.

**Authentication** — authentication enforcement, authorization enforcement, permission boundaries.

**Data Security** — secrets handling, token handling, credential exposure, sensitive logging.

**Application Security** — SQL injection, XSS, CSRF, SSRF, path traversal, command injection, unsafe deserialization, dependency vulnerabilities.

**Operational Security** — stack trace leakage, error leakage, environment handling, production configuration safety.

If security assumptions exist: stop, document assumptions, request clarification.

---

## Changes Requiring Explicit Approval

Do not perform these without explicit approval:

- architectural changes
- dependency additions
- framework migrations
- database schema changes
- API contract changes
- authentication / authorization changes
- infrastructure changes
- build-system changes
- large refactors
- cross-package reorganizations

---

## Before You Change Code

Ask before every significant change — if it adds anything unnecessary, simplify, remove, or ask for clarification:

- Can this be solved with fewer lines, fewer files, or existing code?
- Can this be solved without new abstraction, optimization, or configuration?
- Am I solving today's problem only — not a speculative future one?
- Am I preserving existing patterns and the smallest safe blast radius?
- Does this add unnecessary files, layers, abstractions, dependencies, or complexity?
- Is it secure? Is it production-ready?

---

## Token / Context Efficiency Rules

Context is working memory, not storage.

**Must:** read only necessary files; read only necessary symbols; summarize findings; reuse summaries; keep context focused; compress previous conclusions; avoid repeated explanations and analysis.

**Must Not:** scan entire repositories; read unrelated files; repeat previous context; generate unnecessary plans, alternatives, or verbose explanations; perform exhaustive searches.

### Context Budget

Allocate context approximately:

- 20% requirements
- 30% pattern discovery
- 30% implementation
- 20% validation

When context grows: compress findings, summarize decisions, remove irrelevant context, preserve only critical facts.

---

## Failure Conditions

Stop immediately if:

- requirements are ambiguous
- multiple interpretations exist
- assumptions become necessary
- architecture is unclear
- patterns conflict
- security assumptions appear
- scope expands unexpectedly
- optimization changes requirements

Ask questions. Wait.

---

## Completion Checklist

Verify before declaring the change done.

### Correctness & quality

- requirements satisfied; behavior is correct, including edge cases
- readable, maintainable, and testable; tests pass
- error handling and API design are consistent with the codebase
- dependency hygiene respected; production-ready

### Minimalism & consistency

- scope unchanged; no overengineering introduced
- existing patterns and architecture preserved
- KISS / YAGNI / DRY satisfied; SOLID respected
- no unnecessary files, abstractions, dependencies, or complexity
- smallest safe blast radius; any added complexity is justified

### Security

- security reviewed; no known vulnerability introduced or propagated

**Done means:** correct, minimal, secure, maintainable, consistent, production-ready, easy to understand, easy to modify, easy to test, and hard to misuse.
