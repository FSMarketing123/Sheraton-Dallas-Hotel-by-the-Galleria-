# Section: Hero Banner

## What it does
Full-viewport opening section. Shows the hotel exterior photo with a centered blue translucent box containing the hotel brand logo. Address and broker credit at the bottom. Scroll indicator on the right.

## Required inputs
- Hero photo file path (the primary exterior/aerial shot)
- Hotel brand logo file path (white version)
- Property address (street, city, state, zip)

## Design rules
- Height: `100svh`, min-height 680px
- Photo: `object-fit: cover`, brightness `.72` (show more photo than typical)
- Gradient: **bottom-only** feather — `linear-gradient(to top, var(--ink) 0%, rgba(--ink-rgb, .55) 28%, transparent 52%)`
- NO top gradient (let the sky/building breathe)
- Blue logo box: centered at ~44% from top, background `rgba(--navy-rgb, .82)`, `backdrop-filter: blur(10px)`, border `1px solid rgba(255,255,255,.12)`
- Logo inside box: 300px wide, centered
- Bottom meta bar: address + divider + "Offered by Hodges Ward Elliott"
- Scroll indicator: right side, animated gold-to-transparent line

## Critical alignment rule
The bottom content uses the same `PADDING` as all other sections so the address text aligns with section headings below.

## Component code pattern

```tsx
import Image from "next/image";

const PADDING = "clamp(24px,7vw,100px)";

export default function Hero() {
  return (
    <section style={{ position: "relative", height: "100svh", minHeight: 680, overflow: "hidden" }}>
      <Image
        src="{{HERO_PHOTO_PATH}}"
        alt="{{PROPERTY_NAME}}"
        fill priority
        style={{ objectFit: "cover", filter: "brightness(.72)" }}
        sizes="100vw"
      />
      {/* Bottom-only gradient */}
      <div style={{
        position: "absolute", inset: 0,
        background: "linear-gradient(to top, var(--ink) 0%, rgba(var(--ink-rgb), .55) 28%, transparent 52%)",
      }} />
      {/* Centered blue box with logo */}
      <div style={{
        position: "absolute", top: "44%", left: "50%",
        transform: "translate(-50%, -50%)",
        background: "rgba(var(--navy-rgb), .82)",
        backdropFilter: "blur(10px)",
        border: "1px solid rgba(255,255,255,.12)",
        padding: "clamp(28px,4vh,52px) clamp(36px,5vw,72px)",
        textAlign: "center",
        minWidth: "clamp(280px, 38vw, 540px)",
      }}>
        <Image src="{{BRAND_LOGO_PATH}}" alt="{{PROPERTY_NAME}}" width={300} height={98}
          style={{ objectFit: "contain", objectPosition: "center" }} />
      </div>
      {/* Bottom meta */}
      <div style={{
        position: "absolute", bottom: 0, left: 0, right: 0,
        paddingBottom: "clamp(36px,5vh,64px)", paddingLeft: PADDING, paddingRight: PADDING,
        display: "flex", alignItems: "center", gap: 20, flexWrap: "wrap",
      }}>
        <span style={{ fontSize: 13, color: "var(--muted)", letterSpacing: ".08em" }}>
          {{ADDRESS}}
        </span>
        <span style={{ width: 1, height: 16, background: "rgba(255,255,255,.2)" }} />
        <span style={{ fontSize: 11, letterSpacing: ".22em", textTransform: "uppercase", color: "var(--muted)" }}>
          Offered by Hodges Ward Elliott
        </span>
      </div>
      {/* Scroll cue */}
      <div style={{
        position: "absolute", bottom: "clamp(36px,5vh,64px)", right: PADDING,
        display: "flex", flexDirection: "column", alignItems: "center", gap: 10,
        color: "var(--muted)", fontSize: 10, letterSpacing: ".3em", textTransform: "uppercase",
      }}>
        <div style={{
          width: 1, height: 48,
          background: "linear-gradient(to bottom, var(--red), transparent)",
          animation: "scrollPulse 2s ease-in-out infinite",
        }} />
        <span>Scroll</span>
      </div>
      <style>{`@keyframes scrollPulse { 0%,100% { opacity:1; transform:scaleY(1); } 50% { opacity:.4; transform:scaleY(.6); } }`}</style>
    </section>
  );
}
```

## Edge cases
- If no hero photo uploaded, use a dark gradient background with the logo box only
- If the logo is very wide (>400px natural), cap at 300px and let it scale down
- For light theme: invert the gradient direction and use darker overlay colors
