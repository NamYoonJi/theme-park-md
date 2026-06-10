# design_warm-workspace.md

> Theme: warm-white, friendly workspace aesthetic — modular cards, toggles, and a single calm accent.
> Use case: productivity / collaboration tool landing + template gallery.
> Dummy content: CatTower LTD / Kitty Park, Ya-ong Kim, Calico Lee.
> Icons: Lucide (ISC), stroke 1.75px. No platform emoji; decorative spots use 24px line-style SVG.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Friendly tooling | White background, near-black text, rounded corners, warm copy tone |
| 2 | Product UI as illustration | Simplified product screens (fictional data) serve as the visuals |
| 3 | Monochrome + one accent | Achromatic body; single accent reserved for CTA/links |
| 4 | Template-like structure | Content modularized into cards, galleries, toggles |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Default |
| `--bg-soft` | #F7F6F3 | Alternating sections (warm gray) |
| `--text` | #191918 | Body |
| `--text-soft` | #6F6E69 | Secondary |
| `--accent` | #2383E2 | CTA, links (single, generic UI blue) |
| `--callout` | #FBF3DB | Callout background |
| `--border` | #E9E9E7 | Cards, dividers |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Inter (SIL OFL) | 52px / weight 700 / -0.03em |
| Body | Inter | 16px / 1.6 |
| Serif accent | Lora (SIL OFL) | Quotes/editorial, max 1-2 instances |
| UI | Inter | 14px |

Scale: 12 / 14 / 16 / 20 / 28 / 40 / 52

## 4. Layout

- Max-width 1080px; reading column 720px
- Hero: left-aligned headline + product screen card on the right
- Gallery: 3-column card grid, 24px gap
- Section padding 96px

## 5. Components

| Component | Spec |
|---|---|
| CTA primary | `--accent` bg, radius 8px, height 44px |
| Card | White bg, 1px `--border`, radius 12px; hover shadow 0 4px 12px rgba(0,0,0,.06) |
| Callout | `--callout` bg, radius 8px, left spot icon |
| Toggle list | `chevron-right` rotates 90deg, 0.2s |
| Sidebar mock | 14px rows, hover `--bg-soft`, 12px indent steps |
| Testimonial | 32px circular avatar (fictional initials) + name + title |

## 6. Motion

| Target | Effect |
|---|---|
| Card hover | Shadow + translateY -2px, 0.2s |
| Toggle | Height auto transition 0.25s |
| Everything else | Minimal scroll effects — static-first |

## 7. Content Rules

- Testimonials use fictional people only: "Kitty Park, CEO of CatTower LTD"
- Data inside product screens is fictional
- Copy tone: second person, active voice, outcomes over features

## 8. Don't

- Do not adopt any third party's signature illustration style; use abstract or original artwork only
- Never more than one accent color
- Never substitute platform emoji for icons
