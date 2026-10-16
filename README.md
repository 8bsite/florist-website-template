# Free HTML florist website template with GSAP scroll animations — Moth & Marigold

**Website for a florist or flower shop with delivery, standing orders, events and workshops: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/florist-website-template/)** · **[Use this template](https://github.com/new?template_name=florist-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/florist-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/florist-website-template/"><img src="previews/desktop.png" alt="Moth & Marigold, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/florist-website-template/"><img src="previews/phone.png" alt="Moth & Marigold, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/florist-website-template/"><img src="previews/scroll.gif" alt="Moth & Marigold, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for an evening-delivery flower shop: stems of the week, arrangements, delivery, weekly orders, events, growers, workshops, a care column and an order form. Blush and chocolate grounds with hot-pink script lines; the night rises over the first screen as a dome, the delivery hours slide past on a track that darkens from blush to chocolate, and event photos gather from a loose pile into a board.

Good for: florist or flower shop; flower delivery or subscription service; wedding and event florist; flower farm or farm stand that sells direct; any small shop with weekly stock, a delivery window and workshops. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a florist or flower shop site for <your business: name, town, what you sell, how and when you deliver, prices, events or workshops if any>. Keep the layout, the motion and the single-file format; replace the brand name, copy, photos, prices, dates, growers, links and contacts, remove sections you do not need, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=florist-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — top bar: brand mark and name, section links, Order for tonight button; phone menu overlay with address, hours and phone
- **Moth and Marigold** — first screen: width-filling brand wordmark, two taglines, two actions and a shop photo; then a dark statement screen (demo: "after five")
- **What the fields sent** — this week's stock: six items with source, distance and price, beside one held photo frame (demo: flower stems)
- **Flowers that moved in** — portfolio grid of six arrangements, each with a title and a place/month caption
- **Cut at five, at your door by nine** — how delivery works: five hour panels (5 pm to 9 pm) on a horizontal track, each a shade darker
- **The same evening, every week** — price list of three weekly subscriptions as table rows (demo: The Jar, The Mantel, The Lobby)
- **Big flowers for long tables** — event services with prices and lead times, a button, and a board of six event photos
- **Grown within two hundred miles** — suppliers placed on a 0 to 200 mile scale by distance (demo: seven flower growers)
- **Two hours at the bench after closing** — workshops: four dated classes with price and seats left, a booking button and one photo (demo: Thursday night school)
- **Dear Marigold** — journal or blog: one featured post beside a tall photo, two shorter posts (demo: "Dear Marigold" care column)
- **Before you order** — questions and answers (native &lt;details&gt;)
- **Tell us who they're for** — order form on a card over a shop photo, with address, hours, phone and email
- **Footer** — large brand mark built from three blocks, link columns, address and contacts, copyright and the Design: 8B credit

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, social, email, form) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place. A big display line with `style="--len:N"` fills its width: set N to its new number of characters.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, Lenis 1.3.4 from jsDelivr. No build step, no framework, no npm. 100 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 111+, Safari 16.2+, Firefox 113+ (it uses color-mix(), container query units, cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
