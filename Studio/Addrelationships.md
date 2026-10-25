# Add relationships

In the previous tutorial, we reviewed how to create other types of JSON Schema attributes: choices, conditionals, and pattern fields. By the end of this tutorial, you will master how to add relationships to your entity-relationship diagram.

&nbsp;

You may also [view this tutorial](<https://youtu.be/69zREhcCYuc> "target=\"_blank\"") on YouTube. Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-7-add-relationshipspdf> "target=\"_blank\"").

&nbsp;

> [!NOTE]
> This tutorial does not cover edges of graph targets, a subject which is covered in a later tutorial.

&nbsp;

You expect an Entity-Relationship Diagram to contain relationship lines between entities. Hackolade Studio of course supports foreign key relationships when it comes to relational databases. But we also handle relationships for non-relational databases, as well as between seemingly independent Avro or JSON documents, etc. Is this non-sense? Please read on...

&nbsp;

## Non-relational databases

The fact that NoSQL databases don't enforce foreign-key relationships does not change the fact that there are inevitably relationships in data. Plus, it is easier to understand the structure of data in ERDs when there are relationship lines to document associations. Besides, as NoSQL databases encourage denormalization, data gets duplicated in potentially multiple places. Yet, there needs to be a place where a master version is maintained so, in case it changes, all duplicates can be updated if appropriate. It is easy in Hackolade Studio to maintain these relationships for documentation purposes.

&nbsp;

You will notice a relationship type with 2 possible values "Foreign key" and "Foreign master". The first one is typical. The second one is a Hackolade invention so you can trace and document denormalization in NoSQL databases. This foreign master relationship is never forward-engineered, and is only there for documentation purposes. Its display in the ERD can be toggled on or off with a toolbar button or in Tools > Options > Display.

&nbsp;

## Relational databases and associated

As Hackolade Studio also supports relational databases, you can maintain foreign key relationships to generate constraints in DDLs, including compound keys. In the case of SQL-like data warehouse technology, the relationships can be declared for documentation purposes, but do not appear in DDLs as they are not enforced by the database engine.

&nbsp;

## Create a relationship

Relationships appear in the application at the data model level, i.e. they are not stored at the container (schema/keyspace) level. This is because it is possible in some target technologies to have foreign key relationships across schemas.

&nbsp;

As expected, there are many different ways to create relationships in Hackolade Studio:

- in the ERD by selecting a child attribute and doing a drag-and-drop on top of an attribute of a compatible data type, in the same entity (if recursive) or an another entity:
- with the menu Actions > Add relationship, or the toolbar icon, or a right-click then Add relationship in the contextual menu of the ERD or Object Browser, or by pressing the + sign in the relationships properties pane tab at the model level. All these methods let you enter in the properties pane the name, description, parent and child entities and attributes, etc.

&nbsp;

![Tutorial relationship properties](<lib/Tutorial relationship properties.png>)

- in the properties pane of an attribute, where you can choose the foreign entity and attribute, as well as setting the relationship name and cardinality:

&nbsp;

![Tutorial relationship child properties](<lib/Tutorial relationship child properties.png>)

&nbsp;

With the Style group, you may adjust the thickness and color of each relationship line individually.

&nbsp;

In the case of compound keys in RDBMS, you declare multiple attributes on each side of the relationship, provided that data types are compatible:\
![Tutorial relationship compound child props](<lib/Tutorial relationship compound child props.png>)

&nbsp;

In this tutorial, we reviewed the creation of (foreign key) relationships. In the next tutorial, we will cover how to import or reverse-engineer structures in your data model.
