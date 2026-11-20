# Almakhtoom.com — D2C Shopify Storefront Architecture & CRO Case Study

**Brand:** Ar Raheequl Makhtoom (*"The Sealed Nectar"*)  
**Category:** Direct-to-Consumer (D2C) Specialty Foods — Kashmiri Saffron, Almonds & Walnuts  
**Platform & Theme:** Shopify Online Store 2.0 (`Dawn v3.0.0`)  
**Status:** Pre-Launch Architecture & Conversion Rate Optimization (CRO) Case Study

---

## 1. Business Context & Brand Positioning
**Ar Raheequl Makhtoom** represents a multigenerational Kashmiri agricultural family bringing authentic, farm-direct **Pampore Saffron, Kashmiri Almonds, and Organic Walnuts** directly to domestic and international buyers.

* **Target Audience:** Domestic specialty food buyers across India and cross-border consumers in the GCC (UAE, Saudi Arabia, Qatar) seeking verified origin and purity.
* **Core Value Proposition:** Farm-to-table authenticity, transparent consignment weight specifications, and direct grower pricing without multi-tier middleman markups.

---

## 2. Technical & Storefront Architecture
Built on Shopify's lightweight **Online Store 2.0 (`Dawn v3.0.0`)** modular JSON template architecture for fast mobile load speeds and clean merchandising control:

* **Modular JSON Templates (`templates/`):**
  * `index.json`: Full-width hero banner with farm photography (`860808-Saffronfarm-01-IMG_7707-2`), brand story rich-text block linking to `/pages/about-us`, 8-item Featured Collection grid with secondary hover imagery, multimedia collage, and video storytelling.
  * `product.json`: Sticky product information layout with button-style variant pickers, dynamic checkout buttons, custom collapsible spec tabs (including packed consignment weight transparency), automated `product-recommendations`, and **Shopify Product Reviews** app blocks.
  * `password.json`: Pre-launch lead-capture landing page combining an email signup banner with brand heritage storytelling to build an early-access subscriber list prior to public launch.
* **Cross-Border Localization (`config/settings_data.json`):** Enabled country/currency and language selectors in the footer alongside sticky header navigation (`middle-left` logo layout) to support both Indian and GCC buyers.
* **Promotional & App Integrations (`snippets/`):** Integrated **Hextom Quick Announcement Bar** (`hextom_qab_main.liquid`) supporting product-tag and customer-segment (order count / total spend) targeting rules.

---

## 3. Code-Level CRO & UX Audit (Optimization Roadmap)
Reviewing the exported theme JSON and Liquid templates identified six targeted improvements to maximize conversion rate prior to scaling paid traffic:

| # | Audit Area | File Reference | Finding | Recommended CRO Fix |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **Top-of-Funnel Link Leak** | `config/settings_data.json` | Announcement bar links to an external Google search URL instead of an internal collection or shipping offer. | Route CTA internally to `/collections/all` with a clear free-shipping threshold or first-order incentive. |
| **2** | **Above-the-Fold SEO & H1** | `templates/index.json` | Hero banner leaves `heading` blank and contains a copy typo (`"sarching"`). | Add keyword-rich H1 (*"Farm-Direct Kashmiri Mongra Saffron & Heirloom Dry Fruits"*) to improve 3-second clarity and organic search relevance. |
| **3** | **Dynamic Product Metafields** | `templates/product.json` | *"Overall consignment weight after packing"* accordion hardcodes `3/4 kg` (`organic-walnut`) across the shared product template. | Replace hardcoded HTML with a dynamic product metafield (`{{ product.metafields.custom.packed_weight }}`) so each SKU displays accurate weight. |
| **4** | **Social Proof Placement** | `templates/product.json` | Star-rating app block sits at the bottom of the product template below full reviews. | Move the star-rating badge directly beneath the product title/price above the fold to reinforce trust before the Add-to-Cart CTA. |
| **5** | **Placeholder Boilerplate** | `templates/index.json`, `templates/product.json` | Default Dawn `"Column"` and `"Image with text"` blocks remain unconfigured below the fold. | Replace boilerplate text with GI-tag authenticity proof, lab-tested crocin grade details, and harvest batch traceability. |
| **6** | **Footer Trust & Social Links** | `config/settings_data.json` | `show_social` is disabled and `"About us"` / `"Get in touch"` sit under a `"Products"` footer heading. | Enable verified social channels, rename the footer column to `"Company"`, and surface shipping/refund policies clearly. |

---

## 4. Repository Structure
```text
├── assets/       # Theme CSS stylesheets & vanilla JS modules (cart, facets, predictive search)
├── config/       # Global theme settings, typography, color schemes & header/footer state
├── layout/       # Master Liquid shells (theme.liquid, password.liquid)
├── locales/      # Multi-language translation schemas
├── sections/     # Reusable OS 2.0 Liquid sections (hero, product grid, collapsible tabs)
├── snippets/     # Modular Liquid components (product cards, price, Hextom QAB integration)
└── templates/    # JSON page templates (index, product, collection, cart, password, customer)
