# Idle Saga — Event Timeline

A tiny, single-file web app to track recurring **daily** and **weekly** events in *Idle Saga* (GameHollywood). Server times (UTC+8) are converted to your local clock, with a live "now" line, a daily-reset marker, and four switchable views.

**Live:** https://saintecroquette.github.io/idle-saga-helper/

## Features

- **Four views** (tab to switch, choice is remembered):
  - 🗂️ **Table** — events × 7 days matrix, most compact
  - 📊 **Timeline** — one swimlane per event (no overlap), per-day
  - 📅 **Agenda** — time-grid calendar with side-by-side packing for collisions
  - ⏭️ **Up Next** — chronological list with live countdowns
- Live **now** line and **next event** hero with countdown
- **Daily reset** marker (00:00 server time) shown in every view
- All times anchored to **your computer's clock**

## Calibration

The server runs ahead of your local clock by a fixed offset. Edit one constant in
`index.html` if it ever drifts:

```js
const SERVER_AHEAD_HOURS = 14; // server clock = your computer's clock + 14h
```

(Observed: the game showed 16:00 while this computer showed 02:00 → 14h.)

## Editing events

Events live in the `EVENTS` array near the top of the `<script>` in `index.html`.
Each has a name, color, list of `[start, end]` slots (in **server** time), and a
`days` value (`"daily"`, `"satOnly"`, or `"exceptSat"`). Long availability windows
get `window: true` to render as a background band.

## Running locally

It's a static file — just open `index.html` in a browser. No build step.
