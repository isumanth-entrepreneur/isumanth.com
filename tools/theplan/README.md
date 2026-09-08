# The Plan

Prototype of the morning brief as a personal web app. Lives at `tools/theplan/` on isumanth.com.

## Run it locally

Open `index.html` straight from Finder (double-click), or serve the folder:

```
cd tools/theplan && python3 -m http.server 8080
```

then open http://localhost:8080. Ticks, added items and notes are kept in the browser (localStorage), so they stay put between opens on the same device.

## Add to Dock / home screen

Mac Safari: File > Add to Dock. iPhone Safari: Share > Add to Home Screen. Both open it as a standalone app using `manifest.webmanifest` and the icon PNGs.

## How a day gets in

Two files per morning:

1. `data/YYYY-MM-DD.js` sets `window.THEPLAN.days["YYYY-MM-DD"]` (see the two existing days for the shape: headline, terrain SVG markup, acts, money tiles, sections).
2. `data/index.js` lists the dates; append the new one.

Section kinds: `check` (needs, plan, waiting: get checkboxes), `list` (resolved, good news, watch), `html` (the tracker table).

Item ids are what make carry-over work. Reuse the same id when the same item appears on a later day, and the app shows "since Sep 7" instead of a duplicate. Any open item from an earlier day whose id is missing from the latest day shows under "Still open from earlier days". Put an id in the day's `closed` array when the brief found it resolved, and the app marks it done without a tick.

## Not yet

Password, and a server so ticks sync between phone and Mac. Both come with the worker in the next step.
