# gradient-canvas.md

> Theme: light, trustworthy SaaS landing with one animated gradient moment and diagonal section cuts.
> Use case: B2B product landing with a technical audience.
> Note: accent hue is deliberately offset from a brand-identifying color in the same hue family — keep as specified.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Show, don't tell | Hero pairs a product UI mockup with a live code snippet |
| 2 | One-sentence value prop | Hero headline is one sentence; subcopy max two lines |
| 3 | Section background rhythm | Alternate light / dark sections to pace a long page |
| 4 | Diagonal cuts | Section boundaries clipped at -6deg via `clip-path` |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg-light` | #F6F9FC | Default section background |
| `--bg-dark` | #0A2540 | Alternating deep-navy sections |
| `--text-primary` | #0A2540 | Body on light |
| `--text-secondary` | #425466 | Subcopy |
| `--accent` | #6C5CE7 | CTA, links (single accent) |
| `--gradient` | linear 100deg #FF7AC6 -> #6C5CE7 -> #00D4FF | Hero canvas only, one instance per page |
| `--code-bg` | #0C2D48 | Code blocks |

## 3. Typography

| Role | Font (open license) | Spec |
|---|---|---|
| Display | Inter (SIL OFL) | 56-72px / weight 600 / letter-spacing -0.02em |
| Body | Inter | 18px / line-height 1.55 / weight 400 |
| Code | JetBrains Mono (SIL OFL) | 14px / syntax highlighting required |
| Label | Inter | 13px / weight 600 / uppercase / accent color |

Scale: 13 / 15 / 18 / 24 / 36 / 56 / 72

## 4. Layout

- Max-width 1080px, 12-column grid, 32px gutter
- Hero: text 5 cols left + mockup 7 cols right (mockup bleeds off right viewport edge)
- Section padding: 120px vertical
- Feature sections: text 1/3 + visual 2/3, zigzag alternation

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | Pill (radius 16px), accent bg, `arrow-right` icon shifts 4px on hover |
| CTA secondary | Text + `arrow-right`, no border |
| Code block | Dark card, language tabs, radius 8px, shadow 0 24px 48px rgba(0,0,0,.12) |
| Nav | Transparent at top -> white + blur on scroll, height 64px |
| Logo strip | Six client names in one row, grayscale 60% |
| Stat | 36px weight-600 number + 13px label |

## 6. Motion

| Target | Effect |
|---|---|
| Hero gradient | Canvas animation, 20s loop, slow |
| Section enter | opacity 0->1 + translateY 24px->0, 0.6s ease-out, once |
| Tab switch | Crossfade 0.2s |
| Reduced motion | All disabled under `prefers-reduced-motion` |

## 7. Don't

- No third-party logos, illustrations, or copy text
- Do not swap the accent toward neighboring brand-identifying hues; keep the specified value
- Max one gradient instance per page
