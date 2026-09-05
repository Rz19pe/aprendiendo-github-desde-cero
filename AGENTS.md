# AGENTS.md

## What this repo is

A learning/practice project ("Aprendiendo GitHub desde cero"). The main content is a single self-contained static page: `dashboard.html` — a mock betting dashboard ("BetDash").

## Repo layout

- `dashboard.html` — the mock dashboard (self-contained: CSS in `<style>` block, no JS).
- `CHEATSHEET.md` — Spanish reference of the Git/GitHub commands learned in this project.
- `.gitignore` — protects secret files (e.g. `token.txt`) from being committed.

## Git workflow

- **It is a git repo.** Branch `main`, remote `origin` → GitHub (`Rz19pe/aprendiendo-github-desde-cero`). Push/pull directly against `main`.
- **Commit messages are written in Spanish** (e.g. "Agrego evento de tenis"). Match that convention.
- **Never commit secret files** (tokens, credentials, `.dmp` dumps). They belong in `.gitignore`.

## Key facts for agents

- **No toolchain.** No `package.json`, build step, test suite, or linter. Do not try to install dependencies or run npm/pytest/etc.
- **To preview:** open `dashboard.html` directly in a browser. No dev server needed.
- **Keep it single-file.** All CSS lives in the `<style>` block in `<head>`; there is no JavaScript. Do not split into separate `.css`/`.js` files or add frameworks unless the user explicitly asks.
- **UI text is Spanish** (`lang="es"`). Match that language for any copy you add or edit.
- **It's mock data.** Balances, matches, and odds are hardcoded placeholders — there is no backend or data source to wire up.
