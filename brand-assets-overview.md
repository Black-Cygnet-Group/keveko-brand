# Black Cygnet Brand Assets — Overview

*A short, non-technical introduction for anyone in the business.*

---

## What this is

Two online folders — one for each brand — that hold every official logo, colour, font reference, icon, and brand guide for the two brands in Black Cygnet Group:

- **Keveko** (Keveko Financial Planners, FSP 43268)
- **Black Cygnet Life** (life insurance)

Everything brand-related lives in one place. Any app, website, email, document, or AI tool we build can pull exactly the right logo, the exact right colour, the exact right icon — with a simple web link.

## Why we did this

Before: logos and brand files lived on laptops, in Dropbox, in Google Drive, in email threads. People used slightly different versions. Colours drifted by a few hex points between apps. Fonts got guessed at. Every new project started by asking someone to "send me the logo".

Now: one official source. Every logo, every hex, every icon — one link away, always current. No more sending zip files around.

## The value for the business

- **Consistency.** Every Keveko or BCL touchpoint uses the same logo, the same colour, the same icon. Brand drift is almost impossible.
- **Speed on new projects.** When we build a new app, website, campaign, or AI assistant, the brand is already wired up — no discovery phase, no asking the designer for files.
- **Safe updates.** When the brand team refreshes a logo or tweaks a colour, every future project picks it up automatically. Live products stay stable because they can lock themselves to a specific version.
- **AI-ready.** Any AI tool we use to build UI (Claude, ChatGPT, Cursor, Bolt, Lovable, etc.) can be given the official brand reference in a single paste, and it will produce work that's on-brand from the first draft.
- **Zero running cost.** The CDN that serves these assets globally (a free service called jsDelivr) costs us nothing. No infrastructure to maintain.

## How it works, in plain English

Think of it like a shared Dropbox folder, but with three important differences:

1. **It's public.** Anyone in the world can read it — which is required, because our apps running on the public internet need to see it. This means we cannot store confidential material here (see the brand-maintenance guide for what's okay and what's not).
2. **Every version is kept forever.** If we update a logo today, yesterday's version is still accessible at yesterday's link. Apps can choose to always get the latest, or lock themselves to a known-good version. This is how we make updates without breaking live products.
3. **The technical term is "Git repository".** You don't need to know what that means — it just means "a folder with full history".

## What's inside each folder

- **Logos** — primary (word mark), secondary (with byline), and standalone mark. Multiple colour treatments. Both vector (SVG — infinitely scalable) and raster (PNG).
- **Icon library** — 48 custom icons covering financial, protection, lifestyle, and action concepts.
- **Colour palette** — official hex values, usage rules, and ratios, in three formats developers can read directly.
- **Typography** — the primary font (Museo Sans), web fallback (Century Gothic), and accent font (Feeling Passionate). The font files themselves aren't included — commercial licences forbid hosting them publicly — but there's a guide to where to buy / download each.
- **Brand guidelines PDF** — the full canonical reference written by the designer.

## Who uses it — the three audiences

1. **Marketing and brand team.** You maintain these folders — replacing logos when designers send cleaner versions, adding new assets, updating colours when the brand evolves. See [`brand-maintenance.md`](./brand-maintenance.md) — a step-by-step guide that assumes no technical background.
2. **Developers and AI engineers.** You pull assets into apps, websites, and AI tools. See [`brand-assets-technical-guide.md`](./brand-assets-technical-guide.md) — a technical reference with code examples and AI prompting tips.
3. **Everyone else.** Leadership, sales, partners, new hires — this document exists so you understand what's there and can find the right person to help you with a brand-related question.

## Who looks after it

- **Today:** Gareth Quin (handing over).
- **Short-term:** Mike Hay and Imad Dollie, once they're added as admins on the repos.
- **Long-term:** anyone with a GitHub account and write access — marketing, brand, and tech team members. No single gatekeeper.

## What's left to finish

Each folder has an `OPEN-QUESTIONS.md` file listing small decisions the brand team still needs to resolve — for example, confirming which version of a colour hex is correct, or identifying the source of an accent font. These are quick, checkbox-style questions. Once the brand team works through them, we issue a cleaner, final release on each repo.

- Keveko open questions: https://github.com/Black-Cygnet-Group/keveko-brand/blob/main/OPEN-QUESTIONS.md
- BCL open questions: https://github.com/Black-Cygnet-Group/black-cygnet-life-brand/blob/main/OPEN-QUESTIONS.md

## The repositories

Both are live and usable today:

- Keveko: https://github.com/Black-Cygnet-Group/keveko-brand
- Black Cygnet Life: https://github.com/Black-Cygnet-Group/black-cygnet-life-brand

---

*Questions? Ask Gareth, Mike, or Imad, or post in the team Slack channel.*
