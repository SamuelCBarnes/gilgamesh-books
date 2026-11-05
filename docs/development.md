# Gilgamesh Books — Development Guide

## Requirements

- Git, Node.js compatible with the installed Shopify CLI, and VS Code.
- `npm install -g @shopify/cli@latest`.
- A Shopify account with permission to develop themes.

## Start a local preview

```powershell
git clone https://github.com/SamuelCBarnes/gilgamesh-books.git
cd gilgamesh-books
git switch develop
shopify theme dev --store YOUR-STORE.myshopify.com
```

The CLI may require Shopify authentication and the **storefront password** (different from the Shopify Admin account password). Keep the CLI terminal open while editing. Development previews are unpublished.

## Git workflow

- `main`: stable, reviewed code.
- `develop`: integration and staged work.
- `feature/<topic>`: scoped change branched from `develop`.
- `fix/<topic>`: issue correction.

```powershell
git switch develop
git pull --ff-only origin develop
git switch -c feature/book-metadata
# edit and test
shopify theme check
git add .
git commit -m "feat: add book metadata component"
git push -u origin feature/book-metadata
```

Open a PR targeting `develop`. Include the problem solved, design decisions, screenshots if applicable, QA results, and any performance/accessibility concerns. Promote reviewed changes to `main` through a separate PR. Do not claim independent peer review if self-reviewed.

## Review checklist

1. Run `shopify theme check`; distinguish baseline Dawn warnings from new issues.
2. Test all affected templates on desktop and narrow mobile widths.
3. Check keyboard/focus behavior and semantic markup.
4. Confirm product variants, stock indicators, add-to-cart, pricing, and shipping messaging.
5. Re-run relevant performance tests when adding scripts or images.
6. Inspect changed files for secrets, private customer information, supplier terms, and accidentally added theme-editor data.

## Deployment

`shopify theme dev` makes an unpublished development preview. Deploy to a separate **unpublished** review theme before any live publication. Verify settings, product flows and checkout using Shopify-supported test transactions. Publishing must be intentional and recorded.

A Shopify GitHub integration may be introduced later; if so, explicitly document each connected branch and theme to prevent conflicting deployments.

## Dawn upstream

This repository is based on Shopify Dawn. The original local environment kept Shopify's source as a `dawn-upstream` remote. New clones may add it:

```powershell
git remote add dawn-upstream https://github.com/Shopify/dawn.git
git fetch dawn-upstream
```

Do not blindly merge upstream changes. Compare release notes, tests and local modifications first. Retain Dawn's `LICENSE.md` and notices.
