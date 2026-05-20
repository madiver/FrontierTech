# Skills

Installable Codex skills shared by Frontier Tech.

## Available Skills

- [crypto-algo-quant](crypto-algo-quant/SKILL.md) - quantitative research and execution-aware system design for crypto intraday and day-trading data.

## Install With Codex

Ask Codex:

```text
Install the crypto-algo-quant skill from:
https://github.com/madiver/FrontierTech/tree/main/skills/crypto-algo-quant
```

Restart Codex after installation so the skill is picked up.

## Manual Install

```bash
mkdir -p ~/.codex/skills
git clone --depth 1 https://github.com/madiver/FrontierTech /tmp/frontiertech
cp -R /tmp/frontiertech/skills/crypto-algo-quant ~/.codex/skills/
```

Restart Codex after copying the skill.

## One-Line Install

```bash
mkdir -p ~/.codex/skills && \
curl -L https://github.com/madiver/FrontierTech/archive/refs/heads/main.tar.gz | \
tar -xz -C /tmp && \
cp -R /tmp/FrontierTech-main/skills/crypto-algo-quant ~/.codex/skills/
```

Restart Codex after installation.
