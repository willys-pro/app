# Quick Setup — Deriv Smart Trader Pro v2.0

## 1. Get Your PAT Token (NEW)

Old API tokens no longer work. You need a **Personal Access Token (PAT)**.

1. Go to https://app.deriv.com/account/api-token
2. Click **Create new token**
3. Select scopes: **Read + Trade + Payments**
4. Copy the token — it looks like:
   `pat_c0064658ba53335f34fc820ca5703cb9688048ab9342c8cb5631ef19c14550ee`

---

## 2. Get Your App ID (NEW)

1. Go to https://app.deriv.com/developer-tools
2. Register a new app or use an existing one
3. Copy your App ID — it looks like: `33tgVnJBf1AnlU1cAk2n9`

---

## 3. Push to GitHub

```bash
git init && git add . && git commit -m "v2.0 release" && git branch -M main
git remote add origin https://github.com/<user>/deriv-smart-trader-pro.git
git push -u origin main
```

---

## 4. Enable GitHub Pages

Settings → Pages → Source: **main / root** → Save

URL: `https://<user>.github.io/deriv-smart-trader-pro/`

---

## 5. Login

The login screen now has two fields:

| Field | What to enter |
|---|---|
| **API Token (PAT)** | Your PAT token starting with `pat_` |
| **App ID** | Your registered App ID (alphanumeric) |

- Press **Tab** after entering the PAT token to move to App ID
- Press **Enter** in the App ID field to submit, or click **Connect & Authenticate**

---

## 6. Switching DEMO / REAL Accounts

After login, all linked accounts load automatically.

1. Click your **account ID** in the topbar (next to the connection dot)
2. A dropdown shows all linked accounts with DEMO/REAL badges
3. Click any account to switch — the app re-authenticates and resets state
4. The current active account shows a cyan dot ●

**Note:** Account tokens are provided by the Deriv API when accounts share the same PAT or use OAuth. If a listed account shows no token, log in separately with that account's own PAT token.

---

## 7. Auto Trader — Step by step

Requires **Higher/Lower** contract type and a configured barrier.

| Step | Action |
|---|---|
| 1 | Switch to **Higher/Lower** |
| 2 | Set **barrier offset** (presets or manual) |
| 3 | Set **+/−** sign: `+` locks LOWER only, `−` locks HIGHER only |
| 4 | Set stake, duration, staking mode |
| 5 | Click **Auto Trade** — green pulse = watching |
| 6 | Stage 1: ≥80% + 3 consecutive same-direction signals → amber (armed) |
| 7 | Stage 2: 100% confidence + perfect 1m candle + risk check → fires |
| 8 | Cooldown until next 1m candle, then restarts |

---

## 8. Staking Mode

Select from the **Staking Mode** panel in the sidebar.

| Mode | How it works |
|---|---|
| **Fixed** | Exact value from stake input |
| **Kelly** | 25% conservative Kelly from rolling 20-trade win rate + payout ratio. Needs 5+ trades. |
| **Martingale** | Doubles stake on each loss, resets on win, hard cap at 4 levels |

Set a **Profit Target** (0 = off) — auto-trade stops when session profit reaches this.

---

## 9. Signal Strength Meter

Always-visible bar at the bottom of the chart panel:
- **Width** = confidence %
- **Colour** = green ≥80% / amber ≥60% / grey <60%
- **Direction** = ▲ BULL / ▼ BEAR / WAIT
- **WR** = rolling 20-trade win rate

---

## 10. Pre-Trade Checklist

Visible in the **AI tab** when a signal is active. 8 conditions:

| Check | Pass condition |
|---|---|
| ADX > 18 | Market is trending |
| ATR volatility OK | Move > 20% of ATR |
| HTF bias aligned | EMA trend matches signal |
| Confidence ≥ 70% | Minimum quality gate |
| Not ranging | ADX confirms trend |
| RSI aligned | Not opposing signal |
| 1m candle direction | Candle matches signal |
| No counter-divergence | RSI/MACD not diverging against signal |

Score ≥75% → ✓ Good · ≥50% → ⚠ Marginal · <50% → ✗ Wait

---

## 11. Session Risk Manager

**Stats tab → Risk Settings.**

| Setting | Default | Effect |
|---|---|---|
| Max Session Loss | 0 (off) | Pauses when cumulative loss hits this |
| Max Trades/Session | 0 (off) | Pauses after N trades |
| Max Consec Losses | 3 | Pauses after N consecutive losses |
| Cooldown | 2 min | Wait before auto trade resumes |

---

## 12. Layout controls

| Control | How |
|---|---|
| Resize sidebar | Drag right edge of left panel |
| Resize chart/sub-charts | Drag handle between chart and MACD/AO/RSI |
| Toggle indicators | Buttons in indicator toolbar |
| Force AI re-analysis | Click **⟳ Analyse** |
| Switch theme | Click **☀ / 🌙** in topbar |
| Switch account | Click account ID in topbar |

---

## 13. Troubleshooting

| Problem | Fix |
|---|---|
| "Auth failed" | Check PAT token has Read + Trade + Payments scopes |
| "Invalid App ID" | Verify App ID at app.deriv.com/developer-tools |
| No prices | Use Synthetic Indices — available 24/7 |
| Barrier panel missing | Switch to Higher/Lower contract type |
| Payout shows `…` | Adjust barrier or stake |
| Chart blank | Wait 2–5 ticks after market selection |
| AI shows "Building OHLC…" | Wait ~15 min for 15+ 1m bars |
| Auto Trade blocked | Must be in Higher/Lower with barrier > 0 |
| Auto not arming | Need ≥80% + 3 consecutive same-direction signals |
| Auto not firing | Need 100% + perfect 1m candle |
| Auto disarmed | Barrier sign changed or direction flipped |
| Risk paused | Session limit hit — wait or reset in Stats |
| No sound | Click page once to unlock Web Audio |
| Account switch fails | That account needs its own PAT token |
| Disconnected | Auto-reconnects in 3s — wait for Live status |
| Theme not saving | Check localStorage not blocked |
| DEMO badge showing | You are on a virtual/demo account |
