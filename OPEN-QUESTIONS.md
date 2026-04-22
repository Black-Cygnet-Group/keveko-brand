# Open Brand Questions — Keveko

This file lists open questions the brand and marketing teams need to resolve before they can be incorporated into the brand assets repo.

Each item has:

- **Context** — what we found, and why it's a question.
- **Decision needed** — the options, laid out as a checklist.
- **Interim approach** — what the repo is doing today, until the decision is made.

**How to respond.** Reply to whoever shared this file with you (currently: Gareth Quin / @garethquin) with your decision on each numbered item. Your answers will then be applied to the repo in a new version (`v0.2.0` or similar), and the logo / colour / typography assets updated accordingly.

---

## 1. Logo SVG colours don't match the canonical brand palette

**Context.** The brand guide (`guidelines/keveko-brand-guide.pdf`, page 8) and the internal brand notes both specify these canonical hex values for the primary brand colours:

- Ocean (primary navy): **`#001f49`**
- Sky (primary teal / blue): **`#439bbb`**

However, the supplied logo SVG files actually use slightly different hex values:

- Navy in logos: **`#112148`** — appears 114 times across all logo SVGs
- Sky in logos: **`#3b9bbc`** — appears 46 times; also `#439bbb` appears 4 times

The logos appear to have been exported either against an older palette, or with slight colour drift introduced during export. On screen, the logo navy `#112148` is visibly lighter than the canonical Ocean `#001f49`.

**Decision needed.** Which of the following is correct?

- [ ] **A. The brand guide is authoritative — re-export the logo SVGs.** The designer will re-export to use `#001f49` and `#439bbb`. Once done, the new SVGs will replace the current ones in the repo.
- [ ] **B. The logo SVGs are correct — update the brand guide instead.** The canonical palette should be `#112148` and `#3b9bbc`. The brand guide PDF and internal notes will be revised.
- [ ] **C. Other — specify:** ____________________

**Interim approach in the repo.** The token files (`colour/palette.json`, `colour/palette.css`, `colour/tailwind.colours.ts`) carry the brand-guide hexes (`#001f49`, `#439bbb`) because that's the currently authoritative palette. The logo SVG files have been committed **as supplied** — no colour values have been edited inside them. Apps that pull colour from the token files will match the brand guide; logos will render with the slightly different hexes until re-exported.

---

## 2. Logo mark has no SVG — only PNG

**Context.** The logo mark (the standalone "o" symbol used as an icon) was supplied as PNG only, across 7 colour tints (black, white, navy, sky / blue, candy, light pink, maroon). The high-resolution PNGs (4803 × 4575 pixels) scale well for most use cases, but without an SVG the mark can't be scaled infinitely or recoloured programmatically.

**Decision needed.** Please supply an SVG version of the mark.

- [ ] **A. SVG mark is coming — ETA:** ____________________
- [ ] **B. SVG mark will not be produced.** PNG is the only format we will support. This will be documented in the README as a permanent decision.

**Interim approach in the repo.** The 7 PNG variants are in [`logo/mark/`](./logo/mark/) and usable now. If the SVG arrives later, it will be added in a future release.

---

## 3. "Feeling Passionate" accent font — source unknown

**Context.** The internal brand notes list three fonts:

- **Museo Sans** — primary; available via Adobe Fonts and MyFonts.
- **Century Gothic** — web fallback; widely licensed.
- **Feeling Passionate** — accent, to be used sparingly. **Source not documented anywhere in the brand guide or notes.**

The repo's font-sourcing document ([`typography/fonts.md`](./typography/fonts.md)) needs to tell developers where to obtain each font, but "Feeling Passionate" isn't immediately identifiable from any of the major font distributors.

**Decision needed.**

- [ ] **A. The vendor and licence for the font is:** ____________________
- [ ] **B. We no longer use this font — remove it from all brand documentation.**
- [ ] **C. Replace it with:** ____________________

**Interim approach in the repo.** `fonts.md` lists the font with a "source to be confirmed" note pointing back at this open question. No font file is bundled (commercial font licences forbid redistribution via public repos regardless).

---

## 4. Confirm the `document-secure` icon rename

**Context.** Two icon files were supplied named `socument-secure.svg` and `socument-secure.png`. The brand notes explicitly reference a "document secure" icon in the Protection category, so this appears to be a simple typo ("s" instead of "d"). During migration, the files were renamed to `keveko-icon-document-secure.{svg,png}`.

**Decision needed.**

- [ ] **A. Confirm the rename is correct.** *(Expected default — open the icon, verify it depicts a secured document, and tick this box.)*
- [ ] **B. The icon is not a "document secure" icon — the intended name is:** ____________________

---

## 5. Should the brand tone-of-voice notes be made public?

**Context.** The internal brand notes document (`keveko-assets-logos-fonts-icons-brand-notes.docx` in the source folders) contains substantial tone-of-voice, vocabulary, and copy-style guidance that is not duplicated in the public brand guide PDF. It also includes useful design-system specifications (spacing grid, button styles, icon stroke weight). This content would be valuable to anyone writing copy or building UI for Keveko.

However, the DOCX was authored as an internal handover document and contains design-process annotations like "(visuals attached)" and "(Custom icon files supplied.)" that aren't polished for external use.

**Decision needed.**

- [ ] **A. Produce a polished public tone-of-voice guide** (markdown or PDF) to live alongside the brand guide in `guidelines/`. Who will own this: ____________________
- [ ] **B. Keep tone-of-voice internal only.** The current brand guide PDF is the only public documentation. The DOCX stays on shared internal drives.
- [ ] **C. Commit the DOCX as-is** to `guidelines/`, acknowledging it's rough but useful.

**Interim approach in the repo.** The DOCX is **not** committed. Its palette, typography, and icon-usage facts have been extracted into the README and token files. Tone-of-voice and design-system spacing content is not currently surfaced anywhere public.

---

*Last updated: 2026-04-22.*
