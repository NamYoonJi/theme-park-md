# playful-blocks.md

> Theme: light canvas, saturated multi-color chips and cards, chunky 3D-lip buttons, springy motion — serious product, playful body.
> Use case: collaboration tools, education products, community platforms, onboarding-heavy apps.
> Icons: Lucide (ISC), stroke 2px, rounded joins. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Playful means physical | Buttons have depth (bottom lip) and press down; cards lift; nothing fades limply |
| 2 | Color in blocks, not washes | Saturated hues live in chips, card headers, and full-bleed bands — never page-wide tints |
| 3 | Chunky and rounded | 16px card radius, 2px borders, 999px pills; thick strokes everywhere |
| 4 | One dark anchor | A deep-plum section (footer or CTA band) grounds the colorful page |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Page |
| `--ink` | #21232C | Text |
| `--ink-soft` | #5E6066 | Secondary |
| `--border` | #E4E2E8 | 2px card borders |
| `--deep` | #332354 | Dark anchor sections, primary buttons (deliberately offset deep plum — do not shift toward red-purple) |
| `--tint` | #F6F0FF | Light section bands, chip backgrounds |

Play set (chips, tags, card accents — assign in order, 2px-border friendly):
`#2BB59A` teal · `#F2616B` coral · `#F7B731` gold · `#3FB6E8` sky

Each play color pairs with a 12%-alpha tint of itself for fills. Never use all four inside one component.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Bricolage Grotesque (SIL OFL) | clamp(40px, 6vw, 72px) / 800 / -0.02em / 1.05 |
| Section head | Bricolage Grotesque | 32px / 700 |
| Body | Inter (SIL OFL) | 16px / 1.6 |
| UI / buttons | Inter | 15px / 700 |
| Tags, stats | Inter | 13px / 600, uppercase 0.04em |

Scale: 13 / 15 / 16 / 20 / 24 / 32 / 48 / 72.

## 4. Layout

- Container 1200px, 24px side padding; section padding 96px
- Hero: left-aligned headline + subcopy + button pair; right side a 2px-bordered product card collage with floating color chips
- Feature rows: alternating text/visual, 2-column 50/50, 64px gap
- Full-bleed bands: `--tint` (light) and `--deep` (dark) sections break the white; max one dark band per page
- Card grid: 3 columns, 24px gap
- Footer: `--deep` bg, white text, pill link chips

## 5. Radius Scale (fixed — never freehand)

| Token | Value | Used on |
|---|---|---|
| sm | 8px | Inputs, small chips |
| md | 12px | Inner panels, images |
| lg | 16px | Cards, modals |
| pill | 999px | Buttons, tags, nav pills |

## 6. Components

| Component | Spec |
|---|---|
| Primary button (3D lip) | `--deep` bg, white text, radius 16px, height 50px; `box-shadow: 0 4px 0` darkened `--deep` (#241941); active: translateY(4px) + shadow 0 |
| Secondary button | White bg, 2px `--border`, radius 16px; same lip in `--border` color |
| Card | White, 2px `--border`, radius 16px, `border-bottom-width: 4px` (resting lip); hover: translateY(-4px), border-color play hue |
| Chip / tag | Play-color 12% tint bg, play-color text, radius 999px, 6px 14px padding, 13px/600 |
| Stat block | Play-color number 48px/800 + 14px label |
| Checklist row | 28px circular check (2px stroke), 16px text, 12px gap |
| Nav | White, 2px bottom border; links as pills on hover (`--tint` fill) |
| Input | 2px `--border`, radius 8px, height 48px; focus: 2px `--deep` border, no glow |

## 7. Motion

| Target | Effect |
|---|---|
| Button press | translateY(4px) + shadow collapse, 0.1s ease-out |
| Card hover | translateY(-4px), 0.2s cubic-bezier(.34,1.56,.64,1) |
| Enter (cards, chips) | scale 0.92→1 + opacity, 0.35s cubic-bezier(.34,1.56,.64,1), 60ms stagger |
| Floating chips (hero) | translateY ±6px loop, 4s ease-in-out, desynced |
| Reduced motion | Lifts/springs off; opacity only; floats static |

## 8. Don't

- No gradients — every color is flat
- No shadows except the button/card lip (no blur shadows anywhere)
- Play colors never on body text or full sections; `--deep` is the only dark surface
- No radius below 8px; no sharp corners
- Don't combine more than 2 play colors in one viewport region
- Nothing mascot-like, no character illustration, no hand-drawn squiggles


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#FFFFFF; --ink:#21232C; --ink-soft:#5E6066; --border:#E4E2E8;
  --deep:#332354; --tint:#F6F0FF;
  --play-teal:#2BB59A; --play-coral:#F2616B; --play-gold:#F7B731; --play-sky:#3FB6E8;
  --radius-sm:8px; --radius-md:12px; --radius-lg:16px; --radius-pill:999px;
  --font-display:"Bricolage Grotesque",sans-serif; --font-body:"Inter",system-ui,sans-serif;
}
```
