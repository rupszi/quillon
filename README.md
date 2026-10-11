# Quillon

**A coding agent you can audit.** Terminal-first, runs on open-weight models, and every tool call passes a permission gate and lands in a log.

> **Status: early development.** Quillon is being built in public, one milestone a week, from October to November 2026. It does not do anything useful yet. Follow along in [ROADMAP.md](ROADMAP.md).

A quillon is the crossguard of a sword: the part that protects the hand holding the blade.

## Why

Every coding tool now ships an agent. Few of them answer the first question a bank, an insurer or any careful team asks: **what did the agent do, and who allowed it?**

Quillon is built around that question:

- **Nothing happens without permission.** File writes, shell commands and network calls go through a policy gate: allow, ask or deny, per tool and per path.
- **Changes are diffs you approve.** The agent proposes a change, you see it, you say yes. Every applied change has a git checkpoint and can be undone.
- **Everything is logged.** Each tool call, the decision made about it and its result go into a JSON audit log you can replay.
- **Your models, your machine.** Ollama by default, any OpenAI-compatible API if you choose. No telemetry.

## Planned features

| Feature | Milestone | Status |
|---|---|---|
| CLI chat with streaming, Ollama client | Week 1 · v0.1.1 | In progress |
| Typed tool registry and agent loop | Week 2 · v0.1.2 | Planned |
| Edits as diffs, approval, `/undo` | Week 3 · v0.1.3 | Planned |
| Skills (SKILL.md folders loaded on demand) | Week 4 · v0.1.4 | Planned |
| Policy engine, sandboxed shell, audit log | Week 5 · v0.1.5 | Planned |
| Evaluation on 10 real tasks, first usable release | Week 6 · v0.2.0 | Planned |

## Install

Not ready for use yet. Once v0.2.0 ships:

```bash
pip install quillon      # or: uv tool install quillon
quillon
```

## Development

```bash
git clone https://github.com/rupszi/quillon.git
cd quillon
uv sync
uv run quillon
```

Design decisions and the reasoning behind them are in [DECISIONS.md](DECISIONS.md).

## How AI is used in this project

The core (agent loop, tool registry, diff handling, policy engine) is written by hand. AI assistants are used for code review, explanations and suggesting test cases, not to generate whole modules.

## License

[Apache-2.0](LICENSE)