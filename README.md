# kensho-sweep-mcp — Japan X/Twitter Sweepstakes MCP Server

Read-only MCP server exposing the kensho Japan X/Twitter sweepstakes dataset collected from knshow.com, kenshou.club, ken-kaku.com, and cp.meikan.org.

## Tools

| Tool | Description |
|---|---|
| `current_sweep(keyword)` | Latest sweep matching keyword (prize, brand, URL substring) |
| `sweep_history(keyword, limit=50)` | Price time series (oldest first) |
| `top_prize_movers(direction=None, limit=10)` | Biggest `|delta JPY|` prize value movers, optional up/down filter |

## Data

- Source: `data/accumulated.jsonl` (1133 observations, snapshot 2026-09-27)
- Sources: knshow.com, kenshou.club, ken-kaku.com, cp.meikan.org
- No network, no API key, no account required

## Installation (Smithery)

Install via Smithery registry:
```bash
smithery install @atushi1841/kensho-sweep-mcp
```

## More MCP Servers

- **[kensho-kaku](https://github.com/atushi1841/kensho-kaku)** — Sweepstakes from ken-kaku.com
- **[kensho-kclub](https://github.com/atushi1841/kensho-kclub)** — Sweepstakes from kenshou.club
- **[kensho-kema](https://github.com/atushi1841/kensho-kema)** — Sweepstakes from ke-ma.net
- **[japan-anime-figure-mcp](https://github.com/atushi1841/japan-anime-figure-mcp)** — Anime figure price comparison
- **[tcg-price-japan](https://github.com/atushi1841/tcg-price-japan)** — TCG used-price trends

## Apify Actors

- **[Apify Store: kensho-sweep-mcp](https://apify.com/atushi1841/acts/kensho-sweep-mcp)** — Parent sweepstakes dataset (main)
- **[Apify Store: japan-anime-figure-price-data](https://apify.com/atushi1841/acts/japan-anime-figure-price-data)** — Anime figure prices

## Run

```bash
python server/server.py          # stdio MCP transport
python server/server.py --http   # streamable-http at /mcp
```

Requires `fastmcp>=3.0.0` (see `requirements.txt`).

## MCP Bundle

`manifest.json` follows the MCPB v0.4 spec. Pack with:

```bash
npx -y @anthropic-ai/mcpb pack . dist/kensho-sweep-mcp.mcpb
```