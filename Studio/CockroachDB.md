# CockroachDB

CockroachDB is a commercial distributed SQL database management system developed by Cockroach Labs.&nbsp; It is built on a transactional and strongly-consistent key-value store. It **scales** horizontally; **survives** disk, machine, rack, and even datacenter failures with minimal latency disruption and no manual intervention; supports **strongly-consistent** ACID transactions; and provides a familiar **SQL** API for structuring, manipulating, and querying data.

&nbsp;

CockroachDB is compatible with version 3.0 of the PostgreSQL wire protocol (pgwire) and the majority of PostgreSQL syntax. This means that existing applications built on PostgreSQL can often be migrated to CockroachDB without changing application code.&nbsp; However, CockroachDB does not support some of the PostgreSQL features or behaves differently from PostgreSQL because not all features can be easily implemented in a distributed system. [This page](<https://www.cockroachlabs.com/docs/stable/postgresql-compatibility> "target=\"\_blank\"") documents the known list of differences between PostgreSQL and CockroachDB for identical input.

&nbsp;

CockroachDB supports two JSON data types: JSON and JSONB. They accept *almost* identical sets of values as input. The major practical difference is one of efficiency. The JSON data type stores an exact copy of the input text, which processing functions must reparse on each execution; while JSONB data is stored in a decomposed binary format that makes it slightly slower to input due to added conversion overhead, but significantly faster to process, since no reparsing is needed. JSONB also supports indexing, which can be a significant advantage.

&nbsp;

To perform data modeling for CockroachDB with Hackolade, you must first download the CockroachDB [plugin](<https://hackolade.com/help/DownloadadditionalDBtargetplugin.html> "target=\"\_blank\"").  

&nbsp;

Hackolade was specially adapted to support the data modeling of CockroachDB, including schemas, tables and views, indexes and constraints, plus the generation of DDL Create Table syntax.&nbsp;

&nbsp;

In particular, Hackolade has the unique ability to model complex semi-structured objects stored in columns of the JSON and JSONB data types.&nbsp; We're not talking about functions that "flatten" JSON into standard columns, which runs the risk of inconsistencies, if not errors, when doing the Cartesian product of multiple complex data types.&nbsp; But about the storage of entire JSON documents.&nbsp; The reverse-engineering function, if it detects JSON documents, will sample records and infer the schema to supplement the DDL table definitions. &nbsp;

&nbsp;

The data model in the picture below results from the data modeling of the [flights booking demo](<https://postgrespro.com/education/demodb> "target=\"\_blank\""):

&nbsp;

![Image](<lib/PostgreSQL%20workspace.png>)

&nbsp;

## Databases and schemas

A database can contain one or multiple schemas and each schema belongs to only one database. Two schemas can have different objects that share the same name. &nbsp;

&nbsp;

A schema is a namespace that contains named database objects such as tables, views, indexes, data types, functions, stored procedures and operators.&nbsp; Schemas allow you to organize database objects e.g., tables into logical groups to make them more manageable.&nbsp; CockroachDB automatically creates a schema called public for every new database. Whatever object is created without specifying the schema name, CockroachDB will place it into this public schema.&nbsp; In practice, it is better to refer to a table using a fully qualified name.

&nbsp;

A single Hackolade model deals with a single database but can handle multiple schemas.

&nbsp;

## Tables

A table consists of rows and columns. The number and order of the columns is fixed, and each column has a name.&nbsp; Each column has a data type. The data type constrains the set of possible values that can be assigned to a column and assigns semantics to the data stored in the column so that it can be used for computations.

&nbsp;

## Unique, Primary, and Foreign Keys, plus Not Null, Check and Default constraints

Constraints in CockroachDB are predefined rules and restrictions that are enforced in a single column or multiple columns, regarding the values allowed in the columns, to maintain the integrity, accuracy, and reliability of that column’s data. Constraints in CockroachDB can be defined at the column level, where it is specified as part of the column definition and will be applied to that column only, or declared independently at the table level. 

&nbsp;

There are six main constraints that are commonly used in CockroachDB: NOT NULL, UNIQUE, PRIMARY, FOREIGN, CHECK, and DEFAULT. &nbsp;

## Partitioning

CockroachDB supports basic table partitioning.&nbsp; Partitioning refers to splitting what is logically one large table into smaller physical pieces. Partitioning can provide several benefits on the performance side.

## Indexes

The goal of an index on a database table then is to reduce I/O.&nbsp; Properly indexing a CockroachDB table is key to providing consistent, optimal performance. There are many things to consider when designing an index structure, but this goes beyond the scope of this document. &nbsp;

&nbsp;

Hackolade supports the most common types of CockroachDB indexes. &nbsp;

## Data types

CockroachDB has a rich set of [data types](<https://www.postgresql.org/docs/current/datatype.html> "target=\"\_blank\"") available to users.&nbsp; A data type is an attribute that specifies the type of data that the object can hold: integer data, character data, monetary data, date and time data, binary strings, and so on.

&nbsp;

Additionally, in JSON and JSONB columns, Hackolade supports the data modeling of JSON documents with standard JSON data types: string, number, object, array, boolean, and null. &nbsp;

&nbsp;

User-defined data types are based on the data types in CockroachDB. User-defined data types can be used when several tables store the same domain of values in a column and must ensure that these columns have exactly the same data type, length, and NULLability.

## Views

A view is a virtual table whose contents are defined by a query. Like a table, a view consists of a set of named columns and rows of data. Unless indexed, a view does not exist as a stored set of data values in a database. The rows and columns of data come from tables referenced in the query defining the view and are produced dynamically when the view is referenced.&nbsp; A view acts as a filter on the underlying tables referenced in the view. The query that defines the view can be from one or more tables or from other views in the current or other databases.

&nbsp;

## Forward-Engineering

Hackolade dynamically generates the DDL script to create databases, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Image](<lib/PostgreSQL%20DDL%20forward-engineering.png>)

&nbsp;

If you store documents in JSON or JSONB columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

To apply to instance, you need USAGE privileges, and if that's not possible, then at least INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT

## Reverse-Engineering

The CockroachDB instance can be hosted on-premises, or on virtualized machines in a private or public cloud.&nbsp; Details on how to connect Hackolade to CockroachDB can be found on [this page](<ConnecttoaCockroachDBinstance.md>).

&nbsp;

The Hackolade process for reverse-engineering of CockroachDB databases includes the execution of statements to discover databases, tables, columns and their types, indexes and constraints.&nbsp; For JSON and JSONB columns, Hackolade performs statistical sampling of records followed by probabilistic inference of the JSON document schema.

&nbsp;

**Important:** when reverse-engineering a CockroachDB instance, non-privileged users can see the metadata of only their own objects, so to access others you need to be be granted the role USAGE. &nbsp; It more granularity is necessary, here are the full details:

&#49;) SELECT privileges on all tables in \`pg\_catalog\` schema (is default and included in PUBLIC role).

&#50;) Schemas: CREATE or USAGE privilege.

&#51;) Tables: SELECT or REFERENCES or TRIGGER privilege.

&#52;) Columns: SELECT or REFERENCES privilege.

&#53;) Views: SELECT or REFERENCES or TRIGGER privilege.

&#54;) Function: EXECUTE privilege.

&#55;) Domains: USAGE privilege.

&nbsp;

More information is available [here](<https://www.cockroachlabs.com/docs/stable/security-reference/authorization#privileges> "target=\"\_blank\"").

&nbsp;

For more information on CockroachDB in general, please consult the [website](<https://www.cockroachlabs.com/> "target=\"\_blank\"") and [documentation](<https://www.cockroachlabs.com/docs/> "target=\"\_blank\""). &nbsp;

