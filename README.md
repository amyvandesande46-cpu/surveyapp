# JPM Odour Survey App (PWA)

Installable, offline-capable field app for IAQM timed odour sniff-testing surveys.

## Contents
- `index.html`, `app.js`, `app.css` — the app (React, self-contained)
- `vendor/leaflet/` — the map engine (bundled locally, no CDN needed)
- `manifest.webmanifest`, `service-worker.js`, `icons/` — installable + offline
- Survey data is stored on the device (browser localStorage). Use in-app **Export** (JSON) for backups; **Import JSON** restores them.

## Map
- Real basemap via Leaflet, with **Street** and **Satellite** layers (switch top-right).
- Tap the map to drop a point (or set the source), drag markers to move, tap a point to open it.
- Basemap tiles need signal; **offline the tiles go grey but your points, markers and all data still work**. The app shell itself (and Leaflet) are cached, so it always loads.

## Run locally (quick test)
A service worker must be served over http(s), not opened as a file:

    python3 -m http.server 8080

then visit http://localhost:8080 on the same machine.

## Host it (to install on a phone)
Any static HTTPS host works. Options:
- **Cloudflare Pages + Cloudflare Access** — private: only email addresses you approve can open it (free up to 50 users).
- **Netlify Drop** (app.netlify.com/drop) — drag this folder on; gives an unguessable URL.
- **GitHub Pages** — easy, but the site is publicly reachable even from a private repo.

## Install on a phone
- **iPhone/Safari:** open the URL → Share → **Add to Home Screen**.
- **Android/Chrome:** open the URL → menu ⋮ → **Install app**.
Location (GPS) needs permission granted and the OS location service on.

## Shipping an update
Bump `CACHE = 'jpm-odour-v2'` to `v3` in `service-worker.js` and re-upload, so installed devices refresh their cache.
