# Design System Reference

## Color Roles

Every site requires hex values for each of these roles. Present this table to the user during intake.

| Role | CSS Variable | Description | Example (dark) | Example (light) |
|---|---|---|---|---|
| **Page background** | `--ink` | Darkest background, body color | `#0d1620` | `#ffffff` |
| **Section background** | `--navy` | Alternating section backgrounds | `#152234` | `#f5f7fb` |
| **Section background alt** | `--navy-lt` | Cards, stats panel backgrounds | `#1d3048` | `#eaeef4` |
| **Primary brand** | `--blue` | Main accent — highlight cards, brand section bg, tags | `#21438A` | `#21438A` |
| **Primary brand mid** | `--blue-mid` | Hover state for primary brand elements | `#1a3470` | `#1a3470` |
| **Primary brand light** | `--blue-lt` | Light variant of brand color | `#2d57b0` | `#2d57b0` |
| **CTA color** | `--red` | Call-to-action buttons, accent dots | `#BE2D37` | `#BE2D37` |
| **CTA hover** | `--red-lt` | CTA button hover state | `#d63d48` | `#d63d48` |
| **Dark gray** | `--dark-gray` | Secondary text, muted labels | `#56565B` | `#56565B` |
| **Primary text** | `--cream` | Main text color (white on dark, dark on light) | `#ffffff` | `#0d1620` |
| **Secondary text** | `--off-white` | Slightly muted primary text | `#eaeef4` | `#2d3748` |
| **Muted text** | `--muted` | Body copy, descriptions | `#8ba0b8` | `#6b7b8d` |
| **Divider** | `--divider` | Borders, separators | `rgba(33,67,138,.2)` | `rgba(33,67,138,.12)` |

## Applying the Theme

### Dark theme (default)
```css
body {
  background: var(--ink);
  color: var(--cream);
}
```
Dark backgrounds, light text. Sections alternate between `--ink` and `--navy`. Cards use `--navy-lt`.

### Light theme
```css
body {
  background: var(--ink);  /* which is #ffffff in light mode */
  color: var(--cream);     /* which is #0d1620 in light mode */
}
```
White/light backgrounds, dark text. Sections alternate between `--ink` and `--navy`. Cards use `--navy-lt`.

### Key rule
The color ROLES stay the same regardless of theme. Only the VALUES change. The CSS variable names never change — this means all component code works for both themes without modification.

---

## Typography

### Default pairing (always use unless directed otherwise)
- **Headings**: Cormorant Garamond — weights 300, 400, 500, 600; normal + italic
- **Body / UI**: Jost — weights 300, 400, 500, 600

### CSS variables
```css
--font-cormorant  /* heading font */
--font-jost       /* body font */
```

### Type scale
| Element | Font | Size | Weight | Color | Notes |
|---|---|---|---|---|---|
| H2 section heading | Cormorant | `clamp(36px, 4.5vw, 58px)` | 300 | `--cream` | Main section titles |
| H3 card title | Cormorant | 22–26px | 400 | `#fff` | Inside highlight/brand cards |
| Body paragraph | Jost | 15–15.5px | 300 | `--muted` | Line-height 1.75–1.8 |
| Small label | Jost | 10–11px | 500–600 | varies | Uppercase, letter-spacing .18–.32em |
| Stats value | Cormorant | 26px | 400 | `#fff` | Large numbers in stats card |
| Stats label | Jost | 10px | 300 | `--muted` | Uppercase, letter-spacing .26em |
| Nav link | Jost | `clamp(9px,1vw,11px)` | 400 | `--muted` | Uppercase, letter-spacing .15em |
| CTA button | Jost | 11px | 600 | `#fff` | Uppercase, letter-spacing .22em |

---

## Spacing

### Section padding (CRITICAL — this controls left alignment)
Every section uses the same horizontal padding:
```
padding-left:  clamp(24px, 7vw, 100px);
padding-right: clamp(24px, 7vw, 100px);
```

Store this as a constant:
```tsx
const PADDING = "clamp(24px,7vw,100px)";
```

### Content max-width
All section inner content is constrained to:
```
max-width: 1280px;
margin: 0 auto;
```

### Section vertical padding
```
padding-top:    clamp(64px, 10vh, 120px);
padding-bottom: clamp(64px, 10vh, 120px);
```

### Full-bleed elements
When an element needs to go edge-to-edge (like the gallery grid), use negative margins:
```tsx
marginLeft: `calc(-1 * ${PADDING})`,
marginRight: `calc(-1 * ${PADDING})`,
```

---

## Component Architecture Rules

1. **Every component that uses event handlers (onMouseEnter, onClick, etc.) MUST have `"use client"` at the top**
2. **All images from external URLs must be added to `next.config.ts` remotePatterns**
3. **All uploaded images go in `public/` and are referenced as `/filename.ext`**
4. **Use inline styles (not Tailwind classes) for the main layout** — this makes the HTML export simpler
5. **Tailwind is used only for responsive utility classes** (`hidden md:flex`, etc.)
6. **The `PADDING` constant must be defined in every component** — never hardcode different values

---

## Layout Patterns

### Two-column with heading above
```
┌──────────────────────────────────────┐
│ H2 Heading (full width)              │
├──────────────────┬───────────────────┤
│ Body text        │ Card / Image      │
│ Bullets          │                   │
│ CTAs             │                   │
└──────────────────┴───────────────────┘
```
Used by: Overview (when heading should span both columns)

### Two-column side by side (top-aligned)
```
┌──────────────────┬───────────────────┐
│ H2 Heading       │ Card / Image      │
│ Body text        │                   │
│ Bullets          │                   │
└──────────────────┴───────────────────┘
```
Used by: Location

### Full-bleed grid
```
┌──────────────────────────────────────┐
│ H2 Heading (padded)                  │
├──┬──────┬──────┬─────────────────────┤
│  │ img  │ img  │ (edge to edge)      │
│  │      │      │                     │
└──┴──────┴──────┴─────────────────────┘
```
Used by: Gallery

### Centered content
```
┌──────────────────────────────────────┐
│          H2 Heading (centered)       │
│          Body text (centered)        │
│        [Button]  [Button]            │
└──────────────────────────────────────┘
```
Used by: CTA section
