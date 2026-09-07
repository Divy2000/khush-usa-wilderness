# Khush, pick your American wilderness — May vs December 2027

A single-file photo-and-facts comparison board for US camping-and-landscape trips for Khush (Edmonton, YEG) and his Dallas friend: May 15–31, 2027 vs December 2027, flying to a rendezvous airport vs Khush flying to Dallas and road-tripping in the HR-V. It scores every option on the same seven weights and shows the data; it makes no recommendation.

`index.html` is the whole site: HTML, CSS, data and logic inlined, no build step, no framework, no API keys. The only external request is Google Fonts (Fraunces and Alegreya Sans); if fonts are blocked the page falls back to system serif/sans.

## Deploy to GitHub Pages (new repo)

1. Create a new empty repository (keep it separate from the Big Bend sites).
2. Copy `index.html` (and this README) into the repository root.
3. Commit and push to `main`.
4. Repository → Settings → Pages → Source: "Deploy from a branch" → Branch `main`, folder `/ (root)` → Save.
5. The site appears at `https://<user>.github.io/<repo>/` within a minute or two. Share `…/#dec` to open it on December.

Netlify Drop, Cloudflare Pages or any static host also work: upload the one file.

## Editing the content

Everything editable is in the `<script>` block near the bottom of `index.html`, in plain JavaScript objects:

| Object | What it holds |
|---|---|
| `RESEARCHED` | The "last researched" date shown in the Verify section |
| `WEIGHTS` | The seven scoring dimensions and their percentages (must total 100) |
| `FLIGHTS` | Nonstops from YEG and the DFW note |
| `SURCHARGE_PARKS` | Parks charging the 2026 nonresident fee |
| `DESTINATIONS` | One object per option: seasons, scores per season (0–10), rendezvous/driving, weather, drawback, camping, access rules with status + source URL, route legs, sources |
| `CUT` | Options considered and cut, per season |
| `COLORADO` | Rows in the Denver reality check |
| `CATEGORIES` | Category winners per season (by destination `id`) |
| `VERDICT` | Final recommendation copy and alternates |
| `LEDGER` | The verify-before-booking list |

Change a score or a weight and every ranking, bar, axis and table re-computes on load. Status labels for facts are `confirmed` (published for 2027 or a completed event), `rule2026` (in force now, re-check for 2027), `typical` (historical pattern) and `tbd`.

To add a destination, copy an existing object, give it a unique `id`, set `mode` to `fly` or `drive`, list the `seasons` it competes in, and add a `scores.may` and/or `scores.dec` block. Optional `pair` links a fly-in and a drive-from-Dallas version of the same place.

## Photographs and illustrations

`GALLERIES` (in the `photos.js` block of `index.html`) holds 10–16 photographs for each of the 21 options — exact Wikimedia Commons filenames, all public domain (US National Park Service uploads) or Creative Commons. The first entry of each gallery is the default image in comparisons. Images load through `Special:FilePath/<file>?width=…`; each carries a "Source" chip linking to its Commons file page with full attribution, and the Sources section lists every file. Underneath every image sits a procedurally drawn SVG keyed to the destination's `art` type, so a failed load leaves the illustration rather than a broken image.

Galleries are season-matched where Commons had them: Zion in May, Yosemite Falls photographed May 30, bison calves in Lamar Valley, snow on the Sangre de Cristos above the dunes, Bryce after snow, Zabriskie Point in winter light, Sierra Blanca snow-capped over White Sands, the Everglades in the dry season, Padre Island in November.

Note for previewing: the Claude app's in-chat preview blocks external images, so photos only appear on the deployed site or when the file is opened in a normal browser.

## Verification done before publishing

- Rendered and exercised with headless Chromium at 390×844 and 1366×860: season switch, row expansion, keyboard operation (arrow keys on the dial, Enter/Space on Compare), 2–3-way comparison, no horizontal overflow, `prefers-reduced-motion` honored.
- Official/source URLs for every date and rule, plus 250 Wikimedia Commons photo pages, all taken from pages retrieved during research on September 6, 2026 (NPS, Recreation.gov, Yellowstone National Park Lodges, TPWD, USFWS, New Mexico State Parks, Big Bend Sentinel, FlightConnections, Simple Flying, American Airlines).

## What still needs a human before booking

- Confirm seasonal nonstops for 2027 (YEG–SFO, YEG–SLC, YEG–PSP, YEG–HNL/OGG, DFW–PSP, DFW–KOA).
- Re-check the nonresident fee rule and every 2026 reservation window once 2027 pages publish.
- Re-run drive times with live routing; every figure on the site is approximate.
