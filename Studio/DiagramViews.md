---
description: Create ER Diagram Views, also called subject areas or sub-models, to focus on subsets of entities in large Hackolade Studio models.
seoTitle: ER Diagram Views (subject areas) in Hackolade Studio
image: lib/ERDV editor.png
---
# Diagram Views

This feature of Hackolade Studio is often called "subject area" or "sub-model" in legacy data modeling tools.

With v4.3.2, Hackolade Studio has the possibility to add separate ER Diagram Views (ERDV): a subset of entities selected from the main ER diagram, to help manage large models by focusing on a smaller set of entities, by domain or subject.

Entities may appear in multiple Diagram Views. Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present. And vice-versa.

To find all the Diagram Views that contain a given entity, type the entity name in the search bar at the top of the Object Browser. The filtered tree shows the entity and every Diagram View where it appears. See [Object browser pane](Objectbrowserpane.md).

A new Diagram View can be added in different ways:\
1\) from the Actions menu option:\
![Menu Actions](<lib/Menu Actions.png>)

2\) from the toolbar:\
![Toolbar Create Diagram View](<lib/Toolbar Create Diagram View.png>): toolbar button

3\) from the Object Browser or the main Entity Relationship Diagram:\
by selecting one or more entities, then doing a right-click on an entity to display the contextual menu:\
![Contextual menu add ERDV](<lib/Contextual menu add ERDV.png>)

Editing an ER Diagram View name or membership is done from the contextual menu of the Object Browser:\
![Contextual menu edit ERDV](<lib/Contextual menu edit ERDV.png>)

In this dialog, you may edit the name of the Diagram View and modify the selection of the entities selected:\
![ERDV editor](<lib/ERDV editor.png>)

Display options are specific to each diagram view, and independent of the display options of the main ER Diagram. This allows you to define different Diagram Views with possibly the same containers and entities, while using different display options. This can be useful for data model storytelling.
