---
name: commit-messages
description: VCS commit message format. Use when creating a commit, drafting a commit message, or renaming/rewording an existing commit message, including amend and rebase operations.
---

# Commit messages

Write the commit subject as `PREFIX: message`: an uppercase prefix, a colon, one space, and a concise description of the change.

| Prefix | Change |
| --- | --- |
| `ADD` | Add a new feature, component, or other capability. |
| `FIX` | Fix a bug, incorrect implementation, or incorrect test. |
| `RFC` | Refactor existing code. |
| `RMV` | Remove code or components that are no longer needed. |
| `FMT` | Formatting changes only. |
| `CHG` | Changes that fit none of the categories above. |

- Choose the prefix from the actual changes in the commit, not just its existing message.
- For mixed changes, use the prefix matching the commit's main purpose. Use `FMT` only when every change is formatting-only.
- When rewording, preserve the meaning of the commit while applying this format.
