# Design Spec — Grainy Gradient Background

Style name: **GRAIN/FIELD** (current variant: `aurora`)
Use case: full-page backgrounds for landing, portfolio, product pages.
Implementation reference: `index.html` in this folder.

---

## 1. Concept

- Dark charcoal canvas + blurred vertical color streaks ("light curtains") + heavy uniform film grain.
- Background is fixed; all content scrolls over it.
- Foreground UI: white text, hairline rules, translucent pill buttons, line-style SVG icons. Nothing else.

## 2. Theming — How to Change Colors

All colors live in `:root` CSS variables. Edit only these.

### 2.1 Streak colors (the 6 knobs)

```css
:root{
  --c1:#7C3AED;  /* violet  — left curtain */
  --c2:#EC4899;  /* magenta — left-mid */
  --c3:#3B82F6;  /* blue    — center (widest streak) */
  --c4:#F59E0B;  /* amber   — right-mid (warm accent) */
  --c5:#22D3EE;  /* cyan    — right */
  --c6:#A855F7;  /* purple  — far right */
}
```

Swap any hex; layout, blur, grain are untouched. Preset swaps:

| Preset | --c1 | --c2 | --c3 | --c4 | --c5 | --c6 |
|---|---|---|---|---|---|---|
| `aurora` (default) | `#7C3AED` | `#EC4899` | `#3B82F6` | `#F59E0B` | `#22D3EE` | `#A855F7` |
| `deep-sea` | `#1226A8` | `#1D4ED8` | `#38BDF8` | `#0EA5E9` | `#7DD3FC` | `#1E3A8A` |
| `ember` | `#FF4B2B` | `#F97316` | `#3B82F6` | `#7C2D12` | `#0B1B4A` | `#450A0A` |
| `dusk` | `#3D3A8C` | `#6D28D9` | `#C9B8E8` | `#F4E0E8` | `#8B5CF6` | `#312E81` |

Composition rules when picking custom colors:
- Max 1–2 warm hues; the rest cool or neutral.
- Keep streak `opacity` at 0.35–0.6 — muted, never neon. Grain does the rest.
- The brightest streak should not be the centered one.

### 2.2 Base & foreground

```css
--base:#101013;                    /* canvas charcoal; keep near-black */
--fg:#fff;                         /* headings */
--fg-dim:rgba(255,255,255,.6);     /* body text */
--fg-faint:rgba(255,255,255,.38);  /* meta text */
--rule:rgba(255,255,255,.22);      /* hairlines */
```

### 2.3 Do not edit

- `--noise` (the grain tile data-URI). Grain density is part of the identity.

## 3. Background Construction

### 3.1 Streaks

- 6 absolutely-positioned divs inside a `position:fixed` field (`z-index:-1`, `aria-hidden`).
- Geometry: tall narrow ellipses, `width 8–16vw`, `height 45–80vh`, `border-radius:50%`, `filter:blur(85px)`.
- Spread across the middle band; a `.fade` overlay returns top 28% and bottom ~35% to `--base`.
- Ambient sway: `translateX(2.5vw) scaleY(1.06)`, 22–30s alternate loops, staggered per streak. Off under `prefers-reduced-motion`.

### 3.2 Grain (current method — tiled data-URI)

- One 256×256 SVG noise tile (`feTurbulence fractalNoise`, `baseFrequency 1.1`, `numOctaves 4`, `stitchTiles="stitch"`, desaturated, contrast slope 3 / intercept -1) encoded as a data-URI in `--noise`.
- Two full-bleed divs tile it:
  1. `mix-blend-mode:overlay`, `opacity:1`
  2. `mix-blend-mode:soft-light`, `opacity:.9`, `background-position:128px 64px` (offset breaks tile alignment)
- Why tiles, not inline `<svg>` layers: inline SVGs with `%`-sized filter regions render partial "patches" in some browsers. A tiled `background-image` cannot mis-size. (v2.1.1 fix)
- Target feel: pushed-film grit; no smooth gradient area anywhere.

## 4. Typography

| Role | Settings |
|---|---|
| Display | weight 800, `clamp(52px, 7vw, 118px)`, line-height 1.02, sentence case + trailing period |
| Section heads | 28px / 700 |
| Body / lede | 15px / 1.7, `--fg-dim` |
| Meta / captions | 13px, `--fg-faint` |

Font stack: `-apple-system, BlinkMacSystemFont, "Inter Tight", Inter, "Helvetica Neue", sans-serif`.
SF Pro license forbids self-hosting/embedding; this stack uses it as the OS font on Apple devices (permitted) and falls back to Inter elsewhere.

## 5. Components

| Component | Spec |
|---|---|
| Top bar | 3-col grid: wordmark / centered pills / line-icon buttons. |
| Pill (primary) | `rgba(255,255,255,.25)` fill, `rgba(255,255,255,.35)` 1px border, white text, `backdrop-filter:blur(6px)`. Never opaque white. |
| Pill (secondary) | transparent, `--rule` border. |
| Archive list | Right-aligned month links. Active month: 40px/600/white. Adjacent: 30px/`--fg-dim`. Rest: 24px/`--fg-faint`. Click moves `.active` to that month and `.near` to its neighbors (JS, transition .25s). |
| Notes sidebar | Left vertical hairline, rows divided by hairlines, 15px title with 15px line icon + 13px caption. |
| Hairlines | 1px `--rule`, full-width, framing hero and every section. |
| Cards (gallery) | 1px `--rule` border, radius 14px, `rgba(255,255,255,.03)` fill, gradient thumb 180px. |
| Changelog row | grid `120px 110px 1fr auto`: version / date / message / pill tag. |

## 6. Page Structure

```
topbar -> hairline -> hero (headline+lede | archive | notes)
-> hairline -> in-page nav -> hairline
-> Gallery (3-col cards) -> hairline
-> Changelog (rows) -> hairline
-> Contact (large email + icon links) -> hairline -> footer
```

- Side margins 96px desktop / 24px mobile; all columns stack below 1000px.

## 7. Iconography

- No emoji. Open-source line-style SVG (Lucide / Feather), 1.5px stroke, `currentColor` or `--fg-dim`.

## 9. Accessibility

- Background layers `aria-hidden="true"`; semantic HTML order.
- Body text only over regions darkened by `.fade` or verified AA contrast.
- Streak sway disabled under `prefers-reduced-motion`; grain is static.

## 10. Changelog (of this spec)

- v2.1.1 — Grain moved from inline SVG layers to tiled data-URI backgrounds (fixes partial-render patch). Primary pill changed to 25% translucent white. Archive months made click-interactive. Theming section added with 6-variable palette system.
- v2.1.0 — Aurora palette (vertical streaks on charcoal); full-page layout (gallery / changelog / contact); SF system font stack.
- v2.0.x — Heavy grain pipeline; bloom-based field; initial layout.