# Central pane

&nbsp;

The central pane is where you can visualize your NoSQL database model and collection schema.&nbsp; The central pane adapts to the selected top and bottom tabs, for example:

&nbsp;

Entity Relationship diagram of a database model:

![Central pane - ER diagram](<lib/Central%20pane%20-%20ER%20diagram.png>)

&nbsp;

With large models, it is possible that to fit the entire ERD on screen, the zoom level does not allow to read the information.&nbsp; For performance reasons, Hackolade displays a sketchy rendition of the diagram:

![Central pane - sketchy ERD](<lib/Central%20pane%20-%20sketchy%20ERD.png>)

&nbsp;

You may control the the zoom level range of the sketchy rendition via a parameter in Tools \> Options \> General.

&nbsp;

Hierarchical schema view of an entity schema:

![Central pane - hierarchical schema view](<lib/Central%20pane%20-%20hierarchical%20schema%20view.png>)

&nbsp;

From the ERD, you may open the hierarchical schema view in a number of ways:

\- double click on the entity title\
\- click once on the middle-right icon in the entity title\
\- right-click on the entity title and choose Open in new tab\
\- right-click on the entity name in the Object Browser on the left, and choose Open in new tab

&nbsp;

![JSON Tree in new tab](<lib/JSON%20Tree%20in%20new%20tab.png>)

&nbsp;

&nbsp;

&nbsp;

JSON Preview of an entity:

![Central pane - JSON Preview](<lib/Central%20pane%20-%20JSON%20Preview.png>)

&nbsp;

Standard is limited to purely JSON Schema data types and keywords.

Full is limited to JSON Schema data types, but also includes all properties, including user-defined.

Extended generates an output that may include other data types than JSON Schema-compliant data types.

&nbsp;

Referenced definitions lists $ref references to internal, model, and external definitions

Resolved definitions replaces the references by an instance of the respective definitions

&nbsp;

A set of tabs appears at the top of the central pane.&nbsp; They let you work on several collections in parallel, or consult relevant information in other collections.

![Central pane - top tabs](<lib/Central%20pane%20-%20top%20tabs.png>)

The first tab is fixed and cannot be closed.&nbsp; It is the main tab of the model, showing the Entity Relationship diagram for the database model, and other database model-level information.&nbsp; The other tabs are collection tabs.&nbsp; They are opened when you want to see or maintain collection-level information.&nbsp; They can be closed individually by pressing the x on the right of the tab.&nbsp; To close all tabs, use the shortcut Ctrl+M.&nbsp; If you want to close all tabs except the current one, press Ctrl+Shift+M.

Note that the application remembers the opened tabs of your model, if you save it and exit, so you handily retrieve your configuration when you open the model again.

&nbsp;

If you open more tabs than the width of the central pane can hold, the tabs will shrink as needed.&nbsp; If you hover your mouse cursor over a tab, a handy tooltip pops-up to display the full name:

![Central pane - tab tooltip](<lib/Central%20pane%20-%20tab%20tooltip.png>)

&nbsp;

&nbsp;

A set of tabs also appears at the bottom of the central pane.&nbsp; The bottom tabs are fixed but differ depending on whether you select the database model top tab, or a collection tab:

&nbsp;

Database model bottom tabs:

![Central pane - DB bottom tabs](<lib/Central%20pane%20-%20DB%20bottom%20tabs.png>)

&nbsp;

Collection bottom tabs:

![Central pane - collection bottom tabs](<lib/Central%20pane%20-%20collection%20bottom%20tabs.png>)

&nbsp;

Each bottom tab provides a different view of the entity information. &nbsp;

