# Joining Accuracy — 200 Leads vs <100 Members: Kyun, aur Kaise Fix Karein

Date: 3 October 2026 · Page: `ytsalutions.in` · Pixel: `1089305817042982`
Channel: YOUTUBE MONETIZATION SOLUTIONS (339 subs) · Pending requests: **0**

---

## 0. Aapki baat, confirmed

- Jo log join hue, woh **paid bhi convert kar rahe hain** → **targeting/audience quality theek hai.**
- Pending requests 0 hain → **admin approval aapka problem nahi hai.**

Matlab gap ka location = **"Meta ne lead gina"** aur **"Telegram me member bana"** ke **beech**.

---

## 1. Root cause — ek line me

> Meta jo "Lead" count kar raha hai, woh **confirm-button ka tap** hai — aur ye tap aise log bhi kar dete hain
> **jinke phone me Telegram app hi nahi hai.** Unka safar wahin khatam: t.me page → "Download Telegram" →
> install nahi → wapas nahi aaya. Meta ko is baat ki khabar hi nahi hai.
>
> Jo log **pehle se Telegram use karte hain**, woh join kar lete hain — aur wahi log aage **paid bhi convert**
> kar rahe hain. Isliye "jo aaya wo accha hai, par aadhe log aaye hi nahi" — ye poori tarah consistent hai.
>
> **Fix ka core: Meta ko "asli join" ka signal do. Tab Meta khud aise log dhoondega jinke paas Telegram hai.**
> (Aaj wo sirf "tap karne wale" dhoondh raha hai — Telegram wale aur non-Telegram wale dono.)

---

## 2. Funnel math — 200 kaise ~90 banta hai

| Step | Kaun count karta hai | Typical rate (India, cold Reels traffic) | 200 se bacha |
|---|---|---|---|
| Ad click | Meta | — | 1000 (example) |
| Page load | Pixel `PageView` | 75–90% | ~800 |
| CTA tap | Pixel `TelegramCtaTap` | 25–45% | ~250 |
| Confirm tap | **Pixel `Lead` (= aapka "200")** | 80–92% | **~200** |
| Telegram app khula | ❌ koi nahi | 75–92% | ~160 |
| **Andar pahuncha (join)** | ❌ koi nahi | **45–70%** ← **asli leak** | **~90** |

Aapka 200 → ~90 (<50%) is table ke aakhri row se aata hai. Ye **normal range ke andar hai** — mean koi
tracking bug nahi, balki **last-mile friction + Meta ka galat definition** hai.

---

## 3. Possibilities — ranked, with verification

### 🥇 A. Telegram app / account hi nahi hai (estimated gap ka 30–45%)
India ke Reels/Story traffic me bada hissa aisa hai jinke phone me Telegram nahi hai. Telegram join karne ke
liye app + **phone number verification** chahiye. Ye log page par sab kuch kar lete hain (confirm tap bhi),
phir `t.me` par download screen dekh kar chhod dete hain.

**Kaise pakka karein (aaj):** 3–5 aise logon se karwao jinke phone me Telegram nahi hai. Dekho kahan rukte hain.
Aur Events Manager me `PageView` vs `Lead` ratio nikaalo — agar Lead rate 20%+ hai to bade hisse log
page par sab kar rahe hain par join nahi kar pa rahe.

**Fix:** (i) Meta ko real-join signal (CAPI) → algorithm khud Telegram-users target karega;
(ii) creatives me pre-qualify karo — *"Telegram app hai? Hi tap karein"*.

### 🥈 B. Meta ke number me inflation (estimated 15–30%)
| Sub-cause | Detail | Check |
|---|---|---|
| View-through attribution | "7-day click + **1-day view**" me woh log bhi judte hain jinho ne ad sirf dekhi thi | Ads Manager → Attribution |
| Repeat leads | FB in-app browser ka storage alag hota hai; Safari 7-din me clear → same banda 2 baar "naya" lead | Events Manager |
| Audience Network / bots | AN traffic JS chala kar confirm bhi daba deta hai, par Telegram kabhi nahi jata | Breakdown → Placement |
| Galat column | Kahin "Results" = **Link Clicks / LPV** na ho | Ads Manager → Columns |
| Pixel kisi aur page par bhi | Wahi pixel ID kisi doosri site/test par laga ho | Events Manager → URLs |

### 🥉 C. Handoff friction (5–15% — **yesterday fix ho chuka hai**)
Popup-blocked dead-end, WhatsApp/in-app browsers, Lead fire hote hi navigation. Fix + test results PR me hain.

### D. Pehle se member wale log (5–10%, abhi kam, aage badhega)
Jo already channel me hain woh ad dekh kar dobara tap kar sakte hain → Lead count, par naya member nahi.
**Fix:** converters/members ko exclude karke alag (sasta) retargeting campaign.

### E. Approval queue — **iska jawab mil gaya: yahi nahi hai (0 pending)** ✅

---

## 4. Fix plan — impact ke hisaab se ranked

| # | Kaam | Effort | Expected asar |
|---|---|---|---|
| 1 | **Ads Manager hygiene:** Attribution → *7-day click only*; Audience Network **OFF**; "Results" column ka definition confirm; pixel sirf is domain par hai ye check | 30 min | Inflated leads kam, CPM honest, bot traffic cut |
| 2 | **Last-mile friction kam** (page me kar diya): "Aage kya hoga" 3-step guide + app-na-hone par download hint | ✅ done | Confusion se hone wala drop kam |
| 3 | **Creatives me pre-qualify:** "Telegram app hai to hi join karein" + join ka screenshot | 1 ghanta | Non-Telegram clicks kam → CPC/lead sasta |
| 4 | **Measurement kit** `/go` redirect + Telegram bot (channel admin): join/leave/request log, daily count | 2–3 ghanta, free hosting | Exact pata: drop kis step par aur kitna |
| 5 | **CAPI real-join event** (bot junction + `fbclid`) → campaign **joins par optimize** | 1 din | Joining accuracy ka asli permanent fix |
| 6 | **Retargeting alag campaign** + converters exclude; frequency cap 2–3/din | 30 min | Repeat leads kam, creative burnout se bachav |
| 7 | **Promise match:** page "community/chat" bolta hai, destination broadcast channel hai — text ya destination align karo | 30 min | Join karke turant leave karne wale kam |

> Note: #4 aur #5 ke liye ek Telegram bot banana padega (free) — main poori kit repo me bana sakta hoon,
> aapko sirf BotFather se token lena hai aur bot ko channel me admin banana hai (~10 minute).

---

## 5. Architecture jo is problem ko jad se khatam karta hai

```
Ad → /go?fbclid=<meta>   → click log (server)  → Telegram
                                    ↓
                        Telegram bot (channel admin)
                        - join request → turant approve
                        - join/leave log
                                    ↓
              CAPI event: Lead/Join + fbc (fbclid)  →  Meta
                                    ↓
        Campaign ab "asli join" par optimize → aise log dhoondhta hai
        jinke paas Telegram hai, sirf button dabane wale nahi
```

**Iske baad aapko 3 saaf number milenge:** Meta ne kitne click bheje → kitne Telegram tak pahunche → kitne
actually member bane. Drop exactly kis step par hai, roz pata chalega.

---

## 6. Aaj hi ka checklist

- [ ] Ads Manager → Attribution = **7-day click only**
- [ ] Placements → **Audience Network OFF**, breakdown dekho: kaunsa placement sabse zyada "leads" de raha hai
- [ ] Columns → "Results" exactly kis event par set hai, confirm karo
- [ ] Events Manager → is pixel ke URLs check karo (koi doosri site to nahi)
- [ ] Events Manager → `PageView` vs `Lead` ratio note karo (aaj ka baseline)
- [ ] Ad creative/copy me pre-qualify line add karo: "Telegram app hai to hi tap karein"
- [ ] Landing page ka updated code live karo (PR merge) — 3-step guide + handoff fixes
- [ ] 3–5 non-Telegram logon se funnel test karwao, rukne ki jagah note karo

---

## 7. Code changes (is PR me)

| File | Change |
|---|---|
| `index.html` | Confirm modal me **"Aage kya hoga?"** 3-step guide + app-na-hone wala hint (Telegram screen par confusion se hone wala drop kam) |
| `index.html` | **fbclid + UTM capture** → localStorage (`fb_click_v1`, Meta ka standard `fbc` format). Ye step 5 (CAPI real-join event) ke liye zaroori hai — abhi sirf store hota hai, koi extra network call nahi |
| `LEAD-DROP-REPORT.md` | Handoff bug fixes ka record (pichla PR) |

Pixel ID, event names, confirm-only `Lead`, dedupe — **kuch nahi badla**, running campaign safe hai.
