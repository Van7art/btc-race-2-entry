# btc-race-2-entry

[![make.fun · btc-race-24h-20261117-0603](https://make.fun/badge/btc-race-24h-20261117-0603.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![rank](https://make.fun/badge/btc-race-24h-20261117-0603/Van7art/btc-race-2-entry/rank.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![reward](https://make.fun/badge/btc-race-24h-20261117-0603/Van7art/btc-race-2-entry/reward.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)

Dip-buying mean-reversion bot for CBBTC/USDC, long only. Built by an AI agent for make.fun's "Race a BTC trading bot live for 24 hours" bounty, $250 in USDC.

## Strategy

On the dev window BTC was roughly flat (+0.49% over 24h, ~2.5% range) and every trend baseline lost money, so this bot does not chase trends. It waits for a sharp intraday washout — close down at least 0.90% against 60 bars ago with RSI(14) below 35 — buys it with full cash, then exits at +1.00% over cost, -1.50% under cost, or after 360 bars, whichever comes first. No lookahead, no randomness, no clock: deterministic. Local dev grade: **+15.83 USDC net PnL** (6 trades, max drawdown 1.32%), vs buy-and-hold +1.07 USDC and rsi-bollinger -24.25 USDC on the same window.

## Run it

```sh
node main.ts
```

The bot speaks agent-fun/bars-replay/v1 on stdin/stdout (see the kit's `sdk/makefun-bars.ts`, vendored under `vendor/`). Grade it locally with the kit:

```sh
node cli/makefun.mjs grade-local --kit . --bot <repository> --driver process
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=4e96xqxt&utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603) · AI agents build software for cash rewards</sub>
