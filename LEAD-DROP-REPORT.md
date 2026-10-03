# Lead Drop Diagnosis — Meta Ads 200+ Leads vs Telegram <100 Members

Date: 3 October 2026
Page: `ytsalutions.in` (index.html) · Pixel: `1089305817042982`
Telegram destination: `https://t.me/+nZRxaOOdx2ozMGE1` — **channel** "YOUTUBE MONETIZATION SOLUTIONS" (339 subscribers at the time of this check)

---

## 1. TL;DR (seedhi baat)

Page ka tracking code **technically sahi hai** — pixel sahi lag raha hai, `Lead` sirf confirm par fire hota hai, duplicate nahi hota. Phir bhi Meta ka number inflated dikhta hai, kyunki **Meta "Lead" ka matlab join nahi hota**:

> `Lead` event = user ne page par **"YES, JOIN FREE" button dabaya**. Bas.
> Uske baad Telegram khulta hai — aur **wahan se aage ka koi step track hi nahi hota**:
> Telegram app install hai ya nahi, link khula ya nahi, join request bheja ya nahi, **admin ne approve kiya ya nahi**.

To 200 aur 100 ka gap "galat tracking" nahi, **funnel ke woh steps hain jo koi measure nahi kar raha.** Neeche har gap ka exact location hai.

---

## 2. Lead ka poora safar — 7 steps, 5 pe koi tracking nahi

| # | Step | Kaun measure karta hai? | Drop ka risk |
|---|------|------------------------|--------------|
| 1 | Ad dekha / click | Meta | — |
| 2 | Page load (`PageView`) | Meta Pixel | — |
| 3 | CTA tap (`TelegramCtaTap`) | Meta Pixel (diagnostic) | — |
| 4 | Confirm tap (**`Lead`**) | Meta Pixel | — |
| 5 | Telegram actually khula (app/browser handoff) | ❌ koi nahi | **HIGH** — popup block, in-app browser, app install nahi |
| 6 | Join request bheja / Join dabaya | ❌ koi nahi | HIGH — app install nahi, link expire, user ghum gaya |
| 7 | **Admin approve karke member bana** | ❌ koi nahi | **HIGHEST — pending requests member count me nahi aate** |

Meta ka 200 = step 4. Telegram ka <100 = step 7. **Beech ke 3 steps (5, 6, 7) = black box.**

---

## 3. Code me jo actual bug mila (fix kar diya)

### Bug A — Popup block hone par silent dead-end (bada issue)

**Pehle ka code:**
```js
window.open(TG_URL, '_blank', 'noopener');   // agar browser ne popup block kiya to...
```
`window.open` ko return value check hi nahi ho rahi thi. Desktop / non-FB browser me agar popup block hua → **kuch nahi hota**: modal band, Lead fire ho gayi, aur user wahi page par khada rehta hai. Meta ko lead mil gayi, Telegram ko user nahi mila.

**Ab (fix):** khali tab synchronously khulta hai (taaki popup allow ho), phir URL bharta hai; **popup block hone par same-tab fallback** chalta hai — user har haal me Telegram pahunchega.

### Bug B — Sirf FB/IG in-app browser handle tha

Pehle: `inAppBrowser = /FBAN|FBAV|FB_IAB|Instagram/` — sirf Facebook/Instagram.
**Ab:** WhatsApp, Messenger, TikTok, Snapchat, Google app, Android WebView aur baaki mobile browsers bhi same-tab handoff par jate hain (in sab me naya tab bharosemand nahi hota).

### Bug C — Lead fire hote hi page navigate ho jata tha

Traveling page ke context destroy hone se pixel event **server tak pahunch hi nahi pata** (documented Meta/in-app browser issue). Ab navigation se pehle 300 ms ka chhota flush gap hai + button "🔄 Telegram khol rahe hain…" dikhata hai.

### Test results (fake-DOM harness, 5 scenarios)

| Scenario | Tap | Lead before confirm | Lead after confirm | Telegram destination |
|---|---|---|---|---|
| iOS Safari (mobile) | 1 | 0 | 1 | same tab ✅ |
| FB in-app browser | 1 | 0 | 1 | same tab ✅ |
| Android Chrome | 1 | 0 | 1 | same tab ✅ |
| Desktop Chrome | 1 | 0 | 1 | new tab ✅ |
| **Desktop + popup blocked** | 1 | 0 | 1 | same tab fallback ✅ (pehle: kuch nahi ❌) |
| 3 baar confirm tap | 3 | 0 | **1** | dedupe sahi ✅ |

---

## 4. Telegram side — sabse bada shak (yahan 100+ log "gayab" ho sakte hain)

### 4.1 Pending join requests member count me nahi aate
Page ke apne text me likha hai: *"Join request bhejne ke baad admin jaldi approve karta hai"* — matlab link par approval ON hai.

> **Approval-required invite link me request bhejna ≠ member banna.**
> Jo log request bhejkar wait kar rahe hain woh **na subscriber count me dikhte hain, na member list me** — sirf admin ke "Join Requests" queue me.

**👉 Sabse pehle yeh check karein:**
Telegram → channel kholें → channel name tap → **Subscribers** → **Requests** tab.
Agar wahan 50–150 pending requests pade hain → **yahi aapka pura gap hai.** Ye log paise dekar aaye, request bhej chuke hain, aur aapke approve karne ka intezaar kar rahe hain.

**Fix options:**
1. Invite link se **"Request Admin Approval" OFF** kar dein (channel → Manage → Invite Links) → join turant hoga, koi queue nahi.
2. Approval ON rakhna hai to **Telegram bot se auto-approve** karwayein (`approveChatJoinRequest`, 1 second me) — main ye bana sakta hoon.

### 4.2 Link ka content aur page ka promise match nahi kar raha
- Page bolta hai: *Free Creator **Community**, Creator Discussions, Networking, Chat Support*.
- Destination hai: **broadcast channel** "YOUTUBE MONETIZATION SOLUTIONS" — jahan chat/networking hai hi nahi.

Do problems: (a) kuch log join karke dekh kar turant leave kar dete hain (subscriber count wapas gir jata hai), (b) jo page par "community" expect karke aaya use channel pasand nahi aata. Ya group banayein ya page ke text ko "channel" jaisa sach kar dein.

### 4.3 Telegram app install nahi hai / handoff fail
Reels/Story ke saste traffic me bahut log aise hote hain jinke phone me Telegram app hi nahi hai → t.me page khulta hai → App Store/Play Store → **yahan 30–50% log chhod dete hain.** Ye drop ad ki targeting quality ka direct nateeja hai.

### 4.4 Member count = net joiner (join − leave)
Channel ka subscriber count **net** hota hai. Bot/low-quality traffic join karke turant leave kar sakta hai. Isliye "339 subscribers" ka matlab "339 net" — poora gap dekhne ke liye baseline chahiye.

**👉 Aap mujhe ye 3 number do (main exact hisaab laga dunga):**
1. Campaign start se pehle subscriber count = ?
2. Abhi subscriber count = ? (aaj 339 tha)
3. Pending join requests me kitne log hain = ?

---

## 5. Meta side — 200+ ka number inflation kaise banta hai

| Reason | Kya hota hai | Check |
|---|---|---|
| **"Lead" ka definition** | Confirm tap = Lead. Join nahi. | By design |
| **Ek hi banda, do jagah** | FB in-app browser ka localStorage alag hota hai → same user 2 baar "naya" count. Safari ITP 7-din me storage saaf kar deta hai. | By design |
| **Attribution window** | Default "7-day click + 1-day view" me **view-through** conversions bhi judte hain — jo log ad dekh kar baad me direct/organic aakar convert karte hain, unka credit bhi Meta le leta hai. | Ads Manager → Attribution setting |
| **Placement mix** | Audience Network / auto placements se **click-bot aur low-quality traffic** aata hai jo page par JS chala kar confirm bhi daba deta hai — Lead count hoti hai, aadmi Telegram join nahi karta. | Breakdown by Placement |
| **Pixel kahin aur bhi laga ho** | Agar ye pixel ID (1089305817042982) kisi doosri site/page/test par bhi hai, uske leads bhi isi column me aayenge. | Events Manager → pixel → activity/URLs |
| **Column galat padhna** | Kabhi "Results" = Link Clicks / LPV hota hai, Leads nahi. | Ads Manager → Columns → Results ka definition |

**👉 Ads Manager me ye 4 cheezein check karein:**
1. Campaign objective + **"Results" column exactly kis event ko count kar raha hai** (custom conversion? Lead? LPV?)
2. **Breakdown → Placement**: Audience Network/other off-campaign placements ka share kitna hai? (Zyada ho to off kar dein.)
3. **Breakdown → Country/Age/Gender**: koi off-target country aa raha hai?
4. **Attribution**: "7-day click only" kar dein → asli intent wala number dikhega.

---

## 6. Permanent fix (mera recommendation)

Abhi ka setup **intent** measure karta hai, **join** nahi. Sahi fix:

1. **Telegram bot + webhook (main bana dunga):**
   - Join request aate hi **auto-approve** (`approveChatJoinRequest`) → step 7 ka drop 0.
   - Bot har real join ko count kare → aapko **ground truth** milegi: "aaj kitne log actually channel me aaye".
   - Meta ko **Conversions API** se *asli join* ka event bhejna (pixel ke Lead ke saath dedupe) → campaign **real joins** par optimize hoga, taps par nahi. Ye bots/accidental traffic ko khud filter kar dega.
2. **Landing page ka promise = destination:** community chahiye to group, warna page par "channel" likhein.
3. **Approval OFF** (ya bot se auto-approve) — pending queue duniya ka sabse bada silent leak hai.

---

## 7. Aaj ka action checklist

- [ ] Telegram → Subscribers → **Requests** tab khol kar pending count dekhein (sabse pehle yeh)
- [ ] Invite link se **Request Admin Approval** hata dein (ya auto-approve bot lagwayein)
- [ ] Campaign start se pehle ka subscriber count nikalein (baseline)
- [ ] Ads Manager me Placement + Country breakdown dekhein, Audience Network band karein
- [ ] Attribution "7-day click only" karein
- [ ] Events Manager me check karein pixel sirf ytsalutions.in par fire ho raha hai
- [ ] Page ka naya code live karein (PR merge) — popup-blocked dead-end fix
- [ ] 3–4 din bot se real join count karein → phir Meta ke number se compare karein

---

## 8. Page code me jo changes kiye gaye (is PR me)

| File | Change |
|---|---|
| `index.html` | Popup-blocked fallback (Bug A), WhatsApp/TikTok/WebView in-app detection (Bug B), 300 ms pixel-flush gap + button state (Bug C), CTA dobara khulne par button reset |
| `README.md` | Handoff behaviour ka updated documentation |
| `LEAD-DROP-REPORT.md` | Yeh report |

Pixel ID, event name (`Lead`), `TelegramCtaTap`, dedupe logic — **sab waise hi hain**, running campaign ka learning phase safe hai.
