# Hotel Offering Microsite Builder

## Description
Build a production-ready hotel investment offering microsite for Hodges Ward Elliott (HWE). Generates a single-page, scrollable deal site with polished hospitality/investment aesthetics. Always produces both a Next.js project and a standalone HTML export.

## When to use
Use when the user asks to build a hotel microsite, hotel offering site, deal site, property site, investment offering page, or anything related to creating a web presence for a hotel investment offering.

## The Pipeline

Follow these steps in exact order. Do not skip steps. Do not assume answers.

---

### STEP 1 — GATHER INPUTS

Read the intake questions from `hotel-microsite/intake-questions.md` and ask them one group at a time. Wait for answers before proceeding.

**Group A — Property Brief**
1. Ask user to upload the property brief (Word doc, PDF, or paste text)
2. Read the document and extract all property data per the extraction template in `intake-questions.md`

**Group B — Assets**
3. Ask user to upload property photos (exterior, rooms, lobby, pool, amenities, etc.)
4. Ask user to upload the hotel brand logo (white version, SVG or PNG)
5. Confirm HWE logo is already in `public/` — if not, ask for it

**Group C — Design**
6. Ask: "What's the color palette?" Show them the color role table from `hotel-microsite/design-system.md` and ask for hex values for each role
7. Ask: "Dark theme or light theme?"
8. Ask: "Default section order or custom?" Show the default order

**Group D — Links & Contacts**
9. Ask for the Confidentiality Agreement links (RightSignature URL + DOCX download URL)
10. Ask for broker contact info (or confirm it was in the Word doc)

---

### STEP 2 — CONFIRM EXTRACTION

Before building anything, present a formatted summary of everything extracted:

```
PROPERTY SUMMARY
━━━━━━━━━━━━━━━
Property:     [name]
Brand:        [Hilton / Marriott / etc.]
Address:      [full address]
Rooms:        [count]
Floors:       [count]
Year Opened:  [year]
F&B:          [outlet name]
Meeting Space:[SF]
Parking:      [type + rate]
Amenities:    [list]
Interest:     [fee-simple / leasehold]
Management:   [encumbered / unencumbered]

HIGHLIGHTS (count: N)
1. [title] — [one-line summary]
2. ...

DEMAND GENERATORS (count: N)
1. [name] — [lat, lng]
2. ...

CONTACTS
- [Name], [Title], [email]
- ...

COLOR PALETTE
- Primary:    [hex]
- CTA:        [hex]
- Background: [hex]
- ...

THEME: [dark / light]
SECTION ORDER: [list]
```

Ask: "Does this look correct? Anything to change?"

Wait for confirmation before proceeding.

---

### STEP 3 — BUILD

Read the design system rules from `hotel-microsite/design-system.md`.

For each section in the confirmed order:
1. Read the section template from `hotel-microsite/sections/[section].md`
2. Fill in the extracted data following the template's rules
3. Write the component file
4. If a brand section exists, read brand data from `hotel-microsite/brands/[brand].md`

Build in this sequence:
1. Create the Next.js project scaffold (or use existing)
2. Write `globals.css` with the color tokens from the design system
3. Write `layout.tsx` with the font configuration
4. Write `tailwind.config.ts` with custom colors
5. Write `next.config.ts` with image domains
6. Write each section component in order
7. Write `page.tsx` composing all sections in the confirmed order
8. Copy uploaded assets to `public/`

After writing ALL components, take a screenshot of each major section and present them as a visual checklist per `hotel-microsite/qa-checklist.md`.

---

### STEP 4 — QUALITY ASSURANCE

Follow the QA checklist in `hotel-microsite/qa-checklist.md`:
1. Run `npm run build` — must pass with zero errors
2. Screenshot each section and present side by side
3. Show the visual checklist:

```
VISUAL QA CHECKLIST
━━━━━━━━━━━━━━━━━━
☐ Navbar — logo visible, all links work, CTA button styled
☐ Hero — photo visible, logo centered in box, gradient smooth
☐ Overview — title + body left, stats card right, aligned
☐ Gallery — all photos render, hover zoom works
☐ Highlights — correct card count, text readable
☐ Location — bullets + photos side by side, top-aligned
☐ Demand Map — Leaflet loads, pins visible, table scrollable
☐ Brand — stats render, pillars readable
☐ CTA — both buttons link correctly
☐ Footer — contacts match brief, HWE logo visible
☐ Left alignment — consistent across ALL sections
☐ Colors — match provided hex values
☐ Build — passes with zero errors
```

4. Ask: "Anything to adjust?"

---

### STEP 5 — EXPORT

After the user approves:
1. Ensure the Next.js project builds cleanly
2. Generate a standalone `index.html` file that contains all styles inlined, all images as URLs, and works without a build step
3. Place the HTML export in the project root as `export.html`
4. Commit everything to git

---

## PORTFOLIO DEALS

If the brief contains multiple properties:
1. Build one site with a property selector/tabs in the hero
2. Each property gets its own Overview, Gallery, Highlights, Location, and Demand Map content
3. Brand, CTA, and Footer are shared across all properties
4. The navbar includes a property switcher

---

## DESIGN CHANGES AFTER BUILD

When the user asks to change colors, fonts, layout, or content after the initial build:
1. Read the relevant section template to understand the design rules
2. Make the change
3. Screenshot the affected section
4. Show the updated checklist item

---

## REFERENCES

- Design system: `hotel-microsite/design-system.md`
- Intake questions: `hotel-microsite/intake-questions.md`
- Section templates: `hotel-microsite/sections/*.md`
- Brand data: `hotel-microsite/brands/*.md`
- QA checklist: `hotel-microsite/qa-checklist.md`
