# Section: Property Gallery

## What it does
Full-bleed asymmetric photo grid preceded by a left-aligned heading. The heading sits inside the standard content padding; the images go edge-to-edge.

## Required inputs
- 3–6 property photos with labels
- Heading text (default: "A landmark on the bay" — customize per property)

## Design rules
- Background: `--navy`
- Section top padding only (no bottom padding — images bleed to edge)
- Heading: standard PADDING + maxWidth 1280, Cormorant, `clamp(36px, 4.5vw, 58px)`, weight 300
- Gallery grid: negative margins to escape section padding for full-bleed
- Grid layout: `2fr 1fr 1fr`, 2 rows of 320px, gap 3px
- First image spans both rows (`gridRow: "1 / 3"`)
- Hover: `scale(1.04)` on image, dark overlay fades in, label text appears

## Critical alignment
The heading "A landmark on the bay" MUST be left-aligned with all other section headings. This means:
1. The SECTION has the PADDING applied
2. The heading sits inside a maxWidth 1280 div
3. The gallery grid uses negative margins to break out of the padding

```tsx
<section style={{ paddingLeft: PADDING, paddingRight: PADDING, ... }}>
  <div style={{ maxWidth: 1280, margin: "0 auto" }}>
    <h2>A landmark on the bay</h2>
  </div>
  <div style={{
    marginLeft: `calc(-1 * ${PADDING})`,
    marginRight: `calc(-1 * ${PADDING})`,
    display: "grid", ...
  }}>
    {/* images */}
  </div>
</section>
```

## Edge cases
- **3 photos**: grid becomes `2fr 1fr`, 2 rows. First spans both rows, other two stack.
- **4 photos**: `2fr 1fr 1fr`, first spans rows 1-2, remaining fill right side. One cell empty — fill with a colored `--navy-lt` block.
- **5 photos**: Standard layout (the default we built)
- **6 photos**: `2fr 1fr 1fr`, 2 rows fully filled. First spans both rows, 4 fill right side, last one goes below spanning 2 columns.
- **More than 6**: Use the first 6 in the grid. Add a "View All" overlay on the last image.
