---
applyTo: "extension/**"
description: "VS Code Prompt Orchestrator extension — TypeScript, esbuild, and ESLint conventions for the extension/ sub-project"
date: 2026-05-18T12:00:00.000Z
lastmod: 2026-05-18T12:00:00.000Z
---

# Extension Development Instructions

The `extension/` directory is a **self-contained VS Code extension** ("Prompt Orchestrator") that runs AI workflows defined in `.github/prompts/`. It is independent of the Jekyll site.

## Stack

- TypeScript (strict mode per `tsconfig.json`)
- Bundled with esbuild (`esbuild.js`)
- ESLint flat config (`eslint.config.mjs`)
- VS Code Extension API

## Workflow

```bash
cd extension
npm install
npm run compile        # one-shot build
npm run watch          # esbuild watch + tsc --noEmit watch
npm run lint           # ESLint
npm run test           # vscode-test runner
```

## Rules

1. **Don't refactor existing source unless explicitly asked.** This sub-project is functional; surgical changes only.
2. **Activation events:** declared in `package.json`. Keep them narrow — never `*`.
3. **Commands:** must be declared in both `package.json` `contributes.commands` AND registered in `extension.ts`. Mismatches cause silent failures.
4. **Async/await everywhere.** No `.then()` chains in new code.
5. **No `console.log`** in shipped code — use `vscode.window.createOutputChannel`.
6. **Bundle stays small.** Avoid dependencies that aren't dev-only; prefer `vscode` API + Node built-ins.

## Reading prompts from disk

The extension consumes `.github/prompts/*.prompt.md` files. When changing how prompts are parsed:

- Honor the canonical frontmatter schema in `.github/FRONTMATTER.md` (`mode`, `description`, `tools`, `date`, `lastmod`).
- Gracefully skip files with malformed frontmatter; log to the output channel, never throw at activation.

## Packaging

```bash
cd extension
npx vsce package       # produces a .vsix
```

Do **not** publish to the Marketplace from a local machine without coordinating — this is currently a private workflow tool.

## Before commit

- [ ] `npm run lint` passes
- [ ] `npm run compile` succeeds with no TS errors
- [ ] `package.json` `engines.vscode` not lowered
- [ ] No new runtime dependencies without justification
- [ ] Commit scope is `extension`: `feat(extension): …`, `fix(extension): …`
