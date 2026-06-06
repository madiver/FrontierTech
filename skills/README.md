# Skills

Installable skills shared by Frontier Tech, compatible with Codex and Claude-style skill runtimes.

The skill format (`SKILL.md` with frontmatter plus optional `references/`) is portable, but each agent manages installed skills differently. Follow the install/update path for the agent you are using.

## Available Skills

- [crypto-algo-quant](crypto-algo-quant/SKILL.md) - quantitative research and execution-aware system design for crypto intraday and day-trading data.
- [meeting-briefings](meeting-briefings/SKILL.md) - short pre-meeting briefings for the day's calendar, gathering attendee context from notes, messages, and LinkedIn.

## Install With Codex

Ask Codex, replacing `<skill-name>` with one of the available skill folder names above:

```text
Install the <skill-name> skill from:
https://github.com/madiver/FrontierTech/tree/main/skills/<skill-name>
```

Restart Codex after installation so the skill is picked up.

## Install With Claude

Claude sessions may expose installed skills as a read-only cache, so asking Claude to copy files from chat may not update saved skills. Install or update skills through **Settings -> Capabilities** using the GitHub skill folder URL, replacing `<skill-name>` with one of the available skill folder names above:

```text
https://github.com/madiver/FrontierTech/tree/main/skills/<skill-name>
```

If the skill is already listed in the current session's available skills, it is already active for that session. If the GitHub version is newer, update or replace it through Settings -> Capabilities, then restart the session if the app asks you to.

## Manual Install

Choose the install path that matches your agent. For Claude, prefer Settings -> Capabilities unless your specific Claude environment documents filesystem-based skill installs.

| Agent | Skill directory |
| --- | --- |
| Codex | `~/.codex/skills/` |
| Claude | Manage through Settings -> Capabilities; local paths may be read-only cache |

Set the skill you want to install:

```bash
SKILL_NAME=meeting-briefings
```

For Codex:

```bash
mkdir -p ~/.codex/skills
git clone --depth 1 https://github.com/madiver/FrontierTech /tmp/frontiertech
cp -R "/tmp/frontiertech/skills/$SKILL_NAME" ~/.codex/skills/
```

Restart your agent after copying the skill.

## One-Line Install

For Codex:

```bash
SKILL_NAME=meeting-briefings
mkdir -p ~/.codex/skills && \
curl -L https://github.com/madiver/FrontierTech/archive/refs/heads/main.tar.gz | \
tar -xz -C /tmp && \
cp -R "/tmp/FrontierTech-main/skills/$SKILL_NAME" ~/.codex/skills/
```

Restart your agent after installation.

## Notes On Compatibility

- The `SKILL.md` frontmatter (`name`, `description`) is the portable skill metadata.
- The `references/` subdirectory travels with the skill and should be installed with it.
- The `agents/openai.yaml` file is Codex-specific. Other agents can ignore it.
