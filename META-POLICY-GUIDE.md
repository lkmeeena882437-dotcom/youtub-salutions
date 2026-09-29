# 📕 Meta (Facebook/Instagram) Ads Policy Guide — Hinglish

> **Purpose:** Aapki ads approve hone me koi dikkat na aaye, ad account safe rahe,
> aur landing page 100% compliant rahe. Padh le — baad me reject/ban ka jhanjhat nahi hoga.

---

## 1. 📄 Landing Page ke Rules (Meta page par kya-kya dekhta hai)

Meta ads review ke time **aapka landing page bhi check hota hai**, sirf ad copy nahi.

| Requirement | Hamare page me status |
|---|---|
| Working **Privacy Policy** link | ✅ Added (popup button) |
| Working **Terms & Conditions** | ✅ Added (popup button) |
| **Disclaimer** + contact info | ✅ Added |
| HTTPS / SSL (https:// se open hona) | ✅ GitHub Pages/Cloudflare Pages free dete hain |
| Ad copy aur landing page **match** hone chahiye (no bait-and-switch) | ✅ Aap dhyan rakhein |
| Page fast load ho, koi broken link na ho | ✅ Single lightweight HTML |
| Business ka kaam clear ho page par | ✅ Offer + services listed |
| Intrusive/forced popups nahi hone chahiye | ✅ Sirf chhote text buttons → modals |

**Golden rule:** Jo ad me likha hai, page par dikhe. Ad me "Free Tips" likha aur page par
sirf ₹150 ka offer ho → **Misleading Claims** reject hota hai.

---

## 2. 🚫 Misleading Claims Policy — SABSE BADA RISK

Ye Meta ki sabse strict policy hai. **Ye sab LIKHNA MANA hai:**

- ❌ "100% Guaranteed Monetization" / "Guaranteed YouTube approval"
- ❌ "Raaton-raat amir banein" / "Bina mehnat ₹1 lakh/month" (unrealistic income claims)
- ❌ Fake before-after screenshots (agar aapke khud ke real nahi hain)
- ❌ Fake testimonials / fake reviews / fake subscriber count badges
- ❌ Fake urgency — "Sirf aaj! Kal price double!" **agar sach me aisa nahi hai**
- ❌ "YouTube/Facebook ki official service hai" type claim
- ❌ Hidden text, keyword stuffing, text ko background me chhupana

### ✅ Kya safe hai:
- "Growth strategies", "tips", "tutorials", "guidance", "support package"
- Real numbers agar wo **package ke components** hain + saath me disclaimer
- Countdown timer — **sirf tab** jab offer sach me limited ho (hamare page me
  countdown "aaj ka offer" ke liye hai — agar aapka offer daily nahi chalta to
  countdown hata dein ya sach ke hisaab se set karein)

> ⚠️ **Disclaimer (results vary) hamare page se HATAANA NAHI** — wo aapki
> protection hai. Guarantee claims + no disclaimer = fast rejection.

---

## 3. 🎯 Personal Attributes Policy — Ad Copy me ye NAHI

Meta allow nahi karta ki user ki **personal condition assert** ki jaye:

| ❌ Nahi chalega | ✅ Chalega |
|---|---|
| "Kya aapka channel grow nahi ho raha?" | "YouTube creators ke liye growth strategies" |
| "Berojgar ho? Ghar baithe kamao!" | "Apne channel ki earning potential badhayein" |
| "Aapke paas paisa nahi hai?" | "Budget-friendly growth pack — ₹150" |
| "Kya aap mote/ptle/bimar hain?" | (health/weight bhi restricted — avoid) |

**Rule:** Baat **service** ke baare me karein, **user ki shakal/haalat/shaadi/naukri/health** ke baare me nahi.

---

## 4. ⚠️ Unrealistic Outcomes / Get-Rich-Quick

"5 Million Views", "3K Subscribers" jaise numbers ko **package components/targets**
ki tarah rakhein, guarantee ki tarah NAHI. Ye lines page par already hain:

> *"Package me dikhayi gayi sankhya targets hain... kisi specific number ya
> monetization approval ki guarantee nahi di jaati."*

Ye line policy + dono ke liye zaroori hai. Iske bina "5M Views" claim
**Unrealistic Outcomes** reject bhi ho sakta hai.

---

## 5. 🔒 Circumventing Policies — Ye karo hi mat

- ❌ Reject hui ad ko **chhupa-chhupa ke** dobara chalana (text flip/spin karke)
- ❌ Rejection ke baad **naye-naye ad accounts** banana → **permanent ban** risk
- ❌ Review system ko dhoka dena (white text on white background, etc.)
- ❌ Policy ke against content ko redirect/chhota page bana ke chhupana

**Sahi tarika:** Policy padho → copy/page theek karo → fresh review request karo.

---

## 6. 🚷 Restricted/Prohibited Content — Quick Checklist

- Adult, nudity, violence, drugs, tobacco → **banned**
- Alcohol, gambling, health/medical claims, finance "get rich" → **restricted** (special permission)
- Religion/caste/community ke against hate → **banned**
- Personal attributes (upar #3) → **banned**
- **Brand logos:** Facebook/Instagram/WhatsApp/Meta ke official logos bina
  permission use mat karein — text me "Meta ads", "Telegram" likhna safe hai.
  YouTube/Google logos Google brand guidelines se hi use karein.
- Politicians/election/political content → sensitive, avoid

---

## 7. ⚠️ YouTube/Facebook ke against service bechte waqt — Imaandar salah

Agar aapki service **bots / fake accounts / purchased engagement** se related hai
(fake subs, fake watch hours, fake views):

1. **YouTube ki Fake Engagement Policy** ise allow nahi karta — clients ke channels
   strike/terminate ho sakte hain
2. **Meta** ise "misleading/inauthentic behavior" maan kar ads reject kar sakta hai
3. Ye aapke **ad account ki health** ke liye khatarnaak hai

**Safe positioning (recommended):**
- "Growth Consultation + Strategy + Tutorials + Support"
- "Real promotion / marketing guidance" (agar service sach me real marketing hai)
- Ad copy me **kabhi** na likhein: "YouTube officially supported", "monetization guaranteed"
- Client ko hamesha batayein ki final approval platform ka apna decision hai

---

## 8. 😤 Ad Reject Ho Jaye To Kya Karein

1. **Account Quality** section me jao → exact rejection reason padho
2. Sirf usi claim/page ko fix karo jo violate kar raha hai
3. **Same ad unchanged dobara mat chalao** — ye circumventing hai
4. "Request Review" karo (mostly 24-48 hrs me result)
5. Baar-baar reject hone par ad account disable ho sakta hai — isliye pehli baar me
   compliant copy banao (niche examples hain)

---

## 9. 📊 Meta Pixel Setup — Step by Step

1. **events.facebook.com** → Events Manager → *Connect Data Sources* → **Web** → Pixel banao
2. Pixel ID copy karo (123456789012345 jaisi hoti hai)
3. `index.html` me search karo **`META_PIXEL_ID`** → `'PASTE_PIXEL_ID_HERE'` ko apni ID se badlo
4. Page kholo → Chrome me **"Meta Pixel Helper"** extension lagao → green badge me
   `PageView` fire hona chahiye ✅
5. CTA button click karke check karo → `Lead` event bhi fire hona chahiye
6. Events Manager → **Test Events** tool se live verify karo

### Events jo hamare page me already coded hain:

| Event | Kab fire hota hai | Use |
|---|---|---|
| `PageView` | Page load par (auto) | Tracking base |
| `Lead` | Telegram button click | **Optimization** ke liye main event |
| `TelegramJoinClick` (custom) | Telegram button click | Detailed analysis |

### 🛡️ Double-tracking protection (already coded):
- `Lead` event **ek user par sirf 1 baar** fire hota hai (localStorage flag `tg_lead_v1`),
  chahe user button kitni baar bhi click kare ya page baar-baar khole — numbers inflate nahi honge
- Naye campaign ke liye counting RESET: `index.html` me `'tg_lead_v1'` → `'tg_lead_v2'`

### 📌 Actual Telegram joins verify karna (zaroori):
Pixel `Lead` = **join button ka CLICK**, actual join nahi (user click karke
Telegram khole par join na bhi kare). Actual numbers ke liye:
1. **Alag invite link** sirf ads ke liye banao (Telegram channel → Invite Links → Create Link)
2. Telegram har link ka **join stats** dikhata hai → wo hai aapka "actual subscribers from ads"
3. Cost per subscriber = `Ad spend ÷ Telegram link joins`
4. (Advanced) Welcome **bot** se puch sakte ho "Where did you find us?" — 100% accurate

### Optimization tips:
- Campaign objective: **Leads** (ya shuru me **Landing Page Views / Link Clicks**)
- `Lead` event par optimize karne ke liye Meta ko **~50 events/week** chahiye —
  jab tak utne nahi milte, Landing Page Views se optimize karo
- **Aggregated Event Measurement** me `Lead` ko priority event set karo (iOS ke liye)
- Advanced: **Conversions API (server-side)** baad me add kar sakte ho — 20-30% better tracking
- Har ad set ke liye **UTM parameters** lagao, taaki pata chale konsa ad kaam kar raha:
  `https://aapka-page.com/?utm_source=facebook&utm_medium=paid&utm_campaign=offer_sep`

---

## 10. ✍️ Safe Ad Copy Examples

### ✅ Approve hone wali copy:

> **Headline:** YouTube Creators ke liye Growth Tips & Community 🚀
> **Description:** Tips, tutorials, SEO guides aur 24×7 support — Free Telegram community join karein.
> **CTA:** Join Community

> **Headline:** YouTube Monetization ki jaankari — Hindi me
> **Body:** Subscribers, watch time aur reach badhane ke tarike sikhein. Step-by-step
> tutorials + creator tools ki list. Free community me shamil hon.
> **CTA:** Learn More

### ❌ Reject hone wali copy:

> ~~"₹150 me 100% Monetization GUARANTEED — 3 din me 1M views!!"~~
> ~~"Kya aap berojgar hain? Aaj hi kamao!"~~
> ~~"YouTube ki official service — guaranteed approval"~~

---

## 11. ✅ Launch se Pehle Final Checklist

- [ ] Pixel ID lagayi aur Pixel Helper me `PageView` + `Lead` fire ho raha hai
- [ ] Telegram link (`t.me/`) sahi hai aur mobile me Telegram app khul rahi hai
- [ ] Privacy Policy / Terms / Disclaimer buttons kaam kar rahe hain
- [ ] Email placeholder (`[आपका-ईमेल@example.com]`) ko asli email se badla
- [ ] Ad copy me koi guarantee/100%/unrealistic claim nahi hai
- [ ] Ad copy aur page ka offer match karta hai
- [ ] Countdown tabhi hai jab offer sach me limited hai
- [ ] Page mobile par test kiya (360px width par bhi)
- [ ] HTTPS on hai
- [ ] Ad account + Page verified hai (Business Manager me)

---

## 12. 💡 Extra Optimization Ideas

1. **A/B test** karo: alag headlines (₹150 wale vs free-tips wale angle)
2. **Retargeting audience**: page viewers ko 7 din baad dobara ad dikhao (wahi budget me better ROI)
3. **Lookalike audience**: Telegram joiners ki list se 1-2% lookalike banao
4. **WhatsApp button** secondary rakh sakte ho (India me conversion achha milta hai)
5. **Real testimonials/screenshots** (asli customers ke) — trust badhta hai, policy-safe bhi
6. Page ki speed fast rakho — ye page already <1 sec load hoga
7. Alag-alag audience ke liye **alag landing pages** (YouTube creators vs Facebook page owners)

---

*Ye guide general information ke liye hai — Meta apni policies time-to-time update karta
hai, official source: [https://www.facebook.com/policies/ads](https://www.facebook.com/policies/ads)*
