# pan

A lightweight micro-skill to pan chat logs and transcripts for signal.

Pass after pass, it adds what was missed and corrects what was wrong, until two passes in a row change nothing — washing away the noise until only the gold is left.

## Install

### Claude (Desktop/Web)

Customize → Plugins → Add marketplace → Add from a repository → `unfamiliar-city/marketplace` → Sync → Install `pan`

### ChatGPT

No repo-based install exists. Skills → Create → Create with chat → paste the contents of [`skills/pan/SKILL.md`](skills/pan/SKILL.md) → Install

### Claude Code / Codex CLI

Via the [unfamiliar-city marketplace](https://github.com/unfamiliar-city/marketplace):

```
/plugin marketplace add unfamiliar-city/marketplace
/reload-plugins
/plugin install pan
```

## Use

```
> /pan                 # pans this session's chat log
> /pan transcript.md   # pans a file
```

Manual only — runs when you invoke `/pan`. 

## Supported tools

- **Claude** (Desktop/Web) — works with conversation as currently visible in context
- **ChatGPT** (Desktop/Web) — works with conversation as currently visible in context
- **Claude Code** — reads whole raw session transcript from local disk
- **Codex CLI** — reads whole raw session transcript from local disk

## License

MIT
