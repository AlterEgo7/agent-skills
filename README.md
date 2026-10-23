# Agent skills

Reusable skills for software engineering agents that support the Agent Skills format.

## Included skills

- **coding-principles** guides scoped implementation, clear code, behavioral verification, and root-cause debugging.
- **commit-messages** guides VCS commit subjects when creating or rewording commits.
- **scala-coding-preferences** layers personal Scala coding preferences over other coding skills, favoring direct combinators over short `for` comprehensions.
- **technical-writing** guides concise, accurate engineering documentation and software-development communication.

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

Replace `technical-writing` with `coding-principles`, `commit-messages`, or `scala-coding-preferences` to install another skill.

## License

[MIT](LICENSE)
