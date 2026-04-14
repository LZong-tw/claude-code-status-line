# ccstatusline Integration

Cache token metrics as [ccstatusline](https://github.com/sirmalloc/ccstatusline) Custom Command widgets.

These scripts extract the same cache metrics from session JSONL files that `statusline.sh` does, but split into individual widgets for use with ccstatusline's Custom Command feature.

## Widgets

| Script | Label | What it shows |
|--------|-------|---------------|
| `cache-read.sh` | `ReadCache: 18.9M (91%)` | Cumulative `cache_read_input_tokens` + hit rate % |
| `cache-creation.sh` | `CacheCreate: 2.0M` | Cumulative `cache_creation_input_tokens` |
| `cache-input.sh` | `Uncached: 234` | Cumulative `input_tokens` (full-price, no cache) |

## Setup

1. Copy scripts to `~/.claude/`:

```sh
cp ccstatusline/cache-*.sh ~/.claude/
chmod +x ~/.claude/cache-*.sh
```

2. In ccstatusline TUI, add three **Custom Command** widgets with these paths:

```
~/.claude/cache-read.sh
~/.claude/cache-creation.sh
~/.claude/cache-input.sh
```

## Requirements

- `jq` — JSON processor
- `awk` — text processing (pre-installed on macOS/Linux)

## Powerline note

If you use 4+ status lines with Powerline enabled, ccstatusline's TUI only configures `startCaps`/`endCaps` for the first 3 lines. Manually add entries to `~/.config/ccstatusline/settings.json`:

```json
"startCaps": ["...", "...", "...", "..."],
"endCaps": ["...", "...", "...", "..."]
```

See [sirmalloc/ccstatusline#305](https://github.com/sirmalloc/ccstatusline/issues/305).
