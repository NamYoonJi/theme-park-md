# ascii-portfolio.md

> Theme: black canvas, white dot-matrix display type, a dithered ASCII portrait, keyboard-navigated sections — a terminal-art personal site.
> Use case: developer/creative portfolios, single-person sites, link-in-bio pages.
> Icons: Lucide (ISC), monochrome inline SVG only. No platform/mobile emoji — block/box-drawing glyphs (▓ ░ ■ ↵ →) are allowed as TTY characters.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Type is built from dots | Name and section titles use a dot-matrix display face at large sizes; the dots are the identity |
| 2 | Monochrome, one marker | Pure white-on-black; a single green square is the only accent, used as a status/marker glyph |
| 3 | Keyboard is the interface | A legend of `^X` shortcuts; sections are reachable by key (and tap on touch) |
| 4 | ASCII over imagery | Portraits/visuals are dithered character art, not photos |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #000000 | Page canvas |
| `--fg` | #FFFFFF | Text, dot-matrix display |
| `--dim` | #8A8A8A | Secondary text, `^X` keys, "OVER" connectors |
| `--faint` | #5A5A5A | Decorative ▓ blocks, copyright, disclaimer |
| `--accent` | #2BD964 | Single marker only (■ status square, hover) — never on body text |
| `--line` | #222222 | 1px rules, key-cap borders, section dividers |

Invert mode (the `^I` toggle) swaps to a light tube: `--bg`#FFFFFF · `--fg`#000000 · `--dim`#5A5A5A · `--faint`#9A9A9A · `--line`#CFCFCF (accent unchanged).

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display name | Doto (SIL OFL) | weight 800, clamp(34px, 11.6vw, 128px), line-height .92, letter-spacing .05em |
| Section titles | Doto | weight 500 (airier dots), clamp(30px, 6.2vw, 56px), letter-spacing .07em |
| Body / UI / nav | Share Tech Mono (SIL OFL) | 15px / 1.55 |
| Meta, captions, keys | Share Tech Mono | 13px; key labels 11px |
| ASCII art | Share Tech Mono | 9px / line-height 1.02 (7px on mobile), `white-space: pre` |

Two faces only. Display is always the dot-matrix face; everything readable is the mono face. Headlines are uppercase.

## 4. Layout

- Single column, page padding clamp(16px, 3vw, 40px); no max-width container — content runs edge to edge like a terminal buffer.
- Name spans full width at the top, may wrap across lines.
- Hero: two columns — ASCII portrait (≤420px) left, meta lines right (`/ role`, `/ location`, `/ use your keyboard to navigate ↓`). Stacks under 720px.
- Keyboard legend: 4-column grid of paired shortcuts, framed by 1px `--line` top and bottom rules. Repeated at page foot. → 2 columns under 720px.
- Sections (`biography / projects / services / contact`) separated by 1px `--line` top rules, 64px vertical padding.

## 5. Components

| Component | Spec |
|---|---|
| Display name | Dot-matrix face, full width; non-breaking within words (`&nbsp;`) so dots stay contiguous |
| ASCII portrait | `<pre>` dithered character ramp (` .,:;irsXA…@`), `aria-hidden`; scales by font-size, never an image |
| Key-cap | `^X` in a 1px `--line` box, radius 2px, 11px, `--dim`; turns `--accent` on hover/focus |
| Legend item | key-cap + uppercase label; clickable/tappable (scroll to section or run action) |
| Word grid | Uppercase words on a 4-col grid (2-col mobile); connector words (e.g. "OVER") in `--dim` |
| Project row | `[/> NN]` index + `▓▓▓ TITLE ▓▓▓` + right-aligned `VISIT SITE →`; second line `READ MORE ■ ↵` with the green ■ |
| Service list | `[/> :]` header + staggered-indent rows, each `_ LABEL ↵` |
| Contact footer | Single hairline-topped row: name · email · handle · crew, all mono 13px |
| Invert toggle | `^I` flips the entire palette via a body class, 0.25s color/background crossfade |

## 6. Motion

| Target | Effect |
|---|---|
| Section jump | `scrollIntoView({behavior:'smooth'})` on key/tap |
| Page up/down | `scrollBy` ±0.9 viewport, smooth |
| Invert | background + color crossfade 0.25s linear |
| Hover | color → `--accent` only (no movement) |
| Reduced motion | smooth-scroll and crossfade become instant; nothing else animates |

## 7. Radius Scale (fixed — never freehand)

| Token | Value | Used on |
|---|---|---|
| none | 0 | Everything by default (angular terminal) |
| key | 2px | Key-cap boxes only |

## 8. Don't

- No second accent hue; green is a marker glyph only, never body text or large fills
- No rounded corners beyond the 2px key-caps; no shadows, no gradients, no blur
- No photographic imagery — dithered ASCII only
- No anti-aliased/icon-font glyphs or platform emoji; line SVG or TTY block glyphs only
- Don't bind shortcuts to `Ctrl/Cmd+letter` (clashes with the browser) — listen on bare keys, show `^X` only as a label
- Keep the page keyboard-reachable AND tap-reachable (touch has no keyboard)

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#000000; --fg:#FFFFFF; --dim:#8A8A8A; --faint:#5A5A5A;
  --accent:#2BD964; --line:#222222;
  --radius:0; --radius-key:2px;
  --font-display:"Doto","Share Tech Mono",monospace;
  --font-mono:"Share Tech Mono",ui-monospace,monospace;
}
body.invert{
  --bg:#FFFFFF; --fg:#000000; --dim:#5A5A5A; --faint:#9A9A9A; --line:#CFCFCF;
}
```
