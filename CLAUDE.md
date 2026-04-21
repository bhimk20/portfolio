# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-file static HTML portfolio site (`index.html`) for Bhimeswara Katriki — no build system, no dependencies, no package manager. Everything is self-contained: CSS in `<style>`, JavaScript in `<script>`.

To preview locally, open `index.html` directly in a browser or run a simple server:
```
python3 -m http.server 8000
```

## Architecture

**One file, three layers:**
- **CSS** (`<style>` block, lines 9–178): All styling via CSS custom properties defined in `:root`. No external CSS framework.
- **HTML** (lines 180–426): Semantic sections (`#experience`, `#skills`, `#highlights`, `#education`, `#contact`) plus a fixed `<nav>`.
- **JS** (`<script>` block, lines 412–426): Two small functions — `tab()` for experience card tab switching, and an `IntersectionObserver` for scroll-triggered `.fade-in` animations.

## Design tokens (CSS custom properties)

Defined in `:root` and used everywhere — change these to retheme the whole site:
- `--bg`, `--surface`, `--surface2`, `--surface3`: dark background layers
- `--text`, `--muted`, `--dim`: text hierarchy
- `--a` (lime `#c8f060`), `--a2` (teal `#6af0c0`), `--a3` (orange `#f0a060`): accent colors
- `--mono`, `--serif`, `--sans`: font families (Google Fonts: DM Mono, DM Serif Display, Syne)

Pill colors map to accent variables: `.pg` → teal (`--a2`), `.py` → lime (`--a`), `.po` → orange (`--a3`).

## Experience cards / tab system

Each experience entry (`.exp-card`) has three tab panels: **Impact** (`.imp-grid`), **Work done** (`.work-list`), **Skills used** (`.sk-grid`). The `tab(btn, panelId)` function toggles `.on` classes on both the button and the target panel within the same `.exp-card`. Panel IDs are prefixed: `l-` for Lucid, `m-` for LTIMindtree.

## Responsive breakpoint

Single breakpoint at `768px`: nav links hide, hero collapses to single column, two-column grids (`.hl-grid`, `.ct-grid`) go to one column, `.edu-grid` stacks vertically, tab buttons wrap to 2-per-row.

## Asset files

`Lucid_Knowledge_Hub_v2.docx` and `Mindtree_Knowledge_Hub_v2.docx` are source documents for the experience content — not served by the site, used only as reference.
