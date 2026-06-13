# brutalist-pop.md

> Theme: black canvas, viewport-filling uppercase display type, hard 1-2px white rules, radius 0, one hot pop accent — raw and loud.
> Use case: portfolios, studio sites, event pages, drops.
> Icons: Lucide (ISC), stroke 2px (heavy). No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Type is the image | Display lines sized to the viewport (vw units), uppercase, cropped tight |
| 2 | Hard edges only | Radius 0 everywhere; depth via 1-2px solid rules and color blocks, never shadows |
| 3 | One hot accent | A single orange does all signaling; second accent only inside full-bleed color blocks |
| 4 | Counted, indexed tone | Parenthetical superscript counts and mono indices label everything |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #000000 | Page |
| `--panel` | #1A1A1A | Cards, raised rows |
| `--panel-2` | #212121 | Hover panel |
| `--fg` | #FFFFFF | Text, rules, borders |
| `--fg-soft` | rgba(255,255,255,.64) | Secondary text |
| `--accent` | #FF5C00 | Links, highlights, selection (deliberately offset orange — do not shift toward red) |
| `--block` | #FCB900 | Optional full-bleed pop block sections only |

Inversion is the hover language: black-on-white flips to white-on-black (and vice versa) — no other hover colors.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Archivo Black (SIL OFL) | clamp(64px, 11vw, 160px) / uppercase / line-height 0.9 / -0.01em |
| Section head | Archivo (SIL OFL) | 32px / 700 / uppercase |
| Body | Archivo | 16px / 1.5 |
| Counts, indices, meta | JetBrains Mono (SIL OFL) | 12-13px; superscript counts: `Showcase <sup>(25)</sup>` at 0.6em |
| Marquee strip | Archivo Black | 24px uppercase, 0.04em |

Wordmark convention: lowercase + trailing period (`cattower.`).
Display lines may be cropped by `overflow: hidden` rows — cutting type at section edges is intended.

## 4. Layout

- Full-bleed rows stacked and separated by 2px `--fg` rules; no max-width container for display rows
- Content rows: 1280px max, 24px side padding
- Nav: 56px bar, 2px bottom rule; wordmark left, center links with superscript counts, dotted run (`·····`) as separator
- Marquee strip: 48px tall row between sections, repeated uppercase phrase + separator glyph, 2px rules top/bottom
- Card grid: 2-4 columns, 1px `--fg` borders, no gap (borders collapse into a lattice)
- Footer: giant contact line (display size), then mono index rows
- Index stamps: mono `001 / 002 / ...` prefixes on list rows

## 5. Components

| Component | Spec |
|---|---|
| Primary button | White bg, black text, radius 0, 2px border, height 48px, uppercase 14px/700; hover: invert |
| Ghost button | Transparent, 2px `--fg` border; hover: white fill black text |
| Card | 1px border, `--panel` bg, mono index top-left, title uppercase; hover: bg `--panel-2` and accent index |
| Marquee | `animation: slide 18s linear infinite` on a duplicated track; static under reduced motion |
| List row | 64px row, 1px rule below, title left + mono meta right; hover: invert row |
| Pop block | Full-bleed `--block` or `--accent` bg section, black text, display type |
| Noise overlay | Optional SVG turbulence at 0.04 opacity over hero only |
| Selection | `::selection` accent bg, black text |

## 6. Motion

| Target | Effect |
|---|---|
| Hover inversions | background/color 0.05s linear — abrupt, no easing curves |
| Display reveal | clip-path rise per line, 0.5s cubic-bezier(.77,0,.18,1), staggered 80ms |
| Marquee | linear infinite; duplicate content for seamless loop |
| Scroll | No smooth-scroll hijack, no parallax |
| Reduced motion | Marquee static, reveals replaced by opacity |

## 7. Don't

- No border-radius, no shadows, no gradients, no glassmorphism
- Max 2 pop hues per page (`--accent` + optionally `--block`); never both inside one component
- No serif or script faces; no font weights below 400
- No letter-spacing on display type beyond ±0.01em (bulk comes from size, not tracking)
- Never soften the inversion hover with transitions longer than 0.1s


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#000000; --panel:#1A1A1A; --panel-2:#212121; --fg:#FFFFFF;
  --fg-soft:rgba(255,255,255,.64); --accent:#FF5C00; --block:#FCB900;
  --radius:0;
  --font-display:"Archivo Black",sans-serif; --font-sans:"Archivo",sans-serif; --font-mono:"JetBrains Mono",monospace;
}
```
