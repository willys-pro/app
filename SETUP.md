# Quick Setup — Deriv Smart Trader Pro v2.0

## 1. Get Your PAT Token

1. Go to https://app.deriv.com/account/api-token
2. Click **Create new token**
3. Select scopes: **Read + Trade + Payments**
4. Copy the token — starts with `pat_`

---

## 2. Get Your App ID

1. Go to https://app.deriv.com/developer-tools
2. Register a new app or use an existing one
3. Copy your App ID (alphanumeric string)

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

---

## 5. Login

Enter your PAT token and App ID, then click **Connect & Authenticate**.

- Press **Tab** after PAT to move to App ID
- Press **Enter** in App ID to submit

---

## 6. Troubleshooting

| Problem | Fix |
|---|---|
| Token validation error | Token must start with `pat_` |
| "WebSocket connection failed" | Verify App ID at app.deriv.com/developer-tools |
| "Connection timed out" | Check internet connection and App ID |
| Auth failed | Check token scopes: Read + Trade + Payments |
| No prices | Use Synthetic Indices — available 24/7 |
| Account switch fails | That account needs its own PAT token |
