# New Project Scaffold

Use this prompt in an empty project folder to set up the standard Frontier Tech scaffolding before any product work begins. It initializes git, creates the agent instructions file, sets up a generic `.gitignore`, creates a `README.md` from your project description, checks for required tools, makes the initial commit, and optionally creates and pushes a GitHub repository with a license.

The prompt is interactive at three points: it asks for a project description, asks about installing missing tools, and asks about GitHub setup. Each interactive moment is a natural pause point that fits cleanly into a paired-programming or live-broadcast workflow.

```text
Set up this new project folder with the Frontier Tech standard scaffolding.
Work through these steps in order. Stop when complete and wait for me to
begin the concept conversation for the project.

1. Initialize a git repository in the current directory.

2. Create the agent instructions file by fetching and following the prompt at:
   https://github.com/madiver/FrontierTech/blob/main/prompts/create-agent-instructions-file.md

   That prompt will produce AGENTS.md (Codex) or CLAUDE.md (Claude Code)
   with generic engineering policies. Keep it generic; project-specific
   notes will be filled in later.

3. Create a generic .gitignore with common patterns: node_modules/,
   __pycache__/, *.pyc, .venv/, venv/, .env, .DS_Store, dist/, build/,
   .vscode/, .idea/.

4. Ask me to briefly describe this project in one or two sentences.
   The description will:
   - Appear in README.md beneath the folder name as the H1 title
   - Inform the concept conversation that follows in a later step

   Wait for my answer, then create README.md with my description.

5. Fetch the Frontier Tech common tools list at:
   https://github.com/madiver/FrontierTech/blob/main/tools/common-tools.md

   For each tool listed:
   - If the tool provides a CLI command (e.g., Spec Kit -> speckit,
     GitHub CLI -> gh), check whether the command is available on PATH.
   - If the tool is a reference repository or skill library rather than
     a CLI, list it as a resource I may want to install later and skip
     the availability check.

   For any CLI tool that is missing, ask me whether to install it before
   proceeding. Use the official install link from common-tools.md when
   installing.

6. Configure git, optionally set up GitHub, and create the initial commit.

   First, ask me whether to create a GitHub repository for this project.

   If I say yes:
   - Ask me for the repository name (default: the folder name).
   - Ask me whether the repository should be public or private.
   - If public, ask me which open source license to apply:
     1. MIT (permissive, simple, widely compatible)
     2. Apache 2.0 (permissive, includes patent grant)
     3. GPL v3 (copyleft, derivatives must also be GPL)
     4. BSD 3-Clause (permissive, similar to MIT)
     5. None / decide later
   - If I choose a license, create a LICENSE file in the project root
     with the canonical license text from https://choosealicense.com
     or https://opensource.org/licenses. Get the copyright holder name
     from `git config user.name` (ask me if not configured) and use the
     current year.

   Then, regardless of remote choice:
   - Stage all files with `git add -A`.
   - Make the initial commit with the message:
     "chore: initial project scaffolding".

   This step explicitly authorizes the git commit operation (overriding
   the general git policy from AGENTS.md / CLAUDE.md).

   If I chose to create a GitHub repository:
   - Create the GitHub repository with the chosen name and visibility,
     set the local repository's origin remote to the new GitHub
     repository, and push the initial commit. Use:
     `gh repo create <name> --<public|private> --source=. --remote=origin --push`

   This step explicitly authorizes the git push operation.

   If `gh` is not installed, not authenticated, or fails for any reason,
   surface the issue and ask me how to proceed (continue without remote,
   install or authenticate gh, or skip and I will create the remote
   manually later).

   If I said no to GitHub, do not create a remote or push. The initial
   commit stands as a local-only checkpoint.

7. Set up the language environment based on the project description.

   Reread the description I provided in step 4 and identify any languages
   mentioned (e.g., Python, Node.js, Ruby, Go, Rust).

   If a language is clearly identified:
   - Propose the standard isolation/dependency tool for that language
     (Python -> uv venv, Node.js -> npm or pnpm init, Ruby -> bundle init,
     Go -> go mod init, Rust -> cargo init).
   - Ask me whether to set it up now or defer to after the concept
     conversation.

   If no language is clear from the description:
   - Ask me which language(s) the project will use.
   - Then propose appropriate isolation setup for each, and ask whether
     to set it up now or defer.

   If I choose to set up now:
   - Run the appropriate command(s) to create the environment
     (e.g., `uv venv` for Python).
   - Verify the environment is functional with a sanity check appropriate
     to the tool (e.g., `uv pip list` for Python, `npm --version` from
     within the project for Node).
   - Confirm to me that the environment was created and is functional.

   If I choose to defer: do nothing further on this step. The concept
   conversation will inform the language decision and the appropriate
   setup will happen either during spec-kit task execution or as a
   separate follow-on step.

Stop after step 7. Do not initialize spec-kit, do not generate a roadmap,
and do not start any spec-kit workflow until I explicitly request it.
```

## What Happens Next

After the scaffolding completes, the natural next step is a concept conversation that produces a `docs/ROADMAP.md`, followed by spec-kit initialization, constitution, and the spec-kit workflow (specify → clarify → plan → tasks → implement). Those steps are intentionally NOT part of this scaffolding prompt — they require project-specific context that emerges from the concept conversation.

## Notes

- The prompt fetches two URLs from this repository (`create-agent-instructions-file.md` and `common-tools.md`). Both Codex and Claude Code can fetch URLs directly. Updates to those source files automatically propagate to anyone using this scaffolding prompt.
- The interactive checkpoints (steps 4, 5, 6) are designed to be natural conversation pauses. In a live-broadcast or pair-programming context, they map cleanly to audience-question moments.
- The license question is only asked for public repositories. A private repository can add a license later if it is made public.
- The initial commit uses conventional commit format ("chore: initial project scaffolding") to match the convention established in agent instructions.
