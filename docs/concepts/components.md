# Components

A **Component** represents a unit of information that can be attached to an
instance in Helix.

From the user’s perspective, a component is simply:
- a named piece of data, or
- a named marker whose presence alone is meaningful.

Components are declared explicitly and do not contain behavior.

---

## Data components

A **data component** carries a value.

```rust
#[component]
struct Health(f32);
```

In this example, `Health` is a component holding a `f32` value.

Data components represent state.
They are accessed by systems through queries and never act on their own.

---

## Marker components

A **marker component** (or tag) carries no data.

```rust
#[component]
struct Broken;
```

For marker components, only presence or absence matters.

Markers are typically used to:
- express state flags
- classify instances
- enable or disable behavior through queries

---

## Unified concept

Although data components and marker components differ internally,
they are treated uniformly at the Helix interaction level.

Both are:
- declared the same way
- attached to kinds
- accessed through queries
- validated statically

This allows systems to reason about structure and intent without
depending on representation details.

---

## Components and behavior

Components never contain logic.

All behavior in Helix lives in **systems**, which operate on components
through explicitly declared queries.

This separation ensures that:
- data remains passive
- access rules are explicit
- behavior is centralized and predictable

---

## What components do not define

Components do not define:
- how they are stored
- how many instances exist
- when or where they are accessed
- how execution happens

Those concerns are handled by kinds, queries, systems, and contexts.
