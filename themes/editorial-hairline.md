# editorial-hairline.md

> Theme: warm off-white editorial minimalism — hairline rules, serif-italic accents, static poise.
> Use case: B2B product with a premium, trust-led tone.
> Icons: Lucide (ISC), stroke 1.25px (thin). No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Product as a magazine | Editorial typography and whitespace applied to data-heavy UI |
| 2 | Serif italic accents | Only 1-2 key words per headline switch to serif italic |
| 3 | Restrained chroma | Near-achromatic page; color lives inside product screens |
| 4 | Trust through detail | Hairline rules, precise alignment, understated motion |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FBFAF9 | Warm off-white |
| `--bg-deep` | #14151A | Dark sections |
| `--text` | #1A1B25 | Body |
| `--text-soft` | #70707B | Secondary |
| `--accent` | #5266EB | Links, focus (single, generic indigo) |
| `--hairline` | rgba(26,27,37,.12) | 0.5-1px rules |
| `--screen-tint` | #EEEDFB | Product screen background |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display sans | Inter (SIL OFL) | 56px / weight 500 / -0.025em |
| Display serif accent | Instrument Serif Italic (SIL OFL) | Inline within display lines |
| Body | Inter | 16px / 1.65 |
| Data | Inter tabular-nums | Numbers, tables |

Scale: 13 / 14 / 16 / 21 / 32 / 56
Mixing rule: `Precision in <em class="serif">motion</em>` — max 3 instances per page.

## 4. Layout

- Max-width 1140px; generous section padding (140px)
- Hero: centered two-line headline -> full-width data dashboard screen
- Asymmetric two-column: text 40% left + screen 60% right
- Areas separated by hairlines only; minimal boxed cards

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | Near-black `--text` bg, white text, radius 8px, height 44px |
| CTA text | 1px underline, 4px offset; hover -> `--accent` |
| Dashboard mock | Radius 12px, hairline border |
| Table | Hairline rows; labels left + tabular numbers right |
| Quote | Serif italic 28px + attribution at 13px |
| Badge | Uppercase 11px, letter-spacing 0.08em, hairline-border pill |

## 6. Motion

| Target | Effect |
|---|---|
| Enter | Opacity only, 0.5s (no movement — static poise) |
| Screen mock | Scroll-linked micro-scale 1.0 -> 1.02 |
| Hover | Color transitions only, 0.2s |

## 7. Don't

- No shadows, glows, or gradients (preserve the hairline system)
- Never exceed 3 serif-mix instances


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#FBFAF9; --bg-deep:#14151A; --text:#1A1B25; --text-soft:#70707B;
  --accent:#5266EB; --hairline:rgba(26,27,37,.12); --screen-tint:#EEEDFB;
  --font-sans:"Inter",system-ui,sans-serif; --font-serif:"Instrument Serif",serif;
}
```
