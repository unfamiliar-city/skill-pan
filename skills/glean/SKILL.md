---
name: glean
description: 'Extract signal from noise from a log, looping until two passes in a row find nothing new. Manual only — invoke only if user explicitly runs /glean'
disable-model-invocation: true
---

Read the whole chat log – pull the raw transcript from disk if your tool provides one; otherwise work from the full conversation in context

- Claude Code: JSONL at `~/.claude/projects/<project>/<session-id>.jsonl` — the session id is in your working/scratchpad path
- Codex CLI: JSONL under `${CODEX_HOME:-$HOME/.codex}/sessions/**/rollout-*.jsonl`. No session id is given — use the most recently modified file, verified by its first line's `payload.cwd`
- Claude (Desktop/Web) or ChatGPT: no local raw transcript exists — read the conversation as currently visible in context

Task: extract signal from noise

Loop: each pass, find signal not yet found. Stop once two passes in a row find nothing new.

- Claude Code / Codex CLI: loop autonomously within this invocation, no need to check in with the user between passes. Each pass, spawn a fresh subagent with the transcript plus the findings-so-far; it returns only what's new. Append that to a scratch findings file yourself, then start the next pass. Present the accumulated findings once the loop stops.
- Claude (Desktop/Web) / ChatGPT: one pass per invocation. Present the pass, then ask the user if they want another; stop there either way.
