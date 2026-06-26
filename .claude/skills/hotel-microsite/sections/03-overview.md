# Section: Overview (The Offering)

## What it does
Two-column layout presenting the investment narrative (left) alongside a property statistics card (right). The H2 heading spans full width ABOVE both columns so the stats card aligns with the body text, not the heading.

## Required inputs
- Headline text (e.g., "A premier asset in\ndowntown Pensacola")
- Body paragraphs (2-3)
- Emphasis phrase (rendered in italic white)
- Stats: rooms, floors, year_opened, fnb, meeting_space_sf, parking
- Brand name (for the "HILTON BRAND" tag)
- CA sign URL and download URL

## Design rules
- Background: `--navy`
- Layout: heading full-width above, then 2-column grid below
- Heading: Cormorant, `clamp(36px, 4.5vw, 58px)`, weight 300, line break where specified
- Italic emphasis words in heading: color `--off-white`, opacity .8
- Body text: Jost, 15.5px, `--muted`, line-height 1.8
- Emphasis phrase in body: italic, color `#fff` (not muted)
- Stats card: `--navy-lt` bg, 2x3 grid, divider borders, Cormorant values + Jost labels
- "HILTON BRAND" tag: bg `--blue`, color `#fff`, uppercase
- CTA buttons: red primary (Sign CA) + ghost outline (Download CA)

## Layout diagram
```
┌──────────────────────────────────────────┐
│ A premier asset in                        │
│ downtown Pensacola          (full width)  │
├────────────────────┬─────────────────────┤
│ Body paragraphs    │ ┌─PROPERTY DETAILS─┐│
│                    │ │ GUEST ROOMS  102  ││
│ Emphasis text      │ │ FLOORS       4    ││
│                    │ │ YEAR OPENED  2023 ││
│ [Sign CA]          │ │ F&B     Grille    ││
│ [Download CA]      │ │ MEETING   3,913   ││
│                    │ │ PARKING  Self-park ││
│                    │ └──────────────────┘│
└────────────────────┴─────────────────────┘
```

## Edge cases
- If no meeting space: omit that stat row (card becomes 2x2.5 — use `display: contents` or filter)
- If no F&B: omit that row
- Stats card should never have an odd empty cell — if odd number of stats, the last one spans full width
- For very long property names in the heading, let it wrap naturally — never truncate
