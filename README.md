# reverie-branding

Brand identity for [Reverie](https://github.com/unkos-dev/reverie), a
self-hosted ebook library manager. Marks, lockups, raster artifacts, and
the canonical identity reference.

This repository is the **source of truth** for Reverie's visual identity.
The product repository carries a small subset of these files at
`frontend/public/brand/` for runtime delivery; everything else lives here.

## Start here

- **[`identity.md`](identity.md)** — the canonical reference. Lockups,
  typography, color, mark construction, voice, prohibited variants. Read
  this before making any judgment call about brand-adjacent work.
- **[`index.html`](index.html)** — visual asset browser. Open locally for
  orientation; not a dependency for anything.

## Contents

```
.
├── identity.md                 ← canonical reference
├── index.html                  ← visual asset browser
├── glyph/                      ← the Slot mark
│   ├── slot.svg                  canonical, gold on transparent      [ship]
│   ├── slot-favicon.svg          thicker slot for sub-24px raster    [ship]
│   ├── slot-on-dark.svg          pre-framed on Ink
│   ├── slot-on-parchment.svg     pre-framed on Parchment
│   ├── slot-mono-light.svg       Cream on transparent
│   └── slot-mono-dark.svg        Ink on transparent
├── lockup/                     ← glyph + wordmark
│   ├── lockup-on-dark.svg        canonical for dark UI               [ship]
│   ├── lockup-on-light.svg       canonical for light UI              [ship]
│   ├── lockup-framed-dark.svg    pre-framed Ink panel
│   ├── lockup-framed-light.svg   pre-framed Parchment panel
│   ├── lockup-mono-dark.svg      all-Ink
│   └── lockup-mono-light.svg     all-Cream
├── raster/                     ← rendered PNGs
│   ├── favicon-16.png            browser tab, legacy fallback        [ship]
│   ├── favicon-32.png            browser tab, high-DPI               [ship]
│   ├── favicon-48.png            Windows shortcut icon               [ship]
│   ├── apple-touch-icon-180.png  iOS home-screen, framed             [ship]
│   ├── og-card-1200x630.png      Open Graph / Twitter share          [ship]
│   ├── glyph-256.png             email signatures
│   ├── glyph-512.png             standalone glyph at scale
│   └── glyph-1024.png            macOS / App Store master
└── proportions/
    └── slot-construction.svg   ← annotated grid diagram
```

`[ship]` files are the ones copied into the Reverie product repository's
`frontend/public/brand/` directory at runtime. The rest are reference —
pulled situationally for marketing imagery, app-store submissions,
single-color print, or construction reasoning.

## Locked decisions (summary)

- **Mark.** Solid 24×24 block on a 32×32 grid with a 16×2 horizontal slot
  cut at y=17 (53% from top — *just below* visual center, intentionally).
- **Tagline.** "Your library, catalogued." British spelling locked. Always
  sentence case, comma, trailing full stop.
- **Color.** Reverie Gold `#C9A961` is the only accent. No hue-coded states
  (no red errors, no blue links, no green success). State communicates
  through weight, opacity, and gold accent.
- **Typography.** Author (display) + Satoshi (body) + JetBrains Mono
  (monospace metadata). All locked. Sans-only.

For the full reasoning behind each lock, read [`identity.md`](identity.md).

## Using these assets

See [`LICENSE`](LICENSE). In short:

- **Documentation** (`identity.md`, `index.html`,
  `proportions/slot-construction.svg`) is **CC BY 4.0** — copy, adapt,
  redistribute with attribution.
- **Marks** (`glyph/`, `lockup/`, `raster/`) are reserved trademarks
  identifying the Reverie project. They MAY be used to refer to or link
  to Reverie; they MAY NOT be used to identify a different project, imply
  endorsement, or be sold as merchandise without permission.

If you fork Reverie under its MIT license and rebrand, replace these marks
with your own.

## Editing

Brand evolution happens in this repository. Once a change merges here, the
ship subset is copied (not symlinked) into the Reverie product repository
in a separate, manual PR. This keeps brand history coupled to brand
decisions and product history coupled to product changes.
