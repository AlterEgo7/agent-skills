# Agent skills

Reusable skills for software engineering agents that support the Agent Skills format.

## Included skills

- **coding-principles** guides scoped implementation, clear code, behavioral verification, and root-cause debugging.
- **react-coding-preferences** layers personal React and TypeScript preferences over `vercel-react-best-practices` for client-rendered single-page apps: which Vercel rules apply to Vite, TanStack Router, TanStack Query and React Compiler, personal data kept out of browser storage, and the TypeScript discipline skills to load.
- **scala-coding-preferences** layers personal Scala coding preferences over other coding skills: direct combinators over short `for` comprehensions, braceless syntax, and tagless final services built around `AppResources`.
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

Replace `technical-writing` with `coding-principles`, `react-coding-preferences`, `scala-coding-preferences`, `smithy-principles`, or `vcs-conventions` to install another skill.

## License

[MIT](LICENSE)
