# Roadmap

One milestone a week. Each ends in a working build, a tagged release on PyPI and a short write-up.

**First usable release: v0.2.0, week of 16–22 November 2026.**

## Definition of done for v0.2.0

- `pip install quillon` works, and `quillon` opens a chat in any git repo
- The agent can read files, propose a change as a diff, apply it after a yes, and run the tests
- Skills load from a folder (SKILL.md plus scripts) only when relevant
- No write, shell command or network call happens without passing the permission gate
- Every tool call is in a JSON audit log that can be replayed
- CI is green: ruff, pyright strict, pytest with at least 85% coverage
- README with a demo GIF and honest results on 10 real tasks

## Milestones

### Week 1 · 12–18 Oct · v0.1.1 — Skeleton and first chat

- [x] Reserve the name on PyPI
- [x] Release workflow with PyPI trusted publishing
- [ ] CI workflow: ruff, pyright strict, pytest with coverage
- [ ] Pre-commit hooks, including gitleaks
- [ ] Typer CLI entry point
- [ ] `LLMClient` protocol and an Ollama implementation with streaming
- [ ] REPL with history, `/help`, `/model`, `/exit`

### Week 2 · 19–25 Oct · v0.1.2 — Tools and the agent loop

- [ ] Tool registry: typed functions with Pydantic input schemas
- [ ] Read-only tools: `read_file`, `list_dir`, `grep`, `run_tests`
- [ ] Agent loop with a step limit, a token budget and clear stop reasons
- [ ] `FakeLLM` that replays scripted responses, so the loop is tested offline
- [ ] Compare 2–3 local models on tool calling; pick the default on evidence

### Week 3 · 26 Oct–1 Nov · v0.1.3 — Writing code

- [ ] `edit_file` proposes a unified diff instead of overwriting
- [ ] Diff preview in the terminal; apply only after the user says yes
- [ ] Git checkpoint before every apply; `/undo` rolls back the last change
- [ ] Tests for diff application, including conflicting and stale edits

### Week 4 · 2–8 Nov · v0.1.4 — Skills

- [ ] Skill format: a folder with SKILL.md (YAML front matter) and optional scripts
- [ ] Discovery from `~/.quillon/skills` and the repo's `.quillon/skills`
- [ ] Only names and descriptions go in the prompt; a skill's body loads on request
- [ ] Two reference skills: `python-tests` and `git-commit`

### Week 5 · 9–15 Nov · v0.1.5 — The safety layer

- [ ] Policy file: allow, ask or deny per tool and per path glob
- [ ] Shell runner with a timeout, a fixed working directory, a scrubbed environment and no network by default
- [ ] Lethal-trifecta check: refuse a session that combines private data, untrusted input and an outbound channel
- [ ] Secret redaction on everything sent to the model and written to logs
- [ ] JSON audit log of every tool call; `quillon audit` replays a session

### Week 6 · 16–22 Nov · v0.2.0 — Evaluation and first usable release

- [ ] Ten real tasks on a small sample repo; record pass rate, steps and time per task
- [ ] README with a demo GIF, the results table and known limits
- [ ] SECURITY.md stating what the sandbox does and does not protect against
- [ ] Release v0.2.0

## Not before v0.2.0

Parked on purpose, to keep scope small: a web UI, multi-agent orchestration, MCP support, container or bubblewrap sandboxing, Windows support, hosted models as the default.