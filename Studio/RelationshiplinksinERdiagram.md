# Relationship links in ER diagram

There are several ways to create a new relationship between two collections in the ER diagram of a model:

\- by drag-and-drop action in the ERD by selecting a child field and dragging while holding the mouse button towards a parent field with a compatible field type in another collection

\- via the Actions menu:

![Image](<lib/Menu%20-%20Add%20relationship.png>)

\- by pressing the shortcut Ctrl+R

\- with a click of the toolbar icon ![Image](<lib/Icons%20-%20addRelationship.jpeg>)&nbsp;

\- or with a right-click anywhere in the central pane&nbsp;

![Image](<lib/ER%20Diagram%20-%20contextual%20menu%20-%20add%20relationsh.png>)

&nbsp;

and choose 'Add Relationship'. &nbsp;

&nbsp;

You then proceed to fill relationship properties.

&nbsp;

Hackolade documents and helps visualize 2 types of relationships: foreign key and foreign master.&nbsp; The foreign key relationship is the unique identifier of the data.&nbsp; The foreign master relationship identifies the master for the duplicated field of the denormalized data.&nbsp;

&nbsp;

Hackolade adopts an IE-like notation (Information Engineering notation) applied to physical models in order to display multiplicities on each side of the relationship to represent the cardinality:&nbsp;

&nbsp;

| **Symbol** | **Description** |
| --- | --- |
| ![Image](<lib/Relationship%20cardinality%20-%20one.png>) | only one |
| &nbsp;![Image](<lib/Relationship%20cardinality%20-%20many.png>) | many |
| ![Image](<lib/Relationship%20cardinality%20-%20zero-to-one.png>) | zero or one |
| ![Image](<lib/Relationship%20cardinality%20-%20zero-to-many.png>) | zero or more |
| ![Image](<lib/Relationship%20cardinality%20-%20one-to-many.png>) | one or more |


&nbsp;

Typically, a relationship identifies a parent field within a parent collection on one side, and a child field within a child collection.&nbsp; Below is a simplified example... Say we have a master collection of customers, each identified by a unique id.&nbsp; When creating a document for each sales order, the customer name and address are repeated so as to avoid having to perform joins each time an order is accessed. &nbsp;

&nbsp;

![Image](<lib/Relationships%20and%20denormalization.png>)

Three relationships can be documented in the model:

* a foreign key relationship for the customerID in the customers collection
* a foreign master relationship for the customerName
* a foreign master relationship for the customer address

&nbsp;

Occasionally, it might be needed to model recursive relationships where the parent and child collections are identical.&nbsp; In effect they are siblings:

![Image](<lib/Relationships%20-%20siblings.png>)

&nbsp;

The ERD entity boxes have been enriched with visual indicators.&nbsp; Here is a list of abbreviations:

fk: foreign key

fm: foreign master

dk: denormalized key (parent of a foreign key.)&nbsp; Marks keys that are denormalized elsewhere in the model.

dm: denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are denormalized elsewhere in the model. &nbsp;

&nbsp;

Both dk and dm attributes allow access to the Where-Used function in the contextual menu to find all the places in the model where they are denormalized.

&nbsp;

In RDBMS plugins, it is possible to represent composite (or compound) foreign key relationships&nbsp;

&nbsp;

![Image](<lib/Relationships%20-%20composite%20foreign%20keys.png>)


***
_Created with the Personal Edition of HelpNDoc: [Easy to use tool to create HTML Help files and Help web sites](<https://www.helpndoc.com/help-authoring-tool>)_
