# Neon Reef (flappy-fish)

A neon, underwater take on Flappy Bird. Tap to swim, dodge the glowing coral, grab pearls for bonus points and earn medals. It installs to your phone's home screen as a progressive web app (PWA) and plays offline.

## Play

- **Phone:** tap anywhere to swim.
- **Desktop:** click, Space or ↑ to swim. P pauses, M mutes.
- Passing a coral pillar is worth 1 point and a pearl is worth 2.
- Medals: Bronze 10, Silver 20, Gold 30, Platinum 40.
- Your best score and sound setting are saved on the device.

## Install on your phone

1. Open the deployed URL.
2. **iPhone (Safari):** tap Share, then **Add to Home Screen**.
3. **Android (Chrome):** tap **Install App** on the start screen, or use the browser menu and choose **Install app**.

Once installed it opens full screen and works without a connection.

## Deploy on Vercel

It's a static site with no build step.

1. In Vercel, choose **Add New → Project** and import this repo.
2. Leave **Framework Preset** as **Other**. Leave the build command empty and the output directory as the default (the repo root).
3. Deploy.

`vercel.json` sets the cache headers the service worker and manifest need.

## Run locally

```bash
npx serve .
```

Then open the printed URL. Service workers only run over `http://localhost` or HTTPS, not from a `file://` path.

## Project layout

```
index.html             The whole game (canvas, styles, logic)
manifest.webmanifest   PWA manifest (name, colours, icons)
sw.js                  Service worker for offline play
vercel.json            Vercel headers
icons/                 App icon (SVG source and PNG sizes, including maskable)
fonts/                 Self-hosted Press Start 2P and Orbitron (SIL OFL 1.1)
```

## Updating the game

After you change any file, bump `CACHE_VERSION` in `sw.js` (for example `v1` to `v2`). That way installed copies pick up the new version the next time they open online.

## Tuning

The difficulty constants are at the top of the script in `index.html`: `GAP`, `SPEED`, `G` (gravity), `FLAP`, `SPACING`, `PEARL_CHANCE`, `PEARL_POINTS` and `MEDALS`.
