# Philly on Foot

A single-file interactive guide to Philadelphia for Isabella's Wharton exchange (21 Aug – 11 Oct 2026), built around her flat at 13th & Walnut.

Open `index.html` in any browser. No server, no network: fonts are inlined, the map is hand-drawn SVG (schematic Center City grid, projected from lat/lon and rotated ~9° so the streets run square).

## What's in it

- **Map** – 20 neighbourhoods (click for vibe / known-for / main things / everything to eat and drink there), ~250 pins filtered by type (restaurant, bar, cafe, shop, see, do) and vibe (your London taste, hidden/locals, famous Philly go-to, institution, dive, new 2025-26, on your Apple Maps list, splurge), priority 1–3, scroll-zoom / drag-pan, tooltips, walk time from home on everything.
- **Eat & Drink / See & Do** – card lists with the same filters plus neighbourhood and sort (priority / nearest / neighbourhood), a "the move" tip on each card, and a star shortlist saved in `localStorage`.
- **Walks** – 8 routes drawn on the map with the stops lit up.
- **Calendar** – the seven weeks dated (Phillies, Eagles, Flyers, Union, Penn football, Fringe, First Fridays, 250th events).
- **Top 20** – ranked, click-through to the map.
- **Practical** – transport, grid, BYOB, tipping, safety, weather.

## Editing

Everything editable lives in `src/data.js` (neighbourhoods, places, walks, calendar, top-20, practical). A place is one object:

```js
{n:'Name', t:'eat|drink|cafe|shop|see|do', h:'<hood key>', at:[lat,lon] /* or 'N/Street' grid string */, addr:'…', tags:['you','hidden',…], p:1, price:'$$', d:'blurb', tip:'the move'}
```

Grid strings (`'18/Locust'`, `'W38/Walnut'`) resolve through a calibrated model of the Center City / South Philly / West Philly grid; explicit `[lat,lon]` for anything off-grid (Fishtown, diagonals, further out).

Then `python3 build.py` to regenerate `index.html`. `src/fonts.css` is the base64 @font-face block (DM Serif Display, Geist, Geist Mono; all OFL).

## Sources

Infatuation Philadelphia (best-restaurants Apr 2026, wine bars Jun 2026, cocktail bars Jul 2026), Resy and Philly Mag 2026 hit lists, the Inquirer's 2025 and 2026 closure lists, and the published 2026 Phillies / Eagles / Flyers / Union / Penn schedules, plus Isabella's own Apple Maps "Philly – Restaurants to try" / "Bars to try" guides. Places marked "check address" are 2026 openings whose exact address was not confirmed.
