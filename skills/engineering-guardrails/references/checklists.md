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

## Anti-Bloat Validation

Before every major decision ask:

- Is this solving the requested problem only?
- Is this introducing unnecessary files?
- Is this introducing unnecessary layers?
- Is this introducing unnecessary abstractions?
- Is this introducing unnecessary configuration?
- Is this introducing unnecessary dependencies?
- Is this introducing unnecessary optimization?
- Is this introducing unnecessary complexity?

If yes: simplify, remove, or ask for clarification.

---

## Mid-Implementation Validation

After every major change verify:

- requirements remain unchanged
- scope has not expanded
- existing patterns remain preserved
- no overengineering was introduced
- security assumptions remain valid
- complexity remains justified
- implementation remains minimal

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

## Decision Framework

Before every significant change ask:

```text
1.  Can this be solved with fewer lines?
2.  Can this be solved with fewer files?
3.  Can this be solved with existing code?
4.  Can this be solved without abstraction?
5.  Can this be solved without optimization?
6.  Can this be solved without configuration?
7.  Am I solving today's problem?
8.  Am I preserving existing patterns?
9.  Is this secure?
10. Is this production ready?
```

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

## Completion Validation

Before completion verify:

- ✓ requirements satisfied
- ✓ existing design patterns preserved
- ✓ existing engineering patterns preserved
- ✓ existing architecture preserved
- ✓ no assumptions introduced
- ✓ no unnecessary abstractions introduced
- ✓ no unnecessary optimization introduced
- ✓ no unnecessary dependencies introduced
- ✓ no unnecessary files modified
- ✓ KISS satisfied
- ✓ YAGNI satisfied
- ✓ DRY satisfied
- ✓ SOLID respected
- ✓ security reviewed
- ✓ production safety verified
- ✓ tests pass
- ✓ context usage remained efficient
- ✓ implementation remains understandable
- ✓ implementation remains maintainable
- ✓ implementation remains minimal

---

## Success Criteria

The implementation is successful when it is:

- correct
- minimal
- secure
- maintainable
- consistent
- production ready
- easy to understand
- easy to modify
- difficult to misuse
- free of unnecessary complexity

The best solution is the smallest secure solution that follows the existing codebase.

Optimization requires evidence. Abstraction requires repetition. Architecture changes require explicit approval.
