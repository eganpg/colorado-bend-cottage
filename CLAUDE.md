# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

**Colorado Bend Cottage** — a demand-testing landing page for a short-term rental cabin on the Colorado River near Colorado Bend State Park, Lampasas County, Texas.

The page is intentionally pre-booking: its only conversion goal is email capture. No booking engine, no calendar, no payments.

## Stack

Plain HTML/CSS/JS — single file (`index.html`). No build step, no framework, no dependencies beyond Google Fonts.

## Commands

Open `index.html` directly in a browser — no server needed. For local development with live reload:

```bash
npx serve .
# or
python3 -m http.server 8080
```

## Architecture

Everything lives in `index.html`:
- **Inline CSS** in `<style>` — design tokens defined as CSS custom properties in `:root`
- **Inline JS** in `<script>` — only handles email form submit (currently client-side only, logs to console)
- **Photos** in `photos/` — only JPG/PNG files work in browsers; HEIC files are present but not usable without conversion

## Email Form

The form (`#emailForm`) is wired to a `submit` handler that currently just logs the email and shows a success message. The `TODO` comment marks where to integrate an email service (Mailchimp, ConvertKit, Buttondown, etc.).

## Photos

Browser-compatible files in `photos/`:
- `dji_fly_20250111_*` — drone aerials of the river canyon and cottage (used in hero + gallery)
- `IMG_0768 2.JPG` / `IMG_0768 3.jpg` — annotated aerial showing hike/cabin/fish spots
- `IMG_1150.PNG` — Google Maps screenshot (not used on page)
- HEIC files — not usable in browsers without conversion

## SEO TODOs

- **Open Graph tags** — add `og:title`, `og:description`, `og:image`, `og:url` in `<head>` for social sharing previews
- **Canonical URL** — add `<link rel="canonical" href="...">` once the GitHub Pages URL is live
- **Structured data (JSON-LD)** — add a `LodgingBusiness` schema block with address, geo coordinates, and amenities for Google rich results
- **Body copy** — naturally work in "Post Oak Lake" and "Lampasas" in the visible page text to reinforce those search terms

## Design Tokens

| Token | Value | Usage |
|---|---|---|
| `--green-dark` | `#1E3A2F` | Primary dark, footer, CTA button |
| `--green-mid` | `#2C5544` | Hover states |
| `--green-light` | `#4A8B78` | Accents, labels, pillar card borders |
| `--cream` | `#F7F2EA` | Page background |
| `--sand` | `#E8DDD0` | Gallery section background |
| `--tan` | `#C9B99A` | Fine print, borders |
