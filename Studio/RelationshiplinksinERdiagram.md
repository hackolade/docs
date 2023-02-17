# Relationship links in ER diagram

## Create a Foreign Key relationship line

There are several ways to create a new relationship line between two entity boxes in the ER diagram of a model:

* with a **drag-and-drop** action in the ERD by selecting a child attribute and dragging while holding the mouse button towards a parent field with a compatible field type in another entity
* via the **Actions menu**:

![Menu - Add relationship](<lib/Menu%20-%20Add%20relationship.png>)

* by pressing the **shortcut Ctrl+R** and filling the properties in the right Pane
* with a click of the **toolbar icon** ![Image](<lib/Icons%20-%20addRelationship.jpeg>)&nbsp;
* with a **right-click** anywhere in the central pane to display the **contextual menu**

![ER Diagram - contextual menu - add relationsh](<lib/ER%20Diagram%20-%20contextual%20menu%20-%20add%20relationsh.png>)

&nbsp;

and choose 'Add Relationship'. &nbsp;

* from the Properties Pane of a child attribute

![Properties - Foreign Key relationship](<lib/Properties%20-%20Foreign%20Key%20relationship.png>)

&nbsp;

&nbsp;

### Relationship lines

Hackolade documents and helps visualize 2 types of relationships: foreign key and foreign master.&nbsp; The foreign key relationship is the unique identifier of the data.&nbsp; The foreign master relationship identifies the master for the duplicated field of the denormalized data.&nbsp;

&nbsp;

Hackolade adopts an IE-like notation (Information Engineering notation) applied to physical models in order to display multiplicities on each side of the relationship to represent the cardinality:&nbsp;

&nbsp;

| **Symbol** | **Description** |
| --- | --- |
| ![Relationship cardinality - one](<lib/Relationship%20cardinality%20-%20one.png>) | only one |
| &nbsp;![Relationship cardinality - many](<lib/Relationship%20cardinality%20-%20many.png>) | many |
| ![Relationship cardinality - zero-to-one](<lib/Relationship%20cardinality%20-%20zero-to-one.png>) | zero or one |
| ![Relationship cardinality - zero-to-many](<lib/Relationship%20cardinality%20-%20zero-to-many.png>) | zero or more |
| ![Relationship cardinality - one-to-many](<lib/Relationship%20cardinality%20-%20one-to-many.png>) | one or more |


&nbsp;

Typically, a relationship identifies a parent field within a parent collection on one side, and a child field within a child collection.&nbsp; Below is a simplified example... Say we have a master collection of customers, each identified by a unique id.&nbsp; When creating a document for each sales order, the customer name and address are repeated so as to avoid having to perform joins each time an order is accessed. &nbsp;

&nbsp;

![Relationships and denormalization](<lib/Relationships%20and%20denormalization.png>)

Three relationships can be documented in the model:

* a foreign key relationship for the customerID in the customers collection
* a foreign master relationship for the customerName
* a foreign master relationship for the customer address

&nbsp;

Occasionally, it might be needed to model recursive relationships where the parent and child collections are identical.&nbsp; In effect they are siblings:

![Relationships - siblings](<lib/Relationships%20-%20siblings.png>)

&nbsp;

The ERD entity boxes have been enriched with visual indicators.&nbsp; Here is a list of abbreviations:

**fk:** foreign key

**fm:** foreign master

**dk:** destination or denormalized key (parent of a foreign key.)&nbsp; Marks keys that are the parent of a foreign key or are denormalized elsewhere in the model.

**dm:** destination or denormalized master (parent of a foreign master.)&nbsp; Marks non-key attributes that are the parent of a foreign attribute or are denormalized elsewhere in the model. &nbsp;

&nbsp;

Both dk and dm attributes allow access to the Where-Used function in the contextual menu to find all the places in the model where they are denormalized.

&nbsp;

## Composite relationships

In RDBMS plugins, it is possible to represent composite (aka compound) foreign key relationships&nbsp;

&nbsp;

![Relationships - composite foreign keys](<lib/Relationships%20-%20composite%20foreign%20keys.png>)

&nbsp;

## Adjust relationship lines

With large and complex relational models, the automatic positioning of foreign key relationship lines might look insufficiently organized.&nbsp; As a user, you might want to adjust the lines differently.

&nbsp;

### Automatic or manual adjustments

You may move entity boxes around by dragging the box title bar, in which case the existing lines follow and auto-adjust.&nbsp; Or you may choose to adjust lines separately, as described below.

&nbsp;

![Image](<lib/Adjustable\_relationship\_lines\_medium.gif>)

&nbsp;

### Line geometries

In ERDs (hence excluding here graph diagrams, where edges tend to be curved), there are 2 geometries: orthogonal or oblique.

&nbsp;

An orthogonal line is one where the segments can only be vertical or horizontal. As a result, the angle between the line and the entity boxes can only be 90 degrees. An orthogonal line can be straight if it has a single segment. If multi-segment, the segments can only have a 90-degree angled elbow between them.

![ER lines - orthogonal](<lib/ER%20lines%20-%20orthogonal.png>)

&nbsp;

An oblique line must have a single segment and be straight. The angle between the line and an entity box can be anything, including 90 degrees in some cases.&nbsp; Oblique lines are often used in star schemas, but not only.

![ER lines - oblique](<lib/ER%20lines%20-%20oblique.png>)

&nbsp;

### Line anchors and segments

When you select a line, it gets highlighted, and nodes appear at each end, plus in middle segments, if any.&nbsp; Nodes are are used to move the anchors and segments, by click-and-drag.&nbsp; The mouse cursor when clicking indicates the possible direction(s) you may drag the node.

&nbsp;

Each line has 2 anchors, one on each end and represented by a node, attached to their respective entity box.&nbsp; Middle segments, i.e. segment other than the ones at the end of the line, each have a node in the middle of the segment.

&nbsp;

![ER lines - 3 segments](<lib/ER%20lines%20-%203%20segments.png>)

&nbsp;

A line may have one or more segments, depending on the relative positions of the entity boxes and the line anchors.&nbsp; We don't advise this, but it is possible for a line to have as many as 7 segments.

![ER lines - max segments](<lib/ER%20lines%20-%20max%20segments.png>)

&nbsp;

The number of segments is automatically adapted when you move anchors to a different side of its entity box.

&nbsp;

### Movements

You may move:

* the whole line, whether orthogonal or oblique,
* each anchor,
* or each individual segment of a line.

&nbsp;

To move a line, just grab anywhere in the line, and move in any direction.&nbsp; Depending on the direction you drag, segments and anchors are moved, anchors may change box sides,&nbsp; and the number of segments are automatically recaculated.

![ER lines - moving entire line](<lib/ER%20lines%20-%20moving%20entire%20line.png>)

&nbsp;

To move a single segment at a time, you may grab the node in the middle of the segment, or the anchor if it connects to an entity box. As you click on the node, the mouse cursor turns into a 2-headed arrow indicating the possible directions that you can drag.

![ER lines - 3 segments movements](<lib/ER%20lines%20-%203%20segments%20movements.png>)

&nbsp;

As segments get extended past the anchor of the line, the number of segments may be recalculated, and the anchor moved accordingly.&nbsp; The application will not allow a line to be hidden by any part of an entity box to which it is attached.

![ER lines - 4 segments movements](<lib/ER%20lines%20-%204%20segments%20movements.png>)

&nbsp;

Similarly, the number of segments can be reduced by aligning parallel segments, or by moving an anchor to a box side closer to the opposite andchor.

&nbsp;

Since an oblique line can only have a single segment, the anchors on each end can only be attached to the one or maximum 2 sides of the entity box that are facing the other anchor. &nbsp;

![ER lines - oblique movements](<lib/ER%20lines%20-%20oblique%20movements.png>)

&nbsp;

Each anchor can be moved, but is restricted to the one or maximum 2 sides of the entity box, so as to avoid having the line covered by any part of the entity box.

![Image](<lib/ER%20lines%20-%20oblique%20movements%20horizontal.png>)

&nbsp;

At any time, you may swicth geometry, which will restore the line to default anchors

![ER lines - style and gemetries](<lib/ER%20lines%20-%20style%20and%20gemetries.png>)

&nbsp;

&nbsp;

&nbsp;

