# dark-precision.md

> Theme: dark-only interface with typographic precision, border-based depth, and speed as the core brand value.
> Use case: productivity / developer tool landing.
> Icons: Lucide (ISC), stroke 1.5px, 16-20px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Speed is the brand | All transitions under 0.2s; no loading theatrics |
| 2 | Typographic precision | Optical alignment, -0.02em tracking; hierarchy via text-color tiers |
| 3 | Depth in darkness | 1px borders + subtle gradients instead of shadows |
| 4 | Product is the hero | App screenshot, flat front-facing, no perspective |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg-0` | #08090A | Page background |
| `--bg-1` | #101113 | Cards |
| `--bg-2` | #16171A | Hover |
| `--border` | rgba(255,255,255,.08) | All dividers |
| `--text-1` | #F7F8F8 | Headlines |
| `--text-2` | #8A8F98 | Body |
| `--text-3` | #62666D | Captions |
| `--accent` | #5E6AD2 | Single accent (generic indigo) |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Inter (SIL OFL, variable) | 56px / weight 510 / -0.022em / line-height 1.1 |
| Body | Inter | 15px / 1.6 / weight 400 |
| UI label | Inter | 13px / weight 500 |
| Mono | JetBrains Mono (SIL OFL) | 13px (shortcuts, data) |

Scale: 13 / 15 / 21 / 32 / 56 — few steps; hierarchy completed by `--text-1..3` tiers

## 4. Layout

- Max-width 1024px, single centered column bias
- Section padding 96px; sections divided by 1px `--border` horizontal rules
- Feature grid: 3-column cards, 1px gap (borders act as grid lines)
- Hero: centered headline -> full-width product screenshot with top fade-in mask

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | Radius 8px, `--text-1` bg with `--bg-0` text (inverted), height 36px |
| CTA secondary | `--bg-1` bg + `--border` |
| Card | `--bg-1`, radius 12px; hover -> `--bg-2` + brighter border |
| Keyboard hint | Mono 13px, `--bg-2` pill, 1px border |
| Nav | Fixed, blur(20px), height 56px, single CTA on the right |
| Update-log row | Date (mono) + title + `chevron-right` |

## 6. Motion

| Target | Effect |
|---|---|
| Hover | Background/border 0.15s ease |
| Section enter | opacity + translateY 16px, 0.4s, stagger 0.05s |
| Product screenshot | Scroll-linked subtle parallax (8px range) |
| Forbidden | Bounce, exaggerated springs, any transition over 0.3s |

## 7. Don't

- No third-party app screenshots; build original UI mockups only
- Never more than one accent color
- No box-shadows (border-based depth only)
- No light-mode variant (this system is dark-only)
