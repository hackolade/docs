---
description: How the generated foreign key attributes are added to the primary key with identifying conceptual relationships when deriving from Polyglot in Hackolade Studio.
---
# Derive identifying conceptual relationships

A relationship is identifying when the child entity depends on the parent entity for its identity. An order line, for example, only exists within its order: it is identified by its order together with its own number. A relationship is non-identifying when the child entity has an identity of its own: an order is identified by its own number, whatever the customer who placed it.

&nbsp;

You set this with the **Constraint type** of the relationship, in its Foreign Key constraint section, as described in [Constraint type: identifying versus non-identifying relationships](<https://hackolade.com/help/ConceptualtoLogicalwithPolyglotr.html#Constraint%20type:%20identifying%20versus%20non-identifying%20relationships>). At derivation, Hackolade Studio translates this identity into the primary key: with an identifying relationship, the foreign key attributes are added to the primary key of the child entity.

&nbsp;

## Example: Order and Order line

Let's continue the example of [Derive a one-to-many conceptual relationship](Deriveaone-to-manyconceptualrela.md), and say that an order line only exists inside its order: Order (1) contains Order line (1..n), and the relationship is identifying. Order line has its own primary key in Polyglot, `line number`:

&nbsp;

![Polyglot ER diagram with Order and Order line linked by contains, and the Properties pane of the relationship with Constraint type set to Identifying and an empty Foreign Key constraint](<lib/Conceptual FK Polyglot Order contains Order line.png>)

&nbsp;

After derivation, the `Order_id` column is added to the Order line table and to its primary key, which is made of `line number` + `Order_id`.

&nbsp;

![Derived PostgreSQL model with the order_line table, where line_number and the generated order_id are both marked pk, and the Properties pane of the relationship contains](<lib/Conceptual FK PostgreSQL Order contains Order line.png>)

&nbsp;

> [!NOTE]
> If the child entity has no primary key in Polyglot, Hackolade Studio also creates one. Without the `line number` attribute, the `order_id` and `order_line_id` columns are added to the Order line table, and both form its primary key. The generated `order_line_id` column is needed: with `order_id` alone as primary key, an order could only have one line.

&nbsp;

![Derived PostgreSQL model where the Order line entity had no primary key in Polyglot: the order_line table has the order_id column and a generated order_line_id column, both marked pk](<lib/Conceptual FK PostgreSQL Order contains Order line without primary key.png>)

&nbsp;

> [!IMPORTANT]
> An identifying relationship is only possible when the parent entity is mandatory, with cardinality **1**. A primary key attribute cannot be empty.

&nbsp;

## Primary key of the child entity

The primary key of the child entity changes as follows:

&nbsp;

| Child entity | Non-identifying relationship | Identifying relationship |
| --- | --- | --- |
| Has a primary key | Not changed | The foreign key attributes are added to it |
| Has no primary key, one-to-many | No primary key is created | Foreign key attributes + a generated attribute, `order_line_id` in the example |
| Has no primary key, one-to-one | No primary key is created | Foreign key attributes only |

&nbsp;

> [!NOTE]
> A composite primary key or a unique key is only created when the target supports it.

&nbsp;

## Chains of identifying relationships

Identifying relationships can follow each other. Let's suppose that the relationship between Customer and Order is identifying too. The primary key of the Order table then becomes `id` + `Customer_id`, and this complete key must be added to the Order line table, not only `id`.

&nbsp;

Hackolade Studio resolves the chain in order, so that the keys cascade from one table to the next. The key of the Customer table is first added to the Order table, then the key of the Order table is added to the Order line table. The `Order_id` and `Order_Customer_id` columns are added to the Order line table, and both become part of its primary key, together with its own `line number` column.

&nbsp;

> [!WARNING]
> A chain of identifying relationships cannot loop back: an entity cannot depend on itself for its identity, directly or through other entities. Such a cycle is a design problem in the Polyglot model, for example a recursive relationship set as identifying, such as a Product that replaces another Product. Hackolade Studio then derives the relationships of the cycle, and those that depend on it, as non-identifying, and reports a warning, as described in [Check and update generated foreign keys](<https://hackolade.com/help/Checkandupdategeneratedforeignke.html#Warnings%20after%20derivation>). The same happens when the parent entity has cardinality 0..1.
