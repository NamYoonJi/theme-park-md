# calm-pastel.md

> Theme: warm paper canvas, super-rounded pastel surfaces, breathing motion — softness as a system.
> Use case: wellness products, journaling apps, healthcare, slow-living brands.
> Icons: Lucide (ISC), stroke 1.5px, rounded. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Round to the point of soft | 32px cards, pill buttons, circle media masks — radius is the identity |
| 2 | Warm, not white | Canvas and inks are warm-shifted; pure #FFF appears only inside cards |
| 3 | Pastel fields, one firm accent | Large desaturated color fields; a single saturated blue for every action |
| 4 | Motion breathes | Slow scale/translate loops (4-8s); nothing snaps or bounces |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #F9F4F2 | Page (warm paper) |
| `--card` | #FFFFFF | Cards |
| `--ink` | #2D2C2B | Headings (warm near-black) |
| `--ink-body` | #44423F | Body |
| `--ink-soft` | #8A8580 | Captions |
| `--accent` | #2D52CC | All actions: buttons, links, focus (deliberately offset blue — do not shift toward electric blue) |
| `--accent-warm` | #E8A23D | Small highlights: active dots, stars, streaks |

Pastel fields (section bands, large shapes, card mats):
`#E2DED9` sand · `#D9E4EF` mist · `#F3DDE2` blush · `#EAE4F4` lilac

Fields are backgrounds only — text on fields stays `--ink`/`--ink-body`. Max 2 fields per viewport.

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Bricolage Grotesque (SIL OFL) | clamp(36px, 5vw, 64px) / 600 / -0.01em / 1.1 — never heavier than 600 |
| Section head | Bricolage Grotesque | 28px / 600 |
| Body | Inter (SIL OFL) | 17px / 1.7 |
| UI | Inter | 15px / 500 |
| Overline | Inter | 13px / 600 / uppercase 0.08em / `--ink-soft` |

Scale: 13 / 15 / 17 / 20 / 28 / 40 / 64. Sentence case everywhere; no all-caps headlines.

## 4. Layout

- Container 1140px; section padding 120px (air is part of the calm)
- Hero: centered headline + one-line subcopy + single pill CTA; behind it, 2-3 large soft circles/superellipses in pastel fields (pure geometry — no faces, no characters)
- Feature cards: 3-column grid, 24px gap; generous 32px card padding
- Band sections: full-bleed pastel field with 7rem-radius inner card or circle media mask
- Media masks: circles and 32px-radius rounded rects only
- Footer: sand field, soft links, no dark section anywhere

## 5. Radius Scale (fixed — never freehand)

| Token | Value | Used on |
|---|---|---|
| sm | 8px | Inputs, small chips |
| md | 16px | Inner panels |
| lg | 24px | Media, modals |
| xl | 32px | Cards, bands (the default feel) |
| pill | 112px | Buttons, hero capsules, stat pills |

## 6. Components

| Component | Spec |
|---|---|
| Primary button | `--accent` bg, white text, pill radius, height 56px, 24px side padding, 15px/600 |
| Ghost button | Transparent, 1.5px `--ink` border, pill; hover: `--ink` fill, `--bg` text |
| Card | `--card` bg, radius 32px, no border; shadow only on hover: 0 12px 32px rgba(45,44,43,.08) |
| Stat pill | Pastel field bg, radius pill, 24px padding; mono-free — numbers in Bricolage 40px/600 |
| Progress ring | 4px stroke circle, `--accent` arc on `--bg` track; center number 20px |
| Streak dots | 12px circles row; filled `--accent-warm`, empty 1.5px `--ink-soft` outline |
| Quote block | 28px/1.5 Bricolage 500 on a pastel field, 32px radius |
| Input | `--card` bg, no border, radius 16px, height 52px; focus: 2px `--accent` ring |

## 7. Motion

| Target | Effect |
|---|---|
| Breathing shapes | scale 1→1.04→1, 6-8s ease-in-out infinite, desynced per shape |
| Enter | opacity + 12px translateY, 0.6s ease-out, 100ms stagger |
| Hover (cards) | shadow fade-in + translateY(-2px), 0.3s ease |
| Progress ring | stroke-dashoffset sweep 1s ease-in-out, once on reveal |
| Reduced motion | Breathing off; enters become opacity 0.3s |

## 8. Don't

- No pure-black text, no cold grays — every neutral is warm-shifted
- No borders on cards; separation comes from warmth contrast and radius
- No bounce/spring easings; nothing faster than 0.3s
- No dark sections, no gradients, no glassmorphism
- Pastel fields never carry saturated text or icons — accents live on `--card`/`--bg` only
- No mascots, faces, blob characters, or illustration-style artwork — geometry only


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#F9F4F2; --card:#FFFFFF; --ink:#2D2C2B; --ink-body:#44423F; --ink-soft:#8A8580;
  --accent:#2D52CC; --accent-warm:#E8A23D;
  --field-sand:#E2DED9; --field-mist:#D9E4EF; --field-blush:#F3DDE2; --field-lilac:#EAE4F4;
  --radius-sm:8px; --radius-md:16px; --radius-lg:24px; --radius-xl:32px; --radius-pill:112px;
  --font-display:"Bricolage Grotesque",sans-serif; --font-body:"Inter",system-ui,sans-serif;
}
```
