---
description: Create composite primary keys and composite foreign key relationships in Hackolade Studio data models.
seoTitle: Define composite primary and foreign keys
---
# Define composite key constraints

This page shows how to create composite primary keys (a.k.a. composite PK, compound primary keys, or complex primary keys), as well as composite foreign keys (a.k.a. composite FK, compound foreign keys or complex foreign keys.)

## Primary keys

Not all technology targets support primary keys. However, it might be useful to mark primary keys for documentation purposes.

[How-To: Composite key constraints](<https://youtu.be/WBYiHEXPTG0> "video")

To mark an attribute as a simple Primary key is easy: select the attribute in the ERD or the Object Browser, then check the Primary Key property in the Properties Pane. The attribute is moved to the top of the ERD entity box above a separator line, and is marked with a "pk" identifier. A simple PK generally appears in-line in DDL output.

As soon as an attribute in an entity has been marked as a PK, the primary key property of all other attributes is disabled:\
![Composite PKs property](<lib/Composite PKs property.png>)

If you want to mark as PK a different attribute, you must first uncheck the primary key property for the current attribute PK.

In many case, you may want to declare multiple columns to create a composite primary key (a.k.a. compound primary keys). The order of the keys is important, as well as making sure that the DDL output is properly assembled. As a result, the easy method described above for simple PKs cannot be used. Composite primary keys are declared at the entity level (table), in the Properties Pane tab "Composite keys":. In general, you may give a name to the composite key constraint.

![Composite PK creation](<lib/Composite PK creation.png>)

If a simple PK has already been declared for an attribute, the PK + sign will be disabled. Here again, you would need to first uncheck the primary key property for the current attribute PK, before you are allowed to create a composite PK.

To add multiple attributes a part of the composite PK, click the + sign and do a multiple select in the dialog (using Shift+click for contiguous, or Ctrl/Cmd+click for non-contiguous selections.) You may also add a key in a subsequent operation by clicking the + sign again.

You may change the order of the keys using the up and down arrows, delete keys from the selection by clicking the X, and choose additional options when available:\
![Composite PK selection](<lib/Composite PK selection.png>)

Depending on the target, other properties may be specified for the composite key constraint.

Composite PK constraints appear out-of-line in DDL output.

## Foreign key relationships

As described in [this page](RelationshiplinesinERdiagram.md), simple foreign key relationships can be defined in a number of different ways, via drag-and-drop in the ERD, using the Actions menu or the contextual menu, or via the Properties Pane.

If you have multiple columns in a primary key, it is likely that you have foreign key relationships that include multiple columns to form a composite FK.

When it comes to composite foreign key constraints (a.k.a compound foreign key constraints), it is not possible to define via drag-and-drop. Actually, you may start from a simple FK relationship defined with any of the of the methods above (including drag-and-drop), then enrich it with using the Properties Pane for the relationship by adding the parent and child attributes, using the + sign:\
![Relationships - composite foreign keys](<lib/Relationships - composite foreign keys.png>)

Composite FK constraints appear out-of-line in DDL output.
