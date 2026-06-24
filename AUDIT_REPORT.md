# Audit Report — pinjamanmuhibbah.com
**Date:** 2026-06-24  
**Auditor:** Claude Code (automated full-stack + SEO audit)  
**Repository:** C:\Users\User\muhibbah  
**Live site:** https://pinjamanmuhibbah.com  

---

## 1. Repository Structure

| File | Size | Purpose |
|------|------|---------|
| index.html | 34 KB | Main landing / home page |
| landing.html | 20 KB | Campaign landing page (campaign1) |
| landing2.html | 20 KB | Campaign landing page (campaign2) — identical to landing.html except source field |
| semak.html | 29 KB | Loan eligibility calculator + lead form |
| semak2.html | 29 KB | Near-duplicate of semak.html (slightly different form labels) |
| semak3.html | 24 KB | Alternative application page (Poppins font, different layout) |
| mohon.html | 20 KB | Application page (same as semak3.html content) |
| privasi.html | 5.8 KB | Privacy policy |
| terms.html | 4.9 KB | Terms & Conditions |
| unsubscribe.html | 16 KB | Email unsubscribe handler |
| unsubscribe.htmlo | 13 KB | Old/backup version of unsubscribe (not served) |
| logo.png | 24 KB | Company logo |
| main.png | 1.4 MB | Hero banner image (LARGE) |
| header3.png | 3.2 MB | Image file (VERY LARGE — not referenced anywhere) |
| CNAME | 20 B | GitHub Pages CNAME: pinjamanmuhibbah.com |

---

## 2. SEO Issues

### 2.1 Title Tags
| File | Title | Length | Status |
|------|-------|--------|--------|
| index.html | Muhibbah Alliance Capital - Pembiayaan Koperasi untuk Kakitangan Kerajaan Malaysia | 82 chars | TOO LONG (>60) |
| landing.html | Pinjaman Koperasi Penjawat Awam \| Muhibbah Alliance Capital | 59 chars | OK |
| landing2.html | Pinjaman Koperasi Penjawat Awam \| Muhibbah Alliance Capital | 59 chars | DUPLICATE of landing.html |
| semak.html | Semak Kelayakan Pinjaman Koperasi | 34 chars | Short/no brand |
| semak2.html | Semak Kelayakan Pinjaman Koperasi | 34 chars | DUPLICATE of semak.html |
| semak3.html | Pinjaman Koperasi - Muhibbah Alliance Capital | 46 chars | OK |
| mohon.html | Pinjaman Koperasi - Muhibbah Alliance Capital | 46 chars | DUPLICATE of semak3.html |
| privasi.html | Polisi Privasi \| Muhibbah Alliance Capital Sdn Bhd | 50 chars | OK |
| terms.html | Terma & Syarat - Muhibbah Alliance Capital | 43 chars | Acceptable |
| unsubscribe.html | Berhenti Langgan \| pinjamanmuhibbah.com | 40 chars | Acceptable |

### 2.2 Meta Descriptions
| File | Description Present | Status |
|------|---------------------|--------|
| index.html | Yes | OK (161 chars — slightly long) |
| landing.html | Yes | OK |
| landing2.html | Yes | DUPLICATE of landing.html |
| semak.html | **MISSING** | CRITICAL |
| semak2.html | **MISSING** | CRITICAL |
| semak3.html | **MISSING** | CRITICAL |
| mohon.html | **MISSING** | CRITICAL |
| privasi.html | **MISSING** | HIGH |
| terms.html | **MISSING** | HIGH |
| unsubscribe.html | **MISSING** | MEDIUM |

### 2.3 Open Graph (OG) Tags
| File | og:title | og:description | og:image | og:url | Status |
|------|----------|----------------|----------|--------|--------|
| index.html | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| landing.html | Present | Present | MISSING | Present | Partial |
| landing2.html | Present | Present | MISSING | Present (wrong URL) | Partial |
| semak.html | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| semak2.html | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| semak3.html | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| mohon.html | MISSING | MISSING | MISSING | MISSING | CRITICAL |
| privasi.html | MISSING | MISSING | MISSING | MISSING | LOW |
| terms.html | MISSING | MISSING | MISSING | MISSING | LOW |
| unsubscribe.html | MISSING | MISSING | MISSING | MISSING | LOW |

**Note:** landing2.html has `og:url` pointing to `https://pinjamanmuhibbah.com/` (same as landing.html) — should be `.../landing2.html`.

### 2.4 Canonical URLs
**ALL files are missing `<link rel="canonical">` tags.** This is a significant SEO issue, particularly since semak.html and semak2.html are near-duplicates, and mohon.html and semak3.html are near-duplicates.

### 2.5 Sitemap & Robots
- **sitemap.xml: MISSING** — no sitemap exists at the root
- **robots.txt: MISSING** — no robots.txt exists at the root

---

## 3. Accessibility Issues

### 3.1 Image Alt Attributes
| File | Image | Alt Text | Status |
|------|-------|----------|--------|
| index.html | logo.png (navbar) | "Muhibbah Alliance Capital Logo" | OK |
| index.html | main.png (hero) | "Koperasi4u Banner" | POOR (misleading brand) |
| index.html | logo.png (about section) | "Muhibbah Alliance Capital Logo" | OK |
| landing.html | logo.png | "Company Logo" | POOR (not descriptive) |
| landing2.html | logo.png | "Company Logo" | POOR (not descriptive) |
| semak.html | logo.png | "Muhibbah Alliance Capital Logo" | OK |
| semak2.html | logo.png | "Muhibbah Alliance Capital Logo" | OK |
| semak3.html | logo.png | "Muhibbah Alliance Capital Logo" | OK |
| mohon.html | logo.png | "Muhibbah Alliance Capital Logo" | OK |
| privasi.html | logo.png | "Muhibbah Alliance Capital Logo" | OK |

### 3.2 Form Accessibility
- semak.html / semak2.html: Form inputs for "Nama Penuh" and "No. Telefon" have `<label>` but no `for` attribute linked to the input's `id`. The inputs themselves lack `id` attributes.
- semak3.html / mohon.html: All label/input pairs lack explicit `for`/`id` associations.
- landing.html / landing2.html: `id="agency"` but `name="jabatan"` inconsistency — label references `for="jabatan"` while input has `id="agency"`.

### 3.3 Heading Hierarchy
- index.html: Has H1 inside the body section (line 530) but it appears after H2 elements — heading order is not logical.
- semak3.html / mohon.html: Has a second `<style>` block after `</head>` (CSS placed in body) — bad practice.
- landing.html / landing2.html: `<h2>` used inside a `<span>` element — invalid HTML nesting.

### 3.4 Missing ARIA / Role Attributes
- FAQ toggle in index.html uses div elements with click handlers but no ARIA `role="button"`, `aria-expanded`, or keyboard navigation.
- Back-to-top button has no `aria-label`.

---

## 4. Performance Issues

### 4.1 Image Size
| Image | Size | Status |
|-------|------|--------|
| header3.png | **3.2 MB** | CRITICAL — not referenced anywhere (waste) |
| main.png | **1.4 MB** | HIGH — hero image should be compressed/WebP |
| logo.png | 24 KB | Acceptable |

### 4.2 Missing Lazy Loading
- `<img src="main.png">` in index.html: No `loading="lazy"` (though as hero image it should be `loading="eager"`, but the logo images in other pages should have lazy loading).
- Logo images in semak.html, semak2.html, etc., loaded eagerly without specification.

### 4.3 Render-Blocking Resources
- index.html loads Bootstrap CSS and Font Awesome CSS synchronously in `<head>` — standard but could use `preload`.
- landing.html / landing2.html load Google Fonts with `preconnect` links — good practice.

### 4.4 No Image Dimensions Specified
- main.png in index.html: No explicit width/height causes layout shift (CLS).

---

## 5. Security Issues

### 5.1 External Links Without rel="noopener noreferrer"
- mohon.html line 587: `<a href="https://wa.me/60390540707" target="_blank">` — missing `rel="noopener noreferrer"`
- semak3.html line 587: Same issue
- mohon.html line 448: `<a href="https://pinjamanmuhibbah.com" target="_blank">` — missing rel attribute
- semak3.html line 448: Same issue
- landing.html line 129: Back button uses full https URL — OK (not target=_blank)

### 5.2 Exposed Google Apps Script URLs
- All form pages expose Google Apps Script URLs in JavaScript. These are public APIs, but worth noting.
- No credentials or private keys exposed.

### 5.3 Mixed Content
- Site is HTTPS. All external resources use HTTPS. No mixed content issues found.

---

## 6. Broken Links & Missing Files

### 6.1 Internal Link Audit
- index.html → semak.html: OK (file exists)
- index.html → privasi.html: OK
- index.html → terms.html: OK
- semak.html → privasi.html: OK
- privasi.html → index.html: OK
- terms.html → index.html: OK

### 6.2 Missing Files Referenced
- No broken internal file references found.

### 6.3 Unused Files
- `header3.png` (3.2 MB): Referenced **NOWHERE** in any HTML file — orphaned file.
- `unsubscribe.htmlo` (13 KB): Backup/old file with `.htmlo` extension — not served as HTML, can be removed.

---

## 7. JavaScript Issues

### 7.1 Potential Issues
- landing.html / landing2.html: `document.getElementById('jabatan')` referenced in `buildMessage()` function (line 372), but the input field has `id="agency"` not `id="jabatan"` — this will always return null and produce "undefined" in WhatsApp messages.
- semak.html / semak2.html: `error.querySelector('div')` used to update error message — if `.message.error` div structure changes, this breaks.

### 7.2 No Syntax Errors
All JavaScript appears syntactically valid.

---

## 8. WhatsApp Links

| File | WA Number | Format | Status |
|------|-----------|--------|--------|
| mohon.html | 60390540707 | `https://wa.me/60390540707` | OK |
| semak3.html | 60390540707 | `https://wa.me/60390540707` | OK |
| landing.html | 60390540707 | `https://wa.me/${WHATSAPP_NUMBER}?text=...` | OK |
| landing2.html | 60390540707 | `https://wa.me/${WHATSAPP_NUMBER}?text=...` | OK |

All WhatsApp numbers are consistent (60390540707 = +603 9054 0101).

---

## 9. Mobile Responsiveness

| File | Viewport Meta | Responsive CSS | Media Queries | Status |
|------|---------------|----------------|---------------|--------|
| index.html | Yes | Yes (Bootstrap + custom) | Yes | OK |
| landing.html | Yes | Yes (custom grid) | Yes (max-width:920px) | OK |
| landing2.html | Yes | Yes | Yes | OK |
| semak.html | Yes | Yes | Yes (max-width:1000px, 768px) | OK |
| semak2.html | Yes | Yes | Yes | OK |
| semak3.html | Yes | Yes | Yes (992px, 768px, 480px) | OK |
| mohon.html | Yes | Yes | Yes | OK |
| privasi.html | Yes | Partial (no responsive grid) | None | MEDIUM |
| terms.html | Yes | Partial | None | MEDIUM |
| unsubscribe.html | Yes | Yes | Yes (max-width:480px) | OK |

---

## 10. Google Indexing Readiness

- No `<meta name="robots" content="noindex">` tags found — all pages are indexable.
- No structured data (JSON-LD) present on any page — missed opportunity for rich results.
- Canonical URLs missing — Google may pick wrong canonical for duplicate pages (semak/semak2, mohon/semak3).
- No sitemap.xml — Googlebot has no guided crawl map.
- No robots.txt — Googlebot receives no crawl directives.

---

## 11. Duplicate Content Risk

HIGH RISK: The following pairs are near-identical:
1. **landing.html vs landing2.html** — identical except `source` hidden field value (campaign1 vs campaign2)
2. **semak.html vs semak2.html** — nearly identical layout and form
3. **mohon.html vs semak3.html** — identical content

Without canonical tags, Google may penalise these as duplicate content.
