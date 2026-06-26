# Section: Footer

## What it does
Blue branded footer displaying the HWE logo and broker contact information in a structured two-column layout matching the HWE brand standard.

## Required inputs
- HWE logo path
- Exclusive representatives: array of {name, title, email}
- Acquisition financing advisor: array of {name, title, email} (optional)

## Design rules
- Background: `--blue` (primary brand color — always blue regardless of deal palette)
- Layout: 2-column grid — HWE logo LEFT, contacts RIGHT
- Grid: `gridTemplateColumns: "auto 1fr"`, gap `clamp(48px, 8vw, 120px)`
- HWE logo: 180×72px, white version
- Section headers: Jost, 10.5px, uppercase, letter-spacing .28em, `rgba(255,255,255,.55)`
- Divider line under each header: `1px solid rgba(255,255,255,.2)`, padding-top 20px
- Contact name: Jost, 14px, weight 600, `#fff`
- Contact title: Jost, 13px, `rgba(255,255,255,.6)`
- Contact email: Jost, 13px, `rgba(255,255,255,.6)`, no text-decoration
- Contacts grid: `repeat(auto-fit, minmax(240px, 1fr))`, gap `20px 48px`
- Bottom bar: copyright text, `rgba(255,255,255,.4)`, 11.5px
- Bottom border: `1px solid rgba(255,255,255,.12)`

## Layout diagram
```
┌─────────────┬────────────────────────────────┐
│             │ EXCLUSIVE REPRESENTATIVES       │
│   HWE       │ ────────────────────────────── │
│   LOGO      │ Name          Name             │
│             │ Title         Title             │
│  HODGES     │ email         email             │
│  WARD       │                                │
│  ELLIOTT    │ Name                           │
│             │ Title                           │
│             │ email                           │
│             │                                │
│             │ ACQUISITION FINANCING ADVISOR   │
│             │ ────────────────────────────── │
│             │ Name                           │
│             │ Title                           │
│             │ email                           │
├─────────────┴────────────────────────────────┤
│ © 2025 Hodges Ward Elliott. All rights...    │
└──────────────────────────────────────────────┘
```

## Edge cases
- If no financing advisor: omit that section entirely
- If only 1 representative: single column, no grid needed
- If 4+ representatives: grid wraps to additional rows
- The footer blue background is ALWAYS the `--blue` value, even if the rest of the site is light theme
