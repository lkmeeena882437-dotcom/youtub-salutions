# YouTube & Facebook Creator Support

Static landing page for an independent, free creator community. The page sends visitors to the Telegram community and is hosted on the custom domain `ytsalutions.in`.

## Files

- `index.html` — complete page with HTML, CSS and JavaScript
- `CNAME` — custom domain configuration

## Links

- Main community: `https://t.me/+nZRxaOOdx2ozMGE1`
- Advertising credit: `https://t.me/adstele_agency`

The advertising credit link is only a public attribution link. It has no Meta event or lead tracking. Tracking is attached only to the main Telegram community CTA.

## Tracking (single-button flow)

The page has **one CTA only**. Tapping it fires `Lead` and hands the visitor
straight to Telegram — no confirmation popup, no second button, and no custom
events.

- `PageView` on page load
- `Lead` on the CTA tap, with `content_name` / `content_category` params, and
  **once per browser** (`LEAD_ONCE_PER_BROWSER` in the script — set it to
  `false` to count every tap). A stable `eventID` is stored per browser so a
  future server-side Conversions API event can be deduplicated against it.
- Removed: the old `TelegramCtaTap` diagnostic custom event and the
  confirmation-dialog flow. `TelegramJoinClick` is **not** in this codebase —
  if it appears in Events Manager it comes from another page or an older
  cached version.

Pixel ID, event name (`Lead`) and the Telegram URL are unchanged, so running
campaigns and their learning phase are untouched.

## Conversion helpers

- **Handoff that never dead-ends:** mobile and in-app browser visitors
  (Facebook, Instagram, Messenger, WhatsApp, TikTok, Snapchat, Google app,
  Android WebView) go to Telegram in the same tab. Desktop visitors get a new
  tab opened synchronously inside the tap gesture; if the browser blocks the
  popup, the page falls back to same-tab navigation — the user always reaches
  Telegram (previously a blocked popup silently did nothing while the Lead
  event had already fired).
- **300 ms pixel flush gap:** navigation happens 300 ms after the `Lead`
  event (button shows "🔄 Telegram khol rahe hain…" and is disabled against
  double taps) so the beacon leaves the page before the context is destroyed.
- **`fbclid` / UTM capture:** click IDs are stored in `localStorage`
  (`fb_click_v1`, Meta-standard `fbc` format) as groundwork for server-side
  real-join attribution. No extra network call is made.
- **Join-request expectation note** under the CTA tells users the admin
  approves requests, reducing confusion and repeat taps.

> Note: the `Lead` event measures a CTA tap, not a completed Telegram join.
> See `LEAD-DROP-REPORT.md` and `JOINING-ACCURACY.md` for the funnel analysis.

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
