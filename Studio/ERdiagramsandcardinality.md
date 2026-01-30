# ER diagrams and cardinality

According to [Wikipedia](<https://en.wikipedia.org/wiki/Entity–relationship\_model> "target=\"\_blank\""): "In software engineering, an Entity Relationship model is commonly formed to represent things that a business needs to remember in order to perform business processes. Consequently, the ER model becomes an abstract data model that defines a data or information structure that can be implemented in a database, typically a relational database...

&nbsp;

An entity relationship model is usually the result of systematic analysis to define and describe what is important to processes in an area of a business. It does not define the business processes; it only presents a business data schema in graphical form. It is usually drawn in a graphical form as boxes (entities) that are connected by lines (relationships) which express the associations and dependencies between entities...

&nbsp;

Entities may be characterized not only by relationships, but also by additional properties (attributes), which include identifiers called "primary keys"...

&nbsp;

There is a tradition for ER/data models to be built at two or three levels of abstraction: conceptual, logical, and physical data model."

&nbsp;

Hackolade loosely applies ER principles to the **physical data modeling** of JSON data stores, which are non-relational in nature.&nbsp; As seen in [Relationships and denormalization](<Relationshipsanddenormalization.md>), relationships are implicit, but there remains a need to document their existence, and to display them visually.

&nbsp;

With v4.3.2, Hackolade has introduced the possibility to add separate ER Diagram Views: a subset of entities selected from the main ER diagram, to help manage large models by focusing on a smaller set of entities, by domain or subject.&nbsp; Entities may appear in multiple Diagram Views.&nbsp; Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present.&nbsp;

&nbsp;

Hackolade adopts an IE-like notation (Information Engineering with [crow's foot](<https://en.wikipedia.org/wiki/Entity–relationship\_model#Crow's\_foot\_notation> "target=\"\_blank\"") notation) applied to physical models in order to display multiplicities on each side of the relationship to represent the cardinality:&nbsp;

&nbsp;

| **Symbol** | **Description** |
| --- | --- |
| ![Relationship cardinality - one](<lib/Relationship cardinality - one.png>) | only one |
| &nbsp;![Relationship cardinality - many](<lib/Relationship cardinality - many.png>) | many |
| ![Relationship cardinality - zero-to-one](<lib/Relationship cardinality - zero-to-one.png>) | zero or one |
| ![Relationship cardinality - zero-to-many](<lib/Relationship cardinality - zero-to-many.png>) | zero or more |
| ![Relationship cardinality - one-to-many](<lib/Relationship cardinality - one-to-many.png>) | one or more |


&nbsp;

You may have noticed that one side of the relationship has crow's foot cardinality displayed in blue on the parent side, and red on the child side.

| **Symbol** | **Description** |
| --- | --- |
| ![Relationship child cardinality - one](<lib/Relationship child cardinality - one.png>) | only one |
| &nbsp;![Relationship cardinality - many](<lib/Relationship child cardinality - many.png>) | many |
| ![Relationship child cardinality - zero-to-one](<lib/Relationship child cardinality - zero-to-one.png>) | zero or one |
| ![Relationship child cardinality - zero-to-many](<lib/Relationship child cardinality - zero-to-many.png>) | zero or more |
| ![Relationship child cardinality - one-to-many](<lib/Relationship child cardinality - one-to-many.png>) | one or more |


&nbsp;

&nbsp;

[This page](<EntityboxesinERdiagram.md>) helps understand how to manipulate entities in ER diagrams.

