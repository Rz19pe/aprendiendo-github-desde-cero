# AGENTS.md

## What this repo is

A learning/practice project ("Aprendiendo GitHub desde cero"). The entire project is a single self-contained static page: `dashboard.html` — a mock betting dashboard ("BetDash").

## Key facts for agents

- **No toolchain.** There is no `package.json`, build step, test suite, linter, or git repo. Do not try to install dependencies or run npm/pytest/etc. — there is nothing to run.
- **To preview:** open `dashboard.html` directly in a browser. No dev server needed.
- **Keep it single-file.** All CSS lives in the `<style>` block in `<head>`; there is no JavaScript. Do not split into separate `.css`/`.js` files or add frameworks unless the user explicitly asks.
- **UI text is Spanish** (`lang="es"`). Match that language for any copy you add or edit.
- **It's mock data.** Balances, matches, and odds are hardcoded placeholders — there is no backend or data source to wire up.
