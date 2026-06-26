# Intake Questions & Data Extraction

## Question Flow

Ask these in groups. Wait for each group's answers before proceeding.

---

### GROUP A — Property Brief

**Ask:** "Please upload the property brief — a Word doc, PDF, or paste the text directly."

After receiving the document, extract ALL of the following fields. If a field is missing from the document, mark it as `[NOT PROVIDED]` and ask about it later.

#### Property Data to Extract

```yaml
property:
  name: ""                    # Full property name (e.g., "Hilton Garden Inn Pensacola Downtown")
  brand: ""                   # Hotel brand flag (e.g., "Hilton Garden Inn", "Marriott", "Holiday Inn")
  brand_family: ""            # Parent brand (e.g., "Hilton", "Marriott International", "IHG")
  address: ""                 # Full street address
  city: ""
  state: ""
  zip: ""
  country: "USA"              # Default USA
  rooms: 0                    # Key count
  floors: 0
  year_opened: ""
  year_renovated: ""          # If applicable
  fnb_outlets: ""             # Restaurant/bar name(s)
  meeting_space_sf: 0
  parking: ""                 # Type + rate
  amenities: []               # List: pool, fitness, business center, etc.
  interest: ""                # "Fee-Simple" or "Leasehold"
  management: ""              # "Unencumbered" or "Encumbered by [name]"
  labor: ""                   # "Non-Union" or "Union"

overview:
  headline: ""                # The main pitch line (e.g., "A premier asset in downtown Pensacola")
  body_paragraphs: []         # 2-3 paragraphs of offering narrative
  emphasis_phrase: ""         # The italic/bold phrase (e.g., "newly built, high-performing...")

highlights:
  - title: ""
    body: ""
  # Minimum 2, maximum 8. Grid auto-adjusts:
  # 2 = 1x2, 3 = 1x3, 4 = 2x2, 5-6 = 2x3, 7-8 = 2x4

location:
  headline: ""                # e.g., "At the heart of downtown Pensacola"
  description: ""
  callouts: []                # Bullet points (distance/proximity facts)

demand_generators:
  - name: ""
    lat: 0.0
    lng: 0.0
    note: ""                  # Optional subtitle
  # If lat/lng not provided, the skill should geocode from the name + city

contacts:
  exclusive_representatives:
    - name: ""
      title: ""
      email: ""
  financing_advisor:
    - name: ""
      title: ""
      email: ""

ca_links:
  sign_url: ""                # RightSignature or DocuSign URL
  download_url: ""            # Direct DOCX download URL
```

---

### GROUP B — Assets

**Ask:** "Now I need the visual assets. Please upload:"
1. **Property photos** — exterior, guest rooms, lobby, pool, amenities, meeting space, restaurant, etc. (minimum 3, ideally 5-6)
2. **Hotel brand logo** — white version preferred (SVG or PNG with transparency)
3. **HWE logo** — or confirm the default HWE logo should be used

For each uploaded photo, ask the user to label it or auto-detect from filename:
- Exterior, Guest Room, Lobby, Pool, Amenities, Restaurant, Meeting Space, Aerial, Other

---

### GROUP C — Design

**Ask:** "What's the color palette for this deal? I need hex values for each role:"

Present this table:

```
COLOR PALETTE
━━━━━━━━━━━━
Page background:     #______  (darkest bg — e.g., #0d1620)
Section background:  #______  (alternating sections — e.g., #152234)
Card background:     #______  (stats panel, cards — e.g., #1d3048)
Primary brand:       #______  (main accent color — e.g., #21438A)
CTA buttons:         #______  (action buttons — e.g., #BE2D37)
Dark gray:           #______  (secondary text — e.g., #56565B)
Primary text:        #______  (main text — e.g., #ffffff)
Muted text:          #______  (body copy — e.g., #8ba0b8)
```

Then ask: **"Dark theme or light theme?"**
- Dark: dark backgrounds, light text (like HGI Pensacola)
- Light: white/light backgrounds, dark text

Then ask: **"Default section order, or would you like to rearrange?"**

Default order:
1. Hero
2. Overview (The Offering)
3. Property Gallery
4. Investment Highlights
5. Location
6. Demand Generators
7. Brand Strength
8. Access the Offering Memorandum
9. Footer

---

### GROUP D — Links

**Ask:** "Please provide the Confidentiality Agreement links:"
1. **Sign online URL** — RightSignature, DocuSign, or similar
2. **Download DOCX URL** — direct download link

If these were in the Word doc, confirm them.

---

## Handling Missing Data

If any required field is missing after reading the Word doc:
- **Property stats** (rooms, floors, year): Ask directly — "How many rooms?"
- **Demand generators**: Ask "What are the key demand generators near the property?" and geocode them
- **Contacts**: Ask "Who are the contacts for the footer?"
- **Photos**: If fewer than 3 uploaded, use Unsplash placeholders that match the city/region. Note this in the QA checklist as "placeholder — needs replacement."
- **CA links**: If not provided, use `#` as placeholder and flag in QA
