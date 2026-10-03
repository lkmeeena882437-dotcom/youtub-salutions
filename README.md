# YouTube & Facebook Creator Support

Static landing page for an independent, free creator community. The page sends visitors to the Telegram community and is hosted on the custom domain `ytsalutions.in`.

## Files

- `index.html` — complete page with HTML, CSS and JavaScript
- `CNAME` — custom domain configuration

## Links

- Main community: `https://t.me/+nZRxaOOdx2ozMGE1`
- Advertising credit: `https://t.me/adstele_agency`

The advertising credit link is only a public attribution link. It has no Meta event or lead tracking. Tracking is attached only to the main Telegram community CTA.

## Tracking retained (two-step confirmation lead)

- `PageView` on page load
- `TelegramCtaTap` (custom, **diagnostic only**) on every CTA tap — never
  counted as a lead; exists only to measure accidental-tap volume
- `Lead` fires **only when the user confirms** in the confirmation dialog —
  exactly one event per confirmed user, once per browser. Ads Manager
  "Website Leads" therefore counts confirmed intent, not accidental taps.
  Same pixel ID, same event name, same URL as before, so running campaigns
  and their learning phase are untouched.

## Conversion helpers

- **Two-step confirmation lead:** tapping the CTA opens an on-page
  confirmation dialog ("Haan, Telegram join karna hai" / "Nahi"); the Lead
  event fires only on confirm, so accidental Reels/Story taps never enter
  Ads Manager counts.
- **Handoff that never dead-ends:** after confirm, mobile and in-app browser
  visitors (Facebook, Instagram, Messenger, WhatsApp, TikTok, Snapchat,
  Google app, Android WebView) are sent to Telegram in the same tab. Desktop
  visitors get a new tab opened synchronously inside the tap gesture; if the
  browser blocks the popup, the page falls back to same-tab navigation — the
  user always reaches Telegram (previously a blocked popup silently did
  nothing while the Lead event had already fired).
- **300 ms pixel flush gap:** navigation happens 300 ms after the Lead event
  (button shows "🔄 Telegram khol rahe hain…") so the beacon leaves the page
  before the context is destroyed.
- **Join-request expectation note** under the CTA tells users the admin
  approves requests, reducing confusion and repeat taps.

> Note: the `Lead` event measures a *confirmed CTA tap*, not a completed
> Telegram join. See `LEAD-DROP-REPORT.md` for the full funnel-drop analysis.

## Page structure (top to bottom)

1. Badge + headline + sub-headline
2. 9:16 testimonial video (`assets/testimonial-9x16.mp4`) with gradient
   border ring and a big tap-to-play overlay button
3. "Real Creator Experience & Community Support Review" line
4. Main Telegram CTA (+ sub-points + join-request approval note)
5. "What's Inside" benefits card
6. Rotating ticker, ad credit, legal links, footer micro-copy

The page scrolls naturally (the old single-viewport `overflow:hidden` lock
is removed), so added sections can never overlap or clip again.

## Testimonial video (9:16)

- Tapping the play overlay (or the video itself) plays it inline on the page
  (`controls` + `playsinline`); only metadata is preloaded
  (`preload="metadata"`) so mobile data is saved.
- The section stays fully hidden if the file is missing (404), so the page
  never shows a broken player.
- An "individual experience, results vary" disclaimer sits in the footer
  micro-copy to stay inside Meta's unrealistic-outcomes policy.

The existing Pixel ID and tracking behavior are retained. The page contains no forms, backend, payment flow, or framework.
