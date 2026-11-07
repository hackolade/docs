---
description: Derive a one-to-one conceptual relationship from Polyglot, with a generated foreign key and unique key, and choose which entity holds it.
seoTitle: Derive a one-to-one conceptual relationship
---
# Derive a one-to-one conceptual relationship

Let's extend the example of [Derive a one-to-many conceptual relationship](Deriveaone-to-manyconceptualrela.md) with an Invoice entity.

## Example: Order and Invoice

Each invoice is issued for exactly one order (cardinality **1** on the Order side), and an order has at most one invoice (cardinality **0..1** on the Invoice side, assuming no backorder capability in this example):

![Polyglot ER diagram with Order and Invoice linked by is invoiced by, and the Properties pane of the relationship with cardinality 1 for Order and 0..1 for Invoice](<lib/Conceptual FK Polyglot Order is invoiced by Invoice.png>)

In a one-to-one relationship, the foreign key attributes are created on the optional side. Hackolade Studio adds a required `Order_id` column to the Invoice table, and also creates a **unique key** on this column, so that the same order cannot be invoiced twice. When there are several foreign key columns, the unique key is created on all of them together. No unique key is added when these columns already form the complete primary key of the Invoice table.

![Derived PostgreSQL model with the generated order_id column in invoice, marked uk and fk, and its Properties pane with Unique checked](<lib/Conceptual FK PostgreSQL Order is invoiced by Invoice.png>)

## Same cardinality on both sides

When both sides have the same cardinality (1 and 1, or 0..1 and 0..1), both choices are valid from a modeling point of view. Hackolade Studio then applies a convention: the foreign key attributes are created in the **second** entity listed in the **Linked entities** section of the relationship's properties.

![Conceptual model - swap entities in relationship](<lib/Conceptual model - swap entities in relation.png>)

> [!TIP]
> To get the foreign key attributes in the other entity, swap the two entities in the **Linked entities** section of the relationship's properties *before* deriving, with the arrows described in [Direction as a semantic choice](<https://hackolade.com/help/ConceptualtoLogicalwithPolyglotr.html#Direction%20as%20a%20semantic%20choice>).

## Summary: cardinality impact on placement of foreign key

The child entity and the parent entity are determined according to the logic in this table:

<table style="width:100%">
<colgroup><col style="width:37%"><col style="width:33%"><col style="width:30%"></colgroup>
<thead>
<tr>
<th>Relationship</th>
<th>Child entity</th>
<th>Parent entity</th>
</tr>
</thead>
<tbody>
<tr>
<td>One-to-many</td>
<td>The entity on the "many" side (0..n or 1..n)</td>
<td>The entity on the "one" side (1 or 0..1)</td>
</tr>
<tr>
<td>One-to-zero-to-one, 1 on one side and 0..1 on the other</td>
<td>The entity with cardinality 0..1</td>
<td>The entity with cardinality 1</td>
</tr>
<tr>
<td>One-to-one, same cardinality on both sides</td>
<td>The second entity in the <strong>Linked entities</strong> list</td>
<td>The first entity in the <strong>Linked entities </strong>list</td>
</tr>
</tbody>
</table>
