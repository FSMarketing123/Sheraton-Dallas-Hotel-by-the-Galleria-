# Section: Access the Offering Memorandum (CTA)

## What it does
Centered call-to-action section prompting the user to sign or download the Confidentiality Agreement.

## Required inputs
- CA sign URL
- CA download URL

## Design rules
- Background: `--ink`
- Text-align: center
- Heading: Cormorant, `clamp(40px, 5.5vw, 72px)`, weight 300, `#fff`
- "Offering Memorandum" in italic: color `--off-white`, opacity .75
- Body: Jost, 15.5px, `--muted`, max-width 50ch, centered, line-height 1.8
- Sign button: bg `--red`, color `#fff`, Jost 11px 600, uppercase, letter-spacing .22em
- Download button: bg `--blue`, color `#fff`, same type treatment
- Both buttons: hover opacity .82, translateY(-1px)

## Content (fixed text — same for every deal)
```
Access the
Offering Memorandum

To receive the full Offering Memorandum and access data room
materials, please execute the Confidentiality Agreement below.

[Sign CA Online]  [Download CA (DOCX)]
```

## Edge cases
- If only sign URL provided (no download): show only one button, centered
- If neither URL provided: use `#` placeholders and flag in QA checklist
