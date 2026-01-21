# Helix — Overview

Helix is a runtime framework that treats **structure, access, and execution**
as explicit, statically verifiable concepts.

Rather than inferring behavior at runtime, Helix requires systems to declare
what can exist, what can be accessed, and where execution is allowed to happen.
This information is validated as early as possible using Rust’s type system.

The result is a model that favors predictability and clarity over implicit
behavior and hidden rules.

---

## The model

Helix is built around five core concepts:

- **[Components](concepts/components.md)** represent data or markers.
- **[Kinds](concepts/kinds.md)** describe the structure of instances.
- **[Queries](concepts/queries.md)** declare access and intent.
- **[Systems](concepts/systems.md)** implement behavior.
- **[Contexts](concepts/contexts.md)** define execution boundaries.

Each concept has a single responsibility.
Their interaction defines the runtime behavior.

---

## Separation of concerns

Helix enforces a strict separation between:

- **what exists** — defined by *kinds*
- **what can be accessed** — defined by *queries*
- **what logic exists** — implemented in *systems*
- **where execution happens** — defined by *contexts*

No concept overlaps in responsibility.
Nothing exists or executes implicitly.

---

## Execution philosophy

Systems never decide:
- where they run
- when they run
- what data exists

Contexts never contain business logic.

Execution is always explicit and intentional:
systems are executed only when a context invokes them.

---

## Validation

Helix validates structural correctness at compile time whenever possible.

This includes:
- compatibility between *queries* and *kinds*
- system eligibility within a *context*
- enforcement of execution boundaries

Runtime behavior follows directly from these validated declarations.

---

## Scope

Helix does not provide:
- implicit scheduling
- automatic system ordering
- hidden global state
- domain-specific abstractions

It provides a small, explicit core that can be used to build
game engines, simulations, servers, or other runtime-driven systems.

---

## Reading guide

This documentation is organized by concept.
Each core concept has a dedicated document and is linked inline when referenced.

A typical reading order is:
**Components → Kinds → Queries → Systems → Contexts**

Details about execution semantics are described in the
**[Execution Model](execution-model.md)**.

---

## Status

Helix is a personal project and a work in progress.

The conceptual model is stable.
Implementation details evolve as the design is refined.
