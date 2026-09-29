# 🚀 YouTube & Facebook Page Growth — Landing Page (Meta Ads Funnel)

Ultra high-converting, **single screen (no scrolling)** landing page for Meta ads →
Telegram community join funnel.

## 📁 Files

| File | Kaam |
|---|---|
| `index.html` | **Main landing page** (HTML + CSS + JS sab ek hi file me) |
| `META-POLICY-GUIDE.md` | Meta ads policy guide (Hinglish) — ads reject hone se bachne ke liye |
| `README.md` | Ye file |

## ⚡ Setup — sirf 2 cheezein badalni hain

### 1) Apna Telegram channel link lagao
`index.html` me search karo: **`t.me/`** → `https://t.me/your_channel` ko apne channel se badlo.

```html
href="https://t.me/your_channel"   ← yahan apna link
```

### 2) Meta Pixel ID lagao
`index.html` me search karo: **`META_PIXEL_ID`** → `'PASTE_PIXEL_ID_HERE'` ki jagah apni Pixel ID.

```js
const META_PIXEL_ID = '123456789012345';   ← yahan apni ID
```

Pixel ID milegi: [events.facebook.com](https://events.facebook.com) → Data Sources → Pixels.
Test karne ke liye Chrome me **"Meta Pixel Helper"** extension use karo —
page open karte hi `PageView`, button click par `Lead` fire hona chahiye.

### 3) (Optional) Email placeholder badlo
Privacy/Disclaimer modals me `[आपका-ईमेल@example.com]` ko apne asli email se badal do
(search: `ईमेल`).

## 🌐 Free Hosting (GitHub Pages)

1. Ye repo GitHub par push karo
2. GitHub repo → **Settings → Pages**
3. Source: `Deploy from a branch` → Branch: `main` / `(root)` → Save
4. 1-2 min me page live: `https://username.github.io/youtub-salutions/`

(Alternative: Cloudflare Pages, Netlify — sirf drag-and-drop karo.)

## 📱 Features

- ✅ 100% mobile responsive, single screen — koi scrolling nahi
- ✅ Bada Telegram CTA button: "JOIN FREE TELEGRAM COMMUNITY"
- ✅ Meta Pixel tracking (PageView + Lead + custom event)
- ✅ Privacy Policy / Terms & Conditions / Disclaimer — popup modals
- ✅ Rotating benefits ticker (9 channel benefits + mission)
- ✅ "Aaj ka offer" countdown timer (urgency ke liye)
- ✅ Fast loading — koi framework nahi, ek hi HTML file
- ✅ Landscape phones ke liye 2-column layout

## ⚠️ Important

Ads chalane se pehle **`META-POLICY-GUIDE.md` zaroor padh lena** — usme bataya hai:
kya likhna chahiye/kya nahi, Meta Pixel setup, reject hone par kya karna hai,
aur safe ad copy examples.
