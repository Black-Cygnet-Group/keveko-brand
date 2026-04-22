# Brand Maintenance Guide

*For the marketing and brand team.*

---

## Before we start — read this first

- **You don't need to know how to code.** None of this involves writing code.
- **You don't need to use the command line.** Everything happens in a normal web browser, on github.com, clicking buttons and uploading files.
- **You cannot break anything permanently.** Every change is saved forever, and any previous version can be restored in seconds. The system is designed to let you experiment.
- **When in doubt, ask.** It's always faster than guessing. Ping Gareth, Mike, or Imad on Slack, or leave a question on the GitHub file directly.

---

## Where the two folders live

- **Keveko:** https://github.com/Black-Cygnet-Group/keveko-brand
- **Black Cygnet Life:** https://github.com/Black-Cygnet-Group/black-cygnet-life-brand

You need an account on github.com and admin access to either folder. If you don't have it yet, ask Gareth / Mike / Imad to add you.

---

## The three things you'll do

### 1. Replacing an existing file

By far the most common task. Example: the designer sends you a cleaner version of the Keveko logo.

1. Go to the folder on github.com (link above).
2. Click through the folders to find the file — logos are in `logo/`, icons in `icons/`, and so on.
3. Click the file to open it.
4. For text-like files (SVG, JSON, CSS), click the **pencil icon** in the top right of the file view. For image files (PNG) or PDFs, click the **"..." menu** → **"Replace this file"**.
5. Upload the new file. **Important:** use the exact same filename. This keeps the existing web link working — apps already using it will seamlessly get the new version.
6. Scroll to the bottom. GitHub asks for a short message describing the change. Write it in plain English, e.g.:
   `replace Keveko primary logo with cleaner export`
7. Click the green **Commit changes** button.
8. Done. The change is saved. Anyone pulling the latest version will get the new file within a few minutes.

### 2. Adding a new file

Example: the designer produces a new logo variant for a specific campaign.

1. Navigate to the folder where the file should live (e.g. `logo/primary/` for a new primary logo variant, `icons/` for a new icon).
2. Click **Add file** → **Upload files**.
3. Drag the file into the upload area, or click **"choose your files"**.
4. **Make sure the filename follows the convention** — it matters because the URL will use it. Look at the other files in the folder and match the pattern. For most cases:

   - Keveko files start with `keveko-`
   - BCL files start with `bcl-`
   - Parent-brand (Black Cygnet Group) files start with `bcg-`
   - All lowercase letters, numbers, and hyphens — no spaces, no capitals, no underscores.
   - No version numbers in the filename (like `-v2` or `-final`) — that's handled separately.

   Examples of good filenames:
   - `keveko-logo-primary-full-colour.svg`
   - `bcl-logo-primary-mono-navy.png`
   - `keveko-icon-briefcase.svg`

   If unsure, rename the file on your computer first, then upload.

5. Write a short commit message, e.g. `add Keveko summer campaign logo variant`.
6. Click **Commit changes**.

### 3. Changing a brand colour

This happens rarely, but when it does, you have to change the colour in **three files** in the same sitting — they're kept in sync by hand on purpose (so no code or build tooling is needed).

The three files all live in the `colour/` folder of each repo:

- `palette.json`
- `palette.css`
- `tailwind.colours.ts`

Steps:

1. Open `colour/palette.json`. Click the pencil icon to edit.
2. Find the colour you're changing. Update the hex value (the part that looks like `#001f49`). Scroll down, write a message like `update Sky to #3b9bbc (part 1 of 3)`. Commit.
3. Do the same for `colour/palette.css`. Use the same new hex. Commit with message like `update Sky to #3b9bbc (part 2 of 3)`.
4. Do the same for `colour/tailwind.colours.ts`. Commit with `update Sky to #3b9bbc (part 3 of 3)`.

A colour change is a bigger deal than a logo swap — let the tech team know when you've done it, so they can bump version numbers and notify anyone affected.

---

## What happens after you commit

Once your change is saved, here's what happens automatically:

- Within a few minutes, any app or tool set to always-fetch-the-latest picks up your change.
- The tech team periodically "publishes a release" — this creates a snapshot with a version number (like v0.2.0) so production apps can opt into the new version when they're ready. **You do not need to do this step** — but if you're curious, there's a one-paragraph explainer at the bottom of this document.

So for 95% of tasks: you commit → you're done.

---

## Can I undo something?

Yes. Easily. Every single change is saved forever.

- On any file, click the **History** button (top right of the file view) to see every previous version.
- Click any old version to see what it looked like.
- To restore: either upload the old version again with the same filename, or ask the tech team — a single command reverts any change.

If you committed a wrong file, don't panic. It's fixable. Just let someone know.

---

## What you must not upload

These folders are **public** — visible to anyone on the internet. That's deliberate (it's how our apps fetch the files) but it means these things never go in:

- **Font files.** Museo Sans and other commercial fonts can't be hosted on a public server. Always link to the font vendor's page (Adobe Fonts, MyFonts, etc.) instead of uploading the file.
- **Paid stock photos** we don't own outright.
- **Unannounced logos, rebrands, or new subsidiary brands.** A public folder is effectively a public announcement.
- **Client documents, pitch decks, financial records, contracts.**
- **Anything with personal data** — names, emails, phone numbers, ID numbers — unless that data is already publicly available on our website.
- **Internal passwords, API keys, or system credentials.**

**If in doubt, ask before uploading.** It's easier to check than to remove something from a public repo after the fact.

---

## When to ask for help

- You can't find the file you need to update.
- The naming convention isn't obvious.
- Something feels big or risky — especially if you're changing a primary logo or a brand colour.
- You're not sure whether a file is safe to upload.
- Anything at all feels uncertain.

Contacts: Gareth, Mike, or Imad on Slack, or open an **Issue** on the GitHub repo (green "New issue" button on the Issues tab) — the tech team will pick it up.

---

## A note on the OPEN-QUESTIONS files

Each repo has a file called `OPEN-QUESTIONS.md` — a short list of decisions the brand/marketing team still needs to make (like: "which version of this hex is right?", "where does this accent font come from?"). Please read through, answer the checkboxes, and send your answers to Gareth / Mike / Imad. Once done, we'll apply the answers in a clean new version.

- Keveko: https://github.com/Black-Cygnet-Group/keveko-brand/blob/main/OPEN-QUESTIONS.md
- BCL: https://github.com/Black-Cygnet-Group/black-cygnet-life-brand/blob/main/OPEN-QUESTIONS.md

---

## Optional, advanced — publishing a version

You don't need to know about this for normal maintenance. Skip this section unless you're curious.

When you "publish a release", you give a specific moment in time a name (like `v0.2.0`) so production apps can lock themselves to that exact state. The tech team usually handles this, but if you want to do it yourself:

1. From the repo home page, click **Releases** (right sidebar).
2. Click **Draft a new release**.
3. Click **Choose a tag** → type a new version number. The rule:
   - Fixed a file so it looks the same but cleaner: bump the last digit (e.g. v0.1.2 → v0.1.3).
   - Added something new: bump the middle digit (v0.1.2 → v0.2.0).
   - Removed something or changed a colour: bump the first digit (v0.1.2 → v1.0.0).
4. Title it in plain English, like "v0.2.0 — Updated Keveko primary logo".
5. Add a one-line description.
6. Click **Publish release**.

---

*That's the whole guide. Low-risk, buttons-and-boxes, no coding. If you've used Google Drive, you can use this.*
