# Brand Assets — Technical Guide

*For developers, AI engineers, and anyone building against the brand.*

---

## The URL pattern

```
https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/<repo>@<tag>/<path-in-repo>
```

- `<repo>`: `keveko-brand` or `black-cygnet-life-brand`
- `<tag>`: a released version tag, or `main`
- `<path-in-repo>`: any file path inside the repo

That's the whole contract.

## Current released tags

| Repo | Latest tag |
|---|---|
| `Black-Cygnet-Group/keveko-brand` | `v0.1.1` |
| `Black-Cygnet-Group/black-cygnet-life-brand` | `v0.1.2` |

Check the repo's **Releases** page for the current value; update your pin when you want a new version.

## The one rule you must follow

**Pin to a tag in production. Use `@main` only in dev.**

| Context | Pin to | Why |
|---|---|---|
| Production apps | `@v0.1.1` (released tag) | Immutable. Cached by jsDelivr for 1 year. Nothing can break it. |
| Dev, internal tools, throwaways | `@main` | Auto-updates within minutes when brand commits land. |

Never mix the two in one app. If you use `@main` in prod, every brand commit silently changes what your users see.

---

## Examples

### HTML / email
```html
<img
  src="https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/logo/primary/keveko-logo-primary-full-colour.svg"
  alt="Keveko"
  height="48"
/>
```

### React / Next.js
```tsx
const LOGO = 'https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/logo/primary/keveko-logo-primary-full-colour.svg';

export const Header = () => <img src={LOGO} alt="Keveko" height={48} />;
```

### CSS custom properties
```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/colour/palette.css"
/>
```

```css
.button-primary {
  background: var(--keveko-sky);
  color: var(--keveko-ocean);
}
```

For BCL, use `--bcl-*`.

### Tailwind

Copy `colour/tailwind.colours.ts` into your config, or re-export:

```ts
import { kevekoColours } from 'https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/colour/tailwind.colours.ts';

export default {
  theme: { extend: { colors: { keveko: kevekoColours } } },
};
```

Then use utilities like `bg-keveko-ocean text-keveko-sky`.

### Colour tokens as JSON (source of truth)

```ts
import palette from 'https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/colour/palette.json'
  assert { type: 'json' };

palette.colours.ocean.hex;     // "#001f49"
palette.colours.ocean.usage;   // descriptive string
palette.usageRatio.ocean;      // 0.50
```

Or `fetch()` at runtime if your setup doesn't support import assertions.

### Typography tokens

```ts
import type from 'https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/typography/typography.json'
  assert { type: 'json' };

type.families.primary.name;     // "Museo Sans"
type.families.primary.weights;  // [300, 400, 500, 700, 900]
```

### Icons

48-icon library. Same name set for both brands:

```
icons/keveko-icon-<name>.svg   (or .png)
icons/bcl-icon-<name>.svg      (or .png)
```

Available names (alphabetical):

```
alert, briefcase, business-person, calendar, checklist, coin-stack, disability,
document-calculator, document-secure, document-sign, email, family-heart-shape,
family-of-three, fast-timing, financial-strength, growth, handshake, HIV,
house-and-trees, house-calculator, house-in-hand, house-insurance, house-keys,
increase, injury, investigate, location-pin, logistics-calculator,
message-bubble, nature, pet-insurance, phonecall, pie-bar-graphs, piggy-bank,
puzzle-lightbulb, retail-shop, rewards, rocket-launch, secure, settings,
settings-graph, shopping, target, time, transparency, two-hands, unlock-access,
wealth
```

Inline SVG tip: `fetch()` the file and inject via `dangerouslySetInnerHTML` (React) when you need CSS control over `fill` and `stroke`.

### Fonts

**No font files are committed.** Commercial licences forbid redistribution via public repos.

- **Museo Sans** (primary): Adobe Fonts (Creative Cloud) or MyFonts web-font licence.
- **Century Gothic** (fallback): ships with macOS / Microsoft Office; declare as CSS fallback, no self-hosting needed.
- **Feeling Passionate** (accent): vendor to be confirmed — see `OPEN-QUESTIONS.md`.

Sourcing specifics in `typography/fonts.md` in each repo.

---

## AI prompting

When asking Claude, ChatGPT, Cursor, Bolt, Lovable, or any LLM to produce on-brand UI, paste one of these blocks as context. The AI will use only the paths and values you give it, not hallucinated hexes or fonts.

### Keveko

```
You are building UI for Keveko (Keveko Financial Planners, FSP 43268). Use
only the brand assets at the URLs below. Pin to v0.1.1 in production.

LOGOS
  Primary lockup (default):
    https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/logo/primary/keveko-logo-primary-full-colour.svg
  Variants (same folder): mono-black, mono-navy, mono-white, reversed.
  Byline lockup (when introducing the brand): /logo/secondary/ with same treatments.
  Standalone mark (the "o" symbol): /logo/mark/ in 7 tints: mono-black, mono-white,
    mono-navy, mono-sky, mono-candy, mono-misty-rose, mono-maroon. PNG only at v0.1.1.

COLOURS (https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/colour/palette.json)
  ocean       #001f49   50%   Primary. Body text (NEVER plain black). Dark bg.
  sky         #439bbb   30%   Primary bg. Pairs with Ocean or White text.
  misty-rose  #f6e2e0   10%   Secondary bg. Body only on Ocean bg.
  candy       #fe3725    5%   Error / accent only. NEVER bg or body.
  maroon      #b71d21    5%   Accent only. NEVER bg or body.
  white       #ffffff         Primary bg. Reversed text colour on Ocean.

TYPOGRAPHY
  Primary: Museo Sans (300, 400, 500, 700, 900). All brand work.
  Web fallback: Century Gothic (400, 700).
  Accent: Feeling Passionate (sparing use).
  Rule: body is Ocean, never black.

ICONS
  48-icon library at /icons/keveko-icon-<name>.svg. Full name list: see
  brand-assets-technical-guide.md or the repo's /icons/ folder.

VOICE
  Archetype: The Trusted Navigator (Caregiver + Sage).
  Calm, clear, human, reassuring, expert. Simple language over jargon.

FULL BRAND GUIDE (for reference)
  https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/keveko-brand@v0.1.1/guidelines/keveko-brand-guide.pdf

DO NOT
  - Invent hex values not listed above.
  - Invent asset paths not in the repo.
  - Substitute fonts without confirming with the brand team.
  - Use plain black (#000000) for body text — use Ocean.
```

### Black Cygnet Life

```
You are building UI for Black Cygnet Life, a life insurance brand within Black
Cygnet Group. Use only the brand assets at the URLs below. Pin to v0.1.2 in
production.

LOGOS
  Primary lockup:
    https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/black-cygnet-life-brand@v0.1.2/logo/primary/bcl-logo-primary-full-colour.svg
  Variants (same folder): mono-navy, mono-misty-rose, mono-white. (No mono-black at v0.1.2.)
  Standalone mark: /logo/mark/ in 6 tints — mono-black, mono-white, mono-navy,
    mono-sky, mono-misty-rose, mono-candy. SVG + PNG.
  Parent-brand (BCG) swan mark: /parent-brand/mark/bcg-mark-primary-mono-<colour>.svg.
    Use when referencing the parent brand, not BCL itself.

COLOURS (https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/black-cygnet-life-brand@v0.1.2/colour/palette.json)
  ocean       #001f49   50%   Primary. Body text (NEVER plain black). Dark bg.
  misty-rose  #f6e2e0   30%   Primary bg. Body only on Ocean bg.
  candy       #fe3725   10%   Error / secondary accent. NEVER bg or body.
  sky         #439bbb   10%   Secondary bg / success. Pairs with Ocean or White text.
  white       #ffffff         Primary bg. Reversed text colour on Ocean.
  NOTE: BCL does NOT use Maroon (Keveko's palette has it; BCL does not).

TYPOGRAPHY
  Primary: Museo Sans (300, 400, 500, 700, 900).
  Web fallback: Century Gothic (400, 700).
  Accent: Feeling Passionate (internal marketing use only).
  Rule: body is Ocean, never black.

ICONS
  Same 48-icon library as Keveko at /icons/bcl-icon-<name>.svg (byte-identical set).

VOICE
  Archetype: The Visionary Rebel (Sage + Magician + Outlaw).
  Bold, insightful, courageous, curious, empowering. Challenges conventional
  insurance language. Uses questions to engage. Avoids corporate jargon, passive
  phrasing, cliché sales language. Direct and human — "you", not "the insured party".

FULL BRAND GUIDE (for reference)
  https://cdn.jsdelivr.net/gh/Black-Cygnet-Group/black-cygnet-life-brand@v0.1.2/guidelines/black-cygnet-life-brand-guide.pdf

DO NOT
  - Use Maroon — it's not in the BCL palette.
  - Invent hex values, asset paths, or fonts.
  - Use plain black (#000000) for body — use Ocean.
  - Write in the voice of Keveko; BCL is bolder and more challenger-styled.
```

---

## Best practices

1. **Pin to tags in production.** `@main` is dev-only. Never mix in a single app.
2. **Don't mirror assets into your own repo.** That defeats the point. Always pull from jsDelivr so updates propagate.
3. **Cache-bust via tag bumps, not query strings.** jsDelivr tag URLs are immutable and cached for a year. Moving to a new tag is the right cache-bust mechanism.
4. **Monitor the repo's CHANGELOG** before bumping your pin. Major version jumps are always explained.
5. **Prefer SVG over PNG** wherever possible — smaller, sharper, recolourable via CSS.
6. **Inline SVGs when you need to animate or recolour.** Fetch the file, inject as raw markup, then fill/stroke are CSS-controllable.
7. **Don't self-host fonts** unless your licence explicitly covers web redistribution. Adobe Fonts served via their own CDN is the safe default for Museo Sans.
8. **Use the JSON as your authoritative palette reference** — `palette.json` is the source of truth; `palette.css` and `tailwind.colours.ts` are manual re-expressions of the same values. The brand team keeps all three in sync.

## Performance

- jsDelivr serves from 750+ global edge locations. Expect sub-50ms fetch times worldwide.
- Tag URLs: cached 1 year.
- `@main` URLs: cached 12 hours at edge, a few minutes at the CDN origin.
- CORS: `Access-Control-Allow-Origin: *` on everything. Assets work from any browser origin.
- HTTPS only.
- Typical sizes: primary logo SVG 5–15 KB, icon SVG 2–5 KB, palette JSON 1–2 KB, brand guide PDF 11–12 MB (compressed).

## Gotchas

- **20 MB per-file limit.** jsDelivr returns 403 for files over 20 MB. Both brand guide PDFs are under this, but watch it if someone commits something huge.
- **New tags take 5–10 minutes to index on jsDelivr first time.** If you just cut a release and the URL 404s, wait a moment and retry.
- **Re-used tags are not supported.** Once a tag is published, jsDelivr caches that version forever. Never delete and re-push the same tag — always bump to a new number.
- **Never delete tags.** Apps pinned to them break instantly. Roll forward with a new major.
- **Filename changes are breaking.** If brand rename a file, URLs pinned to it will 404. Watch for major-version releases; they always document renames.

## Repo structure (current at v0.1.1 / v0.1.2)

```
<repo>/
├── README.md
├── HANDOVER.md
├── CHANGELOG.md
├── OPEN-QUESTIONS.md
├── logo/
│   ├── primary/       # wordmark lockup, multiple treatments
│   ├── secondary/     # byline lockup (Keveko only)
│   └── mark/          # standalone symbol, multiple tints
├── icons/             # 48 icons, SVG + PNG
├── colour/
│   ├── palette.json
│   ├── palette.css
│   └── tailwind.colours.ts
├── typography/
│   ├── typography.json
│   └── fonts.md
├── guidelines/        # canonical brand guide PDF
└── parent-brand/      # BCL only — BCG parent swan mark
    └── mark/
```

## Repos at a glance

| | Keveko | Black Cygnet Life |
|---|---|---|
| Repo | `Black-Cygnet-Group/keveko-brand` | `Black-Cygnet-Group/black-cygnet-life-brand` |
| Current tag | v0.1.1 | v0.1.2 |
| File prefix | `keveko-` | `bcl-` (plus `bcg-` for parent-brand assets) |
| Palette colours | 5 + white (Ocean, Sky, Misty Rose, Candy, Maroon) | 4 + white (Ocean, Misty Rose, Candy, Sky) |
| Logo primary variants | 5 | 4 (no `mono-black`) |
| Logo mark variants | 7 (PNG only) | 6 (SVG + PNG) |
| Byline lockup | Yes (`logo/secondary/`) | No |
| Parent-brand assets | No | Yes (`parent-brand/`) |
| Icons | 48 | 48 (byte-identical set) |

---

## Related docs

- [`brand-assets-overview.md`](./brand-assets-overview.md) — non-technical intro, for the whole business.
- [`brand-maintenance.md`](./brand-maintenance.md) — for marketing / brand team, how to update assets.
- Each repo's `README.md` — user-facing repo documentation.
- Each repo's `HANDOVER.md` — maintainer-specific rules including naming convention.
- Each repo's `OPEN-QUESTIONS.md` — open brand-team decisions.
