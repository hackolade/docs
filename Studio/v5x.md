# v5.x

New features in v5.4.4 \[11-Feb-2022\]

\- Reverse-Engineering: added progress bar during parsing of views' SELECT statement

\- Confluent Schema Registry: added possibility to specify a cookie name-value pair to be inserted in during forward-engineering the HTTP header, for example to address BlueCoat SSL inspection re-encrypting with an internal certificate

\- Cosmos DB: added choice of Capacity Mode, to choose between provisioned throughput or serverless

\- DynamoDB: added support for JSON structures in attributes of String data type

\- DynamoDB: added property for Table Class to support Standard-IA (Infrequent Access)

\- DynamoDB: added handling of Capacity Mode (aka Billing Mode) for Provisioned Throughput or On-Demand (aka Pay-per-Request)

\- DynamoDB: added possibility for views (aka facets) to have different Primary and Sort keys than their underlying table in single-table design

\- DynamoDB: added primary and sort keys when deriving from Polyglot

\- MongoDB: added handling of missing property in projection of read-only views during reverse-engineering of pipeline

\- Neo4j, version 4.3 and above: added IF NOT EXISTS for CREATE CONSTRAINT statements

\- Oracle: added handling of quotes in comments during reverse-engineering

\- PostgreSQL: changed reverse-engineering to leverage connection pooling

\- PostgreSQL: added checkbox to control whether to include partitions in table selection dialog, default unchecked

\- PostgreSQL: added handling of table triggers (maintenance, forward- and reverse-engineering)

&nbsp;

New features in v5.4.3 \[04-Feb-2022\]

\- Confluent Schema Registry: added possibility to specify a cookie name-value pair to be inserted in during reverse-engineering the HTTP header, for example to address BlueCoat SSL inspection re-encrypting with an internal certificate

\- Hive: Added if not exists property for databases, tables, and view

\- Hive: Added forward-engineering of row format serde when stored as input/output format

\- OpenAPI: added validation during reverse-engineering, plus display of warning dialog

\- Oracle: added generation of ALTER statements from delta model

\- Oracle: added possibility to fetch system schemas in table selection dialog

\- PostgreSQL: added connection with ssl modes allow, prefer, require

\- PostgreSQL: added handling for empty body in views and procedures

\- PostgreSQL: added reverse-engineering of functions when user is not their owner

\- Snowflake: added wrapping of role with double quotes when it contains special characters

&nbsp;

New features in v5.4.2 \[28-Jan-2022\]

\- Software Key Validation dialog: pre-fill of optional Identifier field with Computer Name + OS username.&nbsp; Can be cleared or overwritten if desired

\- ERD: added more display options to hide attributes with specific properties (non-primary keys, non-required attributes, nullable attributes, etc.)

\- Polyglot: when deriving into Swagger/OpenAPI, added possibility to merge with a template, like with model-driven API generation

\- Avro: added possibility to reverse-engineer multiple record schemas in single .avsc file

\- Databricks: enhanced context creation, plus added Runtime 9 support

\- Oracle: added config to allow connection to Amazon RDS

\- Oracle: added connection by SID

\- Oracle: added possibility to narrow scope of discovery of instance to a single user schema

\- Oracle: added reverse-engineering of table and column comments

\- PostgreSQL: adjusted reverse-engineering of indexes and functions when version 10

\- Snowflake: added timeout from tools options, plus used warehouse auth by credentials

\- Snowflake: added handling of cross-schema views

\- Snowflake: added possibility to apply DDL script to instance

\- Snowflake: added generation of ALTER statements from delta model

\- Snowflake: added snippets for GeoJSON geometries in data type geography

&nbsp;

New features in v5.4.1 \[21-Jan-2022\]

\- Custom properties: ability to mark a custom property with a star (\*) to indicate a required entry, optionally with validation.&nbsp; Consult https://github.com/hackolade/plugins#26-property-controls for more details

\- Model-driven API generation: added choice to keep Swagger/OpenAPI linked to source data model for synchronized evolution, with absolute or relative path

\- Collibra: added publishing of Hackolade custom properties

\- Couchbase: adjusted logic to display dialog to choose document type prompt even if INFER statement returned flavors

\- Delta Lake/Databricks: stopped linking partition keys to primary keys, and detached PARTITION BY statement from column declaration

\- Oracle: added possibility to apply DDL script to instance

\- Snowflake: added GeoSpatial data types

\- SQL Server \& Synapse: added IF NOT EXISTS property for schemas, tables, and views with DDL handling via wrapping of CREATE statement in begin...end and a SELECT to check existence of object

\- all Graph targets when exchanging with Excel: do NOT use a template generated with a previous version of the plugins.&nbsp; Make sure to export model to Excel first, as some of the tab names have been adjusted. &nbsp;

&nbsp;

New features in v5.4.0 \[14-Jan-2022\]

\- Oracle: soft release of a new plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON data types (Oracle 21c and above) and of JSON documents in VARCHAR2, CLOB and BLOB data types (12c, 18c, and 19c) -- many improvemens still to come...

\- Polyglot: added possibility to modify properties of attributes in target model, and hence deviate from the polyglot model (deactivate an attribute, or change constraints,...)

\- Polyglot: enhanced documentation in case of relationships or custom tab of properties&nbsp;

\- JSON Schema reverse-engineering: added dialog to save model when external recursive external references have a relative path

&nbsp;

New features in v5.3.5 \[11-Jan-2022\]

\- Added help button with link to online documentation in Connection Settings dialog of various targets

\- JSON Schema reverse-engineering: enhanced list of missing external definition files for unresolved recursive references

\- Added handling for external references to root of JSON Schema, for example "$ref": "party.json#"

\- Collibra: enhanced reverse-engineering to maintain coupling of business and technical names

&nbsp;

New features in v5.3.4 \[31-Dec-2021\]

\- JSON Schema reverse-engineering: display warning dialog if missing external reference files

\- Cassandra/ScyllaDB: harmonized path and file name for ALTER script CQL file from compMod delta model

\- OpenAPI: added possibility to choose between resolution of references when converting to Polyglot, or save as model definitions (UDTs)

\- PostgreSQL: added CLI command to generate ALTER script DDL from compMod delta model

\- SQL Server: added support for SSL and SSH connections

&nbsp;

New features in v5.3.3 \[24-Dec-2021\]

\- Naming conventions: added tooltips to = signs for coupling of business and technical name

\- Collibra: added Technical Name characteristic and changed mapping of Full Name to use technical name if present

\- JSON Schema reverse-engineering: added tolerance for $ref with OpenAPI structure "/components/schemas/..."

\- JSON Schema reverse-engineering: added tolerance for $ref at root level

\- Avro: added handling of multiple types inside choices

\- Delta Lake/Databricks: refactored reverse-engineering process&nbsp;

\- SQL Server: automatically attempt to reconnect without encryption if localhost set with encryption

&nbsp;

New features in v5.3.2 \[17-Dec-2021\]

\- Avro: added logicalType object generation for definitions

\- Delta Lake/Databricks: implemented support for decimal type precision and scale

\- Delta Lake/Databricks: added handling for truncated output response of the Databricks API

\- MarkLogic: filter out non-JSON documents during reverse-engineering

\- SQL Server: added handling for empty DEFAULT during reverse-engineering

\- all RDBMS targets: enabled choices for JSON data types in JSON columns

&nbsp;

New features in v5.3.1 \[10-Dec-2021\]

\- Model compare and merge: increased consistency between CLI and GUI outputs

\- Avro: added logicalType property generation for local-timestamp-millis and local-timestamp-micros

\- BigQuery: added string literals with quotes and new lines in DDL forward-engineering

\- Cassandra/ScyllaDB: adjusted handling of of CQL for columns with data type map

\- Confluent Schema Registry with Avro Schema, JSON Schema, and Protobuf: added ability to attach a Trust Store (.jks) file for connection

\- Hive: added string literals with quotes and new lines in DDL forward-engineering

\- MariaDB: added string literals with quotes and new lines in DDL forward-engineering

\- MongoDB: improved reverse-engineering when empty collections are in instance

\- MongoDB: improved reverse-engineering when views have unsupported pipeline stage

\- PostgreSQL: improved reverse-engineering to retrieve only columns data types json and jsonb for sampling

\- SQL Server: added handling of additional table options in temporal tables

\- Synapse: added handling of views with binding errors during reverse-engineering

\- all RDBMS targets: improved warning to list names when reverse-engineering choices from JSON Schema or XSDs

&nbsp;

New features in v5.3.0 \[03-Dec-2021\]

\- JSON Schema: added support for undefined data types marked "any"&nbsp;

\- Amazon DocumentDB: added support with a new plugin with full support for forward-and reverse-engineering including inference of schemas in collections

\- Network proxy: added a Test button with log

\- Confluent Schema Registry with Avro Schema, JSON Schema, and Protobuf: added an option for unvalidated SSL connection

\- Avro: adjusted forward-engineering of nested logicaTypes

\- PostgreSQL: added handling when user has insufficient rights to read view select statement from information\_schema

\- PostgreSQL: added handling of column encoding in forward- and reverse-engineering

\- SQL Server: added support for temporal tables

&nbsp;

New features in v5.2.13 \[29-Nov-2021\]

\- Polyglot: when deriving into an RDMBS target and normalizing, enhanced handling to use existing primary keys

\- Polyglot: when converting from Swagger/OpenAPI model, convert component schema definitions into polyglot entities

\- License key validation and concurrent seat activation/release: added option to switch to disaster recovery license server if primary server is down

\- Network proxy: enhanced handling of basic auth

\- Avro: added possibility to edit references to external Avro schemas

\- Avro: enhanced validator to handle external references

&nbsp;

New features in v5.2.12 \[23-Nov-2021\]

\- Avro:added handling of multiple references to same definition in schema generation

\- Avro: added handling for external schema references&nbsp;

\- Delta Lake/Databricks: added reverse-engineering of binary subtypes to complex data types

\- SQL Server: added possibility to disable connection encryption with the SQL Server auth method (to match SSMS options)

\- all RDBMS targets: added warning and handling of choices in reverse-engineering of JSON Schema or XSDs, by picking only the first subschema

&nbsp;

New features in v5.2.11 \[19-Nov-2021\]

\- Polyglot: added handling of edges (with properties) in the context of graph databases

\- Polyglot: disabled and cleaned technical names in definitions

\- MariaDB: adjust API for MySQL driver

\- OpenAPI: added handling of empty properties in reverse-engineering of file

&nbsp;

New features in v5.2.10 \[12-Nov-2021\]

\- Replaced the .hackolade.json filename extension when saving a model with a shorter .hck.json filename extension.&nbsp; Also reduces ambiguity with other .json files

\- ERD: added possibility to select multiple objects via mouse shift+click+drag if clicking inside a container, or or new toolbar button

\- Object Browser: added contextual menu option to alpha sort containers

\- Custom properties: added orderedList capability in group control

\- Collibra: changed REST API channel to accommodate Zscaler proxy with SSL inspection

\- Collibra: allowed publishing of polyglot models

\- Collibra: allowed publishing of models when out-of-the box system attribute types have been edited

\- JSON Document reverse-engineering into RDBMS targets: added detection of ISO 8601 date/time/timestamp/duration in JSON strings, and convert them to best matching data type

\- Polyglot: added warning and handling of choices in reverse-engineering of JSON Schema or XSDs

\- Hive: enabled optional normalization of complex data types when reverse-engineering JSON Data, JSON Schema, or XSDs

\- OpenAPI/Swagger: added control to easily reorder tags

\- PostgreSQL: added forward- and reverse-engineering of PostGIS data types

\- Protobuf: adjusted field numbering in case of oneOf, plus added bool data type as a key type of map

\- SQL Server DDL reverse-engineering: added tolerance for spaces in index declaration

\- SQL Server/Azure SQL: added Azure Active Directory options: username/password, integrated, and with MFA

\- all RDBMS targets: when reverse-engineering JSON Schema with null data type while such type is not available in target, added conversion of field into a string-like data type with null allowed

&nbsp;

New features in v5.2.9 \[05-Nov-2021\]

\- ERD: enhanced placement of new entities inside visible area

\- Model compare \& merge: added option to match by business name or technical name when matching by ID is not possible

\- Model compare \& merge: use naming conventions display choice when matching by ID, or respective name matching choice

\- Polyglot: added Examples property to allow multiple examples for OpenAPI

\- Polyglot: added primary key for "id" columns during automatic normalization of complex objects when deriving into RDBMS targets

\- Polyglot: added checkbox to disable automatic normalization of complex objects when deriving into RDBMS targets

\- OpenAPI file tab: enabled Cmd+C on Mac

\- OpenApi \& Event Bridge: updated request parameter style prop options

\- PostgreSQL: added sslmode support

\- PostgreSQL: added advanced DDL parsing

\- PostgreSQL: added PostGIS data types

&nbsp;

New features in v5.2.8 \[29-Oct-2021\]

\- PostgreSQL: added support with a new plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON and JSONB data types

\- Protobuf: added support with a new plugin with full support for forward-engineering of Protobuf schema, and reverse-engineering, including files on Cloud storage or Schema Registries (Confluent and Pulsar)

\- Added a check when attempting to reverse-engineer a data model instead of just opening it

\- Replaced the .json filename extension when saving a model with a .hackolade.json filename extension to reduce ambiguity with other .json files

\- Added an option in the OS Open dialog to filter files by .hackolade.json extensions

\- Added possibility to define a non-default path for custom properties in Toots \> Options \> Default Paths, for example to align with different development branches

\- Added styling for relationship lines: thickness and color

\- Added possibility to resize textarea dialogs (description, comments, ...)

\- Enhanced line break handling in names of nodes/vertices in graph targets

\- Added logic to auto-select relevant entities of ERD Views when generating documentation

\- Added obfuscation of annotations

\- Collibra: added CLI command to reverse-engineer or synchronize Collibra domain into a Hackolade data model

\- Polyglot: renamed Not Null property to Required (fully understanding that the semantics are different...)

\- Polyglot: implemented conversion of not-required attributes without default for Avro into multiple data types with NULL as primary

\- Polyglot: enhanced the handling of primary keys when deriving from polyglot into Cassandra, Couchbase, and ScyllaDB

\- Polyglot: adjusted conversion of nvarchar data type for MariaDB into varchar with national = true

\- Polyglot: added back the&nbsp; technical name property, but disabled, to clarify that it is not missing

\- Cassandra/ScyllaDB: ignore column moves in ALTER script

\- Snowflake: implemented dollar-quoted comments in DDL forward-engineering

&nbsp;

New features in v5.2.7 \[22-Oct-2021\]

\- JSON document: added detection of string length in nested objects when reverse-engineering into RDBMS targets

\- JSON Schema: added explicit forward-engineering of additionalProperties when set to false

\- Graph database plugins: added a graph view to the ERDV capability

\- Model Compare \& Merge: added alpha sorting of objects in trees to facilitate comparison

\- Polyglot: added denormalization of embedded references when deriving from polyglot to an RDBMS target

\- Polyglot: added length decorators in ERD

\- Cassandra/ScyllaDB: added reverse-engineering of data center name, replication factor, and durable writes from CQL file for each keyspace, if present

&nbsp;

New features in v5.2.6 \[15-Oct-2021\]

\- Polyglot: added inclusion of Clustering Key in primary key when converting models from Cassandra/ScyllaDB

\- Polyglot: allowed primary on additional data types

\- Neo4j: added support for indexes on relationship types for version 4.3 and above

&nbsp;

New features in v5.2.5 \[11-Oct-2021\]

\- Graph databases: adjusted creation of nodes for missing relationships in ERDV

&nbsp;

New features in v5.2.4 \[08-Oct-2021\]

\- Command Line Interface: added --maxErdEntityBoxes argument to revEng, revEngJSON, revEngYAML, revEndDDL, and revEngXSD

\- JSON Schema: added handling of reference description in forward- and reverse-engineering for drafts 2019-09 and 2020-12

\- Polyglot data model: added sign in entity selection dialog next to objects not present in target models

\- Collibra reverse-engineering: added a target compatibility check and warning message

\- Avro: added resolution of UDT in choices, plus handling of arrays without items in union

\- Cassandra Datastax: added support for SASI custom indexes

\- Cassandra \& ScyllaDB: added property to add IF NOT EXISTS in forward-engineering statements if desired

\- Cassandra: removed CREATE KEYSPACE from forward-engineering when applying to Atlas instance (as keyspace cannot be created via script)

&nbsp;

New features in v5.2.3 \[04-Oct-2021\]

\- RDBMS targets: adjusted normalization when reverse-engineering JSON Schema

&nbsp;

New features in v5.2.2 \[01-Oct-2021\]

\- External definitions: added possibility to reference model of any target.&nbsp; Was previously restricted to JSON Schema or model of the same target.

\- External definitions: added resolution of custom properties in JSON Schema preview and forward-engineering

\- Model Compare \& Merge: added on-click button to open each model in a separate instance

\- Plugin Manager: added update button in Available tab if a new version of an installed plugin exists

\- Tools \> Options \> Forwarded-Engineering: added preferred settings for JSON Schema specification, used on JSON Preview and in forward-engineering of JSON Schema

\- XSD reverse-engineering: added support for sql:datatype tag for erwin physical models

\- Cassandra: added different index abbreviations in ERD to distinguish Secondary (2Ix.y) from Search (SIx.y) indexes

&nbsp;

New features in v5.2.1 \[24-Sept-2021\]

\- JSON Schema: added support for latest draft 2020-12

\- Collibra: added possibility to reverse-engineer and merge into Hackolade data model.&nbsp; Also helps truly sync content that may have been entered in Collibra

\- Introduced a Tools \> Options \> Display tab gathering all the display settings: moved some from the General tab, plus added more

\- Tools \> Options \> Forward-Engineering: added a JSON Schema section with preferred settings for compliance and definitions handling, used on JSON Preview and in forward-engineering of JSON Schema

\- JSON Preview and forward-engineering of JSON schema now use preferences set in Tools \> Options \> Forward-Engineering

\- JSON Schema reverse-engineering: adjusted handling of external references when schema only has definitions

\- Alternate keys: added ERD display of multiple constraints on same column

\- Avro reverse-engineering of JSON Schema: added handling of not-required arrays with oneOf choice

\- Delta Lake:added mirroring for table properties, refactored JSON formation, unbatched getting DDL command, refactored table properties parsing

\- Snowflake: added reverse-engineering of auto-increment property, fixed skipped columns during reverse-engineering

&nbsp;

New features in v5.2.0 \[17-Sept-2021\]

\- Polyglot data modeling: added the possibility to convert any physical target model into a technology-agnostic data model, and derive a physical target model - for any target - from a polyglot data model.&nbsp; More info at https://hackolade.com/polyglot-data-modeling.html

\- Model Compare and Merge: added the possibility in the merge process to generate a delta model (similar to the CLI compMod deltamodel output)

\- Collibra: added batch synchronization for large models

\- Collibra: added possibility to fetch domains for an individual community, resulting in higher performance in large organization

\- JSON Schema: adjusted conversion of samples into examples when switching from one draft version to another

\- JSON Schema: adjusted conversion of exclusiveMin/Max when switching from one draft version to another

\- Cassandra and ScyllaDB: adjusted mapping of mapping of complex types when reverse-engineering CQL files

\- OpenAPI: adjusted display of Swagger UI interaction

\- all RDMBS targets: added support for Alternate Keys (MariaDB, Redshift, Snowflake, SQL Server, Synapse)

&nbsp;

New features in v5.1.8 \[10-Sept-2021\]

\- Object Browser: added possibility to alpha sort entities and views via contextual menu

\- Command-Line Interface: added possibility to open Model Compare \& Merge in GUI from command line with --gui=true argument

\- Custom properties multi-select dropdown: added tooltip display

\- Custom properties dependency structure: added possibility to use an array of values in place of more convoluted "or" syntax

\- Custom properties: added "requiredProperty" for display of a red star next to label

\- DDL reverse-engineering: added support for views based on tables with aliases, select statements with wildcard, and unsupported references&nbsp;

\- Delta Lake: refactored reverse-engineering for higher performance by batching Scala commands

&nbsp;

New features in v5.1.7 \[04-Sept-2021\]

\- BigQuery: added support with a new plugin with full support for forward-engineering of DDL scripts, and reverse-engineering

\- Command-Line Interface compMod command: added argument --mergeDeletesasDeactivated to deactivate merged object instead of deleting it

\- Custom properties fieldList control: added tooltip display

\- Model Compare \& Merge: added options for flexible selection in case of multiple data types

\- JSON Schema preview and forward-engineering: added use of technical names and dot.notation in nested objects&nbsp;

\- Hive: added read-on "view on" property to display multiple referenced tables

\- Mongoose reverse-engineering: added support for Map data type

&nbsp;

New features in v5.1.6 \[27-Aug-2021\]

\- Compare and Merge: added viewing of index differences, and other properties pane tabs

\- Added validation of file path and name input in model compare and API model template selection dialogs

\- XSD import for RDDBMS targets: use maxLength as char column length

\- Hive: added reverse-engineering of view columns with CAST function

\- Hive: added support for view columns with aliases

\- Synapse: implemented Azure Active Directory authentication with MFA

&nbsp;

New features in v5.1.5 \[20-Aug-2021\]

\- Excel: added import of views

\- XSD reverse-engineering: added conversion of keys with "XAK" prefix into unique keys for migration of models from erwin

\- Documentation: added handling of block controls inside group controls

\- MarkLogic: added collection name matcher option in reverse-engineering connection parameters

\- Synapse: added MFA support to the Active Directory authentication method

&nbsp;

New features in v5.1.4 \[16-Aug-2021\]

\- Tech refresh of Electron (v13.1.9), NodeJS (v14.17.0), Chromium (v91), React (v17), and Electron-related modules

\- XSD reverse-engineering: added support for import of \<xs:keyref\> into relationships, plus additional fine-tuning

\- Fixed unexpected closing of DDL worker on Mac

\- MarkLogic: added use of global query timeout, plus enhanced getting collection list if specified

\- Azure SQL: added login with email-like username

\- Synapse: added login with email-like username, plus added Azure Active Directory authentication method

&nbsp;

New features in v5.1.3 \[10-Aug-2021\]

\- Colors: added color picker on properties pane options tab for containers, entities, and views

\- Font style: added controls for italic and bold font for container, entity, attributes and views

\- Excel: added export/import of color hex codes and font styles for bulk edit or conditional formatting

\- Excel: improved error information to help troubleshooting when parent structure is missing in import of complex objects

\- Save As Obfuscated: added custom properties to process

\- Indexes: where applicable, added possibility to deactivate index so it does not appear in scripts or gets commented out, if possible: ArangoDB, Cassandra, Cosmos DB (Core SQL, Gremlin, and Mongo APIs), Couchbase, DynamoDB, Hive, JanusGraph, MariaDB, MarkLogic, MongoDB, Neo4j, ScyllaDB, SQL Server, Synapse, TinkerPop

&nbsp;

New features in v5.1.2 \[30-Jul-2021\]

\- Colors: added possibility to change color of attributes in ER Diagram and Object Browser

\- Added option in Tools \> Options \> Forward-engineering to disable structured path for JSON documents and JSON Schema

\- Added a warning dialog to enable lineage capture if reverse-engineering of DDL is for migration from RDBMS

\- Schema inference during reverse-engineering of JSON documents and databases: supplemented detection of pattern fields when using ID-like keys

\- Model API: greyed out deactivated entities in object selection dialog

\- Command-Line Interface: added forwEng arguments to allow publication of Avro and JSON Schemeleca to schema registries (Confluent, Pulsar, Azure for Event Hubs)

\- Collibra: added publishing via Command-Line Interface to Data Dictionary

\- Collibra: added warning when not all entities are selected for synchronization

\- Collibra: enabled publishing of schema definitions of EventBridge, OpenAPI, and Swagger

\- Pulsar: added ability to forward-engineer schemas via Command-Line Interface

&nbsp;

New features in v5.1.1 \[23-Jul-2021\]

\- Model compare and Merge: added indeterminate state for partial uncheck of checkbox (now tri-state)

\- Model compare and Merge: adjusted trim of long path model names, plus added tooltip

\- Improved rendering of large ERD models

\- Collibra: added forward-engineering of foreign keys in subschemas

\- Pulsar: added Command-Line Interface reverse-engineering

\- SQL Server/Azure SQL: added support for forward-engineering of combined schemas,&nbsp; and of all schemas into a single file

&nbsp;

New features in v5.1.0 \[17-Jul-2021\]

\- Collibra Data Dictionary integration.&nbsp; Requires specific license option.&nbsp; See more info at https://hackolade.com/help/CollibraDataDictionaryintegratio.html

\- Docker containers: for the purpose of running the Command-Line Interface in CI/CD pipelines. &nbsp; Requires concurrent license key.&nbsp; See full instructions at https://github.com/hackolade/docker/tree/main/Studio

\- Pulsar Schema Registry: added ability to forward- and reverse-engineer Avro and JSON Schema

\- Lineage capture: added container information to attribute lineage for reverse-engineering, Excel import, etc.

\- Custom properties: added defaultValue in configuration controls

\- DynamoDB: added logic to update table if it already exists when applying to instance

&nbsp;

New features in v5.0.8 \[09-Jul-2021\]

\- ERD drag-and-drop: enhanced tolerance for dropping into an empty entity for both move (drag-and-drop) and copy (Ctrl+drag-and-drop)

\- DynamoDB: added ability to apply forward-engineering scripts to instance

\- DynamoDB: added support for single-table storage, using views (a.k.a. facets in NoSQL Workbench.)&nbsp; These views cannot be forward-engineered to DynamoDB, or derived through reverse-engineering, as the concept does not exist.&nbsp; It however makes it easy to visualize and document access patterns

\- MongoDB: added read-only view pipeline edition after reverse-engineering from DDL

&nbsp;

New features in v5.0.7 \[02-Jul-2021\]

\- DynamoDB: added support for table groups

\- Postgres DDL reverse-engineering: added handling for ONLY keyword in ALTER TABLE statements

\- Cosmos DB-Gremlin: reverse-engineering of nested objects in JSON and JSON Schema now results in their normalization, given that the database does not support complex data types

\- Delta Lake on Databricks: modified message when cluster is unavailable

\- Neptune-Gremlin: reverse-engineering of nested objects in JSON and JSON Schema now results in their normalization, given that the database does not support complex data types

\- OpenAPI/Swagger/EventBridge: added tolerance for lines commented with # during-reverse-engineering

\- OpenAPI/EventBridge: removed empty requestBody for GET and DELETE requests during forward-engineering

&nbsp;

New features in v5.0.6 \[25-Jun-2021\]

\- Avro: added namespace property "Schema group name" for Azure Schema Registry

\- Azure Schema Registry for Avro: added ability to fetch Schema Groups&nbsp;

\- Cassandra DataStax: removed WITH OPTIONS when creating SAI indexes if options are empty

\- Cassandra DataStax on Astra: disabled possibility to define search indexes which are not currently supported by Astra

\- Cassandra DataStax: added possibility to reverse-engineer custom and search indexes from .cql files

\- MongoDB: maintain field order in index creation script for deactivated fields

&nbsp;

New features in v5.0.5 \[18-Jun-2021\]

\- ERD drag-and-drop: added possibility to drop into an empty entity or an empty complex attribute (object or array)

\- Lineage capture: added container level information to event tracing

\- Azure Schema Registry: added possibility to reverse-engineer schemas created via Azure portal console

\- Avro: added validator in model level script tab prior to applying to schema registries

\- Cosmos DB Gremlin: improved error message when specified endpoint is incorrect during forward-engineering to instance

\- MariaDB: implemented possibility to apply DDL script to instance

\- SQL targets: re-ordered DDL scripts to ensure that Foreign Key creations relate to previously created tables

\- Snowflake: added possibility to select combined vs individual schemas from Tools \> Forward-Engineering and Command-Line Interface

&nbsp;

New features in v5.0.4 \[11-Jun-2021\]

\- Neptune with Gremlin API: added support with new plugin, including forward-engineering of schema and sample graph via Gremlin script, plus traditional reverse-engineering

\- ERD: added handle to drag-and-drop attributes (can be hidden with Display Options toolbar icon of View menu).&nbsp; Use ctrl+mouse click to move or copy multiple attributes

\- Tools \> Options \> Naming Conventions: added ability to refresh CSV abbreviation file without necessity to restart the application

\- Toolbar: grouped various display options under a new icon

\- View menu: grouped display options

\- MongoDB: removed filter for inclusion in JSON Schema full/extended of properties from properties tabs: users, indexes, sharding

\- Cassandra/ScyllaDB: removed filter for inclusion in JSON Schema full/extended of properties from properties tab secondary indexes

\- Cassandra on Astra: added possibility for token-based authorization

\- Snowflake: added possibility to forward-engineer all schemas so as to allow foreign keys across multiple schemas

&nbsp;

New features in v5.0.3 \[07-Jun-2021\]

\- Avro: added ability to forward- and reverse-engineer with Azure Schema Registry for EventHub

\- JanusGraph: added support with new plugin, including forward-engineering of schema and sample graph via Gremlin script, plus traditional reverse-engineering

\- Lineage: added tracking of Foreign Key relationships during denormalization

\- Cassandra: added filtering of invalid clustering keys during forward-engineering

\- Delta Lake: added retrieval of table BLOOMFILTER INDEX options and NOT NULL columns during reverse-engineering

\- JSON Schema draft conversion of Sample property in draft-04 to Examples in older drafts, and vice-versa

\- MongoDB pipeline views: use technical names when present

&nbsp;

New features in v5.0.2 \[28-May-2021\]

\- Compare and merge models: adjusted sizing of dialog with high-resolution screens

\- Added option "Start a New Application Instance" from the File menu

\- Properties Pane: added automatic scroll to focus on relationship selected in Object Browser

\- Reverse-engineering of DDLs and XSDs: no longer overwriting the model name after first file

\- Couchbase: adjust reverse-engineering of indexes with special characters in passwords

\- Couchbase: fine-tuned sampling query for Enterprise Edition instances with large buckets

\- Delta Lake: adjusted document sampling

\- Delta Lake: added forward-engineering of CREATE BLOOMFILTER INDEX statement to instance&nbsp;

\- Glue Data Catalog: added possibility to reverse-engineer from .hql files

\- MariaDB: added reverse-engineering of unique and primary options from DDL file

&nbsp;

New features in v5.0.1 \[21-May-2021\]

\- Delta Lake on Databricks: added support with a new plugin (compatible with Azure Databricks, Databricks on AWS, and on Google Cloud), with full support for forward-engineering of HiveQL scripts, and reverse-engineering including inference of JSON in longtext

\- ERD and schema hierarchical view: added toolbar button to toggle between technical and business names; added documentation control and CLI genDoc command argument&nbsp;

\- ERD zoom in: function now takes center of display instead of top left of canvas as reference for zoom operation, whether from toolbar button or ctrl+mouse wheel

\- Forward-Engineering of sample document, schema or script: added Toots \> Options \> FE parameter to skip folder when container level is undefined

\- Reverse-Engineering object picker dialog: added horizontal scrollbar for long file structures and names in cloud storage

\- Reverse-Engineering object picker dialog: added support for periods in file names

\- DDL reverse-engineering: added support for comment constraints on foreign key relationships (PostgreSQL and Redshift only, as not supported in other dialects)

\- Model Compare and Merge: added auto-selecting/deselecting child objects when their parent has added/deleted difference type

\- Cosmos DB (SQL API, and Gremlin API): added support for serverless instances

\- Redshift: added optional sessionToken connection

&nbsp;

New features in v5.0.0 \[15-May-2021\]

\- Full support for features of JSON Schema specifications draft-06, draft-07 and 2019-09, in addition of draft-04 upon which Hackolade was originally built

\- JSON: added reverse-engineering from cloud storage: Amazon S3, Azure Blob Storage, Google Cloud Storage

\- JSON: added support for forward- and reverse-engineering with Confluent Schema Schema Registry

\- Compare and Merge Models: added 2 distinct views: the compare view with 2 side-by-side panes, and the merge view which displays 3 panes including a merged model pane in between the left- and right-hand models

