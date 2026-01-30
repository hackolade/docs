# Entity boxes in ER diagram

In Hackolade Studio, we use the generic name of "entity" to designate objects for which data is collected or transmitted.&nbsp; In physical data models, this entity bears a different name depending on the target technology: table in relational and analytics databases, collection in document database (MongoDB, Couchbase, DocumentDB, etc...), node in graph database, record in Avro, message in Parquet and Protobuf, request and response in REST APIs and GraphQL, class in RDF triple stores, etc...

## Create an entity

In Hackolade Studio, there are many ways to add an entity to the central pane canvas:

\- menu : Action \> Add Entity (added at default location)

\- keyboard shortcut (Ctrl/Cmd+L): added at location of mouse cursor

\- toolbar: Add Entity icon: added at location of mouse cursor

\- Diagram Object pane: Add entity via click (added to default location), or via drag-and-drop to the location of your choice

\- Object Browser pane: right-click on container name and use contextual menu (added at default location)

\- Central pane: right-click on model name and use contextual menu (added at default location)

&nbsp;

&nbsp;

\- via the Actions menu:

![Menu - Actions - Add Collection](<lib/Menu - Actions - Add Collection.png>)

\- by pressing the shortcut Ctrl/Cmd+L

\- with a click of the toolbar icon ![Icons - addCollection](<lib/Icons - addCollection.jpeg>)&nbsp;

\- or with a right-click anywhere in the central pane&nbsp;

![ER Diagram - contextual menu - add collection](<lib/ER Diagram - contextual menu - add collection.png>)

and choose 'Add Collection'. &nbsp;

&nbsp;

You can proceed to fill collection properties and create fields.

&nbsp;

The usual edit actions are possible on an existing collection: cut, copy, paste, duplicate, delete.

&nbsp;

To move a collection in the ER diagram, hover the mouse to the collection title so the mouse cursor becomes a move cross:

![ER Diagram - move collection](<lib/ER Diagram - move collection.png>)

then click and hold your left mouse button, then drag the collection where you'd like to place it.&nbsp; If relationships are attached, they follow the collection and reposition themselves dynamically.

&nbsp;

The name bar of a collection is blue, unless changed in the Options tab.&nbsp; When you select a collection by clicking on the name bar, the related properties pane gets displayed in the Properties Pane on the right.&nbsp; The collection window can be resized so the content fits in.

&nbsp;

![ER Diagram - full size collection box](<lib/ER Diagram - full size collection box.png>)

&nbsp;

Otherwise, vertical and/or horizontal scroll bars appear:

![ER Diagram - reduced size collection box](<lib/ER Diagram - reduced size collection box.png>)

&nbsp;

The collection window position and size are saved with the model, so they can be retrieved next time it is consulted.

&nbsp;

To open a new tab with the hierarchical schema view of a collection, you double-click on the collection name bar, or right-click then choose Open in new tab, or by clicking on the icon

![ERD - open in a new tab](<lib/ERD - open in a new tab.png>)

&nbsp;

&nbsp;

A couple of drag-and-drop operations are possible in the ERD:

\- using the handle on the left of each attribute:

![ERD - attribute drag-and-drop](<lib/ERD - attribute drag-and-drop.png>)

you may move an attribute up or down within an entity, or to another entity, provided that there are no conflicts.&nbsp; It is not possible to move attributes across different views.&nbsp; By pressing the ctrl key, it is possible to perform a copy operation.

\- using the attribute name, to create a relationship.

&nbsp;

Several of the controls available in the [hierarchical schema view](<Attributeboxesinhierarchicalsche.md>) are also available from the ERD view and the Object Browser.

&nbsp;

## Visual indicators

The ERD entity boxes have been enriched with visual indicators to facilitate the interpretation of ERDs.

&nbsp;

When you deactivate an object (container, entity, view, attribute), an icon is displayed accordingly:

&nbsp;

![ERD visual indicator deactivated object](<lib/ERD visual indicator deactivated object.png>)

&nbsp;

&nbsp;

Similarly, in a model derived from polyglot, you may have added attributes that don't exist in the parent polyglot model (this is one of the "deviations" that we allow in derived model -- you may alos modify some of an attribute's properties, or you may delete an attribute if not pertinent in the derived model.)&nbsp; Those attributes are preceded with a + sign icon:

![ERD visual indicator added in derived model](<lib/ERD visual indicator added in derived model.png>)

&nbsp;

For indicators appearing after the attribute name, here is a list of abbreviations:

pk: primary key

fk: foreign key

uk: unique key

fm: [foreign master](<Relationshipsanddenormalization.md>)

dk: destination or denormalized key (parent of a foreign key.)&nbsp; Marks keys that are the parent of a foreign key or are denormalized elsewhere in the model.

dm: destination or denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are the parent of a foreign attribute or are denormalized elsewhere in the model. &nbsp;

PK: partition key, where applicable

CK: clustering key, where applicable

sk: sort key, where applicable

\*: required attribute

\+: only in Avro: null allowed

\#: indication of a [pattern field](<Whatsapatternfield.md>)

Ix,y: indexed attribute, with x= index number, y= attribute number in a composite index

&nbsp;

Both dk and dm attributes allow access to the Where-Used function in the contextual menu to find all the places in the model where they are denormalized.

&nbsp;

## Arrange entity boxes

You may arrange and align entity boxes in the ERD using the menu option Edit \> Align, or the arrange toolbar buttons:

![ERD arrange entities toolbar button](<lib/ERD arrange entities toolbar button.png>)&nbsp; Options include: align left, align center, align right, align top, align middle, align bottom, distribute horizontally, distribute vertically, distribute orthogonally.

&nbsp;

&nbsp;

## Display options

There are different ways to customize your ERD: with the Options tab in the properties pane, you may change the color and font style.&nbsp; You maybe also modify the sizing behavior when adding or removing attributes, if you do not want the box to automatically adjust.

![ERD display options tab-font style and color](<lib/ERD display options tab-font style and color.png>)

&nbsp;

You may also change the display of the ERD and [ERDVs](<DiagramViews.md>).&nbsp; Each ERD and ERDV persists in the model file its own set of Display Options (except business vs technical name display which is controlled by Naming Conventions for the model target), which may be helpful for data model storytelling. &nbsp;

&nbsp;

Display Options are accessible from 3 different places:

&#49;) from the Display Options button in the toolbar

&nbsp;

![ERD display options toolbar](<lib/ERD display options toolbar.png>)

&nbsp;

&#50;) from the View \> Display Options menu:

![ERD display options view menu](<lib/NewItem 27.png>)

&nbsp;

&nbsp;

&#51;) from Tools \> Options \> Display \> ERD(V):

![Image](<lib/ERD display options tools options.png>)

&nbsp;

These 3 methods are of course connected to each other, and making a change in one place gets dynamically reflected in the other methods.

&nbsp;

Some display options are multiple choices, while others simple toggles, and others are mutually exclusive.

&nbsp;

Mutually exclusive display options:

* business names versus technical names: this option affects, non only the ERD and ERDVs, but also the Object Browser (including the OB search) and the schema tree view.&nbsp; Note that this choice, contrary to the other ones below, is specific to each target for which [Naming Conventions](<Namingconventions.md>) have been enabled through through Tools \> Options \> Naming Conventions
* entity box content with attributes, description, or empty: by default, ERDs list attributes for entities, but it is also possible to replace the attributes by the entity description.&nbsp; Or to just display the box without any content, for a more conceptual view of the ERD.

&nbsp;

Toggles:

* diagram objects: you may toggle the display of deactivated modeling objects (containers, entities, attributes, views, relationships), as well as symbols (annotations and rectangles) and database views if applicable to the target \[default = enabled\]
* drag-and-drop handles to move attributes within an entity or from one entity to another, or to hide the handle for a more aesthetic and clean look \[default = enabled\]
* data types: allows to hide data types for attributes, for a more conceptual/logical view of the ERD \[default = enabled\]
* primary key(s) at top: if you don't like for PKs to be automatically moved to the top of the attribute list for an entity, regardless of where in the list they were originally created, you may toggle this option so the attribute (and the DDL schema output) retains its original position in the list \[default = enabled\]
* relationship names \[default = disabled\]
* "[foreign master](<Relationshipsanddenormalization.md>)" relationships (when denormalization has taken place) \[default = enabled\]

&nbsp;

Multiple choices: by default all of the attributes below are displayed.&nbsp; But you may one to only show some while excluding the others.

* primary keys
* foreign keys
* unique keys
* required attributes, also known as Not NULL, or mandatory

&nbsp;

## Diagram Views

Description of this feature, to create subsets of the main diagram in separate views, has now been moved [here](<DiagramViews.md>).

&nbsp;

