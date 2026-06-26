# Section: Navbar

## What it does
Fixed header bar at the top of the page. Contains the HWE logo (left), navigation links (center-right), and a red CTA button (far right).

## Required inputs
- HWE logo file path (default: `/hwe-logo-white.webp`)
- Section names and IDs for nav links (derived from section order)
- CA sign URL for the CTA button

## Design rules
- Position: fixed, top 0, full width, z-index 100
- Height: 68px
- Background: `rgba(--ink-rgb, .96)` with `backdrop-filter: blur(14px)`
- Border bottom: `1px solid var(--divider)`
- All nav links visible at all times — use fluid font sizes `clamp(9px, 1vw, 11px)` to fit
- Nav links: uppercase, letter-spacing `.15em`, color `--muted`, hover `#fff`
- CTA button: background `--red`, color `#fff`, uppercase, letter-spacing `.18em`
- Padding: `0 clamp(16px, 4vw, 72px)`

## Component code pattern

```tsx
"use client";
import Image from "next/image";

const navLinks = [
  // Generated from section order — only sections with IDs get nav links
  { label: "{{SECTION_LABEL}}", href: "#{{SECTION_ID}}" },
];

export default function Navbar() {
  return (
    <header style={{
      position: "fixed", top: 0, left: 0, right: 0, zIndex: 100,
      display: "flex", alignItems: "center", justifyContent: "space-between",
      padding: "0 clamp(16px, 4vw, 72px)", height: 68,
      background: "rgba(var(--ink-rgb, 13,22,32), .96)",
      backdropFilter: "blur(14px)",
      borderBottom: "1px solid var(--divider)",
    }}>
      <a href="/" style={{ display: "flex", alignItems: "center", textDecoration: "none", flexShrink: 0 }}>
        <Image src="{{HWE_LOGO_PATH}}" alt="Hodges Ward Elliott" width={90} height={30} style={{ objectFit: "contain" }} />
      </a>
      <nav style={{ display: "flex", alignItems: "center", gap: "clamp(14px,2vw,32px)", flexWrap: "nowrap" }}>
        {navLinks.map(link => (
          <a key={link.href} href={link.href} style={{
            fontSize: "clamp(9px,1vw,11px)", letterSpacing: ".15em", textTransform: "uppercase",
            color: "var(--muted)", textDecoration: "none", transition: "color .2s",
            fontFamily: "var(--font-jost), sans-serif", whiteSpace: "nowrap",
          }}>{link.label}</a>
        ))}
        <a href="#confidentiality" style={{
          padding: "7px 16px", background: "var(--red)", color: "#fff",
          fontSize: "clamp(9px,1vw,10.5px)", fontWeight: 600, letterSpacing: ".18em",
          textTransform: "uppercase", textDecoration: "none", borderRadius: 1,
          fontFamily: "var(--font-jost), sans-serif", flexShrink: 0,
        }}>Sign CA</a>
      </nav>
    </header>
  );
}
```

## Edge cases
- If there are more than 7 sections in the nav, reduce gap to `clamp(10px, 1.5vw, 24px)`
- On very small screens (<480px), the nav links may need to be hidden behind a hamburger — add a mobile menu toggle
