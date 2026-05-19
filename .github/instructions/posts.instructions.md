---
applyTo: "pages/_posts/**/*.md"
description: "Blog post standards for bashconsultants.com — frontmatter, voice, and SEO rules for the _posts collection"
date: 2026-05-18T12:00:00.000Z
lastmod: 2026-05-18T12:00:00.000Z
---

# Blog Post Instructions

Posts live in `pages/_posts/` and are organized by subfolder (`corp/`, `erp/`, `muses/`, `tech/`). They render via the `article` or `news` layout.

> **Voice, audience, banned phrases, and universal checklist** → see [`content-style.instructions.md`](content-style.instructions.md). This file covers post-specific rules only.

## Subfolder routing

| Subfolder | Topic | Typical reader |
|---|---|---|
| `corp/` | Corporate IT, governance, vendor strategy | SMB owner / CFO |
| `erp/` | ERP, financial systems, QuickBooks-to-X migrations | Controller, operations manager |
| `muses/` | Opinion, industry commentary, longer-form | Mixed |
| `tech/` | How-tos, vendor walk-throughs, architecture notes | In-house IT lead |

If a post doesn't fit, default to `tech/` and revisit at next site audit.

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

## Post-specific structure

A typical post should follow this skeleton (skip sections that don't apply, don't pad):

1. **Hook** — 1–2 sentences naming the problem in the reader's language
2. **Why it matters now** — cost, risk, or opportunity, with a real number when you have one
3. **What we'd actually do** — the recommendation, in plain terms
4. **How it plays out** — phased approach, timeline ranges, what the reader's team has to do
5. **Watch-outs** — the 2–3 things that go wrong in practice
6. **Next step** — link to the relevant `/services/...` page or `/contact/`

## Hard don'ts

- Don't commit posts with `draft: true` to `main` — Pages will publish them.
- Don't reference internal URLs that don't exist; verify with the local build.
- Don't include literal API keys, even as examples — use `${env:VAR}` placeholders.
- Don't bump `date:` on edits — bump `lastmod:` instead.
- Don't write "thought leadership" posts with no recommendation or next step.

## Before commit

- [ ] Subfolder matches topic table above
- [ ] Universal checklist in `content-style.instructions.md` passes
- [ ] Post links to at least one service page or `/contact/`
- [ ] `lastmod` updated
- [ ] Build passes locally
