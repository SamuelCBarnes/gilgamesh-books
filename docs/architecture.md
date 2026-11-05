# Gilgamesh Books — Architecture

**Current state:** Shopify store + Dawn-based CLI development preview. The items marked *planned* below are proposed architecture rather than deployed features.

## System boundaries

- **Shopify:** Commerce platform; products, variants, inventory, locations, payments, checkout, orders, and fulfillment live in Shopify Admin.
- **Theme:** Online Store 2.0 Liquid templates, sections, snippets, CSS, progressive JavaScript, localization, and theme settings.
- **GitHub:** Public, version-controlled source and review history; no credentials or customer data.
- **Shopify CLI:** Authenticated local preview of an unpublished development theme.
- **Future:** Analytics integrations and optional headless Storefront API exploration; neither is required for the core store.

## Theme structure

Dawn 16.1.1 serves as the baseline. Use reusable, merchant-editable sections and JSON templates. Preserve native product, cart, search and accessibility functionality. Prefer unique `gilgamesh-` CSS and file naming for our additions.

Planned custom components (not yet written):

```text
sections/gilgamesh-hero.liquid
sections/gilgamesh-editorial-feature.liquid
snippets/gilgamesh-book-metadata.liquid
snippets/gilgamesh-author-profile.liquid
assets/gilgamesh.css
```

## Catalog model

Gilgamesh Books owns and ships physical stock. Each stocked edition needs an accurate SKU, ISBN-13/barcode where applicable, format, condition, inventory quantity, acquisition cost, selling price, shipping weight, and shipping location. Variant-level stock and pricing are mandatory when using variants for different bindings/editions. Separate product records are appropriate for substantially different editions.

Proposed metadata definitions, to validate in Shopify Admin before creation:

| Field | Type | Usage |
| --- | --- | --- |
| `custom.isbn_13` | Single-line text | Editorial access; canonical barcode also on variant |
| `custom.publication_year` | Integer | Edition publication year |
| `custom.page_count` | Integer | Length |
| `custom.binding` | Single-line text | Format, if not a variant option |
| `custom.translator` | Single-line text | Translator |
| `custom.author` | Metaobject reference | Reusable author profile |
| `custom.editorial_note` | Rich text | Curatorial recommendation |

**Planned author metaobject:** name, biography, portrait (rights cleared), historical period, and editorial introduction. Prefer Shopify-native product properties over duplicate metafields.

## Analytics and experimentation plan

1. Define e-commerce event names, parameters, and data ownership.
2. Configure supported Shopify/Google integrations and customer-event/web-pixel paths; verify checkout limitations rather than assuming legacy GTM scripts work everywhere.
3. Debug `view_item`, `add_to_cart`, `begin_checkout`, and `purchase`, including item identifiers, value, currency, and deduplication.
4. Evaluate apps on permissions, recurring cost, customer experience, performance impact, support, and native alternatives.
5. Document conversion hypotheses and experiment outcomes only when sufficient real traffic allows responsible interpretation.

## SEO, accessibility and speed

Semantic headings, keyboard operation, focus indicators, accurate product metadata, edition-specific details, canonical URLs, breadcrumbs, valid structured data, correctly sized images, and minimal JavaScript. Measure representative page templates with repeatable Lighthouse tests and use real-user Core Web Vitals when available. No unmeasured score or uplift claims.

## Security and operational boundaries

The repo is public: never commit secrets, API tokens, customer records, personal shipping addresses, or confidential supplier pricing. Review `config/settings_data.json` and new public content before commit. Shopify owns payment processing; the theme must not collect card data.

## Delivery

Feature branch → reviewed pull request into `develop` → unpublished Shopify theme QA → review/promotion to `main` → explicit live publish. Repository changes alone do not publish a storefront.
