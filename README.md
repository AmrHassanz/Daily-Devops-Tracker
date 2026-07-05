# Desk Lamp — Daily Habit & Study Tracker

A single-file HTML/CSS/JS habit tracker. No build tools, no frameworks.

## What it does
- **Tasks sidebar**: Qur'an, Sport, CCNA video, Decoding DevOps, 100 Days of Python — drag any onto a day.
- **Week board**: drop a task onto a day, tick it done, and add a short note about what you covered.
- **Curriculum checklists**: click "curriculum" on any task card to see a breakdown of that course and check off sections as you progress through it (independent of your daily log).
- **Stats**: current streak, today's completion %, total tasks logged.
- **Backup**: "Export backup" downloads a JSON file of everything; "Import backup" restores it. Useful before clearing your browser or moving devices, since data is stored in `localStorage` (per browser, not synced anywhere).

## Run it locally
Just open `index.html` in any browser — no server needed.

## Deploy to GitHub Pages
1. Create a new GitHub repository (e.g. `habit-tracker`).
2. Add `index.html` to the root of the repo and push:
   ```bash
   git init
   git add index.html
   git commit -m "Add habit tracker"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. On GitHub: go to the repo → **Settings** → **Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`. Save.
5. Wait a minute, then your tracker will be live at:
   `https://<your-username>.github.io/<repo-name>/`

## Sync across laptops (GitHub)
Click **⚙ Sync** in the header to open the settings panel:
1. Create a small GitHub repo just for this (can be private) — e.g. `habit-tracker-data`.
2. Generate a [fine-grained personal access token](https://github.com/settings/tokens?type=beta) scoped to **only that repo**, with **Contents: Read and write** permission. (Fine-grained tokens let you limit the blast radius if the token ever leaks — don't use a classic all-repo token.)
3. In the Sync panel, fill in:
   - **Repository** — `yourusername/habit-tracker-data`
   - **Branch** — `main` (or whatever your default branch is)
   - **File path** — `desklamp-data.json` (or anything you like)
   - **Personal access token** — paste it in
4. Click **Save & connect**. If the repo already has data, you'll be asked whether to load it; otherwise it pushes your current data to create the file.

After that, every change you make (ticking a task, adding a note, editing curriculum) auto-pushes to GitHub a couple seconds after you stop typing/clicking. Opening the page on another laptop (with the same repo + token entered) automatically pulls the latest version, and it also re-pulls whenever you switch back to the browser tab.

Use **Pull latest** to manually refresh from GitHub, or **Push now** to force an immediate push. **Disconnect** stops syncing but keeps your local data intact.

**Security note:** the token is stored in this browser's `localStorage`, and is only ever sent directly to GitHub's API from your browser — never to any other server. Anyone with access to the browser/device could read it from dev tools, so only use a token scoped to this one repo, and revoke it from GitHub's settings if you ever stop using a shared/public computer for this.

## Note on the course checklists
- **CCNA video (Sajad)**: I couldn't verify the exact channel/video numbering behind "Sajad CCNA 220", so the checklist instead follows Cisco's official CCNA 200-301 exam blueprint domains — a reliable way to tag which topic area each video falls under. Let me know the channel/playlist and I can rebuild it video-by-video.
- **Decoding DevOps (Imran Teli)**: built from the published Udemy course outline.
- **100 Days of Python (Angela Yu)**: the real course has 100 individual daily projects; I grouped them into 7 phases based on the published curriculum since listing all 100 would clutter the sidebar — happy to expand any phase into full daily items if you want.
