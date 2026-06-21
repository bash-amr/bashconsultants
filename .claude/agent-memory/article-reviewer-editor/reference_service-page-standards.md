---
name: reference-service-page-standards
description: Service-page frontmatter schema, required structure, and SEO limits from services.instructions.md
metadata:
  type: reference
---

Source: `.github/instructions/services.instructions.md` (applyTo pages/_services/**/*.md).

**Required frontmatter:** title, sub-title, description (120–155 chars), preview (SVG preferred, /assets/images/<service>.svg), snippet (1-sentence card pitch), author "Amr Abdel-Motaleb", layout default, keywords (5–10), tags, lastmod (ISO-8601 with .000Z). Content pages also commonly carry: categories, faq_items, slug, permalink, draft.

**Page structure order:** headline (H1 from title) -> problem statement -> what we do (3–6 bullets) -> who it's for (industry example) -> approach (discovery->plan->deliver->support) -> outcomes (ranges) -> tech stack/partners -> CTA to /contact/.

**Rules:** concrete > abstract; name the buying signal; no competitor bashing; never publish fixed prices (ranges/"starting at" only); vendor marks with attribution.

**Hub (index.md):** when adding a service, create the sub-page, update hub cards, update `_data/navigation/`.
