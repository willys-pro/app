# Deriv Smart Trader Pro

AI-powered trading platform for [Deriv.com](https://deriv.com). Runs entirely in your browser — no server, no build step, single HTML file.

---

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "v2.0 release"
git branch -M main
git remote add origin https://github.com/<username>/deriv-smart-trader-pro.git
git push -u origin main
```

Then: **Settings → Pages → Source: main / root → Save**

Live at: `https://<username>.github.io/deriv-smart-trader-pro/`

---

## Login — New API Requirements (v2.0)

Deriv now requires a **Personal Access Token (PAT)** and a registered **App ID**.

### Step 1 — Get Your PAT Token
1. Log in at [app.deriv.com](https://app.deriv.com)
2. Go to **Account Settings → API Token**
3. Click **Create new token**
4. Required scopes: **Read + Trade + Payments**
5. Copy the token — it looks like: `pat_c0064658ba53335f34fc820ca5703cb9688048ab9342c8cb5631ef19c14550ee`

### Step 2 — Get Your App ID
1. Go to [app.deriv.com/developer-tools](https://app.deriv.com/developer-tools)
2. Register a new application or use an existing one
3. Copy your App ID — it looks like: `33tgVnJBf1AnlU1cAk2n9`

### Step 3 — Login
1. Paste your PAT token into the **API Token (PAT)** field
2. Paste your App ID into the **App ID** field
3. Click **Connect & Authenticate**

---

## DEMO / REAL Account Switching (v2.0)

After login, all linked accounts (DEMO and REAL) are automatically loaded from the Deriv API.

- The **account switcher** appears in the topbar next to your account ID
- Click your account ID to open the dropdown — all linked accounts are listed
- Each account shows its badge (**DEMO** amber or **REAL** red), login ID, and currency
- Click any account to switch instantly — the app re-authenticates and resets state cleanly
- The active account is highlighted with a cyan dot

> **Important:** Deriv returns tokens for linked accounts only when you use OAuth or when accounts share the same API token. If a linked account has no token in the list, you will need to log in separately with that account's own PAT token.

---

## Features

- Live WebSocket price feed (Deriv API v3) with auto-reconnect
- Synthetic Indices (24/7), Forex, Crypto, Baskets, Metals
- Rise/Fall and Higher/Lower contracts
- **Barrier offset control** — live constraints from `contracts_for` API, presets, absolute price display, +/− toggle, live payout proposal
- Charts: EMA 5/20, SMA 50, Bollinger Bands, MACD, Awesome Oscillator, RSI
- **1-minute candle panel** — live forming candle + last 5 closed candles, body%, PERFECT indicator
- **OHLC-based 12-indicator AI engine** (see table below)
- **Auto Trader** — 2-stage barrier-locked execution engine
- **Staking engine** — Fixed / Kelly Criterion / Martingale
- **Session risk manager** — loss limit, trade limit, consecutive loss limit, cooldown, equity curve
- **Signal strength meter** — always-visible confidence bar with rolling win rate
- **Pre-trade checklist** — 8-point pass/fail gate
- **DEMO/REAL badge** — automatic from Deriv API `is_virtual` flag
- Sound alerts, entry snapshots, WebSocket auto-reconnect, light/dark mode

---

## AI Signal Engine — 12 Indicators (OHLC-based)

| # | Indicator | Max Pts |
|---|---|---|
| 1 | EMA 5/20 cross/alignment | 25 |
| 2 | MACD line + histogram | 20 |
| 3 | Awesome Oscillator | 15 |
| 4 | RSI 14 | 15 |
| 5 | Stochastic (14,3) | 10 |
| 6 | BB Squeeze Breakout | 10 |
| 7 | ADX (14) trend strength | 10 |
| 8 | HTF Bias (EMA 20/50) | 8 |
| 9 | Price Trend (5-bar) | 7 |
| 10 | RSI/MACD Divergence | 15 |
| 11 | Candle Sequence (3-bar) | 20 |
| 12 | Tick Velocity | 5 |

**Max possible score: 155 pts.** Confidence = 60% absolute + 40% separation. Signal only if dominant ≥25pts AND separation ≥15pts.

---

## Auto Trader — Barrier-Locked 2-Stage Logic

| Barrier sign | Auto trades |
|---|---|
| `+` (above spot) | **LOWER only** |
| `−` (below spot) | **HIGHER only** |

**Stage 1 — ARM:** ≥80% confidence + 3 consecutive same-direction signals → amber pulse.

**Stage 2 — FIRE:** 100% confidence + perfect 1m candle + risk check passes → trade executes.

---

## Staking Modes

| Mode | Description |
|---|---|
| Fixed | Exact value from stake input |
| Kelly | 25% conservative Kelly fraction from rolling win rate + payout |
| Martingale | Doubles on loss, resets on win, hard cap at 4 levels |

---

## Full Change History

| Version | Change |
|---|---|
| v2.0 | **New Deriv API login** — PAT token + App ID required (old token format no longer works) |
| v2.0 | **DEMO/REAL account switcher** — topbar dropdown to switch between all linked accounts |
| v2.0 | WebSocket URL now built from user-supplied App ID |
| v2.0 | account_list fetched after auth — all linked accounts loaded automatically |
| v2.0 | Tab key on PAT field moves to App ID field; Enter on App ID submits |
| v2.0 | Clean state reset on account switch |
| v1.9 | RSI + MACD divergence detection with pivot analysis |
| v1.9 | Candle sequence analysis — 3 soldiers/crows, consecutive, reversal |
| v1.9 | Tick velocity — ticks/sec momentum proxy |
| v1.9 | Kelly Criterion + Martingale staking modes |
| v1.9 | Session profit target |
| v1.9 | Signal strength meter + rolling win rate |
| v1.9 | Pre-trade checklist (8 conditions) |
| v1.9 | DEMO/REAL badge from is_virtual flag |
| v1.8 | Sound engine, session risk manager, OHLC engine, 9-indicator AI, entry snapshots |
| v1.7 | Barrier-locked auto trader |
| v1.6 | 2-stage auto trader + 1m candle panel |
| v1.5 | Font clarity + light/dark mode |
| v1.4 | Compact layout + resizable sidebar |
| v1.3 | Barrier offset + live payout proposal |
| v1.2 | Bug fixes |

---

## Disclaimer

Educational and personal use only. Trading involves significant risk of loss. AI signals, the Auto Trader, and staking modes do not guarantee profit. Always test on a demo account first.

## License

MIT
