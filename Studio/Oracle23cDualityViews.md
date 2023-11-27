# Oracle 23c Duality Views

Duality Views expose data stored in relational tables as JSON documents. The documents are materialized -- generated on demand, not stored as such. Duality views are organized both relationally and hierarchically. They combine the advantages of using JSON documents with the advantages of the relational model, while avoiding the limitations of each.&nbsp;

&nbsp;

Hackolade Studio is the first and only tool to facilitate the adoptions of this revolutionary feature released with Oracle 23c.

&nbsp;

## Overview

In this excellent [introductory video](<https://www.youtube.com/watch?v=e8-jBkO1NqY> "target=\"\_blank\""), Oracle explains that there are 2 ways to bake cake.&nbsp; You may start from individual ingredients and follow a recipe:

&nbsp;

![Oracle Duality Views - Baking cake ingredients](<lib/ORD%20-%20Baking%20cake%20ingredients.png>)

&nbsp;

&nbsp;

Or you may start with a cake mix:

&nbsp;

![Oracle Duality Views - Baking cake mix](<lib/ORD%20-%20Baking%20cake%20mix.png>)

&nbsp;

The analogy is that a relational database is like assembling different basic ingredients using joins, like you would when following a recipe. In contrast, the JSON document model is like using cake mix: easy to use but you cannot deviate from the mix, or use the ingredients in your fridge to combine with another recipe.

&nbsp;

![Oracle Duality Views - relational cake ingredients](<lib/ORD%20-%20relational%20cake%20ingredients.png>)

&nbsp;

With Oracle 23c, Oracle introduces a way to combine both approaches, hence combining the benefits of normalized tables (traditional Oracle) and the document model (like MongoDB.)

&nbsp;

![Image](<lib/ORD%20-%20Power%20and%20Simplicty.png>)

&nbsp;

&nbsp;

The idea is to create a convergence of the traditional relational/normalized approach with the more recent JSON document approach, to achieve with the combination more than the sum of the parts

&nbsp;

![Oracle Duality Views - Best of both worlds](<lib/ORD%20-%20Best%20of%20both%20worlds.png>)

&nbsp;

Oracle call this approach "JSON-Relational Duality Views"

&nbsp;

![Oracle JSON-Relational Duality Views](<lib/ORD%20-%20JSON-Relational%20Duality%20Views.png>)

&nbsp;

JSON-relational duality views combine the advantages of using JSON documents with the advantages of the relational model, while avoiding the limitations of each:

* A single JSON document can represent an application object directly, capturing the hierarchical relations among its components. A JSON document is standalone: self-contained and self-describing — no outside references, no need to consult an outside schema. There's no decomposition, which means that JSON is schema-flexible: you can easily add and remove fields, and change their type, as required by application changes.
* The relational model decomposes application objects ("business objects") into normalized tables, which are explicitly related but whose content is otherwise independent. This independence allows for flexible and efficient data combination (joining) that is rigorously correct and reliable.

&nbsp;

A duality view exposes data stored in relational tables as JSON documents. The documents are materialized — generated on demand, not stored as such. Duality views give your data both a conceptual and an operational duality: it's organized both relationally and hierarchically. You can base different duality views on data stored in one or more of the same tables, providing different JSON hierarchies over the same, shared data.

&nbsp;

This means that applications can access (create, query, modify) the same data as a set of JSON documents or as a set of related tables and columns, and both approaches can be employed at the same time

&nbsp;

Also, duality views could be said to be a kind of ORM (Object-Relational Mapping): they too map hierarchical object data to/from relational data. But they're fundamentally different from alternative approaches. Duality views centralize the persistence format of application objects for both server-side and client-side applications — all clients, regardless of language or framework.

&nbsp;

The persistence model presents two aspects for the same data: table and document. Server-side code can manipulate relational data in tables; client-side code can manipulate a set of documents. Client code need only convert its programming objects to/from JSON, which is familiar and easy. A duality view automatically persists JSON as relational data. There's no need for any separate mapper — the duality view is the mapping.

&nbsp;

![Oracle JSON Document Relational duality](<lib/ORD%20-%20JSON%20Document%20Relational%20duality.png>)

&nbsp;

&nbsp;

## Oracle Duality Views in Hackolade Studio

The Oracle plugin has been adapted, based on this [comprehensive developer's guide](<https://docs.oracle.com/en/database/oracle/oracle-database/23/jsnvu/overview-json-relational-duality-views.html#GUID-CE7227BF-B4AF-4024-A578-ED52795F4525> "target=\"\_blank\""), to natively support the data modeling of duality views, as well as the forward- and reverse-engineering of the DDL scripts.

&nbsp;

While the duality views feature sounds complex, and probably is quite complex under the hood of the database engine to work efficiently, the implementation in Hackolade Studio is rather straight forward.

&nbsp;

Previously in our Oracle plugin, we supported the creation of traditional views (materialized or not.)&nbsp; Views have a set of properties and selected columns. Together they can be forward-engineered in a CREATE VIEW statement of the the DDL script. And they can be reverse-engineered with the SELECT statement parsed to generate the view structure in the model and display the ERD.

&nbsp;

A duality view is just a special kind of view, also with properties and columns. The only differences are:

* nested objects of a special kind can be contained in the view
* the syntax of the DDL script introduces some new vocabulary and structure, which impacts forward- and reverse-engineering.

&nbsp;

The examples below are based on this [repository](<https://github.com/oracle-samples/oracle-db-examples/blob/main/json-relational-duality/DualityViewTutorial.sql> "target=\"\_blank\"") provided by Oracle.

&nbsp;

The reverse-engineering of the relational tables in [this sample DDL](<https://github.com/oracle-samples/oracle-db-examples/blob/main/json-relational-duality/DualityViewTutorial.sql> "target=\"\_blank\"") generates this car racing model:

![Oracle Duality Views- relational tables ERD](<lib/ORD%20-%20relational%20tables%20ERD.png>)

&nbsp;

The duality views defined with point-and-click in Hackolade Studio lead to this part of the ERD:

![Oracle Duality Views ERD](<lib/ORD%20-%20Duality%20Views%20ERD.png>)

&nbsp;

and the application automatically produces the syntactically correct part of the DDL script, with no required knowledge of the necessary syntax:

&nbsp;

![Oracle Duality Views - DDL](<lib/ORD%20-%20DDL.png>)

&nbsp;

The syntax is based on this Oracle [documentation page](<https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/create-json-relational-duality-view.html#GUID-64B579AD-BF97-4B27-BF22-94C1FB6FD6DF> "target=\"\_blank\"") and its (always excellent) diagrams.

&nbsp;

![Oracle Duality Views - Syntax](<lib/ORD%20-%20Syntax.png>)

&nbsp;

&nbsp;

**Important note**: Hackolade Studio currently only supports the SQL syntax for duality views, i.e. not yet the GraphQL syntax to achieve the same result.

&nbsp;

## Create a duality view

As usual with Hackolade Studio, there are several different ways to do things.&nbsp; To create a duality view, you first create a "generic" view, using a keyboard shortcut, the menu bar:

&nbsp;

![Oracle duality view creation menu](<lib/ORD%20-%20duality%20view%20creation%20menu.png>)

&nbsp;

or the contextual menu (via mouse right-click) in either the Object Browser or the Entity Relationship Diagram pane:

&nbsp;

&nbsp;

![Oracle duality view creation contextual menu](<lib/ORD%20-%20duality%20view%20creation%20contextual%20menu.png>)

&nbsp;

&nbsp;

Then you tick the checkbox "Duality" to display the related properties:

&nbsp;

![Oracle duality view properties](<lib/ORD%20-%20duality%20view%20properties.png>)

&nbsp;

&nbsp;

You must choose the root table from the dropdown list of tables in the schema.&nbsp; You may optionally set a root table alias.

&nbsp;

You may also set the Force and Editionable flags.

&nbsp;

You should of course give your duality view a name.&nbsp; If Naming Conventions are enabled, you provide a business name which gets transformed into a technical name according to the set rules.

&nbsp;

### Table tags clause

A duality view does not, itself, store any data.&nbsp; All of the data that underlies its supported JSON documents (which are generated) is stored in tables underlying the view. For a duality view to be updatable means that you can update some or all of the data in its underlying tables, and so you can update some or all of the fields in its supported documents.

&nbsp;

Applications can update JSON documents supported by a duality view, if you define the view as updatable. You can specify which kinds of updating operations (update, insertion, and deletion) are allowed, for which document fields, how/when, and by whom.&nbsp; An application can update a complete document, replacing the existing document. Or it can update only particular fields, in place.&nbsp; There are many possible permutations and rules to fit your use case, with all the details explained in [this document](<https://docs.oracle.com/en/database/oracle/oracle-database/23/jsnvu/updatable-json-relational-duality-views.html#GUID-1D013418-2095-4659-A503-75BD99C3A2CB> "target=\"\_blank\"").

&nbsp;

The update annotations are set using table tags clause constructed by optionally setting (no)check, (no)insert, (no)update, and (no)delete properties.

&nbsp;

## Select columns from root table

The JSON format of duality views allows to include both root-level fields as well as embedded complex objects that are the result of joins with other tables.&nbsp; Let's start with the root table columns.

&nbsp;

From the Object Browser, from the selected view in the ERD pane, or from the hierarchical schema tab, you must right-click to bring the contextual menu and choose the option "Pick from field list":

![Oracle duality view pick columns](<lib/ORD%20-%20duality%20view%20pick%20columns.png>)

&nbsp;

&nbsp;

This brings a dialog where you can select one or more columns from the selected root table:

&nbsp;

![Oracle duality view pick columns dialog](<lib/ORD%20-%20duality%20view%20pick%20columns%20dialog.png>)

&nbsp;

&nbsp;

For each field, you may set a JSON key alias if it is different than the underlying column name:

![Oracle duality view field properties](<lib/ORD%20-%20duality%20view%20field%20properties.png>)

&nbsp;

And you may also set annotations for (no)check and (no)update for tags clause at the field level.

&nbsp;

For documentation purposes, you may check the Key property for the field playing the role of primary key.&nbsp; However, this information does not appear in DDL script.

&nbsp;

You may modify the order of fields using the up/down arrows in the toolbar or drag-and-drop in the ERD like you would do for attributes in tables.

&nbsp;

&nbsp;

## Add nested object or array subquery

This is the heart of the benefits of duality views.&nbsp; A duality view is a JSON generation view that has a limited structure, expressly designed so that your applications can update the view, and in so doing automatically update the underlying tables.

&nbsp;

A duality view and its corresponding top-level JSON object provides a hierarchy of JSON objects and arrays, which are defined in the view definition using nested SQL subqueries. Data gathered from a subquery is joined to data gathered from a parent subquery or the root table by a relationship between a primary or unique key in the parent and a foreign key in the child subquery's WHERE clause.

&nbsp;

The cardinality of relationships dictates whether you use an object or an array type of subquery.

&nbsp;

You may create multi-level nesting to represent recursive joins. &nbsp;

&nbsp;

To add a subquery, invoke the contextual menu to append a column and choose Subquery:

&nbsp;

![Oracle duality view contextual menu adding subquery](<lib/ORD%20-%20duality%20view%20add%20subquery.png>)

&nbsp;

You should provide a name for the subquery and choose the type object or array depending on the cardinality of your join: object for 1-to-1 relationships, and array for 1-to-many relationships:

&nbsp;

![Oracle duality view subquery properties](<lib/ORD%20-%20duality%20view%20subquery%20properties.png>)

&nbsp;

&nbsp;

You must choose the child table from the dropdown list of tables in the schema.&nbsp; You may optionally set a child table alias.

&nbsp;

The update annotations use the table tags clause constructed by optionally setting (no)check, (no)insert, (no)update, and (no)delete properties.

&nbsp;

You must enter the WHERE clause for the join.

&nbsp;

## Add unnested fields

In some cases, you might prefer to flatten structures instead of the nested subquery.&nbsp; The unnested subquery allows to select columns in the underlying child table and present the fields in the JSON at the same level as the columns of the prent table.&nbsp; This can be done at any level of the tree.

&nbsp;

![Oracle duality view unnested subquery properties](<lib/ORD%20-%20duality%20view%20unnest%20subquery%20properties.png>)

&nbsp;

While the fields are unnested in the JSON document, the unnesting structure remains visible in the ERD and Object Browser.

&nbsp;

![Oracle duality view ERD Entity-Relationship Diagram](<lib/ORD%20-%20duality%20view%20ERD.png>)

&nbsp;

or in the hierarchical schema tab

![Oracle duality view hierarchical schema tab](<lib/ORD%20-%20duality%20view%20hierarchical%20schema%20tab.png>)

&nbsp;

&nbsp;

## Forward-engineer DDL script

The application automatically produces the syntactically correct DDL script, with no required knowledge of the necessary syntax:

&nbsp;

&nbsp;

![Oracle duality view DDL script](<lib/ORD%20-%20duality%20view%20DDL%20script.png>)

&nbsp;

which can be exported to a file, copied/pasted, or applied directly to a database instance.

&nbsp;

## Reverse-engineer an existing instance or a DDL file

Hackolade Studio can reverse-engineer DDL files including duality views defines in SQL syntax.&nbsp; This is particularly useful if it is not possible to connect the application to the Oracle database instance. &nbsp;

&nbsp;

The drawback of DDL file-based reverse-engineering however is that, in the event of columns defined with a JSON data type or LOB containing JSON documents, the application will not have a chance to sample JSON in order to infer the schema.&nbsp; Such information never appears in DDLs and only Hackolade Studio is able to infer the schema of JSON in RDBMS.

&nbsp;

The most effective method to get a full picture of the data structure is to connect Hackolade Studio to the database instance and launch the reverse-engineering process, which produces an ERD representation of the instance.

&nbsp;

