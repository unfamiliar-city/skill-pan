---
name: pan
description: 'Extract signal from noise from a log, revising the distillation pass after pass until two passes in a row change nothing material. Manual only — invoke only if user explicitly runs /pan'
disable-model-invocation: true
---

Source: the given file; otherwise the raw chat log
- Claude Code: JSONL at `~/.claude/projects/<project>/<session-id>.jsonl` — the session id is in your working/scratchpad path
- Codex CLI: JSONL under `${CODEX_HOME:-$HOME/.codex}/sessions/**/rollout-*.jsonl` — most recently modified, verified by its first line's `payload.cwd`
- Claude (Desktop/Web) or ChatGPT: the conversation as visible in context

Claude Code / Codex CLI: run each prompt in a fresh subagent, exactly as written — add nothing. `<scratch>` is your scratch directory, as an absolute path.

1. Audit — given file only, if the user agrees: `Source: <source path>. Audit source for clarity. Propose amendments with evidence. Ask what needs clarification. Write it to <scratch>/audit.md.`
   Show the user each amendment with its evidence, and the questions; wait. Apply only what they agree to a copy, `<scratch>/source.md`, keeping line numbers; log changes in `<scratch>/amendments.md`. That copy is `<source path>` from here on.
2. First pass: `Extract signal from noise in <source path>. Write it to <scratch>/notes.md. Be ultra concise without losing meaning.`
3. Later passes: `Extract signal from noise in <source path>. Revise <scratch>/notes.md: add what's missing, correct what's wrong. Be ultra concise without losing meaning.`
   Snapshot `notes.md` before each (`notes.1.md`, …); never edit it yourself. Stop once two passes in a row make no material change — new or corrected signal, not rewording — judged from the diff. Present the final `notes.md`.

Claude (Desktop/Web) / ChatGPT: do these steps yourself, one pass per invocation. Present the notes, then ask if the user wants another.
