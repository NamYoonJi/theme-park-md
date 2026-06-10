# phosphor — Bitmap Terminal Design System

A nerdy, geeky, phosphor-green CRT aesthetic. Everything is angular, pixelated, and
deliberately un-smoothed — like a green monochrome terminal from the early 80s.

---

## 1. Design Principles

- **No edge smoothing.** All raster art uses `image-rendering: pixelated`. Pixel sprites
  are drawn block-by-block on `<canvas>` with hard square pixels (no anti-aliasing).
- **Everything is angular.** `border-radius: 0` everywhere. No rounded corners, no pills,
  no soft shadows.
- **Single accent, dark canvas.** Pure black background, one phosphor-green family. The
  glow comes from the color itself, not from blur (one subtle `text-shadow` on the hero only).
- **Terminal as metaphor.** Prompts (`>`, `$`), monospace text, blinking cursor, a working
  command line, and a fixed status bar make the page read like a TTY session.
- **Structure encodes content.** Numbered cards (01/02/03…) are used only where the list is
  a real enumeration. Dashed dividers separate sections like ruled paper.

---

## 2. Color Tokens

```css
:root{
  --green:      #00ff41;  /* primary text, active state, accents       */
  --dark-green: #00aa2b;  /* secondary / muted body text               */
  --dim-green:  #004d15;  /* borders, dividers, inactive labels, fills */
  --black:      #000000;  /* page + surface background                 */
}
```

- `--green` — anything live or important: headings, hovered state, active quote line.
- `--dark-green` — body copy, descriptions, terminal command echoes.
- `--dim-green` — 1px borders, grid lines, placeholder/inactive text, card backgrounds on hover.
- `--black` — the only background. Surfaces are distinguished by 1px green borders, not fills.

There is **no white, no gray, no second hue.** Contrast is built entirely from the three greens on black.

---

## 3. Typography

Both faces are open-source (Google Fonts).

| Role            | Font                | Usage                                              |
|-----------------|---------------------|----------------------------------------------------|
| Display / chrome | **Doto** (wght 900) | Hero title, logo, big numbers, section labels, footer |
| Body / data     | **Share Tech Mono** | All paragraph text, terminal, captions, tags        |

```html
<link href="https://fonts.googleapis.com/css2?family=Doto:wght@100..900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

**Doto** is a dot-matrix / bitmap display face — it carries the "each glyph is made of pixels"
identity. Use it at heavy weight (900) and large sizes only. **Share Tech Mono** is a clean
fixed-width terminal font for everything readable.

### Type scale
- Hero title: `64px`, `letter-spacing: -2px`, Doto 900
- Footer big: `48px`, Doto 900
- Card number: `32px`, Doto 900
- Stat number: `28px`, Doto 900
- Section label: `11px`, `letter-spacing: 4px`, uppercase, Doto 900
- Body / terminal: `12–13px`, `line-height: 2`, Share Tech Mono
- Caption / tag: `10px`, `letter-spacing: 2px`

Section labels are wrapped in brackets via CSS: `[ LABEL ]`.
Hero subtitles are wrapped in dashes: `-- subtitle --`.

---

## 4. Layout

- Max content width `1200px`, centered, `24px` side padding.
- **Section rhythm:** each `.section` is `48px` vertical padding with a `1px solid --dim-green`
  bottom border, separated by a dashed `.px-div` divider.
- **Grids use 1px gaps over a green background** so cell edges read as hairline rules:
  `gap: 1px; background: var(--dim-green);` with each cell `background: var(--black);`.
  This produces a CRT "spreadsheet" grid without drawing individual borders.
- **Hero** is a two-column grid (text left, pixel canvas + quote block right), collapsing to
  one column under 700px.

---

## 5. Signature Elements

1. **Pixel-art canvas sprite.** A bitmap drawn on `<canvas>` from a 2D array of 0/1, scaled
   ×5 with no smoothing. Swap the array to change the subject (camera → cat → robot → etc).
2. **Scanlines.** A fixed full-screen overlay of faint horizontal lines:
   ```css
   background: repeating-linear-gradient(0deg, transparent 0 2px, rgba(0,0,0,.03) 2px 4px);
   pointer-events: none;
   ```
3. **Live terminal.** A read-only command log plus a working `<input>` prompt that responds
   to typed commands (`help`, etc.). Prompt format: `you@host/path >`.
4. **Fixed status bar.** Bottom-pinned `--dim-green` bar with black Doto text: left = version,
   center = live clock, right = STATUS.
5. **Cycling quote block.** Lines fade between `--dark-green` and `--green` on a timer to mimic
   a refreshing display.
6. **Dashed dividers** (`.px-div`): a `repeating-linear-gradient` of 4px dash / 4px gap.

---

## 6. Interaction & Motion

- **Hover:** links/labels go `--dim-green → --green`; cards invert to a `--dim-green` fill.
  Transitions are fast (`0.05s`) or instant — nothing eases slowly; this is a snappy terminal.
- **Blinking cursor:** `@keyframes blink` (step-end, 1s) on an 8×14px green block.
- **No smooth scrolling, no parallax, no fade-up-on-scroll.** Motion is limited to the
  cursor blink, the cycling quote, and the live clock.
- Respect `prefers-reduced-motion` by disabling the quote cycle / cursor blink if added.

---

## 7. Do / Don't

**Do**
- Keep all corners square.
- Keep the palette to the three greens on black.
- Use Doto sparingly (chrome only) and Share Tech Mono for everything readable.
- Make canvas sprites from explicit pixel arrays so they stay crisp at any scale.

**Don't**
- Add gradients, blur, glow halos, drop shadows, or a second accent color.
- Use rounded corners, soft cards, or anti-aliased icons.
- Use platform/mobile emoji or typed unicode symbols for UI — use pixel sprites or SVG icons instead.
- Mix in a sans-serif body font — it breaks the TTY illusion.
- Over-animate. The aesthetic is static-with-a-pulse, not motion-heavy.