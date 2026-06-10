# quiet-paper.md

> Theme: paper-toned quiet luxury — long-form copy, hairline rules, zero urgency, rectilinear geometry.
> Use case: premium product commerce with an editorial voice.
> Icons: Lucide (ISC), stroke 1px (hairline). No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Quiet authority | No sale banners, no urgency patterns, no exclamation marks |
| 2 | Text sells | Long-form product descriptions; literate, measured copy |
| 3 | Muted world | Entire palette within a narrow warm-neutral range |
| 4 | One product, one frame | Product imagery isolated, centered, generous margins |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FFFEF2 | Warm paper |
| `--bg-alt` | #F6F5E8 | Alternating sections |
| `--text` | #333330 | Body charcoal |
| `--text-soft` | #6B6B66 | Secondary |
| `--line` | #D8D7CC | Hairline dividers |
| `--dark` | #252525 | Footer / inverted blocks |

No accent color. Interaction states use underlines and tone shifts only.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Archivo (SIL OFL) | 40-48px / weight 400 / normal tracking — large but quiet |
| Body | Archivo | 16px / 1.7 |
| Editorial serif | Lora (SIL OFL) | 20px / quotes and category intros |
| Meta | Archivo | 12px / uppercase / letter-spacing 0.1em |

Scale: 12 / 14 / 16 / 20 / 28 / 40 / 48 — weight stays 400-500 throughout; size carries hierarchy.

## 4. Layout

- Max-width 1280px; reading measure 640px
- Hero: full-bleed muted visual (original artwork or license-verified imagery) + minimal overlay text
- Product grid: 3 columns, large gaps (48px), no card borders — whitespace separates
- Section padding 128px; hairline rules between major blocks

## 5. Components

| Component | Spec |
|---|---|
| CTA | Underlined text link or 1px-border rectangle, radius 0, height 48px |
| Product tile | Image on `--bg-alt`, name 16px, one-line description, price 14px |
| Description block | 640px measure, 2-3 paragraphs, serif intro line |
| Drawer | Slides from right, `--bg`, hairline left edge |
| Footer | `--dark` bg, cream text, newsletter input with underline-only field |
| Input | No box; bottom 1px `--line`, focus -> `--text` |

## 6. Motion

| Target | Effect |
|---|---|
| Page transitions | Crossfade 0.4s |
| Image hover | Opacity 1 -> 0.92 (no zoom) |
| Drawer | translateX 0.35s ease |
| Forbidden | Parallax, autoplaying carousels, badges, countdowns |

## 7. Don't

- No radius anywhere (rectilinear system)
- No bold weights above 500
- No dark-pattern commerce elements (timers, scarcity counters)
- Do not pair this aesthetic with packaging/photography styles that imitate an existing premium brand's identity bundle — original artwork only
