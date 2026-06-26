# Section: Brand Strength

## What it does
Showcases the hotel brand's global presence and competitive advantages. Uses the primary brand color as the full section background. Contains stat counters + pillar descriptions.

## Required inputs
- Brand family name (e.g., "Hilton", "Marriott")
- Brand stats (loaded from `brands/[brand].md`)
- Brand pillars (loaded from `brands/[brand].md`)
- If brand not in the brands directory, ask the user for stats and pillars

## Design rules
- Background: `--blue` (full section)
- Decorative: subtle radial gradient overlay for depth
- Heading: Cormorant, `clamp(36px, 4.5vw, 58px)`, weight 300, `#fff`
- Subheading: Jost, 15px, `rgba(255,255,255,.65)`, line-height 1.75
- Stat cards: `rgba(255,255,255,.1)` bg, 2px gap grid
- Stat value: Cormorant, `clamp(28px, 3vw, 44px)`, `#fff`
- Stat label: Jost, 11px, uppercase, `rgba(255,255,255,.6)`
- Pillar cards: left border `2px solid rgba(255,255,255,.25)`, padding-left 24px
- Pillar title: Cormorant, 22px, `#fff`
- Pillar body: Jost, 14px, `rgba(255,255,255,.65)`

## Layout
```
Stats: auto-fit grid, minmax(160px, 1fr), gap 2px
Pillars: auto-fit grid, minmax(260px, 1fr), gap 24px
```

## Edge cases
- Unknown brand: ask user for 4 stats and 4 pillars
- Brand with fewer than 4 stats: grid auto-adjusts
- For light theme: the blue section keeps its blue background (it's the brand color) — text stays white
