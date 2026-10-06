# askdex-addin-icons

Public host for the **AskDex for Office** add-in ribbon icons (GitHub Pages).

## Why this repo exists

The add-in runs on an internal domain (`office.askdex.findex.solutions`) that is not
reachable from the public internet. When the add-in is deployed centrally via the
Microsoft 365 admin center (Integrated Apps), **Microsoft's cloud fetches the icon URLs
from the manifest** to snapshot and render the ribbon button on desktop clients. Because
it cannot reach the internal domain, the desktop ribbon icon came up blank for everyone.

Hosting the icons here (public, HTTPS, CDN-backed) lets Microsoft fetch them. The add-in's
`manifest.xml` points `IconUrl`, `HighResolutionIconUrl` and the ribbon `bt:Image` resids
at `https://fdxinnovationhub.github.io/askdex-addin-icons/icon-<size>.png`. Everything else
(task pane, API) stays internal and is loaded device-side on the corporate network.

## Files

`icon-16.png`, `icon-32.png`, `icon-64.png`, `icon-80.png`, `icon-128.png` — the AskDex
speech-bubble mark, transparent background, legible on both light and dark ribbons.

## Updating

Replace a PNG and push to `main`; GitHub Pages redeploys. Because manifest icon URLs are
snapshotted by Microsoft at validation time, after changing an icon you must also bump the
add-in manifest `<Version>` and click **Update** on the app in Integrated Apps so Microsoft
re-fetches. Prefer changing the filename (e.g. `icon-32.v2.png`) for a guaranteed refresh.

## Manifest

`manifest.xml` is also published here so Integrated Apps can validate it by URL
(the add-in's own `office.askdex…` domain is internal and not publicly fetchable):

    https://fdxinnovationhub.github.io/askdex-addin-icons/manifest.xml

Source of truth is `askdex-add-in/manifest.xml` in the ask-dex-M365 repo. When that
changes, copy it here and push, then bump `<Version>` and re-validate in Integrated Apps.
