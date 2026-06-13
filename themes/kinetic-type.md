# kinetic-type.md

> Theme: white canvas, oversized serif-meets-grotesque display, full-bleed color-block sections, scroll-driven type motion.
> Use case: portfolios, studios, editorial showcases, conference sites.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead.
> Technique note: composed from multiple independent references; borrow the techniques below, never any single site's composition.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Typography is the interaction | Type moves with scroll — reveals, skews, slides; imagery is secondary |
| 2 | Two voices per headline | Grotesque caps + serif italic inside one display line, never more |
| 3 | Sections are color blocks | Full-bleed background swaps (white → black → accent) divide the page |
| 4 | Grid made to be broken | 12-column base; text and media deliberately offset and overlapped |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Default section |
| `--ink` | #000000 | Text, rules |
| `--bg-dark` | #1D1F23 | Dark sections (charcoal, not pure black) |
| `--accent-block` | #4338E3 | Full-bleed accent section (deliberately offset electric indigo — do not shift toward pure ultramarine) |
| `--accent-warm` | #E04A2B | Rare second block / link hover (deliberately offset) |
| `--soft` | rgba(0,0,0,.55) | Secondary text on white |

Each section declares its own `--color-bg` / `--color` pair; text is always pure black or pure white against blocks.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display grotesque | Space Grotesk (SIL OFL) | clamp(56px, 9vw, 140px) / 500 / line-height 0.95 |
| Display serif accent | Instrument Serif Italic (SIL OFL) | Inline within display lines, same size, 1-2 words max |
| Body | Space Grotesk | Responsive steps: 15px → 17px → 19px → 21px (small → xl viewports) |
| Labels, indices | JetBrains Mono (SIL OFL) | 11-12px uppercase, 0.08em; may rotate 90° as margin labels |

Display variants: outlined type (`-webkit-text-stroke: 1px`, transparent fill) for repeated or background lines; filled for the primary line.

## 4. Layout

- 12-column grid, 1440px max, 32px gutters; columns are a visible design tool — text blocks start at col 3, 5, 7 (varying per section)
- Hero: display headline broken across 2-3 lines with deliberate horizontal offsets per line; mono index top-left, scroll cue bottom
- Color-block sections: full-bleed; generous 160px vertical padding
- Project/list rows: oversized titles (48px+) with thin 1px rules; counter `01 — 06` mono prefix
- Media blocks: images overlap text columns by 1-2 columns; captions rotated 90° in the margin
- Footer: dark block, giant serif-italic contact line

## 5. Components

| Component | Spec |
|---|---|
| Link | 1px underline, 3px offset; hover: `--accent-warm` text, underline slides out/in |
| Button (rare) | 1px `--ink` border, radius 0, uppercase mono 12px, 16px 32px padding; hover invert |
| List row | 1px rule below; title + mono meta right; hover: title slides 16px right, 0.4s |
| Repeated text band | Same display line stacked 3-5 times: one filled, rest outlined |
| Image card | No border, no radius; grayscale at rest, full color on hover (0.4s) |
| Mono margin label | 11px uppercase, rotated, fixed to section edge |

## 6. Motion

| Target | Effect |
|---|---|
| Display reveal | Per-line mask rise: translateY(110%) → 0, 0.8s cubic-bezier(.19,1,.22,1), 90ms stagger |
| Scroll skew | Display lines skewY by scroll velocity, max 4°, spring back when scroll stops |
| Horizontal type slide | Background display bands translateX linked to scroll progress (±10vw) |
| Section blocks | Background-color crossfade 0.6s as block enters |
| Image parallax | Inner image translateY ±8% of container while scrolling |
| Hover (links/rows) | 0.4s cubic-bezier(.19,1,.22,1) |
| Reduced motion | All transforms off; reveals become opacity 0.3s; blocks switch instantly |

## 7. Don't

- Never more than one serif-italic phrase per headline
- No shadows, no radius, no gradients — color blocks and rules only
- Skew/parallax are scroll-linked only; nothing loops or autoplays
- Don't combine outlined and accent-colored type in the same line
- Mobile (<768px): kill skew and horizontal slides; keep mask reveals only
