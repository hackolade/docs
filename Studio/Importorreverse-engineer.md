# Import or reverse-engineer

In the previous tutorial, we reviewed how to create other types of JSON Schema attributes: choices, conditionals, and pattern fields.&nbsp; By the end of this tutorial, importing data structures and reverse-engineering of existing instances will have no secrets for you.

&nbsp;

The reverse-engineering function is used to import information into pre-existing or empty data models.&nbsp; Reverse engineering is a useful feature to facilitate the modeling and documentation of existing instances.&nbsp; After the reverse engineering has been performed, the user can enrich the model created, by filling descriptions, recording constraints that were not obvious from the stored data, documenting relationships, etc…

&nbsp;

Hackolade supports the reverse engineer of different types of data sources:

* a JSON or YAML document: during this process, we infer the schema for the data in the file(s)
* a JSON Schema or YAML Schema: during this process, when applied to an RDBMS target, we optionally normalize nested structures into separate entities.
* a Data Definition Language file (DDL): from Oracle, Microsoft SQL Server, MySQL, PostgreSQL, Hadoop Hive, Snowflake, Teradata, DB2, Informix, Redshift, MariaDB
* an XSD schema file from another ER tool, such as erwin, ER/Studio, PowerDesigner, or other
* an Excel file template: first export a Hackolade model (even an empty one) to generate an Excel file for the target of your choice.&nbsp; Then you may bulk edit your model or create a new one before ingesting it back into the application.
* target-specific instances
* from a data dictionary (currently only Collibra.)

&nbsp;

The first 5 sources assume access to files on the (local or network) file system, whereas others require connection settings to access on-prem or cloud instances.

&nbsp;

To import from these sources, you simply go to Tools \> Reverse-Engineer and choose from the menu options.&nbsp; These options differ slightly from target to target. &nbsp;

&nbsp;

![Image](<lib/Tutorial%20-%20import%20reverse-engineer.png>)

&nbsp;

&nbsp;

## Importing file-based sources

For file-based imports, you are prompted with a dialog which varies slightly for each option:

&nbsp;

![Image](<lib/Tutorial%20-%20Reverse-engineer%20from%20JSON%20Schema.png>)

You must select one or more files to import.&nbsp; In most cases, you will want to import as entities in the Entity-Relationship Diagram.&nbsp; But also may want to import the schema as model definitions (user-defined types for RDBMS and some other targets, component schemas for OpenAPI) so they can be reused in many places in the model.

&nbsp;

When importing in the ERD, you may also merge the imported structure into an existing or new container (schema for RDBMS, namespace or keyspace for some targets, etc.)

&nbsp;

Finally, when importing nested structures into RDBMS targets (which don't support complex data types), you are presented with an option to automatically normalize into flat tables:

![Image](<lib/Titorial%20-%20normalize%20complex%20data%20types.png>)

&nbsp;

&nbsp;

## Reverse-engineering instances

When you reverse-engineer from on-prem or cloud instances, you generally must provide connection parameters and security credentials.&nbsp; This is done via a Connections dialog such as:

&nbsp;

![Tutorial - Connections dialog](<lib/Tutorial%20-%20Connections%20dialog.png>)

&nbsp;

This confidential information stays on your local system with encrypted passwords.&nbsp; With this screen you can connect to previously saved connections, as well as add, edit, copy, import, export, and delete connections. &nbsp;

&nbsp;

The connection settings differ for each target, depending on the respective protocols and authentication mechanisms of each target technology.

&nbsp;

When connecting to an instance, the reverse-engineering process differs as well.&nbsp; In the case of RDBMS, we can simply retrieve the DDL.&nbsp; However, things gets trickier when there is JSON in RDBMS or in document databases.&nbsp; In those cases, we launch a sampling process, then proceed with inference of the schema, prior to converting into a Hackolade data model.&nbsp; We apply a similar approach to schemaless NoSQL databases such as property graphs, key-value, and column-oriented databases.

&nbsp;

In this tutorial, we reviewed how to import data structures and reverse-engineer existing instances into a data model.&nbsp; In the next tutorial, we will cover how to export or forward-engineer artifacts from your data model.

