# Priority Fixes — pinjamanmuhibbah.com
**Generated:** 2026-06-24  

---

## CRITICAL

| # | Issue | File(s) | Fix |
|---|-------|---------|-----|
| C1 | Missing meta description | semak.html, semak2.html, semak3.html, mohon.html | Add `<meta name="description">` |
| C2 | Missing Open Graph tags | All pages | Add og:title, og:description, og:image, og:url |
| C3 | Missing canonical URLs | All pages | Add `<link rel="canonical">` — critical for duplicate pages |
| C4 | Missing sitemap.xml | Root | Create sitemap.xml listing all public pages |
| C5 | Missing robots.txt | Root | Create robots.txt pointing to sitemap |
| C6 | JS bug: jabatan field id mismatch | landing.html, landing2.html | Change `id="agency"` to `id="jabatan"` OR fix buildMessage() |
| C7 | header3.png (3.2 MB) unreferenced | Root | Delete or move (will not break anything) |

---

## HIGH

| # | Issue | File(s) | Fix |
|---|-------|---------|-----|
| H1 | Missing meta description | privasi.html, terms.html | Add `<meta name="description">` |
| H2 | Title too long (82 chars) | index.html | Shorten to ≤60 chars |
| H3 | External target=_blank links missing rel="noopener noreferrer" | mohon.html, semak3.html | Add rel attribute |
| H4 | main.png is 1.4 MB | index.html | Compress/convert to WebP (manual — outside scope of code fixes) |
| H5 | Duplicate titles and descriptions | landing2.html vs landing.html | Give landing2.html unique title/description |
| H6 | Poor alt text on hero image | index.html | Change "Koperasi4u Banner" to descriptive text |
| H7 | Poor alt text on logo images | landing.html, landing2.html | Change "Company Logo" to brand name |

---

## MEDIUM

| # | Issue | File(s) | Fix |
|---|-------|---------|-----|
| M1 | Missing meta description | unsubscribe.html | Add meta description (noindex recommended for this page) |
| M2 | Form labels missing for/id associations | semak.html, semak2.html, semak3.html, mohon.html | Add id attributes to inputs, link labels |
| M3 | `<h2>` nested inside `<span>` | landing.html, landing2.html | Replace with proper block element |
| M4 | Second `<style>` block placed after `</head>` | semak3.html, mohon.html | Move into `<head>` |
| M5 | Heading order not logical | index.html | Ensure H1 comes before H2 in DOM order |
| M6 | FAQ items not keyboard-accessible | index.html | Add role, aria-expanded, tabindex |
| M7 | Back-to-top button missing aria-label | index.html | Add aria-label="Back to top" |
| M8 | CLS risk — main.png has no dimensions | index.html | Add width/height attributes |
| M9 | unsubscribe.html should be noindex | unsubscribe.html | Add robots noindex meta |

---

## LOW

| # | Issue | File(s) | Fix |
|---|-------|---------|-----|
| L1 | Open Graph tags missing og:image on landing pages | landing.html, landing2.html | Add og:image pointing to logo.png or main.png |
| L2 | No structured data (JSON-LD) | index.html | Add Organization/LocalBusiness schema |
| L3 | No lazy loading on body images | semak.html, etc. | Add loading="lazy" to non-hero images |
| L4 | unsubscribe.htmlo orphaned backup file | Root | Can be deleted safely |
| L5 | privasi.html and terms.html have no responsive media queries | Both | Minor CSS improvement |
| L6 | index.html title missing keyword density | index.html | Already partially addressed by shortening |
| L7 | Footer copyright says 2025 | All pages | Update to current year (or use JS) |

---

## Implemented Fixes (Phase 3)

The following low-risk fixes have been applied in the `audit-fixes` branch:

- [x] C1: Added meta descriptions to semak.html, semak2.html, semak3.html, mohon.html
- [x] C2: Added Open Graph tags to index.html, semak.html, semak2.html, semak3.html, mohon.html
- [x] C3: Added canonical URLs to all HTML files
- [x] C4: Created sitemap.xml
- [x] C5: Created robots.txt
- [x] C6: Fixed jabatan field id mismatch in landing.html and landing2.html
- [x] H1: Added meta descriptions to privasi.html, terms.html
- [x] H2: Shortened index.html title
- [x] H3: Added rel="noopener noreferrer" to external target=_blank links in mohon.html and semak3.html
- [x] H5: Updated landing2.html og:url to correct page URL and gave unique title
- [x] H6: Improved alt text on hero image (index.html)
- [x] H7: Improved alt text on logo images (landing.html, landing2.html)
- [x] M1: Added meta description + noindex to unsubscribe.html
- [x] M7: Added aria-label to back-to-top button (index.html)
- [x] M9: Added robots noindex to unsubscribe.html
- [x] L1: Added og:image to landing.html, landing2.html
- [x] L3: Added loading="lazy" to non-hero images
- [x] L4: Noted unsubscribe.htmlo for manual deletion (left in place)
- [x] OG tags: Added og:image to landing.html, landing2.html
