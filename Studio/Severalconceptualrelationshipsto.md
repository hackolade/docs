---
description: How Hackolade Studio names the generated foreign key attributes when an entity has several conceptual relationships to the same entity.
---
# Several conceptual relationships to the same entity

This page finishes the example of [Derive a one-to-many conceptual relationship](Deriveaone-to-manyconceptualrela.md) with addresses.

&nbsp;

## Billing address and delivery address

An order has a billing address and a delivery address, so the Order entity is linked twice to the Address entity, with cardinality 1 on the Address side. With the [standard pattern](<https://hackolade.com/help/Deriveaone-to-manyconceptualrela.html#Names%20of%20the%20generated%20attributes>), both foreign key attributes would be named `Address_id`.

&nbsp;

![Polyglot ER diagram with Order linked twice to Address, by is delivered to and is billed to, with the roles delivery address and billing address on the Address side](<lib/Conceptual FK Polyglot Order and Address.png>)

&nbsp;

When two generated attributes of the child entity would have the same name, Hackolade Studio replaces the entity name in the generated name:

- by the role of the parent entity, when you defined one on the relationship,
- otherwise, by the name of the relationship.

&nbsp;

In our example, the roles are set on the Address side of each relationship:

&nbsp;

![Properties pane of the Polyglot relationship is billed to, with the role billing address for Address](<lib/Conceptual FK Polyglot billing address role.png>)

&nbsp;

![Properties pane of the Polyglot relationship is delivered to, with the role delivery address for Address](<lib/Conceptual FK Polyglot delivery address role.png>)

&nbsp;

With the roles "billing address" and "delivery address", the attributes added to the Order entity are `billing address_id` and `delivery address_id`. Both attributes are renamed, not only the second one, so the result is the same at each derivation. The same rule applies when the child entity already contains an attribute with the generated name.

&nbsp;

With the naming conventions of the PostgreSQL model, they become `billing_address_id` and `delivery_address_id`:

&nbsp;

![Derived PostgreSQL model with the order table and its generated billing_address_id and delivery_address_id columns, linked to the address table by is_billed_to and is_delivered_to](<lib/Conceptual FK PostgreSQL Order and Address.png>)

&nbsp;

> [!TIP]
> Defining roles on such relationships gives you readable names, and saves a manual rename after each derivation.
