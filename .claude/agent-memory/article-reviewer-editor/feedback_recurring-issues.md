---
name: feedback-recurring-issues
description: Recurring editorial issues observed across bashconsultants service pages
metadata:
  type: project
---

Recurring issues found in bashconsultants content review (first observed on `pages/_services/index.md`, 2026-06-21):

**Why:** These patterns repeat across the service pages and the house style guide forbids them, so they are worth checking on every review.

**How to apply — check each review for:**
1. **Title-case H2s** where the style guide mandates sentence case (e.g. "AI Solutions and Intelligent Automation" should be "AI solutions and intelligent automation"). The same page often mixes title case and sentence case ("How we work", "Get started"), so flag for internal consistency too. Sibling pages (cloud/data/dev/erp/fintech/strat) all violate this — pre-existing, not yet fixed.
2. **Undefined acronyms on first use** (OCR, ETL, KPI, ARM) — guide requires spell-out on first mention.
3. **FAQ duplication** — `faq_items` in frontmatter (drives JSON-LD per commit history) AND a body "Frequently asked questions" section can repeat near-verbatim, risking duplicate content. Decide one canonical home or differentiate.
4. **Description nudging over 155 chars** (160 is hard limit).
5. **Multiple CTAs** vs the "one CTA per page" rule — defensible on a hub page but note the tradeoff.

See [[reference-content-style]] for the authoritative rules.
