# Gilgamesh Books

**An inventory-owned independent bookstore and a public Shopify engineering case study.**

Gilgamesh Books is a real e-commerce project focused on thoughtfully curated literature, mythology, philosophy, and history. Its second purpose is to document hands-on Shopify engineering and e-commerce operations: Liquid theme development, structured catalog data, inventory management, analytics, performance, SEO, merchandising, and conversion optimization.

> **Status — November 2026:** Foundation in progress. The Shopify store, local Dawn-based theme preview, Shopify CLI connection, and public source repository are established. Custom book components, live inventory, analytics integrations, and measured improvements are **planned, not yet completed**.

## Technology

| Area | Approach |
| --- | --- |
| Storefront | Shopify Online Store 2.0, Liquid, JSON templates, CSS, JavaScript |
| Base theme | [Shopify Dawn](https://github.com/Shopify/dawn), starting from Dawn 16.1.1 |
| Development | VS Code, GitHub, Shopify CLI |
| Commerce | Shopify products, checkout, inventory, orders, and fulfillment |
| Book data | Edition-specific SKUs and ISBNs; planned metafields and author metaobjects |
| Quality | Shopify Theme Check, accessibility checks; planned Lighthouse audits |
| Analytics | Planned Shopify/GA4 event validation and conversion research |

**Website:** [gilgameshbooks.com](https://gilgameshbooks.com) (public storefront launch not yet verified)  
**Repository:** [SamuelCBarnes/gilgamesh-books](https://github.com/SamuelCBarnes/gilgamesh-books)

## What we're building

- A curated bookstore organized around Ancient Worlds & Mythology, Philosophy & Ideas, Literary Classics, and History & Civilization.
- Mobile-first, accessible Shopify Liquid storefront components and editorial merchandising.
- Book product pages with accurate edition, ISBN, format, author, condition, and inventory information.
- Author profiles and reading guides based on Shopify's structured content features.
- A measurable e-commerce funnel with documented event validation, technical audits, and responsible experimentation.

## Project documentation

- [Architecture](docs/architecture.md) — systems, theme patterns, book data, and integration boundaries.
- [Development](docs/development.md) — local setup, Git workflow, QA, and release process.
- [Roadmap](docs/roadmap.md) — milestones and objective exit criteria.

## Local setup

Prerequisites: Git, compatible Node.js, Shopify CLI, and access to a Shopify store for theme development.

```powershell
git clone https://github.com/SamuelCBarnes/gilgamesh-books.git
cd gilgamesh-books
git switch develop
npm install -g @shopify/cli@latest
shopify theme dev --store YOUR-STORE.myshopify.com
```

Use `shopify theme check` to validate theme source. `shopify theme dev` runs an unpublished preview; it does **not** publish the live storefront.

## Engineering principles

Use Shopify-native commerce and server-rendered Liquid where possible; introduce client JavaScript or third-party apps only for documented needs. Use focused feature branches and pull requests. Record before/after comparisons with methods and evidence. Do not report hypothetical results as actual performance or revenue improvements.

## Origin and attribution

This project **starts from [Shopify Dawn](https://github.com/Shopify/dawn)**. The inherited Dawn code and Git history are not presented as original Gilgamesh Books work. Shopify's existing [LICENSE.md](LICENSE.md), copyright notices, and attribution are retained. New Gilgamesh-specific work will be visible in subsequent commits and pull requests.

Maintained by [SamuelCBarnes](https://github.com/SamuelCBarnes).
