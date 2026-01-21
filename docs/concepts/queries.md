# Queries

A **Query** is a compile-time contract that declares access and eligibility.

Queries describe *what a system is allowed to access* and *which instances it
may operate on*, without defining execution or iteration behavior.

---

## Role of queries

Queries are used to:
- declare component access (read or write)
- express presence requirements
- restrict system eligibility
- define structural compatibility

Queries do not execute logic.
They do not iterate instances.
They do not control execution.

---

## Access contracts

A query specifies how a system intends to access components.

This includes:
- which **[Components](components.md)** are required
- whether access is immutable or mutable
- whether a component must be present or may be optional

Access rules are validated against **[Kinds](kinds.md)** at compile time
whenever possible.

---

## Structural matching

Queries match instances *structurally*.

An instance is eligible if:
- its **[Kind](kinds.md)** declares compatible components
- required access modes are satisfied
- required marker components are present in the expected state

Queries do not match absence.
All requirements are explicit and positive.

---

## Declaration

Queries are declared explicitly using the `#[query]` attribute.

```rust
#[query]
struct Movable(
    HasMut<Position>,
    Has<Velocity>,
);
```

This declaration defines a reusable access contract.

It does not describe iteration, ordering, or execution.

---

## Queries and systems

A **[System](systems.md)** may:
- declare one or more queries
- become eligible for a **[Context](contexts.md)** based on those queries

Eligibility is passive.
A system never runs because of a query alone.

---

## Queries and kinds

Queries are validated against **[Kinds](kinds.md)**.

A query is compatible with a kind if:
- all required components exist on the kind
- access modes are compatible
- marker requirements are satisfied

Incompatible queries result in compile-time errors whenever possible.

---

## What queries do not define

Queries do not define:
- how many instances are processed
- how instances are iterated
- execution order
- system scheduling
- context boundaries

These concerns belong to **[Systems](systems.md)** and
**[Contexts](contexts.md)**.

---

## Summary

- Queries declare access and eligibility
- Queries are structural and static
- Queries do not execute or iterate
- Queries restrict where systems may run
