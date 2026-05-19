# AGENTS.md — AI Agent Guide for bashconsultants

> Cross-tool entry point for AI coding agents (GitHub Copilot, Codex, Cursor, Aider, Claude Code, …). Follows the [agents.md](https://agents.md/) convention.

## Project Snapshot

Dual-purpose repository:

1. **Jekyll site** (root) — `bashconsultants.com` marketing/content site, GitHub Pages deploy on push to `main`, uses `jekyll-theme-zer0` remote theme.
2. **VS Code extension** (`extension/`) — "Prompt Orchestrator", TypeScript + esbuild, self-contained sub-project.

Default dev environment: Docker Compose for the Jekyll site (`docker-compose up`); `npm` inside `extension/` for the extension.

For the full overview see [`.github/copilot-instructions.md`](./.github/copilot-instructions.md).

## Where Agent Guidance Lives

| Layer | Location | When to read |
|---|---|---|
| Cross-tool entry | `AGENTS.md` (this file) | Always first |
| Project Copilot instructions | `.github/copilot-instructions.md` | Always second |
| Canonical frontmatter schema | `.github/FRONTMATTER.md` | When editing any `.prompt.md` or `.instructions.md` |
| Reusable prompts | `.github/prompts/*.prompt.md` | When asked to run a multi-step task that matches a prompt |
| Workflows | `.github/workflows/` | When changing CI |

## Reusable Prompts

| Task | Prompt |
|---|---|
| Full commit + push + deploy workflow | `.github/prompts/commit-publish.prompt.md` |
| Review an article for structure / SEO | `.github/prompts/article-review.prompt.md` |
| Generate documentation | `.github/prompts/documentation.prompt.md` |
| Implement / refactor code | `.github/prompts/code-implementation.prompt.md`, `code-refactoring.prompt.md` |
| Debug an issue | `.github/prompts/debugging.prompt.md` |
| Generate tests | `.github/prompts/test-generation.prompt.md` |
| System design / requirements | `.github/prompts/system-design.prompt.md`, `requirements-analysis.prompt.md` |
| Prompt engineering | `.github/prompts/prompt-engineering.prompt.md` |

## Essential Commands

```bash
# Jekyll site
docker-compose up                                          # Start dev server
docker-compose exec jekyll bundle exec jekyll build \
  --config '_config.yml,_config_dev.yml'                   # Validate build
docker-compose down

# Extension
cd extension && npm install
cd extension && npm run lint && npm run compile

# Publish
# Use /commit-publish prompt — direct-to-main triggers Pages deploy
```

## Operating Rules

1. **Minimal, surgical changes.** Match existing style. Don't refactor adjacent code.
2. **Validate before declaring done.** Jekyll changes → run the Docker build. Extension changes → `npm run lint && npm run compile`.
3. **Conventional commits**: `<type>(<scope>): <subject>`.
4. **Update `CHANGELOG.md`** for user-visible changes (add to `[Unreleased]`).
5. **No secrets.** Refuse to commit literal `ghp_*`, `sk-*`, `AKIA*`.
6. **Don't mix Jekyll and extension changes** in one commit.
7. **Don't commit** `_site/`, `node_modules/`, `vendor/`.

---

_Keep this file short — push detail into `.github/copilot-instructions.md` and `.github/prompts/`._
