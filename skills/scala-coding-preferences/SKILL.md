---
name: scala-coding-preferences
description: Personal Scala coding preferences. Use alongside coding-principles and relevant library skills when writing, refactoring, or reviewing Scala code.
---

# Scala coding preferences

Apply these preferences as an overlay to other coding skills.

- Prefer direct combinators over short `for` comprehensions when they express the same operation clearly. Choose a suitable combinator from the receiver's API, preserving effect order and whether the original or transformed value is returned. The examples `map`, `flatMap`, `flatTap`, `evalMap`, and `evalTap` are illustrative, not exhaustive.
- Write Scala 3's braceless syntax: indentation for blocks and a colon before a lambda or `case` argument, as in `.flatMap: logger =>` and `HttpRoutes.of[F]:`. When the project has a `.scalafmt.conf`, run its formatter so the configuration settles layout.
- Write services in tagless final style. Every class and function takes an effect type `F[_]` with context bounds for the smallest typeclasses it uses, from cats, cats-effect, cats-mtl and libraries such as log4cats and otel4s, as in `def health[F[_]: {Concurrent, Logger}]`. Only the entry point, the `IOApp`, fixes `F` to `IO` and supplies `IO`-specific instances, such as a logger or an `IOLocal` context provider; tests may also fix `F` to `IO`.
- Compose a service around `AppResources[F]`: a case class holding its long-lived dependencies, such as clients, telemetry and shared state, in a `resources` package, built once by `AppResources.build[F]`, which returns a `Resource[F, AppResources[F]]`. The entry point loads configuration, builds `AppResources`, and passes its fields to routes and servers.
