<p align="center">
  <img src="assets/banner.svg" alt="theme-park.md" width="100%">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/themes-13-5E6AD2?style=flat-square" alt="13 themes">
  <img src="https://img.shields.io/badge/format-markdown_only-101820?style=flat-square" alt="markdown only">
  <img src="https://img.shields.io/badge/docs-CC_BY_4.0-2383E2?style=flat-square" alt="CC BY 4.0">
</p>

# theme-park.md

AI-generated pages are ugly and all look the same. These specs fix that: deliberate colors and layout, and less AI-looking output — no emojis (~~🚀~~ ~~✨~~ ~~🎉~~ ~~🔥~~ ~~✅~~), line-style SVG icons instead.

Each `design_*.md` is a self-contained spec: color tokens, typography, layout, components, motion, and a Don't list.

## Themes

| Theme | Visual character |
|---|---|
| `design_gradient-canvas.md` | Light, one animated gradient moment, diagonal cuts |
| `design_dark-precision.md` | Dark-only, typographic precision, border-based depth |
| `design_mono-grid.md` | Black/white geometry, exposed line grid, mono artifacts |
| `design_warm-workspace.md` | Warm white, cards and toggles, one calm accent |
| `design_scroll-story-blue.md` | Mobile-first full-screen scroll narrative, single blue |
| `design_editorial-hairline.md` | Warm off-white, hairline rules, serif-italic accents |
| `design_bold-twotone.md` | One deep + one bright tone, condensed display type |
| `design_quiet-paper.md` | Paper tones, long-form copy, radius 0, zero urgency |
| `design_spec-minimal.md` | Monochrome, oversized spec numerals, uppercase labels |
| `design_mono-editorial-shop.md` | B/W editorial commerce, mixed Latin/Korean type |
| `design_midnight.md` | Dark navy engineering UI, single ice-blue accent, border depth |
| `design_phosphor.md` | Green CRT terminal, bitmap type, working TTY |
| `design_violet-phosphor.md` | Violet CRT terminal variant, live monitor and shell |

## Previews

Each theme below was built into a single self-contained HTML page from its spec alone — fictional content, line-style icons, no emoji. The caption under each preview links to the spec it was built from.

<table>
<tr>
<td width="50%"><img src="assets/gradient-canvas.png" alt="gradient-canvas preview"><br><sub><a href="designs/gradient-canvas.md">designs/gradient-canvas.md</a></sub></td>
<td width="50%"><img src="assets/dark-precision.png" alt="dark-precision preview"><br><sub><a href="designs/dark-precision.md">designs/dark-precision.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/mono-grid.png" alt="mono-grid preview"><br><sub><a href="designs/mono-grid.md">designs/mono-grid.md</a></sub></td>
<td><img src="assets/warm-workspace.png" alt="warm-workspace preview"><br><sub><a href="designs/warm-workspace.md">designs/warm-workspace.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/scroll-story-blue.png" alt="scroll-story-blue preview"><br><sub><a href="designs/scroll-story-blue.md">designs/scroll-story-blue.md</a></sub></td>
<td><img src="assets/editorial-hairline.png" alt="editorial-hairline preview"><br><sub><a href="designs/editorial-hairline.md">designs/editorial-hairline.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/bold-twotone.png" alt="bold-twotone preview"><br><sub><a href="designs/bold-twotone.md">designs/bold-twotone.md</a></sub></td>
<td><img src="assets/quiet-paper.png" alt="quiet-paper preview"><br><sub><a href="designs/quiet-paper.md">designs/quiet-paper.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/spec-minimal.png" alt="spec-minimal preview"><br><sub><a href="designs/spec-minimal.md">designs/spec-minimal.md</a></sub></td>
<td><img src="assets/mono-editorial-shop.png" alt="mono-editorial-shop preview"><br><sub><a href="designs/mono-editorial-shop.md">designs/mono-editorial-shop.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/midnight.png" alt="midnight preview"><br><sub><a href="designs/midnight.md">designs/midnight.md</a></sub></td>
<td><img src="assets/phosphor.png" alt="phosphor preview"><br><sub><a href="designs/phosphor.md">designs/phosphor.md</a></sub></td>
</tr>
<tr>
<td><img src="assets/violet-phosphor.png" alt="violet-phosphor preview"><br><sub><a href="designs/violet-phosphor.md">designs/violet-phosphor.md</a></sub></td>
<td width="50%"></td>
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
> Follow `~/theme-park.md/design_dark-precision.md` exactly, including the Don't section.

Optionally pin a theme to a project: `cp ~/theme-park.md/design_dark-precision.md ./DESIGN.md` — then "follow DESIGN.md" is the whole prompt.

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