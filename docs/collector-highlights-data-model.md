# Book product data model — Collector Highlights

Each highlighted card reads its actual Shopify product selected in the Theme Editor. Price, availability, featured image and URL use native Shopify fields, not manually typed values.

## Required to publish a real book
- Accurate title and edition/publisher identification.
- SKU for the physical unit or edition; ISBN in the variant barcode when applicable.
- Correct price and stock quantity at the fulfillment location.
- Photos of the actual copy for rare or collectible used inventory, including defects and signature/provenance if claimed.
- Real shipping weight, condition, and appropriate policies.

## Create two optional product metafields
Shopify Admin → Settings → Custom data → Products → Add definition:

1. **Book condition** — namespace/key `custom.book_condition`, type Single line text. Examples: Fine, Very Good, Good. Apply a consistent grading standard and give a full condition description on the product page.
2. **Edition details** — namespace/key `custom.edition_details`, type Single line text. Examples: `First printing · 1952` only if independently verified. Avoid asserting first edition, signature, or provenance without evidence.

The section renders these fields when present and gracefully omits them otherwise. If a book has different edition variants, each variant should carry its distinct barcode, SKU and price; don't use product-level edition claims to mislabel other variants. For valuable copies, prefer one product per individually documented physical copy.

## Merchandising principle
A featured product card uses a **View details** link instead of one-click checkout. Collectors should inspect condition, provenance, and edition photos before purchasing. The product page will be customized in a later phase.
