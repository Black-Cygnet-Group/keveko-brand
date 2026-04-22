# Fonts

Keveko uses three fonts. **No font files are committed to this repo** — commercial font licences almost always forbid redistribution via public repositories. This document tells you where to obtain each one.

## Museo Sans — primary

Used on all brand collateral.

**Weights used:** Light (300), Regular (400), Medium (500), Bold (700), Black (900).

**Where to get it:**

- [Adobe Fonts](https://fonts.adobe.com/fonts/museo-sans) — included with most Adobe Creative Cloud subscriptions.
- [MyFonts](https://www.myfonts.com/collections/museo-sans-font-exljbris) — individual weight licences available.

**Web use.** Serve either via Adobe's hosted CDN (with an Adobe Fonts subscription) or via self-hosted `@font-face` files purchased for web use from MyFonts. Do **not** commit `.ttf`, `.otf`, `.woff`, or `.woff2` files to this repo under any circumstances.

## Century Gothic — web fallback

Used only when Museo Sans is unavailable or fails to load.

**Weights used:** Regular (400), Bold (700).

**Where to get it.** Century Gothic ships with Microsoft Office and macOS, and is widely pre-installed. In most cases you don't need to self-host — declare it as a font-family fallback:

```css
font-family: "Museo Sans", "Century Gothic", sans-serif;
```

## Feeling Passionate — accent

Used sparingly, to add character. Never for body text or headings.

**Weights used:** Regular (400).

**Where to get it.** **Source to be confirmed by the brand team.** See [`../OPEN-QUESTIONS.md`](../OPEN-QUESTIONS.md) item 3. Until this is resolved, do not assume the font is available for any given project — either coordinate with the brand team to obtain licensed copies, or substitute with a compatible alternative on a per-project basis.

## Colour rule for type

Body text is always **Ocean** (`#001f49`), never plain black. See [`../colour/palette.json`](../colour/palette.json).
