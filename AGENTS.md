# Moth & Marigold — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/florist-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:navigation`: `.nav__menu` `.menu__close` `.menu__links`
  - `section-script:opening`: `.op__hold`
  - `scene:dusk`: `.op__night` `.op__photo` `.op__w--1` `.op__w--2` `.op__and` `.op__statement` `.op__ribbon`
  - `scene:bench`: `.bench__ph` `.bench__row` `.bench__name` `.bench__rows`
  - `scene:drift`: `.work__grid` `.work__item`
  - `scene:hours`: `.dusk__run` `.dusk__stage` `.dusk__track` `.dusk__panel` `.dusk__hour` `.dusk__ph`
  - `scene:gather`: `.ev__board` `.ev__ph`
  - `scene:miles`: `.gr__row` `.gr__rows` `.gr__pin` `.gr__line`
  - `section-script:contact`: `.ct__form` `.ct__done`
  - `scene:letter`: `.nt__frame` `.nt__letter`
  - `scene:card`: `.ct__card` `.ct__room`
  - `scene:mark`: `.ft__mark` `.ft__rect` `.ft__dome` `.ft__bar`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- A display line with `style="--len:N"` is sized to fill its width: N is its number of characters, spaces included (`Moth and Marigold` → 17, `after five` → 10).
- Keep the header comment and `<meta name="generator">`; the "Design: 8B" footer link is optional.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, social, email, form); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Order for tonight buttons in the nav, the phone menu and the first screen: link to #contact now; point them to your online shop or order page URL (or keep the order form in contact).
- Build a bouquet from the bench (under the stem list): link to #contact now; point them to your shop's product page or order form URL.
- Start the Jar / Start the Mantel / Ask about the Lobby in standing orders: link to #contact now; point them to the sign-up or subscription checkout URL of each order.
- Plan an event buttons (first screen and events): link to #events and #contact now; point them to your event enquiry form or booking URL.
- Save a seat in the workshops section: link to #contact now; point them to your workshop booking or ticket URL.
- See every arrangement (row link under arrangements) and Instagram in the footer: link to https://www.instagram.com/ now; point them to your Instagram profile or portfolio URL.
- **The form sends nothing.** `section-script:contact` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Address and city: "418 Whitaker Street, Savannah, GA 31401" (phone menu, contact, footer), "Whitaker Street" (opening statement and closing line, on the bench intro, dusk delivery "The last cut", growers scale), Savannah in the title, meta description and "© 2026 Moth & Marigold, Savannah" (footer).
  - Opening hours: "Tue–Sat, 11 am to 9 pm" (phone menu, contact, footer); collection "any time from eleven to nine", ready "an hour after you place them" (FAQ).
  - Phone (912) 000-0000 and emails orders@ / marigold@mothandmarigold.example (menu, notes, contact, footer) — placeholders.
  - Delivery window and rules: delivered between five and nine (opening taglines, dusk heading, standing orders footnote, meta description); order by three in the afternoon, Tuesday to Saturday (dusk intro, FAQ); "we text ten minutes ahead", flowers left in the shade with water (dusk); "two vans, eleven neighbourhoods", Midtown first, islands last (dusk); the islands on Fridays (standing orders, FAQ); delivery $12, free on standing orders (FAQ); the neighbourhoods Historic District, Ardsley Park, Thunderbolt, the Southside, Tybee (FAQ).
  - Sourcing claims: "grown within two hundred miles" (opening, growers heading, meta description), "nothing flies in" (growers), growers' trucks every Tuesday (on the bench intro), foraging "with permission" on the Isle of Hope (growers).
  - Grower names, towns and distances: Ogeechee Flower Co., Richmond Hill, 22 mi; Bluff Road Farm, Ridgeland, 38 mi; Three Pines Growers, Statesboro, 64 mi; Sand Hill Nursery, Aiken, 128 mi; Ocmulgee River Farm, Macon, 168 mi; Isle of Hope, 9 mi; our own beds, 0 mi (on the bench, growers). They are invented names that may match real farms.
  - Stem prices: $6, $3, $5, $8 a branch, $7 and $6 a length (on the bench).
  - Standing orders: The Jar $45 a week, twelve to fifteen stems, weekly or every other week, jar refills; The Mantel $85 a week; The Lobby from $240 a week, twice a week, vessels on loan; Tuesday or Friday; skip or pause with a text (standing orders).
  - Events: weddings from $4,500, six months ahead; dinners and openings from $1,200, three weeks ahead; installations quoted after a site visit (events); six months for April to June and October, three months otherwise, at most two weddings a weekend (FAQ); build on site, strike after the last guest, compost (events).
  - Clients and past work: "The Mercer dinner" (forty feet of table, Jones Street, September), a kitchen in Ardsley Park ("every Friday since 2023"), "The Collins wedding" (twelve bouquets, Tybee Island, May), "The Drayton lobby" (twice a week, Drayton Street), a mantel in Gordonston (December), a memorial on the Isle of Hope (March) (arrangements).
  - Workshops: Thursdays, eight seats, two hours, "a glass of something cold"; dates Thu 15 Oct, 22 Oct, 5 Nov, 19 Nov (2026 in the datetime attributes), prices $85, $95, $110, $90, seats left 3, 5, 8, 6 (night school).
  - Care column: post dates "3 October", "19 September", "5 September", the reader "Wilting, in Thunderbolt", the signature "Marigold" (notes).
  - Promises and methods: "one pair of hands makes each order", "never cellophane, never foam", cards written in ink (dusk delivery); no floral foam, everything reused or composted (FAQ); flowers last five to ten days, a care card with every order (FAQ); sympathy flowers the same day (FAQ); "a person answers" the phone (FAQ); "we'll call before five" (contact form thank-you message).
  - Budget options $60, $90, $150 in the contact form.
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The brand marks in the nav and the footer are drawn from simple shapes (an inline SVG and three CSS blocks), not images: recolour them through the CSS variables, or replace them with your logo.
- Without JavaScript the phone menu button cannot open the overlay; the links stay reachable in the footer.
- Long words in the width-filling wordmark need the --len value updated, or the line overflows or looks small.

## Common edits
- Rebrand: search the old name (`Moth & Marigold`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
