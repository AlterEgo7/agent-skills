---
name: coding-principles
description: Software coding principles for planning and performing code changes. Always use alongside planning skills when a plan is intended to produce code, tests, build, CI, or configuration changes; also use during implementation, editing, refactoring, testing, debugging, and review. Do not use for documentation-only work, planning with no intended software change, or operational summaries.
---

# Coding Principles

## Scope

- Make the smallest safe change that fully satisfies the requirement; avoid speculative work and unrelated refactors.
- Preserve existing implementations. Do not rewrite or replace them, or add backward-compatibility behavior, without explicit approval.
- Prefer simple, maintainable solutions. Remove duplication introduced or exposed by the change when that stays within scope; do not broaden the task only to deduplicate unrelated code.
- Follow the nearest repository instructions and the surrounding code's conventions.

## Clarity

- Name code for its current domain purpose, not its history, implementation mechanism, or unnecessary pattern jargon.
- Import symbols and use their declared class, type, function, or value names without namespace prefixes whenever this is unambiguous. When names conflict, first prefer an import rename or alias in languages that support it; otherwise use the shortest namespace prefix that resolves the ambiguity. Use longer or fully qualified names only when neither option is available.

  For example, in Scala:

  ```scala
  import example.library.{Config as LibraryConfig, Parser}

  val parser = Parser(...)
  val config = LibraryConfig(...)
  ```

  Prefer this over repeating `example.library.Parser(...)` or another unnecessarily long namespace at each use site.
- Add a short, precise comment only when it usefully explains non-obvious rationale that the code cannot express clearly; when in doubt, omit it.
- For necessary comments about an entire declaration, prefer the language's supported documentation-comment format, such as Javadoc, Scaladoc, or equivalent. Use a plain code comment only when a documentation comment is inappropriate.
- Keep comments current and preserve existing comments; only remove or correct one when it is demonstrably false. Do not narrate change history.

## Verification

- Keep planning, review, and verification proportional to the task's scope and risk. Require only checks that can materially affect the requested behavior.
- Test real behavior. Mocks may isolate collaborators, but assertions must cover the subject's behavior; do not use mocks in end-to-end tests.
- Do not delete or weaken failing tests; preserve meaningful coverage for changed behavior.
- Run relevant validation and inspect its output. Do not ignore, suppress, or misreport failures.
- Do not block or iterate on optional, redundant, unrelated, or pre-existing validation concerns; note them briefly and proceed. Investigate failures only when the change caused them or they undermine confidence in the requested outcome.
- Stop once sufficient evidence shows that the requested behavior works. Do not pursue low-impact verification rabbit holes or additional checks that cannot change the conclusion.

## Debugging

- Diagnose and fix root causes, not symptoms or workarounds. Reproduce the failure, prove the cause with the smallest failing case, and verify the fix against it.
