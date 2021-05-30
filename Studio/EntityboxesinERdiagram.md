# Entity boxes in ER diagram

There are several ways to create a new collection in the ER diagram of a model:

\- via the Actions menu:

![Image](<lib/Menu%20-%20Actions%20-%20Add%20Collection.png>)

\- by pressing the shortcut Ctrl+L

\- with a click of the toolbar icon ![Image](<lib/Icons%20-%20addCollection.jpeg>)&nbsp;

\- or with a right-click anywhere in the central pane&nbsp;

![Image](<lib/ER%20Diagram%20-%20contextual%20menu%20-%20add%20collection.png>)

and choose 'Add Collection'. &nbsp;

&nbsp;

You can proceed to fill collection properties and create fields.

&nbsp;

The usual edit actions are possible on an existing collection: cut, copy, paste, duplicate, delete.

&nbsp;

To move a collection in the ER diagram, hover the mouse to the collection title so the mouse cursor becomes a move cross:

![Image](<lib/ER%20Diagram%20-%20move%20collection.png>)

then click and hold your left mouse button, then drag the collection where you'd like to place it.&nbsp; If relationships are attached, they follow the collection and reposition themselves dynamically.

&nbsp;

The name bar of a collection is blue.&nbsp; When you select a collection by clicking on the name bar, it becomes green and the related properties pane gets displayed.&nbsp; The collection window can be resized so the content fits in.

&nbsp;

![Image](<lib/ER%20Diagram%20-%20full%20size%20collection%20box.png>)

&nbsp;

Otherwise, vertical and/or horizontal scroll bars appear:

![Image](<lib/ER%20Diagram%20-%20reduced%20size%20collection%20box.png>)

&nbsp;

The collection window position and size are saved with the model, so they can be retrieved next time it is consulted.

&nbsp;

To get more information about a field, simply hover your mouse cursor over the desired field, and a box pops up with more information:

![Image](<lib/ER%20Diagram%20-%20collection%20with%20field%20info.png>)

&nbsp;

To open a new tab with the hierarchical schema view of a collection, you double-click on the collection name bar, or right-click then choose Open in new tab.

&nbsp;

Most of the controls available in the [hierarchical schema view](<Attributeboxesinhierarchicalsche.md>) are also available from the ERD view and the Object Browser.

&nbsp;

The ERD entity boxes have been enriched with visual indicators.&nbsp; Here is a list of abbreviations:

pk: primary key

fk: foreign key

fm: foreign master

dk: denormalized key (parent of a foreign key.)&nbsp; Marks keys that are denormalized elsewhere in the model.

dm: denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are denormalized elsewhere in the model. &nbsp;

\*: required attribute

\+: only in Avro: null allowed

Ix,y: indexed attribute, with x= index number, y= attribute number in a composite index

&nbsp;

Both dk and dm attributes allow access to the Where-Used function in the contextual menu to find all the places in the model where they are denormalized.

&nbsp;

## ER Diagram Views

With v4.3.2, Hackolade has introduced the possibility to add separate ER Diagram Views (ERDV): a subset of entities selected from the main ER diagram, to help manage large models by focusing on a smaller set of entities, by domain or subject.&nbsp; Entities may appear in multiple Diagram Views.&nbsp; Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present.&nbsp;

&nbsp;

A new Diagram View can be added in different ways:

&#49;) from the Actions menu option:

![Image](<lib/Menu%20Actions.png>)

&nbsp;

&#50;) from the toolbar:

![Image](<lib/Toolbar%20Create%20Diagram%20View.png>): toolbar button

&nbsp;

&#51;) from the Object Browser or the main Entity Relationship Diagram:

by selecting one or more entities, then doing a right-click on an entity to display the contextual menu:

![Image](<lib/Contextual%20menu%20add%20ERDV.png>)

&nbsp;

Editing an ER Diagram View name or membership is done from the contextual menu of the Object Browser:

![Image](<lib/Contextual%20menu%20edit%20ERDV.png>)

&nbsp;

&nbsp;

In this dialog, you may edit the name of the Diagram View and modify the selection of the entities selected:

![Image](<lib/ERDV%20editor.png>)

