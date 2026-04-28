# Reverie · Brand Identity

A short reference for anyone working on Reverie's identity. Read this before
recoloring, redrawing, or laying out the mark in a new context.

---

## 1. The mark

Reverie's mark is the **Slot** — a solid block with a thin negative-space slot
cut horizontally below center.

![Slot glyph](glyph/slot.svg)

The slot is a deliberate metaphor. A self-hosted library tool is, conceptually,
an act of **inscription**: you take a book and you commit it to your record.
The mark is a stone tablet with an inscription cut into it — small, weighted,
permanent. It is not a bookmark, not a page, not a logo for a reading app. It
is the act of cataloging itself, made into a shape.

The mark always appears **inline-left** of the wordmark in the canonical
lockup. It is not a frame, not a stacked element, not an ornament.

---

## 2. Tagline

> **Your library, catalogued.**

This is the canonical tagline. It is the only tagline. Use it whenever the
product needs to be categorized in a sentence.

**Where it lives:** Open Graph card, meta description, app store listing,
README, footer, homepage hero (as subhead under the wordmark), email
signatures, anywhere a stranger needs to know what Reverie is in three
words.

**Set in:** Author 400, sentence case, no italics. The comma is part of the
line — never drop it. Always trailed by a full stop.

**Don't:**

- Don't pair it with a second tagline. There is no atmospheric companion
  line; the workhorse carries the brand alone.
- Don't substitute synonyms ("organised," "on record," "in order"). The
  word is *catalogued*. The British spelling is intentional and locked.
- Don't translate or reflow it as marketing copy. "Catalogue your library
  with Reverie" is not the tagline.
- Don't set it in Satoshi. The tagline is the one place a serif appears in
  the lockup family — it's the editorial counterweight to the wordmark's
  geometric stamp.

---

## 3. Construction

The glyph is built on a **32 × 32 unit grid**.

![Slot construction](proportions/slot-construction.svg)

| Element              | Spec                                            |
| -------------------- | ----------------------------------------------- |
| Grid                 | 32 × 32 units                                   |
| Block                | 24 × 24 units · 4u inset on all sides           |
| Slot width           | 16 units (50% of grid · 66.7% of block)         |
| Slot height          | 2 units (6.25% of grid)                         |
| Slot Y position      | 17u from top (53.1% — just below visual center) |
| Slot X position      | 8u from left (centered horizontally)            |

**The slot's vertical position is the most important rule.** It sits at 53%
from the top — *just below* visual center. Centered slots read mechanical
(an envelope, a mail slot). Below-center slots read **inscribed** (a carved
line in stone). Do not center the slot.

### Favicon variant (small-size fallback)

At 16–24px raster, the standard 2u slot can blur or fill from anti-aliasing.
Use the **favicon variant** (slot height 4u, width 14u) for any rendered
output below 24px. The proportional system is preserved; the slot is just
thicker so the carved gesture survives.

---

## 4. Color

Reverie has two colors with semantic weight: an **accent** and an
**alarm**. They sit on different axes and do different work.

The accent says *"this matters."* It marks state — focus, selection,
completion, the active surface. It is Reverie Gold and there is exactly
one.

The alarm says *"stop."* It marks irreversibility and unrecoverable
error. It is Reverie Alarm and there is exactly one.

These are not two members of a severity palette. They are two
punctuation marks on the page, each used sparingly, each meaning one
thing.

Beyond accent and alarm, Reverie uses a near-black canvas (Ink), a
paper-warm light canvas (Parchment), and a single off-white (Cream).

| Token                 | Value     | Use                                                                 |
| --------------------- | --------- | ------------------------------------------------------------------- |
| Reverie Gold          | `#C9A961` | The accent on dark surfaces. Glyph fill. Single source of glow.     |
| Reverie Gold (Light)  | `#8E6F38` | The accent on Parchment. Darkened for legibility (see below).       |
| Reverie Alarm         | `#F26C7B` | The alarm on dark surfaces. Fill only, never body text.             |
| Reverie Alarm (Light) | `#BC2937` | The alarm on Parchment. Fill only, never body text.                 |
| Ink                   | `#0E0D0A` | Dark canvas. Wordmark on light surfaces.                            |
| Cream                 | `#E8E0D0` | Wordmark on dark surfaces.                                          |
| Parchment             | `#E8DCC2` | Light theme canvas.                                                 |

State, hierarchy, and emphasis below the level of "this matters" or
"stop" are communicated through **weight, opacity, type scale, density,
and motion** — never through additional hues.

### Light-theme accent: a deliberate constraint

On Parchment, Reverie Gold at `#C9A961` does not meet WCAG AA contrast
(it falls under 3:1 against `#E8DCC2`). The light-theme accent darkens
to `#8E6F38`. The gold *register* is preserved — warm metallic — and
the *value* shifts only as far as legibility forces.

`#8E6F38` on Parchment passes WCAG 2.2 1.4.11 (UI component 3:1) and
1.4.3 large-text (≥ 18pt regular or ≥ 14pt bold), but does **not**
pass 1.4.3 normal-text (4.5:1). This is a brand-locked trade-off:
darkening further compromises gold-hue identity, and the alternative
(introducing a second high-contrast hue for body text) violates the
single-accent rule above.

The mitigation is restriction. On light surfaces, the accent is used
only for:

- Focus rings
- Large CTAs (the primary action on a surface)
- Recovery actions (the gesture out of an error state)

It is **not** used for normal-size body text, links, inline emphasis,
or any chrome that runs at the body type scale. axe-core will surface
contrast violations on any light surface that breaks this rule, and
those violations are the right signal — they mean the surface is
misusing the accent, not that the accent is wrong.

### Reverie Alarm: the carve-out

The alarm exists because some moments cannot be communicated by weight
alone without compromising user safety. There are exactly two such
cases:

1. **Irreversible destructive confirmation.** The moment the user is
   about to take an action that cannot be undone — bulk delete a series,
   overwrite curated metadata, wipe a tome's enrichment record. The
   alarm appears on the confirm-destructive button, alongside typed-name
   confirmation and an undo window where one is feasible.

2. **Unrecoverable system errors.** Errors meeting **both** criteria:

   - the system cannot recover without user intervention, **and**
   - continuing to use the product in the current state risks data
     loss, silent failure of subsequent operations, or divergence from
     the user's expected state.

   Framing test for contributors: *will the user form a wrong mental
   model of "it's working" that survives until their next intentional
   interaction with this surface?* If yes, alarm. If no, gold or
   neutral.

   Qualifies: auth token expired (sync stops silently), database
   connection lost (writes fail silently), disk full (next import fails
   silently). Does not qualify: indexing failed for a single book
   (loud, scoped, no silent downstream effect); Kobo offline on an
   ad-hoc retry (recoverable, no corruption).

**Alarm colour is reinforcement, not the primary channel.** Destructive
intent and unrecoverable error must always be communicated through copy,
friction, and iconography first; Reverie Alarm makes those signals
louder for users who can perceive it. Every red has this problem —
roughly 1 in 12 men with deuteranopia/protanopia will read the hue as
muddy brown — which is acceptable here precisely because the design
never depended on the colour.

**Where alarm appears.** As fill, border, or icon — never as body text.
Toasts and dialogs render text in Ink (or Cream on dark mode); the
alarm is the accent bar, the button fill, the icon stroke. This
restriction follows the same logic as the gold light-theme constraint
above.

#### Contrast (verified)

- `#BC2937` on Parchment `#E8DCC2`: **4.4:1**. Passes WCAG 2.2 1.4.11
  (UI component, 3:1) with margin. Marginally fails 1.4.3 normal text
  (4.5:1) — which is why alarm is fill-only on light surfaces.
- `#F26C7B` on Ink `#0E0D0A`: **6.7:1**. Passes 1.4.3 normal text and
  1.4.11 with comfortable margin.

#### Hue and lightness

Both values sit at hue 354° — slightly cool of pure red so they cannot
be misread as warm cousins of gold. Light mode uses lightness ~45%;
dark mode lifts to ~69% with the hue held constant. The same coat, two
modes — not two alarms.

**Lightness is reserved for mode (light/dark); hue is the tunable for
distinguishability.** Adjustment of last resort: if alarm/gold
separation reads ambiguous on Ink at icon sizes, shift Reverie Alarm
hue cooler (toward 350°) before reducing lightness. Reducing lightness
breaks the same-coat principle and quietly creates a severity ladder.

### Rejected accents

Recorded so the next "but what about…" conversation lands in five
minutes, not an hour.

| Rejected                                                  | Why                                                                                                                                                                                              | Use instead                                     |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------- |
| Warning amber / yellow                                    | Severity ladders always grow once cracked; amber dilutes the alarm signal and invents a "soft alarm" register                                                                                    | Copy, friction, position                        |
| Success green                                             | Completion is gold weight, not a new colour. A green checkmark drifts the brand into generic-dashboard territory                                                                                 | Gold checkmark, weight shift, micro-motion      |
| Info blue                                                 | "Did you know" patterns rarely earn their screen. If something needs saying, say it in body type                                                                                                 | Plain text or omit                              |
| Red severity tints (red-50, red-200, etc.)                | One alarm = one colour. Tints invent a gradient that doesn't exist and reintroduce the severity-ladder problem from a different direction                                                       | Solid Reverie Alarm, opacity for hover/disabled |
| Branded/muted alarm red (burgundy, oxblood, muted carmine) | Alarm is punctuation; it works *because* it doesn't try to fit. Burgundy reads decorative and weakens the stop signal. The carve-out's whole premise is that this token is not asked to be on-brand | Use the unbranded red as specified above        |

### Implementation note

The Tailwind config must use `theme.colors` — which **replaces** the
default ramps — rather than `theme.extend.colors`, which **adds** to
them. With `extend`, `text-red-500` and the rest of the default red,
blue, green, and yellow ramps continue to resolve, and the alarm
carve-out leaks at every utility-class call site. Default ramps must be
absent, not overridden. The difference between a wall and a fence.

Reverie Alarm is importable only from the two component contexts that
need it: the destructive-confirm component and the system-error toast.
Lint and review enforce that boundary across CSS values, Tailwind
utilities, SVG fills/strokes, and inline styles. Image assets (PNG/JPG)
cannot be linted and rely on review.

---

## 5. Typography

| Role        | Family        | Weight | Tracking | Case      |
| ----------- | ------------- | ------ | -------- | --------- |
| Wordmark    | Satoshi       | 700    | 0.32em   | UPPERCASE |
| Display     | Author        | 500    | -0.012em | Sentence  |
| Body        | Satoshi       | 400/500| 0        | Sentence  |
| Italic accent | Author italic | 400/500 | -0.012em | Sentence |
| Monospace metadata | JetBrains Mono | 400 | 0.04em | UPPERCASE small |

**Author** is the display family — used for hero text, book titles in detail
views, italic accent moments. It does the editorial work.

**Satoshi** is the workhorse — used for body, navigation, controls, and the
wordmark itself. It does the structural work.

The wordmark uses Satoshi rather than Author because the wide-tracked stamp
treatment is itself doing identity work. Satoshi's neutral grotesque lets
that treatment carry, instead of competing with display character. Author
is reserved for places where the typeface itself should speak.

---

## 6. Lockup rules

The canonical brand expression is the lockup: glyph + wordmark, inline.

![Lockup, dark](lockup/lockup-on-dark.svg)

| Rule                | Spec                                                   |
| ------------------- | ------------------------------------------------------ |
| Layout              | Glyph left, wordmark right, baseline-aligned to center |
| Glyph size          | 0.95 × cap-height                                      |
| Gap                 | 0.5 × cap-height (≈ 14px at 28px wordmark size)        |
| Wordmark left-pad   | 0.32em (compensates for tracking optical balance)      |

There are three lockup forms, ranked by canonicality:

1. **Lockup with glyph** — canonical. Use everywhere you can.
2. **Glyph alone** — for favicons, app icons, very compressed contexts.
3. **Wordmark alone** — only when neither fits (footer microtext, plain-text
   email signatures). Never use as a primary mark.

**Why the hierarchy:** wide-tracked uppercase grotesques are a register
heavily used in fashion and luxury (think DTC minimalism). The wordmark
alone drifts toward that register. The glyph anchors it back to
archive/library. Without the glyph, the brand drifts; with the glyph, it
holds.

---

## 7. Don'ts

- Do not recolor the slot. It is always Reverie Gold.
- Do not center the slot vertically. It sits at 53% from top.
- Do not change the wordmark tracking. 0.32em is the spec.
- Do not switch the wordmark family to Author. Satoshi is the spec.
- Do not stack the lockup vertically. Inline-left is the spec.
- Do not add a frame, container, or shape behind the lockup unless using a
  `framed-*` variant (see Asset index).
- Do not rotate, skew, or distort the glyph.
- Do not apply effects (shadow, glow, gradient, bevel, outline).
- Do not use the wordmark alone as a primary mark.
- Do not introduce additional accents or alarms. Gold is the only
  accent; Reverie Alarm is the only alarm. See the rejected-accents
  list in §4 for what has been considered and rejected.
- Do not use Reverie Gold on Parchment for normal-size body text. The
  light-theme accent (`#8E6F38`) passes WCAG large-text contrast only;
  body type on a gold fill fails AA. Restrict to focus rings, large
  CTAs, and recovery actions on light surfaces.

---

## 8. Asset index

All assets are in `brand/`. Use SVG wherever possible — raster files exist
only for contexts that don't accept SVG (older browsers, social media,
operating-system icons).

### Glyph (`brand/glyph/`)

| File                       | Use                                          |
| -------------------------- | -------------------------------------------- |
| `slot.svg`                 | Canonical. Gold on transparent.              |
| `slot-favicon.svg`         | Small-size fallback (16–24px raster).        |
| `slot-on-dark.svg`         | Gold on Ink — for printing on light surfaces.|
| `slot-on-parchment.svg`    | Gold on Parchment — for printing on dark surfaces. |
| `slot-mono-light.svg`      | Cream on transparent. Single-color light.    |
| `slot-mono-dark.svg`       | Ink on transparent. Single-color dark.       |

### Lockup (`brand/lockup/`)

| File                        | Use                                             |
| --------------------------- | ----------------------------------------------- |
| `lockup-on-dark.svg`        | Canonical for dark UI. Gold + Cream, transparent.|
| `lockup-on-light.svg`       | Canonical for light UI. Gold + Ink, transparent. |
| `lockup-framed-dark.svg`    | Gold + Cream on Ink frame. Use on imagery/photos.|
| `lockup-framed-light.svg`   | Gold + Ink on Parchment frame.                   |
| `lockup-mono-light.svg`     | All-Cream. Single-color light contexts.          |
| `lockup-mono-dark.svg`      | All-Ink. Single-color dark contexts.             |

### Raster (`brand/raster/`)

| File                          | Use                                          |
| ----------------------------- | -------------------------------------------- |
| `favicon-16.png`              | Browser tab favicon (legacy fallback).       |
| `favicon-32.png`              | Browser tab favicon (high-DPI).              |
| `favicon-48.png`              | Windows shortcut icon.                       |
| `apple-touch-icon-180.png`    | iOS home-screen icon. Framed (Ink + Gold).   |
| `glyph-256.png`               | Standalone glyph raster. Email signatures.   |
| `glyph-512.png`               | App store / Play store icon.                 |
| `glyph-1024.png`              | macOS app icon, App Store master.            |
| `og-card-1200x630.png`        | Open Graph / Twitter card share image.       |

### Construction (`brand/proportions/`)

| File                         | Use                                          |
| ---------------------------- | -------------------------------------------- |
| `slot-construction.svg`      | Annotated grid diagram. For docs only.       |

---

## 9. HTML integration

The minimum favicon block to drop into the React app's `index.html`:

```html
<link rel="icon" type="image/svg+xml" href="/brand/glyph/slot-favicon.svg" />
<link rel="icon" type="image/png" sizes="16x16" href="/brand/raster/favicon-16.png" />
<link rel="icon" type="image/png" sizes="32x32" href="/brand/raster/favicon-32.png" />
<link rel="apple-touch-icon" sizes="180x180" href="/brand/raster/apple-touch-icon-180.png" />
<meta property="og:image" content="/brand/raster/og-card-1200x630.png" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
```

Modern browsers will prefer the SVG favicon; older ones fall back to the PNGs.

---

## 10. Decision log

The mark and lockup were chosen over a number of alternatives explored
during the typography + identity phase. For context, the alternates that
got close:

- **Open Brackets** (D5) — bracketed-R monogram. Strong working mark, but
  registered too "literary brand" and didn't argue for the inscription thesis.
- **Dog-Ear** (G3) — folded-corner glyph. Read as "bookmark app," too
  literal for the position.
- **Inset** (A6) — outline + off-center solid square. Closest abstract
  alternative. Lost on stroke-weight mismatch with the stamp wordmark.
- **Aperture** (A1) — interlocking arcs. Mechanical-precise but the
  focused-view metaphor stretched too far for a cataloging tool.

The Slot was chosen because it is the only mark in the explored set that
*embodies* the act of inscription rather than gesturing at it. Documented
here so we don't relitigate the decision when someone asks why not a book.
