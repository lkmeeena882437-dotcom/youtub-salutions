# 🚀 YouTube & Facebook Page Growth — Landing Page (Meta Ads Funnel)

Ultra high-converting, **single screen (no scrolling)** landing page for Meta ads →
Telegram community join funnel.

## 📁 Files

| File | Kaam |
|---|---|
| `index.html` | **Main landing page** (HTML + CSS + JS sab ek hi file me) |
| `META-POLICY-GUIDE.md` | Meta ads policy guide (Hinglish) — ads reject hone se bachne ke liye |
| `README.md` | Ye file |

## ⚡ Setup

### 1) Telegram link — ✅ already set
`https://t.me/+nZRxaOOdx2ozMGE1` — page me lag chuka hai.
Badalna ho to `index.html` me **`t.me/`** search karo.

### 2) Meta Pixel ID — ⏳ aapko lagani hai
`index.html` me search karo: **`META_PIXEL_ID`** → `'PASTE_PIXEL_ID_HERE'` ki jagah apni Pixel ID.

```js
const META_PIXEL_ID = '123456789012345';   ← yahan apni ID
```

Pixel ID milegi: [events.facebook.com](https://events.facebook.com) → Data Sources → Pixels.
Test: Chrome me **"Meta Pixel Helper"** extension — page par `PageView`,
button click par `Lead` fire hona chahiye.

### 3) (Optional) Email placeholder badlo
Legal modals me `[your-email@example.com]` ko apne asli email se badal do.

## 📊 Meta Tracking kaise kaam karta hai

| Event | Kab | Kitni baar |
|---|---|---|
| `PageView` | Page load | Har visit par (normal) |
| `Lead` | Telegram button click | **Sirf 1 baar per user/browser** 🛡️ |
| `TelegramJoinClick` (custom) | Telegram button click | **Sirf 1 baar per user/browser** 🛡️ |

**Double-tracking protection (already coded):**
`localStorage` flag (`tg_lead_v1`) ki wajah se koi user button 100 baar bhi
click kare ya page baar-baar khole — `Lead` **sirf ek hi baar** count hoga.
Naye campaign ke liye counting reset karni ho to `index.html` me
`'tg_lead_v1'` → `'tg_lead_v2'` kar do.

**Ads Manager me kya dekhna hai:**
- Campaign objective: **Leads** (optimise event: `Lead`)
- Columns: *Results (Leads)* + *Cost per Result (Cost per Lead)*
- Actual Telegram joins verify: Telegram ka **per-invite-link stats**
  (ads ke liye ek alag invite link banao — Telegram khud batata hai
  kitne log us link se join hue) → compare with Pixel Leads

## 🌐 Free Hosting (GitHub Pages)

1. Ye repo GitHub par push karo
2. GitHub repo → **Settings → Pages**
3. Source: `Deploy from a branch` → Branch: `main` / `(root)` → Save
4. 1-2 min me page live: `https://username.github.io/youtub-salutions/`

(Alternative: Cloudflare Pages, Netlify — sirf drag-and-drop karo.)

## 📱 Features

- ✅ 100% mobile responsive, single screen — koi scrolling nahi
- ✅ Bada Telegram CTA button: "JOIN FREE TELEGRAM COMMUNITY"
- ✅ Meta Pixel tracking with **one-lead-per-user** dedup
- ✅ Privacy Policy / Terms & Conditions / Disclaimer — popup modals (full UK English)
- ✅ Rotating benefits ticker (9 channel benefits + mission)
- ✅ "Aaj ka offer" countdown timer (urgency ke liye)
- ✅ Fast loading — koi framework nahi, ek hi HTML file
- ✅ Landscape phones ke liye 2-column layout

## ⚠️ Important

Ads chalane se pehle **`META-POLICY-GUIDE.md` zaroor padh lena** — usme bataya hai:
kya likhna chahiye/kya nahi, Meta Pixel setup, reject hone par kya karna hai,
aur safe ad copy examples.
