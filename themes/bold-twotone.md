# bold-twotone.md

> Theme: loud two-tone system — one deep tone, one bright tone, condensed display type, concrete numbers.
> Use case: consumer service landing with a confident brand voice.
> Note: the two tones are deliberately offset from a brand-identifying color pair in the same families — keep as specified.
> Icons: Lucide (ISC), stroke 2px (bold to match display weight). No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Loud confidence | Oversized condensed display type; statements, not slogans |
| 2 | Two-tone world | One deep tone + one bright tone carry the entire page |
| 3 | Numbers are concrete | Show actual figures — totals, percentages — in tabular numerals |
| 4 | Self-serve first | The key interactive element (estimator/configurator) sits in the hero |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bright` | #CDE82A | Accent surfaces, CTA |
| `--deep` | #1C3424 | Dark sections, text on bright |
| `--bg` | #FFFFFF | Default sections |
| `--text` | #0E0F0C | Body |
| `--text-soft` | #5C5F5A | Secondary |
| `--border` | rgba(14,15,12,.14) | Dividers |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Bricolage Grotesque (SIL OFL) | 64-96px / weight 800 / condensed width / -0.01em |
| Body | Inter (SIL OFL) | 17px / 1.6 |
| Numbers | Inter tabular-nums | All figures |
| Label | Inter | 13px / weight 600 / uppercase |

Scale: 13 / 15 / 17 / 24 / 40 / 64 / 96

## 4. Layout

- Max-width 1200px
- Hero: display headline spanning 2-3 lines + inline interactive card
- Full-bleed `--deep` and `--bright` band sections alternate with white
- Section padding 112px

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | `--bright` bg + `--deep` text, pill radius, height 52px, weight 700 |
| Estimator card | White card, radius 16px, two inputs + live computed row (tabular) |
| Value row | Label left + tabular number right, `--border` divider |
| Comparison table | Alternatives ("Option A", "Provider B") vs the brand; checkmarks via Lucide `check` |
| Stat band | `--deep` bg, `--bright` oversized numbers |
| Footer | `--deep` bg, white text, 4-column |

## 6. Motion

| Target | Effect |
|---|---|
| Display headline | Per-line rise-in 0.5s, stagger 0.08s, once |
| Estimator | Live recalculation, number tween 0.3s |
| Band sections | Background color swap on scroll boundary (no parallax) |
| Reduced motion | Static fallback required |

## 7. Don't

- Do not shift the two tones toward neighboring brand-identifying pairs; keep the specified values
- No unverifiable claims
- No national flag icons for locale/currency — use ISO codes (USD, EUR, KRW)
- Display face never used below 40px (condensed weight breaks at small sizes)
