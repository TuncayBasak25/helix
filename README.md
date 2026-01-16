# Helix

Helix is a compile-time language for building deterministic runtimes
(games, simulations, servers, tools) with fully static, typed APIs.

Helix is written *in* Rust syntax, but it is **not a Rust library**.
It is a language frontend, compiler toolchain, and runtime generator.

## Core ideas

- User code lives in `src/**.rs`
- Helix generates typed APIs in `src/helix/`
- A compiler backend generates a separate runnable project
- The generated runtime is deterministic by construction
- Optimization is a backend concern, not a language concern

## Project status

This repository currently focuses on the **language frontend**:
syntax, semantics, tooling, and generated APIs.
The runtime compiler backend will be implemented later.

## Structure

- `helix/` — the Helix language toolchain (macros, watcher, CLI)
- `examples/` — small Helix programs
- `docs/` — design and architecture notes
