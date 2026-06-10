# Design References — Well-Known Websites for Web Design / UI / UX

> Purpose: reference index for producing `design_(company).md` files.
> Researched: 2026-06-10. Intended for public GitHub distribution.
> Preview images removed for public distribution (third-party screenshots are copyrighted material). For local preview, use `https://image.thum.io/get/width/640/<url>`.

---

## 0. Legal Baseline

| Protected element | Legal basis | Risk |
|---|---|---|
| Code, text, photos, illustrations, icons, video | Copyright (footer notice + Terms of Use) | HIGH — direct reproduction is infringement |
| Logos, brand names | Trademark | HIGH — never use |
| Overall look & feel, layout bundle | Trade dress / design patents (bigger practical risk than copyright) | MEDIUM — 1:1 clones are risky |
| Layout patterns, interaction ideas, grids, spacing principles | Ideas are not protected | LOW — "inspired by" reference is fine |
| Fonts | Per-font license (mostly commercial) | MEDIUM — verify individually; use SIL OFL substitutes |
| Single colors | Not copyrightable; protectable only as color trademark / trade dress with secondary meaning | LOW alone; rises in combination |

### 0-1. Eligibility for design.md Production

> No license can legally prohibit a style-reference design.md (copyright does not protect style or ideas).
> Exclusions below exist because the output would be unusable in practice.

| Class | Criteria | Sites | Action |
|---|---|---|---|
| EXCLUDED | Official "do not imitate" clause + style equals brand identity + trade dress litigation history | Apple ("Do not imitate Apple communications") | No design.md. Study individual UX patterns only |
| EXCLUDED | Brand campaign site — entire design is a protected brand asset | Hall of Zero Limits (Sprite / Coca-Cola) | No design.md |
| CONDITIONAL | Character/illustration style is the core of the design (illustration = copyrighted artwork) | Duolingo, Headspace, Baemin (characters) | Extract layout/UX structure only; exclude illustration and character style |
| CONDITIONAL | Signature work of a single artist/studio (industry plagiarism norms, not law) | All creative studios (Lusion, Obys, etc.) | Never use as a sole reference; combine 2+ references; borrow techniques, not compositions |
| FREE | Standard ToS protection — patterns, structure, principles extractable | Everything else | design.md allowed, zero asset reuse |
| RECOMMENDED | Explicit open license | Section 9 design systems | Tokens/components directly usable |

### 0-2. Color Policy (finalized for public distribution)

| Rule | Verdict | Applies to |
|---|---|---|
| Registered color trademark or enforcement history (Tiffany Blue, T-Mobile Magenta class) | AVOID — use offset hue | none of the 10 current targets |
| Color pairing is the centerpiece of the brand identity AND the hue is uncommon | AVOID — use offset hue | Wise (neon lime + forest green), Stripe (blurple; same-industry dummy triggers the confusion bundle) |
| Common hue families (blues, indigos, neutrals, black/white) | USE ORIGINAL values | Linear, Vercel, Notion, Toss, Mercury, Aesop, Polestar, 29CM |
| Combination rule (always active) | Never combine: distinctive color + same industry + near-identical layout + brand name/logo | all |

### 0-3. Public GitHub Checklist

- [ ] All md files in English
- [ ] No brand assets in the repo: no logos, no proprietary fonts, no site screenshots, no copied copywriting
- [ ] Fonts referenced are open-licensed only (SIL OFL: Inter, Geist, Pretendard, JetBrains Mono, Lora, Instrument Serif, Archivo, Noto Serif KR)
- [ ] Icons: Lucide (ISC license), line style — no platform emoji anywhere
- [ ] Repo includes LICENSE (MIT or CC BY 4.0 for docs) + DISCLAIMER (template in section 11)
- [ ] Dummy content uses fictional entities only: Kitty Park, Ya-ong Kim, Calico Lee / CatTower LTD
- [ ] AVOID-class colors use offset values; original values may be listed as reference-only with a "do not ship" note

---

## 1. Global Product / SaaS

| # | Site | Link | Known for | License / imitation policy |
|---|---|---|---|---|
| 1 | ~~Apple~~ | https://www.apple.com | Minimal, premium imagery, scroll choreography | EXCLUDED — explicit "Do not imitate Apple communications"; trade dress litigation (Apple v. Samsung) |
| 2 | Stripe | https://stripe.com | Gradients, type hierarchy, developer landing standard | Marks Usage Agreement (stripe.com/legal/marks); color: AVOID blurple in same-industry output |
| 3 | Linear | https://linear.app | Dark UI, precise type, restrained motion | Standard ToS; "Linear style" widely adopted industry-wide; assets protected |
| 4 | Notion | https://www.notion.com | Illustration-led, friendly tone, mono + accent | Media kit / trademark guide; signature illustration style is copyrighted |
| 5 | Figma | https://www.figma.com | Colorful geometry, playful motion | Brand usage guide (no logo modification) |
| 6 | Vercel | https://vercel.com | Black/white minimal, Geist design language | Logo restricted; Geist font is open (SIL OFL) |
| 7 | Framer | https://www.framer.com | Motion-first landing, interactive demos | Standard ToS |
| 8 | Webflow | https://webflow.com | Embedded interactive product demo | ToS + brand guide |
| 9 | Slack | https://slack.com | Playful tone + clear onboarding | Media kit / brand guidelines |
| 10 | Dropbox | https://www.dropbox.com | Minimal/utility balance | Dedicated brand guidelines site |
| 11 | Airbnb | https://www.airbnb.com | Search-first home, DLS textbook | Belo logo trademarked; brand assets restricted |
| 12 | Spotify | https://open.spotify.com | Dark UI + vivid green, card grids | Design guidelines strictly restrict brand elements |
| 13 | Mailchimp | https://mailchimp.com | Illustration + copywriting; famous content style guide | Brand guide public (reference only) |
| 14 | Shopify | https://www.shopify.com | Conversion-focused landing structure | Polaris design system open source; brand assets restricted |
| 15 | Intercom | https://www.intercom.com | B2B SaaS landing hierarchy standard | Standard ToS |
| 16 | Loom | https://www.loom.com | Video-first hero | Standard ToS |
| 17 | Raycast | https://www.raycast.com | Dark glassmorphism, developer aesthetic | Standard ToS |
| 18 | The Browser Company | https://thebrowser.company | Editorial, handcrafted brand tone | Check footer terms; illustrations copyrighted |
| 19 | Superhuman | https://superhuman.com | Speed visualized through motion, gradients | Standard ToS |
| 20 | Pitch | https://pitch.com | Bold type + product screenshot staging | Standard ToS |
| 21 | Duolingo | https://www.duolingo.com | Character-driven gamified UX | CONDITIONAL: structure only; characters/illustration excluded |
| 22 | Headspace | https://www.headspace.com | Pastel illustration, emotion-led UX | CONDITIONAL: color mood/UX tone only; illustration style excluded |

## 2. Fintech

| # | Site | Link | Known for | License / imitation policy |
|---|---|---|---|---|
| 23 | Jeton | https://www.jeton.com | Awwwards SOTD; scroll morphing; b/w + orange | Check ToS; built by Burocratik |
| 24 | Wise | https://wise.com | Neon green brand, bold display type | 2023 rebrand assets fully protected; color: AVOID the lime/forest pair |
| 25 | Revolut | https://www.revolut.com | 3D renders + dark premium | Standard ToS |
| 26 | Mercury | https://mercury.com | Editorial-minimal fintech benchmark | Standard ToS |
| 27 | Ramp | https://ramp.com | Data-visualization-led B2B landing | Standard ToS |
| 28 | Cash App | https://cash.app | Experimental brand, strong green | Block brand guide; $ mark trademarked |

## 3. Korea

| # | Site | Link | Known for | License / imitation policy |
|---|---|---|---|---|
| 29 | Toss | https://toss.im | Korean fintech UX standard; scroll storytelling | TDS (internal design system) is private; some resources (Toss Face emoji font) openly licensed — verify per asset |
| 30 | Woowa Bros (Baemin) | https://www.woowahan.com | Kitschy brand tone, proprietary typefaces | CONDITIONAL: Baemin fonts (Eulji-ro, etc.) free with attribution; characters/kitsch illustration excluded |
| 31 | 29CM | https://www.29cm.co.kr | Editorial commerce; "Guide to Better Choice" | Standard ToS; editorial photos/copy protected |
| 32 | Musinsa | https://www.musinsa.com | High-density grid commerce UX | Standard ToS |

## 4. Creative Studios / Agencies

> All entries CONDITIONAL: never a sole reference; combine 2+; borrow techniques, not compositions.

| # | Site | Link | Known for |
|---|---|---|---|
| 33 | Lusion | https://lusion.co | Awwwards Developer SOTY 2023; real-time WebGL |
| 34 | Locomotive | https://locomotive.ca | 6x Awwwards Agency of the Year; custom typeface; locomotive-scroll is open source |
| 35 | Obys Agency | https://obys.agency | Typographic experiments, broken grids |
| 36 | Active Theory | https://activetheory.net | WebGL interactive pioneer |
| 37 | Resn | https://resn.co.nz | Experimental interaction |
| 38 | basement.studio | https://basement.studio | Brutalism + retro |
| 39 | Darkroom (ex Studio Freight) | https://darkroom.engineering | Lenis smooth-scroll authors (open source) |
| 40 | Noomo Agency | https://noomoagency.com | SOTY 2023 nominee; 3D narrative |
| 41 | Hello Monday | https://www.hellomonday.com | Type + interaction balance |
| 42 | Dogstudio | https://dogstudio.co | 3D mascot interaction |
| 43 | Igloo Inc | https://www.igloo.inc | Awwwards SOTY 2024; 3D voxel |

## 5. Brand / Commerce

| # | Site | Link | Known for | Policy |
|---|---|---|---|---|
| 44 | Aesop | https://www.aesop.com | Minimal luxury commerce standard; serif type | Brand identity (incl. store design) is the core asset — trade dress risk on close imitation |
| 45 | Bang & Olufsen | https://www.bang-olufsen.com | Premium product photography + dark tone | Active product trade dress enforcement |
| 46 | Gufram | https://www.gufram.it | Art furniture, bold visual storytelling | Products protected by design rights |
| 47 | Mana Yerba Mate | https://drinkmana.com | Awwwards SOTY 2023; 3D commerce | Check ToS |
| 48 | Polestar | https://www.polestar.com | Automotive minimalism benchmark | Brand guide exists |
| 49 | KPR | https://k-p-r.co | Awwwards SOTY 2022; storytelling commerce | Check ToS |

## 6. Interactive / Experience (Campaigns)

| # | Site | Link | Known for | Policy |
|---|---|---|---|---|
| 50 | Persepolis Reimagined | https://persepolis.getty.edu | SOTY 2022; scroll-based 3D tour | Getty cultural content protected |
| 51 | ~~Hall of Zero Limits (Sprite)~~ | https://www.hallofzerolimits.com | Brand campaign 3D experience | EXCLUDED — Coca-Cola brand campaign; entire design is brand asset |
| 52 | Opal Tadpole | https://opalcamera.com/opal-tadpole | SOTY 2024; product scroll staging | Check ToS |
| 53 | Don't Board Me | https://dontboard.me | SOTY 2024; illustrated interaction | No separate guide found |

## 7. Editorial / Content

| # | Site | Link | Known for | Policy |
|---|---|---|---|---|
| 54 | Medium | https://medium.com | Reading-experience standard (type/space/contrast) | ToS; posts owned by authors |
| 55 | The Pudding | https://pudding.cool | Data-journalism scrollytelling | Some project code public — verify per repo |
| 56 | It's Nice That | https://www.itsnicethat.com | Design magazine grid | ToS; featured works belong to artists |

## 8. Inspiration Galleries (discovery tools)

> Copyright of showcased work belongs to each original creator. Being listed in a gallery is not a usage grant.

| # | Site | Link | Use |
|---|---|---|---|
| 57 | Awwwards | https://www.awwwards.com | SOTD/SOTM/SOTY awards; global standard |
| 58 | CSS Design Awards | https://www.cssdesignawards.com | UI/UX/innovation categories |
| 59 | FWA | https://thefwa.com | Interactive/experimental work |
| 60 | Dribbble | https://dribbble.com | Shot-level UI browsing |
| 61 | Behance | https://www.behance.net | Project-level case studies |
| 62 | Mobbin | https://mobbin.com | Real app screen-flow archive (mobile UX) |
| 63 | Godly | https://godly.website | Modern/experimental curation |
| 64 | Land-book | https://land-book.com | Landing-page focused |
| 65 | Minimal Gallery | https://minimal.gallery | Minimal design focused |
| 66 | Siteinspire | https://www.siteinspire.com | Style/type filtered browsing |
| 67 | Httpster | https://httpster.net | Trend curation |
| 68 | Osmo | https://www.osmo.supply | Interaction code resources (paid membership; check its own license) |

## 9. Open Design Systems (directly usable by license)

> Safest primary sources for design.md token work. Code is open; each company's logos and brand assets are NOT included.

| # | System | Link | Owner | Code license |
|---|---|---|---|---|
| 69 | Material Design 3 | https://m3.material.io | Google | Apache 2.0 |
| 70 | Carbon | https://carbondesignsystem.com | IBM | Apache 2.0 |
| 71 | Polaris | https://polaris.shopify.com | Shopify | MIT |
| 72 | Primer | https://primer.style | GitHub | MIT |
| 73 | Fluent 2 | https://fluent2.microsoft.design | Microsoft | MIT |
| 74 | Atlassian Design System | https://atlassian.design | Atlassian | Partially open — verify per component |
| 75 | Lightning | https://www.lightningdesignsystem.com | Salesforce | BSD-3 |
| 76 | Base | https://base.uber.com | Uber | MIT (Base Web) |

---

## 10. design.md Production Checklist

- [ ] EXCLUDED sites (Apple, Hall of Zero Limits) are never design.md targets
- [ ] CONDITIONAL sites: extract structure/UX only; illustration and character styles excluded
- [ ] Combine 2+ references — no 1:1 reproduction of a single site (studios especially)
- [ ] No asset extraction (fonts/icons/images/illustrations) — open-licensed substitutes only (Google Fonts, Lucide, Heroicons)
- [ ] No logos, no brand names, no AVOID-class signature colors in shipped output
- [ ] Dummy content: fictional entities only — Kitty Park, Ya-ong Kim, Calico Lee / CatTower LTD
- [ ] All copy self-written (no copied original text)
- [ ] All md files in English

## 11. Theme File Naming Policy

> Verdict: do NOT name theme files after brands ("notion-like-theme", "stripe-style").
> Reason: mentioning a brand inside a document to identify a study source is nominative fair use; putting a trademark **in the name of your own work** is a different, riskier use (brand-named themes are routinely removed from marketplaces and repos on trademark complaints). Theme files are therefore named by visual character and contain no company names or domain-specific terms.

| Theme file | Visual character |
|---|---|
| design_gradient-canvas.md | Light SaaS, animated gradient hero, diagonal section cuts |
| design_dark-precision.md | Dark-only, typographic precision, border-based depth |
| design_mono-grid.md | Black/white geometry, exposed line grid, mono artifacts |
| design_warm-workspace.md | Warm white workspace, cards/toggles, single calm accent |
| design_scroll-story-blue.md | Mobile-first full-screen scroll narrative, single blue |
| design_editorial-hairline.md | Warm off-white, hairline rules, serif-italic accents |
| design_bold-twotone.md | Deep + bright two-tone, condensed display type |
| design_quiet-paper.md | Paper-toned quiet luxury, long-form copy, radius 0 |
| design_spec-minimal.md | Monochrome product page, oversized spec numerals |
| design_mono-editorial-shop.md | B/W editorial commerce, mixed Latin/Korean type |

Study sources for each theme are recorded in sections 1-7 of this document only. If zero linkage between themes and sources is preferred in the public repo, keep this reference file private and publish the theme files alone — they are self-contained.

## 12. Repository DISCLAIMER Template

```
DISCLAIMER

This repository contains independent design-pattern study notes and
demonstration pages. It is not affiliated with, sponsored by, or endorsed
by any of the companies referenced. All product names, logos, and brands
are property of their respective owners and are used for identification
and reference purposes only (nominative fair use).

No brand assets are reproduced in this repository: no logos, proprietary
fonts, screenshots, imagery, or copywriting from the referenced sites.
Color values are either common-hue approximations or deliberately offset
from brand-identifying colors. All demonstration content uses fictional
people and companies (Kitty Park, Ya-ong Kim, Calico Lee, CatTower LTD).

Documentation license: CC BY 4.0. Code samples: MIT.
```
