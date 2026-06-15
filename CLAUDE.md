# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Design spec is binding

`DEEPTECH-FRONTIER-design-system.md` (project root) is the **authoritative design specification — every change to the site must follow it.** Read the relevant section before editing any page. It supersedes the older `deeptech_frontier/DESIGN.md` (kept only as an archived early draft).

Hard, non-negotiable constraints from that spec:
- Background is paper-white `#F6F5F1` — **no blue / blue-black fields anywhere** (this is the spec's central tenet: 「蓝是点睛不是底色」).
- Ink `#0B0B0C` text, secondary gray `#6F6F74`, 1px hairlines `#E3E1DB` **only** — no cards, borders-as-boxes, shadows, glassmorphism, or rounded corners.
- Cold-cyan accent `#16B9A6` must stay **under 5%** of any view — active nav underline / status dots / hover / one thin rule only. Never as fill, background, paired bars, or a second accent color.
- Text links with `→`, not solid/pill/shadowed buttons.
- Grotesque display + mono numerals; 12-col grid, 96px desktop margins, asymmetric layout, generous whitespace.
- Illustrations follow the §8 STYLE LOCK (studio macro photographic treatment, near-grayscale, hairline-framed) — never CGI/HUD/orbital/glowing-chip clichés.

See the spec's §7 global forbidden list and §11 common-pitfall fix scripts before adding anything new. **Caveat:** the spec mandates `#16B9A6`, but the integrated pages currently use `#00E5FF` / `#00B8D4` for the accent. Reconcile toward the spec value when you touch a page's accent; do not propagate the off-spec values to new work.

## What this is

A static, multi-page site for the "DEEPTECH FRONTIER / 深蓝前沿" homepage UI. The five screens were generated independently by Google Stitch and then **integrated into a linked site at the project root**. There is **no build system, no package manager, no tests, and no server**. Each page is a self-contained HTML file that pulls all dependencies (Tailwind, fonts) from CDNs at runtime.

## Project layout

### Integrated site (root) — the live, navigable pages

These five files are the integrated site. They are copies of the original Stitch outputs with **only the top-nav `href`s rewired** to link the pages together; nothing else was changed. Edit these for site behavior.

| File | Nav label | Copied from |
|------|-----------|-------------|
| `index.html` | 首页 | `deeptech_frontier_homepage_mockup/code.html` |
| `matrix.html` | 技术矩阵 | `deeptech_frontier_technology_matrix_optimized/code.html` |
| `explore.html` | 探索前沿 | `deeptech_frontier_explore_the_frontier_fixed/code.html` |
| `innovations.html` | 创新成果 | `deeptech_frontier_innovations/code.html` |
| `roadmap.html` | 未来计划 | `deeptech_frontier_future_roadmap/code.html` |

The top nav appears on every page with the same five items; each page highlights its own item as "active" using a per-page style (see the active-marker note below). Only the five nav `<a href>`s point to real files — all other `href="#"` links (footer, body links) are still placeholders by design.

### Original Stitch sources (archive) — do not treat as live

- `deeptech_frontier/DESIGN.md` — the canonical design system spec (colors, typography, spacing, component rules). The source of truth for design intent.
- `deeptech_frontier_homepage_mockup/`, `deeptech_frontier_technology_matrix_optimized/`, `deeptech_frontier_explore_the_frontier_fixed/`, `deeptech_frontier_innovations/`, `deeptech_frontier_future_roadmap/` — each holds the original `code.html` plus a `screen.png` reference render.

When editing a page, treat the matching `screen.png` in its source directory as the visual target. If you change design (not just links), keep the root file and its archived `code.html` in sync, or note the divergence.

## Viewing / "running"

There is nothing to build. Open `index.html` directly in a browser (e.g. on Windows: `start index.html`) and use the top nav to move between the five pages. Tailwind compiles in-browser via `https://cdn.tailwindcss.com`, so an internet connection is required for styling and fonts to load.

## Architecture & conventions

These files share a deliberate, rigid structure. When editing or adding screens, match it exactly:

- **Single-file pages.** Each page is `<head>` (Tailwind config + a small `<style>` block) followed by `<body>` containing `<nav>/<header>` → `<main>` → `<footer>`, and an optional trailing `<script>` for minor micro-interactions only. No external CSS/JS files.
- **Tailwind config is inlined** in a `<script id="tailwind-config">` block per file. The Material-Design color tokens (`surface`, `on-surface`, `outline-variant`, etc.), the custom `spacing` tokens (`margin-desktop: 96px`, `gutter: 24px`, `unit: 8px`, `columns: 12`), and the custom `fontFamily`/`fontSize` scale (`display-xl`, `headline-md`, `numeral-md`, `label-caps`, etc.) are duplicated into each file. Edit the config in the file you're working on; there is no shared config to import.
- **Design language is Swiss International Style / subtractive minimalism** (see `DESIGN.md`): strictly flat (no shadows/blurs), sharp 0px corners, 1px hairline borders (`#E3E1DB` / `outline-variant`) instead of elevation, a strict 12-column grid (`grid-cols-12 gap-gutter`) with 96px desktop margins, asymmetric layout (content on cols 1–7/8, meta/whitespace on the rest).
- **Typography carries the brand.** Hanken Grotesk for everything except technical data, dates, coordinates, and figure refs, which use JetBrains Mono via the `font-numeral-md` class. Labels/sub-labels use `font-label-caps` with wide tracking (`tracking-[0.18em]`–`[0.3em]`) and uppercase.
- **Accent color discipline.** Cold Cyan (`#00E5FF` / `cold-cyan`) is the only accent and must stay under ~5% of any view — used for active nav underlines, status dots, and small rules. Do not add gradients, glows, or new accent colors.
- **Content is bilingual** Chinese + English (page `lang="zh-CN"`): a Chinese headline paired with an uppercase English `label-caps` descriptor is the standard pattern.

### Inconsistencies to be aware of

The screens were generated independently and have drifted, so do not assume one file's setup matches another:

- `borderRadius` is `0px` in `homepage_mockup` (correct per the sharp-corners spec) but `0.25rem`/`0.5rem` in `explore_the_frontier_fixed`. Prefer 0px for new work.
- Custom semantic tokens `ink` (`#0B0B0C`), `warm-paper` (`#F6F5F1`), `cold-cyan` (`#00E5FF`) are defined in `homepage_mockup` but **not** in `explore_the_frontier_fixed`, which instead styles against the Material tokens (`primary`, `surface`, `outline-variant`). Check which token set a file uses before adding classes.
- Hairline helper classes differ by file (`.hairline`/`.hairline-v` vs `.hairline-x`/`.hairline-y` vs `.grid-hairline-x`/`.grid-hairline-y`). Reuse whatever the target file already defines.
- **The "active" nav marker differs per page** — there is no shared component. `index.html` uses `border-cold-cyan`, `matrix.html` uses `border-[#16B9A6]`, `explore.html` uses a `.custom-active` class, `innovations.html` uses `border-primary`, `roadmap.html` uses `border-cyan-accent`. When adding a nav item or touching the active state, match the convention already in that file.

When making a change consistent across all pages (e.g. a nav item, a footer link), apply it to each root `.html` file individually — there is no shared include or template. The nav `href`s are the one thing already wired up across all five (`index`/`matrix`/`explore`/`innovations`/`roadmap`.html); keep them intact when editing the nav.
