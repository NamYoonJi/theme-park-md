# Midnight UI Design System

## Overview

Midnight UI is a dark-mode, engineering-grade design system built for developer platforms, AI tooling, and technical product sites. It pairs a deep near-black navy canvas with a single cool ice-blue accent, letting generous whitespace and restrained typography carry the weight. There are no loud colors, no heavy ornamentation, and no more than one bright call to action per view. Everything reads as calm, premium, and confident -- the interface gets out of the way so the product can speak. This is technical minimalism as a design language.

---

## Colors

- **Background Base** (#04070E): Page canvas -- a near-black navy, never pure black
- **Background Nav** (#040710): Navigation bar surface, slightly cooler than base
- **Background Elevated** (#0C1019): Buttons, cards, and panels lifted off the canvas
- **Background Card** (#0D1525): Content cards and dashboard surfaces
- **Border** (#1A2030): Dividers and element outlines, used at low opacity
- **Text Primary** (#FFFFFF): Logo and highest-emphasis text
- **Text Heading** (#A8CAFA): Hero headline gradient endpoint (soft periwinkle blue)
- **Text Nav** (#E0E9F8): Navigation links and secondary headings
- **Text Body** (#B6D6FC): Body copy and hero subtext
- **Text Muted** (#667085): Captions, labels, and supporting detail
- **Accent** (#9DC8FF): Primary accent -- icons, glows, emphasis (ice blue)
- **Accent Glow** (#CAEEFF): Lightest highlight, used in radial glows only
- **Success** (#5EDFAA): Positive status (mint green)
- **Warning** (#F5C842): Caution status (warm amber)
- **Info** (#9DC8FF): Informational status (same as accent)

The accent (#9DC8FF) is the only chromatic color permitted at meaningful saturation; everything else lives in the navy-to-white axis.

## Typography

- **Display Font**: Inter
- **Body Font**: Inter
- **Mono Font**: JetBrains Mono

- **h1**: Inter 62-68px regular (400), 1.08 line height, -0.025em tracking
- **h2**: Inter 42-48px regular (400), 1.12 line height, -0.02em tracking
- **h3**: Inter 28-32px medium (500), 1.2 line height, -0.01em tracking
- **h4**: Inter 20-22px medium (500), 1.25 line height
- **body**: Inter 16px regular (400), 1.6 line height
- **body-large**: Inter 18-19px regular (400), 1.65 line height
- **small**: Inter 14px regular (400), 1.5 line height
- **label**: Inter 12px medium (500), 1.4 line height, uppercase, 0.1em tracking
- **mono**: JetBrains Mono 14px regular, 1.5 line height

Headlines use a light-to-accent gradient applied through `background-clip: text` (#FFFFFF to #A8CAFA), centered or left-aligned depending on layout. Weight stays low -- 300 to 500 only -- so the type feels airy rather than heavy.

---

## Spacing

Base unit: 8px. Spacing is generous and breathing-room-first; sections are spaced far apart to let content rest.
- **sp-1**: 8px
- **sp-2**: 12px
- **sp-3**: 16px
- **sp-4**: 24px
- **sp-5**: 32px
- **sp-6**: 48px
- **sp-7**: 80px
- **sp-8**: 100-120px (section vertical padding)

Layout container maxes out at 1240px with 48px side padding, narrowing on smaller viewports.

## Border Radius

- **radius-sm** (6-8px): Buttons, small icon containers
- **radius-md** (10-12px): Cards, dashboards, feature panels
- **radius-lg** (16px): Large feature grids and hero panels
- **radius-pill** (999px): Tags, badges, status chips, lifecycle markers

Corners are softly rounded throughout -- never sharp, never fully circular except for pills and avatars.

## Elevation

Midnight UI uses **no drop shadows**. Hierarchy comes from surface lightness and border contrast: each layer (base to elevated to card) steps slightly lighter, and a 1px low-opacity border separates surfaces. The only "glow" is a soft radial gradient of the accent color behind hero and CTA sections, used as atmosphere, not as a shadow.
- **glow-ambient**: radial-gradient of accent at 6-10% opacity, large and diffuse, behind hero/CTA only.

## Components

### Buttons
#### Primary
white (#F8FFFF) fill, dark navy (#04070E) text, no border, radius-sm. The single highest-contrast element on any view. Hover: opacity 0.88.
#### Secondary / Ghost
transparent fill, light (#E0E9F8) text, 1px border at rgba(255,255,255,0.18), radius-sm. Hover: faint white fill (rgba 255,255,255,0.05), border brightens.
#### Hero Primary
transparent fill, body-blue (#B6D6FC) text, 1px border at rgba(90,140,200,0.5), radius-sm. Hover: accent border + faint accent fill.
#### Hero Secondary
elevated navy (#122138) fill, soft-blue (#A1BFDB) text, 1px (#1E3554) border, radius-sm. Hover: background lightens to #162840.
#### Sizes
Small (9px 20px, 14px), Medium (13px 28px, 15px), Large (14px 32px, 15px).
#### With Icon
Leading Tabler icon at 14-16px, 6-8px gap before the label.
---

### Cards
#### Default
card navy (#0D1525) fill, 1px border at rgba(255,255,255,0.08), radius-md, no shadow. sp-5 (32px) padding. Hover: border brightens to rgba(255,255,255,0.14).
#### Elevated / Featured
card navy fill, 1px brighter border (rgba 255,255,255,0.14), radius-lg. Reserved for the single featured item in a group; may carry a soft accent glow in one corner.
#### Dashboard Card
card navy fill, brighter border, radius-lg, sp-4 padding. Contains a header row, a hero metric, and stacked data rows.
---

### Inputs
elevated navy (#0C1019) fill, light text, 1px border at rgba(255,255,255,0.12), radius-sm. Inter or mono 14-15px. 10-12px padding.
- **Default**: 1px low-opacity border.
- **Hover**: border brightens slightly.
- **Focus**: accent-tinted border, soft focus ring (no harsh outline).
- **Error**: red-tinted border.
- **Disabled**: muted border, reduced text contrast.
#### Label
muted text. Inter 12px medium, uppercase, 0.1em tracking. 4px margin-bottom.
#### Helper Text
muted (default) or red (error) text. Inter 12px regular. 4px margin-top.
---

### Pills / Tags
#### Lifecycle Marker
faint white fill (rgba 255,255,255,0.03), 1px border (rgba 255,255,255,0.1), radius-pill. 7px 16px padding, uppercase, 12px, 0.05em tracking. Pairs a small icon-pill on the left with a label. Used for sequence steps.
#### Status Chip
radius-pill, tinted fill + matching text in one color family. 11px medium. 3px 9px padding.
- **Success**: mint fill (rgba 30,180,100,0.15), mint (#5EDFAA) text.
- **Info**: accent fill (rgba 157,200,255,0.12), accent (#9DC8FF) text.
- **Warning**: amber fill (rgba 255,190,50,0.12), amber (#F5C842) text.
#### Eyebrow Label
no fill, muted text, uppercase, 12px, 0.1em tracking. Sits above section titles.
---

### Icons

All icons come from an open-source outline set rather than emoji or unicode symbols.
- **Library**: Tabler Icons (open source, MIT licensed)
- **CDN**: `https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.19.0/dist/tabler-icons.min.css`
- **Usage**: `<i class="ti ti-{name}">` -- outline weight only, never the `-filled` variants
- **Color**: accent (#9DC8FF) by default; inherits font-size from parent

#### Icon Pill
The standard pattern: an outline icon centered inside a rounded-square tinted container. This is the system's signature icon treatment.
```css
.icon-pill {
  width: 40px; height: 40px;
  border-radius: 10px;
  background: rgba(157, 200, 255, 0.12);
  border: 1px solid rgba(157, 200, 255, 0.18);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.icon-pill i { font-size: 20px; color: #9DC8FF; }

/* Size variants */
.icon-pill.sm { width: 32px; height: 32px; border-radius: 8px; }
.icon-pill.sm i { font-size: 16px; }
.icon-pill.xs { width: 26px; height: 26px; border-radius: 6px; }
.icon-pill.xs i { font-size: 13px; }
```

#### Inline Affordance Icons
Decorative symbols inside text or links must use icons, never typed characters.
- Dropdown caret: `ti-chevron-down` at 11px, opacity 0.6, slight vertical nudge -- replaces the typed `v`/`∨`.
- Link arrow: `ti-arrow-right`, sized to match the link text.
- Checklist bullet: `ti-check` in accent, leading each list item.
- Status dot: a small CSS circle in the success color -- not an emoji.
---

### Navigation
sticky top bar, 56-64px tall, nav-navy (#040710) fill with backdrop blur, 1px bottom border at rgba(255,255,255,0.08). Layout is logo (left) | links (center-left) | CTAs (right).
- Logo: icon-pill + wordmark.
- Links: muted text at ~0.72 opacity, full opacity on hover. Items with a submenu carry a `ti-chevron-down` icon, not a typed caret.
- CTAs: one Primary (white) + one Ghost, right-aligned.
---

### Lists
transparent, Inter 13-16px. 1px bottom divider at rgba(255,255,255,0.08), 10-16px item padding. Used for feature checklists (with `ti-check` bullets) and footer link columns.
- No emoji bullets; icon or em-dash only.
---

### Tooltips / Dropdowns
card navy fill, light text, 1px border, radius-md. Fade in via opacity + small translateY over 200-250ms ease. No hard shadow -- the border and surface lift do the separation.

---

## Motion & Interaction

- **Hero entrance**: staggered fade-up of headline, subtext, buttons, then lifecycle markers, ~600ms ease-out.
- **Marquee**: logo row scrolls infinitely on a linear CSS animation; pauses on hover.
- **Button hover**: opacity drop (Primary) or background/border lightening (Ghost).
- **Card hover**: border brightens from 0.08 to 0.14 opacity.
- **Live indicator**: small pulsing dot, 2s opacity loop.
- **Dropdowns**: opacity + translateY fade-in, 200-250ms ease.

Keep motion subtle; excess animation undermines the calm, technical tone.

---

## Responsive Breakpoints

- **> 1280px**: Full desktop layout, two-column hero and feature grids.
- **992-1280px**: Condensed nav, reduced section padding.
- **768-991px**: Hamburger menu, hero collapses to single column, type scales down.
- **< 768px**: Mobile stack, full-width buttons, grids become single column.

---

## Do's and Don'ts

1. **Do** keep the background a deep navy (#04070E), never pure black -- the cool tint is the whole mood.
2. **Don't** introduce a second bright accent; the ice blue (#9DC8FF) is the only saturated color allowed.
3. **Do** spend your one high-contrast moment on a single white Primary button per view.
4. **Don't** use drop shadows; separate surfaces with lighter fills and 1px borders instead.
5. **Do** wrap icons in the rounded-square icon-pill; it is the system's signature.
6. **Don't** use emoji or typed unicode symbols (`v`, arrows, checks) for UI affordances -- always use outline icons.
7. **Do** let whitespace breathe; sections sit far apart and headlines have room around them.
8. **Do** keep type weights light (300-500) and lean on size and spacing for hierarchy.
9. **Don't** fully round corners except on pills, avatars, and status chips.
10. **Do** keep copy plain and specific; the tone is "a precise tool for builders," not a sales pitch.