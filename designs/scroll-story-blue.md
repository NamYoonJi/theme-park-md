# scroll-story-blue.md

> Theme: mobile-first, full-screen scroll storytelling with plain language and a single blue accent.
> Use case: Korean-language consumer app landing.
> Icons: Lucide (ISC), stroke 1.5px. No platform/mobile emoji — use SVG icons instead; no 3D icon styles, line SVG only.

## 1. Principles

| # | Principle | Implementation |
|---|---|---|
| 1 | One screen, one message | Each full-screen section carries one headline + one visual |
| 2 | Scroll storytelling | Fade + slide on section entry; features ordered as a narrative |
| 3 | Plain language | Conversational copy instead of jargon; headlines within ~12 characters (KR) |
| 4 | Phone mockup centric | ~80% of visuals are app screens inside a device frame |

## 2. Color Tokens

| Token | Hex | Usage |
|---|---|---|
| `--bg` | #FFFFFF | Default |
| `--bg-section` | #F2F4F6 | Alternating sections |
| `--bg-dark` | #17171C | 1-2 impact sections |
| `--text` | #191F28 | Headlines |
| `--text-sub` | #4E5968 | Body |
| `--accent` | #3182F6 | CTA, graphs (common-hue blue) |
| `--increase` | #F04452 | Increase: red |
| `--decrease` | #3182F6 | Decrease: blue |

## 3. Typography

| Role | Font | Spec |
|---|---|---|
| Display | Pretendard (SIL OFL) | 48-60px / weight 700 / -0.02em / manual line breaks |
| Body | Pretendard | 17px / 1.6 / weight 400 |
| Numbers | Pretendard | tabular-nums required (numeric displays) |
| Caption | Pretendard | 13px / `--text-sub` |

Scale: 13 / 15 / 17 / 22 / 32 / 48 / 60
Numeric format: `1,234,567` with unit attached — never split the unit from the number.

## 4. Layout

- Mobile-first: content width 100% (max 480px); desktop centers at 720px
- Full-screen sections: min-height 100vh, vertically centered
- Fixed order per section: headline -> subcopy -> mockup, left-aligned
- Section spacing: 160px desktop / 100px mobile

## 5. Components

| Component | Spec |
|---|---|
| CTA | Full-width (mobile), `--accent` bg, radius 12px, height 56px, weight 600 |
| Phone mock | Radius-36px frame, shadow 0 32px 64px rgba(0,0,0,.12) |
| Number counter | Counts 0 -> target over 1s on scroll entry |
| List row | Left Lucide icon 24px + title/description + right `chevron-right`, height 64px |
| Graph | Single-color line chart in `--accent`, 8%-opacity area fill |
| FAQ | Toggles with border-bottom dividers |

## 6. Motion

| Target | Effect |
|---|---|
| Section enter | opacity 0->1 + translateY 30px->0, 0.7s cubic-bezier(.2,.8,.2,1) |
| Element stagger | Headline -> sub -> mockup at 0.1s intervals |
| Inside phone mock | Auto-playing 3-step demo loop |
| CTA press | scale 0.98 press feedback |

## 7. Don't

- No 3D graphics, characters, or illustration styles borrowed from existing products
- No jargon in headlines (use everyday equivalents)
- Never scale the mobile layout up on desktop — mockups keep fixed width
