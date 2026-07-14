---
name: glean
description: 'Extract signal from noise from a log, looping until two passes in a row find nothing new. Manual only — invoke only if user explicitly runs /glean'
disable-model-invocation: true
---

Read the whole chat log — pull the raw transcript from disk when your tool provides one; otherwise work from the full conversation as it appears in context

- Claude Code: JSONL at `~/.claude/projects/<project>/<session-id>.jsonl` — the session id is in your working/scratchpad path
- Codex CLI: JSONL under `${CODEX_HOME:-$HOME/.codex}/sessions/**/rollout-*.jsonl`. No session id is given — use the most recently modified file, verified by its first line's `payload.cwd`
- Claude (Desktop/Web) or ChatGPT: no local raw transcript exists — read the conversation as currently visible in context

Task: extract signal from noise

Loop: each pass, find signal not yet found. Stop if two passes in a row find nothing new
