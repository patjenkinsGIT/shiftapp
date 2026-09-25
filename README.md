# SHIFT AI Walkthrough — a free phone app for SHIFT members

**Live:** https://app.tooltaxhq.com

A phone-first, installable walkthrough of SHIFT AI that a member can hand to anyone who asks "so what is SHIFT?" It covers the ten studios, what the plans cost, and how the five EcoPay streams work, in about two minutes on a phone, with no income claims.

Every member gets their own copy. In your copy, every button leads to *your* SHIFT invite page. Nobody on the team hosts, installs or maintains anything.

Built and maintained by Pat Jenkins ([@patjenkinsGIT](https://github.com/patjenkinsGIT)), an independent SHIFT member who publishes as Tool Tax. **This is not an official SHIFT product** and is not endorsed by SHIFT AI.

---

## For SHIFT members: get your own copy (1 minute)

1. On your phone, open **https://app.tooltaxhq.com**
2. Scroll to **"Make this app yours"** and type your SHIFT username (the part after `go.shiftai.club/` in your invite link)
3. Tap **Open my copy**, then add it to your home screen:
   - **iPhone (Safari):** Share icon → *Add to Home Screen*
   - **Android (Chrome):** tap *Install* on the banner, or ⋮ → *Install app*
4. Send your link to anyone. The **Share** button inside the app sends it for you.

Your link looks like `https://app.tooltaxhq.com/?ref=yourname`, and you can also type it by hand. Check that `https://go.shiftai.club/yourname` opens your own invite page; if it doesn't, the username is wrong.

Once you open your copy, that phone remembers your username, so it keeps showing your version even at the plain address. To switch back to the default copy, open `https://app.tooltaxhq.com/?ref=tooltaxhq`, or use a private browser tab.

## What a prospect sees

**The platform tab**
- One login and one credit balance across SHIFT's ten studios: Chat, Image, Voice, Avatar, Translate, Video & Reels, Deck, Prospect, Music, Brand Pack
- The $99/month membership: 20,000 credits every month, cancel anytime
- Company facts as SHIFT states them (incorporated in the USA, headquartered in Texas, 193 countries, 135+ currencies)

**The "How it pays" tab**
- The five EcoPay streams (ClubPay, CreditPay, ContentPay, CoachPay, CompetePay) described in SHIFT's own words
- A clear statement that the $99 membership is credits only, and that the streams come with a club membership starting at the Standard Club ($499 one-time, then $99/month)
- No percentages, projections or earnings examples. SHIFT publishes rates with its rewards plan, and this app quotes none of them.
- SHIFT's standard income disclaimer, verbatim

## How it stays accurate

Every product, pricing and stream claim was checked against SHIFT's own pricing, EcoPay, Studio and Opportunity pages on **September 25, 2026**. When SHIFT changes something, the app is updated once here, and every member's installed copy picks up the change the next time it's opened.

Deliberately left out: invitation-only enterprise tiers and their prices, launch-window and Founder's Club promotions, travel vouchers, calculator figures, and anything that reads as an earnings promise.

Found something out of date? [Open an issue](https://github.com/patjenkinsGIT/shiftapp/issues) with a screenshot of the SHIFT page that shows the current version.

## Privacy

The app has no analytics, no cookies, no ads, and no forms that send data anywhere. The only thing it stores is the SHIFT username in a copy's link, kept in your own browser (`localStorage`) so an installed copy remembers whose it is. All code is in this repo; `index.html` is the whole app.

## How attribution works

- `?ref=username` in the URL sets every button to `https://go.shiftai.club/username`, sets the footer to "Shared by username", and makes the Share button send that same personalized link.
- The username is saved on the device, so a prospect who installs a member's copy keeps that member's attribution after the `?ref=` disappears from view.
- The owner-only extras, the "Questions first?" link and the "Make this app yours" builder, appear only on the default copy. A prospect on a member's link never sees them.
- Usernames are validated (letters, numbers, `-` and `_`); anything else is ignored.

---

## Maintaining it (Pat)

**Edit:** everything lives in `index.html`. The `CONFIG` block at the top holds:

| Key | What it does |
|---|---|
| `REFERRAL_LINK` | Default invite link when there's no `?ref=` (`go.shiftai.club/tooltaxhq`) |
| `REF_BASE` | Prefix a username is appended to (`https://go.shiftai.club/`) |
| `SHARED_BY` | Footer name on the default copy |
| `CONTACT_LINK` | "Questions first?" link, default copy only |
| `PRICE_LINE` | Membership price line. Set to `""` to hide. |

**Publish:** bump `CACHE_VERSION` in `sw.js` (for example `v6` → `v7`) so installed copies refresh, then commit and push to `main`. Cloudflare Pages redeploys automatically in about a minute.

**Hosting:** Cloudflare Pages project `shiftapp`, Git-connected to this repo; `app.tooltaxhq.com` is a proxied CNAME to `shiftapp-dmj.pages.dev`. GitHub Pages is also enabled as an unused fallback.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app: markup, CSS and JS inline, no build step, no dependencies |
| `manifest.webmanifest` | Makes it installable (name, icon, full-screen, theme color) |
| `sw.js` | Service worker: caches the app for offline use; network-first for the page so edits show up |
| `icons/` | 192, 512 and 512-maskable PNG icons |
| `.nojekyll` | Keeps GitHub Pages from processing the files |
| `.gitignore` | Keeps macOS `.DS_Store` files out of the repo |

## If it helped you

It's free, no strings. If it saves you time, restamp the **"Free SHIFT walkthrough app"** card in the SHIFT Vault. Your restamped copy carries your own link.
