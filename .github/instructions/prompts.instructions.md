---
applyTo: ".github/prompts/**/*.md,.github/instructions/**/*.md"
description: "Authoring rules for .prompt.md and .instructions.md files — enforces the canonical frontmatter schema and lean body style"
date: 2026-05-18T12:00:00.000Z
lastmod: 2026-05-18T12:00:00.000Z
---

# Prompt & Instruction Authoring

Files under `.github/prompts/` and `.github/instructions/` are read by GitHub Copilot, Cursor, Aider, Claude Code, and other AGENTS.md-aware tools. They must follow the canonical schema in [`.github/FRONTMATTER.md`](../FRONTMATTER.md).

## Frontmatter (non-negotiable)

**`.prompt.md`:**

```yaml
---
mode: agent
description: "<= 160 chars, double-quoted, one sentence, no trailing period"
tools: [optional, list]
date: YYYY-MM-DDTHH:MM:SS.000Z
lastmod: YYYY-MM-DDTHH:MM:SS.000Z
---
```

**`.instructions.md`:**

```yaml
---
applyTo: "glob1,glob2"            # comma-separated, no spaces
description: "<= 160 chars"
date: YYYY-MM-DDTHH:MM:SS.000Z
lastmod: YYYY-MM-DDTHH:MM:SS.000Z
---
```

## Body style — slash hard

- **Actionable rules only.** No motivational filler, no "in today's AI era" framing.
- **One canonical example per concept.** Delete the second example.
- **Bullets > prose.** If a rule fits on one line, make it one line.
- **Target ≤ 100 lines per file.** Split if you exceed it.
- **Cross-link, don't duplicate.** If `FRONTMATTER.md` already says it, link to it.

## File naming

- Prompts: `<slug>.prompt.md` → becomes `/<slug>` slash command in supported tools.
- Instructions: `<scope>.instructions.md` → auto-loaded when files match `applyTo`.
- One concern per file. If you're tempted to add an "or" to the filename, split it.

## `applyTo` rules

- Prefer narrow globs (`pages/_posts/**/*.md`) over `**/*`.
- Reserve `**/*` for genuinely repo-wide instructions (contributing, work).
- Comma-separated, no spaces: `"_includes/**,_layouts/**"`.
- Test with a real path before committing.

## On every edit

- [ ] Bump `lastmod` to today's date
- [ ] Re-verify `description` is ≤ 160 chars
- [ ] Run the validator snippet in `FRONTMATTER.md` if you added/removed files
- [ ] Cross-repo: if you change a pattern that exists in `zer0-mistakes` or `it-journey`, mirror the change
