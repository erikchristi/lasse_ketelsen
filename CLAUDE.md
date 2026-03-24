# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML website for **Lasse Ketelsen Haus & Hof Service** — a landscaping/craftsman business in Nordfriesland, Germany. No build tools, no package manager, no framework. Open HTML files directly in a browser to preview.

## Files

| File | Purpose |
|---|---|
| `index.html` | Main website (single page) |
| `impressum.html` | Legal imprint (§5 TMG) |
| `datenschutz.html` | Privacy policy (DSGVO) |
| `bilder/` | Project photos used in gallery and service cards |
| `Lasse_ketelsen_logo.png` | Square LK monogram logo — works on light backgrounds |

## Design System (index.html)

**Stack:** Pure HTML + Tailwind CSS via CDN (`cdn.tailwindcss.com`). No compilation step.

**Theme name:** "Nordic Craftsman Dark"

**Custom Tailwind colors** (defined in inline `tailwind.config`):
- `stone-dark` `#141C1A` · `stone` `#1E2B28` · `stone-mid` `#2C3D39`
- `sand` `#C8B48A` (gold accent) · `sand-light` `#E2D5B8` · `sand-pale` / `cream` `#F4F0E8`
- `terra` `#A85C3A` (CTA orange-brown) · `terra-light` `#C47A58`

**Fonts:** Bebas Neue (display/headings, renders uppercase) + Source Sans 3 (body). Loaded from Google Fonts.

**Key CSS classes:**
- `.hero-bg` — dark green gradient background for hero section
- `.grain::before` — SVG noise texture overlay
- `.gallery-grid` — CSS grid with responsive `grid-auto-rows` (140px mobile / 200px desktop)
- `.gallery-item` / `.gallery-overlay` — hover reveals caption overlay
- `.service-card` — lift + arrow reveal on hover
- `.btn-pulse` — terra-colored pulsing animation for primary CTA

## Page Structure (index.html sections)

1. `#start` — Hero (fixed header + full-bleed dark gradient)
2. Trust bar — 3-column strip (always 3 cols, even on mobile)
3. `#leistungen` — 3 service cards with real photos
4. `#ueber-uns` — 2-col layout: portrait placeholder + text + floating "10+" badge
5. `#referenzen` — Gallery grid (9 items, links to Instagram posts)
6. `#kontakt` — Dark CTA section with email + phone buttons
7. Footer — 3 columns + bottom bar with Impressum/Datenschutz links

## Gallery (Referenzen)

Each gallery item is an `<a>` linking to an Instagram post. Images come from `bilder/`. Items without a photo use a CSS gradient placeholder (`.ph-stone`, `.ph-earth`, `.ph-garden`, etc.).

**To add/update a gallery item:**
- Drop the image into `bilder/`
- Replace `<div class="ph ph-xxx ..."></div>` with `<img src="bilder/filename.png" alt="..." class="w-full h-full object-cover object-center">`
- Update the `href` to the correct Instagram post URL

**Instagram embeds do NOT work** — Instagram blocks embeds for non-logged-in users since 2024. Use local images instead.

## Company Data

| Field | Value |
|---|---|
| Name | Lasse Ketelsen |
| Legal form | Einzelunternehmer |
| Address | Horsbüller Str. 18, 25924 Emmelsbüll-Horsbüll |
| Phone | 04665/2209894 |
| Email | info@lk-hausundhof.de |
| Instagram | https://www.instagram.com/lasse__ketelsen/ |
| Facebook | https://www.facebook.com/lasse.ketelsen.9/ |

## Design Conventions

- All section headings use `font-display` (Bebas Neue) — automatically uppercase
- Body text: `font-normal` minimum (never `font-light` — too thin on mobile)
- Opacity for secondary text: `/80` minimum for readability
- Mobile: Trust bar stays 3-column with `flex-col` items and hidden subtitles (`hidden sm:block`)
- The `ui-ux-pro-max` skill is available for design system generation — run with `py ".claude/skills/ui-ux-pro-max/scripts/search.py"` (use `py` not `python3` on Windows)
