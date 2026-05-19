---
applyTo: "pages/_services/**/*.md"
description: "Service page standards for bashconsultants.com — frontmatter, structure, and conversion-focused content rules"
date: 2026-05-18T12:00:00.000Z
lastmod: 2026-05-18T12:00:00.000Z
---

# Service Page Instructions

Service pages live in `pages/_services/` (`cloud.md`, `data.md`, `dev.md`, `erp.md`, `fintech.md`, `strat.md`) plus the `index.md` hub. These are the primary conversion pages for the site.

## Required frontmatter

```yaml
---
title: "Service Name"
sub-title: "Short value-prop tagline"
description: "120–155 chars. What you do + who it's for + outcome."
preview: /assets/images/<service>.svg
snippet: "1-sentence pitch shown in service cards on the hub page."
author: "Amr Abdel-Motaleb"
layout: default
keywords:                # YAML list — used for SEO
  - Primary Keyword
  - Secondary Keyword
tags:                    # YAML list — used for cross-linking
  - Tag1
  - Tag2
lastmod: YYYY-MM-DDTHH:MM:SS.000Z
---
```

## Page structure

Each service page should include, in order:

1. **Headline** (H1 via `title`) + sub-headline
2. **Problem statement** — the pain SMBs feel in this domain (1–2 paragraphs)
3. **What we do** — 3–6 concrete offerings as a bulleted list
4. **Approach / methodology** — how we engage (discovery → plan → deliver)
5. **Outcomes** — measurable results (uptime, cost reduction, time-to-market)
6. **Tech stack / partners** — vendors and platforms we work with
7. **Call to action** — link to `/contact/` or scheduling link

## Content rules

- **Concrete > abstract.** "Migrate your on-prem SQL Server to Azure SQL in 6–8 weeks" beats "leverage cloud transformation".
- **No competitor bashing.** Compare positively to vendor offerings, not other consultancies.
- **Pricing:** never publish fixed prices; use ranges or "starting at" only when accurate.
- **Logos and trademarks:** use vendor marks only with attribution; SVGs in `/assets/images/`.

## Hub page (`index.md`)

When adding a new service:
1. Create `pages/_services/<slug>.md` with full content
2. Update `pages/_services/index.md` cards to include the new service
3. Update site navigation in `_data/navigation/` if applicable

## Before commit

- [ ] `description` is 120–155 chars and lead with outcome
- [ ] `snippet` ≤ 140 chars (renders in card UI)
- [ ] At least one call-to-action linking to `/contact/`
- [ ] No fixed pricing claims
- [ ] Build passes locally
