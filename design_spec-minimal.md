# design_spec-minimal.md

> Theme: monochrome product minimalism — full-bleed media, oversized spec numerals, uppercase wayfinding, one signal accent.
> Use case: premium hardware / physical product page.
> Dummy content: CatTower LTD product "CT-1" / Kitty Park, Ya-ong Kim, Calico Lee.
> Icons: Lucide (ISC), stroke 1.5px. No platform emoji.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Restraint as identity | Monochrome, flat surfaces, zero decoration |
| 2 | Specification as poetry | Key metrics displayed as large-type statements |
| 3 | Film-grade imagery | Full-bleed visuals with cinematic ratio (21:9 crops) |
| 4 | Uppercase wayfinding | Navigation and labels in small uppercase with wide tracking |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Default |
| `--bg-dim` | #F5F5F5 | Alternating sections |
| `--ink` | #101820 | Text, near-black |
| `--gray` | #6E7176 | Secondary |
| `--line` | #D6D6D6 | Hairlines |
| `--signal` | #FF7500 | Single accent, max 2 uses per page (common safety-orange hue) |
| `--carbon` | #0C0C0C | Dark immersive sections |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Inter Tight (SIL OFL) | 56-72px / weight 500 / -0.02em |
| Body | Inter (SIL OFL) | 16px / 1.6 |
| Spec numerals | Inter Tight | 64px / weight 300 / tabular |
| Label | Inter | 12px / uppercase / letter-spacing 0.14em |

Scale: 12 / 14 / 16 / 24 / 40 / 56 / 72

## 4. Layout

- Full-bleed media sections alternate with 1200px contained text sections
- Hero: 100vh product visual, bottom-left product name + two-word tagline
- Spec band: 3-4 columns, numeral + unit + 12px label, hairline separators
- Section padding 120px; media sections 0 padding

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | Rectangular (radius 0), `--ink` bg, white text, height 48px, uppercase 13px |
| CTA ghost | 1px `--ink` border, transparent |
| Spec item | 64px numeral + unit superscript + uppercase label |
| Configurator strip | Horizontal swatch row, selected state = 2px `--ink` underline |
| Sticky product nav | Appears after hero: product name left, anchor links + CTA right, height 56px |
| Gallery | Edge-to-edge horizontal scroll, snap points |

## 6. Motion

| Target | Effect |
|---|---|
| Hero visual | Slow scale 1.04 -> 1.0 on load, 1.2s |
| Spec numerals | Count-up on entry, 0.8s |
| Section enter | Fade only, 0.5s |
| Gallery | Scroll-snap, native momentum |

## 7. Don't

- No emblem-like geometric marks that could read as an existing logo
- `--signal` accent never exceeds 2 instances per page
- No rounded corners, no shadows
- Metrics must be plausible but fictional — never real product data presented as fact
