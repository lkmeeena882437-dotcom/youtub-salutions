# YouTube & Facebook Creator Support

Static landing page for an independent, free creator community. The page sends visitors to the Telegram community and is hosted on the custom domain `ytsalutions.in`.

## Files

- `index.html` — complete page with HTML, CSS and JavaScript
- `CNAME` — custom domain configuration

## Links

- Main community: `https://t.me/+nZRxaOOdx2ozMGE1`
- Advertising credit: `https://t.me/adstele_agency`

The advertising credit link is only a public attribution link. It has no Meta event or lead tracking. Tracking is attached only to the main Telegram community CTA.

## Tracking retained

- `PageView` on page load
- `Lead` on the main Telegram CTA — **exactly one event per tap**, once per browser
  (the old duplicate custom event `TelegramJoinClick` was removed so that
  Ads Manager "Website Leads" = 1 tap = 1 lead, with no double counting)

## Conversion helpers

- **Automatic in-app browser handoff:** visitors inside the Facebook /
  Instagram in-app browser (where `t.me` links often fail in a new tab) are
  sent straight to Telegram in the same tab on CTA tap — zero extra taps,
  no dialog. Telegram's own page handles the app handoff from there.
  No extra pixel event is fired, keeping the 1 tap = 1 lead rule intact.
- **Join-request expectation note** under the CTA tells users the admin
  approves requests, reducing confusion and repeat taps.

## Testimonial video (9:16)

- Video lives at `assets/testimonial-9x16.mp4` (portrait 9:16), placed
  between the compact "What's Inside" card and the CTA button.
- Tapping the video plays it inline on the page (`controls` + `playsinline`);
  only metadata is preloaded (`preload="metadata"`) so mobile data is saved.
- The section stays fully hidden if the file is missing (404), so the page
  never shows a broken player.
- Heading under the video: "Real Creator Experience & Community Support
  Review", sitting just above the CTA.
- An "individual experience, results vary" disclaimer sits in the footer
  micro-copy to stay inside Meta's unrealistic-outcomes policy.

The existing Pixel ID and tracking behavior are retained. The page contains no forms, backend, payment flow, or framework.
