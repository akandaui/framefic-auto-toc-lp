# Auto TOC landing page (Framefic)

Landing page for **Auto TOC**, a Framer plugin by Framefic, built as plain HTML/CSS/JS for **Bricks Builder** (WordPress).

## Preview locally

```
python3 -m http.server 4321
```

Then open http://127.0.0.1:4321/

## Structure

| Path | What it is |
|---|---|
| `index.html` | The full page (preview) |
| `assets/css/style.css` | All styles; tokens are CSS variables at the top, classes use the `atoc-` prefix |
| `assets/js/main.js` | Scroll reveals, word-by-word headlines, pinned "How it works", play-button lightbox, hero ASCII field |
| `assets/img/` | Images and plugin favs |
| `bricks/` | **Bricks package**: head code, custom CSS, footer script, one snippet per section, media. Start with `bricks/README.md` |

## Building in Bricks

Follow `bricks/README.md`. In short: upload `bricks/media/`, replace `{{MEDIA}}` with its URL, paste the three code files into Bricks custom code, then build each section (Code elements for animated sections, native elements for the rest).

## Content still to confirm

- Pricing and "Start Your 7-Day Trial" are template placeholders (Auto TOC is Free + Pro $79 lifetime).
- FAQ answers.
- Demo video URL (`data-video` on the play button).
- All links are `#` placeholders.
