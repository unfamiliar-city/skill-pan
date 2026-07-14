# glean

A lightweight micro-skill to iteratively extract signal from noise in chat logs.

Iteratively loops as if panning for gold. Pass after pass, stopping only once two passes in a row come up empty.

## Install

Via the [unfamiliar-city marketplace](https://github.com/unfamiliar-city/marketplace):

```
/plugin marketplace add unfamiliar-city/marketplace
/reload-plugins
/plugin install glean
```

## Use

```
> /glean
```

Manual only — runs when you invoke `/glean`. 

## Supported tools

- **Claude** (Desktop/Web) — works with conversation as currently visible in context
- **ChatGPT** (Desktop/Web) — works with conversation as currently visible in context
- **Claude Code** — reads whole raw session transcript from local disk
- **Codex CLI** — reads whole raw session transcript from local disk

## License

MIT
