# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file static personal academic website for Dr. Seongho An (University of Central Florida, School of Public Administration). The entire site lives in `index.html` — no build tools, no frameworks, no dependencies.

## Deployment

Open `index.html` directly in a browser, or deploy to GitHub Pages by pushing to the repo root.

## Architecture

Everything is in one file: `index.html` contains all CSS (in `<style>`), HTML, and JavaScript (in `<script>` at the bottom).

**Sections (in order):** Nav → Hero (`#about`) → Current Projects (`#research`) → Publications (`#publications`) → Teaching (`#teaching`) → Contact (`#contact`) → Footer

**CSS variable tokens** (defined in `:root`):
- `--accent: #1a3a5c` — primary dark navy
- `--link: #0066cc` — link blue
- `--text: #1d1d1f`, `--text-secondary: #6e6e73` — Apple-style near-black and gray
- `--surface: #f5f5f7`, `--border: #d2d2d7` — light gray backgrounds/borders

**Carousel pattern** (used in both Publications and Teaching):
- Full viewport-width scrollable row: `margin-left: calc(50% - 50vw); width: 100vw`
- Horizontal scroll with `scroll-snap-type: x mandatory`
- Cards use `flex: 0 0 [width]px` and `scroll-snap-align: start`
- Arrow buttons call `scrollPub(dir)` / `scrollCourse(dir)` JS functions at the bottom
- Padding aligns card start with the `.container` (max-width 900px): `padding: 0 max(24px, calc(50vw - 450px))`

**Card top-border style** (used in project, publication, and course cards):
- `border-top: 4px solid var(--text)` — thick black line at top of each card

**Project cards** (`.project-card`): Full `<a>` tags linking to external project sites. 2-column grid. Last odd card gets `max-width: calc(50% - 10px)` to avoid spanning full width alone.

## Content Notes

- Profile photo: add `photo.jpg` to the folder, then uncomment `<img src="photo.jpg">` in the hero section
- CV PDF: add `cv.pdf` to the folder, update the `href="#"` on the "Download CV" button
- ORCID: placeholder `href="#"` in the Contact section needs a real link
- All 21 refereed articles are in the Publications carousel, ordered newest → oldest (2026–2016)
