# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Design spec is binding

`DEEPTECH-FRONTIER-design-system.md` (project root) is the **authoritative design specification — every change to the site must follow it.** Read the relevant section before editing any page. It supersedes the older `原始素材/deeptech_frontier/DESIGN.md` (kept only as an archived early draft).

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
| `index.html` | 首页 | `原始素材/deeptech_frontier_homepage_mockup/code.html` |
| `matrix.html` | 技术矩阵 | `原始素材/deeptech_frontier_technology_matrix_optimized/code.html` |
| `explore.html` | 探索前沿 | `原始素材/deeptech_frontier_explore_the_frontier_fixed/code.html` |
| `innovations.html` | 创新成果 | `原始素材/deeptech_frontier_innovations/code.html` |
| `roadmap.html` | 未来计划 | `原始素材/deeptech_frontier_future_roadmap/code.html` |

The top nav appears on every page with the same five items; each page highlights its own item as "active" using a per-page style (see the active-marker note below). Only the five nav `<a href>`s point to real files — all other `href="#"` links (footer, body links) are still placeholders by design.

**Brand name:** the homepage hero / wordmark / footer now read **`Information / Frontier`** (the old `深蓝前沿` was replaced; `DEEPTECH FRONTIER` remains as the uppercase English sub-mark). The design spec's §1 was updated to match. Subpages keep `DEEPTECH FRONTIER` as their wordmark.


### Original Stitch sources (archive) — do not treat as live

All six original Stitch export directories live under `原始素材/` (gitignored — local only, not published):

- `原始素材/deeptech_frontier/DESIGN.md` — an archived early design draft (superseded by the root `DEEPTECH-FRONTIER-design-system.md`).
- `原始素材/deeptech_frontier_homepage_mockup/`, `原始素材/deeptech_frontier_technology_matrix_optimized/`, `原始素材/deeptech_frontier_explore_the_frontier_fixed/`, `原始素材/deeptech_frontier_innovations/`, `原始素材/deeptech_frontier_future_roadmap/` — each holds the original `code.html` plus a `screen.png` reference render.

When editing a page, treat the matching `screen.png` in its source directory as the visual target. If you change design (not just links), keep the root file and its archived `code.html` in sync, or note the divergence.

### Current-state screenshots

`screenshots/` holds one full-page render per live page (`index.png`, `matrix.png`, `explore.png`, `innovations.png`, `roadmap.png`) — captured at 1440px width / 2× density with all scroll-reveal animations already triggered (final, fully-revealed state). These reflect the **current** integrated site after the brand rename + metal-title work, unlike the archived `原始素材/**/screen.png` which show the pre-integration Stitch originals. Regenerate them after visual changes by serving locally and screenshotting each page full-page.

## Viewing / "running"

There is nothing to build. For a quick look, open `index.html` directly (e.g. on Windows: `start index.html`) — every page still works standalone over `file://`, and Tailwind compiles in-browser via `https://cdn.tailwindcss.com` (internet required for styling/fonts).

**To experience the real navigation (zero-flicker SPA transitions), serve over HTTP**, not `file://`. The in-page router uses `fetch`, which the browser blocks under `file://` (CORS) — there it silently falls back to ordinary full-page navigation (the fade-out/in). Start a local server from the project root:

```
python -m http.server 8000
```

then open `http://localhost:8000/index.html`.

## Architecture & conventions

The five root pages were originally independent Stitch exports, but have since been **unified into a pseudo-SPA**: they now share a byte-identical `<head>` (Tailwind config + `<style>`) and an identical trailing `<script>`, so clicking the nav swaps only `<main>` in place (Tailwind compiles once → no FOUC flicker). When editing, preserve this shared structure.

- **Each page is still a complete, standalone HTML file** — `<head>` → `<body>` with `<nav>/<header>` → `<main>` → `<footer>` → unified `<script>`. No external CSS/JS files. Direct-loading any page works; the SPA is a progressive enhancement layered on top.
- **The `<head>` is now identical across all five pages** — same inlined `tailwind.config` (the union of every page's tokens) and same `<style>` block (all hairline/accent/animation helper classes merged). **When you change the config or a shared style, apply the exact same edit to all five files** so the SPA's single-compile assumption holds. There is still no build-time shared include — the duplication is intentional and must stay in sync.
- **The trailing `<script> is identical across all five pages.** It defines `initPage()` (re-entrant: scroll-reveal observers, hairline-draw, hero parallax — re-run after each `<main>` swap), `bindGlobalInteractions()` (header hairline-on-scroll, plus matrix table-row and roadmap milestone hovers via event delegation), and the SPA router (`fetch` → `DOMParser` → replace `<main>` + `<title>` + active nav, `history.pushState`, `popstate` for back/forward, wrapped in `document.startViewTransition` when available). **Any failure (e.g. `file://` CORS) falls back to a normal `window.location` navigation** — the site never breaks.
- **Scroll & page-transition motion** is deliberately restrained per the design spec (§0/§7): `[data-reveal]` (fade+rise), `[data-draw]`/`[data-draw-y]` (hairlines drawn in), tiny hero parallax, and a cross-fade on page swap. All gated behind `prefers-reduced-motion`.
- **Design language is Swiss International Style / subtractive minimalism**: strictly flat (no shadows/blurs), sharp 0px corners, 1px hairline borders (`#E3E1DB` / `outline-variant`) instead of elevation, a strict 12-column grid (`grid-cols-12 gap-gutter`) with 96px desktop margins, asymmetric layout (content on cols 1–7/8, meta/whitespace on the rest).
- **Typography carries the brand.** Hanken Grotesk for everything except technical data, dates, coordinates, and figure refs, which use JetBrains Mono via the `font-numeral-md` class. Labels/sub-labels use `font-label-caps` with wide tracking (`tracking-[0.18em]`–`[0.3em]`) and uppercase.
- **Hero / masthead display titles use a brushed-metal treatment** via the shared `.metal-text` class — a silver-grey vertical gradient + faint vertical brush stripes clipped to the text (`background-clip:text`), near-grayscale to fit the §8 "brushed aluminum" material DNA (no saturated color). It is gated behind `@supports (background-clip:text)` and falls back to ink `#0B0B0C`. Applied **only to the largest titles** (homepage hero `Information / Frontier`, and each subpage's `display-lg` masthead title) where the heavy weight lets the gradient read; never on nav/footer/body text where thin strokes would muddy it. The class lives in the shared `<style>`, so it must stay identical across all five files.
- **Accent color discipline.** Cold Cyan is the only accent and must stay under ~5% of any view — active nav underline, status dots, small rules. The codebase uses `#00E5FF` (exposed as both `cold-cyan` and `cyan-accent` tokens, which now point to the same value). **Note:** the design spec (`DEEPTECH-FRONTIER-design-system.md`) mandates `#16B9A6`; the site intentionally stays on `#00E5FF` per an explicit owner decision. Do not add gradients, glows, or new accent colors.
- **Active nav** is a single shared hook: the `.nav-active` class (2px `#00E5FF` underline). The router toggles it by filename on load and on every swap. All five pages' nav `<a>`s use it — do not reintroduce per-page active markers.
- **Content is bilingual** Chinese + English (page `lang="zh-CN"`): a Chinese headline paired with an uppercase English `label-caps` descriptor is the standard pattern.

### Editing rules (post-unification)

- **A change to `<head>` or `<script>` must be replicated verbatim across all five files.** They are intentionally identical; if they drift, the SPA swap will mis-render (a swapped-in `<main>` is styled by the *host* page's config). After editing, diff the five `<head>`/`<script>` blocks to confirm they still match.
- **`<main>` is the only swap target** — keep exactly one `<main>…</main>` per page. Per-page content, layout, and `data-reveal`/`data-draw` markup live inside `<main>` and may differ freely.
- **`nav`/`footer` DOM is left per-page** (not yet unified); only the `.nav-active` hook and the five nav `href`s are shared. Keep the five `href`s (`index`/`matrix`/`explore`/`innovations`/`roadmap`.html) intact — the router keys off them.
- All other `href="#"` links (footer, body CTAs) remain placeholders by design; the router ignores them.
