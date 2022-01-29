# Entity boxes in ER diagram

There are several ways to create a new collection in the ER diagram of a model:

\- via the Actions menu:

![Menu - Actions - Add Collection](<lib/Menu%20-%20Actions%20-%20Add%20Collection.png>)

\- by pressing the shortcut Ctrl+L

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

The name bar of a collection is blue.&nbsp; When you select a collection by clicking on the name bar, it becomes green and the related properties pane gets displayed.&nbsp; The collection window can be resized so the content fits in.

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

The ERD entity boxes have been enriched with visual indicators.&nbsp; Here is a list of abbreviations:

pk: primary key

fk: foreign key

fm: foreign master

dk: denormalized key (parent of a foreign key.)&nbsp; Marks keys that are denormalized elsewhere in the model.

dm: denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are denormalized elsewhere in the model. &nbsp;

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

## ER Diagram Views

With v4.3.2, Hackolade has introduced the possibility to add separate ER Diagram Views (ERDV): a subset of entities selected from the main ER diagram, to help manage large models by focusing on a smaller set of entities, by domain or subject.&nbsp; Entities may appear in multiple Diagram Views.&nbsp; Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present.&nbsp;

&nbsp;

A new Diagram View can be added in different ways:

&#49;) from the Actions menu option:

![Menu Actions](<lib/Menu%20Actions.png>)

&nbsp;

&#50;) from the toolbar:

![Toolbar Create Diagram View](<lib/Toolbar%20Create%20Diagram%20View.png>): toolbar button

&nbsp;

&#51;) from the Object Browser or the main Entity Relationship Diagram:

by selecting one or more entities, then doing a right-click on an entity to display the contextual menu:

![Contextual menu add ERDV](<lib/Contextual%20menu%20add%20ERDV.png>)

&nbsp;

Editing an ER Diagram View name or membership is done from the contextual menu of the Object Browser:

![Contextual menu edit ERDV](<lib/Contextual%20menu%20edit%20ERDV.png>)

&nbsp;

&nbsp;

In this dialog, you may edit the name of the Diagram View and modify the selection of the entities selected:

![ERDV editor](<lib/ERDV%20editor.png>)

