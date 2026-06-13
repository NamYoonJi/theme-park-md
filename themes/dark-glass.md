# dark-glass.md

> Theme: near-black canvas, frosted-glass surfaces, hairline highlights, one violet light-source — speed and precision rendered as translucency.
> Use case: developer tools, productivity apps, keyboard-driven products.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | Depth through light, not borders | Surfaces separate via backdrop blur + inset top highlights, not heavy outlines |
| 2 | Keyboard-first identity | Keycaps, command rows, and mono metadata are first-class visuals |
| 3 | One light source | A single violet glow zone behind the hero; everything else near-black |
| 4 | Measured restraint | Tight 4px-based scales; nothing freehand |

## 2. Color Tokens

| Token | Value | Usage |
|---|---|---|
| `--bg` | #07080A | Page canvas |
| `--bg-100` | #101111 | Raised section |
| `--bg-200` | #181A1A | Card base under glass |
| `--bg-300` | #313133 | Pressed / active |
| `--fg` | #F4F4F6 | Headings |
| `--fg-200` | #C2C7CA | Body |
| `--fg-300` | #78787C | Secondary |
| `--fg-400` | #5E6366 | Meta, placeholders |
| `--border` | hsl(195,5%,15%) | Hairline borders |
| `--accent` | #58AEFF | Links, focus, active keycap |
| `--glow` | #7B5BD6 | Hero light curtain only (violet, deliberately offset from any brand hue) |
| `--button-bg` | rgba(255,255,255,.815) | Primary button fill |
| `--button-fg` | #181A1A | Primary button text |

Accent tints: any accent at 15% alpha for chips/badges (`rgba(88,174,255,.15)`).

## 3. Glass Recipe (the identity — apply exactly)

| Layer | Spec |
|---|---|
| Nav glass | `backdrop-filter: blur(10px)`; bg `rgba(16,17,17,.75)`; 1px `--border` |
| Card glass | `backdrop-filter: blur(20px)`; bg `rgba(24,26,26,.6)` |
| Modal glass | `backdrop-filter: blur(36px)` |
| Top highlight | `inset 0 1px 0 0 rgba(255,255,255,.1)` on every glass surface |
| Floating shadow | `0 4px 40px 8px rgba(0,0,0,.4), 0 0 0 .5px rgba(0,0,0,.8), inset 0 .5px 0 0 rgba(255,255,255,.3)` |
| Ambient glow | `0 0 40px 20px rgba(255,255,255,.03)` on the hero window |

## 4. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Inter (SIL OFL) | clamp(48px, 7vw, 80px) / weight 700 / -0.02em / line-height 1.05; sentence case with trailing period |
| Section head | Inter | 32px / 600 |
| Body | Inter | 16px / 1.6 |
| UI | Inter | 13-14px / 500 |
| Meta / data | JetBrains Mono (SIL OFL) | 12-13px; pipe-separated runs: `v1.0.4  |  ready  |  3 sources` |

Scale: 11 / 12 / 13 / 14 / 16 / 18 / 20 / 24 / 32 / display.

## 5. Layout

- Containers: 746px (text), 1064px (cards), 1204px (default); grid gap 32px (24px under 768px)
- Floating nav bar: height 58px, detached from top by 16px, radius 16px, glass recipe
- Hero: centered, two-line display headline over the violet glow; primary + secondary buttons side by side; mono metadata line beneath
- Spacing scale (4px base): 4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 56 / 64 / 80 / 96 / 112 / 168
- Section padding: 96-112px vertical

## 6. Radius Scale (fixed — never freehand)

| Token | Value | Used on |
|---|---|---|
| xs | 4px | Keycaps, small chips |
| sm | 6px | Buttons, inputs, badges |
| md | 12px | Cards, list rows |
| lg | 16px | Nav bar, large panels |
| xl | 20px | Hero window |
| full | 999px | Pills |

## 7. Components

| Component | Spec |
|---|---|
| Primary button | `--button-bg` fill, `--button-fg` text, radius 6px, height 40px, 14px/500 |
| Secondary button | transparent, 1px `--border`, `--fg-200` text; hover bg `rgba(255,255,255,.06)` |
| Keycap | 24px square, radius 4px, bg `--bg-300`, `inset 0 1px 1px 0 rgba(255,255,255,.15)`, mono 12px |
| Command row | 44px height, radius 6px, icon + label + right-aligned keycaps; hover bg `rgba(255,255,255,.05)` |
| Hero window | Glass card radius 20px containing a command list; floating shadow + ambient glow |
| Badge | 15%-alpha accent bg, accent text, radius 6px, 12px mono uppercase |
| Divider | 1px `--border`, or fade-out: `linear-gradient(90deg, transparent, var(--border) 15%, var(--border) 65%, transparent)` |

## 8. Motion

| Target | Effect |
|---|---|
| Hover (color/opacity) | 0.3s ease |
| Enter (cards) | opacity + 8px translateY, 0.3s cubic-bezier(.4,0,.22,.96), staggered 60ms |
| Press / toggle | transform 0.15s cubic-bezier(.34,1.56,.64,1) (slight spring) |
| Glow | static; optional 22s opacity drift 0.9→1.0 |
| Reduced motion | all transforms off; opacity only |

## 9. Don't

- No light mode, no white sections
- No opaque cards where glass is specified — translucency is the identity
- No saturated red/orange accents (keep the single blue + violet glow)
- No borders thicker than 1px; depth comes from blur and highlights
- Never put body text directly over the glow without a glass layer between


---

## CSS tokens

Copy-paste starting point - the same values documented above, as CSS custom properties (the prose spec stays the source of truth).

```css
:root{
  --bg:#07080A; --bg-100:#101111; --bg-200:#181A1A; --bg-300:#313133;
  --fg:#F4F4F6; --fg-200:#C2C7CA; --fg-300:#78787C; --fg-400:#5E6366;
  --border:hsl(195,5%,15%); --accent:#58AEFF; --glow:#7B5BD6;
  --button-bg:rgba(255,255,255,.815); --button-fg:#181A1A;
  --radius-xs:4px; --radius-sm:6px; --radius-md:12px; --radius-lg:16px; --radius-xl:20px; --radius-full:999px;
  --font-sans:"Inter",system-ui,sans-serif; --font-mono:"JetBrains Mono",monospace;
}
```
