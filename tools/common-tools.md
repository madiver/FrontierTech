# Common Tools

Reusable development tools that are broadly useful across software projects.

This list is intentionally small and practical. Prefer official install pages, avoid project-specific setup assumptions, and add notes only when they help a new project adopt the tool safely.

| Tool | What It Is Useful For | Install / Setup Link | Notes |
| --- | --- | --- | --- |
| [Spec Kit](https://github.com/github/spec-kit) | Specification-driven development workflows with AI coding agents. It helps create specs, plans, tasks, and project guidance for structured implementation work. | [Spec Kit installation guide](https://github.com/github/spec-kit/blob/main/docs/installation.md) | The official docs recommend installing from the GitHub repository. Pin a release tag for repeatable team setup. |
| [GitHub CLI (`gh`)](https://cli.github.com/) | Working with GitHub from the terminal, including issues, pull requests, releases, workflow runs, and repository automation. | [GitHub CLI installation instructions](https://github.com/cli/cli#installation) | Useful for agent workflows that need to inspect PRs, fetch CI logs, create issues, or automate GitHub tasks with explicit user approval. |
| [am-will/codex-skills](https://github.com/am-will/codex-skills) | A community collection of Codex and agent skills for planning, documentation access, frontend development, browser automation, hooks, and multi-agent workflows. | [Repository installation instructions](https://github.com/am-will/codex-skills?tab=readme-ov-file#installation) | Includes the `frontend-design` skill. Review each skill's license and attribution before copying text; the repository notes some skills are imported from upstream sources. |

## Contribution Guidelines

When adding a tool:

- Link to the official project page.
- Link directly to the official install or setup instructions.
- Keep the description project-neutral.
- Mention security, authentication, or version-pinning concerns when relevant.
- Avoid recommending tools that require private credentials, paid services, or company-specific infrastructure unless the entry clearly explains that dependency.
