# NVIDIA Ecosystem Tracker

A single-file dashboard that monitors NVIDIA's key suppliers, partners, and direct
investments — IP, foundry, memory, packaging, equipment, networking, server OEMs,
power, and direct investments — in one Bloomberg-terminal-meets-Robinhood view.

**Live data:** [Finnhub](https://finnhub.io) (quotes, fundamentals, news, earnings).
**Charts:** embedded TradingView widgets (1D / 1W / 1M / 1Y / 5Y).
No build step, no backend, no database — everything runs client-side with an
in-memory cache and a rate-limited request queue (~54 calls/min, under the
free tier's 60/min limit).

## Features

- **KPI bar** — NVDA price, total ecosystem market cap, companies reporting in 7 days, avg daily move
- **Ecosystem grid** — 33 tickers across 10 categories; price, daily %, market cap, P/E, YTD %, 1Y %
- **Detail view** — interactive price chart, key fundamentals, supply-chain role, recent news
- **News feed** — aggregated headlines across all tickers, filterable by category or company
- **Earnings calendar** — next ~45 days, next-7-days rows highlighted

## Use

Open `index.html` in a browser (or visit the GitHub Pages URL). Enter a free
Finnhub API key on the gate screen and hit **Load**. The key is held in memory
for the session only.

## Deploy to GitHub Pages

```bash
git init
git add index.html README.md
git commit -m "Add NVIDIA Ecosystem Tracker"
git branch -M main
git remote add origin https://github.com/sunnypately/nvidia-ecosystem-tracker.git
git push -u origin main
```

Then in the repo: **Settings → Pages → Source: `main` / root**.
Live at `https://sunnypately.github.io/nvidia-ecosystem-tracker/`.

## Notes

- Fundamentals (YTD, 1Y, P/E) come from Finnhub `stock/metric`, sidestepping the
  now-premium candle endpoint. Fields show `—` when Finnhub returns no value.
- `calendar/earnings` may be plan-gated on some free keys; the Earnings tab
  degrades gracefully if so.
- Not investment advice.
