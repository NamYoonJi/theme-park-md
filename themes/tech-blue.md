# Design Spec — "Global Tech Brand" Style (Samsung.com-inspired)

Codename: `techcorp-global`
Reference feel: large consumer-electronics brand homepage (samsung.com/sec style) — clean, white, product-photography-driven, full-bleed promotional cards, dense but ordered.
Rule: any demo content built from this spec must use fictional brands and persons only — never real people or publications.

---

## 1. Design Principles

1. Product is the hero — UI recedes; large product photography on neutral backgrounds carries the page.
2. Card-grid merchandising — homepage is a stack of full-width and split promotional cards, each one self-contained (image + headline + CTA).
3. White-first, black-accent — near-zero chroma chrome; color comes only from product imagery and occasional promo gradients.
4. Pill CTAs — rounded-full buttons, black fill or 1px black outline. No other button shapes.
5. Quiet typography, loud scale — one sans family; hierarchy by size/weight only, never by color or decoration.
6. Edge-to-edge sections, contained text — sections span viewport; text aligns to a 1440px max container.

## 2. Color Tokens

| Token | Hex | Use |
|---|---|---|
| `bg-base` | `#FFFFFF` | Page background |
| `bg-soft` | `#F7F7F7` | Card / section alt background |
| `bg-inverse` | `#000000` | Footer, dark promo cards, primary CTA |
| `ink-primary` | `#000000` | Headlines, body |
| `ink-secondary` | `#555555` | Sub copy, captions |
| `ink-tertiary` | `#909090` | Legal, disclaimers |
| `line` | `#E5E5E5` | Dividers, card borders |
| `accent-blue` | `#1428A0` | Brand lockup, active nav, campaign accent words, NEW tags |
| `badge-navy` | `#2B3DA8` | Benefit-card badge fill |
| `sky` | `#D9E9FA` | Campaign hero background (flat, no texture) |
| `promo-gradient` | `#0F2027 → #2C5364` | Optional dark hero gradients |

Rule: `accent-blue` never appears on buttons; it is reserved for brand identity, active navigation states, campaign accent text, and NEW tags.

## 3. Typography

| Role | Family | Size / Weight | Notes |
|---|---|---|---|
| Display (hero) | "Inter", system sans | 56–72px / 700 | -0.02em tracking, tight leading 1.05 |
| Section title | same | 36–44px / 700 | Centered above card grids |
| Card headline | same | 24–28px / 700 | |
| Body | same | 16px / 400, 1.6 lh | `ink-secondary` for sub copy |
| Caption / legal | same | 12px / 400 | `ink-tertiary` |
| Nav / utility | same | 14px / 500 | |

One family only. Korean-market parity: if KR locale, substitute "Noto Sans KR" with identical scale.

## 4. Layout

- Container: `max-width: 1440px`, side padding 24px (mobile) / 40px (desktop).
- Grid: 12-col, 24px gutter.
- Section vertical rhythm: 12px gap between promo cards; 80px between distinct sections.
- Card radius: 10px (cards), 14px (large surfaces). Curvature is kept low; only buttons are pills (9999px).
- Breakpoints: 768 / 1024 / 1440.

### Page anatomy (homepage)

```
┌──────────────────────────────────────────────┐
│ Utility bar (links, locale)        h:40 thin │
├──────────────────────────────────────────────┤
│ GNB: logo | category nav | search, cart, user│  sticky, mega-menu
├──────────────────────────────────────────────┤
│ CAMPAIGN HERO (light textured bg)            │  ~760px
│  left: campaign copy + emblem + date range   │
│  right: 2–3 stacked benefit cards            │
│  bottom-center: text link + outline pill CTA │
│  bottom-right: floating AI assistant button  │
├──────────────────────────────────────────────┤
│ "Featured" — 4-up product card row           │
├──────────────────────────────────────────────┤
│ CATEGORY SECTION (in-page, samsung PLP style)│
│  H1 + subcategory card carousel + tabs       │
│  filter bar + dropdown filter pills          │
├──────────────────────────────────────────────┤
│ Editorial strip: 3-up news/story cards       │
├──────────────────────────────────────────────┤
│ Footer (bg-inverse, multi-column link tree)  │
└──────────────────────────────────────────────┘
```

### Campaign hero (observed pattern)

- Background: flat `sky` (#D9E9FA). No texture, no gradient.
- Left block: 2-line sentiment copy (18px, `accent-blue`), emblem illustration, campaign title 44–56/700 with one accent-blue word, date range 24/700 in lighter blue.
- Right block: stacked **benefit cards**, width ~640px, 16px gap.
- Bottom center: underlined text link ("See event details") + outline pill CTA.
- Floating button: 56px circle, white, soft shadow, sparkle SVG, fixed bottom-right.

### Benefit card anatomy

```
┌────────────────────────────────────────────────┐ tint bg #EDF1FB or
│ ┌──────────┐  Title 18/700                     │ white + 1px line,
│ │ label 12 │  Sub copy 14/400 ink-2            │ radius 16
│ │ VALUE 28 │  *disclaimer 12/400 ink-3         │
│ └──────────┘                                   │ badge: navy #2B3DA8,
└────────────────────────────────────────────────┘ radius 12, white text
```

### Mega-menu anatomy

- Full-width white panel under GNB, top border `line`, opens on hover/focus.
- Active nav item: `accent-blue` text + 2px blue underline.
- Left zone: product thumbnail grid (7-up desktop), each item = image 120px + 14/500 label; optional `NEW` tag (12/600, `accent-blue`) above image.
- Right zone: divider + "Learn more" column header (14, ink-3) + vertical text links (16/400).

### Category page (PLP) anatomy

```
H1 (48/700, left)
┌active card────┐┌card┐┌card┐┌card┐┌card┐ →  subcategory carousel
│title+desc+img ││icon││icon││icon││icon│    active: white + 1px black
└───────────────┘└────┘└────┘└────┘└────┘    border; rest: bg-soft
────────────●────────────────  (←)(→)        progress bar + circle arrows
전체  TypeA  TypeB  TypeC ...                tab row, active = underline
필터 | 279 results          [toggle] sub    filter status bar
(배송유형 ▾)(사이즈 ▾)(유형 ▾)(가격대 ▾)...     dropdown filter pills
```

- Subcategory card: radius 10; active card 2-col (text left, image right); inactive cards: centered title top + icon/image bottom, `bg-soft`.
- Tab row: 16/500, active 700 + 2px black underline.
- Filter pills: white, 1px `line`, radius 9999, 14/500, chevron-down SVG; hover border black.
- Results toggle: iOS-style switch, 40×22, active black.

## 5. Components

### 5.1 GNB (global nav)
- Height 80px, white, sticky; bottom border `line` appears only after scroll.
- Left: CatTower LTD wordmark (`accent-blue`). Center: category links (Cat Towers, Scratchers, Smart Feeders, Accessories, Support). Right: SVG icons — search, cart, account.
- Mega-menu on hover: full-width white panel, 4-col product thumbnails, 200ms fade.

### 5.2 Campaign hero
- Light textured full-width section (not a card), min-height 720px desktop.
- Left copy column + right benefit-card stack (see anatomy); stacks vertically <1024px.
- Floating AI assistant button: fixed, 56px white circle, sparkle line-SVG, shadow `0 4px 16px rgba(0,0,0,.12)`.

### 5.2b Benefit card
- Container: white, radius 10, soft shadow `0 2px 10px rgba(20,40,160,.06)`, padding 20–24.
- Badge: `badge-navy`, radius 8, ~150px wide, label 12/600 + value 26–30/700, white.
- Right text: title 17–18/700 (may contain accent-blue spans), sub 14 `ink-2`, disclaimers 12 `ink-3`.

### 5.2c Mega-menu
- Opens below GNB on hover/focus; closes on mouseleave/Esc.
- Thumbnail grid items: 120px line-art image, 14/500 label, optional `NEW` 12/600 accent-blue tag.
- Right "Learn more" link column separated by 1px `line` divider.

### 5.2d Subcategory carousel (PLP)
- Horizontal scroll row; active card outlined (1px black, white bg), inactive `bg-soft`.
- Below: progress bar (2px track `line`, black fill = scroll progress) + 48px circular outline arrow buttons.

### 5.2e Filter system (PLP)
- Tab row → status bar ("필터 | N results" left, toggle + help right) → pill dropdown row.
- Pills horizontally scrollable on mobile.

### 5.3 Product card (4-up)
- `bg-soft` tile, image centered, name 16/600, price 16/700, star rating (SVG line stars), "Buy" pill outline.
- Hover: image scale 1.04, 300ms ease.

### 5.4 Buttons
| Variant | Style |
|---|---|
| Primary | black fill, white text, pill, 14px/600, padding 12×28 |
| Secondary | transparent, 1px black border, pill |
| On-dark | white fill / white outline inversions |
Hover: 90% opacity (filled) or black-fill flip (outline).

### 5.5 Footer
- `bg-inverse`, 5-column sitemap, 13px white/60 links; bottom row: locale selector, legal, social SVG icons.

## 6. Iconography

- Open-source line icons only (Lucide / Feather). 1.5px stroke, 24px grid, `currentColor`.
- No emoji anywhere. Ratings, badges, arrows = inline SVG.
- Common set: `search`, `shopping-cart`, `user`, `chevron-down`, `arrow-right`, `star`, `play`, `pause`, `globe`.

## 7. Motion

| Element | Effect | Duration |
|---|---|---|
| Card hover | translateY(-4px) + shadow soft | 250ms ease-out |
| Mega-menu | fade + 8px drop | 200ms |
| Hero slide | crossfade | 500ms |
| Scroll reveal | opacity 0→1, y 24→0, once | 400ms |

Disable all under `prefers-reduced-motion`.

## 8. Accessibility & Quality Floor

- Contrast: all text ≥ 4.5:1 against background.
- Visible focus ring: 2px `#000` offset 2px.
- Carousel: keyboard operable, pause control, `aria-roledescription="carousel"`.
- Images: meaningful `alt`; decorative product shots `alt=""` when adjacent text duplicates.
- Semantic landmarks: `header / nav / main / footer`.


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg-base:#FFFFFF; --bg-soft:#F7F7F7; --bg-inverse:#000000;
  --ink-primary:#000000; --ink-secondary:#555555; --ink-tertiary:#909090; --line:#E5E5E5;
  --accent-blue:#1428A0; --badge-navy:#2B3DA8; --sky:#D9E9FA;
  --radius-card:10px; --radius-lg:14px; --radius-pill:9999px;
  --font-sans:"Inter",system-ui,sans-serif;
}
```
