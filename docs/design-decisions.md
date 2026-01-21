# Design Decisions

This document records the major design decisions behind Helix.

It focuses on *why* certain choices were made, rather than *how* they are implemented.
The goal is to make the design intent explicit and avoid ambiguity.

---

## Explicitness over inference

Helix favors explicit declarations over runtime inference.

Rather than inferring execution order, access patterns, or system dependencies,
Helix requires these aspects to be stated directly through
**[Kinds](concepts/kinds.md)**, **[Queries](concepts/queries.md)**,
**[Systems](concepts/systems.md)**, and **[Contexts](concepts/contexts.md)**.

This improves predictability, debuggability, and compile-time validation.

---

## Eligibility is passive

A **[System](concepts/systems.md)** becomes *eligible* for a
**[Context](concepts/contexts.md)** when its declared constraints are compatible.

Eligibility does not imply execution.

Systems run only when explicitly invoked by a context, either from a lifecycle
root or from another system.

This avoids hidden control flow and implicit scheduling.

---

## Separation of structure and execution

Helix strictly separates:
- structural declarations (*what can exist*)
- execution decisions (*what actually runs*)

**[Kinds](concepts/kinds.md)** and **[Queries](concepts/queries.md)** describe
structure and access.

**[Contexts](concepts/contexts.md)** control execution.

This separation prevents accidental coupling between data layout and behavior.

---

## No implicit scheduling

Helix does not provide:
- automatic system ordering
- dependency-based scheduling
- hidden execution graphs

Any execution order or control flow must be expressed explicitly in user code.

This makes execution behavior fully visible and intentional.

---

## Compile-time validation first

Whenever possible, Helix shifts errors from runtime to compile time.

This includes:
- incompatible queries
- invalid access modes
- system-context mismatches
- illegal execution boundaries

Some runtime checks remain unavoidable, but they are minimized by design.

---

## Minimal core, extensible surface

Helix aims to keep its core model small and well-defined.

Rather than embedding domain-specific behavior (e.g. rendering, IO, events),
Helix provides a foundation on which such systems can be built explicitly.

This keeps the core reusable across domains such as games, simulations, or servers.

---

## Explicit trade-offs

Helix intentionally accepts:
- more verbose declarations
- stricter APIs
- less automation

in exchange for:
- stronger guarantees
- clearer mental models
- predictable execution

These trade-offs are considered fundamental to the design.

---

## Open directions

Some aspects of the design are still evolving.

Examples include:
- finer-grained execution control
- improved ergonomics for common system patterns
- representation of context-level state

These areas are explored cautiously to avoid weakening the core model.

---

## Summary

Helix is designed around explicit structure, explicit access, and explicit execution.

Every major design decision follows this principle.
