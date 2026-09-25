# SHIFT AI Overview — installable web app

A phone-first, installable overview of SHIFT AI. Product first; the earning streams live on a second tab with no percentages or dollar figures.

**Live URL:** https://app.tooltaxhq.com/

Nobody on the team hosts anything. There is one copy, served by Cloudflare Pages straight from this repo, and each person gets a personalized link.

## Team links

Add `?ref=` and your SHIFT slug to the live URL:

```
https://app.tooltaxhq.com/?ref=YOUR-SLUG
```

Your slug is the last part of your SHIFT invite page, `go.shiftai.club/YOUR-SLUG`. With `?ref=` present, every button on the page points at *your* invite page, the footer shows your name, and the Share button passes your link on. The page remembers the slug on that phone, so a prospect who installs it from your link keeps your attribution.

No `?ref=` means the default link in `CONFIG` (currently `tooltaxhq`).

## Sharing and installing

Send the link by text, DM, or social. Nothing to download.

- **iPhone:** open the link in Safari → Share icon → *Add to Home Screen*.
- **Android:** open in Chrome → tap *Install* on the banner, or ⋮ → *Install app*.
- **Desktop Chrome/Edge:** install icon at the right end of the address bar.

Once installed it opens full-screen with its own icon and works offline.

## Editing (Pat)

Everything is in `index.html`. The `CONFIG` block at the top holds the default referral link, the `REF_BASE` prefix, the footer name, the contact link and the price line. Set any of the text values to `""` to hide that element.

After editing `index.html`, bump `CACHE_VERSION` in `sw.js` (`v1` → `v2`) so installed copies refresh, then commit and push. Cloudflare redeploys in about a minute.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole page. CSS and JS inline. |
| `manifest.webmanifest` | Makes it installable (name, icon, full-screen, theme color). |
| `sw.js` | Service worker: caches the shell for offline use. |
| `icons/` | 192, 512 and 512-maskable PNGs. Swap for real brand icons any time; keep the names. |
| `.nojekyll` | Harmless; keeps GitHub Pages (the fallback host) from processing the files. |

## Before sharing widely

The source deck is out of date in places and the copy came from two sources that disagreed. Check against the platform:

- The price line (`PRICE_LINE`).
- The stream names. The deck says *ConnectPay*; SHIFT's Chat Studio said the current name is *CoachPay*. The page uses CoachPay.
- The studio list (Chat, Image, Video, Voice, Avatar, Translate, Music, Deck, Brand Pack).

Deliberately left out: the Founder's Club window, travel vouchers, the EcoPay calculator numbers, per-club percentages, tier dollar thresholds, and the Miami event.
