---
name: vcs-conventions
description: "REQUIRED when naming a branch/bookmark, writing a commit message, or writing a PR title/description, in git or jj. Overrides format rules in the git/jujutsu skills."
---

# VCS Conventions

Applies to git and jj (bookmark = branch, description = commit message).

## Commits
- Subject: `PREFIX: message`: an uppercase prefix, a colon, one space, and a concise description of the change.
  e.g. `FIX: Preserve track order when importing playlists`

  | Prefix | Change |
  | --- | --- |
  | `ADD` | Add a new feature, component, or other capability. |
  | `FIX` | Fix a bug, incorrect implementation, or incorrect test. |
  | `RFC` | Refactor existing code. |
  | `RMV` | Remove code or components that are no longer needed. |
  | `FMT` | Formatting changes only. |
  | `CHG` | Changes that fit none of the categories above. |

- Choose the prefix from the actual changes in the commit, not just its existing message. For mixed changes, use the prefix matching the commit's main purpose. Use `FMT` only when every change is formatting-only.
- When rewording, preserve the meaning of the commit while applying this format.
- Optional body: only context the diff can't show.
- No attributions: no `Co-authored-by`/`Generated-by` trailers, tool or agent credits, or names.

## Branches
`<ticket>-<short-title>`: lowercase, kebab-case, 2–5 words, no username or type prefix. Ignore tracker-suggested names.
e.g. `audio-247-preserve-playlist-order`

## PRs
- Title = commit subject.
- Description goes in the template's freeform section (usually `Summary`). Fill other template sections factually and delete irrelevant ones. No template: ticket link, then description.
- Write for a human reviewer: brief, dense, only what they can't get faster from the diff or ticket. That means what the change does, non-obvious decisions and why, risks or one-way doors, the tricky part to scrutinise, merge or deploy notes.
- Never: restate the ticket, list what wasn't done, narrate files or process, add filler, or include test boilerplate.

Bad: "This PR addresses AUDIO-247… I investigated… Changes: updated PlaylistImporter.scala, added sorting. Note: doesn't fix playback."
Good: "Preserves playlist order using each entry's source position rather than its track title. Duplicate tracks stay in place because positions belong to playlist entries, not tracks. Review the handling of missing positions: those entries remain at the end in their original relative order."
