---
name: pan
description: 'Extract signal from noise from a log, revising the distillation pass after pass until two passes in a row change nothing material. Manual only — invoke only if user explicitly runs /pan'
disable-model-invocation: true
---

Source: the file given as argument; otherwise the raw chat log
- Claude Code: JSONL at `~/.claude/projects/<project>/<session-id>.jsonl` — the session id is in your working/scratchpad path
- Codex CLI: JSONL under `${CODEX_HOME:-$HOME/.codex}/sessions/**/rollout-*.jsonl` — most recently modified, verified by its first line's `payload.cwd`
- Claude (Desktop/Web) or ChatGPT: the conversation as visible in context

Claude Code / Codex CLI: loop autonomously. Each pass, spawn a fresh subagent with exactly this prompt — add nothing:

- First pass: `Extract signal from noise in <source path>. Write it to <findings path>.`
- Later passes: `Extract signal from noise in <source path>. Revise <findings path>: add what's missing, correct what's wrong.`

The findings file lives in scratch. Never edit it yourself. Before each later pass, snapshot it (`findings.1.md`, `findings.2.md`, …). Stop once two passes in a row make no material change — new or corrected signal, not rewording — judged from the diff. Present the final findings file.

Claude (Desktop/Web) / ChatGPT: one pass per invocation, same instructions applied yourself to the distillation in context. Present it, then ask if the user wants another.
