# Live Stream Monitor

A single-file, client-side web app for monitoring multiple live streams (a multiview video wall).
No backend or build step — it's one HTML file served as a static page.

## Layout
- **`public/index.html`** — the app; this is the file that gets served. **Edit this one.**
- **`live_stream_monitor_V*.html`** — versioned snapshots kept for history (not published).

## Hosting (Cloudflare Pages)
The site is hosted on **Cloudflare Pages**, connected to this GitHub repo:

- Live URL: **https://live-stream-monitor.pages.dev/**
- Build settings in the Cloudflare dashboard: **Framework preset: None**, **Build command: (empty)**,
  **Build output directory: `public`** (so only `public/` is published — nothing else in the repo is exposed).
- Every push to `main` auto-deploys in ~1 minute.

(GitHub Pages is intentionally disabled — Cloudflare is the single host.)

## Updating the site
Edit `public/index.html`, then:
```bash
cd "C:/Users/adamb/Desktop/Multiview"
git add public/index.html
git commit -m "Describe the change"
git push
```
Cloudflare redeploys automatically.

> To keep a numbered snapshot, copy `public/index.html` to `live_stream_monitor_V<N>.html` and commit both.

## Notes
- **Settings are per-browser** (stored in `localStorage`), so each visitor gets their own toggles, presets, etc.
- This is an **unlisted** site: anyone with the link can open it (no login gate). Ask to switch on
  Cloudflare Access if you later want to restrict it to specific email addresses.
- **Playback / CORS:** served over HTTPS with HTTPS streams (no mixed content). Video playback relies on
  the stream provider sending permissive CORS headers. If tiles stay gray with `Access-Control-Allow-Origin`
  errors in the console, that's on the provider's side, not this file.
