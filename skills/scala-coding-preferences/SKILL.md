---
name: scala-coding-preferences
description: Personal Scala coding preferences. Use alongside coding-principles and relevant library skills when writing, refactoring, or reviewing Scala code.
---

# Scala coding preferences

Apply these preferences as an overlay to other coding skills.

- Prefer direct combinators over short `for` comprehensions when they express the same operation clearly. Choose a suitable combinator from the receiver's API, preserving effect order and whether the original or transformed value is returned. The examples `map`, `flatMap`, `flatTap`, `evalMap`, and `evalTap` are illustrative, not exhaustive.
