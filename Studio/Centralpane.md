# Central pane

The central pane is where you can visualize your data model and the schema for each individual entity.&nbsp; The central pane adapts to the selected top and bottom tabs:

&nbsp;

## Entity Relationship Diagram view

Hackolade has this unique capability to represent hierarchical structures in entity-relationship diagrams in a user-friendly manner.&nbsp; This is an improvement on traditional ERD tools which will represent each nested object in a separate box of the ERD.

&nbsp;

The central pane displays the ERD, letting you create, maintain and visualize your data structure:

![Central pane - ER diagram](<lib/Central pane - ER diagram.png>)

&nbsp;

With large models, it is possible that, to fit the entire ERD on screen, the zoom level does not allow to read the information.&nbsp; For performance reasons, Hackolade displays a sketchy rendition of the diagram:

![Central pane - sketchy ERD](<lib/Central pane - sketchy ERD.png>)

&nbsp;

You may control the the zoom level range of the sketchy rendition via a parameter in Tools \> Options \> General.

&nbsp;

## Hierarchical schema view

For each entity in your diagram, it can be very handy to visualize and maintain the structure in a separate tab with the hierarchical schema view of the entity schema:

![Central pane - hierarchical schema view](<lib/Central pane - hierarchical schema view.png>)

&nbsp;

From the ERD, you may open the hierarchical schema view in a number of ways:

\- double click on the entity title\
\- click once on the middle-right icon in the entity title\
\- right-click on the entity title and choose Open in new tab\
\- right-click on the entity name in the Object Browser on the left, and choose Open in new tab, or double-click on the entity name

&nbsp;

![JSON Tree in new tab](<lib/JSON Tree in new tab.png>)

&nbsp;

&nbsp;

&nbsp;

### JSON Preview

In this upper tab dedicated to a specific entity, there are several lower tabs.&nbsp; The JSON Preview tab provides 2 side-by-side panes: one for the JSON Schema of the entity, and the other tab is for a sample JSON document of the structure:

![Central pane - JSON Preview](<lib/Central pane - JSON Preview.png>)

&nbsp;

&nbsp;

Several options are available for the display of the JSON Preview lower tab:

Hackolade extends JSON Schema for data types as well as non-standard keywords.&nbsp; When displaying or exporting JSON Schema, you may choose the compliance level:

\- standard: only JSON Schema keywords and data types are used -- this output should pass validation with standard validators

\- full: custom keywords are also listed for a full view of the schema, but only standard JSON data types are used -- this output should pass validation as long as additionalProperties are set to true

\- extended: data types are specific to the target of the model, plus internal properties and keywords are also listed. &nbsp;

&nbsp;

**Important note:** in extended compliance, it is normal that the exported JSON Schema does not pass the test of validators.&nbsp; This is because data types used for a given target may be non-JSON data types.&nbsp; For example ObjectId for MongoDB, or UUID in Cassandra, etc...

&nbsp;

&nbsp;

JSON Schema output is dynamically adapted to the selected specification:

\- [draft-04](<https://json-schema.org/specification-links.html#draft-4> "target=\"\_blank\"")

\- [draft-06](<https://json-schema.org/specification-links.html#draft-6> "target=\"\_blank\"")

\- [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\"")

\- [2019-09](<https://json-schema.org/specification-links.html#2019-09-formerly-known-as-draft-8> "target=\"\_blank\"")

\- [2020-12](<https://json-schema.org/specification-links.html#2020-12> "target=\"\_blank\"")

&nbsp;

When displaying or exporting JSON Schema, the references can used as described or transformed:

\- referenced: definitions are referenced as described in the model, using $ref syntax

\- resolved:: definitions are resolved to list the content of the reference.

\- internal: references to external and model definitions are converted into internal definitions

&nbsp;

## Upper and lower tabs

A set of tabs appears at the top of the central pane.&nbsp; They let you work on several entities in parallel, or consult relevant information in other collections.

![Central pane - top tabs](<lib/Central pane - top tabs.png>)

The first tab is fixed and cannot be closed.&nbsp; It is the main tab of the model, showing the Entity Relationship diagram for the database model, and other database model-level information.&nbsp; The other tabs are collection tabs.&nbsp; They are opened when you want to see or maintain collection-level information.&nbsp; They can be closed individually by pressing the x on the right of the tab.&nbsp; To close all tabs, use the shortcut Ctrl+M.&nbsp; If you want to close all tabs except the current one, press Ctrl+Shift+M.

Note that the application remembers the opened tabs of your model, if you save it and exit, so you handily retrieve your configuration when you open the model again.

&nbsp;

If you open more tabs than the width of the central pane can hold, the tabs will shrink as needed.&nbsp; If you hover your mouse cursor over a tab, a handy tooltip pops-up to display the full name:

![Central pane - tab tooltip](<lib/Central pane - tab tooltip.png>)

&nbsp;

&nbsp;

A set of tabs also appears at the bottom of the central pane.&nbsp; The bottom tabs are fixed but differ depending on whether you select the database model top tab, or a collection tab:

&nbsp;

Database model bottom tabs:

![Central pane - DB bottom tabs](<lib/Central pane - DB bottom tabs.png>)

&nbsp;

Collection bottom tabs:

![Central pane - collection bottom tabs](<lib/Central pane - collection bottom tabs.png>)

&nbsp;

Each bottom tab provides a different view of the entity information. &nbsp;

