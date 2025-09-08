# Realtime Countdown (for Glide Web Embed)

A single-file, zero-dependency **realtime countdown** that accepts a target datetime through the URL query string. Perfect for embedding in Glide via the **Web Embed** component.

## Quick Start (Local test)
Open `index.html` directly in a browser. It will default to 1 hour from now.
You can also pass a target datetime, e.g.:
```
index.html?target=2025-09-30T18:00:00+07:00
```

---

## Deploy Option A — GitHub Pages (free)
1. Create a new **public** repository on GitHub (e.g., `countdown`).
2. Upload `index.html` to the repository and commit.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set:
   - Source: `Deploy from a branch`
   - Branch: `main` (root)
5. Wait 1–2 minutes. Your site will be live at:
   ```
   https://<username>.github.io/<repo>/
   ```
6. Test with a target:
   ```
   https://<username>.github.io/<repo>/?target=2025-09-30T18:00:00+07:00
   ```

---

## Deploy Option B — Netlify (free, drag‑and‑drop)
1. Go to https://app.netlify.com/ and sign in.
2. Click **Add new site → Deploy manually (Drag and drop)**.
3. Drag `index.html` into the drop area.
4. Netlify will give you a site URL like `https://<random-name>.netlify.app/`.
5. Test with a target:
   ```
   https://<random-name>.netlify.app/?target=2025-09-30T18:00:00+07:00
   ```

### (Optional) Continuous deploy from GitHub
- Click **Add new site → Import an existing project**, connect your GitHub repo.
- Build settings: none required (static file only).
- Netlify will auto‑deploy on every commit to `main`.

---

## Deploy Option C — Vercel (free)
1. Go to https://vercel.com/ and sign in.
2. **New Project → Import** your GitHub repo or **Deploy** a new project.
3. Framework preset: `Other` (no build step).
4. Deploy → You get `https://<project>.vercel.app/`.

---

## Using in Glide
1. In **Data Editor**, add a **Template** column, e.g. `Countdown URL` with:
   ```
   https://<your-site>/?target={Target At}
   ```
   Replace `{Target At}` with your Date/Time column.
2. In your screen **Detail View**, add **Web Embed** and bind the URL to `Countdown URL`.
3. Done — your countdown now ticks every second inside the app.

---

## URL Parameters
- `target`: ISO datetime or Unix timestamp.
  - Examples:
    - `?target=2025-09-30T18:00:00+07:00`
    - `?target=1735641600` (Unix seconds)
- `label`: Title above the timer (e.g., `?label=Ticket%20Sales%20Close`)
- `fg`, `bg`, `accent`: Hex colors to theme the page.
  - Example: `?fg=%23ffffff&bg=%230b0c10&accent=%2300ffc3`

---

## Notes
- The timer runs purely on the client, suitable for visual countdowns.
- For mission‑critical cutoffs, enforce logic in Glide/Make backend (e.g., hide purchase button when server time has passed).
