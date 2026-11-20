# LA Shake Watch

A small web map of every earthquake recorded in Southern California in the past 7 days, with the distance of each one from USC.

SSCI 591 Web & Mobile GIS · Project 5 (Take your web GIS app to the cloud) · Yuqi (Jeff) Ge · Fall 2026

## What it does

- Loads the live USGS `all_week` GeoJSON feed in the browser (no API key) and keeps only quakes inside a Southern California box.
- Circle size = magnitude; red = last 24 hours, amber = earlier this week; USC is the yellow dot.
- A status line shows how many quakes, the biggest one, and the one closest to USC. A button filters to M2.5+.
- The bar at the top says where the page is served from (a local file, or AWS Amplify Hosting).

## Cloud job: host the page

The page is a single static `index.html`, hosted on **AWS Amplify Hosting** and connected to this GitHub repository. Every push to `main` triggers a new build and deploy. No build step is needed.

`customHttp.yml` adds security headers (HSTS, no-sniff, no framing, a Content Security Policy that only allows Leaflet from unpkg, OpenStreetMap tiles, and the USGS feed).

## Files

- `index.html` — the app (Leaflet 1.9.4 with Subresource Integrity hashes)
- `customHttp.yml` — Amplify custom headers
- `README.md` — this file

## Credits

Data: U.S. Geological Survey earthquake feed. Basemap: © OpenStreetMap contributors. Map library: Leaflet. AI tools: Claude (Anthropic) helped draft the code and this README; I reviewed and tested it.
