# Philly on Foot

A single-file interactive guide to Philadelphia for a seven-week Wharton exchange (21 Aug – 11 Oct 2026), built around a base at 13th & Walnut, Center City. Opinionated, personal, and honest about what to skip.

Open `index.html` in any browser (or the private artifact link). Fonts are inlined; the map is a real Leaflet basemap (CARTO Positron light / Dark Matter dark tiles, OpenStreetMap data) with neighbourhood polygons and pins overlaid. Offline, or anywhere that blocks outside hosts (the claude.ai artifact sandbox), it falls back to a hand-drawn schematic SVG map of the same data (projected from lat/lon and rotated ~9° so the grid runs square).

## What's in it

- **Map** – 28 neighbourhoods (23 on the map, 5 further out) (click for vibe / known-for / main things / everything to eat and drink there), ~250 pins filtered by type (restaurant, bar, cafe, shop, see, do) and vibe (your London taste, hidden/locals, famous Philly go-to, institution, dive, new 2025-26, on your Apple Maps list, splurge), priority 1–3, scroll-zoom / drag-pan, tooltips, walk time from home on everything.
- **Eat & Drink / See & Do** – card lists with the same filters plus neighbourhood and sort (priority / nearest / neighbourhood), a "the move" tip on each card, and a star shortlist saved in `localStorage`.
- **Neighbourhoods** – all 28 ranked in the order to spend time on them, with verdict (go / once / pass through / skip), when to go, and the closest London and New York equivalent for vibe; the map panel carries the full honest write-up and an Avoid list.
- **Walks** – 8 routes drawn on the map with the stops lit up.
- **Music** – the scene, ten music bars/rooms, and every notable show 21 Aug – 11 Oct 2026 across ~20 venues (compiled from venue calendars mid-Aug 2026).
- **Dates** – the fixed things (sport fixtures, festivals, standing weekly rhythms) grouped, not a week-by-week plan.
- **Top 20** – ranked, click-through to the map.
- **Practical** – transport, grid, BYOB, tipping, safety, weather.

## Editing

Everything editable lives in `src/data.js` (neighbourhoods, places, walks, calendar, top-20, practical). A place is one object:

```js
{n:'Name', t:'eat|drink|cafe|shop|see|do', h:'<hood key>', at:[lat,lon] /* or 'N/Street' grid string */, addr:'…', tags:['you','hidden',…], p:1, price:'$$', d:'blurb', tip:'the move'}
```

Most pins were geocoded from their street address via OpenStreetMap Nominatim (Aug 2026); a handful of places carry exact Apple Maps coordinates. Grid strings (`'18/Locust'`, `'W38/Walnut'`) resolve through a calibrated model of the Center City / South Philly / West Philly grid for anything not geocoded.

Then `python3 build.py` to regenerate `index.html`. `src/fonts.css` is the base64 @font-face block (DM Serif Display, Geist, Geist Mono; all OFL).

## Sources

Infatuation Philadelphia (best-restaurants Apr 2026, wine bars Jun 2026, cocktail bars Jul 2026), Resy and Philly Mag 2026 hit lists, the Inquirer's 2025 and 2026 closure lists, and the published 2026 Phillies / Eagles / Flyers / Union / Penn schedules. Places marked "check address" are 2026 openings whose exact address was not confirmed.
