---
name: engineering-guardrails
description: >-
  Engineering guardrails for changing existing or production codebases — preserve
  existing patterns and architecture, prefer the smallest safe blast radius, avoid
  assumptions, validate security, and prevent overengineering. Use when modifying,
  refactoring, debugging, reviewing, or extending existing systems, especially when
  architectural, abstraction, optimization, or security decisions are involved.
---

# engineering-guardrails

## Purpose

**The objective is not to write theoretically perfect code; the objective is to produce the smallest correct, secure, maintainable solution that preserves the existing codebase's deliberate engineering decisions.**

This skill enforces engineering discipline, pattern preservation, minimalism, security, and context efficiency throughout the entire software development lifecycle, and applies continuously:

- Before implementation
- During implementation
- Before every major decision
- During reviews
- Before testing
- Before completion
- Before submission

## When NOT to use

Skip this skill for throwaway work where discipline isn't the point:

- prototypes, spikes, proof-of-concepts
- experiments and exploratory scripts
- coding-interview / tutorial / toy-project code

---

## Core Philosophy

Existing code is the primary source of truth. Preserve established patterns that are correct, secure, maintainable, and actively used; identify and avoid perpetuating legacy patterns, anti-patterns, and isolated implementation mistakes.

When goals conflict, resolve in this order:

1. Correctness
2. Security
3. Existing-codebase consistency
4. Simplicity
5. Maintainability
6. Optimization

---

## Fundamental Rules

### Rule 1 — Never assume

If information is missing:

- stop
- ask concise questions
- wait for clarification

### Rule 2 — Follow existing patterns

Do not introduce:

- new architecture
- new conventions
- new abstractions
- new frameworks
- new organizational patterns

unless explicitly requested.

Preserve proven patterns, not historical accidents. Reuse the good, consistent parts. When code you must touch or reuse has a genuine defect (a security flaw, a correctness bug, or a clear anti-pattern), do not silently copy it and do not silently rewrite it — flag it and ask whether to (a) match it for consistency, (b) fix it within the current scope, or (c) leave it and note a follow-up. Default to consistency for style; default to flagging for correctness and security. Never propagate a known security vulnerability for the sake of consistency.

When multiple established patterns exist, prefer the one the codebase is converging on — typically the most recent, most widely adopted, and actively maintained.

### Rule 3 — Prefer the smallest correct solution

Optimization requires evidence. Abstraction requires repetition. Architecture changes require explicit approval.

### Rule 4 — Do not solve future problems

Implement only current requirements.

### Rule 5 — Context is a constrained resource

Optimize for signal density, not token count.

---

## Phase 1: Requirement Analysis

Before any implementation determine:

- What exactly needs to change?
- Why does it need to change?
- What is the expected behavior?
- What files may be modified?
- What is out of scope?
- What assumptions exist?
- What information is missing?
- What constraints exist?
- What security requirements exist?
- What performance requirements exist?

If ambiguity exists: **STOP. Ask concise questions.**

Example:

```text
Before implementation I need clarification:

1. Should existing API contracts remain unchanged?
2. Is backward compatibility required?
3. Is this intended as a minimal fix or architectural improvement?
4. Are there security constraints that must be preserved?
```

---

## Phase 2: Pattern Discovery

Before writing code, analyze:

**Project Structure** — repository organization, folder structure, package boundaries, architectural layers.

**Coding Patterns** — variable declarations, naming conventions, function declarations, class patterns, component patterns, async patterns, error handling, logging conventions.

**Engineering Patterns** — dependency management, state management, API design, testing strategy, validation strategy, security patterns, caching patterns, configuration patterns.

**Architecture Patterns** — layering, composition, dependency direction, service boundaries, domain boundaries.

Produce:

```text
Observed Patterns

Variables:
- const preferred
- camelCase naming

Functions:
- arrow functions
- early returns

Architecture:
- service layer pattern
- repository pattern

Errors:
- centralized error handling

Testing:
- integration-first testing
```

Identify sufficient patterns to safely modify the requested code. Do not continue if critical patterns remain unclear.

---

## Phase 3: Solution Analysis

Always evaluate two approaches.

- **Option A** — smallest possible implementation.
- **Option B** — architectural or optimized implementation.

Provide:

```text
Minimal Approach
Files Changed: 2
Complexity: Low
Risk: Low
Maintenance Cost: Low

Optimized Approach
Files Changed: 9
Complexity: Medium
Risk: Medium
Maintenance Cost: Medium

Recommendation:
Use minimal approach because additional abstraction is not justified.
```

Default to minimal.

---

## Phase 4: Engineering Principles Validation

Continuously validate:

- **KISS** — Is this the simplest solution? Can complexity be reduced?
- **YAGNI** — Is this solving an actual requirement? Is this speculative functionality?
- **DRY** — Is existing logic duplicated? Can existing functionality be reused?
- **SOLID** — Are responsibilities preserved? Is coupling minimized? Are boundaries maintained?

### Principle Priority

Apply principles in this order:

1. Existing codebase patterns
2. KISS
3. YAGNI
4. DRY
5. SOLID

SOLID is advisory; existing project conventions always take precedence.

Never violate existing project conventions for theoretical purity.

---

## Phase 5: Implementation Rules

**Must:** follow existing patterns; preserve architecture, naming conventions, folder structure, API contracts, security boundaries, and testing conventions; reuse existing utilities; minimize code changes and files changed; prefer the solution that touches the fewest files, modules, and abstractions — prefer the smallest safe blast radius and preserve existing boundaries.

**Must Not:** refactor unrelated code; reorganize folders; rename unrelated structures; introduce new dependencies, abstractions, or future-proofing; optimize prematurely; rewrite working code.

### Anti-Overengineering

Do not introduce factories for one implementation, interfaces for one consumer, hooks/utilities/abstractions used once, generic wrappers, unnecessary services/repositories/configuration/dependency injection, or speculative extensibility/optimization.

> If a pattern exists fewer than three times, do not abstract it.

### No Heroics

Do not redesign systems, solve adjacent problems, fix unrelated issues, improve architecture opportunistically, or optimize without evidence — even when tempting.

---

## Immutable Rules

The best solution is the smallest secure solution that follows the existing codebase.

- Existing code is the primary source of truth; preserve proven patterns, not historical accidents.
- Never assume.
- Optimization requires evidence.
- Abstraction requires repetition.
- Architecture changes require approval.
- Security assumptions require clarification.
- Context is a constrained resource.
- Prefer the smallest safe blast radius.
- Solve today's problem only.
- Stop when certainty is insufficient.

---

## Detailed checklists

Before completion, security review, and major decisions, consult **`references/checklists.md`** — it contains the Security Validation taxonomy, the Changes Requiring Explicit Approval list, the "Before You Change Code" and "Completion" checklists, Token/Context Efficiency rules, and Failure Conditions.
