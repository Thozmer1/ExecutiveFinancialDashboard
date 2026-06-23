# Innovien Executive Financial Dashboard — Vercel Deploy

Self-contained static HTML dashboard, deployed to Vercel via GitHub.

## One-time setup (first deploy)

### Step 1 — Create a private GitHub repo

1. Go to [github.com](https://github.com) (sign up if you don't have an account)
2. Click "+" top right → "New repository"
3. Name it `innovien-dashboard` (or any name)
4. Set visibility to **Private** (keeps the source files non-discoverable; the deployed URL is still public per your call, but the source repo doesn't need to be)
5. Skip the README/license/.gitignore options
6. Click "Create repository"

### Step 2 — Upload the dashboard files

On the new repo's empty page, click "uploading an existing file" and drag in these three files from this folder:

- `index.html`
- `vercel.json`
- `README.md`

Click "Commit changes" at the bottom.

### Step 3 — Connect Vercel

1. Go to [vercel.com](https://vercel.com) and sign up (use "Sign in with GitHub" — it'll connect automatically)
2. Once signed in, click "Add New..." → "Project"
3. Vercel shows your GitHub repos — click "Import" next to `innovien-dashboard`
4. Vercel auto-detects this is a static site. **Don't change any settings.** Just click "Deploy"
5. ~30 seconds later, Vercel gives you a URL like `innovien-dashboard.vercel.app`

That URL is your live dashboard. Share it with Camryn and Josh.

## Monthly update flow

After each monthly close, when Claude rebuilds the dashboard:

1. The new `Innovien Executive Dashboard — <Month> YYYY.html` lands in your `Innovien CFO` folder
2. Open this `vercel-deploy` folder and replace `index.html` with the new one (rename the file to `index.html`)
3. On GitHub, navigate to the `innovien-dashboard` repo
4. Drag the new `index.html` onto the page (it'll prompt you to commit the change)
5. Click "Commit changes"
6. Vercel auto-deploys within 60 seconds — the URL stays the same; the content updates

That's it. Camryn and Josh always have the same bookmark; the data behind it is current.

## Notes

- **Caching:** The `vercel.json` sets a 5-minute browser cache. If leadership refreshes the URL right after you push an update and don't see new numbers, they can hard-refresh (Ctrl+Shift+R / Cmd+Shift+R) or wait 5 minutes.
- **Dependencies:** The dashboard loads Chart.js from a public CDN (`cdn.jsdelivr.net`). It needs internet access on the viewer's device. If Innovien's network blocks that CDN, charts won't render — let me know and I'll inline the library (adds ~250KB).
- **Privacy:** This deployment is public-URL accessible to anyone with the link. Don't post it in Slack or email it to large groups. If sharing scope expands, the right next step is enabling Vercel's password protection (Vercel Pro plan, $20/mo).
- **Logs:** Vercel records every page view (IP + timestamp) in the Project's Analytics tab. Useful if you want to see whether Camryn and Josh actually open it.
- **Versioning:** Each commit you push to GitHub creates a Vercel "deployment" with its own preview URL. The main production URL always serves the latest commit. So you have a full history of every month's snapshot if you ever need to look back.
