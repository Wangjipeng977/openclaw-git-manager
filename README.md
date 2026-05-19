# git-watcher

[中文版](./README_zh.md)

**Git Version Control for OpenClaw Configuration Files.**

📦 Install: `clawhub install git-watcher`
📂 GitHub: `https://github.com/Wangjipeng977/openclaw-git-manager`

---

## One-Liner

Every config change is automatically tracked with diff — rollback to any previous version with one command. No more "I have no idea what broke."

---

## Problem It Solves

You changed something in OpenClaw, a week later a feature stops working and you:
- Can't remember what you changed
- Can't remember when you changed it
- Have to trial-and-error everything

This skill puts your `openclaw.json`, `credentials/`, `agents/` and other config files under git version control. Every change is logged, comparable, and reversible.

---

## Core Commands

| Command | What It Does |
|---------|-------------|
| `commit` | One-shot commit of current config state, auto-generates key-level diff summary |
| `log` | View history — each entry shows "which files, what changed" |
| `diff` | Compare any two versions |
| `restore <hash>` | Rollback to specified version with auto-validation + restart hints |
| `undo` | Undo the last restore operation |

---

## Safety Guarantees

- **Credentials auto-redacted**: Real API keys never enter git commits — they show as `[REDACTED-api-key]`
- **Sensitive files excluded**: Logs, media, and memory files are never tracked
- **Full audit trail**: `.secrets-log.json` records every redact with timestamp, file, and type

---

## Usage Examples

```
# First time setup
python3 git_manager.py init

# After any config change
python3 git_manager.py commit
# → Auto-shows diff summary like:
#   ~agent:main:dashboard.estimatedCostUsd: 0.066 → 0.005

# Something broke? Rollback
python3 git_manager.py log          # find a working version
python3 git_manager.py restore a1b2c3d  # rollback
# → Auto-runs openclaw gateway doctor to validate, tells you next steps
```

---

## Install

```bash
# Via clawhub (recommended)
clawhub install git-watcher

# Or manual
cp -r openclaw-git-manager/ ~/.openclaw/workspace/skills/
```

Trigger phrases: `commit the config` / `save this version` / `what changed` / `restore` / `rollback` / `git manager` / `git-watcher`

---

MIT License · Author: wangjipeng
