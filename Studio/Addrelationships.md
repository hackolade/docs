# Add relationships

In the previous tutorial, we reviewed how to create other types of JSON Schema attributes: choices, conditionals, and pattern fields.&nbsp; By the end of this tutorial, you will master how to add relationships to your entity-relationship diagram.

&nbsp;

**Note:** this tutorial does not cover edges of graph targets, a subject which is covered in a later tutorial.

&nbsp;

You expect an Entity-Relationship Diagram to contain relationship lines between entities.&nbsp; Hackolade Studio of course supports foreign key relationships when it comes to relational databases.&nbsp; But we also handle relationships for non-relational databases, as well as between seemingly independent Avro or JSON documents, etc.&nbsp; Is this non-sense?&nbsp; Please read on...

&nbsp;

## Non-relational databases

The fact that NoSQL databases don't enforce foreign-key relationships does not change the fact that there are inevitably relationships in data.&nbsp; Plus, it is easier to understand the structure of data in ERDs when there are relationship lines to document associations.&nbsp; Besides, as NoSQL databases encourage denormalization, data gets duplicated in potentially multiple places.&nbsp; Yet, there needs to be a place where a master version is maintained so, in case it changes, all duplicates can be updated if appropriate.&nbsp; It is easy in Hackolade Studio to maintain these relationships for documentation purposes.

&nbsp;

You will notice a relationship type with 2 possible values "Foreign key" and "Foreign master".&nbsp; The first one is typical.&nbsp; The second one is a Hackolade invention so you can trace and document denormalization in NoSQL databases.&nbsp; This foreign master relationship is never forward-engineered, and is only there for documentation purposes.&nbsp; Its display in the ERD can be toggled on or off with a toolbar button or in Tools \> Options \> Display.

&nbsp;

## Relational databases and associated

As Hackolade Studio also supports relational databases, you can maintain foreign key relationships to generate constraints in DDLs, including compound keys.&nbsp; In the case of SQL-like data warehouse technology, the relationships can be declared for documentation purposes, but do not appear in DDLs as they are not enforced by the database engine.

&nbsp;

## Create a relationship

Relationships appear in the application at the data model level, i.e. they are not stored at the container (schema/keyspace) level.&nbsp; This is because it is possible in some target technologies to have foreign key relationships across schemas.&nbsp;

&nbsp;

As expected, there are many different ways to create relationships in Hackolade Studio:

\- in the ERD by selecting a child attribute and doing a drag-and-drop on top of an attribute of a compatible data type, in the same entity (if recursive) or an another entity:

\- with the menu Actions \> Add relationship, or the toolbar icon, or a right-click then Add relationship in the contextual menu of the ERD or Object Browser, or by pressing the + sign in the relationships properties pane tab at the model level.&nbsp; All these methods let you enter in the properties pane the name, description, parent and child entities and attributes, etc.

![Tutorial relationship properties](<lib/Tutorial%20relationship%20properties.png>)

\- in the properties pane of an attribute, where you can choose the foreign entity and attribute, as well as setting the relationship name and cardinality:

![Tutorial relationship child properties](<lib/Tutorial%20relationship%20child%20properties.png>)

&nbsp;

With the Style group, you may adjust the thickness and color of each relationship line individually.

&nbsp;

In the case of compound keys in RDBMS, you declare multiple attributes on each side of the relationship, provided that data types are compatible:

![Tutorial relationship compound child props](<lib/Tutorial%20relationship%20compound%20child%20props.png>)

&nbsp;

In this tutorial, we reviewed the creation of (foreign key) relationships.&nbsp; In the next tutorial, we will cover how to import or reverse-engineer structures in your data model.

