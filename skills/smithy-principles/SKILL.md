---
name: smithy-principles
description: Personal Smithy modelling principles. Use when designing, writing, or reviewing Smithy models.
---

# Smithy principles

Apply every principle below to each shape you add, change, or review, and flag existing shapes that break one.

## Newtype every member

Every member targets a named shape. Each simple value gets a _newtype_: a simple shape in your own namespace, reused by every member that holds the same value. This covers structure, union, list and map members, including the members of inline operation inputs and outputs.

Constraints live on the newtype. It carries every constraint trait that applies to its value, such as `@length`, `@pattern` or `@range`, and the members targeting it carry no constraint traits. A member that needs different limits gets its own newtype. A value with no applicable constraint still gets a newtype, with no constraint traits.

Members never target a prelude simple type such as `String`, `Integer` or `Boolean`, or another library's simple shape such as `alloy#UUID`. Apply the library's trait to your own newtype instead, as in `@alloy#uuidFormat string ChildId`.

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
