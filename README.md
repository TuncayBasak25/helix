# Helix

Helix is an experimental runtime framework written in Rust.

It focuses on making **structure, access, and execution explicit and statically
verifiable**, using Rust’s type system as the primary source of correctness.

Helix is designed around clarity, predictability, and explicit control,
rather than implicit behavior or runtime inference.

---

## Core idea

Helix models execution as the interaction of a small set of explicit concepts:

- **[Components](docs/concepts/components.md)** — data or marker types
- **[Kinds](docs/concepts/kinds.md)** — static descriptions of what can exist
- **[Queries](docs/concepts/queries.md)** — access and intent contracts
- **[Systems](docs/concepts/systems.md)** — pure logic
- **[Contexts](docs/concepts/contexts.md)** — execution boundaries

Each concept has a single, well-defined responsibility.
Their interaction defines the execution model.

---

## What Helix is

Helix is a framework where:

- existence is declared explicitly through *kinds*
- access is declared explicitly through *queries*
- behavior is implemented in *systems*
- execution happens only inside *contexts*

Nothing exists, runs, or interacts implicitly.

---

## What Helix is not

Helix does not:
- infer execution order
- schedule systems implicitly
- hide ownership or access rules
- couple application logic to a specific domain

All execution is intentional and visible.

---

## Usage philosophy

Helix is not a framework you “run”.

It is a framework you **define against**.

Users describe:
- which components exist
- which kinds are possible
- which systems are available
- which contexts execute them

Helix validates these definitions at compile time and provides a minimal
runtime to execute them.

---

## Status

Helix is a personal project and a work in progress.

The core model and direction are stable.
Implementation details continue to evolve as the design is refined.

---

## Documentation

- [Overview](docs/overview.md)
- [Components](docs/concepts/components.md)
- [Kinds](docs/concepts/kinds.md)
- [Queries](docs/concepts/queries.md)
- [Systems](docs/concepts/systems.md)
- [Contexts](docs/concepts/contexts.md)
- [Execution model](docs/execution-model.md)
- [Design decisions](docs/design-decisions.md)
