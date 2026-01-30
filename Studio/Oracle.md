# Oracle

Oracle is a multi-model database management system commonly used for running online transaction processing (OLTP), data warehousing (DW) and mixed (OLTP \& DW) database workloads.&nbsp; It may be run by several service providers on-prem, on-cloud, or as hybrid cloud installation, as well as on Oracle hardware. &nbsp;

&nbsp;

To perform data modeling for Oracle with Hackolade, you must first download the Oracle [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of Oracle, including schemas, tables and views, indexes and constraints, plus the generation of DDL Create Table syntax. Hackolade also supports the Oracle Autonomous cloud database that uses machine learning to automate database tuning, security, backups, updates, and other routine management tasks traditionally performed by DBAs.&nbsp; This includes the JSON-centric autonomous database.

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the [JSON data types](<https://docs.oracle.com/en/database/oracle/oracle-database/23/adjsn/json-schema.html> "target=\"\_blank\"") (actually Oracle optimized native binary JSON storage format \[OSON\] in v21c and above) and of JSON documents in BLOB data types (v12c, v18c, and v19c).&nbsp; We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types.&nbsp; But about the storage of entire JSON documents.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions. &nbsp;

&nbsp;

With 21c, Oracle Database now supports JSON data natively with relational database features, including transactions, indexing, declarative querying, and views.&nbsp; Prior to 21c, JSON data is stored in Oracle Database using SQL data types VARCHAR2, CLOB, and BLOB. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of the [Oracle customer order sample schemas](<https://docs.oracle.com/en/database/oracle/oracle-database/21/comsc/introduction-to-sample-schemas.html#GUID-BF7EBD46-7AF6-40C7-8B4E-7244169A07E8> "target=\"\_blank\""):

&nbsp;

![Image](<lib/Oracle workspace.png>)

## Schemas

A schema is a collection of logical structures of data, or schema objects. A schema is owned by a database user and has the same name as that user. Each user owns a single schema.&nbsp; Examples of schema objects are tables and indexes.

&nbsp;

A single Hackolade model deals with a single database but can handle multiple schemas.

&nbsp;

## Tables

A table is the basic unit of data organization in an Oracle database.&nbsp; A table describes an entity, which is something of significance about which information must be recorded. For example, an employee could be an entity.

&nbsp;

A table definition includes a table name and set of columns. A [column](<https://docs.oracle.com/en/database/oracle/oracle-database/21/cncpt/glossary.html#GUID-F1D9AA5F-C66A-4D5F-A84C-8D7360DE3BE5>) identifies an attribute of the entity described by the table. In general, each column has a column name, a [data type](<https://docs.oracle.com/en/database/oracle/oracle-database/21/cncpt/glossary.html#GUID-3873B26C-657D-4508-B13D-9155F1D5D8F4>), and a width when you create a table.  A row is a collection of column information corresponding to a record in a table.

&nbsp;

## Unique, Primary, and Foreign Keys, plus Not Null, Check and Default constraints

Constraints are used to define rules that restricts the values in a database. Oracle Database lets you create constraints and lets you declare them in two ways.

&nbsp;

The types of integrity constraint are described briefly below:

* A **NOT** **NULL** **constraint** prohibits a database value from being null.
* A **unique constraint** prohibits multiple rows from having the same value in the same column or combination of columns but allows some values to be null.
* A **primary key constraint** combines a NOT NULL constraint and a unique constraint in a single declaration. That is, it prohibits multiple rows from having the same value in the same column or combination of columns and prohibits values from being null.
* A **foreign key constraint** requires values in one table to match values in another table.
* A **check constraint** requires a value in the database to comply with a specified condition.

&nbsp;

You can define constraints syntactically in two ways:

* As part of the definition of an individual column or attribute. This is called **inline** specification.
* As part of the table definition. This is called **out-of-line** specification.

&nbsp;

## Partitioning

Partitioning enhances the performance, manageability, and availability of applications and helps reduce the total cost of ownership for storing large amounts of data.

&nbsp;

Partitioning allows tables, indexes, and index-organized tables to be subdivided into smaller pieces, enabling these database objects to be managed and accessed at a finer level of granularity. Oracle provides a rich variety of partitioning strategies and extensions to address every business requirement. Because it is entirely transparent, partitioning can be applied to almost any application without the need for potentially expensive and time consuming application changes.

&nbsp;

## Indexes

An index is an optional structure, associated with a table or [table cluster](<https://docs.oracle.com/cd/E11882\_01/server.112/e40540/glossary.htm#CHDJGGGF>), that can sometimes speed data access. By creating an [index](<https://docs.oracle.com/cd/E11882\_01/server.112/e40540/glossary.htm#i432409>) on one or more columns of a table, you gain the ability in some cases to retrieve a small set of randomly distributed rows from the table. Indexes are one of many means of reducing disk I/O.

&nbsp;

Hackolade supports the most common types of Oracle indexes. &nbsp;

## Data types

Each value manipulated by Oracle Database has a [data type](<https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Data-Types.html#GUID-A3C0D836-BADB-44E5-A5D4-265BA5968483> "target=\"\_blank\""). The data type of a value associates a fixed set of properties with the value. These properties cause Oracle to treat values of one data type differently from values of another. For example, you can add values of NUMBER data type, but not values of RAW data type.

&nbsp;

When you create a table or cluster, you must specify a data type for each of its columns. When you create a procedure or stored function, you must specify a data type for each of its arguments. These data types define the domain of values that each column can contain or each argument can have. 

&nbsp;

Oracle Database provides a number of built-in data types as well as several categories for user-defined types that can be used as data types. A data type is either scalar or non-scalar. A scalar type contains an atomic value, whereas a non-scalar contains a set of values. A large object (LOB) is a special form of scalar data type representing a large scalar value of binary or character data. LOBs are subject to some restrictions that do not affect other scalar types because of their size. 

&nbsp;

With 21c, Oracle Database now supports JSON data natively with relational database features, including transactions, indexing, declarative querying, and views.&nbsp; Prior to 21c, JSON data is stored in Oracle Database using SQL data types VARCHAR2, CLOB, and BLOB.&nbsp; Hackolade supports the data modeling of JSON documents with standard JSON data types: string, number, object, array, boolean, and null.

&nbsp;

With version 26ai, Oracle added a new [*data type vector*](<https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/Data-Types.html#GUID-801FFE49-217D-4012-9C55-66DAE1BA806F> "target=\"\_blank\"") with the possible declaration formats below, all supported in Hackolade Studio:

![Oracle vector declaration](<lib/Oracle vector declaration.png>)

&nbsp;

### JSON prior to 21c

Oracle recommends that you always use an is\_json check constraint to ensure that column values are valid JSON instances.&nbsp; JSON data in the database is textual, but the text can be stored using data type BLOB, as well as VARCHAR2 or CLOB.&nbsp; When possible, prior to 21c, Oracle recommends that you use BLOB storage.&nbsp; In particular, doing so obviates the need for any character-set conversion plus it allows to store binaries.

So you don’t waste time searching for resolutions to the issues I encountered…

* If you create a column with a field type CLOB, you need to set the table constraint: (“\<column\_name\>” IS JSON)
* If you create a column with a&nbsp; field type BLOB, you need to set the table constraint: (“\<column\_name\>” IS JSON FORMAT JSON)

Then, the JSON data type was introduced in the Oracle 20c preview release to provide native JSON support and improve the performance of JSON processing. It has become generally available in Oracle 21c.&nbsp; The JSON data type is an Oracle optimized binary JSON format called OSON. It is designed for faster query and DML performance in the database and in database clients from version 20c/21c upward.

&nbsp;

## Views

A view is a logical representation of another table or combination of tables. A view derives its data from the tables on which it is based. These tables are called base tables. Base tables might in turn be actual tables or might be views themselves. All operations performed on a view actually affect the base table of the view. You can use views in almost the same way as tables. You can query, update, insert into, and delete from views, just as you can standard tables.

Views can provide a different representation (such as subsets or supersets) of the data that resides within other tables and views. Views are very powerful because they allow you to tailor the presentation of data to different types of users.

&nbsp;

## JSON-Relational Duality Views in 26ai

Duality Views expose data stored in relational tables as JSON documents. The documents are materialized — generated on demand, not stored as such. Duality views are organized both relationally and hierarchically. They combine the advantages of using JSON documents with the advantages of the relational model, while avoiding the limitations of each.&nbsp;

&nbsp;

Hackolade Studio is the first and only tool to facilitate the adoptions of this revolutionary feature released with Oracle 26ai.&nbsp; Many more details are available in [this page](<Oracle23aiand26aiDualityViews.md>).

&nbsp;

&nbsp;

## Triggers, Functions and Procedures

TBA

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Oracle DDL forward-engineering](<lib/Oracle DDL forward-engineering.png>)

&nbsp;

If you store documents in JSON columns (21c and above) or for 12c thru 19c in BLOB columns, as well as VARCHAR2 or CLOB, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

## Reverse-Engineering

The Oracle instance can hosted on-premises, or on virtualized machines in a private or public cloud.&nbsp; Details on how to connect Hackolade Studio to Oracle can be found on [this page](<ConnecttoanOracleinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of Oracle databases includes the execution of statements to discover databases, tables, columns and their types, indexes and constraints.&nbsp; For JSON columns (21c and above) or for 12c thru 19c in BLOB columns, as well as VARCHAR2 or CLOB, Hackolade Studio performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

**Important:** when reverse-engineering an Oracle instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be granted SELECT\_CATALOG\_ROLE. More information is available [here](<https://docs.oracle.com/cd/B19306\_01/appdev.102/b14258/d\_metada.htm#i1016867> "target=\"\_blank\"").

&nbsp;

For more information on Oracle in general, please consult the [website](<https://www.oracle.com/database/technologies/> "target=\"\_blank\"") and [documentation](<https://docs.oracle.com/en/database/oracle/oracle-database/> "target=\"\_blank\""). &nbsp;

&nbsp;

