# Design Spec — "Offset Mono" (Editorial Webpage Style)

A single continuous webpage system — not a slide deck. Monochrome editorial look: stepped black headline blocks, pale gray canvas, white content bands, hairline structure, one burnt-persimmon accent reserved for data and emphasis.

---

## 1. Identity

| Item | Value |
|---|---|
| Codename | Offset Mono |
| Artifact type | Continuous scrolling webpage (one HTML document, normal sections) |
| Mood | Editorial, precise, quietly confident |
| Use cases | Brand/agency site, studio profile, consulting landing page |

Explicit non-goals: no slide cards, no page numbers, no per-section drop shadows, no deck collage. Content flows as one page.

---

## 2. Color Tokens

Accent is deliberately offset from pure coral-orange: deeper, slightly burnt persimmon.

```css
:root {
  --canvas:      #EDEDEF;  /* page background, cool pale gray */
  --band:        #FFFFFF;  /* alternating white content bands */
  --ink:         #111113;  /* black blocks, headings, primary text */
  --ink-soft:    #55555A;  /* body copy */
  --ink-faint:   #9A9AA0;  /* captions, meta, sources */
  --line:        #DDDDE1;  /* hairline rules and borders */
  --accent:      #E2603A;  /* burnt persimmon — key numbers, active states, one chart series */
  --accent-soft: #F6DED4;  /* accent tint — tag fills, chart area fills */
  --neutral-bar: #D2D2D6;  /* baseline series in comparisons */
}
```

Rules:
- **Global geometry — zero radius.** `border-radius: 0` on every box: sections, panels, cards, bars, chips, tabs, tags, buttons, inputs, images, avatars. No rounded corners anywhere in the UI. Exemptions: chart dot markers (circles) and the internal stroke geometry of line-style SVG icons (round caps/joins per icon set).
- Black is the brand color; accent appears in at most 2 elements per viewport.
- Accent never used for body text or backgrounds of large areas; flat fills only, no gradients on accent.
- Canvas may carry one faint diagonal light streak (gradient, opacity ≤ 0.05, fixed attachment).

---

## 3. Typography

| Role | Face | Weight / size | Notes |
|---|---|---|---|
| Display (stepped blocks, section openers) | Archivo | 800, clamp(38px, 6.5vw, 88px) | -0.02em tracking, white on black blocks |
| Section heading | Inter Tight | 700, clamp(24px, 3vw, 34px) | `--ink` |
| Body | Inter | 400, 15–16px / 1.7 | `--ink-soft`, max-width 64ch |
| Caption / meta / eyebrow | Inter | 500–600, 12–13px | `--ink-faint`; eyebrows uppercase, 0.14em tracking |
| Numeric emphasis | Archivo | 700–800, 20–48px | Key figures may use `--accent` |

---

## 4. Signature Element — Stepped Block Headline

The one memorable device, used exactly twice per page (hero + final CTA). A multi-line display headline where each line sits in its own solid-black rectangle, offset horizontally like stacked bricks.

```
┌──────────────┐
│ STUDIO NAME  │
└──────┬───────┴────────┐
       │  SPACE INTO    │
       └──┬─────────────┴──────────┐
          │  CONTENT & BUSINESS    │
          └────────────────────────┘
```

Spec:
- Each line: `display:table; background:var(--ink); color:#fff; padding:0.08em 0.32em;`
- Line N indented `(N-1) × 7%` of container width (4% on mobile).
- Lines overlap vertically by ~4px (negative top margin) so edges read as one stair-stepped mass.
- A 56–64px line-style SVG mark (house/tower glyph) sits at the top-right shoulder of the stack.
- On load: line-by-line `clip-path` wipe reveal, 120ms stagger. Section headings elsewhere are plain black text — the block treatment stays exclusive to these two moments.

---

## 5. Page Structure (single scroll)

Single column, max-width 1120px, 24px side padding. Sections are full-width background bands alternating `--canvas` / `--band` / one `--ink` band; content inside aligns to the same grid. Section separation = background change + generous spacing (120–160px desktop, 64px mobile) — never borders-as-frames or card shadows.

```
[Sticky header]  logo glyph + wordmark | nav: Services · Process · Market · Work · Contact
[Hero]           canvas band — stepped block headline, subtitle, interpunct tagline
[Statement]      ink band — large white statement, accent-underlined key phrase, founder row
[Services]       band — 4-up grid, top-border cards (borders, not shadows)
[Process]        canvas band — vertical numbered flow + inline comparison bar chart
[Market]         band — two mini line-chart figures side by side, prose between
[Work / Refs]    canvas band — hairline reference table + inline stat figures
[CTA]            band — second (smaller) stepped block headline + contact link
[Footer]         ink band — glyph, disclaimer line, mono meta
```

Sticky header: `--canvas` at 90% opacity + blur, bottom hairline; active nav item gets a 2px `--accent` underline.

---

## 6. Components

### 6.1 Eyebrow + Heading pattern
Every section opens with: uppercase eyebrow (`--ink-faint`) → heading (`--ink`) → one-sentence lede (`--ink-soft`, max 64ch). No decorative rules above headings.

### 6.2 Black Header Bar (MANDATORY for tables & list panels)
Every table, process list, or grouped-list panel MUST open with a full-width solid-black title bar:
- `background: var(--ink); color: #fff;` centered label, Inter Tight 600, 13–14px, 0.04em tracking, 12px vertical padding, square corners.
- The bar spans the exact width of the table/list it titles; content below sits on white with hairline row dividers.
- Never replace it with a plain heading, eyebrow, or colored bar — this bar is the canonical title treatment for tabular/grouped content.

### 6.3 Numbered Process Flow
- Lives under a Black Header Bar (e.g. `One-stop Process`).
- Each step = 18×18px solid-black square chip (white numeral, no radius) + bold title + 2-line description.
- Step titles may embed arrow sequences in text: `Plan → Execute → Distribute → Educate`.
- Generous row spacing (28–36px) between steps; optional hairline dividers.
- Numbering is allowed here only because the content is a true sequence.

### 6.4 Black Tab Label (MANDATORY for every chart figure)
Every chart `<figure>` MUST carry a small black tab as its title, anchored top-left of the figure:
- `display:inline-block; background: var(--ink); color:#fff;` 12px Inter 600, ~6px × 12px padding, square corners.
- Never use a plain text caption, eyebrow, or accent-colored label as a chart title.

### 6.5 Comparison Bar Figure (inline, not a card)
- Titled by a Black Tab Label (6.4). Two bars: `--neutral-bar` baseline vs `--accent` target, value labels in Archivo 700 above (accent bar label in accent, `+α` suffix allowed).
- Axis-free; year labels under bars; `* Source:` caption in `--ink-faint`.
- Bars grow from baseline on scroll-into-view (600ms, once).

### 6.6 Line Chart Figure
- Titled by a Black Tab Label (6.4). Inline SVG, viewBox-based, no chart library.
- MANDATORY data treatment: every data point gets a dot marker (filled or white-filled with stroke ring) AND a numeric value label directly above it (Archivo 700, 11px). No unlabeled lines.
- Primary series `--ink`; secondary `--accent`; tertiary `--neutral-bar`. Horizontal hairline gridlines (`--line`) allowed; no vertical gridlines, no axis box.
- X-axis labels (years) in `--ink-faint` 10–11px below the plot.
- Figcaption sits on a `#F5F5F7` strip, 12.5px.

### 6.7 Service Cards
- 4-up grid (2-up tablet, 1-up mobile): white, `1px solid var(--line)` with `border-top: 2px solid var(--ink)`.
- Title 14.5px Inter Tight 700; one-line muted descriptor; 24px line-style SVG icon (stroke 1.5, currentColor) bottom-left.
- Hover: top border switches to `--accent`, icon translates up 2px. No shadow, no lift.

### 6.8 Reference Table
- Opens with a Black Header Bar (6.2), e.g. `Domestic Lectures`.
- Two-column: category label (bold, `--ink`) | rows with hairline dividers.

### 6.9 Stat Figures
- Inline, not floating chips: oversized Archivo number (`1,500+` in `--ink`, `98%` in `--accent`) with a small label beneath; placed in a row beside or under the reference table.

### 6.10 Tags
- Square-corner tags: `--accent-soft` background, `--ink` 12px text, used sparingly for service categories.

---

## 7. Iconography

- Line-style open-source SVG only (Lucide / Tabler, MIT). Stroke 1.5–1.75, round caps/joins, `currentColor`.
- Allowed set: home, mic, globe, building, camera, presentation, bar-chart, arrow-right, arrow-up-right.
- No emoji anywhere — copy, labels, alt text, loading states included.

---

## 8. Motion

- Hero stepped blocks: clip-path wipe per line, 0.55s, 120ms stagger, once on load.
- Sections: 16px rise + fade on scroll-into-view, 500ms `cubic-bezier(0.2, 0.7, 0.2, 1)`, threshold 0.18, once.
- Bar/line figures animate draw/grow on first reveal only.
- Hover micro-interactions ≤ 150ms; no parallax, no continuous ambient motion.
- `prefers-reduced-motion`: all entrances become opacity-only; charts render in final state.

---

## 9. Responsive & Quality Floor

- Breakpoints: 1120px container; grid collapses 4→2→1 at 1024 / 640px; stepped headline indent 7% → 4%; section spacing 160 → 64px.
- Contrast: body text never in accent; accent reserved for large numerals and 2px state indicators.
- Keyboard focus: `outline: 2px solid var(--ink); outline-offset: 2px` on all interactive elements.
- Charts are semantic `<figure>`/`<figcaption>` with `role="img"` and descriptive `aria-label`.
- Sticky header remains usable at 320px width.
