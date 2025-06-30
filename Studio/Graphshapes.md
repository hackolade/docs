# Graph shapes

With the addition of Neo4j, Hackolade introduced a new Graph Diagram view with circular node labels.&nbsp; Each node label contains 5 control buttons, and each relationship type line has 2 control buttons.&nbsp; Depending on the database, nodes are also known as vertex (vertices), while relationships may also be known as edges.

&nbsp;

Since version 3.5.4, we implemented force-directed layout algorithms with spring-like attractive forces, see this [example](<https://hackolade.com/img/Force-directed\_animated\_compressed.gif> "target=\"\_blank\"").&nbsp; The controls are details below

&nbsp;

## Node label controls

![Graph node label](<lib/Graph node label.png>)

Since version 3.5.0, the node label controls only appear when you hover the mouse pointer on the node label circle.

##### Display node label properties box

![Graph display node label property](<lib/Graph display node label property.png>) This icon lets you toggle the properties for the selected node label.&nbsp;

&nbsp;

##### Create new edge label (aka relationship type)

![Graph create relationship type icon](<lib/Graph create relationship type icon.png>) Use this icon to activate the creation of a relationship type, originating from this node label.&nbsp; The next node label will be target of the relationship: if you select the same node label, it will create a recursive relationship, otherwise you should select another node label. &nbsp;

&nbsp;

Since version 3.5.0 you may also create a relationship type line plus a new target node label in one single operation, by clicking anywhere in the workspace except on a node label.

&nbsp;

##### Change size of node label circle

![Graph change size of node label icon](<lib/Graph change size of node label icon.png>)This icon toggles the display of a circle size picker:

&nbsp;

![Graph node label size palette](<lib/Graph node label size palette.png>)

If you will want to apply a new size to all node labels in the model, check the box prior to choosing the new size.

&nbsp;

##### Change color of node label circle

![Graph change color of node label icon](<lib/Graph change color of node label icon.png>) This icon toggles the display of a color picker:

![Graph node label color palette](<lib/Graph node label color palette.png>)

&nbsp;

If you will want to apply a new color to all node labels in the model, check the box prior to choosing the new color.

&nbsp;

##### Pin node in place (only when force-directed layout is enabled)

![Graph node label pin](<lib/Graph node label pin.png>)&nbsp; This icon allows you to pin in place the node label.&nbsp; It will not move when other nodes are dragged, using the force-directed layout.

&nbsp;

## Node label subclass &nbsp;

For a given node label with its properties, there may be a need to declare additional node labels.&nbsp; These sub-nodes are a business-driven representation, and do not result in physical storage impacts.&nbsp; They are not forward-engineered, and cannot be inferred during reverse-engineering.&nbsp; Also, sub-nodes do have any properties.

&nbsp;

![Graph subclasses](<lib/Graph subclasses.png>)

&nbsp;

You may edit the edge label in the properties pane of the sub-node:

![Graph subclass label](<lib/Graph subclass label.png>)

&nbsp;

&nbsp;

&nbsp;

## Edge labels (aka relationship types) line controls

&nbsp;

![Graph relationship type](<lib/Graph relationship type.png>)

&nbsp;

Starting with version 3.5.0, you may toggle between 2 positions for the relationship line name: horizontal, or along the line.&nbsp; You may also toggle the relationship line name ON or OFF.

&nbsp;

##### Change relationship type line thickness

![Graph relationship line thickness icon](<lib/Graph relationship line thickness icon.png>) This icon toggles the display of a line thickness picker

&nbsp;

&nbsp;

![Graph relationship line thickness palette](<lib/Graph relationship line thickness palette.png>)

If you will want to apply a new thickness to all relationship types in the model, check the box prior to choosing the new thickness.

&nbsp;

##### Display relationship type properties box

![Graph relationship type property box icon](<lib/Graph relationship type property box icon.png>) This icon toggles the display of the properties for the selected relationship type

&nbsp;

![Graph relationship properties](<lib/Graph relationship properties.png>)

&nbsp;

##### Reverse relationship

![Graph relationship type reverse direction ico](<lib/Graph relationship type reverse direction ico.png>) This icon reverses the direction of the relationship type.&nbsp; For recursive relationships, this control allows to toggle between 2 modes: a loop or a duplicate node label:

&nbsp;

![Graph recursive loop](<lib/Graph recursive loop.png>) and&nbsp; ![Graph recursive node label](<lib/Graph recursive node label.png>)

&nbsp;

&nbsp;

## View controls

Additional controls are available in the toolbar (and also in the View menu):

![Graph view controls toolbar icons](<lib/Graph view controls toolbar icons.png>)

&nbsp;

\- Toggle force-directed layout

\- Toggle display of relationship type name

\- Show relationship type name along the line vs always horizontal.

\- Toggle display of properties boxes.&nbsp; Once all boxes are displayed, you may individually hide selected boxes.&nbsp; In order to bring a box to the front, individually hide it then redisplay.

&nbsp;

## Force-directed layout

A force-directed layout tends to arrange nodes in such a way that highly connected nodes are placed more to the center of the visualization, whereas less connected ones are placed in the periphery.&nbsp; It consists of 3 different forces: edges act as springs, while nodes repel each other, and drag forces ensure that nodes settle.&nbsp; The forces are interactively applied, resulting in a fluid animation that dynamically positions the nodes. See example [here](<https://hackolade.com/img/Force-directed\_animated\_compressed.gif> "target=\"\_blank\"").

&nbsp;

Beside the ability to move shapes as seen in the example, you have several additional controls:

a) you may pin selected nodes so they are not affected by the force-directed layout.&nbsp; This is done by hovering the mouse cursor over the node label and clicking the pin icon ![Graph node label pin](<lib/Graph node label pin.png>)

b) you may move a single node label (without the others moving as a result of the forced-directed layout) by holding the shift key while selecting and moving the node label.

c) you may adjust the length of the relationship lines with a slider that appears when you hove the toolbar button

![Graph shapes - toggle force-directed layout](<lib/Graph shapes - toggle force-directed layout.png>)

&nbsp;

&nbsp;

## Graph diagram views

Similar to ER Diagram Views, we introduced with v5.2.7 the possibility to select and view in a separate tab a subset of vertices/nodes selected from the main graph diagram.&nbsp; This feature helps manage large models by focusing on a smaller set of vertices/nodes, by domain or subject.&nbsp; Vertices/nodes and their related edges/relationships may appear in multiple Diagram Views.&nbsp; Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present. &nbsp; This feature is often called "subject area" or "sub-model" in legacy data modeling tools.

&nbsp;

You may refer to [this page](<EntityboxesinERdiagram.md>) for more details, section ER Diagram Views.

