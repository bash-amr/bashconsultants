---
applyTo: "pages/_posts/**/*.md"
description: "Blog post standards for bashconsultants.com — frontmatter, voice, and SEO rules for the _posts collection"
date: 2026-05-18T12:00:00.000Z
lastmod: 2026-05-18T12:00:00.000Z
---

# Blog Post Instructions

Posts live in `pages/_posts/` and are organized by subfolder (`corp/`, `erp/`, `muses/`, `tech/`). They render via the `article` or `news` layout.

## Required frontmatter

```yaml
---
title: "Sentence-case title, no trailing period"
description: "120–155 chars. One sentence. Business outcome first, tech second."
author: "Amr Abdel-Motaleb"   # or a real contributor name
layout: article                # or "news" for the news index
date: YYYY-MM-DDTHH:MM:SS.000Z
lastmod: YYYY-MM-DDTHH:MM:SS.000Z
draft: false
categories: [Category]         # YAML list, never bare string
tags: [tag1, tag2]             # YAML list
preview: /images/previews/<slug>.png
---
```

## Filename

`YYYY-MM-DD-kebab-case-title.md` under the appropriate subfolder. Date in filename must match `date:` in frontmatter.

## Voice and content rules

- **Audience:** SMB owners, operators, and IT decision-makers in the Denver metro.
- **Lead with the business outcome**, follow with the technical mechanism.
- **No jargon without definition.** First use of an acronym: spell it out.
- **Cite costs and time savings concretely** when the topic warrants (e.g., "cuts month-end close from 5 days to 2"), never invent numbers.
- **No marketing fluff.** Skip phrases like "in today's fast-paced world", "leverage synergies", "unlock value".
- **One H1 only** (rendered from `title`). Body starts at H2.

## Hard don'ts

- Don't commit posts with `draft: true` to `main` — Pages will publish them.
- Don't reference internal URLs that don't exist; verify with `docker-compose exec jekyll bundle exec jekyll build`.
- Don't include literal API keys, even as examples — use `${env:VAR}` placeholders.
- Don't bump `date:` on edits — bump `lastmod:` instead.

## Before commit

- [ ] Frontmatter has all required fields
- [ ] `description` is 120–155 chars
- [ ] `categories` and `tags` are YAML lists
- [ ] `lastmod` updated
- [ ] Build passes locally
