# Section: Demand Generators Map

## What it does
Interactive Leaflet.js map showing demand generator pins alongside a scrollable table. Clicking a pin or table row zooms the map. Uses CartoDB light tiles.

## Required inputs
- Array of demand generators: name, lat, lng, optional note
- The hotel's own lat/lng (marked as special "subject hotel" pin)

## Dependencies
- `npm install leaflet @types/leaflet`
- Leaflet CSS loaded via `<link>` tag in the component
- Next.js config must NOT conflict with Leaflet's dynamic imports

## Design rules
- Background: `--ink`
- Map container: white bg, border `1px solid #d8dee8`, shadow `0 24px 80px rgba(0,0,0,.35)`, rounded 2px
- Layout: `gridTemplateColumns: "1fr 380px"`, min-height 520px
- Map tiles: CartoDB light (`https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png`)
- Default zoom: 12, centered on hotel
- Scroll wheel zoom: disabled (prevents accidental scroll hijack)
- Numbered pins: dark `#0d1620` circles, 28x28px, white number text
- Hotel pin: `--blue` background with ✦ symbol
- Table header: `#f8f4ef` bg, uppercase labels
- Table rows: hover bg `#f5f7fb`, selected bg `#f0f4fa`
- Reset button: `--blue` bg, white text, positioned bottom-right of map
- Click behavior: fly to location at zoom 15, open popup with name

## Critical: Leaflet + Next.js
Leaflet must be dynamically imported because it accesses `window`:
```tsx
useEffect(() => {
  import("leaflet").then(L => {
    // All Leaflet code here
  });
}, []);
```

## Edge cases
- **8 or fewer generators**: table fits without scroll, no scroll bar needed
- **30+ generators**: table scrolls, map stays same size
- **Missing lat/lng**: geocode from name + city using a reasonable default position
- **Mobile (<700px)**: stack map above table (single column), map height 400px, table height 400px
- **Popup tip**: hidden via CSS (`.leaflet-popup-tip-container { display: none; }`)
