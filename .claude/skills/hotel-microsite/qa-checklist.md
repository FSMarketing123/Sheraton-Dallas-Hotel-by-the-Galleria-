# QA Checklist

## Process

After building all sections:

### 1. Build verification
Run `npm run build`. It MUST pass with zero errors and zero warnings. If it fails:
- Fix the error
- Rebuild
- Do NOT proceed to screenshots until the build is clean

### 2. Section-by-section screenshots
Start the dev server and take a screenshot of each section. Present them to the user as a grid.

Scroll positions to capture:
- **Hero**: scroll position 0
- **Overview**: scroll to `#overview` offset - 80px
- **Gallery**: scroll to `#property` offset - 80px
- **Highlights**: scroll to `#highlights` offset - 80px
- **Location**: scroll to `#location` offset - 80px
- **Demand Map**: scroll to `#demand` offset - 80px
- **Brand**: scroll to Brand section offset - 80px
- **CTA**: scroll to `#confidentiality` offset - 80px
- **Footer**: scroll to `document.body.scrollHeight`

### 3. Visual checklist

Present this checklist. Mark each item ✓ or ✗ based on the screenshots:

```
VISUAL QA CHECKLIST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

NAVBAR
  ☐ HWE logo visible in top-left
  ☐ All nav links visible (not truncated or hidden)
  ☐ Red "Sign CA" button visible on right
  ☐ Nav background is translucent with blur

HERO BANNER
  ☐ Hotel photo clearly visible (not over-darkened)
  ☐ Blue box centered on the photo
  ☐ Hotel brand logo inside the box, readable
  ☐ Bottom gradient fades smoothly to next section
  ☐ Address and "Offered by HWE" visible at bottom
  ☐ Scroll indicator animating on the right

OVERVIEW
  ☐ Heading spans full width above both columns
  ☐ Body text left-aligned with heading
  ☐ Stats card top-aligned with body text (not heading)
  ☐ "HILTON BRAND" (or brand name) tag visible in blue
  ☐ All stat values populated correctly
  ☐ Sign CA button is RED
  ☐ Download CA button is ghost outline

GALLERY
  ☐ "A landmark on the bay" heading left-aligned with other headings
  ☐ Gallery images go edge-to-edge
  ☐ First image spans 2 rows
  ☐ All photos load without broken images
  ☐ Hover zoom effect works

HIGHLIGHTS
  ☐ Cards use primary brand color (blue) as background
  ☐ Correct number of cards (matches brief)
  ☐ No numbers visible on cards
  ☐ Grid is balanced (e.g., 2x2 for 4 cards)
  ☐ Text readable (white on blue)

LOCATION
  ☐ Heading top-aligned with photos (same baseline)
  ☐ Photos visible and properly sized
  ☐ Red bullet dots on callout list
  ☐ Two columns side by side (not stacked)

DEMAND MAP
  ☐ Leaflet map loads with CartoDB tiles
  ☐ All numbered pins visible
  ☐ Hotel pin uses blue color with ✦ symbol
  ☐ Table shows all demand generators
  ☐ "RESET MAP" button visible
  ☐ Clicking a row zooms the map

BRAND STRENGTH
  ☐ Blue background (primary brand color)
  ☐ Stats render with large Cormorant numbers
  ☐ 4 pillar descriptions readable
  ☐ Border-left accent on each pillar

CTA
  ☐ "Access the Offering Memorandum" heading centered
  ☐ "Offering Memorandum" in italic
  ☐ Red "Sign CA" button works (correct URL)
  ☐ Blue "Download CA" button works (correct URL)

FOOTER
  ☐ Blue background
  ☐ HWE logo visible on left
  ☐ All contacts listed with correct names/titles/emails
  ☐ Section headers ("EXCLUSIVE REPRESENTATIVES") visible
  ☐ Copyright line at bottom

GLOBAL CHECKS
  ☐ Left alignment consistent across ALL sections
  ☐ Colors match provided hex values
  ☐ No console errors
  ☐ Build passes with zero errors
  ☐ All external links open in new tabs
  ☐ Placeholder images flagged (if any)
```

### 4. Ask for approval

After presenting the checklist:
"Here's the visual QA checklist. Anything to adjust before I finalize?"

### 5. Final export

After approval:
1. Generate `export.html` — a standalone file with all CSS inlined
2. Commit everything to git with a descriptive message
3. Report: "Build complete. Files ready at [path]. Both Next.js project and export.html available."
