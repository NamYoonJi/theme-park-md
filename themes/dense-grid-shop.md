# dense-grid-shop.md

> Theme: white canvas, high-density product grid, black/white chrome with one warm red for prices — browsing as the hero.
> Use case: catalogs, marketplaces, galleries, ranked lists — any card-heavy browse surface.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | The grid is the page | Cards from the first viewport; hero is at most one slim banner |
| 2 | Chrome stays monochrome | Nav, filters, tabs in black/white/gray; color only on prices, badges, saves |
| 3 | Density with discipline | 12px UI text, tight gaps, but fixed aspect ratios and aligned baselines |
| 4 | Everything is ranked | Numbers, counts, and badges quantify every card |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Page |
| `--panel` | #F7F7F7 | Filter bar, input fills, image placeholders |
| `--ink` | #222222 | Text, active states |
| `--ink-mid` | #717171 | Secondary text, counts |
| `--border` | #DDDDDD | 1px rules, card outlines on hover |
| `--accent` | #E8474D | Sale prices, discount rates, save-heart active (deliberately offset warm red — do not shift toward pink) |
| `--badge` | #222222 | Rank badges (white text) |

Focus ring (keyboard): double ring `0 0 0 2px #FFFFFF, 0 0 0 4px #222222`.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| All text | Pretendard (SIL OFL) | Latin + Korean in one face |
| Page / section title | — | 20px / 700 |
| Card brand line | — | 12px / 700 |
| Card product line | — | 13px / 400, 2-line clamp |
| Price | — | 14px / 700; discount % in `--accent` left of price |
| UI (tabs, chips, counts) | — | 12px / 500 |

Scale: 11 / 12 / 13 / 14 / 16 / 20. `font-variant-numeric: tabular-nums` on all counts and prices.

## 4. Layout

- Full-width with 16px side padding; max 1440px
- Top nav 56px: logotype left, search pill center (pill radius, `--panel` fill, height 40px), icon buttons right
- Category tab row: 12px tabs, active = 2px `--ink` underline; horizontally scrollable
- Sticky filter bar (under tabs): filter chips + sort dropdown right, 48px tall, 1px bottom border
- Product grid: `repeat(auto-fill, minmax(180px, 1fr))`, gap 12px × 28px (tight columns, roomier rows)
- Image aspect ratio: 3:4 fixed, `--panel` placeholder
- Section breaks: 8px `--panel` full-bleed band between modules (no margins-only separation)
- Ranked module: horizontal scroll row of cards with rank badges 1-10

## 5. Radius Scale (fixed — never freehand)

| Token | Value | Used on |
|---|---|---|
| xs | 2px | Rank badges, discount tags |
| sm | 4px | Product thumbnails, small buttons |
| md | 12px | Feature cards, modals, dropdowns |
| lg | 24px | Bottom sheets, large banners |
| pill | 9999px | Search bar, filter chips |

## 6. Components

| Component | Spec |
|---|---|
| Product card | Borderless: 4px-radius image + text block below (brand 12px/700, name 13px 2-line, price row); hover: 1px `--border` outline + second image swap |
| Price row | `--accent` percent 14px/700 + `--ink` price 14px/700 + struck list price 12px `--ink-mid` |
| Save (heart) | 24px outline icon bottom-right of image; active: `--accent` fill; count 11px below |
| Rank badge | 20px square, `--badge` bg, white 11px/700, radius 2px, top-left of image |
| Filter chip | Height 32px, pill, 1px `--border`, 12px text; active: `--ink` bg white text |
| Tag | 11px, `--panel` bg, radius 2px, 2px 6px padding |
| Tab | 12px; active 700 + 2px underline; inactive `--ink-mid` |
| Banner | 12px radius, `--panel` bg, 1px border, max 120px tall |
| Skeleton | `--panel` blocks shimmering 1.4s linear (off under reduced motion) |

## 7. Motion

| Target | Effect |
|---|---|
| Image swap (hover) | opacity crossfade 0.2s ease |
| Heart toggle | scale 1→1.3→1, 0.3s cubic-bezier(.34,1.56,.64,1) |
| Chip/tab state | instant (no transition) — browsing must feel snappy |
| Grid enter | opacity 0.25s, 30ms stagger, first 12 cards only |
| Sticky bar | shadow `0 1px 0 var(--border)` appears when stuck |
| Reduced motion | swap becomes instant; heart pop off |

## 8. Don't

- No hero section taller than 120px; the grid starts above the fold
- Color never on chrome — accent is reserved for price/save/badge semantics
- No shadows on cards; elevation only on dropdowns/sheets (0 2px 16px rgba(0,0,0,.12))
- Never crop product images to non-3:4 ratios; never rounded more than 4px
- No more than one ranked row per page section
- Don't animate layout (no reflowing masonry); grid positions are stable
