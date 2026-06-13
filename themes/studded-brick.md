# Design Spec — Studded Brick UI

Codename: `BRICKBOARD`
Type: Dark studded-brick design system. Layout and elements are built from interlocking toy-style bricks. Typography stays clean and modern (no pixel/blocky fonts).

---

## 1. Concept

- The entire page reads as a black studded baseplate. Every UI element (cards, buttons, images, charts, avatars) is assembled from brick units snapped to that baseplate grid.
- Fonts are NOT brick-styled. Text floats on top of the brick world in a clean grotesque/serif pairing. Contrast between "toy-built" surfaces and "adult" typography is the core tension of the design.
- Images and hero graphics are rendered as brick mosaics: pixelated color blocks, each cell carrying a circular stud highlight.

## 2. Design Tokens

### 2.1 Color

| Token | Hex | Use |
|---|---|---|
| `--plate-black` | `#0D0D11` | Page background (baseplate) |
| `--plate-cell` | `#15151B` | Visible baseplate cell tint |
| `--stud-line` | `#1F1F27` | Stud outline / grid line on baseplate |
| `--brick-orange` | `#E8623C` | Primary accent brick |
| `--brick-purple` | `#9A6BE0` | Secondary brick |
| `--brick-blue` | `#5BB8E8` | Tertiary brick |
| `--brick-green` | `#5FCE8B` | Success / quaternary brick |
| `--brick-pink` | `#F2A7C3` | Soft accent brick |
| `--ink-white` | `#F4F2EE` | Headline / primary text |
| `--ink-dim` | `#8B8B96` | Secondary text, captions |

Rules:
- Background is always `--plate-black` with the baseplate grid visible at low contrast.
- Brick colors are used as solid fills only. No gradients across a brick; depth comes from stud shading.
- Max 3 brick colors per section. Orange leads.

### 2.2 Typography

| Role | Face | Weight | Notes |
|---|---|---|---|
| Display | "Instrument Serif" or "Fraunces" | 400–500 | Large, tight leading. Set in white over the baseplate |
| Body / UI | "Inter" (or any neutral grotesque) | 400 / 500 | 15–16px base, 1.6 line-height |
| Label / Eyebrow | Same grotesque | 600, uppercase, +0.12em tracking | Small caps style labels, e.g. `UX/UI DESIGN RESOURCE` |

Rules:
- No pixel, bitmap, or blocky display fonts anywhere.
- Text never sits inside a single brick cell; text spans freely across the grid.

### 2.3 Grid (the baseplate)

- Unit: `--stud: 48px` desktop / `40px` tablet / `32px` mobile. One unit = one stud cell.
- All brick-built elements snap position AND size to whole stud units.
- Page padding, gaps between cards: multiples of one stud unit.
- Free-floating text blocks may ignore the snap; brick surfaces may not.

## 3. The Brick System (core visual mechanic)

### 3.1 Baseplate background

- CSS: repeating grid of `--stud` cells.
- Each cell: 1px inset border in `--stud-line`, plus a centered circle (≈55% of cell width) drawn with a radial-gradient — top-lit (lighter top edge, darker bottom edge) to simulate a raised stud.
- Implementation: one `background-image` stack (two `linear-gradient`s for grid lines + one `radial-gradient` for the stud), `background-size: var(--stud) var(--stud)`. No per-cell DOM nodes.

### 3.2 Brick surface (colored elements)

Every colored element = a cluster of stud cells:

1. Fill: solid brick color, clipped to whole stud cells (sizes in `calc(var(--stud) * n)`).
2. Stud overlay: same radial-gradient stud pattern as the baseplate, rendered on top at low opacity (`~0.18` white highlight top / `~0.22` black shadow bottom).
3. Cell seams: 1px darker lines (same color, ~12% darkened) between cells so individual bricks read.
4. Per-cell tone jitter: optional `±4%` lightness variation cell-to-cell (pseudo-random via small overlay pattern) so large areas look hand-assembled, not flat.
5. Corners: square by default. "Rounded" shapes are approximated by stepping cells (staircase pixelation), never by `border-radius`.

### 3.3 Brick mosaic images

- Photos/illustrations are replaced by mosaics: downsample the source to the stud grid, render each cell as a solid brick with stud overlay.
- Recommended: `<canvas>` downsampling at runtime, or pre-baked CSS grid of cells for static pages.
- Mosaic edges follow the pixel staircase — circles become stepped, mosaic-style outlines.

### 3.4 Elevation

- One elevation step only: a raised brick casts a 1-stud-offset hard shadow (`box-shadow: 0 calc(var(--stud)/6) 0 rgba(0,0,0,.45)`), suggesting it sits one plate higher.
- No soft/blurred drop shadows.

## 4. Components

| Component | Spec |
|---|---|
| Button | 1-stud tall (min), width snapped to studs. Brick fill + stud overlay. Hover: lifts one elevation step + translates up 2px. Active: presses flat (shadow removed). Label in grotesque 600 |
| Card | Brick-bordered panel: interior is `--plate-cell`, border is a 1-stud-wide colored brick frame OR a header bar made of bricks. Content text sits on dark interior, not on color |
| Nav bar | Transparent over baseplate. Logo left, links right. Active link marked by a 1×1 brick under the label |
| Tag / Chip | 1-stud tall single brick, soft colors (`--brick-pink`, `--brick-blue`), dark text allowed on light bricks |
| Avatar | Stepped-circle brick mosaic, 2×2 or 3×3 studs, initials overlaid in grotesque |
| Stat / Chart | Bar charts are literal brick stacks (each bar = column of stud cells). Values in display serif |
| Divider | A single 1-stud-tall row of alternating brick cells, 3–5 cells long, left-aligned |
| Input | Recessed cell: `--plate-black` fill, 1px `--stud-line` border, focus = 2px brick-orange border snapped to grid |
| Footer | Baseplate continues; content in `--ink-dim`; one brick-built logo mark |

## 5. Layout

### 5.1 Hero (signature moment)

```
┌────────────────────────────────────────────────┐
│ baseplate grid runs edge-to-edge               │
│                                                │
│  EYEBROW LABEL                ┌──▓▓▓▓──┐       │
│  Display serif headline       │ brick   │      │
│  spanning ~6 grid cols        │ mosaic  │      │
│  Body copy, 2 lines           │ artwork │      │
│  [Brick Button] [Ghost]       └──▓▓▓▓──┘       │
└────────────────────────────────────────────────┘
```

- Left: clean type stack. Right: large brick mosaic (product logo / mascot / data shape) assembled from 3 brick colors.
- Signature element: the mosaic assembles on load — cells snap in one-by-one (staggered, 8–14ms apart, scale 1.15→1 with a hard ease-out "click").

### 5.2 Sections

- Section rhythm: alternating "type-led" (text on bare baseplate) and "brick-led" (cards/mosaics dominant) bands.
- Max content width: 24 studs desktop, centered; baseplate bleeds full width.

## 6. Motion

| Trigger | Behavior |
|---|---|
| Page load | Hero mosaic snap-in (see 5.1). One orchestrated moment only |
| Scroll reveal | Brick elements assemble row-by-row (bottom-up), 200ms per row, once |
| Button hover | Lift one plate (translateY −2px + hard shadow) |
| Button press | Press flat, 80ms |
| Reduced motion | All assembly animations replaced by instant render; hover lift kept (no transition) |

- All easings: `cubic-bezier(0.2, 0, 0, 1)` — abrupt, mechanical "snap", never bouncy.

## 7. Iconography

- No emoji (no Unicode/mobile-style emoji anywhere, including copy and labels).
- Use open-source line-style SVG icons: Lucide (preferred) or Feather. Stroke `1.5px`, `currentColor`, 20–24px.
- Icons sit in text color (`--ink-white` / `--ink-dim`); they are never brick-rendered.

## 8. Dummy Content (for demo pages)

- Company: **CatTower LTD** — fictional design-tools studio.
- People: **Kitty Park** (Design Lead), **Ya-ong Kim** (UI Designer), **Calico Lee** (Engineer).
- Sample copy directions: "Build interfaces brick by brick", product name "Brickboard", resource label "UX/UI Design Resource".
- Never use real people, real brands, or real publications. The studded-brick look is a generic visual metaphor only — do not reference, name, or depict any specific toy-brick brand, logo, or trademark in copy or imagery.

## 9. Quality Floor

- Responsive: stud unit scales down (48→40→32px); mosaics reduce cell count, not cell size, on mobile.
- Contrast: body text ≥ 4.5:1 against `--plate-black`; never set body text on saturated bricks.
- Keyboard focus: 2px `--brick-orange` outline, offset 2px, grid-snapped where possible.
- Brick surfaces are CSS-only (gradients/patterns); avoid per-stud DOM except inside mosaics (cap ≈ 400 cells per mosaic).


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --plate-black:#0D0D11; --plate-cell:#15151B; --stud-line:#1F1F27;
  --brick-orange:#E8623C; --brick-purple:#9A6BE0; --brick-blue:#5BB8E8;
  --brick-green:#5FCE8B; --brick-pink:#F2A7C3;
  --ink-white:#F4F2EE; --ink-dim:#8B8B96;
  --stud:48px; --radius:0;
  --font-display:"Instrument Serif",serif; --font-body:"Inter",system-ui,sans-serif;
}
```
