# H&S Group  /  Website

Prepared by revmedia for H&S Group Inc. A static, SEO-optimized multi-page site built for direct deployment to GitHub Pages, Netlify, or any static host.

## What's inside

* **16 HTML pages** covering home, about, the group overview, 6 company detail pages (HS Construction, H&S Services, Align Interiors, Purus, BlueSky, Waterr), services, industries, leadership, clients, why H&S, careers, and contact.
* **Shared design system** in `assets/css/main.css` (design tokens, components, responsive rules).
* **Shared interactions** in `assets/js/main.js` (sticky nav, mobile menu, scroll reveal, counter animations, form handling, parallax).
* **Full SEO meta**, Open Graph tags, canonical URLs, and JSON-LD on every page.
* **`robots.txt`** and **`sitemap.xml`** included for search engine indexing.
* **Custom SVG favicon** with the H&S lion monogram in brand colors.

## File structure

```
hsgroup/
  index.html
  about/index.html
  group-companies/
    index.html
    hs-construction/index.html
    hs-services/index.html
    align-interiors/index.html
    purus/index.html
    bluesky/index.html
    waterr/index.html
  services/index.html
  industries/index.html
  leadership/index.html
  clients-and-partnerships/index.html
  why-hs/index.html
  careers/index.html
  contact/index.html
  assets/
    css/main.css
    js/main.js
  favicon.svg
  robots.txt
  sitemap.xml
  README.md
```

## Tech approach

* **Static HTML, CSS, vanilla JS.** No build step, no dependencies. Drop the folder onto any static host.
* **Folder-based clean URLs** (`/about/`, `/group-companies/purus/`). Each page is `index.html` inside its folder.
* **Satoshi typeface** via Fontshare CDN. Replaces the paid Neue Haas Grotesk specified in the original brand brief while keeping the premium grotesque character.
* **Premium photography** sourced via Unsplash CDN URLs with size parameters. Swap with client-supplied photography by editing the `src` attributes.
* **Text-based wordmarks** for each group company. Built in HTML/CSS for sharpness at every zoom level. Easy to replace with real SVG logos when supplied by the client (search for `class="company-logo"` to locate insertion points).

## How to deploy

### Option A. GitHub Pages

1. Create a new repository on GitHub.
2. Copy the entire `hsgroup/` directory contents into the repo root.
3. Commit and push to `main`.
4. In repo settings, enable Pages from the `main` branch root.
5. Point the `hsholdings.ca` domain at GitHub Pages via your DNS provider (CNAME record).

### Option B. Netlify or Vercel

1. Connect the repo to Netlify or Vercel.
2. Set the publish directory to the repo root. No build command needed.
3. Deploy. Custom domain via the platform settings.

### Option C. Any static host

Upload the entire folder to any web server. The folder structure handles routing through `index.html` files.

## Brand assets

The H&S Holdings master logo (lion crest wordmark) is bundled locally in `assets/logos/` in transparent PNG form, generated from the official files supplied by the client:

* `hs-logo-white.png` and `hs-logo-navy.png` (full lockup, white and navy)
* `hs-lion-white.png` and `hs-lion-navy.png` (crest only)
* `favicon.png` and `apple-touch-icon.png` (lion crest on navy)

The white logo is used in the navigation bar and footer. The lion crest appears as a subtle watermark in the homepage hero. These are self-hosted and do not depend on any third party.

The six group-company logos (HS Construction, Align, Purus, Stella, BlueSky, Hash) and the client logos still reference the existing Wix CDN. Export and self-host these the same way before fully retiring the Wix site. Search for `wixstatic.com` to find them.

## Pre-launch checklist (client-facing)

* Company and client logos now reference the real brand assets hosted on the existing Wix CDN (static.wixstatic.com). These display correctly in any browser. For full independence from Wix (recommended before fully retiring the old site), export the original logo files from the client and host them locally in an `assets/logos/` folder, then update the `src` attributes. Search for `wixstatic.com` to find every logo reference.
* The three unlabelled client logos (filenames 3.png, 5.png, 7.png, TRANSPARENT.png) were pulled from the existing site. Confirm the final client logo set and ordering with the client before launch.
* Replace leadership photo placeholders with professional headshots. Files are located in `<div class="leader-photo">` blocks. Replace `<div class="leader-photo-placeholder">XX</div>` with `<img src="/path/to/headshot.jpg" alt="Name">`.
* Wire the contact form to a real backend handler (Formspree, Netlify Forms, or custom endpoint). Form submission currently runs a demo client-side success state. The handler is in `assets/js/main.js` under `form[data-form="inquiry"]`.
* Update the OG image meta tag with a real 1200 by 630 social share image once design is approved.
* Validate the site through Google's Rich Results Test for the JSON-LD structured data.
* Submit the sitemap to Google Search Console after launch.

## Editing pages

All secondary pages are regenerated from `build_pages.py` (not included in deployment, kept separately by revmedia). To make content changes after launch, edit the HTML files directly. The structure is consistent across every page so changes are predictable.

## Notes

* No em dashes or double dashes are used anywhere in the site copy, per the brand brief.
* All page copy is verbatim from the strategy document delivered alongside this build.
* The site is accessible (skip links, semantic HTML, ARIA labels on interactive elements, reduced-motion support, sufficient contrast).
* Performance is strong out of the box (no JS framework, lazy-loaded images, preconnect hints, minimal CSS payload).

Prepared by revmedia. info@revmedia.ca
