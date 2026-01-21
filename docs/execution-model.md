# Execution Model

This document describes how execution happens in Helix.

It explains how **[Systems](concepts/systems.md)**, **[Contexts](concepts/contexts.md)**,
**[Queries](concepts/queries.md)**, and **[Kinds](concepts/kinds.md)** interact at runtime,
without introducing new structural concepts.

---

## Fundamental rule

All execution in Helix happens **inside a [Context](concepts/contexts.md)**.

Nothing executes implicitly.
Nothing executes globally.

If a system runs, it is because a context explicitly executed it.

---

## Eligibility vs execution

A **[System](concepts/systems.md)** declares constraints through its parameters
or associated **[Queries](concepts/queries.md)**.

If those constraints are compatible with the structure of a
**[Context](concepts/contexts.md)**, the system becomes *eligible* for that context.

Eligibility is passive.

A system does **not** run just because it is eligible.
Execution happens only when the context explicitly invokes the system.

---

## Execution roots

Helix defines a fixed set of execution roots (lifecycle phases).

A context may define an entry point for any of these roots.
If a root is not defined, it is treated as a no-op.

Roots are the only entry points through which the runtime initiates execution.
All other system execution originates from these roots.

---

## System invocation

Systems may be executed in two ways:

- directly from a context root
- from another system

In both cases, execution is explicit and visible in user code.

There is no implicit scheduling or automatic system chaining.

---

## Instance execution

When a system operates on instance-level data, execution is driven by
**[Queries](concepts/queries.md)** matched against **[Kinds](concepts/kinds.md)**.

For each eligible instance, the system logic is applied according to
the system’s declared access pattern.

Iteration behavior is part of the execution model and is never inferred
from hidden rules.

---

## Context-scoped execution

Some systems are defined directly within a **[Context](concepts/contexts.md)**.

These systems:
- are bound to a specific context
- may access context-level APIs directly
- follow the same eligibility and execution rules

This allows local orchestration logic without weakening execution boundaries.

---

## Execution boundaries

A **[Context](concepts/contexts.md)** represents an execution boundary.

- execution does not cross contexts implicitly
- contexts may execute independently
- cross-context interaction is explicit and controlled

Concurrency between contexts is handled by the runtime.
Users never manage synchronization between contexts directly.

---

## Determinism and visibility

Helix favors explicit execution over implicit optimization.

Execution order, system invocation, and control flow are always visible
in user-defined code.

Any form of parallelism or reordering must be explicitly introduced and
validated against the execution model.

---

## Summary

- All execution happens inside a context
- Eligibility does not imply execution
- Execution starts from explicit roots
- Systems never execute implicitly
- Execution boundaries are explicit and enforced
