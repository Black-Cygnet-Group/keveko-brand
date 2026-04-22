# Changelog

All notable changes to the Keveko brand assets repository will be documented here.
Newest entries at the top. Versions follow [Semantic Versioning](https://semver.org/).

## v0.1.1 — 2026-04-22

**Fixed:**

- Replaced the brand guide PDF with a compressed version (~12 MB, down from ~21 MB). This resolves an unreported issue in v0.1.0: the original PDF exceeded jsDelivr's 20 MB per-file limit and returned 403 when fetched via the CDN. The compressed version is now under that limit and CDN-accessible. Content is unchanged — all 27 pages present, compressed via TinyWow.

## v0.1.0 — 2026-04-22

Initial release. Migrated Keveko brand assets from local source folders into this public repo, served via jsDelivr.

**Added:**

- Primary logo set (5 colour treatments: `full-colour`, `reversed`, `mono-black`, `mono-navy`, `mono-white`) in SVG + PNG. See [`logo/primary/`](./logo/primary/).
- Secondary / byline logo set — the primary word mark paired with "Your Financial Planner" — same 5 colour treatments, SVG + PNG. See [`logo/secondary/`](./logo/secondary/).
- Logo mark set — 7 tinted PNG variants (`mono-black`, `mono-white`, `mono-navy`, `mono-sky`, `mono-candy`, `mono-misty-rose`, `mono-maroon`). SVG not yet available; see [`OPEN-QUESTIONS.md`](./OPEN-QUESTIONS.md) item 2.
- Icon library of 48 custom icons, each in SVG + PNG.
- Colour palette tokens in three hand-kept-in-sync formats: [`colour/palette.json`](./colour/palette.json), [`colour/palette.css`](./colour/palette.css), [`colour/tailwind.colours.ts`](./colour/tailwind.colours.ts).
- Typography spec ([`typography/typography.json`](./typography/typography.json)) and font-sourcing guide ([`typography/fonts.md`](./typography/fonts.md)).
- Canonical brand guidelines PDF ([`guidelines/keveko-brand-guide.pdf`](./guidelines/keveko-brand-guide.pdf)).
- Repository documentation: [`README.md`](./README.md), [`HANDOVER.md`](./HANDOVER.md), [`OPEN-QUESTIONS.md`](./OPEN-QUESTIONS.md).

**Renamed during migration:**

- All files renamed to the convention `keveko-<asset-type>-<variant>-<colour-treatment>.<ext>` — see [`HANDOVER.md`](./HANDOVER.md) for the full convention.
- `socument-secure.{svg,png}` → `keveko-icon-document-secure.{svg,png}` (typo fix; the brand notes explicitly list "document secure" as the intended icon).

**Skipped during migration (for reference):**

- 96 duplicate icon files in a nested `keveko-assets-iconography/` folder in the source (byte-for-byte identical to the top-level `SVG/` and `PNG/` folders via md5). Kept only the top-level copies.
- 4 archive (`.zip`) files redundant with their extracted folders.
- 1 internal working DOCX (`keveko-assets-logos-fonts-icons-brand-notes.docx`). Its content informed the token files and README, but the document itself was not committed. See [`OPEN-QUESTIONS.md`](./OPEN-QUESTIONS.md) item 5.

**Known issues to be resolved by the brand / marketing team** — see [`OPEN-QUESTIONS.md`](./OPEN-QUESTIONS.md):

1. Logo SVGs use `#112148` / `#3b9bbc` while the canonical palette is `#001f49` / `#439bbb`. Tokens use the canonical values; logo SVGs are committed as-is pending re-export.
2. Logo mark SVG is not yet available — PNG only.
3. The "Feeling Passionate" accent font has no confirmed vendor source.
