---
name: add-attraction
description: Add, replace, move or remove an attraction in the Black Forest trip site (single-page Hebrew index.html). Use whenever the user asks to add/swap/drop a sight, cable car, park, pool or other stop on a trip day, so every place on the page that mentions attractions stays in sync.
---
# Add / replace an attraction (Black Forest site)

An attraction appears in **several places** in `index.html`. Update all of them, then run the route check.
All visible text is Hebrew; wrap Latin names that reorder inside `<bdi>`.
Party: 2 adults, kids 3, 7, 10 (`inAdults=2`, `inKids=2`, `inSmall=1`).

## 1. Research first (WebSearch; official site first)
For the planned date collect:
- Opening days and hours, last entry / last ascent.
- Prices **by age**: adult, child 6–15, child 3–5.
- Card status:
  - **Hochschwarzwald Card** ("הכרטיס האדום"; free / discount, valid only in Hochschwarzwald; booking portal mein.hochschwarzwald.de/en).
  - **SchwarzwaldCard** ("⚫", the paid card).
- Whether advance booking is needed, with the official **English** booking URL.
- Stroller suitability.
- Exact location.
- A Wikipedia/Commons photo (not an SVG).

## 2. Day timeline (`<article class="day" id="dayN">`, `<ol class="timeline">`)
Add an `<li class="key">` at the right time, following the existing pattern:
```html
<li class="key"><time>HH:MM</time><div class="what"><b>EMOJI שם<span class="pram ok|part|no">👶 …</span></b><small class="pn">stroller note</small><small>description · <a class="nav" target="_blank" rel="noopener" href="https://www.google.com/maps/dir/?api=1&travelmode=driving&destination=PLACE">🗺️ גוגל מפות</a></small><small class="bk">📅 card status · booking note + <a href="EN_URL" target="_blank" rel="noopener">EN ↗</a> · ⚫ SchwarzwaldCard: …</small></div></li>
```
- Use `travelmode=walking` and "🚶 ניווט ברגל" for walking legs.
- Waze buttons are added automatically next to driving Google Maps `dir` links; don't add them by hand.
- Fix the `drive` rows before and after the new stop.
  - Times = OSRM (router.project-osrm.org) ×1.1, rounded to 5 min.
  - Shift every later time in the day; departure stays 09:00.
- The hero "אטרקציות" count is computed from the `small.bk` lines automatically.

## 3. Cost model (`var ATTR = { … }` in the costs script)
- Add the attraction with prices per person: `key: { name: "שם", p: [adult, kid6_15, kid3_5] }`.
  Use 0 when it is in the red card or free.
- In `DAYS[N]` add the key to `attr: [...]`, and update `drive`, `km` and `parking` if the route changed.
- Meals: the 3-year-old is not counted (`MEAL` has 2 values).

## 4. Map and catalog
- Map `var ATTR = [ … ]`: `{ n: "שם", ph: "wiki:Title", e: "EMOJI", d: "יום D.M", ll: [lat, lon], day: "dayN" }`.
- Red-card catalog (`CATALOG`) day links, if the attraction is in the card.

## 5. Check and ship
1. When replacing or removing, `grep` the page for the old name; no leftovers.
2. Check JS syntax and load the page with Playwright (390px + desktop).
   Expect no JS errors and no horizontal overflow.
3. Run the **route-checker** agent; this is an itinerary change.
4. Publish per CLAUDE.md, then tell the user in Hebrew:
   - what changed
   - booking and card status
   - price
   - anything unverified
