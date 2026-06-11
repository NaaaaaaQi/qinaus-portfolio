# Qinaus Portfolio Generator

> A data-driven artist portfolio system that converts website content into a print-ready PDF — no design tools, no manual layout.

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg)](LICENSE)
[![Format](https://img.shields.io/badge/Output-A4%20PDF-8b0000.svg)]()
[![Stack](https://img.shields.io/badge/Stack-Vanilla%20JS%20%2B%20CSS-c9a87c.svg)]()

---

## Overview

This project generates a professional artist portfolio PDF directly from structured content data. It powers the portfolio of **[Qinaus](https://www.qinaus.com)** — a contemporary oil painter based in San Francisco, CA.

The core idea: **separate content from presentation**.

```
data.js       ← all text, image URLs, CV entries  (edit this when content changes)
index.html    ← layout engine + print CSS         (stable, rarely touched)
```

Open `index.html` in Chrome → **File → Print → Save as PDF** → done.

---

## Features

- **Zero dependencies** — pure HTML, CSS, and vanilla JavaScript
- **Data-driven** — all content lives in one file; the template never changes
- **Print-optimised** — A4 CSS with `page-break-before` per section, `page-break-inside: avoid` on image blocks
- **7 layout types** — hero, hero-multicolumn, grid-2×2, sidebar, and more
- **Live image loading** — Squarespace CDN URLs loaded directly; no local asset management
- **Section numbering** — computed dynamically from the data structure

---

## Structure

```
qinaus-portfolio/
├── index.html      # Renderer: CSS + JS layout engine
└── data.js         # Content: artist info, CV, series, artworks
```

### Layout types available

| Key | Description |
|-----|-------------|
| `hero` | Full-bleed image + description |
| `hero-multicolumn` | Full-bleed image + 2-column paragraph array |
| `grid-2-then-1` | 2 artworks side-by-side, 1 full-width below |
| `grid-2x2` | 2 × 2 artwork grid |
| `grid-1full+2` | 1 full-width artwork, then 2 side-by-side |
| `sidebar` | Tall artwork left + stacked artworks right |
| `grid-2+1wide` | 2 side-by-side, 1 full-width below |

---

## Usage

### View / Export PDF

1. Clone or download the repository
2. Open `index.html` in **Google Chrome**
3. `File → Print` → Destination: **Save as PDF** → Paper: **A4** → Margins: **None**

### Update content

All content lives in `data.js`. The structure is documented inline:

```js
const PORTFOLIO = {
  artist: { name, subtitle, location, website, email, instagram, year },
  cover:  { imageUrl },
  statement: { paragraphs[], pullquote, closing },
  cv:     { education[], exhibitions[], studios[], professional[] },
  series: [
    {
      num: 'I',
      name: 'Series Name',
      pages: [
        {
          layout: 'hero',
          artwork: { title, meta, imageUrl, description }
        }
      ]
    }
  ]
}
```

To add a new series, append an object to the `series` array and choose a layout type.

### Push updates to GitHub

```bash
git add data.js
git commit -m "add new series"
git push
```

---

## Design System

| Token | Value |
|-------|-------|
| Page size | A4 (210 × 297 mm) |
| Margin | 18 mm |
| Accent | `#8b0000` (deep red) |
| Serif | Georgia |
| Sans | Helvetica Neue |
| Body text | 8.5 pt / 1.75 line-height |

---

## About the Artist

**Qinaus** is a contemporary oil painter based in San Francisco, California. Her work investigates experiences at moments of transition — between conscious and unconscious, past and future, observer and observed.

→ [www.qinaus.com](https://www.qinaus.com) · [@qinaus_](https://instagram.com/qinaus_)

---

*Built with HTML, CSS, and one JavaScript file. No frameworks. No build step.*
