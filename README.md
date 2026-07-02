# Live Stream Monitor

A single-file, client-side web app for monitoring multiple live streams (a multiview video wall).
No backend or build step — it's one HTML file served as a static page.

- **`index.html`** — the page that gets served (this is what GitHub Pages hosts).
- **`live_stream_monitor_V14.html`** — the current versioned snapshot (kept for history).

## Hosting on GitHub Pages

### One-time setup
1. Create a new repository on GitHub (e.g., `live-stream-monitor`). It can be public or private
   (Pages works with private repos on paid plans; public is simplest and free).
2. From this folder, push the code:
   ```bash
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git branch -M main
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages**. Under "Build and deployment", set **Source: Deploy from a branch**,
   **Branch: `main`**, **Folder: `/ (root)`**, then **Save**.
4. Wait ~1 minute. Your site will be live at:
   `https://<your-username>.github.io/<your-repo>/`

### Updating the site later
Edit `index.html`, then:
```bash
git add index.html
git commit -m "Describe the change"
git push
```
GitHub Pages redeploys automatically within a minute or so.

> Tip: going forward, treat `index.html` as the working file. When you want a numbered snapshot,
> copy it to `live_stream_monitor_V<N>.html` and commit both.

## Notes
- **Settings are per-browser** (stored in `localStorage`), so each visitor gets their own toggles,
  presets, hidden shows, etc.
- **Anyone with the link can open it.** Preset stream URLs are visible in the page source (they're
  already public CDN links). The **API Login** still requires each user's own credentials.
- **Playback / CORS:** the site is served over HTTPS and streams are HTTPS, so there's no mixed-content
  issue. Video playback relies on the stream provider's servers sending permissive CORS headers
  (`Access-Control-Allow-Origin`). If tiles stay gray with CORS errors in the browser console (F12),
  that's a request for the stream provider to allow the site's domain — not a change to this file.
