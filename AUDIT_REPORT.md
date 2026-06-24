# Full Site Audit Report — pinjamanmuhibbah.com
**Date:** 2026-06-24  
**Auditor:** Claude Sonnet 4.6 (Senior Full-Stack / SEO)  
**Scope:** Code, SEO, UX, Accessibility, Security, Performance

---

## 1. Repository Overview

| File | Size | Notes |
|---|---|---|
| index.html | 38 KB | Main homepage |
| landing.html | 21 KB | Campaign page 1 |
| landing2.html | 21 KB | Campaign page 2 |
| semak.html | 30 KB | Eligibility calculator |
| semak2.html | 31 KB | Eligibility calculator (alt) |
| semak3.html | 22 KB | Application form |
| mohon.html | 22 KB | Application form (alt) |
| privasi.html | 6 KB | Privacy policy |
| terms.html | 5 KB | Terms & conditions |
| unsubscribe.html | 17 KB | Email unsubscribe |
| logo.png | 24 KB | OK |
| main.png | **1.4 MB** | Not compressed |
| header3.png | **3.2 MB** | Unreferenced anywhere — wasted space |
| unsubscribe.htmlo | 17 KB | Stray backup file — should not exist |

---

## 2. Code Issues

### 2.1 Invalid CSS — `index.html` line 182
```css
.feature-box { padding: rem; }
```
`rem` alone is not a valid CSS value. Browsers silently ignore it, leaving zero padding on feature boxes.  
**Fix:** Change to `padding: 1rem;`

### 2.2 Rogue `<style>` block outside `<head>` — `semak3.html` & `mohon.html`
Both pages have this invalid block between `</head>` and `<body>`:
```html
</head>
<style>
  body { font-size: 12px; line-height: 1; }
</style>
<body>
```
Problems:
- `<style>` must be inside `<head>`. Placing it between `</head>` and `<body>` is invalid HTML.
- `line-height: 1` overrides the correct `line-height: 1.6` defined inside `<head>`, causing text lines to collapse — a WCAG 1.4.12 violation.
- `font-size: 12px` is below the WCAG 1.4.4 comfort threshold for body text.  
**Fix:** Remove the rogue block entirely. Proper body styles already exist in `<head>`.

### 2.3 Duplicate back-to-top buttons — `index.html`
Two overlapping fixed-position elements both anchored to bottom-right:
- `.floating-back` (`← Back to Top`) at line 401 — no aria-label, always visible
- `.back-to-top` (icon button) at line 814 — has `aria-label="Kembali ke atas"`, shows only after 300px scroll

Both have `z-index: 9999` and physically overlap on all screen sizes.  
**Fix:** Remove the `.floating-back` element and its CSS block from `index.html`. The `.back-to-top` is the correct implementation.

### 2.4 Stray backup file — `unsubscribe.htmlo`
A 17 KB file named `unsubscribe.htmlo` exists in the repo root. Not referenced anywhere. Likely an accidental editor backup.  
**Fix:** Delete the file.

### 2.5 `lang` attribute inconsistency
`index.html` uses `lang="ms-MY"` (correct BCP 47 tag for Malay/Malaysia). All other 9 HTML files use `lang="ms"`.  
**Fix:** Standardise all pages to `lang="ms-MY"`.

---

## 3. SEO Issues

### 3.1 Missing Open Graph tags — `privasi.html` & `terms.html`
Both pages have `<title>` and `<meta name="description">` but are completely missing all `og:*` tags. When these URLs are shared on WhatsApp or social media, no preview card appears.  
**Fix:** Add full OG tag set to both pages.

### 3.2 Missing `<meta name="keywords">` — `privasi.html` & `terms.html`
**Fix:** Add keywords meta tag consistent with other pages.

### 3.3 `www` URL inconsistency in footer — `semak3.html` & `mohon.html`
```html
<a href="https://www.pinjamanmuhibbah.com">www.pinjamanmuhibbah.com</a>
```
The canonical URL is `https://pinjamanmuhibbah.com` (no www). Using `www.` causes an extra redirect and signals to Google a secondary origin.  
**Fix:** Change to `https://pinjamanmuhibbah.com`.

### 3.4 Orphaned pages — `landing.html`, `landing2.html`, `mohon.html`, `semak3.html`
These four pages have zero inbound internal links from the homepage or navigation. Google discovery relies on crawling links; orphaned pages rank poorly even after sitemap submission.  
**Fix:** Add links to `mohon.html` / `semak3.html` in the homepage footer. Note: landing pages are intentionally campaign-only (not for organic).

### 3.5 Footer missing legal links — `landing.html`, `landing2.html`
Both campaign page footers show only company name and copyright. No link to Privacy Policy or Terms — this is also a PDPA best-practice requirement.  
**Fix:** Add links to `privasi.html` and `terms.html` in both footers.

### 3.6 `semak.html` & `semak2.html` footers — missing Terms link
Footer only links to `privasi.html`.  
**Fix:** Add `terms.html` link.

---

## 4. Accessibility Issues (WCAG 2.1)

### 4.1 Form labels not connected to inputs — `semak.html`, `semak2.html`, `semak3.html`, `mohon.html`
All four form pages have `<label>` elements with no `for` attribute and `<input>` elements with no `id`. Screen readers cannot associate the label with its input, failing WCAG 1.3.1.
```html
<!-- Broken -->
<label>Nama Penuh <span>*</span></label>
<input type="text" name="nama" required>

<!-- Fixed -->
<label for="f-nama">Nama Penuh <span>*</span></label>
<input id="f-nama" type="text" name="nama" required>
```
**WCAG:** 1.3.1 Info and Relationships (Level A)

### 4.2 `line-height: 1` override — `semak3.html` & `mohon.html`
Covered in §2.2. Violates WCAG 1.4.12 Text Spacing (Level AA).

### 4.3 `javascript:history.back()` on Back buttons
Used in `semak2.html`, `privasi.html`, `terms.html`. If user arrives directly from Google (empty history), this silently fails or navigates off-site.  
**Recommendation (manual):** Change legal pages to `href="index.html"`.

---

## 5. Performance Issues

### 5.1 Hero image uncompressed — `main.png` (1.4 MB)
The hero image weighs 1.4 MB. A WebP equivalent should be under 100 KB. This is the single biggest Core Web Vitals LCP issue on the site.  
**Fix (manual):** Compress via Squoosh.app and convert to WebP. Cannot be automated without the original source image.

### 5.2 No `<link rel="preload">` for LCP image
`main.png` is the LCP element but has no browser preload hint.  
**Fix (auto):** Add `<link rel="preload" as="image" href="main.png">` to `index.html`.

### 5.3 Unreferenced 3.2 MB image — `header3.png`
Not referenced in any HTML file. Wasting 3.2 MB of repository storage.  
**Fix (manual):** Delete after confirming it's not used by any external system.

### 5.4 FontAwesome full CSS on every page (~80 KB gzipped)
Only a handful of icons are used per page, but the entire FontAwesome library is loaded.  
**Recommendation (manual):** Use Font Awesome Kit or inline only the SVG icons needed per page.

---

## 6. Security Issues

### 6.1 Google Apps Script URLs exposed in client-side JS
The GAS endpoints are visible in page source. This is unavoidable for a static site. Honeypot fields and PDPA consent partially mitigate spam.  
**Recommendation:** Implement rate limiting and duplicate-submission detection in the GAS script.

### 6.2 No Content-Security-Policy (CSP) headers
Cannot be set via static HTML alone on GitHub Pages.  
**Recommendation (manual):** Add Cloudflare in front of the site to inject security headers.

### 6.3 Mixed external link targets
Any future `target="_blank"` links should carry `rel="noopener noreferrer"`. Current external links in semak3.html/mohon.html already have this.

---

## 7. JavaScript Issues

### 7.1 `response.json()` called on Google Apps Script redirect response
In `semak3.html` and `mohon.html`, the form submit handler calls `response.json()` on a response that may be a redirect (GAS commonly redirects). The try/catch wrapping handles this gracefully, so it works in practice.  
**Status:** Low risk, documented.

### 7.2 `landing.html`/`landing2.html` WhatsApp message builder
Previously `jabatan` field had a mismatched `id`. Fixed in prior commit. Verified working.

---

## 8. Forms & WhatsApp Audit

| Page | Form Submits | Honeypot | PDPA Consent | WhatsApp |
|---|---|---|---|---|
| semak.html | GAS ✓ | — | ✓ | — |
| semak2.html | GAS ✓ | — | ✓ | — |
| semak3.html | GAS ✓ | ✓ | ✓ | 60390540707 ✓ |
| mohon.html | GAS ✓ | ✓ | ✓ | 60390540707 ✓ |
| landing.html | GAS ✓ | ✓ | ✓ | 60390540707 ✓ |
| landing2.html | GAS ✓ | ✓ | ✓ | 60390540707 ✓ |

All WhatsApp numbers consistent. All forms functional.

---

## 9. Mobile Responsiveness

All 10 pages have `<meta name="viewport" content="width=device-width, initial-scale=1.0">` and appropriate responsive breakpoints via Bootstrap or custom CSS media queries. No mobile issues found.

---

## 10. Google Indexing Readiness

| Check | Status |
|---|---|
| sitemap.xml | Submitted |
| robots.txt | Correct |
| Canonical URLs | All pages |
| noindex | Only unsubscribe.html |
| JSON-LD schema | index, semak, semak2, semak3, mohon |
| OG tags | All pages (privasi/terms fixed in this audit) |
| Currently indexed | 2/10 (sitemap newly submitted — wait 7–14 days) |

---

## Summary

| Category | Issues Found | Auto-Fixed | Manual Required |
|---|---|---|---|
| Code | 5 | 4 | 1 (header3.png deletion) |
| SEO | 6 | 5 | 1 (image compression) |
| Accessibility | 3 | 2 | 1 (history.back on legal pages) |
| Performance | 4 | 1 | 3 |
| Security | 3 | 0 | 3 |
| **Total** | **21** | **12** | **9** |
