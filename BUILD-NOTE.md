# Build note — btc-race-24h-20261117-0603

Built 2026-11-17 ~15:00 WITA (competition opened 2026-11-17T06:03:00Z, entries close 2026-11-17 12:03 UTC = 20:03 WITA).

## Kit
- Kit dir: `~/workspace/makefun/btc-race-2-kit/btc-race-24h-20261117-0603-kit/` (downloaded from https://make.fun/c/btc-race-24h-20261117-0603/kit, bundle sha256 71ab12f0…)
- RULES.txt + competition.yaml read in full. Free entry ($0), harness bars-replay/v1, NOT a Claude Code/Codex-only harness.

## Entry
- Dir: `~/workspace/makefun/btc-race-2-entry/` — main.ts, vendor/makefun-bars.ts (byte-identical copy of kit SDK), LICENSE (MIT), README.md
- Strategy: dip-buying mean reversion, ported from the previous race's proven entry (which graded +14.26 USDC on its window) and retuned on THIS dev window: entry when close is down ≥0.90% vs 60 bars ago AND RSI(14) < 35; exit at +1.00% TP / -1.50% SL / 360-bar time stop; full cash, long only.
- TypeScript, not Python: the kit's local grader on this machine runs Node only — `grade-local` refuses Python ("python3.13 runs only inside Docker", no Docker here). The server grades Python fine, but TS is verifiable locally with the kit's own command, so TS was chosen.

## Local dev grade (kit grade-local --driver process, run twice)
- Net PnL: **+15.827934 USDC** (gate: > $0 — PASSES with margin)
- Trades: 6 (3 round trips, win rate 66.7%), fees 2.429151 USDC, rejected orders 0
- Max drawdown: 1.32% (guardrail: ≤ 25% — passes)
- Return: +1.58%, Sharpe 0.023, net PnL at 2x fees: +13.40 USDC (still positive)
- Determinism: L1 reproduced = true on both runs; action_log_sha256 identical across two independent grade-local runs: `5107f529fc589b44fad26d00622f38b909eacd7b0b435c10350efdd5c7381753`
- result_sha256: `0f371d89ad8a489eae9cc4265da809eb211f13d4a0d3bd68d2a3d383f6c4b3d2`
- Only mismatch vs server: local Node v24.22.1 vs server harness Node v26.13.1 (same note as the previous entry's grade; code uses erasable TS only)
- Baselines on the same dev window for comparison: buy-and-hold +1.07, momentum +2.45, rsi-bollinger -24.25, ema-cross -106.21 USDC. The old entry's params (dip 1.50%/30 bars, TP +0.50%) graded +5.09 USDC here; the new params (+15.83) sit mid-plateau — neighbours dip 0.70–1.10% × TP 0.80–1.20% all grade +15 to +24 USDC, so not a knife-edge fit.

## What Ovan still needs to do (NOT done by this build)
1. Create a NEW public GitHub repo AFTER the competition opened (2026-11-17T06:03:00Z) — e.g. `Van7art/btc-race-2-entry` — and install the GitHub App. Baby cannot create repos via the connector.
2. If the repo name differs from `btc-race-2-entry`, fix the owner/repo in the rank/reward badge URLs in README.md (the competition badge needs no owner).
3. Set the repo About (description + homepage https://make.fun/bounty/btc-race-24h-20261117-0603 + topics makefun, ai-agents, bounties, trading) before submitting.
4. Push this entry dir, bundle transcripts, run `check`, then submit before 20:03 WITA today. Do NOT submit a bundle from a session that started before the competition opened.

## Not done (per task)
- No push to GitHub, no repo created, no transcript bundle, no submission.
