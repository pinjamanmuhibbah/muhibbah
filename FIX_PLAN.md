# Fix Plan — pinjamanmuhibbah.com
**Generated:** 2026-06-24

---

## AUTO-IMPLEMENTED (Safe Fixes)

### [CODE-1] Fix invalid CSS `padding: rem` — `index.html`
- **File:** `index.html` line 182
- **Change:** `padding: rem;` → `padding: 1rem;`
- **Risk:** Zero — purely additive CSS fix

### [CODE-2] Remove rogue `<style>` outside `<head>` — `semak3.html` & `mohon.html`
- **Files:** `semak3.html`, `mohon.html` lines 463–468
- **Change:** Delete the 6-line `<style>` block that overrides body to `font-size:12px; line-height:1`
- **Risk:** Zero — proper body styles already exist inside `<head>`. This block was overriding them incorrectly.

### [CODE-3] Remove duplicate back-to-top button — `index.html`
- **File:** `index.html`
- **Change:** Remove the `.floating-back` CSS block (~18 lines) and its HTML element (`<a href="#" class="floating-back">`)
- **Risk:** Zero — `.back-to-top` button (with aria-label + scroll behaviour) replaces this cleanly

### [CODE-4] Standardise `lang="ms-MY"` — all HTML pages
- **Files:** landing.html, landing2.html, semak.html, semak2.html, semak3.html, mohon.html, privasi.html, terms.html
- **Change:** `lang="ms"` → `lang="ms-MY"`
- **Risk:** Zero — BCP 47 correctness fix

### [CODE-5] Delete stray backup file `unsubscribe.htmlo`
- **Change:** `git rm unsubscribe.htmlo`
- **Risk:** Zero — file is unreferenced

### [SEO-1] Add OG tags to `privasi.html` & `terms.html`
- **Change:** Add `og:title`, `og:description`, `og:image`, `og:url`, `og:type`, `og:site_name`
- **Risk:** Zero — additive only

### [SEO-2] Add `<meta name="keywords">` to `privasi.html` & `terms.html`
- **Risk:** Zero — additive only

### [SEO-3] Fix `www.pinjamanmuhibbah.com` → `pinjamanmuhibbah.com` — `semak3.html` & `mohon.html`
- **Risk:** Zero — URL consistency fix

### [SEO-4] Add `mohon.html` / `semak3.html` links to homepage footer
- **File:** `index.html` footer Quick Links section
- **Risk:** Low — additive internal links

### [SEO-5] Add Privacy & Terms links to `landing.html`, `landing2.html` footers
- **Risk:** Zero — additive only

### [SEO-6] Add Terms link to `semak.html` & `semak2.html` footers
- **Risk:** Zero — additive only

### [A11Y-1] Connect form labels to inputs via `for`/`id` — `semak.html`, `semak2.html`, `semak3.html`, `mohon.html`
- **Change:** Add `for="f-*"` to each `<label>` and matching `id="f-*"` to each `<input>`
- **Risk:** Zero — IDs chosen to avoid conflicts with existing element IDs

### [PERF-1] Add `<link rel="preload">` for LCP hero image — `index.html`
- **Change:** Add `<link rel="preload" as="image" href="main.png">` in `<head>`
- **Risk:** Zero — additive performance hint

---

## MANUAL ACTION REQUIRED

### [PERF-2] Compress `main.png` — 1.4 MB → target <100 KB WebP
- Go to https://squoosh.app
- Upload `main.png`, export as WebP at ~80% quality
- Replace `main.png` in repo (or add `main.webp` + `<picture>` fallback)
- **Impact:** Biggest single Core Web Vitals improvement possible

### [PERF-3] Delete `header3.png` (3.2 MB, unreferenced)
- Verify not used by any external campaign or email template
- Then: `git rm header3.png && git commit`

### [PERF-4] Subset FontAwesome to only icons used
- Per-page audit of which FA icons are actually used
- Replace CDN link with a custom kit or inline SVGs

### [SEC-1] Add security headers via Cloudflare
- Add site to Cloudflare (free tier)
- Enable: `X-Frame-Options: DENY`, `X-Content-Type-Options: nosniff`, `Referrer-Policy`, `Content-Security-Policy`

### [SEC-2] Implement GAS rate limiting
- In your Google Apps Script, add per-IC/email rate limiting and log suspicious submission patterns

### [A11Y-2] Fix `javascript:history.back()` on legal page back buttons
- `privasi.html` and `terms.html`: change floating back button to `href="index.html"`
- Low priority but improves direct-link user experience

### [SEO-7] Compress and modernise hero image
- Same as PERF-2 — affects both performance and SEO (Core Web Vitals are a ranking signal)

---

## Status Tracking

| ID | Description | Status |
|---|---|---|
| CODE-1 | Fix `padding: rem` | DONE |
| CODE-2 | Remove rogue style block (semak3/mohon) | DONE |
| CODE-3 | Remove duplicate back-to-top (index) | DONE |
| CODE-4 | Standardise `lang="ms-MY"` | DONE |
| CODE-5 | Delete `unsubscribe.htmlo` | DONE |
| SEO-1 | OG tags on privasi/terms | DONE |
| SEO-2 | Keywords meta on privasi/terms | DONE |
| SEO-3 | Fix www URL in semak3/mohon | DONE |
| SEO-4 | Add mohon/semak3 links to homepage footer | DONE |
| SEO-5 | Legal links in landing footers | DONE |
| SEO-6 | Terms link in semak/semak2 footers | DONE |
| A11Y-1 | Form label for/id connections | DONE |
| PERF-1 | Preload hint for main.png | DONE |
| PERF-2 | Compress main.png to WebP | MANUAL |
| PERF-3 | Delete header3.png | MANUAL |
| PERF-4 | Subset FontAwesome | MANUAL |
| SEC-1 | Cloudflare security headers | MANUAL |
| SEC-2 | GAS rate limiting | MANUAL |
| A11Y-2 | Fix history.back() | MANUAL |
