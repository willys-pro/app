# Deriv Smart Trader Pro

AI-powered trading platform for [Deriv.com](https://deriv.com). Runs entirely in your browser — no server, no build step, single HTML file.

---

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "v3.0 release"
git branch -M main
git remote add origin https://github.com/<username>/deriv-smart-trader-pro.git
git push -u origin main
```

Then: **Settings → Pages → Source: main / root → Save**

Live at: `https://<username>.github.io/deriv-smart-trader-pro/`

---

## Login — New API (v3.0)

Deriv has updated its API. Login now uses the new `developers.deriv.com` portal.

### Step 1 — Register Your App

1. Go to [developers.deriv.com](https://developers.deriv.com)
2. Log in and go to **Dashboard**
3. Click **Register a new application**
4. Choose type: **PAT** (for personal/desktop use)
5. Copy your **App ID** — it looks like: `33twueeulu2pNK1RhIYVz`

### Step 2 — Create a PAT Token

1. In the same Dashboard, go to **API Tokens**
2. Click **Create new token**
3. Select scopes: **trade** + **account_manage**
4. Copy your token

### Step 3 — Login

1. Paste your PAT token into the **PAT Token** field
2. Paste your App ID into the **App ID** field
3. Click **Connect & Authenticate**
4. If you have multiple accounts, select one from the dropdown
5. Click **Connect Selected Account**

---

## How It Works (New API Flow)

```
1. REST GET  /trading/v1/options/accounts          → get your account list
2. REST POST /trading/v1/options/accounts/{id}/otp → get authenticated WebSocket URL
3. WebSocket connect to the OTP URL               → live trading socket (no authorize needed)
```

---

## Features

- Live WebSocket price feed (Deriv API v3) with auto-reconnect
- Synthetic Indices (24/7), Forex, Crypto, Baskets, Metals
- Rise/Fall and Higher/Lower contracts
- **Barrier offset control** — live constraints from `contracts_for` API, presets, absolute price display, +/− toggle, live payout proposal
- Charts: EMA 5/20, SMA 50, Bollinger Bands, MACD, Awesome Oscillator, RSI
- **1-minute candle panel** — live forming candle + last 5 closed candles, body%, PERFECT indicator
- **OHLC-based 12-indicator AI engine**
- **Auto Trader** — 2-stage barrier-locked execution engine
- **Staking engine** — Fixed / Kelly Criterion / Martingale
- **Session risk manager** — loss limit, trade limit, consecutive loss limit, cooldown, equity curve
- **Signal strength meter** — always-visible confidence bar with rolling win rate
- **Pre-trade checklist** — 8-point pass/fail gate
- **DEMO/REAL badge** — automatic from account type
- Sound alerts, entry snapshots, WebSocket auto-reconnect, light/dark mode

---

## Disclaimer

Educational and personal use only. Trading involves significant risk of loss.

## License

MIT
