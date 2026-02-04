# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page impress.js presentation titled "Fake it 'til they take it" — a 2600 talk about cryptocurrency poisoned address scams.

## Development

No build tools, package manager, or tests. Open `index.html` directly in a browser to view.

External dependencies are loaded via CDN (impress.js 2.0.0, Google Fonts) — no installation step needed.

## Architecture

Everything lives in `index.html`:
- **CSS** is embedded in `<style>` in the `<head>`
- **Slides** are `<div class="step">` elements inside `<div id="impress">`, positioned with `data-x`, `data-y`, `data-rotate`, and `data-scale` attributes
- **impress.js** is initialized at the bottom with `impress().init()`
- The final step is always an invisible `#overview` div whose `data-x`, `data-y`, and `data-scale` should be updated to encompass all slides whenever slides are added or repositioned

## Slide Conventions

- Each slide gets a comment header with `═` box-drawing characters
- Slides use incrementing `data-x` / `data-y` values and slight `data-rotate` to create a sweeping arc through space
- Section tags use `<span class="tag">` (variants: `.tag.red`, `.tag.blue`, `.tag.orange`)
- Color-coded actors: Alice = `.accent` (green #00e676), Bob = `.blue` (#40c4ff), Mallory = `.warn` (red #ff5252), general callouts = `.highlight` (orange #ffab40)
- Bullet lists use `<ul><li>` — CSS replaces default bullets with green `▸` markers
- Code snippets use `<code>` inline or `<pre>` for blocks (Source Code Pro monospace)
