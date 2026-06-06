# Quick Setup — Deriv Smart Trader Pro v3.0

## 1. Register Your App at developers.deriv.com

1. Go to https://developers.deriv.com
2. Log in (create an account if needed)
3. Click **Dashboard**
4. Click **Register a new application**
5. Choose type: **PAT** (recommended for personal use)
6. Copy your **App ID** — format: `33twueeulu2pNK1RhIYVz` (alphanumeric)

> **Important:** Legacy App IDs from `api.deriv.com` will NOT work. You must register a new app at `developers.deriv.com`.

---

## 2. Create a PAT Token

1. In the same Dashboard, go to **API Tokens**
2. Click **Create new token**
3. Select scopes: **trade** + **account_manage**
4. Copy the token (you cannot view it again after creation)

---

## 3. Push to GitHub

```bash
git init && git add . && git commit -m "v3.0 release" && git branch -M main
git remote add origin https://github.com/<user>/deriv-smart-trader-pro.git
git push -u origin main
```

---

## 4. Enable GitHub Pages

Settings → Pages → Source: **main / root** → Save

URL: `https://<user>.github.io/deriv-smart-trader-pro/`

---

## 5. Login Flow

| Step | What happens |
|------|-------------|
| Enter PAT + App ID, click **Connect & Authenticate** | App calls REST API to fetch your accounts |
| If you have multiple accounts | A dropdown appears — select DEMO or REAL |
| Click **Connect Selected Account** | App gets OTP WebSocket URL and connects |
| App shows **Live** status | You're connected and trading |

---

## 6. Troubleshooting

| Problem | Fix |
|---------|-----|
| "Failed to load accounts" | Check PAT has `trade` + `account_manage` scopes |
| "HTTP 401" | App ID or PAT token is wrong |
| "HTTP 403" | Token scope missing — regenerate with correct scopes |
| "No accounts found" | Your account may not have Options trading enabled |
| App ID not working | Must register at developers.deriv.com (not api.deriv.com) |
| Multiple accounts shown | Select DEMO to practice, REAL for live trading |
| Disconnected during trading | Auto-reconnects in 3 seconds |
| No prices after login | Switch market or wait 2–5 ticks |
| AI shows "Building OHLC…" | Wait ~15 min for 15+ 1m bars |
| Auto Trade blocked | Must be in Higher/Lower with barrier > 0 |
