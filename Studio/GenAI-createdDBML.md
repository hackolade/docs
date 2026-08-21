# GenAI-created DBML

This features allows to instantly generate models, polyglot or physical, then edit and enrich them, plus integrate suggestions from GenAI.&nbsp; By integrating AI-generated diagrams with Hackolade Studio’s intuitive modeling, teams can efficiently develop and refine their data models, enhancing collaboration and accelerating the development cycle.

&nbsp;

## DBML&nbsp;

[DBML](<https://dbml.dbdiagram.io/home> "target=\"\_blank\"") (Database Markup Language) is an open-source DSL (a small, special‑purpose language designed for one particular domain, in this case **database schemas**) designed to define and document database schemas and structures.&nbsp; It is designed to be simple, consistent and highly-readable.&nbsp; Its [playground](<https://dbdiagram.io/d> "target=\"\_blank\"") also allows to create simple diagrams, although far from the professional level and capabilities of Hackolade Studio.

&nbsp;

DBML‑style DSLs are especially good for bi-directional exchanges of schemas with Generative AI because they combine compactness, simplicity, and structure -- exactly what an LLM needs to understand and rewrite database layouts reliably.&nbsp; It is text‑only, declarative, and close to “pseudo‑code”.&nbsp; A DBML DSL cleanly separates intent (the schema) from implementation (SQL for a specific DB).

&nbsp;

ChatGPT, Claude, CoPilot, Gemini and other generative AI models find it easier to generate ER diagrams in DBML compared to SQL DDL or traditional modeling standards because DBML uses a simple, human-readable syntax that closely aligns with natural language. Its declarative and visual style allows AI to map conceptual relationships directly into diagram code without needing strict adherence to data types, constraints, or database-specific rules. Unlike DDLs, which requires precision and contextual knowledge of database engines, DBML is more forgiving and doesn’t require runtime validation. This makes it an ideal format for GenAI to produce quickly and accurately from natural prompts.

&nbsp;

Compared with [Mermaid ER code](<https://www.mermaidchart.com/> "target=\"\_blank\""), DBML‑style DSLs are better for exchanging schemas with GenAI mainly because they are more “schema‑oriented” and less “diagram‑oriented,” which makes them easier for an AI to parse, reason about, and transform.&nbsp; Mermaid ER syntax is designed to describe graphics and layout: boxes, lines, cardinality labels, and sometimes notes while DBML is purely about tables, columns, types, constraints, and relationships; it does not care how the diagram is rendered. That makes it much closer to the “true” data model an AI needs to understand.&nbsp; DBML can cleanly encode things like pk, not null, indexes, enums, and extensions (e.g., dbdiagram project‑level notes), which are useful for AI‑driven schema evolution and SQL generation.

&nbsp;

DBML works well for **tables, columns, and relational constraints, but l**ike Mermaid however, it does not define “types” with nested fields or array‑of‑objects structures the way you can in JSON‑schema or a document‑aware modeling language. DBML is not a logical‑type DSL for subobjects or arrays; it delegates that complexity to the database‑level JSON/array types and to external schemas.

&nbsp;

## Prompt

You may create prompts using entire business requirements, and fine-tune the prompt until the result suits your needs.&nbsp; For the purpose of this documentation page, here is a super simple prompt example:

> Generate a physical ERD in DBML for an e-commerce application running on PostgreSQL, full with tables, columns, data types, relationships. &nbsp;

&nbsp;

With some LLMs, it might be required to specify:&nbsp;

Provide syntactically correct code so it can be accepted without errors by [https://dbml.dbdiagram.io/home](<https://dbml.dbdiagram.io/home> "target=\"\_blank\"")

&nbsp;

**Note:** results vary greatly depending on the LLM and the prompt. &nbsp;

&nbsp;

Here is a simple example response from Claude Sonnet 4.6 for the above prompt:

&nbsp;

> // =====================================================\
// E-Commerce Application - Entity Relationship Diagram\
// =====================================================\
\
Project ecommerce {\
&nbsp; database\_type: 'PostgreSQL'\
&nbsp; Note: 'E-commerce platform schema covering customers, catalog, orders, payments, shipping, and reviews'\
}\
\
Table customers {\
&nbsp; customer\_id &nbsp; bigint&nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique customer identifier'\]\
&nbsp; email &nbsp; &nbsp; &nbsp; &nbsp; varchar(255) \[unique, not null, note: 'Login email, must be unique'\]\
&nbsp; password\_hash varchar(255) \[not null, note: 'Hashed password — never store plaintext'\]\
&nbsp; first\_name&nbsp; &nbsp; varchar(100) \[not null, note: 'Customer given name'\]\
&nbsp; last\_name &nbsp; &nbsp; varchar(100) \[not null, note: 'Customer family name'\]\
&nbsp; phone &nbsp; &nbsp; &nbsp; &nbsp; varchar(30)&nbsp; \[note: 'E.164 formatted phone number'\]\
&nbsp; date\_of\_birth date &nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Used for age-restricted products and marketing'\]\
&nbsp; is\_active &nbsp; &nbsp; boolean &nbsp; &nbsp; \[not null, default: true, note: 'Soft-disable flag'\]\
&nbsp; created\_at&nbsp; &nbsp; timestamp &nbsp; \[not null, default: \`now()\`, note: 'Account creation timestamp'\]\
&nbsp; updated\_at&nbsp; &nbsp; timestamp &nbsp; \[not null, default: \`now()\`, note: 'Last profile modification'\]\
\
&nbsp; Indexes {\
&nbsp; &nbsp; email \[unique\]\
&nbsp; &nbsp; (last\_name, first\_name)\
&nbsp; }\
\
&nbsp;&nbsp; Note: 'Registered shoppers and guest accounts'\
}\
\
Table addresses {\
&nbsp; address\_id &nbsp; bigint&nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique address identifier'\]\
&nbsp; customer\_id&nbsp; bigint&nbsp; &nbsp; &nbsp; \[not null, ref: \> customers.customer\_id, note: 'Owner of the address'\]\
&nbsp; address\_type varchar(20) \[not null, note: 'billing or shipping'\]\
&nbsp; line1&nbsp; &nbsp; &nbsp; &nbsp; varchar(255) \[not null, note: 'Street address line 1'\]\
&nbsp; line2&nbsp; &nbsp; &nbsp; &nbsp; varchar(255) \[note: 'Apartment, suite, etc.'\]\
&nbsp; city &nbsp; &nbsp; &nbsp; &nbsp; varchar(100) \[not null, note: 'City or locality'\]\
&nbsp; state&nbsp; &nbsp; &nbsp; &nbsp; varchar(100) \[note: 'State, province, or region'\]\
&nbsp; postal\_code&nbsp; varchar(20)&nbsp; \[not null, note: 'ZIP or postal code'\]\
&nbsp; country\_code char(2) &nbsp; &nbsp; \[not null, note: 'ISO 3166-1 alpha-2 country code'\]\
&nbsp; is\_default &nbsp; boolean &nbsp; &nbsp; \[not null, default: false, note: 'Default address for this type'\]\
&nbsp; created\_at &nbsp; timestamp &nbsp; \[not null, default: \`now()\`\]\
\
&nbsp; Note: 'Shipping and billing addresses linked to customers'\
}\
\
Table categories {\
&nbsp; category\_id&nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique category identifier'\]\
&nbsp; parent\_category\_id bigint&nbsp; &nbsp; &nbsp; \[ref: \> categories.category\_id, note: 'Parent category for hierarchy; null for root'\]\
&nbsp; name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(150) \[not null, note: 'Display name of the category'\]\
&nbsp; slug &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(150) \[unique, not null, note: 'URL-friendly identifier'\]\
&nbsp; description&nbsp; &nbsp; &nbsp; &nbsp; text&nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Long-form category description'\]\
&nbsp; sort\_order &nbsp; &nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; \[not null, default: 0, note: 'Display ordering within parent'\]\
&nbsp; is\_active&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; boolean &nbsp; &nbsp; \[not null, default: true\]\
\
&nbsp; Note: 'Hierarchical product categories (self-referential)'\
}\
\
Table brands {\
&nbsp; brand\_id&nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; name&nbsp; &nbsp; &nbsp; &nbsp; varchar(150) \[unique, not null, note: 'Brand display name'\]\
&nbsp; slug&nbsp; &nbsp; &nbsp; &nbsp; varchar(150) \[unique, not null, note: 'URL-friendly brand identifier'\]\
&nbsp; description text&nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Brand story or bio'\]\
&nbsp; logo\_url&nbsp; &nbsp; varchar(500) \[note: 'CDN URL for brand logo'\]\
\
&nbsp; Note: 'Suppliers or brands providing products'\
}\
\
Table products {\
&nbsp; product\_id &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique product identifier'\]\
&nbsp; brand\_id &nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[ref: \> brands.brand\_id, note: 'Associated brand'\]\
&nbsp; category\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> categories.category\_id, note: 'Primary category'\]\
&nbsp; sku&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(64) &nbsp; \[unique, not null, note: 'Stock keeping unit'\]\
&nbsp; name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(255)&nbsp; \[not null, note: 'Product display name'\]\
&nbsp; slug &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(255)&nbsp; \[unique, not null, note: 'URL-friendly product identifier'\]\
&nbsp; description&nbsp; &nbsp; &nbsp; text&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Full product description, supports markdown'\]\
&nbsp; short\_description varchar(500) \[note: 'Summary used in listings'\]\
&nbsp; base\_price &nbsp; &nbsp; &nbsp; numeric(12,2) \[not null, note: 'List price in store base currency'\]\
&nbsp; currency\_code&nbsp; &nbsp; char(3) &nbsp; &nbsp; &nbsp; \[not null, default: 'USD', note: 'ISO 4217 currency code'\]\
&nbsp; weight\_grams &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Shipping weight in grams'\]\
&nbsp; is\_active&nbsp; &nbsp; &nbsp; &nbsp; boolean &nbsp; &nbsp; &nbsp; \[not null, default: true, note: 'Visible in storefront'\]\
&nbsp; created\_at &nbsp; &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`\]\
&nbsp; updated\_at &nbsp; &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`\]\
\
&nbsp; Indexes {\
&nbsp; &nbsp; sku \[unique\]\
&nbsp; &nbsp; (category\_id, is\_active)\
&nbsp; &nbsp; name\
&nbsp; }\
\
&nbsp; Note: 'Master product catalog'\
}\
\
Table product\_variants {\
&nbsp; variant\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique variant identifier'\]\
&nbsp; product\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> products.product\_id, note: 'Parent product'\]\
&nbsp; variant\_sku &nbsp; &nbsp; varchar(64) &nbsp; \[unique, not null, note: 'Variant-level SKU'\]\
&nbsp; variant\_name&nbsp; &nbsp; varchar(255)&nbsp; \[not null, note: 'e.g. "Red / Large"'\]\
&nbsp; price\_override&nbsp; numeric(12,2) \[note: 'If set, overrides product.base\_price'\]\
&nbsp; stock\_quantity&nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[not null, default: 0, note: 'On-hand inventory count'\]\
&nbsp; weight\_grams&nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Variant-specific shipping weight'\]\
&nbsp; is\_active &nbsp; &nbsp; &nbsp; boolean &nbsp; &nbsp; &nbsp; \[not null, default: true\]\
\
&nbsp; Note: 'Product variants (size, color, etc.) with their own stock and price'\
}\
\
Table product\_images {\
&nbsp; image\_id&nbsp; &nbsp; bigint &nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; product\_id&nbsp; bigint &nbsp; &nbsp; &nbsp; \[not null, ref: \> products.product\_id, note: 'Product this image belongs to'\]\
&nbsp; variant\_id&nbsp; bigint &nbsp; &nbsp; &nbsp; \[ref: \> product\_variants.variant\_id, note: 'Optional variant-specific image'\]\
&nbsp; url &nbsp; &nbsp; &nbsp; &nbsp; varchar(500) \[not null, note: 'CDN URL of the image'\]\
&nbsp; alt\_text&nbsp; &nbsp; varchar(255) \[note: 'Accessibility alt text'\]\
&nbsp; sort\_order&nbsp; int&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[not null, default: 0, note: 'Display ordering in gallery'\]\
&nbsp; is\_primary&nbsp; boolean&nbsp; &nbsp; &nbsp; \[not null, default: false, note: 'Hero image flag'\]\
\
&nbsp; Note: 'Product images, ordered for galleries'\
}\
\
Table carts {\
&nbsp; cart\_id &nbsp; &nbsp; bigint&nbsp; &nbsp; \[pk, increment\]\
&nbsp; customer\_id bigint&nbsp; &nbsp; \[ref: \> customers.customer\_id, note: 'Owning customer; null for guest carts'\]\
&nbsp; session\_id&nbsp; varchar(100) \[note: 'Session key for guest carts'\]\
&nbsp; created\_at&nbsp; timestamp \[not null, default: \`now()\`\]\
&nbsp; updated\_at&nbsp; timestamp \[not null, default: \`now()\`\]\
\
&nbsp; Note: 'Shopping cart header (one open cart per customer)'\
}\
\
Table cart\_items {\
&nbsp; cart\_item\_id bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; cart\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> carts.cart\_id, note: 'Parent cart'\]\
&nbsp; variant\_id &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> product\_variants.variant\_id, note: 'Selected variant'\]\
&nbsp; quantity &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[not null, default: 1, note: 'Quantity in cart'\]\
&nbsp; unit\_price &nbsp; numeric(12,2) \[not null, note: 'Price captured at time of add-to-cart'\]\
&nbsp; added\_at &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`\]\
\
&nbsp; Note: 'Line items inside a shopping cart'\
}\
\
Table orders {\
&nbsp; order\_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment, note: 'Unique order identifier'\]\
&nbsp; customer\_id &nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> customers.customer\_id, note: 'Purchasing customer'\]\
&nbsp; order\_number&nbsp; &nbsp; &nbsp; &nbsp; varchar(32) &nbsp; \[unique, not null, note: 'Human-readable order reference'\]\
&nbsp; status&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(30) &nbsp; \[not null, note: 'pending, paid, shipped, delivered, cancelled, refunded'\]\
&nbsp; billing\_address\_id&nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> addresses.address\_id\]\
&nbsp; shipping\_address\_id bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> addresses.address\_id\]\
&nbsp; subtotal&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; numeric(12,2) \[not null, note: 'Sum of line items before tax and shipping'\]\
&nbsp; tax\_amount&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; numeric(12,2) \[not null, default: 0\]\
&nbsp; shipping\_amount &nbsp; &nbsp; numeric(12,2) \[not null, default: 0\]\
&nbsp; discount\_amount &nbsp; &nbsp; numeric(12,2) \[not null, default: 0\]\
&nbsp; total\_amount&nbsp; &nbsp; &nbsp; &nbsp; numeric(12,2) \[not null, note: 'Final amount charged to customer'\]\
&nbsp; currency\_code &nbsp; &nbsp; &nbsp; char(3) &nbsp; &nbsp; &nbsp; \[not null, default: 'USD'\]\
&nbsp; placed\_at &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`, note: 'Order placement timestamp'\]\
&nbsp; updated\_at&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`\]\
\
&nbsp; Indexes {\
&nbsp; &nbsp; order\_number \[unique\]\
&nbsp; &nbsp; (customer\_id, placed\_at)\
&nbsp; &nbsp; status\
&nbsp; }\
\
&nbsp;Note: 'Customer orders header'\
}\
\
Table order\_items {\
&nbsp; order\_item\_id bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; order\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> orders.order\_id, note: 'Parent order'\]\
&nbsp; variant\_id&nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> product\_variants.variant\_id, note: 'Purchased variant'\]\
&nbsp; product\_name&nbsp; varchar(255)&nbsp; \[not null, note: 'Snapshot of product name at purchase time'\]\
&nbsp; variant\_name&nbsp; varchar(255)&nbsp; \[not null, note: 'Snapshot of variant description'\]\
&nbsp; quantity&nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[not null, note: 'Units purchased'\]\
&nbsp; unit\_price&nbsp; &nbsp; numeric(12,2) \[not null, note: 'Price per unit at time of purchase'\]\
&nbsp; line\_total&nbsp; &nbsp; numeric(12,2) \[not null, note: 'quantity \* unit\_price minus line discount'\]\
\
&nbsp;Note: 'Line items on a placed order (immutable once order is paid)'\
}\
\
Table payments {\
&nbsp; payment\_id &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; order\_id &nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> orders.order\_id, note: 'Order being paid'\]\
&nbsp; payment\_method &nbsp; varchar(30) &nbsp; \[not null, note: 'card, paypal, bank\_transfer, gift\_card, etc.'\]\
&nbsp; provider &nbsp; &nbsp; &nbsp; &nbsp; varchar(50) &nbsp; \[note: 'Stripe, Adyen, PayPal, etc.'\]\
&nbsp; provider\_txn\_id&nbsp; varchar(100)&nbsp; \[note: 'Gateway transaction reference'\]\
&nbsp; amount &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; numeric(12,2) \[not null, note: 'Amount charged in order currency'\]\
&nbsp; currency\_code&nbsp; &nbsp; char(3) &nbsp; &nbsp; &nbsp; \[not null, default: 'USD'\]\
&nbsp; status &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(30) &nbsp; \[not null, note: 'authorized, captured, failed, refunded'\]\
&nbsp; processed\_at &nbsp; &nbsp; timestamp &nbsp; &nbsp; \[not null, default: \`now()\`\]\
\
&nbsp;Note: 'Payment transactions against orders'\
}\
\
Table shipments {\
&nbsp; shipment\_id&nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; order\_id &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; \[not null, ref: \> orders.order\_id, note: 'Parent order'\]\
&nbsp; carrier&nbsp; &nbsp; &nbsp; &nbsp; varchar(50) \[note: 'UPS, FedEx, DHL, etc.'\]\
&nbsp; tracking\_number varchar(100) \[note: 'Carrier tracking reference'\]\
&nbsp; status &nbsp; &nbsp; &nbsp; &nbsp; varchar(30) \[not null, note: 'pending, in\_transit, delivered, returned'\]\
&nbsp; shipped\_at &nbsp; &nbsp; timestamp &nbsp; \[note: 'When the package left the warehouse'\]\
&nbsp; delivered\_at &nbsp; timestamp &nbsp; \[note: 'Confirmed delivery timestamp'\]\
\
\
&nbsp; Note: 'Outbound shipments for orders (an order can split into multiple shipments)'\
}\
\
Table discount\_codes {\
&nbsp; discount\_code\_id bigint&nbsp; &nbsp; &nbsp; &nbsp; \[pk, increment\]\
&nbsp; code &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; varchar(50) &nbsp; \[unique, not null, note: 'Promo code entered at checkout'\]\
&nbsp; description&nbsp; &nbsp; &nbsp; varchar(255)\
&nbsp; discount\_type&nbsp; &nbsp; varchar(20) &nbsp; \[not null, note: 'percentage or fixed\_amount'\]\
&nbsp; discount\_value &nbsp; numeric(12,2) \[not null, note: 'Percent or fixed amount depending on type'\]\
&nbsp; min\_order\_amount numeric(12,2) \[note: 'Minimum subtotal required to apply'\]\
&nbsp; max\_uses &nbsp; &nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[note: 'Global usage cap; null for unlimited'\]\
&nbsp; uses\_count &nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \[not null, default: 0, note: 'Running usage counter'\]\
&nbsp; valid\_from &nbsp; &nbsp; &nbsp; timestamp\
&nbsp; valid\_until&nbsp; &nbsp; &nbsp; timestamp\
&nbsp; is\_active&nbsp; &nbsp; &nbsp; &nbsp; boolean &nbsp; &nbsp; &nbsp; \[not null, default: true\]\
\
&nbsp; Note: 'Discount and promo codes'\
}\
\
Table order\_discounts {\
&nbsp; order\_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> orders.order\_id\]\
&nbsp; discount\_code\_id&nbsp; bigint&nbsp; &nbsp; &nbsp; &nbsp; \[not null, ref: \> discount\_codes.discount\_code\_id\]\
&nbsp; amount\_applied&nbsp; &nbsp; numeric(12,2) \[not null, note: 'Actual discount value applied to this order'\]\
&nbsp; Indexes {\
&nbsp; &nbsp; (order\_id, discount\_code\_id) \[pk\]\
&nbsp; }\
\
&nbsp; Note: 'Junction table: discount codes applied to orders'\
}\
\
Table reviews {\
&nbsp; review\_id &nbsp; bigint&nbsp; &nbsp; \[pk, increment\]\
&nbsp; product\_id&nbsp; bigint&nbsp; &nbsp; \[not null, ref: \> products.product\_id, note: 'Reviewed product'\]\
&nbsp; customer\_id bigint&nbsp; &nbsp; \[not null, ref: \> customers.customer\_id, note: 'Reviewing customer'\]\
&nbsp; order\_id&nbsp; &nbsp; bigint&nbsp; &nbsp; \[ref: \> orders.order\_id, note: 'Verified purchase reference'\]\
&nbsp; rating&nbsp; &nbsp; &nbsp; int &nbsp; &nbsp; &nbsp; \[not null, note: 'Integer 1 through 5'\]\
&nbsp; title &nbsp; &nbsp; &nbsp; varchar(255)\
&nbsp; body&nbsp; &nbsp; &nbsp; &nbsp; text&nbsp; &nbsp; &nbsp; \[note: 'Full review text'\]\
&nbsp; is\_verified boolean &nbsp; \[not null, default: false, note: 'True when tied to a valid order'\]\
&nbsp; created\_at&nbsp; timestamp \[not null, default: \`now()\`\]\
\
&nbsp; Indexes {\
&nbsp; &nbsp; (product\_id, rating)\
&nbsp; &nbsp; (customer\_id, created\_at)\
&nbsp; }\
\
&nbsp; Note: 'Customer product reviews'\
}\
\
Table wishlists {\
&nbsp; wishlist\_id bigint&nbsp; &nbsp; \[pk, increment\]\
&nbsp; customer\_id bigint&nbsp; &nbsp; \[not null, ref: \> customers.customer\_id\]\
&nbsp; name&nbsp; &nbsp; &nbsp; &nbsp; varchar(150) \[not null, default: 'My Wishlist'\]\
&nbsp; is\_public &nbsp; boolean &nbsp; \[not null, default: false\]\
&nbsp; created\_at&nbsp; timestamp \[not null, default: \`now()\`\]\
\
&nbsp; Note: 'Customer wishlists (one per customer, simple model)'\
}\
\
Table wishlist\_items {\
&nbsp; wishlist\_item\_id bigint&nbsp; &nbsp; \[pk, increment\]\
&nbsp; wishlist\_id&nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; \[not null, ref: \> wishlists.wishlist\_id\]\
&nbsp; product\_id &nbsp; &nbsp; &nbsp; bigint&nbsp; &nbsp; \[not null, ref: \> products.product\_id\]\
&nbsp; added\_at &nbsp; &nbsp; &nbsp; &nbsp; timestamp \[not null, default: \`now()\`\]\
&nbsp; Indexes {\
&nbsp; &nbsp; (wishlist\_id, product\_id) \[unique\]\
&nbsp; }\
\
&nbsp; Note: 'Items inside a wishlist'\
}\
&nbsp;

&nbsp;

&nbsp;

A more complex prompt based on requirements could be:

&nbsp;

> I am tasked with designing a Human Resources training database system for employees.\
Each employee is uniquely identified by their Employee Reference Number. Employees belong to specific departments, and each department is managed by an employee, and each department has an Assistant Manager.\
The system will store information about various training courses, including the attendance and grades of employees for each course.\
Generate an Entity-Relationship Diagram (ERD) according to the DBML specification, including the tables, columns, data types, relationships, and constraints.

.&nbsp;

## Prompt template

To avoid too much iterative prompting, you may want to combine your requirements with a template such as the one below, replacing the options with your specific instructions.

&nbsp;

> You are a senior data modeler with 20 years of experience.\
\
Task: Generate a complete DBML diagram for \[system, domain to model\] \
(e.g., an e-commerce application, a hospital management system, a ride-sharing platform).\
\
Modeling context:\
\- Level of data modeling: \[conceptual \| logical \| physical\]\
\- For \[Targeted technology, platform\] (e.g., technology-agnostic, RDBMS, document store, key-value stores, search engines, graph databases...)\
\
Rules for this diagram:\
&#49;. DBML syntax compliance\
&nbsp;&nbsp; a. Follow the official spec: https://dbml.dbdiagram.io/home/\
&nbsp;&nbsp; b. Must compile without errors on https://dbdiagram.io/d\
\
&#50;. Comments\
&nbsp;&nbsp; a. Use notes for each entity to describe its purpose.\
&nbsp;&nbsp; b. Use notes for comments of each column to describe its purpose.\
\
&#51;. Entities\
&nbsp;&nbsp; a. Must include \[list required entities\] (or generate them based on the domain).\
\
&#52;. Attributes\
&nbsp;&nbsp; a. All attributes must have a data type for logical and physical models. Types must be single tokens (no commas or parentheses) to be compatible with DBML syntax.\
&nbsp;&nbsp; b. Add constraints when applicable. \
\
&#53;. Relationships\
&nbsp;&nbsp; a. Define relationships with appropriate cardinality, including 0-to-many using DBML syntax.\
&nbsp;&nbsp; b. If this is a physical model with many-to-many relationships, provide junction tables to fully normalize the model.\
&nbsp;&nbsp; c. Ensure relationships make sense for the chosen modeling level and paradigm.\
\
&#54;. Naming conventions\
&nbsp;&nbsp; a. Use \[naming style\] (e.g., Proper Case for conceptual and logical models, and snake\_case for physical models).\
\
Output format: Provide a DBML block that is ready to paste directly into a DBML-compatible renderer.

&nbsp;

Sometimes the generated DBML code cannot be reverse-engineered because the syntax is not fully valid, which can happen with AI-generated output.&nbsp; If necessary, continue the conversation with the LLM using an iterative prompting approach.

&nbsp;

1. Copy the exact parsing error message you received:
1. Provide this error message and ask the LLM to fix the code based on that error.

&nbsp;

Gen AI will adjust the output to address the parsing issue and progressively improve the code until it meets DBML syntax requirements.

&nbsp;

## Reverse-engineer in Hackolade Studio

There are 2 ways to import DBML diagram code into Hackolade Studio: by reading DBML files with .dbml extensions, or by reading the clipboard into which you would have copied the DBML code from the GenAI provider's response to your prompt.

&nbsp;

Depending on the target technology of your model, the import process will convert the data types into the closest corresponding type for the target.&nbsp; Naming conventions, if enabled, are applied.

&nbsp;

With either method, the above DBML code will result in this Hackolade Studio diagram:

![Mermaid ER e-commerce from ChatGPT](<lib/Mermaid ER e-commerce from ChatGPT.png>)

&nbsp;

### From DBML files

Go to Tools \> Reverse-Engineer \> Diagrams \> DBML... and select one or more DBML files with the extension .dbml

&nbsp;

![Mermaid RE from file](<lib/Mermaid RE from file.png>)

&nbsp;

### From your Clipboard

Our Open From dialog, which already allows to [open models from](<OpenmodelfromGitrepo.md>) either your local computer or from any of the Git repo providers you might have configured, is where we have allowed to read your clipboard (the temporary storage in your computer's memory.).&nbsp; When you prompt your GPT and ask to create output in DBML diagram code, you may click the Copy button which populates your clipboard.&nbsp; When you access the Open From dialog and choose the Clipboard tab on the left, we automatically read the latest entry in your clipboard.&nbsp; If you change the content of the clipboard, you can update the content of the dialog by clicking the Refresh button.

&nbsp;

![Open From Mermaid ER diagram code](<lib/Open From Mermaid ER diagram code.png>)

&nbsp;

&nbsp;

When you click on the Open button, the DBML diagram code is parsed and is added to the currently opened model.&nbsp; Depending on the selected target, the data types are mapped according to the closest available data type for that target.&nbsp; If no model is already opened, you are prompted to choose the target.

&nbsp;

&nbsp;

### From remote repository

Similarly, it is possible, if you have a [repository connection](<Connecttoarepositoryhub.md>) to a repo provider, to select one or more files with DBML diagram code.

&nbsp;

&nbsp;

### With the Command-Line Interface

With the argument --source=dbml in the command [revEngDiagram](<https://hackolade.com/help/CommandLineInterface.html#revEngDiagram> "target=\"\_blank\"") of the CLI, you may automate the import of files with DBML diagram code.

&nbsp;

