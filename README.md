# JPM Odour Survey App (PWA)

An installable, offline-capable field app for IAQM timed odour sniff-testing surveys.

## What's in here
- `index.html`, `app.js`, `app.css` — the app (React, self-contained, no internet needed once loaded)
- `manifest.webmanifest`, `service-worker.js`, `icons/` — make it installable + work offline
- Data is stored on the device (browser localStorage). Use in-app **Export** (JSON) for permanent backups; **Import JSON** restores them.

## Run it locally (quick test)
A service worker needs to be served over http(s), not opened as a file. From this folder:

    python3 -m http.server 8080

then visit http://localhost:8080 on the same machine.

## Host it (so you can install it on a phone)
Any static host works. Easiest is GitHub Pages:
1. Create a repo and upload the contents of this folder (index.html at the repo root, or in a /docs folder).
2. Settings -> Pages -> deploy from branch, choose the folder.
3. Open the HTTPS URL on your phone.

Other options: Netlify (drag-and-drop this folder), Cloudflare Pages, or any web server. HTTPS is required for install + offline.

## Install on a phone
- **Android/Chrome:** open the URL, menu -> "Add to Home screen" / "Install app".
- **iPhone/Safari:** open the URL, Share -> "Add to Home Screen".

After the first load it works with no signal. To ship an update, change `CACHE = 'jpm-odour-v1'` to `v2` in service-worker.js so devices refresh their cache.

## Notes
- GPS, vibration and the sample-cue beep use real device features and work once installed.
- The site map is an offline plan view (no street tiles). A street/satellite basemap can be added later if you host with a map provider.
