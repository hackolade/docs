# Define composite key constraints

## Primary keys

Not all technology targets support primary keys.&nbsp; However, it might be useful to mark primary keys for documentation purposes.

&nbsp;

You may also view this [short video](<https://www.youtube.com/watch?v=WBYiHEXPTG0> "target=\"\_blank\"") on YouTube.

&nbsp;

To mark an attribute as a simple Primary key is easy: select the attribute in the ERD or the Object Browser, then check the Primary Key property in the Properties Pane.&nbsp; The attribute is moved to the top of the ERD entity box above a separator line, and is marked with a "pk" identifier.&nbsp; A simple PK generally appears in-line in DDL output.

&nbsp;

As soon as an attribute in an entity has been marked as a PK, the primary key property of all other attributes is disabled:

![Composite PKs property](<lib/Composite%20PKs%20property.png>)

&nbsp;

If you want to mark as PK a different attribute, you must first uncheck the primary key property for the current attribute PK.

&nbsp;

When the target supports composite keys (a.k.a. compound keys), the order of the keys is important, as well as making sure that the DDL output is properly assembled.&nbsp; As a result, the easy method described above for simple PKs cannot be used.&nbsp; Composite keys are declared at the entity level, in the Properties Pane tab "Composite keys":.&nbsp; In general, you may give a name to the composite key constraint.

&nbsp;

![Composite PK creation](<lib/Composite%20PK%20creation.png>)

&nbsp;

If a simple PK has already been declared for an attribute, the PK + sign will be disabled.&nbsp; Here again, you would need to first uncheck the primary key property for the current attribute PK, before you are allowed to create a composite PK.

&nbsp;

To add multiple attributes a part of the composite PK, click the + sign and do a multiple select in the dialog (using Shift+click for contiguous, or Ctrl/Cmd+click for non-contiguous selections.)&nbsp; You may also add a key in a subsequent operation by clicking the + sign again.

&nbsp;

You may change the order of the keys using the up and down arrows, delete keys from the selection by clicking the X, and choose additional options when available:

![Composite PK selection](<lib/Composite%20PK%20selection.png>)

&nbsp;

Depending on the target, other properties may be specified for the composite key constraint.

&nbsp;

Composite PK constraints appear out-of-line in DDL output.

&nbsp;

## Foreign key relationships

As described in [this page](<RelationshiplinksinERdiagram.md>), simple foreign key relationships can be defined in a number of different ways, via drag-and-drop in the ERD, using the Actions menu or the contextual menu, or via the Properties Pane.

&nbsp;

When it comes to composite foreign keys, it is not possible to define via drag-and-drop.&nbsp; Actually, you may start from a simple FK relationship defined&nbsp; with any of the of the methods above (including drag-and-drop), then enrich it with using the Properties Pane for the relationship by adding the parent and child attributes, using the + sign:

![Relationships - composite foreign keys](<lib/Relationships%20-%20composite%20foreign%20keys.png>)

&nbsp;

Composite FK constraints appear out-of-line in DDL output.

