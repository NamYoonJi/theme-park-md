<p align="center">
  <img src="assets/banner.svg" alt="theme-park.md" width="100%">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/themes-31-5E6AD2?style=flat-square" alt="31 themes">
  <img src="https://img.shields.io/badge/format-markdown_only-101820?style=flat-square" alt="markdown only">
  <img src="https://img.shields.io/badge/docs-CC_BY_4.0-2383E2?style=flat-square" alt="CC BY 4.0">
</p>

# theme-park.md

AI-generated pages are ugly and all look the same. These specs fix that: deliberate colors and layout, and less AI-looking output — no emojis (~~🚀~~ ~~✨~~ ~~🎉~~ ~~🔥~~ ~~✅~~), line-style SVG icons instead.

Each `themes/*.md` is a self-contained spec: color tokens, typography, layout, components, motion, and a Don't list.

## Before / After

Same content, restyled with a theme — a plain page becomes a deliberate one.

You can turn this
<p align="center"><img src="assets/before.webp" alt="before" width="50%"></p>
into this
<table>
<tr>
<td width="59%"><img src="assets/grainy-blur1.png" alt="grainy-blur1" width="100%"></td>
<td width="41%"><img src="assets/grainy-blur2.png" alt="grainy-blur2" width="100%"></td>
</tr>
</table>

## Themes

### Dashboards & consoles

Data, metrics and monitoring UIs — each shown in both its light and dark scheme.

| Theme | Visual character |
|---|---|
| `themes/aurora.md` | Light analytics dashboard, dark sidebar, purple accent, donut/bar viz |
| `themes/graphite.md` | Matte charcoal industrial console, color only in data, ink-in reveal |
| `themes/marine-grid.md` | Square-corner corporate sensor board, deep marine blue, hairline panels |
| `themes/lumen.md` | Navy instrument panel, radial gauges, uniform-ramp heatmaps, mono readouts |
| `themes/nocturne.md` | Dense slate night-ops board, frost accent, packed 12-col panels |
| `themes/pulse.md` | Consumer-soft monitor, one blue, springy count-ups, large rounded cards |
| `themes/lab-console.md` | Light engineering console, dense run tables, live metrics |

### Research & project pages

Paper landings, case studies and scroll-driven data stories.

| Theme | Visual character |
|---|---|
| `themes/dark-editorial-scroll.md` | Research/paper landing, sticky title column, bright figure cards on near-black |
| `themes/scrolly-data.md` | Light scroll-driven data essay, serif editorial voice, live charts |

### Commerce & catalog

Product grids, storefronts and campaign pages.

| Theme | Visual character |
|---|---|
| `themes/dense-grid-shop.md` | High-density product grid, b/w chrome, one warm red for prices |
| `themes/mono-editorial-shop.md` | B/W editorial commerce, mixed Latin/Korean type |
| `themes/tech-blue.md` | Sky-tint campaign commerce UI, single cobalt accent |

### Portfolio & editorial

Expressive type, galleries and long-form reading.

| Theme | Visual character |
|---|---|
| `themes/kinetic-type.md` | White canvas, oversized grotesque + serif italic, scroll-driven type |
| `themes/mono-grid.md` | Black/white geometry, exposed line grid, mono artifacts |
| `themes/orange-offset-mono.md` | Offset black headline blocks on gray, mono labels, stair motif |
| `themes/editorial-hairline.md` | Warm off-white, hairline rules, serif-italic accents |
| `themes/brutalist-pop.md` | Black poster-size grotesque, single orange pop, marquee bands |
| `themes/quiet-paper.md` | Paper tones, long-form copy, radius 0, zero urgency |

### Terminal & experimental

CRT terminals, textured and toy-like novelty surfaces.

| Theme | Visual character |
|---|---|
| `themes/phosphor.md` | Green CRT terminal, bitmap type, working TTY |
| `themes/violet-phosphor.md` | Violet CRT terminal variant, live monitor and shell |
| `themes/grainy-blur.md` | Dark charcoal canvas, blurred color light-curtains, heavy film grain |
| `themes/studded-brick.md` | Studded toy-brick components, hard shadows, baseplate grid |

### Landing & marketing

General web pages, split by default colour scheme.

**Light**

| Theme | Visual character |
|---|---|
| `themes/gradient-canvas.md` | Light, one animated gradient moment, diagonal cuts |
| `themes/warm-workspace.md` | Warm white, cards and toggles, one calm accent |
| `themes/calm-pastel.md` | Warm paper canvas, super-rounded pastel surfaces, breathing motion |
| `themes/playful-blocks.md` | Saturated color chips, chunky 3D-lip buttons, springy motion |
| `themes/spec-minimal.md` | Monochrome, oversized spec numerals, uppercase labels |
| `themes/scroll-story-blue.md` | Mobile-first full-screen scroll narrative, single blue |

**Dark**

| Theme | Visual character |
|---|---|
| `themes/dark-glass.md` | Near-black frosted glass, hairline highlights, single violet glow |
| `themes/bold-twotone.md` | One deep + one bright tone, condensed display type |
| `themes/midnight.md` | Dark navy engineering UI, single ice-blue accent, border depth |

## Previews

Each theme was built into a single self-contained HTML page from its spec alone — fictional content, line-style icons, no emoji. Two views per theme (hero + a section below the fold; dashboards show the opposite colour scheme). Grouped by what each theme is for.

### Dashboards & consoles

Data, metrics and monitoring UIs — each shown in both its light and dark scheme.

<table>
<tr>
<td width="50%"><img src="assets/aurora.png" alt="aurora preview" width="49%"><img src="assets/aurora-b.png" alt="aurora second view" width="49%"><br><sub><a href="themes/aurora.md">themes/aurora.md</a></sub></td>
<td width="50%"><img src="assets/graphite.png" alt="graphite preview" width="49%"><img src="assets/graphite-b.png" alt="graphite second view" width="49%"><br><sub><a href="themes/graphite.md">themes/graphite.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/marine-grid.png" alt="marine-grid preview" width="49%"><img src="assets/marine-grid-b.png" alt="marine-grid second view" width="49%"><br><sub><a href="themes/marine-grid.md">themes/marine-grid.md</a></sub></td>
<td width="50%"><img src="assets/lumen.png" alt="lumen preview" width="49%"><img src="assets/lumen-b.png" alt="lumen second view" width="49%"><br><sub><a href="themes/lumen.md">themes/lumen.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/nocturne.png" alt="nocturne preview" width="49%"><img src="assets/nocturne-b.png" alt="nocturne second view" width="49%"><br><sub><a href="themes/nocturne.md">themes/nocturne.md</a></sub></td>
<td width="50%"><img src="assets/pulse.png" alt="pulse preview" width="49%"><img src="assets/pulse-b.png" alt="pulse second view" width="49%"><br><sub><a href="themes/pulse.md">themes/pulse.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/lab-console.png" alt="lab-console preview" width="49%"><img src="assets/lab-console-b.png" alt="lab-console second view" width="49%"><br><sub><a href="themes/lab-console.md">themes/lab-console.md</a></sub></td>
</tr>
</table>

### Research & project pages

Paper landings, case studies and scroll-driven data stories.

<table>
<tr>
<td width="50%"><img src="assets/dark-editorial-scroll.png" alt="dark-editorial-scroll preview" width="49%"><img src="assets/dark-editorial-scroll-b.png" alt="dark-editorial-scroll second view" width="49%"><br><sub><a href="themes/dark-editorial-scroll.md">themes/dark-editorial-scroll.md</a></sub></td>
<td width="50%"><img src="assets/scrolly-data.png" alt="scrolly-data preview" width="49%"><img src="assets/scrolly-data-b.png" alt="scrolly-data second view" width="49%"><br><sub><a href="themes/scrolly-data.md">themes/scrolly-data.md</a></sub></td>
</tr>
</table>

### Commerce & catalog

Product grids, storefronts and campaign pages.

<table>
<tr>
<td width="50%"><img src="assets/dense-grid-shop.png" alt="dense-grid-shop preview" width="49%"><img src="assets/dense-grid-shop-b.png" alt="dense-grid-shop second view" width="49%"><br><sub><a href="themes/dense-grid-shop.md">themes/dense-grid-shop.md</a></sub></td>
<td width="50%"><img src="assets/mono-editorial-shop.png" alt="mono-editorial-shop preview" width="49%"><img src="assets/mono-editorial-shop-b.png" alt="mono-editorial-shop second view" width="49%"><br><sub><a href="themes/mono-editorial-shop.md">themes/mono-editorial-shop.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/tech-blue.png" alt="tech-blue preview" width="49%"><img src="assets/tech-blue-b.png" alt="tech-blue second view" width="49%"><br><sub><a href="themes/tech-blue.md">themes/tech-blue.md</a></sub></td>
</tr>
</table>

### Portfolio & editorial

Expressive type, galleries and long-form reading.

<table>
<tr>
<td width="50%"><img src="assets/kinetic-type.png" alt="kinetic-type preview" width="49%"><img src="assets/kinetic-type-b.png" alt="kinetic-type second view" width="49%"><br><sub><a href="themes/kinetic-type.md">themes/kinetic-type.md</a></sub></td>
<td width="50%"><img src="assets/mono-grid.png" alt="mono-grid preview" width="49%"><img src="assets/mono-grid-b.png" alt="mono-grid second view" width="49%"><br><sub><a href="themes/mono-grid.md">themes/mono-grid.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/orange-offset-mono.png" alt="orange-offset-mono preview" width="49%"><img src="assets/orange-offset-mono-b.png" alt="orange-offset-mono second view" width="49%"><br><sub><a href="themes/orange-offset-mono.md">themes/orange-offset-mono.md</a></sub></td>
<td width="50%"><img src="assets/editorial-hairline.png" alt="editorial-hairline preview" width="49%"><img src="assets/editorial-hairline-b.png" alt="editorial-hairline second view" width="49%"><br><sub><a href="themes/editorial-hairline.md">themes/editorial-hairline.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/brutalist-pop.png" alt="brutalist-pop preview" width="49%"><img src="assets/brutalist-pop-b.png" alt="brutalist-pop second view" width="49%"><br><sub><a href="themes/brutalist-pop.md">themes/brutalist-pop.md</a></sub></td>
<td width="50%"><img src="assets/quiet-paper.png" alt="quiet-paper preview" width="49%"><img src="assets/quiet-paper-b.png" alt="quiet-paper second view" width="49%"><br><sub><a href="themes/quiet-paper.md">themes/quiet-paper.md</a></sub></td>
</tr>
</table>

### Terminal & experimental

CRT terminals, textured and toy-like novelty surfaces.

<table>
<tr>
<td width="50%"><img src="assets/phosphor.png" alt="phosphor preview" width="49%"><img src="assets/phosphor-b.png" alt="phosphor second view" width="49%"><br><sub><a href="themes/phosphor.md">themes/phosphor.md</a></sub></td>
<td width="50%"><img src="assets/violet-phosphor.png" alt="violet-phosphor preview" width="49%"><img src="assets/violet-phosphor-b.png" alt="violet-phosphor second view" width="49%"><br><sub><a href="themes/violet-phosphor.md">themes/violet-phosphor.md</a></sub></td>
</tr>
<tr>
<td width="50%"><img src="assets/grainy-blur1.png" alt="grainy-blur preview" width="49%"><img src="assets/grainy-blur2.png" alt="grainy-blur second view" width="49%"><br><sub><a href="themes/grainy-blur.md">themes/grainy-blur.md</a></sub></td>
<td width="50%"><img src="assets/studded-brick.png" alt="studded-brick preview" width="49%"><img src="assets/studded-brick-b.png" alt="studded-brick second view" width="49%"><br><sub><a href="themes/studded-brick.md">themes/studded-brick.md</a></sub></td>
</tr>
</table>

### Landing & marketing

General web pages — the left column is light-scheme themes, the right column is dark-scheme themes.

<table>
<tr><th width="50%">Light</th><th width="50%">Dark</th></tr><tr><td width="50%"><img src="assets/gradient-canvas.png" alt="gradient-canvas preview" width="49%"><img src="assets/gradient-canvas-b.png" alt="gradient-canvas second view" width="49%"><br><sub><a href="themes/gradient-canvas.md">themes/gradient-canvas.md</a></sub></td><td width="50%"><img src="assets/dark-glass.png" alt="dark-glass preview" width="49%"><img src="assets/dark-glass-b.png" alt="dark-glass second view" width="49%"><br><sub><a href="themes/dark-glass.md">themes/dark-glass.md</a></sub></td></tr><tr><td width="50%"><img src="assets/warm-workspace.png" alt="warm-workspace preview" width="49%"><img src="assets/warm-workspace-b.png" alt="warm-workspace second view" width="49%"><br><sub><a href="themes/warm-workspace.md">themes/warm-workspace.md</a></sub></td><td width="50%"><img src="assets/bold-twotone.png" alt="bold-twotone preview" width="49%"><img src="assets/bold-twotone-b.png" alt="bold-twotone second view" width="49%"><br><sub><a href="themes/bold-twotone.md">themes/bold-twotone.md</a></sub></td></tr><tr><td width="50%"><img src="assets/calm-pastel.png" alt="calm-pastel preview" width="49%"><img src="assets/calm-pastel-b.png" alt="calm-pastel second view" width="49%"><br><sub><a href="themes/calm-pastel.md">themes/calm-pastel.md</a></sub></td><td width="50%"><img src="assets/midnight.png" alt="midnight preview" width="49%"><img src="assets/midnight-b.png" alt="midnight second view" width="49%"><br><sub><a href="themes/midnight.md">themes/midnight.md</a></sub></td></tr><tr><td width="50%"><img src="assets/playful-blocks.png" alt="playful-blocks preview" width="49%"><img src="assets/playful-blocks-b.png" alt="playful-blocks second view" width="49%"><br><sub><a href="themes/playful-blocks.md">themes/playful-blocks.md</a></sub></td><td></td></tr><tr><td width="50%"><img src="assets/spec-minimal.png" alt="spec-minimal preview" width="49%"><img src="assets/spec-minimal-b.png" alt="spec-minimal second view" width="49%"><br><sub><a href="themes/spec-minimal.md">themes/spec-minimal.md</a></sub></td><td></td></tr><tr><td width="50%"><img src="assets/scroll-story-blue.png" alt="scroll-story-blue preview" width="49%"><img src="assets/scroll-story-blue-b.png" alt="scroll-story-blue second view" width="49%"><br><sub><a href="themes/scroll-story-blue.md">themes/scroll-story-blue.md</a></sub></td><td></td></tr></table>

> [!NOTE]
> Previews are screenshots rendered at 1280px. Dashboard cells pair the light and dark scheme of one theme; all other cells pair the hero with a section below the fold.

## Usage

```
git clone https://github.com/<you>/theme-park.md ~/theme-park.md
```

Then, from any project, prompt your assistant:

> Build the page as a single HTML file.
> Follow `~/theme-park.md/themes/midnight.md` exactly, including the Don't section.

Optionally pin a theme to a project: `cp ~/theme-park.md/themes/midnight.md ./DESIGN.md` — then "follow DESIGN.md" is the whole prompt.

> [!IMPORTANT]
> One theme per page. Mixing two defeats the purpose.

## Rules baked into every theme

- No emojis — line-style SVG icons only (Lucide, ISC)
- Open-licensed fonts only (SIL OFL), referenced by CDN
- Some colors are deliberately offset from brand-identifying hues

## Disclaimer & License

> [!NOTE]
> Independent design-pattern study. Not affiliated with any company; no brand assets included; all demo content fictional (except my profile).

Docs: CC BY 4.0 · Code samples: MIT
