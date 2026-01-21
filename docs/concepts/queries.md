# Queries

A **Query** defines a compile-time access contract in Helix.

It describes what a system *intends* to access or control, without describing
how data is stored or how execution happens.

A query answers the question:

> “What does this system need, and under which conditions?”

---

## Role of queries

Queries are used to:
- declare access to components and tags
- express mutability and optionality
- define eligibility rules for systems
- group kinds by structural capability

Queries do not describe structure.
They describe **intent and access**.

---

## Queries and kinds

A query does not target a specific kind.

Instead, it is matched **structurally** against kinds.

A kind is eligible for a query if it satisfies all the query’s declared
requirements.

This allows:
- grouping different kinds under a common behavior
- separating instances of the same kind into different behavioral sets
- expressing capability-based logic

---

## Declaring a query

Queries are declared explicitly using the `#[query]` attribute.

```rust
#[query]
struct Movable(
    HasMut<Position>,
    Has<Velocity>,
);
```

This query declares that:
- `Position` must be present and accessed mutably
- `Velocity` must be present and accessed immutably

Any kind satisfying these requirements is eligible for this query.

---

## Access modifiers

Queries express access rules using explicit modifiers.

### Required components

- `Has<T>`  
  Requires component `T` to be present and accessed immutably.

- `HasMut<T>`  
  Requires component `T` to be present and accessed mutably.

---

### Optional components

- `Opt<T>`  
  Component `T` may or may not be present. Access is read-only.

- `OptMut<T>`  
  Component `T` may or may not be present. Access is mutable.

`OptMut<T>` expresses *optional access* and does not imply any specific
storage model.

---

### Structural mutation

- `SparseMut<T>`

`SparseMut<T>` expresses **structural mutation intent**.

It allows:
- inserting the component
- removing the component

This modifier only matches kinds where the component is declared as optional
and structurally mutable.

Unlike `OptMut<T>`, `SparseMut<T>` does not match dense components and
explicitly requires a sparse representation.

---

### Marker components (tags)

Queries can express conditions on marker components.

- `Is<Tag>`  
  Requires the tag to be present and active.

- `Not<Tag>`  
  Requires the tag to be present and inactive.

- `Maybe<Tag>`  
  The system explicitly handles whether the tag is present or not.

- `MaybeMut<Tag>`  
  Allows checking and mutating the tag’s presence when supported.

---

## Structural intent

Queries are intentionally **structural**, not nominal.

They resemble:
- trait bounds
- capability-based typing
- structural interfaces

A query defines *what a system can work with*, not *what it works on*.

---

## Query types

At a conceptual level, Helix distinguishes between:
- **instance queries**, which operate on entity instances
- **context queries**, which operate on context-level capabilities

A query is always one or the other.

---

## What queries do not define

Queries do not define:
- storage layout
- iteration order
- execution timing
- scheduling
- instance creation

Those concerns are handled elsewhere in the model.

---

## Summary

- A query defines an access contract
- Queries express intent, not structure
- Queries are matched structurally against kinds
- Queries enable static validation of system behavior
