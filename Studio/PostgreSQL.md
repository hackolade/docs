# PostgreSQL

PostgreSQL, also known as Postgres, is a free and open-source relational database management system (RDBMS) emphasizing extensibility and SQL compliance.&nbsp; It has earned a strong reputation for reliability, feature robustness, and performance.

&nbsp;

EnterpriseDB (EDB), a privately held company based in Massachusetts, provides software and services based on the open-source database PostgreSQL. EDB develops and integrates performance, security, and manageability enhancements into PostgreSQL to support enterprise-class workloads for its database. &nbsp;

&nbsp;

Postgres supports two JSON data types: JSON and JSONB. They accept *almost* identical sets of values as input. The major practical difference is one of efficiency. The JSON data type stores an exact copy of the input text, which processing functions must reparse on each execution; while JSONB data is stored in a decomposed binary format that makes it slightly slower to input due to added conversion overhead, but significantly faster to process, since no reparsing is needed. JSONB also supports indexing, which can be a significant advantage.

&nbsp;

To perform data modeling for PostgreSQL with Hackolade, you must first download the PostgreSQL [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of PostgreSQL, including schemas, tables and views, indexes and constraints, plus the generation of DDL Create Table syntax.&nbsp;

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the JSON and JSONB data types.&nbsp; We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types.&nbsp; But about the storage of entire JSON documents.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of the [flights booking demo](<https://postgrespro.com/education/demodb> "target=\"\_blank\""):

&nbsp;

![Image](<lib/PostgreSQL%20workspace.png>)

&nbsp;

## Tablespaces, databases, and schemas

A tablespace is a location on the disk where PostgreSQL stores data files containing database objects e.g., indexes, and tables.&nbsp; Tablespaces allow control of how data is stored in the file system. Tablespaces are useful in many cases such as managing large tables and improving database performance.&nbsp; PostgreSQL uses a tablespace to map a logical name to a physical location on disk.

&nbsp;

A database can contain one or multiple schemas and each schema belongs to only one database. Two schemas can have different objects that share the same name. &nbsp;

&nbsp;

A schema is a namespace that contains named database objects such as tables, views, indexes, data types, functions, stored procedures and operators.&nbsp; Schemas allow you to organize database objects e.g., tables into logical groups to make them more manageable.&nbsp; PostgreSQL automatically creates a schema called public for every new database. Whatever object is created without specifying the schema name, PostgreSQL will place it into this public schema.&nbsp; In practice, it is better to refer to a table using a fully qualified name.

&nbsp;

A single Hackolade model deals with a single database but can handle multiple schemas.

&nbsp;

## Tables

A table consists of rows and columns. The number and order of the columns is fixed, and each column has a name.&nbsp; Each column has a data type. The data type constrains the set of possible values that can be assigned to a column and assigns semantics to the data stored in the column so that it can be used for computations.

&nbsp;

## Unique, Primary, and Foreign Keys, plus Not Null, Check and Default constraints

Constraints in PostgreSQL are predefined rules and restrictions that are enforced in a single column or multiple columns, regarding the values allowed in the columns, to maintain the integrity, accuracy, and reliability of that column’s data. Constraints in PostgreSQL can be defined at the column level, where it is specified as part of the column definition and will be applied to that column only, or declared independently at the table level. 

&nbsp;

There are six main constraints that are commonly used in PostgreSQL: NOT NULL, UNIQUE, PRIMARY, FOREIGN, CHECK, and DEFAULT. &nbsp;

## Partitioning

PostgreSQL supports basic table partitioning.&nbsp; Partitioning refers to splitting what is logically one large table into smaller physical pieces. Partitioning can provide several benefits on the performance side.

## Indexes

The goal of an index on a database table then is to reduce I/O.&nbsp; Properly indexing a PostgreSQL table is key to providing consistent, optimal performance. There are many things to consider when designing an index structure, but this goes beyond the scope of this document. &nbsp;

&nbsp;

Hackolade supports the most common types of PostgreSQL indexes. &nbsp;

## Data types

PostgreSQLhas a rich set of [data types](<https://www.postgresql.org/docs/current/datatype.html> "target=\"\_blank\"") available to users.&nbsp; A data type is an attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.

&nbsp;

Additionally, in JSON and JSONB columns, Hackolade supports the data modeling of JSON documents with standard JSON data types: string, number, object, array, boolean, and null.&nbsp; We also support geometries and geographies used in PostGIS.

&nbsp;

User-defined data types are based on the data types in PostgreSQL. User-defined data types can be used when several tables store the same domain of values in a column and must ensure that these columns have exactly the same data type, length, and NULLability.

## Views

A view is a virtual table whose contents are defined by a query. Like a table, a view consists of a set of named columns and rows of data. Unless indexed, a view does not exist as a stored set of data values in a database. The rows and columns of data come from tables referenced in the query defining the view and are produced dynamically when the view is referenced.&nbsp; A view acts as a filter on the underlying tables referenced in the view. The query that defines the view can be from one or more tables or from other views in the current or other databases.

&nbsp;

## Functions and Procedures

A function takes any number of arguments and returns a value from the function body. The function body can be any valid SQL expression as you would use, for example, in any select expression.A Stored Procedure is a routine invoked with a [CALL](<https://www.postgresql.org/docs/current/sql-syntax-calling-funcs.html> "target=\"\_blank\"") statement. It may have input parameters, output parameters and parameters that are both input parameters and output parameters.&nbsp;

&nbsp;

In Hackolade Studio, functions and procedures are maintained at the schema level, where you will find dedicated tabs in the Properties Pane.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create databases, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

![Image](<lib/PostgreSQL%20DDL%20forward-engineering.png>)

&nbsp;

If you store documents in JSON or JSONB columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

To apply to instance, you need USAGE privileges, and if that's not possible, then at least INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT

## Reverse-Engineering

The PostgreSQL instance can be hosted on-premises, or on virtualized machines in a private or public cloud.&nbsp; Details on how to connect Hackolade to PostgreSQL can be found on [this page](<ConnecttoaPostgreSQLinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of PostgreSQL databases includes the execution of statements to discover databases, tables, columns and their types, indexes and constraints.&nbsp; For JSON and JSONB columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

**Important:** when reverse-engineering a PostgreSQL instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted the role USAGE. &nbsp; It more granularity is necessary, here are the full details:

&#49;) SELECT privileges on all tables in \`pg\_catalog\` schema (is default and included in PUBLIC role).

&#50;) Schemas: CREATE or USAGE privilege.

&#51;) Tables: SELECT or REFERENCES or TRIGGER privilege.

&#52;) Columns: SELECT or REFERENCES privilege.

&#53;) Views: SELECT or REFERENCES or TRIGGER privilege.

&#54;) Function: EXECUTE privilege.

&#55;) Domains: USAGE privilege.

&nbsp;

More information is available [here](<https://www.postgresql.org/docs/current/ddl-priv.html> "target=\"\_blank\"").

&nbsp;

For more information on PostgreSQL in general, please consult the [website](<https://www.postgresql.org/> "target=\"\_blank\"") and [documentation](<https://www.postgresql.org/docs/current/index.html> "target=\"\_blank\""). &nbsp;

