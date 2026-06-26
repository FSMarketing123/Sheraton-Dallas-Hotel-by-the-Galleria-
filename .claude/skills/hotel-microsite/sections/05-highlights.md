# Section: Investment Highlights

## What it does
Grid of highlight cards presenting key investment reasons. Cards use the primary brand color (`--blue`) as background. No numbers, no dividers — just title and description text.

## Required inputs
- Heading (default: "Why [City]. Why Now.")
- Subheading (default: "A convergence of location, brand, and market timing defines this offering.")
- Array of highlights, each with `title` and `body`

## Design rules
- Background: `--ink`
- Cards: bg `--blue`, padding 44px 40px, hover darkens to `--blue-mid`
- Card title: Cormorant, 26px, weight 400, `#fff`
- Card body: Jost, 15px, line-height 1.78, `rgba(255,255,255,.65)`
- Grid gap: 3px (hairline between cards)
- NO card numbers (removed in final design)
- NO accent bars or dividers inside cards

## Grid auto-sizing

| Count | Columns | Rows |
|---|---|---|
| 2 | 2 | 1 |
| 3 | 3 | 1 |
| 4 | 2 | 2 |
| 5 | 3 | 2 (last row: 2 items) |
| 6 | 3 | 2 |
| 7 | 4 | 2 (last row: 3 items) |
| 8 | 4 | 2 |

Implementation:
- 2-4: `gridTemplateColumns: "1fr 1fr"`
- 3: `gridTemplateColumns: "1fr 1fr 1fr"`
- 5-6: `gridTemplateColumns: "1fr 1fr 1fr"`
- 7-8: `gridTemplateColumns: "repeat(4, 1fr)"`

At mobile (<640px), always single column.

## Edge cases
- If only 1 highlight: render as a full-width card, no grid
- If highlights have very long body text: cards will naturally grow taller — this is fine, the grid stretches evenly
- For light theme: cards still use `--blue` background with white text (brand color stays)
