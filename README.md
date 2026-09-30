# YouTube & Facebook Creator Support — Landing Page

Policy-friendly, single-screen landing page for a free independent creator community. The page is designed for Meta ads and sends interested creators to the Telegram community.

## Files

| File | Kaam |
|---|---|
| `index.html` | Main landing page — HTML, CSS and JavaScript in one file |
| `CNAME` | Custom domain: `ytsalutions.in` |
| `README.md` | Setup and tracking notes |

## Current page flow

`Meta ad → creator support landing page → Telegram community`

The page presents educational benefits such as algorithm updates, content and video tips, creator networking, Q&A discussions and community support. It does not promise specific views, subscribers, reach, approval or earnings, and clearly states that it is independent and not affiliated with YouTube, Facebook, Meta or Telegram.

## Telegram links

- Main community CTA: `https://t.me/+nZRxaOOdx2ozMGE1`
- Advertising credit link: `https://t.me/adstele_agency`

The `Advertising by @adstele_agency` link is only a credit/link for the advertising channel. It has no Meta event or lead tracking attached to it. Only the main Telegram community CTA keeps the existing Lead tracking.

## Meta Pixel and events

The existing Meta Pixel setup and event behavior have been preserved:

| Event | Kab | Kitni baar |
|---|---|---|
| `PageView` | Page load | Har visit par |
| `Lead` | Main Telegram community CTA click | One time per browser via `localStorage` |
| `TelegramJoinClick` | Main Telegram community CTA click | One time per browser via `localStorage` |

Pixel ID, Pixel script, and existing tracking logic are intentionally unchanged. The tracking key is `tg_lead_v1`; changing it to a new version would reset the one-lead-per-browser protection.

## Free hosting with GitHub Pages

1. Push the repository to GitHub.
2. Open **Settings → Pages**.
3. Select **Deploy from a branch** → branch `main` / `(root)`.
4. For the custom domain, keep `CNAME` as `ytsalutions.in` and configure the domain DNS as required by GitHub Pages.

Cloudflare Pages and Netlify can also host this static page without a build step.

## Notes

- No framework or backend is required.
- The page is mobile responsive and optimized for a single screen.
- Privacy Policy, Terms & Conditions, and Disclaimer are available in modal dialogs.
- Replace the Telegram community link only if the destination changes; do not add tracking attributes to the advertising-credit link unless that requirement changes later.
