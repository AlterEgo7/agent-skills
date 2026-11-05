---
name: smithy-principles
description: Personal Smithy modelling principles. Use when designing, writing, or reviewing Smithy models.
---

# Smithy principles

Apply every principle below to each shape you add, change, or review, and flag existing shapes that break one.

## Newtype every member

Every member targets a named shape. Each simple value gets a _newtype_: a named simple shape, reused by every member that holds the same value. This covers structure, union, list and map members, including the members of inline operation inputs and outputs. A newtype carries every constraint trait that applies to its value, such as `@length`, `@pattern` or `@range`. A value with no applicable constraint still gets a newtype, with no constraint traits.

Members never target a prelude simple type such as `String`, `Integer` or `Boolean` directly.

```smithy
@range(min: 1, max: 100)
integer Quantity

string OrderNote

structure OrderLine {
    @required
    quantity: Quantity

    note: OrderNote
}
```
