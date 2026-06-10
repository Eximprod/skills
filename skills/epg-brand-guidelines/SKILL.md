---
name: epg-brand-guidelines
description: Applies Eximprod Group's (EPG) official brand colors and typography to any artifact that benefits from the company's look-and-feel — presentations (.pptx), documents (.docx / Google Docs), and web/HTML/CSS. Use it whenever brand colors, style guidelines, visual formatting, or company design standards apply, even if the user doesn't explicitly say "brand."
license: Complete terms in LICENSE.txt
---

# Eximprod Group Brand Styling

## Overview

To access Eximprod Group's (EPG) official brand identity and style resources, use this skill.

**Keywords**: branding, corporate identity, visual identity, post-processing, styling, brand colors, typography, Eximprod brand, EPG, visual formatting, visual design, slides, presentations, documents, web, HTML, CSS

## Brand Guidelines

### Colors

**Main Colors:**

- Ink:        `#0A1A3F`  - Primary text / dark backgrounds (navy-derived, not pure black)
- Light:      `#FFFFFF`  - Light backgrounds and text on dark
- Mid Gray:   `#6B7280`  - Secondary elements
- Light Gray: `#EAEDF2`  - Subtle backgrounds

**Accent Colors:**

- EPG Yellow: `#FFEF10` - Primary accent
- EPG Navy Blue: `#002060` - Secondary accent
- EPG Emerald: `#10B981` - Tertiary accent

### Accent Usage Hierarchy

Do not distribute the three accents evenly. They are not interchangeable — each has a defined role and proportion. Apply them in this order of dominance:

1. **Navy `#002060` — the workhorse.** This is the default accent for structural emphasis: heading bars, primary buttons, dividers, table header rows, the primary data series in charts, and most non-text shapes. When in doubt, reach for navy.
2. **Emerald `#10B981` — secondary highlight.** Use for supporting elements: secondary buttons, positive/success states, secondary chart series, icons, and callouts. It complements navy without competing with it.
3. **Yellow `#FFEF10` — sparing pop only.** Reserve for a single focal highlight, an attention/CTA element, or a small graphic accent. Aim for no more than one yellow element per view, and keep it under roughly 10% of any colored area.

**Contrast rules (non-negotiable):**

- Yellow is a *fill* color, never text. Never place yellow text on a light background — it is effectively invisible.
- Text on yellow must be navy `#002060` or dark `#0A1A3F`.
- Text on navy must be light `#FAF9F5` (or yellow for a single emphasized word).
- Navy-on-white and navy-on-yellow both pass WCAG AA; yellow-on-white fails — avoid it entirely.

### Typography

- **Headings**: Raleway (with Arial fallback)
- **Body Text**: Inter (with system-ui / Arial fallback)
- **Monospace / code & technical data**: IBM Plex Mono (with Consolas / monospace fallback)
- **Note**: For best results, pre-install Raleway, Inter, and IBM Plex Mono. The skill falls back gracefully to system fonts when they are unavailable.

## Applying the Brand by Format

The colors, hierarchy, and typography above are universal. The sections below cover how to apply them in each artifact type.

### Presentations (PowerPoint / .pptx)

- Headings 24pt and larger: Raleway; body text: Inter; fall back to Arial.
- Apply colors via python-pptx's `RGBColor` class (RGB values for precise brand matching).
- Color non-text shapes using the accent hierarchy: navy dominant, emerald for secondary shapes, yellow for at most one focal accent per slide.
- Title slides and section dividers: navy background with light `#FAF9F5` text; a single yellow rule or shape for emphasis.

### Documents (Word / .docx, Google Docs)

- Map Heading styles to Raleway; map Normal/body to Inter; fall back to Arial / Georgia-class system fonts where needed.
- Heading text or rule lines: navy. Callout/info boxes: emerald fill with dark text. Yellow only as a highlight behind short phrases of dark text.
- Tables: navy header row with light text; light-gray `#e8e6dc` for zebra striping.

### Web (HTML / CSS)

Expose the brand as CSS custom properties and apply them via the hierarchy:

```css
:root {
  /* Accents */
  --epg-yellow:  #FFEF10;
  --epg-navy:    #002060;
  --epg-emerald: #10B981;

  /* Neutrals */
  --epg-dark:       #0A1A3F;
  --epg-light:      #FAF9F5;
  --epg-gray:       #6B7280;
  --epg-gray-light: #EAEDF2;

  /* Type */
  --epg-font-heading: 'Raleway', Arial, sans-serif;
  --epg-font-body:    'Inter', system-ui, Arial, sans-serif;
  --epg-font-mono:    'IBM Plex Mono', Consolas, monospace;
}
```

- Load fonts from Google Fonts (Raleway, Inter, IBM Plex Mono) via `<link>` or `@import`.
- Buttons: primary = navy background + light text; secondary = emerald; reserve yellow for a single CTA or badge, always with navy text.
- Links and interactive accents: navy default, emerald for hover/active or success states.
- Headings use `--epg-font-heading`; body and UI use `--epg-font-body`; code, logs, and protocol/technical data use `--epg-font-mono`.

## Font Handling

- Uses system-installed Raleway, Inter, and IBM Plex Mono when available.
- Provides automatic fallback to Arial (headings/body) and Consolas/monospace (code).
- No font installation strictly required — works with existing system fonts, but installing the brand fonts gives the intended look.
- Maintains text hierarchy, readability, and color fidelity across systems.