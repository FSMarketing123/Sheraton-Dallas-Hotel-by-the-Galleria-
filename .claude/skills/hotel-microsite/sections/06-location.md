# Section: Location

## What it does
Two-column layout: heading + description + bullet callouts on the LEFT, stacked location photos on the RIGHT. Both columns top-aligned.

## Required inputs
- Heading (e.g., "At the heart of\ndowntown Pensacola")
- Description paragraph
- Callout bullet points (distance/proximity facts)
- 2 location/area photos (or use Unsplash placeholders for the city)

## Design rules
- Background: `--navy`
- Two-column grid: `repeat(auto-fit, minmax(300px, 1fr))`, gap 64px, `alignItems: start`
- LEFT column heading: marginTop 0 (critical — must align with photo top)
- Heading: Cormorant, `clamp(36px, 4.5vw, 58px)`, weight 300, `#fff`
- Description: Jost, 15px, `--muted`, line-height 1.75
- Bullet dots: `--red`, 6x6px circles
- Bullet text: Jost, 15px, `--muted`, line-height 1.6
- RIGHT column: stacked photos in a flex column, gap 4px, rounded 2px, shadow `0 24px 80px rgba(0,0,0,.45)`
- Each photo: height 230px, `object-fit: cover`, hover zoom to 1.05
- Photo caption overlay: bottom gradient, 10.5px uppercase label

## Critical alignment
The heading "At the heart of" MUST be top-aligned with the first photo. This means:
- `h2` has `marginTop: 0`
- The left column `div` has `paddingTop: 0`
- Both columns in the grid use `alignItems: "start"`

## Edge cases
- If no photos uploaded for this section: use 2 Unsplash photos of the city/region
- If only 1 photo: render it full height (460px) instead of 2 stacked
- If 3+ photos: use the first 2, or switch to a 3-photo stack at 160px each
