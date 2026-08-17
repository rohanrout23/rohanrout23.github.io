# Rohan Rout — AI Mentorship Website

A single-page, plain HTML/CSS/JavaScript mentorship platform website. No frameworks, no build step, no npm install required.

## Project Structure

```
project/
├── index.html              # Everything: markup, CSS, JS — open this file to view the site
├── assets/
│   ├── images/
│   │   ├── rohan-nav-logo.jpg
│   │   ├── rohan-mentor-card.jpg
│   │   ├── rohan-about-avatar.jpg
│   │   └── rishav-mentor-card.jpg
│   └── docs/
│       ├── Rohan_Rout_Resume.pdf
│       └── DSA_Success_Map.xlsx
└── README.md                # This file
```

## How to Open in VS Code

1. Unzip this folder anywhere on your computer.
2. Open VS Code → File → Open Folder → select the `project` folder.
3. Right-click `index.html` → "Open with Live Server" (install the free **Live Server** extension first if you don't have it) — this gives you auto-refresh on save.
   - Alternative: just double-click `index.html` to open it directly in your browser. It works fine without Live Server too, since there's no build step.

## Important: Keep the folder structure intact

`index.html` references images and documents via relative paths like `assets/images/rohan-nav-logo.jpg`. If you move `index.html` without the `assets/` folder, images and downloads will break. Always deploy/upload the **entire folder**, not just `index.html`.

## Deploying (GitHub Pages — free)

1. Create a GitHub repo named exactly `yourusername.github.io`.
2. Upload the entire contents of this folder (index.html + the assets folder) to the repo root.
3. In repo Settings → Pages, set source to your main branch.
4. Your site goes live at `https://yourusername.github.io` within a minute or two.

## What's currently static (no backend)

- The contact form is wired to **Formspree** — you still need to replace `YOUR_FORM_ID` in `index.html` with your real Formspree form ID (search for `YOUR_FORM_ID` in the file).
- "Book on WhatsApp" buttons are plain `wa.me` links — no backend needed for these.
- The resume and DSA roadmap downloads are direct links to files in `assets/docs/`.

## Editing

Everything is in `index.html` — CSS is in the `<style>` block at the top, JavaScript is in the `<script>` block near the bottom. No compiling, no `npm install`, no build process. Just edit and refresh.
