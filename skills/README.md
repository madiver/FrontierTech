# Skills

Installable skills shared by Frontier Tech, compatible with both Codex and Claude Code.

The skill format (`SKILL.md` with frontmatter plus optional `references/`) works for both agents. Only the install location differs.

## Available Skills

- [crypto-algo-quant](crypto-algo-quant/SKILL.md) - quantitative research and execution-aware system design for crypto intraday and day-trading data.

## Install With Codex

Ask Codex:

```text
Install the crypto-algo-quant skill from:
https://github.com/madiver/FrontierTech/tree/main/skills/crypto-algo-quant
```

Restart Codex after installation so the skill is picked up.

## Install With Claude Code

Ask Claude Code:

```text
Install the crypto-algo-quant skill from:
https://github.com/madiver/FrontierTech/tree/main/skills/crypto-algo-quant
```

Restart Claude Code after installation so the skill is picked up.

## Manual Install

Choose the install path that matches your agent.

| Agent | Skill directory |
| --- | --- |
| Codex | `~/.codex/skills/` |
| Claude Code | `~/.claude/skills/` |

For Codex:

```bash
mkdir -p ~/.codex/skills
git clone --depth 1 https://github.com/madiver/FrontierTech /tmp/frontiertech
cp -R /tmp/frontiertech/skills/crypto-algo-quant ~/.codex/skills/
```

For Claude Code:

```bash
mkdir -p ~/.claude/skills
git clone --depth 1 https://github.com/madiver/FrontierTech /tmp/frontiertech
cp -R /tmp/frontiertech/skills/crypto-algo-quant ~/.claude/skills/
```

Restart your agent after copying the skill.

## One-Line Install

For Codex:

```bash
mkdir -p ~/.codex/skills && \
curl -L https://github.com/madiver/FrontierTech/archive/refs/heads/main.tar.gz | \
tar -xz -C /tmp && \
cp -R /tmp/FrontierTech-main/skills/crypto-algo-quant ~/.codex/skills/
```

For Claude Code:

```bash
mkdir -p ~/.claude/skills && \
curl -L https://github.com/madiver/FrontierTech/archive/refs/heads/main.tar.gz | \
tar -xz -C /tmp && \
cp -R /tmp/FrontierTech-main/skills/crypto-algo-quant ~/.claude/skills/
```

Restart your agent after installation.

## Notes On Compatibility

- The `SKILL.md` frontmatter (`name`, `description`) is the standard format both agents read.
- The `references/` subdirectory is supported by both agents.
- The `agents/openai.yaml` file is Codex-specific. Claude Code ignores it.
