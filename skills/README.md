# Skills

Installable skills shared by Frontier Tech, compatible with both Codex and Claude Code.

The skill format (`SKILL.md` with frontmatter plus optional `references/`) works for both agents. Only the install location differs.

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

## Install With Claude Code

Ask Claude Code, replacing `<skill-name>` with one of the available skill folder names above:

```text
Install the <skill-name> skill from:
https://github.com/madiver/FrontierTech/tree/main/skills/<skill-name>
```

Restart Claude Code after installation so the skill is picked up.

## Manual Install

Choose the install path that matches your agent.

| Agent | Skill directory |
| --- | --- |
| Codex | `~/.codex/skills/` |
| Claude Code | `~/.claude/skills/` |

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

For Claude Code:

```bash
mkdir -p ~/.claude/skills
git clone --depth 1 https://github.com/madiver/FrontierTech /tmp/frontiertech
cp -R "/tmp/frontiertech/skills/$SKILL_NAME" ~/.claude/skills/
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

For Claude Code:

```bash
SKILL_NAME=meeting-briefings
mkdir -p ~/.claude/skills && \
curl -L https://github.com/madiver/FrontierTech/archive/refs/heads/main.tar.gz | \
tar -xz -C /tmp && \
cp -R "/tmp/FrontierTech-main/skills/$SKILL_NAME" ~/.claude/skills/
```

Restart your agent after installation.

## Notes On Compatibility

- The `SKILL.md` frontmatter (`name`, `description`) is the standard format both agents read.
- The `references/` subdirectory is supported by both agents.
- The `agents/openai.yaml` file is Codex-specific. Claude Code ignores it.
