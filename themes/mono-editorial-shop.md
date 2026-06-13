# mono-editorial-shop.md

> Theme: black-and-white editorial commerce — magazine-style front, curated grids, mixed Latin/Korean typography.
> Use case: curation-led shop with story-driven merchandising.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Curation over catalog | Few products per view, each with an editorial reason-to-buy |
| 2 | Magazine front, store back | Home reads as a magazine cover; commerce UI appears on detail pages |
| 3 | Type does the branding | Black-on-white typography is the identity; imagery stays unfiltered |
| 4 | Mixed-script discipline | Latin display + Korean body, baseline-aligned deliberately |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Default |
| `--ink` | #000000 | Text, buttons |
| `--gray` | #8E8E8E | Secondary, pre-discount values |
| `--line` | #ECECEC | Hairlines |
| `--inverse` | #000000 bg / #FFFFFF text | Editorial feature blocks |

No accent color. Notice/sale states use `--ink` weight changes, not red.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Latin display | Archivo (SIL OFL) | 48-64px / weight 600 / -0.02em |
| Korean body | Pretendard (SIL OFL) | 15px / 1.65 |
| Editorial serif (KR) | Noto Serif KR (SIL OFL) | 22px / feature intros |
| Meta | Pretendard | 12px / `--gray` |

Scale: 12 / 13 / 15 / 18 / 24 / 36 / 48 / 64

## 4. Layout

- Max-width 1280px; mobile is the primary target
- Home: full-width editorial hero (one feature) -> 2-column story cards -> 4-column product grid
- Product grid: tight 12px gaps, image ratio 3:4 fixed
- Detail page: image column left (sticky) + text column right (scrolls)

## 5. Components

| Component | Spec |
|---|---|
| Story card | Image + Latin kicker 12px uppercase + Korean title 18px + one-line dek |
| Product tile | Image, brand 12px `--gray`, name 14px, price 14px weight 600 |
| CTA (buy) | Full-width `--ink` bg, white text, radius 0, height 52px |
| Like | Lucide `heart`, stroke -> fill on toggle |
| Tab nav | Uppercase 13px, active = 2px `--ink` underline |
| Editorial block | `--inverse`, serif intro, max 560px measure |

## 6. Motion

| Target | Effect |
|---|---|
| Image hover | Second image crossfade 0.25s |
| Grid entry | Fade-up 12px, stagger 0.04s, once |
| Sticky detail | Image column position: sticky; no parallax |
| Forbidden | Autoplaying carousels, zoom-on-hover |

## 7. Don't

- No accent or sale-red color (monochrome discipline)
- No filters or treatments on product imagery


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#FFFFFF; --ink:#000000; --gray:#8E8E8E; --line:#ECECEC;
  --radius:0;
  --font-latin:"Archivo",sans-serif; --font-kr:"Pretendard",sans-serif; --font-serif-kr:"Noto Serif KR",serif;
}
```
