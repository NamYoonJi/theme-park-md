<p align="center">
  <img src="assets/banner.svg" alt="theme-park.md — a park of UI themes, written entirely in markdown" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/themes-10-5E6AD2?style=flat-square" alt="10 themes">
  <img src="https://img.shields.io/badge/format-markdown_only-101820?style=flat-square" alt="markdown only">
  <img src="https://img.shields.io/badge/emojis-0-F04452?style=flat-square" alt="zero emojis">
  <img src="https://img.shields.io/badge/docs-CC_BY_4.0-2383E2?style=flat-square" alt="CC BY 4.0">
</p>

# theme-park.md

A park of UI themes, written entirely in markdown.

Self-contained design specs (`design_*.md`) you can drop into any project and hand to an AI coding assistant — so it stops inventing its own color sense.

## Why this exists

We asked an AI coding assistant (yes, Claude Code) to build a landing page.

It worked. It also chose colors no human has ever put next to each other on purpose, centered everything, bolded half the page, and sprinkled emojis like confetti.

The problem wasn't the assistant — it was the missing spec. An LLM with no design constraints averages the entire internet, and the average of the internet is ugly. These files are the constraints: precise, opinionated, machine-readable-enough design specs that turn "make it look nice" into an actual instruction.

## What's inside

Each theme is one self-contained markdown file: principles, color tokens, typography, layout, components, motion, and an explicit don't-list.

| Theme | Visual character | Good for |
|---|---|---|
| `design_gradient-canvas.md` | Light, one animated gradient moment, diagonal section cuts | SaaS landing, technical audience |
| `design_dark-precision.md` | Dark-only, typographic precision, border-based depth | Productivity / developer tools |
| `design_mono-grid.md` | Black/white geometry, exposed line grid, monospace artifacts | Developer infrastructure, docs |
| `design_warm-workspace.md` | Warm white, cards and toggles, one calm accent | Collaboration tools, templates |
| `design_scroll-story-blue.md` | Mobile-first full-screen scroll narrative, single blue | Consumer app landing (KR-ready) |
| `design_editorial-hairline.md` | Warm off-white, hairline rules, serif-italic accents | Premium B2B, trust-led tone |
| `design_bold-twotone.md` | One deep tone + one bright tone, condensed display type | Confident consumer services |
| `design_quiet-paper.md` | Paper tones, long-form copy, radius 0, zero urgency | Premium commerce, editorial |
| `design_spec-minimal.md` | Monochrome, oversized spec numerals, uppercase wayfinding | Hardware / physical products |
| `design_mono-editorial-shop.md` | B/W editorial commerce, mixed Latin/Korean type | Curation-led shops |

## How to use

Clone once, reference forever. This repo is a library you point at — nothing gets copied into your projects.

1. Clone it anywhere:

   ```
   git clone https://github.com/<you>/theme-park.md ~/theme-park.md
   ```

2. Work in your own project directory as usual.
3. When it's time to build a page, hand your assistant the path:

   > Build the landing page as a single HTML file.
   > Follow `~/theme-park.md/design_dark-precision.md` exactly, including the Don't section.

4. Review the output against the spec, not against vibes. Every token, size, and motion rule in the file is checkable.

> [!IMPORTANT]
> One theme per page. Mixing two defeats the purpose.

Notes for this workflow:

- Themes are self-contained — the assistant needs that one file only, no other context from this repo.
- Filenames are lowercase kebab-case on purpose: paths get typed into prompts, so they should be typeable.
- `git pull` occasionally; specs may tighten over time.

### Optional: pin a theme to a project

For a project you'll iterate on, copy the chosen theme into the project root and rename it to `DESIGN.md`:

```
cp ~/theme-park.md/design_dark-precision.md ./DESIGN.md
```

Why caps, why root: this follows the `CLAUDE.md` / `AGENTS.md` convention — a single uppercase instruction file at the root that assistants treat as standing context. From then on, "follow DESIGN.md" is the whole prompt.

Side benefit: copying pins the spec version to the project. The library can evolve (`git pull`) without shifting the ground under work in progress. Inside this repo, themes stay lowercase (they're library content); `DESIGN.md` in caps exists only in consuming projects (it's an instruction file there).

## House rules

Every theme enforces the same baseline:

**No more emojis.** ~~🚀~~ ~~✨~~ ~~🎉~~ ~~💡~~ ~~🔥~~ ~~✅~~ ~~📈~~ ~~🎨~~ ~~👍~~ ~~⚡~~ — none of these. If a visual marker is genuinely needed, use a line-style SVG icon (Lucide, ISC license). An emoji is a font-rendering decision made by someone else's operating system; an icon is a design decision made by you.

**Open-licensed fonts only.** Inter, Geist, Pretendard, Bricolage Grotesque, Archivo, Lora, Instrument Serif, Noto Serif KR, JetBrains Mono — all SIL OFL. Reference by CDN; no font binaries in this repo.

**Fictional content only.** Demo people are Kitty Park, Ya-ong Kim, and Calico Lee. The demo company is CatTower LTD. No real people, companies, or publications in any dummy content.

**Deliberate color choices.** Common hue families are used freely. A few tokens are intentionally offset from brand-identifying colors — the spec will say so. Keep them as specified.

**One accent maximum.** Most pages die by a thousand accent colors. Each theme allows at most one (some allow zero).

## Disclaimer

> [!NOTE]
> This repository contains independent design-pattern study notes. It is not affiliated with, sponsored by, or endorsed by any company. No brand assets are included: no logos, proprietary fonts, screenshots, imagery, or copied copywriting. All demonstration content is fictional.

## License

Documentation: CC BY 4.0. Code samples: MIT.