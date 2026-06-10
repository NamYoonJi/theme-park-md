<p align="center">
  <img src="assets/banner.svg" alt="theme-park.md" width="100%">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/themes-14-5E6AD2?style=flat-square" alt="14 themes">
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

| Theme | Visual character |
|---|---|
| `themes/gradient-canvas.md` | Light, one animated gradient moment, diagonal cuts |
| `themes/dark-precision.md` | Dark-only, typographic precision, border-based depth |
| `themes/mono-grid.md` | Black/white geometry, exposed line grid, mono artifacts |
| `themes/warm-workspace.md` | Warm white, cards and toggles, one calm accent |
| `themes/scroll-story-blue.md` | Mobile-first full-screen scroll narrative, single blue |
| `themes/editorial-hairline.md` | Warm off-white, hairline rules, serif-italic accents |
| `themes/bold-twotone.md` | One deep + one bright tone, condensed display type |
| `themes/quiet-paper.md` | Paper tones, long-form copy, radius 0, zero urgency |
| `themes/spec-minimal.md` | Monochrome, oversized spec numerals, uppercase labels |
| `themes/mono-editorial-shop.md` | B/W editorial commerce, mixed Latin/Korean type |
| `themes/midnight.md` | Dark navy engineering UI, single ice-blue accent, border depth |
| `themes/phosphor.md` | Green CRT terminal, bitmap type, working TTY |
| `themes/violet-phosphor.md` | Violet CRT terminal variant, live monitor and shell |
| `themes/grainy-blur.md` | Dark charcoal canvas, blurred color light-curtains, heavy film grain |

## Previews

Each theme below was built into a single self-contained HTML page from its spec alone — fictional content, line-style icons, no emoji. The caption under each preview links to the spec it was built from.

<table>
<tr>
<td width="50%"><img src="assets/gradient-canvas.png" alt="gradient-canvas preview"><br><sub><a href="themes/gradient-canvas.md">themes/gradient-canvas.md</a></sub></td>
<td width="50%"><img src="assets/dark-precision.png" alt="dark-precision preview"><br><sub><a href="themes/dark-precision.md">themes/dark-precision.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/mono-grid.png" alt="mono-grid preview"><br><sub><a href="themes/mono-grid.md">themes/mono-grid.md</a></sub></td>
<td><img src="assets/warm-workspace.png" alt="warm-workspace preview"><br><sub><a href="themes/warm-workspace.md">themes/warm-workspace.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/scroll-story-blue.png" alt="scroll-story-blue preview"><br><sub><a href="themes/scroll-story-blue.md">themes/scroll-story-blue.md</a></sub></td>
<td><img src="assets/editorial-hairline.png" alt="editorial-hairline preview"><br><sub><a href="themes/editorial-hairline.md">themes/editorial-hairline.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/bold-twotone.png" alt="bold-twotone preview"><br><sub><a href="themes/bold-twotone.md">themes/bold-twotone.md</a></sub></td>
<td><img src="assets/quiet-paper.png" alt="quiet-paper preview"><br><sub><a href="themes/quiet-paper.md">themes/quiet-paper.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/spec-minimal.png" alt="spec-minimal preview"><br><sub><a href="themes/spec-minimal.md">themes/spec-minimal.md</a></sub></td>
<td><img src="assets/mono-editorial-shop.png" alt="mono-editorial-shop preview"><br><sub><a href="themes/mono-editorial-shop.md">themes/mono-editorial-shop.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/midnight.png" alt="midnight preview"><br><sub><a href="themes/midnight.md">themes/midnight.md</a></sub></td>
<td><img src="assets/phosphor.png" alt="phosphor preview"><br><sub><a href="themes/phosphor.md">themes/phosphor.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/violet-phosphor.png" alt="violet-phosphor preview"><br><sub><a href="themes/violet-phosphor.md">themes/violet-phosphor.md</a></sub></td>
<td><img src="assets/grainy-blur1.png" alt="grainy-blur preview"><br><sub><a href="themes/grainy-blur.md">themes/grainy-blur.md</a></sub></td>
</tr>
</table>

> [!NOTE]
> Previews are above-the-fold screenshots rendered at 1280px.

## Usage

```
git clone https://github.com/<you>/theme-park.md ~/theme-park.md
```

Then, from any project, prompt your assistant:

> Build the page as a single HTML file.
> Follow `~/theme-park.md/themes/dark-precision.md` exactly, including the Don't section.

Optionally pin a theme to a project: `cp ~/theme-park.md/themes/dark-precision.md ./DESIGN.md` — then "follow DESIGN.md" is the whole prompt.

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