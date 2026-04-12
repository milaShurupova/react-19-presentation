# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A single-file HTML slide deck for a ~95-minute two-presenter lecture on React 19 features. No build tools, no framework, no dependencies — just `index.html`. Deployable as a static site (e.g. GitHub Pages).

## How to Run

Open `index.html` in a browser. Navigate slides with arrow keys, Space, PageUp/PageDown, Home/End. Slide number is stored in the URL hash (`#slide-N`).

## Architecture

`index.html` is the entire presentation:
- CSS in an inline `<style>` block
- ~50 `<section class="slide">` elements
- A vanilla JS navigation engine at the bottom

### Slide Structure

Each slide is a `<section class="slide" data-presenter="p1|p2|shared">` with a type class:
- `title-slide` — centered, large text
- `divider-slide` — section dividers with gradient background
- `code-slide` — code-heavy, top-aligned
- `two-col-slide` — two-column layout

Presenter badges (`<span class="badge p1|p2|shared">`) appear top-right.

### Syntax Highlighting

Manual span-based highlighting using CSS classes: `.kw` (keyword/purple), `.fn` (function/blue), `.tag` (JSX tag/red), `.attr` (attribute/yellow), `.str` (string/green), `.num` (number/orange), `.cm` (comment/gray), `.dir` (directive/green bold).

### CSS Conventions

- CSS variables defined in `:root` — use these for all colors
- Code comparisons use `.code-compare` grid with `.before`/`.after` children
- Key takeaways use `.takeaway` styled blockquote
- Feature cards use `.card` inside `.feature-grid`
- Target viewport is 1536×678; every slide must fit without vertical overflow (use internal scrollbars on code/tables if needed)

### Navigation Engine

The `<script>` at the bottom manages slide transitions via `show(n)`, keyboard handlers, URL hash persistence, and a progress bar. Keep it self-contained — no external JS.
