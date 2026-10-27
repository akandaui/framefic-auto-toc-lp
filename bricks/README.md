# 09 · Auto TOC landing page: Bricks Builder setup

**Date:** 2026-10-27
**Back to:** `docs/Context.md` · `docs/00-plan.md` (full copy: `docs/09-bricks-setup.md`)
**Purpose:** step-by-step checklist for moving the coded landing page (`framer LP/`) into Bricks Builder, using the ready-made package in `framer LP/bricks/`.

---

## What's in the package (`framer LP/bricks/`)

| File | Goes into |
|---|---|
| `1-head-code.html` | Bricks → Settings → Custom code → **Header scripts** |
| `2-custom-css.css` | Bricks → Settings → Custom code → **Custom CSS** |
| `3-body-footer-code.html` | Bricks → Settings → Custom code → **Body (footer) scripts** |
| `sections/01-header.html` … `10-video-lightbox.html` | One file per page section (see step 5) |
| `media/` (+ `media/fav/`) | Every image the page uses |

All image paths in the CSS and section files start with the placeholder **`{{MEDIA}}`**.

---

## Steps

### 1. Upload the media
1. Upload the whole `media/` folder (including `fav/`) to one folder on the site, e.g. `/wp-content/uploads/atoc-lp/` (via FTP, the host's File Manager, or a folder plugin).
2. Note the folder URL, e.g. `/wp-content/uploads/atoc-lp`.
3. In `2-custom-css.css` and every file in `sections/`, find and replace **`{{MEDIA}}`** with that URL.

> If you upload through the WordPress Media Library instead, files land in dated folders. Then you have to replace each image path one by one.

### 2. Header code (fonts + script flag)
Paste `1-head-code.html` into **Header scripts**. It:
- loads **Instrument Sans** (the only font the page uses; weights 400–700);
- adds the `atoc-js` class to `<html>` so the fade-in animations start hidden only when the script is running.

### 3. CSS
Paste `2-custom-css.css` into **Custom CSS**.
- All colours, spacing and fonts are variables at the top (`--atoc-500`, `--atoc-space-24` …). Change the brand there.
- Every class starts with `atoc-` so nothing clashes with other Bricks styles.

### 4. Footer script
Paste `3-body-footer-code.html` into **Body (footer) scripts**. It runs the scroll fade-ins, header glass state, word-by-word headlines, pinned "How it works", play-button lightbox and the hero ASCII field.

To load it on this page only, use the page's **Settings → Custom code** fields instead of the site-wide ones.

### 5. Theme Styles (do this before building)
- **Section padding:** 0 (the CSS sets its own spacing).
- **Container width:** 1200px.
- Turn off Bricks' default heading margins if your theme style adds them.

### 6. Build the sections
Use a mix:

| Section file | Recommended in Bricks |
|---|---|
| 01 Header | Header template: native elements, or a Code element |
| 02 Hero | **Code element** (poster, play button, ASCII canvas) |
| 03 Core capabilities | Native elements |
| 04 Founder | **Code element** (plugin orbit) |
| 05 More features | Native elements |
| 06 How it works | **Code element** (illustrations + pinning) |
| 07 Pricing | Native elements |
| 08 FAQ + CTA | Native elements |
| 09 Footer | Footer template: native elements, or a Code element |
| 10 Video lightbox | **Code element**, placed anywhere on the page (it's hidden until opened) |

**Code element:** paste the section file, enable **Execute code**, and save.

**Native elements:** rebuild the tree in the section file (Section → Container → Div / Heading / Text / Image / Button). Give each element the same class(es) as in the file, e.g. `atoc-cap__card`, `atoc-plan atoc-plan--featured`. Set heading tags (h1/h2/h3) to match. The pasted CSS styles them automatically.

### 7. Attributes to keep (Element → Style → Attributes)
| Element | Attribute |
|---|---|
| How it works `<section>` | `data-atoc-pin` (turns on the pinned scroll) |
| Hero play button | `data-video="https://…"` (YouTube, Vimeo or .mp4 link; empty shows the poster) |
| Hero `<canvas>` | class `atoc-hero__ascii`, `aria-hidden="true"` |

### 8. Check before publishing
- [ ] All images load (no `{{MEDIA}}` left anywhere).
- [ ] Sections fade in on scroll on the live page (they show without animation inside the Bricks editor; that's expected).
- [ ] "How it works" pins on desktop (≥ 992px wide) and stacks on tablet/mobile.
- [ ] Play button opens the lightbox; Esc closes it.
- [ ] No sideways scroll on a phone.

---

## Still open (content, not code)
- Pricing section and "Start Your 7-Day Trial" still show template content (Auto TOC is Free + Pro $79 lifetime).
- FAQ has questions only; answers needed before the rows can expand.
- Demo video URL for the play button.
- All links are `#` placeholders.
