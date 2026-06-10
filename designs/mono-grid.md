# design_mono-grid.md

> Theme: black-and-white geometric system with exposed line grids, monospace artifacts, and documentation-grade density.
> Use case: developer tool / infrastructure marketing + docs.
> Icons: Lucide (ISC) or any MIT-licensed line set, stroke 1.5px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Monochrome by default, color is data | UI stays achromatic; color only for states, charts, gradient demos |
| 2 | Geometric clarity | Radius 6px everywhere; no ornament beyond basic geometry |
| 3 | Text is the interface | Buttons, links, labels are text-first; icons assist |
| 4 | Marketing reads like docs | Documentation-grade information density on marketing pages |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #000000 dark / #FFFFFF light | Dual mode required |
| `--fg` | #FFFFFF / #000000 | Inverted |
| `--gray-100..900` | #1A1A1A -> #EAEAEA, 9 steps | All hierarchy |
| `--blue` | #0070F3 | Links, info (generic UI blue) |
| `--success` | #50E3C2 | Status |
| `--error` | #FF4D4D | Status |
| `--gradient-demo` | #007CF0->#00DFD8, #7928CA->#FF0080 | Demo text only |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Geist Sans (SIL OFL) | 64-80px / weight 600 / -0.04em |
| Body | Geist Sans | 16px / 1.6 |
| Code | Geist Mono (SIL OFL) | 14px |
| Caption | Geist Sans | 13px / `--gray-500` |

Scale: 13 / 14 / 16 / 20 / 32 / 48 / 64 / 80

## 4. Layout

- Max-width 1200px, 24px padding
- Hero: centered, oversized headline + paired CTAs (inverted pair: black/white)
- Grid background: exposed 1px `--gray-100/200` line grid behind sections
- Section padding 128px

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | `--fg` bg + `--bg` text, radius 6px, height 40px |
| CTA secondary | Transparent + 1px `--gray-400` border |
| Terminal card | Three achromatic window dots, mono text with typing effect |
| Status card | State dot (success) + mono identifier + timestamp |
| Tabs | 2px `--fg` underline; text `--gray-500` -> `--fg` |
| Footer | 5-column link matrix, 13px |

## 6. Motion

| Target | Effect |
|---|---|
| Gradient text | Hue rotation 8s loop (one demo instance max) |
| Terminal | Typing at 30ms/char |
| Hover | Color transitions only (0.15s); no movement |

## 7. Don't

- No standalone geometric marks that read as logos
- No chromatic color on layout elements
- No radius values other than 6px
- Gradients never extend to body text or backgrounds
