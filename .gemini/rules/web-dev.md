# Web Stack & Infrastructure Guidelines

## Architecture Overview
- **Documentation/Wiki Site (Public/Player Lore):** MKDocs (using `mkdocs-material` theme) reading directly from `/content/setting/`.
- **Commercial Site (Storefront):** Main marketplace (Shopify / Astro / Next.js) hosting digital PDF sales, product pages, and email leads.

## MKDocs Integration Rules
- Raw LegendKeeper exports in `/content/raw_export/` should be cleaned and output to `/content/setting/` for MKDocs consumption.
- Use standard Markdown callout boxes (`!!! info`, `!!! note`) for inline GM tips and player lore notes.
- Include a global top-bar link in `mkdocs.yml` pointing back to the main marketplace store.