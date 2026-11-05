# Agent skills

Reusable skills for software engineering agents that support the Agent Skills format.

## Included skills

- **coding-principles** guides scoped implementation, clear code, behavioral verification, and root-cause debugging.
- **scala-coding-preferences** layers personal Scala coding preferences over other coding skills, favoring direct combinators over short `for` comprehensions.
- **smithy-principles** sets personal Smithy modelling principles, such as targeting a constrained newtype from every member.
- **technical-writing** guides concise, accurate engineering documentation and software-development communication.
- **vcs-conventions** sets commit, branch/bookmark, and PR title/description conventions for git and jj.

## Install

List the available skills:

```bash
npx skills add AlterEgo7/agent-skills --list
```

Install the skills interactively:

```bash
npx skills add AlterEgo7/agent-skills
```

Install one skill globally for OpenCode:

```bash
npx skills add AlterEgo7/agent-skills \
  --skill technical-writing \
  --agent opencode \
  --global
```

Replace `technical-writing` with `coding-principles`, `scala-coding-preferences`, `smithy-principles`, or `vcs-conventions` to install another skill.

## License

[MIT](LICENSE)
