# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static single-page website for **Bounty Gallery** — a 24/7 art gallery inside Bounty Coffee Bar in Tashkent. Deployed via GitHub Pages (`bgallery.github.io`).

## Structure

- `index.html` — the entire site: CSS (inline `<style>`), HTML, and embedded base64 images
- `img/1/art.jpeg` — current month's painting (swap this to change the exhibited artwork)

No build step, no dependencies, no package manager. Open `index.html` directly in a browser to preview.

## Architecture

Everything lives in `index.html`:

- **CSS variables** at `:root` define the full color palette (`--teal`, `--gold`, `--ink`, etc.)
- **Layout**: CSS Grid two-column hero (`hero-left` = text/stats, `hero-right` = painting), then stacked sections below
- **Animations**: `fadeUp`, `fadeIn`, `pulse`, `fillBar`, `marquee` — all defined via `@keyframes` in `<style>`
- **Café photos**: embedded as base64 `data:image/jpeg` strings directly in `<img src="">` tags
- **Current exhibition**: update `.pname`, `.pauthor`, `.ptext`, `.pdates`, the `<img src="img/1/art.jpeg">`, and the `--pct` CSS variable on `.mbfill` (controls the month progress bar fill)
- **Responsive**: single `@media(max-width:860px)` breakpoint switches to single-column layout

## Deployment

Push to `main` → GitHub Pages serves `index.html` automatically.
