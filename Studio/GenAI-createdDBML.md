# GenAI-created DBML

This features allows to instantly generate models, polyglot or physical, then edit and enrich them, plus integrate suggestions from GenAI. By integrating AI-generated diagrams with Hackolade Studio’s intuitive modeling, teams can efficiently develop and refine their data models, enhancing collaboration and accelerating the development cycle.

&nbsp;

## DBML

[DBML](<https://dbml.dbdiagram.io/home> "target=\"_blank\"") (Database Markup Language) is an open-source DSL (a small, special‑purpose language designed for one particular domain, in this case **database schemas**) designed to define and document database schemas and structures. It is designed to be simple, consistent and highly-readable. Its [playground](<https://dbdiagram.io/d> "target=\"_blank\"") also allows to create simple diagrams, although far from the professional level and capabilities of Hackolade Studio.

&nbsp;

DBML‑style DSLs are especially good for bi-directional exchanges of schemas with Generative AI because they combine compactness, simplicity, and structure -- exactly what an LLM needs to understand and rewrite database layouts reliably. It is text‑only, declarative, and close to “pseudo‑code”. A DBML DSL cleanly separates intent (the schema) from implementation (SQL for a specific DB).

&nbsp;

ChatGPT, Claude, CoPilot, Gemini and other generative AI models find it easier to generate ER diagrams in DBML compared to SQL DDL or traditional modeling standards because DBML uses a simple, human-readable syntax that closely aligns with natural language. Its declarative and visual style allows AI to map conceptual relationships directly into diagram code without needing strict adherence to data types, constraints, or database-specific rules. Unlike DDLs, which requires precision and contextual knowledge of database engines, DBML is more forgiving and doesn’t require runtime validation. This makes it an ideal format for GenAI to produce quickly and accurately from natural prompts.

&nbsp;

Compared with [Mermaid ER code](<https://www.mermaidchart.com/> "target=\"_blank\""), DBML‑style DSLs are better for exchanging schemas with GenAI mainly because they are more “schema‑oriented” and less “diagram‑oriented,” which makes them easier for an AI to parse, reason about, and transform. Mermaid ER syntax is designed to describe graphics and layout: boxes, lines, cardinality labels, and sometimes notes while DBML is purely about tables, columns, types, constraints, and relationships; it does not care how the diagram is rendered. That makes it much closer to the “true” data model an AI needs to understand. DBML can cleanly encode things like pk, not null, indexes, enums, and extensions (e.g., dbdiagram project‑level notes), which are useful for AI‑driven schema evolution and SQL generation.

&nbsp;

DBML works well for **tables, columns, and relational constraints, but l**ike Mermaid however, it does not define “types” with nested fields or array‑of‑objects structures the way you can in JSON‑schema or a document‑aware modeling language. DBML is not a logical‑type DSL for subobjects or arrays; it delegates that complexity to the database‑level JSON/array types and to external schemas.

&nbsp;

## Prompt

You may create prompts using entire business requirements, and fine-tune the prompt until the result suits your needs. For the purpose of this documentation page, here is a super simple prompt example:

&nbsp;

```text
Generate a physical ERD in DBML for an e-commerce application running on PostgreSQL, full with tables, columns, data types, relationships.
```

&nbsp;

With some LLMs, it might be required to specify:\
`Provide syntactically correct code so it can be accepted without errors by `[`https://dbml.dbdiagram.io/home`](<https://dbml.dbdiagram.io/home> "target=\"_blank\"")

&nbsp;

> [!NOTE]
> Results vary greatly depending on the LLM and the prompt.

&nbsp;

Here is a simple example response from Claude Sonnet 4.6 for the above prompt:

&nbsp;

```javascript
// =====================================================
// E-Commerce Application - Entity Relationship Diagram
// =====================================================

Project ecommerce {
  database_type: 'PostgreSQL'
  Note: 'E-commerce platform schema covering customers, catalog, orders, payments, shipping, and reviews'
}

Table customers {
  customer_id   bigint      [pk, increment, note: 'Unique customer identifier']
  email         varchar(255) [unique, not null, note: 'Login email, must be unique']
  password_hash varchar(255) [not null, note: 'Hashed password — never store plaintext']
  first_name    varchar(100) [not null, note: 'Customer given name']
  last_name     varchar(100) [not null, note: 'Customer family name']
  phone         varchar(30)  [note: 'E.164 formatted phone number']
  date_of_birth date         [note: 'Used for age-restricted products and marketing']
  is_active     boolean     [not null, default: true, note: 'Soft-disable flag']
  created_at    timestamp   [not null, default: `now()`, note: 'Account creation timestamp']
  updated_at    timestamp   [not null, default: `now()`, note: 'Last profile modification']

  Indexes {
    email [unique]
    (last_name, first_name)
  }

   Note: 'Registered shoppers and guest accounts'
}

Table addresses {
  address_id   bigint      [pk, increment, note: 'Unique address identifier']
  customer_id  bigint      [not null, ref: > customers.customer_id, note: 'Owner of the address']
  address_type varchar(20) [not null, note: 'billing or shipping']
  line1        varchar(255) [not null, note: 'Street address line 1']
  line2        varchar(255) [note: 'Apartment, suite, etc.']
  city         varchar(100) [not null, note: 'City or locality']
  state        varchar(100) [note: 'State, province, or region']
  postal_code  varchar(20)  [not null, note: 'ZIP or postal code']
  country_code char(2)     [not null, note: 'ISO 3166-1 alpha-2 country code']
  is_default   boolean     [not null, default: false, note: 'Default address for this type']
  created_at   timestamp   [not null, default: `now()`]

  Note: 'Shipping and billing addresses linked to customers'
}

Table categories {
  category_id        bigint      [pk, increment, note: 'Unique category identifier']
  parent_category_id bigint      [ref: > categories.category_id, note: 'Parent category for hierarchy; null for root']
  name               varchar(150) [not null, note: 'Display name of the category']
  slug               varchar(150) [unique, not null, note: 'URL-friendly identifier']
  description        text        [note: 'Long-form category description']
  sort_order         int         [not null, default: 0, note: 'Display ordering within parent']
  is_active          boolean     [not null, default: true]

  Note: 'Hierarchical product categories (self-referential)'
}

Table brands {
  brand_id    bigint      [pk, increment]
  name        varchar(150) [unique, not null, note: 'Brand display name']
  slug        varchar(150) [unique, not null, note: 'URL-friendly brand identifier']
  description text        [note: 'Brand story or bio']
  logo_url    varchar(500) [note: 'CDN URL for brand logo']
  Note: 'Suppliers or brands providing products'
}

Table products {
  product_id       bigint        [pk, increment, note: 'Unique product identifier']
  brand_id         bigint        [ref: > brands.brand_id, note: 'Associated brand']
  category_id      bigint        [not null, ref: > categories.category_id, note: 'Primary category']
  sku              varchar(64)   [unique, not null, note: 'Stock keeping unit']
  name             varchar(255)  [not null, note: 'Product display name']
  slug             varchar(255)  [unique, not null, note: 'URL-friendly product identifier']
  description      text          [note: 'Full product description, supports markdown']
  short_description varchar(500) [note: 'Summary used in listings']
  base_price       numeric(12,2) [not null, note: 'List price in store base currency']
  currency_code    char(3)       [not null, default: 'USD', note: 'ISO 4217 currency code']
  weight_grams     int           [note: 'Shipping weight in grams']
  is_active        boolean       [not null, default: true, note: 'Visible in storefront']
  created_at       timestamp     [not null, default: `now()`]
  updated_at       timestamp     [not null, default: `now()`]

  Indexes {
    sku [unique]
    (category_id, is_active)
    name
  }
  Note: 'Master product catalog'
}

Table product_variants {
  variant_id      bigint        [pk, increment, note: 'Unique variant identifier']
  product_id      bigint        [not null, ref: > products.product_id, note: 'Parent product']
  variant_sku     varchar(64)   [unique, not null, note: 'Variant-level SKU']
  variant_name    varchar(255)  [not null, note: 'e.g. "Red / Large"']
  price_override  numeric(12,2) [note: 'If set, overrides product.base_price']
  stock_quantity  int           [not null, default: 0, note: 'On-hand inventory count']
  weight_grams    int           [note: 'Variant-specific shipping weight']
  is_active       boolean       [not null, default: true]

  Note: 'Product variants (size, color, etc.) with their own stock and price'
}

Table product_images {
  image_id    bigint       [pk, increment]
  product_id  bigint       [not null, ref: > products.product_id, note: 'Product this image belongs to']
  variant_id  bigint       [ref: > product_variants.variant_id, note: 'Optional variant-specific image']
  url         varchar(500) [not null, note: 'CDN URL of the image']
  alt_text    varchar(255) [note: 'Accessibility alt text']
  sort_order  int          [not null, default: 0, note: 'Display ordering in gallery']
  is_primary  boolean      [not null, default: false, note: 'Hero image flag']

  Note: 'Product images, ordered for galleries'
}

Table carts {
  cart_id     bigint    [pk, increment]
  customer_id bigint    [ref: > customers.customer_id, note: 'Owning customer; null for guest carts']
  session_id  varchar(100) [note: 'Session key for guest carts']
  created_at  timestamp [not null, default: `now()`]
  updated_at  timestamp [not null, default: `now()`]

  Note: 'Shopping cart header (one open cart per customer)'
}

Table cart_items {
  cart_item_id bigint        [pk, increment]
  cart_id      bigint        [not null, ref: > carts.cart_id, note: 'Parent cart']
  variant_id   bigint        [not null, ref: > product_variants.variant_id, note: 'Selected variant']
  quantity     int           [not null, default: 1, note: 'Quantity in cart']
  unit_price   numeric(12,2) [not null, note: 'Price captured at time of add-to-cart']
  added_at     timestamp     [not null, default: `now()`]

  Note: 'Line items inside a shopping cart'
}

Table orders {
  order_id            bigint        [pk, increment, note: 'Unique order identifier']
  customer_id         bigint        [not null, ref: > customers.customer_id, note: 'Purchasing customer']
  order_number        varchar(32)   [unique, not null, note: 'Human-readable order reference']
  status              varchar(30)   [not null, note: 'pending, paid, shipped, delivered, cancelled, refunded']
  billing_address_id  bigint        [not null, ref: > addresses.address_id]
  shipping_address_id bigint        [not null, ref: > addresses.address_id]
  subtotal            numeric(12,2) [not null, note: 'Sum of line items before tax and shipping']
  tax_amount          numeric(12,2) [not null, default: 0]
  shipping_amount     numeric(12,2) [not null, default: 0]
  discount_amount     numeric(12,2) [not null, default: 0]
  total_amount        numeric(12,2) [not null, note: 'Final amount charged to customer']
  currency_code       char(3)       [not null, default: 'USD']
  placed_at           timestamp     [not null, default: `now()`, note: 'Order placement timestamp']
  updated_at          timestamp     [not null, default: `now()`]

  Indexes {
    order_number [unique]
    (customer_id, placed_at)
    status
  }

 Note: 'Customer orders header'
}

Table order_items {
  order_item_id bigint        [pk, increment]
  order_id      bigint        [not null, ref: > orders.order_id, note: 'Parent order']
  variant_id    bigint        [not null, ref: > product_variants.variant_id, note: 'Purchased variant']
  product_name  varchar(255)  [not null, note: 'Snapshot of product name at purchase time']
  variant_name  varchar(255)  [not null, note: 'Snapshot of variant description']
  quantity      int           [not null, note: 'Units purchased']
  unit_price    numeric(12,2) [not null, note: 'Price per unit at time of purchase']
  line_total    numeric(12,2) [not null, note: 'quantity * unit_price minus line discount']

 Note: 'Line items on a placed order (immutable once order is paid)'
}

Table payments {
  payment_id       bigint        [pk, increment]
  order_id         bigint        [not null, ref: > orders.order_id, note: 'Order being paid']
  payment_method   varchar(30)   [not null, note: 'card, paypal, bank_transfer, gift_card, etc.']
  provider         varchar(50)   [note: 'Stripe, Adyen, PayPal, etc.']
  provider_txn_id  varchar(100)  [note: 'Gateway transaction reference']
  amount           numeric(12,2) [not null, note: 'Amount charged in order currency']
  currency_code    char(3)       [not null, default: 'USD']
  status           varchar(30)   [not null, note: 'authorized, captured, failed, refunded']
  processed_at     timestamp     [not null, default: `now()`]

 Note: 'Payment transactions against orders'
}

Table shipments {
  shipment_id    bigint      [pk, increment]
  order_id       bigint      [not null, ref: > orders.order_id, note: 'Parent order']
  carrier        varchar(50) [note: 'UPS, FedEx, DHL, etc.']
  tracking_number varchar(100) [note: 'Carrier tracking reference']
  status         varchar(30) [not null, note: 'pending, in_transit, delivered, returned']
  shipped_at     timestamp   [note: 'When the package left the warehouse']
  delivered_at   timestamp   [note: 'Confirmed delivery timestamp']
  Note: 'Outbound shipments for orders (an order can split into multiple shipments)'
}

Table discount_codes {
  discount_code_id bigint        [pk, increment]
  code             varchar(50)   [unique, not null, note: 'Promo code entered at checkout']
  description      varchar(255)
  discount_type    varchar(20)   [not null, note: 'percentage or fixed_amount']
  discount_value   numeric(12,2) [not null, note: 'Percent or fixed amount depending on type']
  min_order_amount numeric(12,2) [note: 'Minimum subtotal required to apply']
  max_uses         int           [note: 'Global usage cap; null for unlimited']
  uses_count       int           [not null, default: 0, note: 'Running usage counter']
  valid_from       timestamp
  valid_until      timestamp
  is_active        boolean       [not null, default: true]

  Note: 'Discount and promo codes'
}

Table order_discounts {
  order_id          bigint        [not null, ref: > orders.order_id]
  discount_code_id  bigint        [not null, ref: > discount_codes.discount_code_id]
  amount_applied    numeric(12,2) [not null, note: 'Actual discount value applied to this order']
  Indexes {
    (order_id, discount_code_id) [pk]
  }

  Note: 'Junction table: discount codes applied to orders'
}

Table reviews {
  review_id   bigint    [pk, increment]
  product_id  bigint    [not null, ref: > products.product_id, note: 'Reviewed product']
  customer_id bigint    [not null, ref: > customers.customer_id, note: 'Reviewing customer']
  order_id    bigint    [ref: > orders.order_id, note: 'Verified purchase reference']
  rating      int       [not null, note: 'Integer 1 through 5']
  title       varchar(255)
  body        text      [note: 'Full review text']
  is_verified boolean   [not null, default: false, note: 'True when tied to a valid order']
  created_at  timestamp [not null, default: `now()`]

  Indexes {
    (product_id, rating)
    (customer_id, created_at)
  }

  Note: 'Customer product reviews'
}

Table wishlists {
  wishlist_id bigint    [pk, increment]
  customer_id bigint    [not null, ref: > customers.customer_id]
  name        varchar(150) [not null, default: 'My Wishlist']
  is_public   boolean   [not null, default: false]
  created_at  timestamp [not null, default: `now()`]

  Note: 'Customer wishlists (one per customer, simple model)'
}

Table wishlist_items {
  wishlist_item_id bigint    [pk, increment]
  wishlist_id      bigint    [not null, ref: > wishlists.wishlist_id]
  product_id       bigint    [not null, ref: > products.product_id]
  added_at         timestamp [not null, default: `now()`]
  Indexes {
    (wishlist_id, product_id) [unique]
  }

  Note: 'Items inside a wishlist'
}
```

&nbsp;

A more complex prompt based on requirements could be:

&nbsp;

```text
I am tasked with designing a Human Resources training database system for employees.
Each employee is uniquely identified by their Employee Reference Number. Employees belong to specific departments, and each department is managed by an employee, and each department has an Assistant Manager.
The system will store information about various training courses, including the attendance and grades of employees for each course.
Generate an Entity-Relationship Diagram (ERD) according to the DBML specification, including the tables, columns, data types, relationships, and constraints.
.
```

&nbsp;

## Prompt template

To avoid too much iterative prompting, you may want to combine your requirements with a template such as the one below, replacing the options with your specific instructions.

&nbsp;

```text
You are a senior data modeler with 20 years of experience.
Task: Generate a complete DBML diagram for [system, domain to model]
(e.g., an e-commerce application, a hospital management system, a ride-sharing platform).

Modeling context:
- Level of data modeling: [conceptual | logical | physical]
- For [Targeted technology, platform] (e.g., technology-agnostic, RDBMS, document store, key-value stores, search engines, graph databases...)

Rules for this diagram:
1. DBML syntax compliance
   a. Follow the official spec: https://dbml.dbdiagram.io/home/
   b. Must compile without errors on https://dbdiagram.io/d

2. Comments
   a. Use notes for each entity to describe its purpose.
   b. Use notes for comments of each column to describe its purpose.

3. Entities
   a. Must include [list required entities] (or generate them based on the domain).

4. Attributes
   a. All attributes must have a data type for logical and physical models. Types must be single tokens (no commas or parentheses) to be compatible with DBML syntax.
   b. Add constraints when applicable.
5. Relationships
   a. Define relationships with appropriate cardinality, including 0-to-many using DBML syntax.
   b. If this is a physical model with many-to-many relationships, provide junction tables to fully normalize the model.
   c. Ensure relationships make sense for the chosen modeling level and paradigm.

6. Naming conventions
   a. Use [naming style] (e.g., Proper Case for conceptual and logical models, and snake_case for physical models).

Output format: Provide a DBML block that is ready to paste directly into a DBML-compatible renderer.
```

&nbsp;

Sometimes the generated DBML code cannot be reverse-engineered because the syntax is not fully valid, which can happen with AI-generated output. If necessary, continue the conversation with the LLM using an iterative prompting approach.

1. Copy the exact parsing error message you received:
2. Provide this error message and ask the LLM to fix the code based on that error.

&nbsp;

Gen AI will adjust the output to address the parsing issue and progressively improve the code until it meets DBML syntax requirements.

&nbsp;

## Reverse-engineer in Hackolade Studio

There are 2 ways to import DBML diagram code into Hackolade Studio: by reading DBML files with .dbml extensions, or by reading the clipboard into which you would have copied the DBML code from the GenAI provider's response to your prompt.

&nbsp;

Depending on the target technology of your model, the import process will convert the data types into the closest corresponding type for the target. Naming conventions, if enabled, are applied.

&nbsp;

With either method, the above DBML code will result in this Hackolade Studio diagram:\
![Mermaid ER e-commerce from ChatGPT](<lib/Mermaid ER e-commerce from ChatGPT.png>)

&nbsp;

### From DBML files

Go to Tools > Reverse-Engineer > Diagrams > DBML... and select one or more DBML files with the extension .dbml

&nbsp;

![Mermaid RE from file](<lib/Mermaid RE from file.png>)

&nbsp;

### From your Clipboard

Our Open From dialog, which already allows to [open models from](OpenmodelfromGitrepo.md) either your local computer or from any of the Git repo providers you might have configured, is where we have allowed to read your clipboard (the temporary storage in your computer's memory.). When you prompt your GPT and ask to create output in DBML diagram code, you may click the Copy button which populates your clipboard. When you access the Open From dialog and choose the Clipboard tab on the left, we automatically read the latest entry in your clipboard. If you change the content of the clipboard, you can update the content of the dialog by clicking the Refresh button.

&nbsp;

![Open From Mermaid ER diagram code](<lib/Open From Mermaid ER diagram code.png>)

&nbsp;

When you click on the Open button, the DBML diagram code is parsed and is added to the currently opened model. Depending on the selected target, the data types are mapped according to the closest available data type for that target. If no model is already opened, you are prompted to choose the target.

&nbsp;

### From remote repository

Similarly, it is possible, if you have a [repository connection](Connecttoarepositoryhub.md) to a repo provider, to select one or more files with DBML diagram code.

&nbsp;

### With the Command-Line Interface

With the argument --source=dbml in the command [revEngDiagram](<https://hackolade.com/help/CommandLineInterface.html#revEngDiagram>) of the CLI, you may automate the import of files with DBML diagram code.
