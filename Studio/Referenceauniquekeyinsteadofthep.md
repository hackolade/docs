---
description: Choose the destination key attributes of a conceptual relationship, such as a unique business identifier, when deriving from Polyglot in Hackolade Studio.
seoTitle: Point a foreign key to a unique key
---
# Point a foreign key to a unique key instead of the primary key

By default, the destination key columns are the primary key of the parent entity. In some models, you want the foreign key to point to a business identifier instead.

## Example: Order line and Product

Let's add a Product entity to the example, and link it to the Order line entity of [Derive identifying conceptual relationships](Deriveidentifyingconceptualrelat.md). The Product entity has a technical primary key `id` (a UUID) and a business identifier `SKU`, defined as unique. Each order line is for exactly one product. To point the foreign key to `SKU` instead of `id`, select `SKU` in **Attribute(s) of Product**, and leave **Attribute(s) of Order line** empty:

![Polyglot ER diagram with Product and Order line linked by is ordered in, and the Properties pane of the relationship with SKU selected in Attribute(s) of Product and Attribute(s) of Order line empty](<lib/Conceptual FK Polyglot Product is ordered in Order line.png>)

After derivation, the foreign key column `Product_SKU` is added to the Order line table, with `Product.SKU` as destination key column. With the naming conventions of the PostgreSQL model, `Product_SKU` becomes `product_sku`:

![Derived PostgreSQL model with the generated product_sku column in order_line, and the Properties pane of the relationship with Parent field sku and Child field product_sku](<lib/Conceptual FK PostgreSQL Product is ordered in Order line.png>)

This is the same approach as for [associative tables that use non-key attributes](<https://hackolade.com/help/Associativeentitiesformany-to-ma.html#How%20to%20use%20non-key%20attributes%20as%20PK%20in%20associative%20entities>).

> [!IMPORTANT]
> The attributes you select must be unique in the Product entity.

## How the destination key attributes are chosen

The destination key attributes are chosen in this order:

- the attributes you selected for the parent entity in the Foreign Key constraint section, if any,
- otherwise its primary key. With a composite primary key, one foreign key attribute is added to the child entity for each attribute of the key, and one Foreign Key constraint is created on all of them together,
- otherwise, when the parent entity has no primary key, Hackolade Studio creates an attribute `id` in it as primary key, which then becomes the destination key attribute. This is the same rule as for associative tables.

> [!WARNING]
> The attribute `id` is created even if the entity already has an attribute with that name that is not its primary key. The existing attribute is not reused.
