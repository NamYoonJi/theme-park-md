<p align="center">
  <img src="assets/banner.svg" alt="theme-park.md" width="100%">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/themes-10-5E6AD2?style=flat-square" alt="10 themes">
  <img src="https://img.shields.io/badge/format-markdown_only-101820?style=flat-square" alt="markdown only">
  <img src="https://img.shields.io/badge/emojis-0-F04452?style=flat-square" alt="zero emojis">
  <img src="https://img.shields.io/badge/docs-CC_BY_4.0-2383E2?style=flat-square" alt="CC BY 4.0">
</p>
theme-park.md
AI-generated pages are ugly and all look the same. These specs fix that: deliberate colors and layout, and less AI-looking output — no emojis (🚀 ✨ 🎉 🔥 ✅), line-style SVG icons instead.
Each design_*.md is a self-contained spec: color tokens, typography, layout, components, motion, and a Don't list.
Themes
ThemeVisual characterdesign_gradient-canvas.mdLight, one animated gradient moment, diagonal cutsdesign_dark-precision.mdDark-only, typographic precision, border-based depthdesign_mono-grid.mdBlack/white geometry, exposed line grid, mono artifactsdesign_warm-workspace.mdWarm white, cards and toggles, one calm accentdesign_scroll-story-blue.mdMobile-first full-screen scroll narrative, single bluedesign_editorial-hairline.mdWarm off-white, hairline rules, serif-italic accentsdesign_bold-twotone.mdOne deep + one bright tone, condensed display typedesign_quiet-paper.mdPaper tones, long-form copy, radius 0, zero urgencydesign_spec-minimal.mdMonochrome, oversized spec numerals, uppercase labelsdesign_mono-editorial-shop.mdB/W editorial commerce, mixed Latin/Korean type
Usage
git clone https://github.com/<you>/theme-park.md ~/theme-park.md
Then, from any project, prompt your assistant:

Build the page as a single HTML file.
Follow ~/theme-park.md/design_dark-precision.md exactly, including the Don't section.

Optionally pin a theme to a project: cp ~/theme-park.md/design_dark-precision.md ./DESIGN.md — then "follow DESIGN.md" is the whole prompt.

[!IMPORTANT]
One theme per page. Mixing two defeats the purpose.

Rules baked into every theme

No emojis — line-style SVG icons only (Lucide, ISC)
Open-licensed fonts only (SIL OFL), referenced by CDN
Fictional demo content only: Kitty Park, Ya-ong Kim, Calico Lee / CatTower LTD
At most one accent color; some tokens are deliberately offset from brand-identifying hues — keep as specified

Disclaimer & License

[!NOTE]
Independent design-pattern study. Not affiliated with any company; no brand assets included; all demo content fictional.

Docs: CC BY 4.0 · Code samples: MIT