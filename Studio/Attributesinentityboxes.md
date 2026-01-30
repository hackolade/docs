# Attributes in entity boxes

In Hackolade Studio, we use the generic name of "attribute" for an individual piece of information whose values identify, describe, or measure instances of an entity objects.&nbsp; In physical data models, this attribute bears a different name depending on the target technology: column in relational and analytics databases, field in document and graph databases and also in Avro and REST APIs, etc...

&nbsp;

## Create an attribute

In Hackolade Studio, there are many ways to add an attribute to an entity in the central pane canvas:

\- menu : Action \> Add Attribute (appended at the bottom of the entity)

\- keyboard shortcut (Ctrl/Cmd+R): appended at the bottom of the entity

\- toolbar: Add Attribute icon: appended at the bottom of the entity

\- Diagram Object pane: Add attribute via click (appended at the bottom of the entity)

\- Object Browser pane: right-click on entity name and use contextual menu (appended at the bottom of the entity)

\- Central pane: right-click on model name and use contextual menu (appended at the bottom of the entity)

&nbsp;

It is also possible to insert an attribute above the currently selected one.&nbsp; And for complex data types (objects and arrays), it is possible to add "child" attributes.&nbsp; For complex data types, it often found to be more convenient to maintain attributes in the [hierarchical schema view](<Attributeboxesinhierarchicalsche.md>).

&nbsp;

## Move an attribute

It is easy to modify the order of attributes.&nbsp; This can be done in different ways:

* to reorder attributes within a level, select the attribute in the ERD or in the Object Browser, then use the Move Up or Move Down icons in the toolbar: ![Toolbar field order up-down arrows](<lib/DTD field order arrows.png>)
* using the handle on the left of each attribute in the ERD:\
![ERD - attribute drag-and-drop](<lib/ERD - attribute drag-and-drop.png>)\
you may move an attribute up or down within an entity, or to another entity, provided that there are no conflicts.&nbsp; It is not possible to move attributes across different views.&nbsp; By pressing the Ctrl/Cmd key+select the handle with the mouse, it is possible to perform a copy operation. \
**Note:** if the handle does not show, you may toggle its display through the Display Options icon in the toolbar or via Tools \> Options \> Display.
* in the hierarchical schema tree view, you can select an attribute box to move it up or down within the same level, or to another compatible level.&nbsp; By pressing the Ctrl/Cmd key+select the handle with the mouse, it is possible to perform a copy operation.\
![Image](<lib/Schema tree view - attribute drag-n-drop.png>)
* in the Object Browser, by right-clicking the entity name and choosing the option to Alpha Sort Attributes/column/fields\
![Object Browser - alpha sort attributes](<lib/Object Browser - alpha sort attributes.png>)

&nbsp;

&nbsp;

&nbsp;

