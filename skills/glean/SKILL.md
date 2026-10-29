---
name: glean
description: 'Extract signal from noise from a log, looping until two passes in a row find nothing new. Manual only — invoke only if user explicitly runs /glean'
disable-model-invocation: true
---

Source: the file given as argument; otherwise the raw chat log
- Claude Code: JSONL at `~/.claude/projects/<project>/<session-id>.jsonl` — the session id is in your working/scratchpad path
- Codex CLI: JSONL under `${CODEX_HOME:-$HOME/.codex}/sessions/**/rollout-*.jsonl` — most recently modified, verified by its first line's `payload.cwd`
- Claude (Desktop/Web) or ChatGPT: the conversation as visible in context

Claude Code / Codex CLI: loop autonomously. Each pass, spawn a fresh subagent with exactly this prompt — add nothing:

- First pass: `Extract signal from noise in <source path>.`
- Later passes: `Extract signal from noise in <source path>. Already captured: <findings path>. Capture only signal not already there.`

Append each reply to a scratch findings file verbatim. Stop once two passes in a row add nothing. Present the findings file.

Claude (Desktop/Web) / ChatGPT: one pass per invocation, same instruction applied yourself. Present it, then ask if the user wants another.
