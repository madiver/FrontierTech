# Create Agent Instructions File

Use this prompt in a new repository when you want a coding agent to create a reusable project instructions file.

```text
Create an agent-instructions file for this repository.

If you are running inside Codex, create or update `AGENTS.md`.
If you are running inside Claude Code, create or update `CLAUDE.md`.
If you cannot confidently detect the environment, ask me which filename to use before writing.

First, briefly inspect the repository structure so the file reflects the project without inventing details. Keep the result generic and reusable. Do not add product-specific rules unless they are obvious from the repository.

The file should establish these generic software-engineering policies:

1. Engineering Standards
- Prefer production-ready, maintainable fixes over temporary or dev-only shortcuts.
- Read and understand the existing code before changing it.
- Follow existing project patterns, frameworks, and conventions.
- Keep changes small, incremental, and reversible.
- Resolve root causes instead of masking defects with superficial workarounds.
- Add abstractions only when they reduce real complexity or match an established pattern.
- For projects using languages with dependency isolation (Python, Node.js, Ruby, etc.), set up a virtual environment or equivalent isolation mechanism as part of initial project setup. Use the project's chosen tooling (uv for Python, npm/pnpm for Node, bundler for Ruby).

2. Repository Boundaries
- Preserve module, package, and repo boundaries.
- Keep app-specific logic out of shared libraries.
- Keep backend, frontend, infrastructure, and tooling concerns separated unless the project already uses a different pattern.
- Do not introduce cross-layer dependencies without a clear reason.

3. Security And Privacy
- Do not hardcode secrets, tokens, credentials, API keys, or private URLs.
- Use the project-approved secrets/configuration mechanism.
- Do not log sensitive values.
- Diagnostics, exports, and debug tools should be allowlist-based and avoid sensitive data.
- Treat authentication, authorization, payment, identity, and data-retention changes as high-risk.

4. Git Policy
- Do not run `git commit`, `git push`, `git merge`, `git rebase`, branch creation, or destructive git commands unless explicitly requested in the current task.
- Never revert user changes unless explicitly instructed.
- Check worktree status before broad edits.
- If unrelated changes exist, leave them alone.

5. Testing And Validation
- Use the repository's existing test runner, package manager, virtualenv, or build tooling.
- Add or update tests for behavior changes.
- Run focused tests first, then broader tests when risk justifies it.
- If tests cannot be run, explain why and identify residual risk.
- Validate supported runtime or packaging behavior before calling work complete when relevant.

6. Issue And PR Workflow
- When work is tied to issue tracking, reference the issue.
- Issue titles should describe the problem plainly.
- Issue bodies should include: Summary, Impact, Evidence, Proposed fix, and Acceptance criteria.
- PR descriptions should include root cause, solution summary, linked issues, and tests run.
- Use closing keywords like `Fixes #123` only when the PR fully resolves the issue.

7. UI/UX Work
- Follow the existing design system and UI patterns.
- Keep layouts simple, deterministic, accessible, and testable.
- Reuse established components before creating new ones.
- Persist only normalized user settings or state.
- Avoid one-off UI wiring unless explicitly justified.
- Validate responsive behavior or supported desktop platforms when relevant.

8. Documentation
- Prefer updating canonical docs over scattering notes.
- Document commands, architecture decisions, and recurring pitfalls only when they help future work.
- Keep project-specific notes separate from generic rules.

Write the file in clear Markdown with concise sections. Start with a short title and a one-paragraph purpose statement. Include a final `Project-Specific Notes` section with placeholders for:
- Tech stack
- Dependency management and virtual environment setup
- Common commands
- Architecture boundaries
- Testing notes
- Deployment/packaging notes
- Known pitfalls

Do not include references to any previous project, product, framework, or tool unless this repository actually uses it. It is fine to mention Codex or Claude Code only when explaining which agent-instructions filename was selected.

After writing the file, summarize what you created and mention the path.
```
