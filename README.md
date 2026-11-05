# AeroSense · Interactive Prototype (static site)

A public, mobile-first showcase of the AeroSense interfaces: the caregiver phone, the phone docked on AeroSync, the AeroSync ventilator, the Apple Watch, and the clinician portal. All five share one simulated state.
**All data is simulated for a fictional patient. AeroSense is a student design concept, not a medical device.**

There is no build step, no framework and no third-party requests: one `index.html`, plus self-hosted fonts and icons.

## Deploy on Vercel
Use any one of these:
- **Drag and drop:** open vercel.com/new, choose to deploy without Git, and drop this folder in.
- **CLI:** run `npm i -g vercel`, then `vercel --prod` inside this folder.
- **Git:** push this folder to a repo and import it in Vercel.
  - Framework preset: **Other**.
  - Build command: *(none)*.
  - Output directory: **./** (the repo root).

`vercel.json` sends every non-file path to `index.html`, so deep links and page refreshes always load the app. It also gives the fonts long-lived caching. Vercel applies gzip or Brotli compression automatically; the page is roughly 100 KB compressed.

## Link to a specific interface + state
Use query parameters, e.g. `/?device=ventilator&state=high-pressure`. The address bar updates as visitors explore, so whatever they're looking at can be shared as-is. There's also a **Share this view** button in the Simulation panel.

| `device` | `state` |
|---|---|
| `phone` · `docked` · `ventilator` · `watch` · `portal` | `normal` · `secretions` · `low-spo2` · `high-pressure` · `critical-low-spo2` · `two-alerts` · `halo-offline` · `aerosync-offline` · `both-offline` · `delayed` · `restored` |

- **Shortcuts:**
  - `state=alarm` (or `critical`) → `high-pressure`.
  - `state=warning` (or `attention`) → `low-spo2`.
- **Guided scenarios:** add `scenario=normal-monitoring`, `scenario=oxygen-alert` or `scenario=ventilator-alarm`. These open the scenario card and its most relevant device.
- **Path form:** `/ventilator/alarm` and `/phone/normal` also work.

Examples:
- `/?device=phone&state=normal`
- `/?device=ventilator&state=alarm`
- `/?scenario=oxygen-alert`
- `/portal/high-pressure`

## Share preview
`og-image.png` is the link-preview image. Some platforms, Facebook and LinkedIn among them, require an absolute URL. After you deploy, change the `og:image` content in `index.html` to `https://<your-domain>/og-image.png`.
