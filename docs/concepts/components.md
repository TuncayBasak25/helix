# Components

A **Component** represents a unit of data or a marker that can be attached to an instance.

Components describe *what data exists*, but not *how it is accessed*,
*how it is stored*, or *how it is used*.

---

## Role of components

Components are the smallest building blocks in Helix.

They are used to:
- describe the data carried by instances
- express capabilities or properties through markers
- serve as the basis for structural definitions and access contracts

Components are passive.
They do not contain behavior and do not execute.

---

## Data and marker components

Helix distinguishes between two kinds of components:

### Data components

Data components carry values.

They represent structured data that systems may read or mutate,
depending on declared access.

### Marker components

Marker components carry no data.

Their presence or absence is meaningful by itself and is typically used
to express properties, states, or capabilities.

Marker components are treated as first-class components,
even though they do not store values.

---

## Declaration

Components are declared explicitly using the `#[component]` attribute.

```rust
#[component]
struct Position(f32, f32);

#[component]
struct Grounded;
```

This declaration defines a component type.
It does not determine where the component exists or how it is accessed.

---

## What components do not define

Components do not define:
- how instances are structured
- whether a component is optional or required
- whether a component is mutable or immutable
- how components are accessed
- where components exist

These aspects are defined by **[Kinds](kinds.md)**,
**[Queries](queries.md)**, and **[Contexts](contexts.md)**.

---

## Summary

- Components represent data or markers
- Components are passive and declarative
- Components do not define structure or behavior
- Components are used by other concepts to express meaning
