---
name: smithy-principles
description: Personal Smithy modelling principles. Use when designing, writing, or reviewing Smithy models.
---

# Smithy principles

Apply every principle below to each shape, validator, and model file you add, change, or review, and flag existing ones that break a principle.

## Newtype every member

Every member targets a named shape. Each simple value gets a _newtype_: a simple shape in your own namespace, reused by every member that holds the same value. This covers structure, union, list and map members, including the members of operation inputs and outputs.

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

## Name shapes specifically

Be sceptical of generic shape names such as `Email`, `Status` or `Details`. A later shape with a different meaning will likely want the same name, and readers cannot tell which meaning a member uses. Prefer a name that says what sets the value apart, such as `VerifiableEmail` for an address together with its verification status. Keep a short name only when the model can give that word no other meaning.

When you are unsure which name fits, ask the user to choose from your candidate names, with the trade-off of each, before you write the shape.

## Write validator messages about the problem

A validator's `message` helps the person who sees it understand what is wrong with their model and how to fix it. Describe the problem in the model's terms, not how the validator discovered it, such as the selector or the traits it matched.

```text
Prefer: This value has no type of its own, so the model cannot say what it means or which values are valid. Define a newtype for it.
Over:   Members must not target prelude shapes.
```

## Lay out the model by module

Keep the Smithy project in a top-level `smithy/` directory with one directory per module, such as `gateway/`, `healthchecks/` or `identity/`. Each module separates services from shapes, and public services from internal ones:

```text
smithy/<module>/
├── api/
│   ├── errors/      # error structures
│   ├── internal/    # services that only callers inside the system reach
│   └── public/      # services that clients call through the gateway
└── model/
    ├── *.smithy     # shapes that the module's public and internal services share
    ├── internal/    # inputs, outputs and other shapes that only internal services use
    └── public/      # inputs, outputs and other shapes that only public services use
```

- Leave out directories that would be empty.
- Give a versioned service a version directory under both `api/public/` and `model/public/`, such as `identity/api/public/v1/` and `identity/model/public/v1/`.
- Give every operation named `@input` and `@output` structures in `model/` instead of declaring them inline.
- Put shapes that belong together in one file named after what relates them, such as `verifiable-email.smithy` for an email structure and its newtypes. Never put all of a module's shapes in one file.
- Put definitions that several modules share in a module of their own, such as `gateway/`.

## Keep validators in their own files

Put `metadata validators` in files that define no shapes, separate from the shapes they check. Validators that apply to the whole model go in a file without a namespace at the root of the Smithy project, such as `conventions.smithy`. Validators for one module go in that module's directory, such as `gateway/validators.smithy`.
