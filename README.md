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

- "Book on WhatsApp" buttons are plain `wa.me` links — no backend needed for these to work.
- The resume and DSA roadmap downloads are direct links to files in `assets/docs/`.

## Setting up your data store (Supabase) + contact form (Formspree)

Your contact form and booking buttons are already wired in the code to save data — you just need to create two free accounts and paste in your own keys. Takes about 10 minutes.

### Part A: Supabase (stores messages + booking clicks in a real database)

1. Go to **supabase.com** → Sign up free → "New Project".
2. Give it any name, set a database password (save it somewhere safe), pick a region close to you (e.g. Singapore or Mumbai), and wait ~2 minutes for it to finish setting up.
3. In the left sidebar, click **SQL Editor** → "New query", paste this in, and click **Run**:

```sql
create table messages (
  id uuid primary key default gen_random_uuid(),
  created_at timestamptz default now(),
  name text,
  email text,
  experience_level text,
  message text
);
alter table messages enable row level security;
create policy "Allow public insert" on messages for insert to anon with check (true);

create table bookings (
  id uuid primary key default gen_random_uuid(),
  created_at timestamptz default now(),
  mentor text
);
alter table bookings enable row level security;
create policy "Allow public insert" on bookings for insert to anon with check (true);
```

This creates two tables and allows your public website to write to them (but not read others' data — standard safe setup for a public form).

4. In the left sidebar, click **Settings → API**. Copy the **Project URL** and the **anon public** key (a long string).
5. Open `index.html` in VS Code, search for `PASTE_YOUR_SUPABASE_URL_HERE` and replace it with your Project URL (keep the quotes). Do the same for `PASTE_YOUR_SUPABASE_ANON_KEY_HERE` with your anon key.
6. To see your data later: Supabase dashboard → **Table Editor** → click `messages` or `bookings`.

### Part B: Formspree (emails you when someone submits the contact form)

1. Go to **formspree.io** → sign up free → create a new form pointed at your email.
2. Copy the form endpoint (looks like `https://formspree.io/f/abcd1234`).
3. In `index.html`, find `YOUR_FORM_ID` (inside `data-formspree="..."` on the form tag) and replace the whole URL with your real one.

### After editing

Save the file in VS Code, then re-upload the updated `index.html` to your GitHub repo (Add file → Upload files → drag in `index.html` → Commit). GitHub Pages will automatically redeploy within a minute or two.


## Editing

Everything is in `index.html` — CSS is in the `<style>` block at the top, JavaScript is in the `<script>` block near the bottom. No compiling, no `npm install`, no build process. Just edit and refresh.
