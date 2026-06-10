# violet-phosphor — Bitmap Terminal Design System (TTY Edition)

A nerdy, geeky, violet-phosphor CRT aesthetic. The page does not just *look* like a
terminal — it *behaves* like one: boot logs, a live system monitor, a process table,
a streaming log, and a real interactive shell. Everything is angular, pixelated, and
deliberately un-smoothed, glowing at "380nm".

This is the violet variant of the base `phosphor` system. The only palette difference is
the `:root` token block; all layout, type, and motion rules are shared. A green, amber,
or cyan tube can be produced the same way by swapping four tokens.

---

## 1. Design Principles

- **No edge smoothing.** All raster art uses `image-rendering: pixelated`. Pixel sprites
  are drawn block-by-block on `<canvas>` with hard square pixels (no anti-aliasing).
- **Everything is angular.** `border-radius: 0` everywhere. No rounded corners, no soft shadows.
- **Single accent, near-black canvas.** One violet family on a violet-tinted black. Glow
  comes from the color plus one subtle `text-shadow` on the logo only — never from blur.
- **Terminal as behavior, not decoration.** Prompts, monospace, blinking cursors, ASCII
  bars and box-frames, command history, and live-updating panels make the page a working TTY.
- **Structure encodes content.** Numbered cards and tables are used only for real
  enumerations. Dashed dividers and 1px grid gaps separate sections like ruled paper.

---

## 2. Color Tokens

```css
:root{
  --violet:      #c77dff;  /* primary text, active state, accents, bar fill   */
  --dark-violet: #9d4edd;  /* secondary / muted body text, command echoes     */
  --dim-violet:  #3c096c;  /* borders, dividers, inactive labels, empty bars  */
  --black:       #08000f;  /* page + surface background (violet-tinted black) */
}
```

- `--violet` — anything live or important: logo, hovered state, active line, filled bar cells.
- `--dark-violet` — body copy, descriptions, terminal output, table cells.
- `--dim-violet` — 1px borders, grid lines, window-bar fills, placeholder/empty bar cells.
- `--black` — the only background. Surfaces are distinguished by 1px violet borders, not fills.

No white, no gray, no second hue. To retheme: replace only these four values.
Reference tubes — green `#00ff41 / #00aa2b / #004d15 / #000000`, amber `#ffb000 / ...`.

---

## 3. Typography

Both faces are open-source (Google Fonts).

| Role             | Font                | Usage                                                    |
|------------------|---------------------|----------------------------------------------------------|
| Display / chrome | **Doto** (wght 900) | ASCII logo support, section labels, window-bar titles, status bar |
| Body / data      | **Share Tech Mono** | All body text, boot log, terminal, tables, monitor bars  |

```html
<link href="https://fonts.googleapis.com/css2?family=Doto:wght@100..900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
```

### Type scale
- ASCII logo: `11px`, `line-height: 1.1`, monospace, `white-space: pre`
- Section label: `11px`, `letter-spacing: 4px`, uppercase, Doto 900, wrapped `[ LABEL ]`
- Hero subtitle: `13px`, Doto-adjacent, wrapped `-- subtitle --`
- Body / terminal / tables / monitor: `12–13px`, `line-height: 1.8–2`, Share Tech Mono
- Window-bar title: `10px`, `letter-spacing: 2px`, Doto 900
- Status bar / hints: `10px`, `letter-spacing: 1–2px`

---

## 4. Layout

- Max content width `1200px`, centered, `24px` side padding.
- **Section rhythm:** each `.section` is `40px` vertical padding with a `1px solid --dim-violet`
  bottom border.
- **1px-gap grids over a violet background** so cell edges read as hairline rules:
  `gap: 1px; background: var(--dim-violet);` with each cell `background: var(--black);`.
- **Hero** is a two-column grid (ASCII logo + copy left, live monitor right), collapsing to
  one column under 700px (ASCII logo shrinks to `7px`).
- **Two-pane rows** (tree + log feed; any side-by-side panels) use the same 1px-gap pattern.

---

## 5. Signature Elements

### 5.1 ASCII Window Frame (`.win`)
Every panel is wrapped in a frame with a title bar:
- `.win` — `1px solid --dim-violet` container.
- `.win-bar` — `--dim-violet` fill, Doto 900, holds a left title (`$ command` or app name)
  and a right meta slot (uptime, `80x24`, dot indicators `▣ ▣ ▣`).
- `.win-body` — `14px 16px` padding (set to `0` for full-bleed tables).

### 5.2 Boot Sequence (`.boot`)
On load, lines append every ~180ms: `[ OK ] <message>`. `[ OK ]` is `--violet`, the message
is `--dark-violet`, parenthetical/disabled notes are `--dim-violet`. Ends with a
`login:` line plus a blinking cursor. Minimum height reserved so layout doesn't jump.

### 5.3 Live System Monitor (htop-style)
Rows of `label | bar | percent`. Bars are pure text: `[` + `|`×filled (`--violet`) +
`.`×empty (`--dim-violet`) + `]`, computed over a 24-cell width. Values jitter around a
base every ~1.4s via a `jitter(base)` helper clamped to 2–99%. Channels can be real
(CPU0/CPU1/MEM/SWAP) or thematic (e.g. PURR pinned high).

### 5.4 Process Table (`.ptable`)
`top`-style: columns PID / USER / %CPU / %MEM / TIME / COMMAND. Header in Doto/`--dim-violet`,
PID in `--violet`, cells in `--dark-violet`, row hover inverts to `--dim-violet` fill. A few
`%CPU` cells update live alongside the monitor.

### 5.5 Streaming Log (`tail -f`)
A feed that appends a timestamped line (`HH:MM:SS message`) every ~1.9s and trims to the last
~8 lines. Timestamp `--dark-violet`, message `--violet`. Title bar shows `$ tail -f <file>`
plus a blinking cursor.

### 5.6 Interactive Shell (`tty0`)
A real command line, not a canned responder:
- Typed commands accumulate above the prompt (echoed as `$ cmd`, then output lines).
- **Command map** keyed by lowercased input: `help, ls, ls -la, cat <file>, ps, top,
  neofetch, theme, echo <x>, date, sudo, pwd, uname -a, whoami, clear`.
- **History:** `↑/↓` walk a `history[]` array.
- **Autocomplete:** `Tab` completes against the command list (prefix match).
- **Unknown input:** `bash: <cmd>: command not found. type "help"`.
- Hint line below: `[TAB autocomplete] [↑/↓ history] [type help]`.

### 5.7 Pixel-art Canvas Sprite
A bitmap drawn on `<canvas>` from a 2D 0/1 array, scaled ×5, no smoothing. Background filled
with `--black`, pixels with `--violet`; eyes/cutouts re-filled with `--black`. Swap the array
to change the subject.

### 5.8 Scanlines
Fixed full-screen overlay, `pointer-events: none`:
```css
background: repeating-linear-gradient(0deg, transparent 0 2px, rgba(0,0,0,.04) 2px 4px);
```

### 5.9 Status Bar
Bottom-pinned `--dim-violet` bar, two segments. Left: version + live `load 0.42 0.31 0.19`.
Right: live clock + `STATUS`. Window bars may also carry a live `up H:MM:SS` uptime counter.

### 5.10 Dashed Dividers
`repeating-linear-gradient(90deg, --dim-violet 0 4px, transparent 4px 8px)` as a 1px rule.

---

## 5.5b Iconography

**No emoji. No icon fonts.** Never use emoji glyphs (🐈, ✅, 🔥, etc.) or webfont icon sets
(Font Awesome, Material Icons, Lucide-as-font, etc.). Emoji render with their own colored,
anti-aliased, rounded shapes and icon fonts hint/smooth their edges — both break the flat,
angular, single-accent CRT look instantly.

**Use inline SVG, drawn in a bitmap / pixel style.** Icons must look like they were plotted
on the same grid as the rest of the system:

- **Grid-snapped geometry.** Build every icon on a coarse integer grid (e.g. a 16×16 or
  10×10 `viewBox`) so each segment lands on a whole-pixel coordinate. No sub-pixel points.
- **Orthogonal only.** Horizontal and vertical strokes, plus hard 45° diagonals stepped as
  pixels when needed. No bezier curves, no smooth arcs — approximate circles as octagons or
  stepped blocks.
- **Hard edges.** `shape-rendering="crispEdges"` on the `<svg>`. No `border-radius`, no
  rounded `stroke-linejoin`/`stroke-linecap` (use `miter` / `butt`), no blur, no gradient fill.
- **Monochrome, token-driven.** Fill/stroke with `currentColor` so the icon inherits
  `--violet` / `--dark-violet` / `--dim-violet` from context and follows hover states. One
  color per icon; no multi-tone.
- **Pixel weight.** Strokes are a whole number of grid units (commonly 1–2 units), uniform
  across the icon, matching the 1px hairline rules elsewhere.
- **Match the sprite resolution.** Treat icons as small siblings of the `<canvas>` pixel
  sprites (§5.7): same blocky vocabulary, just authored as SVG paths/rects instead of a
  drawn bitmap.

Acceptable terminal glyphs (block/box-drawing characters like `█ ▀ ▄ ▣ ◆ ─ │ ├ └`) are *not*
emoji and may be used freely for frames, bullets, and indicators — they are part of the TTY
character set, not a colored icon font.

```html
<!-- example: a blocky "folder" icon, grid-snapped, currentColor, crisp edges -->
<svg viewBox="0 0 16 16" width="14" height="14" shape-rendering="crispEdges"
     fill="none" stroke="currentColor" stroke-width="1" stroke-linejoin="miter">
  <rect x="1" y="4" width="14" height="9"/>
  <rect x="1" y="2" width="6"  height="2"/>
</svg>
```

---

## 6. Interaction & Motion

- **Blinking cursor** (`.cur`): 9×15px `--violet` block, `@keyframes blink` step-end 1s.
  Used in nav, login line, log/tail bars, and beside the shell input.
- **Hover:** links/labels and PIDs go `--dim-violet → --violet`; table rows and cards
  invert to a `--dim-violet` fill. Transitions are fast (`0.05s`) or instant.
- **Live timers:** boot (~180ms step), monitor (~1.4s), log feed (~1.9s), clock/uptime/load (1s).
- **No smooth scrolling, no parallax, no fade-up-on-scroll.** Motion is the cursor blink,
  the appending logs, the jittering bars, and the clock — a TTY pulse, not page animation.
- Honor `prefers-reduced-motion` by freezing the cursor blink and slowing/stopping feeds.

---

## 7. Do / Don't

**Do**
- Keep all corners square and the palette to the four violet tokens on near-black.
- Wrap panels in `.win` frames with a `$ command` or app-name title.
- Make panels behave: jittering bars, streaming logs, a shell that actually parses input.
- Use Doto sparingly (chrome only); Share Tech Mono for everything readable.
- Draw icons as inline SVG on an integer grid — orthogonal strokes, `crispEdges`,
  `currentColor`, no curves. Block/box-drawing glyphs are fine as TTY characters.

**Don't**
- Add gradients, blur, glow halos, drop shadows, or a second accent color.
- Use rounded corners, soft cards, or anti-aliased icons.
- Use emoji or icon fonts (Font Awesome, Material, etc.) — they smooth/round and add color.
- Fake the terminal with a static image — wire up history, Tab, and `command not found`.
- Mix in a sans-serif body font — it breaks the TTY illusion.
- Over-animate. The aesthetic is static-with-a-pulse, not motion-heavy.

---

## 8. Theme Variants

Only the `:root` block changes between tubes; everything in sections 3–7 is shared.

| Variant | --accent  | --dark    | --dim     | --black   |
|---------|-----------|-----------|-----------|-----------|
| green   | `#00ff41` | `#00aa2b` | `#004d15` | `#000000` |
| violet  | `#c77dff` | `#9d4edd` | `#3c096c` | `#08000f` |
| amber   | `#ffb000` | `#cc8500` | `#4a2e00` | `#0f0700` |
| cyan    | `#00e5ff` | `#00a3b8` | `#054652` | `#000a0c` |