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

![Menu - Actions - Add Collection](<lib/Menu%20-%20Actions%20-%20Add%20Collection.png>)

\- by pressing the shortcut Ctrl/Cmd+L

\- with a click of the toolbar icon ![Icons - addCollection](<lib/Icons%20-%20addCollection.jpeg>)&nbsp;

\- or with a right-click anywhere in the central pane&nbsp;

![ER Diagram - contextual menu - add collection](<lib/ER%20Diagram%20-%20contextual%20menu%20-%20add%20collection.png>)

and choose 'Add Collection'. &nbsp;

&nbsp;

You can proceed to fill collection properties and create fields.

&nbsp;

The usual edit actions are possible on an existing collection: cut, copy, paste, duplicate, delete.

&nbsp;

To move a collection in the ER diagram, hover the mouse to the collection title so the mouse cursor becomes a move cross:

![ER Diagram - move collection](<lib/ER%20Diagram%20-%20move%20collection.png>)

then click and hold your left mouse button, then drag the collection where you'd like to place it.&nbsp; If relationships are attached, they follow the collection and reposition themselves dynamically.

&nbsp;

The name bar of a collection is blue, unless changed in the Options tab.&nbsp; When you select a collection by clicking on the name bar, the related properties pane gets displayed in the Properties Pane on the right.&nbsp; The collection window can be resized so the content fits in.

&nbsp;

![ER Diagram - full size collection box](<lib/ER%20Diagram%20-%20full%20size%20collection%20box.png>)

&nbsp;

Otherwise, vertical and/or horizontal scroll bars appear:

![ER Diagram - reduced size collection box](<lib/ER%20Diagram%20-%20reduced%20size%20collection%20box.png>)

&nbsp;

The collection window position and size are saved with the model, so they can be retrieved next time it is consulted.

&nbsp;

To open a new tab with the hierarchical schema view of a collection, you double-click on the collection name bar, or right-click then choose Open in new tab, or by clicking on the icon

![ERD - open in a new tab](<lib/ERD%20-%20open%20in%20a%20new%20tab.png>)

&nbsp;

&nbsp;

A couple of drag-and-drop operations are possible in the ERD:

\- using the handle on the left of each attribute:

![ERD - attribute drag-and-drop](<lib/ERD%20-%20attribute%20drag-and-drop.png>)

you may move an attribute up or down within an entity, or to another entity, provided that there are no conflicts.&nbsp; It is not possible to move attributes across different views.&nbsp; By pressing the ctrl key, it is possible to perform a copy operation.

\- using the attribute name, to create a relationship.

&nbsp;

Several of the controls available in the [hierarchical schema view](<Attributeboxesinhierarchicalsche.md>) are also available from the ERD view and the Object Browser.

&nbsp;

## Visual indicators

The ERD entity boxes have been enriched with visual indicators.&nbsp; Here is a list of abbreviations:

pk: primary key

fk: foreign key

fm: foreign master

dk: destination or denormalized key (parent of a foreign key.)&nbsp; Marks keys that are the parent of a foreign key or are denormalized elsewhere in the model.

dm: destination or denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are the parent of a foreign attribute or are denormalized elsewhere in the model. &nbsp;

PK: partition key, where applicable

CK: clustering key, where applicable

sk: sort key, where applicable

\*: required attribute

\+: only in Avro: null allowed

Ix,y: indexed attribute, with x= index number, y= attribute number in a composite index

&nbsp;

Both dk and dm attributes allow access to the Where-Used function in the contextual menu to find all the places in the model where they are denormalized.

&nbsp;

You may arrange and align entity boxes in the ERD using the menu option Edit \> Align, or the arrange toolbar buttons:

![ERD arrange entities toolbar button](<lib/ERD%20arrange%20entities%20toolbar%20button.png>)&nbsp; Options include: align left, align center, align right, align top, align middle, align bottom, distribute horizontally, distribute vertically, distribute orthogonally.

&nbsp;

&nbsp;

## Display options

There are different ways to customize your ERD: with the Options tab in the properties pane, you may change the color and font style.&nbsp; You maybe also modify the sizing behavior when adding or removing attributes, if you do not want the box to automatically adjust.

![ERD display options tab-font style and color](<lib/ERD%20display%20options%20tab-font%20style%20and%20color.png>)

&nbsp;

You may also change the display of the ERD:

&nbsp;

![ERD display options toolbar](<lib/ERD%20display%20options%20toolbar.png>)

&nbsp;

to toggle the display of:

\- business names versus technical names

\- the handle allowing to drag-and-drop attributes within the entity

\- annotations

\- materialized/read-only views where applicable

\- foreign master relationships (when denormalization has taken place)

\- data types

\- attributes

\- non-primary key attributes

\- non-required attributes

&nbsp;

## Diagram Views

Description of this feature, to create subsets of the main diagram in separate views, has now been moved [here](<DiagramViews.md>).

&nbsp;

