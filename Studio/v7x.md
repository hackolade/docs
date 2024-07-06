# v7.x

New features in v7.6.0 \[05-Jul-2024\]

\- Tech refresh of Electron (v31.1.0), NodeJS (v20.14.0), Chromium (v126.0.6478.114), V8 (v12.6) and related modules

\- Welcome page: updated social media icons

\- Diagram Objects pane: added possibility to add attributes to views

\- Collibra: added tolerance for trailing slash / in host URLs

\- PowerDesigner reverse-engineering: display warning dialog in case a package is detected in .ldm file

\- PowerDesigner reverse-engineering: open dialog in default reverse-engineering path if set

\- BigQuery: added adapter to adjust old models with change in partitioning structure

\- Cassandra: limited minProperties and maxProperties to Map, and Object data types, and MinItems/maxItems to List and Set data types

\- Cassandra and ScyllaDB: provided geospatial data type with properties so it can behave like an array

\- Couchbase legacy: added Activated property at attribute level

\- Couchbase: added indicator of segment order in structured PK&nbsp;

\- Graph targets: added zoom on node in canvas when selecting it in Object Browser

\- OpenAPI: allowed to edit Diagram View membership

\- Oracle: added support for Boolean data type in 23ai&nbsp;

\- Oracle: added support for JSON flex column in 23ai duality views

\- Oracle: adjusted mapping of integer when deriving from Polyglot

&nbsp;

New features in v7.5.1 \[28-Jun-2024\]

\- Docker image: upgraded to Ubuntu 24.04 LTS in latest version 0.0.20

\- Custom properties: display in a separate tab any detected custom prop that is not found in the local configuration

\- Excel import: eliminated false-positive warnings when reverse-engineering Excel file with custom properties

\- PowerDesigner .LDM file reverse-engineering: added import of custom extensions

\- Avro: added documentation for existing support of schema annotations&nbsp;

\- Couchbase v7+: added possibility to reverse-engineer an .n1ql file

\- Oracle: added support for vector data type in 23ai

\- CockroachDB, CosmosDB, Neptune, SQL Server, Tinkerpop, YugabyteDB: moved ssh tunneling from plugin to core app

&nbsp;

New features in v7.5.0 \[21-Jun-2024\]

\- Tech refresh of Electron (v30.1.1), NodeJS (v20.14.0), Chromium (v124.0.6367.243), V8 (v12.4) and related modules

\- Toolbar and Diagram Objects pane: changed to more obvious icons for Add Entity and Add Attributes

\- Bulk test data generation: upgraded FakerJS library to v8.4.1

\- Bulk test data generation: added Faker function capability at entity level to ensure consistency of related synthetic data within entity

\- Excel import: allowed changes to some properties in physical models derived from Polyglot, when already allowed in UI

\- Excel import: added log entry when import of changed property is not allowed

\- Graph diagrams: added centering canvas on selection in the Object Browser

\- PowerDesigner .LDM file reverse-engineering: added orthogonal distribution of entity boxes at end of process

\- Couchbase: added support for configurable structured Primary Key design based on existing fields, constants, separators, and patterns

\- Delta Lake/Databricks: updated parsing grammar for catalog names in create statements

\- MarkLogic: updated to latest SDK version 3.4.0

\- MarkLogic: added integer data type

\- BigQuery, CockroachDB, CosmosDB w/ MongoDB API, Elasticsearch, Firebase, Firestore, HBase, MariaDB, MarkLogic, MySQL, Protobuf, Redshift, SQL Server, Synapse, Teradata: limited minProperties and maxProperties to Map and Object data types

\- BigQuery, Delta Lake/Databricks, Glue, Hive, Redshift, Teradata: limited json data type to json objects and json arrays

\- Cassandra, MariaDB, Neo4j, ScyllaDB: moved ssh tunneling from plugin to core app

&nbsp;

New features in v7.4.8 \[14-Jun-2024\]

\- Object Browser: added alt+mouse click control so selection centers ERD canvas on selected object but without zoom

\- PowerDesigner .LDM file reverse-engineering: added support for import of super-types and sub-types

\- PowerDesigner .LDM file reverse-engineering: added import of architectureAreas into containers

\- Polyglot: limited minProperties and maxProperties to Map and Object data types

\- Oracle: moved ssh tunneling from plugin to core app

\- Oracle: limited minProperties and maxProperties to Map and Object data types

\- PostgreSQL: moved ssh tunneling from plugin to core app

\- PostgreSQL: limited minProperties and maxProperties to Map and Object data types

&nbsp;

New features in v7.4.7 \[10-Jun-2024\]

\- ERD rendering: added workaround for a regression in ReactJS function shouldComponentUpdate() that may affect opening of some models

&nbsp;

New features in v7.4.6 \[07-Jun-2024\]

\- PowerDesigner: added possibility to directly read .LDM files into Polyglot models, including entities, attributes, relationships, and logical diagrams (mapped to our Diagram Views)

\- Print diagram: adjusted container coordinates and size for PDF format

\- External model definitions: allowed cross-target references to be replaced by their attributes

\- Db2: adjusted validation of default property for string and numeric data types

\- Db2: disabled unsupported encrypt property, arrayType for XML data type, and json data type for array items

\- Neo4j: added logging for generating probabilistic schema logic

\- Oracle: renamed version 23c to 23ai

&nbsp;

New features in v7.4.5 \[31-May-2024\]

\- Diagram Objects pane: added possibility to drag-and-drop objects in desired location the canvas

\- Model validation: added validation of rules when an objects is in focus and property is changed

\- Model validation: added display of warning badge in Properties Pane tab

\- Collibra: added publishing of relationship cardinality into new custom attributes

\- Collibra: added reverse-engineering of relationship cardinality

\- Plugins: migrated to new deployment infrastructure with version 0.2.x

\- Teradata: rebuilt plugin client to support Java version 8 and above

&nbsp;

New features in v7.4.4 \[24-May-2024\]

\- Model validation: enhanced handling for custom rules in comments and descriptions

\- Model validation: added consistency of badge display in ERD and Object Browser in several circumstances

\- Collibra: refactored ability to fetch assets and related attributes with output module API for higher performance and scale

\- Diagram Objects pane: added an icon to add/append attribute

\- Polyglot: added adapter to auto-fix containers with references when derived from polyglot&nbsp;

\- Excel: added ability to clear boolean values

\- Excel: fixed import of data types binary, blob, and timestamp

\- Couchbase legacy and v7plus with scopes and collections: allowed key to use sample property in JSON data

\- Db2: added reverse-engineering from instance

\- PostgreSQL: added support for changes to and in unique keys in ALTER scripts

&nbsp;

New features in v7.4.3 \[17-May-2024\]

\- ERD: adjusted keyboard shortcut paste operation to place object in location of mouse cursor

\- Validation: added optional check of validation rules upon opening model, off by default, and controlled in Tools \> Options \> General

\- JSON Schema: added preservation of GUIDs during reverse-engineering when using the replace option of a conflict detection dialog

\- Workgroup edition: fixed hanging spinner in case of multiple subscriptions for an opened model change event

\- Avro: fixed handling of required property for complex types derived from polyglot models

\- Db2: added support for auxiliary tables

&nbsp;

New features in v7.4.2 \[10-May-2024\]

\- ERD and Object Browser panes: allow in-place editing of names for containers, entities and attributes with second click or F2 function key

\- Object Browser: added mark in entity title bar for reference to model and external definitions&nbsp;

\- Conflict detection: retain GUIDs (if available) in Replace option of conflict detection during reverse-engineering

\- Collibra: added progress report during reverse-engineering

\- Db2: added support for tablespaces

\- Db2: added support for index comments

\- Db2: added support for check constraints

\- Graph targets: enhance Diagram Views layout behavior when adding nodes

&nbsp;

New features in v7.4.1 \[08-May-2024\]

\- Personal Edition: enabled feature to Infer PKs and FKs

\- Graph targets: fixed issue when opening models more than once within a single application session

&nbsp;

New features in v7.4.0 \[03-May-2024\]

\- IBM Db2: soft launch -- added plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON data types -- additional feature support to be added progressively

\- ERD: added a collapsible Diagram Object section above the Object Browser to easily add objects

\- ERD: added mark in entity title bar for reference to model and external definitions&nbsp;

\- Added foreground opening of Windows Explorer when invoked

\- Added foreground opening of email message in Windows when invoked during error reporting

\- Collibra: adjusted reverse-engineering to reduce number of API calls when fetching attributes for assets

\- Cassandra: added map-reduce of map data type during reverse-engineering when multiple map samples are encountered

\- MySQL: enhanced decryption of key during SSH tunnel connection in Windows

\- OpenAPI: added requestBody only for request that allow it

\- OpenAPi: patched upgraded Swagger UI library to handle resolution of schema references with spaces in Windows path

&nbsp;

New features in v7.3.11 \[26-Apr-2024\]

\- ERD: added + button in title bar of entities to easily append new attribute/field/column

\- ERD: paste container boxes via shortcut in the place where mouse cursor is located

\- Error dialog: added fallback with shorter email in case max character limit reached with Outlook client

\- Browser deployment: added health check troubleshooting tile to download logs and contact support

\- Views: added possibility to pick columns from list of entities derived from Polyglot and definitions

\- Glue Data Catalog: added reverse-engineering of SerDe table property

\- Glue Data Catalog: updated to latest aws-sdk library version

\- Oracle: added ALTER script for creation and deletion of foreign key relationship constraints

\- PostgreSQL: added handling of min and max values in sequence during reverse-engineering

\- Teradata: added escaping wrapper for path to JAVA binary file

\- Teradata: added handling of Teradata cutting large DDLs into chunks during reverse-engineering

\- Teradata: added conversion of COMPRESS statements into ENUM attributes during reverse-engineering

&nbsp;

New features in v7.3.10 \[19-Apr-2024\]

\- ERD: paste entity boxes via shortcut in the place where mouse cursor is located

\- Collibra: increased logging in reverse-engineering process

\- Couchbase with scopes and collections: added possibility for multiple indexes plus export in JSON Schema full and extended compliance

\- MongoDB: fixed indicator of views in reverse-engineering entity picker dialog

\- Oracle: added ALTER script for the creation of an index on a newly created table or column

\- Parquet: added schema script tab at model level

\- PostgreSQL: added ALTER script for the creation of an index on a newly created table or column

\- Snowflake: added forward-engineering of composite key constraints

&nbsp;

New features in v7.3.9 \[12-Apr-2024\]

\- Command-Line Interface: allowed space as delimiter between argument key and value, in addition to existing equal sign

\- JSON Schema: added index key name when forward-engineering MongoDB index in Extended compliance

\- JSON Schema: refactored to preserve GUIDs in block/group properties when reverse-engineering files with Extended compliance

\- Workgroup: do not offer option to create local branch if branch of same name exists on remote

\- OpenAPI: limited forward-engineering of examples schema property to OAS 3.1.0+

\- OpenAPI: added requestBody for delete method in OAS 3.1+.&nbsp; While permitted, the spec advises to avoid it, given lack of precise semantics...

\- Synapse: reduced fetching of metadata to user-defines constraints, filtering out system metadata

\- Synapse: made reverse-engineering more resilient to complete process despite non-blocking errors

\- Synapse: skipped querying DB for sampling if sample is set to zero

\- Synapse: replaced parallel requests to instance with iterative calls via loop

&nbsp;

New features in v7.3.8 \[05-Apr-2024\]

\- Browser deployment: added health check screen, including first tile for config of browser's local storage

\- Naming conventions: adjusted business name validation if no technical name is present

\- JSON Schema export: added possibility to convert model definitions into internal definitions when they are already a subobject an an internal definition

\- Avro: added possibility to convert enum's symbol default to polyglot and derive from it

\- Couchbase with scopes and collections: added detection of multiple data types for collections with no primary index

\- DynamoDB: added restriction of multiple data types to JSON fields only

\- OpenAPI: adjusted generation of example property in sample JSON data when data type is other than string

\- Protobuf: added reverse-engineering of referencing field even if no internal definition is present in file

\- Protobuf: added filter for not referenced definition in individual message scripts

\- Synapse: added explicit config timeout control for query pool

\- Synapse: added API for connection string parsing

\- Teradata: added handling of large data sample

&nbsp;

New features in v7.3.7 \[01-Apr-2024\]

\- JSON Schema forward-engineering: added GUIDs for MongoDB indexes in Extended compliance

\- JSON Schema reverse-engineering: added possibility to reverse-engineer indexes in Full and Extended compliance

&nbsp;

New features in v7.3.6 \[29-Mar-2024\]

\- Avro: added validation of Symbol default property for enum data type

\- Avro: adjusted handling of default for enums in Avro schema forward-engineering

\- DeltaLake/Databricks: show in ERD length from maxLength property for char and varchar data types

\- Elasticsearch: added refresh\_interval\_unit property

\- Elasticsearch: added time\_series\_dimensions for ES v8 and up

\- Oracle: added forward- and reverse-engineering of sequences with instance

\- Oracle: added support for sequences in ALTER scrip of delta models

\- Snowflake: added more descriptive message if a view SELECT statement is invalid

\- Snowflake: upgraded libraries to remove potential vulnerabilities

\- XSD reverse-engineering: added error message when circular references are detected

&nbsp;

New features in v7.3.5 \[22-Mar-2024\]

\- Property validation: enhanced use of custom regex in validationRegularExpressions.json custom config file

\- Compare \& Merge: added display of differences for custom tabs at model level

\- Multiple data types: fixed handling in native targets (MongoDB, Couchbase, DynamoDB, and JSON) when custom properties are present at field level

\- Browser deployment: added handling with warning when site data is disabled

\- Community edition desktop and browser: enabled some previously disabled forward-engineering function for RDBMS and SQL-like targets -- limit of 50 objects remains

\- Collibra: enhanced handling of views referencing tables not present in the model

\- Databricks: added reverse-engineering of Unity Catalog tags in HQL files

\- OpenAPI: fixed generation of OAS 3.1 examples property when data type is other than string

\- Oracle: added support for creation and handling of sequences

\- Oracle: added DDL forward- and reverse-engineering of sequences from DDL

\- Protobuf: added commenting of schema lines for deactivated messages and columns

\- Protobuf: added handling for commented lines when reverse-engineering schemas

\- ADLS and Blog Storage: added ability to fetch Avro, JSON, and Parquet files in nested folders

&nbsp;

New features in v7.3.4 \[15-Mar-2024\]

\- Object picker dialog: refactored for more intuitive and consistent behavior of search, collapse/expand tree, and select all

\- Excel import: added handling of multiple polyglot references

\- Collibra: added global assignment configuration of foreign master relationships

\- Couchbase: added plugin for support of v7+ with scopes and collections

\- Couchbase v7+: handled race condition in forward-engineering Apply to instance

\- Couchbase v7+: handled creation of a collection even if no scope is declared

\- Elasticsearch v7+: adjusted field properties based on the selected subtype

\- Neo4j: added handling of JSON pattern fields for forward-engineering of properties in Cypher scripts

\- Oracle: added IF NOT EXISTS property for indexes, with dynamic SQL forward-engineering for versions prior to 23c and static SQL with 23c and after

\- Oracle: added reverse-engineering of IF NOT EXISTS in DDLs from 23C and above

\- Oracle: added ALTER script for indexes

&nbsp;

New features in v7.3.3 \[08-Mar-2024\]

\- Improved performance when opening models with new schema validation library (cut time in half)

\- Community edition desktop and browser: enabled some previously disabled functions: text diff, convert to polyglot, and verify data model -- limit of 50 objects remains

\- Entity tab schema tree view: removed 200px max length

\- Documentation and Print Diagram: removed 200px max length in all formats

\- Collibra: added reverse-engineering of logical data dictionaries into polyglot models

\- Databricks: added support for Unity Catalog tags in views

\- Databricks: added handling of Unity Catalog tags in ALTER scripts

\- MongoDB: added reverse-engineering of indexes in JSON Schema files exported with full or extended compliance

\- PostgreSQL: added reverse-engineering of sequences

\- PostgreSQL: added handling of sequences in ALTER scripts

\- PostgreSQL: added handling of indexes in ALTER scripts

&nbsp;

New features in v7.3.2 \[01-Mar-2024\]

\- Enhanced memory usage in model open/close processes

\- Print diagram: increased size of image for PNG format

\- Command-Line Interface: added new argument --references to polyglotUpdate command to allow granular selection

\- Command-Line Interface: deprecated old argument --selecteObjects from polyglotUpdate command

\- BigQuery: added possibility to comment out deactivated relationships in forward-engineering script

\- Databricks Unity Catalog: added support for tags in ALTER scripts of delta models

&nbsp;

New features in v7.3.1 \[23-Feb-2024\]

\- Object browser: significantly reduced memory consumption and increased stability with super large models

\- Collibra: added publishing of Polyglot models to Collibra logical data dictionaries with model/entity/attribute data assets

\- Databricks: added support for tags in Unity Catalog

\- Oracle: added support for function-based indexes

\- Oracle: removed case-sensitivity on inline constraints

\- Oracle: added support for reverse-engineering of hash-partitioned tables, plus composite partitions with LIST subpartitions

\- Polyglot: fixed "max map limit" error upon opening of super large models derived from polyglot

\- PostgreSQL: added support for creation and handling of sequences

\- Protobuf: added possibility to declare single and blocks comments between name and body

\- Synapse: added logger argument

&nbsp;

New features in v7.3.0 \[16-Feb-2024\]

\- Browser: official launch at https://studio.hackolade.com of Community Edition with common code base with Desktop: No credit card. No registration. No download. Runs in browser. No cookies. Local storage of models. Security first.

\- Desktop tech refresh to Electron (v28.2.2), NodeJS (v18.18.2), Chromium (v120.0.6099.276), V8 (v12.0) and related modules

\- Compare \& Merge and Impact Analysis: added button to select all deletions

\- Custom properties: fixed editing of group properties on references when using the enabledforReferences template variable

\- Plugin Manager: added detection of lack of Write rights in folder for plugin installation due to anti-virus

\- JSON: added nesting restriction for scalar data types

\- Oracle DDL reverse-engineering: enhanced parser to skip spool statements

\- Snowflake: updated to latest SDK version to circumvent Snowflake limit when sampling rate is higher that SDK's response capacity&nbsp;

&nbsp;

New features in v7.2.3 \[09-Feb-2024\]

\- DDL reverse-engineering: removed case-sensitivity of columns for PK constraints, indexes, and partitions

\- Polyglot: added support for entity references to handle the fact that this concept exists in Avro

\- Polyglot: added handling of deletion decorative symbols during update of references

\- Workgroup: renamed GitHub Enterprise into GitHub Server, since Enterprise is also available in github.com Cloud

\- Workgroup: removed the OAuth option from GitHub Server

\- Avro: added possibility to edit $ref property for references without definition

\- Collibra: added the possibility to fetch nested Communities

\- Oracle: added reverse-engineering of view comments and view column comments

&nbsp;

New features in v7.2.2 \[02-Feb-2024\]

\- Compare and Merge: added rendering of array items that are references

\- Polyglot Impact Analysis: added rendering of array items that are references

\- Reverse-Engineering from DDLs and XSDs: enriched log file to include system information

\- Collibra: optimized domain fetching logic and performance

\- Delta Lake/Databricks: allow forward-engineering of FK relationships for tables without a schema

\- Excel import: adjusted logic to reverse-engineer edge relationships into polyglot models

\- Oracle: added ability to reverse-engineer Duality View fields defined as simple column references

\- Oracle: relaxed constraint around former reserved keyword SEQ during reverse-engineering and parsing of DDLs

&nbsp;

New features in v7.2.1 \[29-Jan-2024\]

\- Reverted back to Electron v27.2.1 due to issues with workers on MacOS

\- Polyglot and external references: adjusted user experience for relative vs absolute path in file chooser&nbsp;

&nbsp;

New features in v7.2.0 \[26-Jan-2024\]

\- Tech refresh of Electron (v28.1.4), NodeJS (v18.18.2), Chromium (v120.0.6099.216), V8 (v12.0) and related modules

\- Infer PKs and FKs: added spinner to prevent user from multiple clicks on submit button

\- Polyglot: added filtering of views when converting target model to Polyglot

\- Polyglot: added comparison of annotation symbols to Impact Analysis screen

\- Polyglot: fixed anomaly during Impact Analysis of of normalized structures

\- Polyglot and external references: streamlined user experience for relative vs absolute path in file chooser&nbsp;

\- Workgroup Edition: added handling of HTML response from Git server during authentication

\- CockroachDB: added ability to model check constraints, including forward- and reverse-engineering

\- CockroachDB: added ability to model indexes, including forward- and reverse-engineering

\- Collibra: improved logging for publishing of custom configuration

\- Collibra: allowed for factory default reset when creating custom setup

\- Delta Lake/Databricks: added data type timestamp\_nz for Runtime 13 and up

\- Delta Lake/Databricks: changed container terminology from database to schema, as per Databricks recommendation

&nbsp;

New features in v7.1.1 \[19-Jan-2024\]

\- Command-Line Interface: allowed \* wildcard in --files argument of commands revEng, revEngJSON and revEngYAML

\- Application launch: display warning if application erroneously installed in AppData folder

\- Forward-engineering: added logging of system and application information&nbsp;

\- Custom properties: harmonized sample xLevelconfig;json file with array for all targets to show support custom tabs

\- Workgroup edition: added deselection by default for deletions in the Git conflict resolution screen

\- Workgroup edition: physical Git conflict markers are associated to logical differences in conflict resolution screen

\- CockroachDB: added support for reverse-engineering of UDTs

\- CockroachDB: added ability to model table partitions, including forward- and reverse-engineering

\- CockroachDB: added ability to model table options, including forward- and reverse-engineering

\- CockroachDB: added properties for using, partitioning, hash, and visibility clauses in indexes, plus ability to parse btree and and hash-sharded indexes

&nbsp;

New features in v7.1.0 \[12-Jan-2024\]

\- Tech refresh of Electron (v27.2.1), NodeJS (v18.17.1), Chromium (v118.0.5993.159), V8 (v11.8) and related modules

\- Polyglot: implemented 12x performance enhancement on refreshing references in derived models

\- ERD: adjusted box alignment function to keep zoom level

\- Properties Pane: added the automatic marking of Required/Not Null for PKs during reverse-engineering of JSON or derive from Polyglot

\- Documentation: added missing custom properties in native targets

\- Command Line Interface: fixed effect of --maxErdEntityBoxes argument of revEng commands

\- Workgroup : added default deselection of checkbox for deleted attributes in case of conflict resolution

\- CockroachDB: adjusted numeric data types to reflect CRDB's different approach than PostgreSQL

\- CockroachDB: fixed reverse-engineering of table comments

\- CockroachDB: removed tablespace clause from forward- and reverse-engineering

\- Delta Lake/Databricks: suppressed extraneous table options during reverse-engineering of DDL

\- Delta Lake/Databricks: added null safety check to filter check constraints

\- SQL Server/Synapse: increased logging to catch server timeouts during reverse-engineering

\- SQL Server/Synapse: removed unnecessary index query in reverse-engineering

&nbsp;

New features in v7.0.7 \[05-Jan-2024\]

\- Forward-engineering: added possibility to select individual entities of an ERDV

\- CockroachDB: added plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON and JSONB data types

\- Delta Lake/Databricks: suppressed extraneous space in encoding of special ASCII characters in object technical names

\- MariaDB: added possibility to define cross-schema views

\- MySQL: added possibility to define cross-schema views

\- Oracle: relaxed technical name validation to allow all ASCII characters, as DDL generation uses quotes

\- Oracle: added possibility to define cross-schema views

\- PostgreSQL: added possibility to define cross-schema views

\- Teradata: added possibility to define cross-schema views

\- YugabyteDB: added possibility to define cross-schema views

&nbsp;

New features in v7.0.6 \[29-Dec-2023\]

\- Compare and Merge: enhanced detection of duplications and deletions in merge conflicts for models derived from polyglot

\- Excel: fixed inconsistent behavior in persistence of selected column options

\- Avro: added support for cross-namespace schema references

\- Cassandra: added support for the Cassandra 5.0 vector\<float,dimension\> data type

\- Cassandra: added possibility to create custom index with similarity\_function option for vector search

&nbsp;

New features in v7.0.5 \[22-Dec-2023\]

\- ERD: implemented 10x performance improvement when display name is technical

\- Polyglot: implemented update of entity name changes in impact analysis screen

\- ERDV: fixed adding entities to ERDV via contextual menu

\- Excel: added exclusion of entity and view columns in export&nbsp;

\- Forward-engineering: restructured selection tree in entity picker dialog

\- Reverse-Engineering: added reset of entity selection after cancel and immediate restart of the process

\- Avro: added use of record technical name in Schema Registry API forward-engineering of entity references in choices

\- Snowflake: further enhanced parsing of view SELECT statements and forward-engineering of view select statements

&nbsp;

New features in v7.0.4 \[15-Dec-2023\]

\- ERD: added possibility to add FK relationships from parent to child with creation of attribute in child entity.&nbsp; Behavior can be toggled with child-to-parent direction in Tools \> Options \> General.&nbsp; Opposite behavior possible with Ctrl+mouse drag-and-drop

\- Context bar: added Home icon for 1-click access to Welcome page

\- External definitions and parent polyglot model: added Properties Pane button to open reference in new instance

\- Forward-engineering: added possibility to create files according to ERDV membership

\- Workgroup: added tolerance for undocumented 8-symbol conflict markers

\- Avro: added escaping of the schema in forward-engineering with the Schema Registry format

\- Avro: used namespace.name for generation of schema references in forward-engineering with the Schema Registry format

\- Couchbase: upgrade to latest v4.2.4 of couchnode SDK

\- Couchbase: added handling of bucket names with spaces and special characters

\- Couchbase: added handling of delays in creation of new bucket by target instance

\- Databricks: added possibility to generate FaskerJS-based bulk synthetic INSERT records for testing

\- MongoDB: added consent dialog about risks of executing JavaScript when reverse-engineering Mongoose schema files

\- RDBMS and OLAP targets: removed extraneous View On property as DDL is assembled based on the table of the selected columns

\- Snowflake: further enhanced parsing of view SELECT statements to include options in WHERE clauses

&nbsp;

New features in v7.0.3 \[08-Dec-2023\]

\- External definitions: enabled selection of choices and subschemas in external references

\- ERD: fixed bug preventing duplicate action on entities

\- FK relationship: allowed update of relationship name from the child attribute's properties pane

\- Avro: added support for forward- and reverse-engineering of schemas made of oneOf union of schema references

\- Delta Lake/Databricks: removed extraneous View On property as DDL is assembled based on the table of the selected columns

\- DocumentDB: added handling of special characters in username/password

\- MongoDB: added handling of invalid BSON date data type

\- PostgreSQL/YugabyteDB: added estimated rows to udf if the function returns a set

\- PostgreSQL/YugabyteDB: allowed definition of number of estimated rows for udfs that returns table

\- PostgreSQL/YugabyteDB: added comments on functions to DDL generation

\- PostgreSQL/YugabyteDB: allowed creation of indexes without a method

\- Snowflake: added support for view SELECT statements with nested statements and Snowflake-specific syntax like OVER clause and multiple clauses

&nbsp;

New features in v7.0.2 \[01-Dec-2023\]

\- Model obfuscation: added effect to attributes added to a target model derived from polyglot

\- Bulk test data generation: upgraded FakerJS library to v8.3.1

\- Forward-engineering to file system: removed format from the folder name only for unstructured path

\- Avro: removed extraneous POST command in forward-engineering for Schema Registry

\- Delta Lake/Databricks: replaced blanks and dots with underscores in FK relationship constraint names to avoid Unity Catalog restriction not handling backticks

\- Hive: removed extraneous mode=int for in JSON Schema Full compliance when type=integer

\- OpenAPI: removed restriction to replace schema with component reference when derived from polyglot

\- PostgreSQL: removed restrictions on composite PKs when adding update columns to triggers

\- Redshift: removed extraneous mode=int for in JSON Schema Full compliance when type=integer

\- Snowflake: added support for view SELECT statements referencing parsed JSON

\- YugabyteDB: removed restrictions on composite PKs when adding update columns to triggers

&nbsp;

New features in v7.0.1 \[24-Nov-2023\]

\- License status screen: added copying of license key to clipboard prior to release

\- Views: enabled changing the database/schema container while keeping reference to the view on table property

\- Excel: added export and import of lineage sources

\- Polyglot: added possibility to select individual branch of subtype relationship to be deleted

\- Forward-engineering to file system: added format to the folder name

\- Avro: added option to include namespace as part of file name during forward-engineering to file

\- Cosmos DB with Core API: updated axios library to latest to take into account latest vulnerabilities

\- Delta Lake/Databricks: added support for table level constraints

\- Delta Lake/Databricks: adjusted conditions for which USE CATALOG statement is generated in DDL forward-engineering

\- PostgreSQL: added support for NULLS NOT DISTINCT in unique indexes and unique key constraints

\- PostgreSQL: added support for DEFERABLE unique constraints

\- PostgreSQL: added support for stored generated columns

&nbsp;

New features in v7.0.0 \[17-Nov-2023\]

\- Browser: deployment of Community Edition with common code base with Desktop, soft launched at https://studio.hackolade.com, basis for many upcoming enhancements

\- Desktop: Community Edition no longer requires a license key

\- Desktop: redesigned License status screen, also available from Context bar

\- License status screen: added one-step validation of another key, replacing 2-step release of old key plus validation of new key

\- Application packaging: added OS-specific prebuild of native modules

\- Command-Line Interface: added different file name patterns to compMod command \[commit:\]\[path\]\<*file*\> with OS-based escaping for names with spaces

\- Command-Line Interface: added logging and friendly error messages

\- Avro: added possibility to use --defstrategy CLI argument to specify whether an entity should be resolved (default) or referenced

\- Cosmos DB with Core API: added fine-tuning of database and container creation via Azure CLI for partition-key-path, serverless, and TTL parameters

\- Delta Lake/Databricks: added support for data type changes in ALTER script of delta models

\- Delta Lake/Databricks: added support for SET LOCATION changes in ALTER script of delta models

\- Delta Lake/Databricks: added support for SET/UNSET TBLPROPERTIES changes in ALTER script of delta models

\- Oracle: added import of out-of-line column comments in DDL files

\- Snowflake: added schema name escaping plus function arguments, comments generation, and references in CONSTRAINT statements

&nbsp;

&nbsp;

&nbsp;

&nbsp;

