# v4.x

New features in v4.3.22 \[21-May-2021\]

\- Reverse-Engineering object picker dialog: added horizontal scrollbar for long file structures and names in cloud storage

\- Reverse-Engineering object picker dialog: added support for periods in file names

\- DDL reverse-engineering: added support for comment constraints on foreign key relationships (PostgreSQL and Redshift only, as not supported in other dialects)

\- Confluent Schema Registry reverse-engineering: added conflict resolution dialog

\- Cloud storage reverse-engineering of JSON documents: added possibility to combine schemas

\- JSON Schema reverse-engineering: added tolerance for illegal trailing commas

&nbsp;

New features in v4.3.21 \[14-May-2021\]

\- References: added possibility to reference internal definitions of external models and JSON Schema

\- Cassandra/ScyllaDB: added handling of table option identifier values and comments in reverse-engineering of .cql files

\- Amazon Web Services: added optional sessionToken connection for AWS data sources (DynamoDB, Glue Data Catalog, EventBridge Schema Registry, S3 for Avro and Parquet)

&nbsp;

New features in v4.3.20 \[07-May-2021\]

\- Confluent Schema Registry: added support for Subject Name Strategy choices, and schema type -key/-value

\- Confluent Schema Registry: extended possibility to fetch more than 100 subjects

\- MariaDB: sample rows during reverse-engineering only if table is suspected to contain JSON in LONGTEXT column(s)

\- OpenAPI: added ability to export components.schemas to JSON Schema&nbsp;

\- Swagger: added ability to export definitions to JSON Schema&nbsp;

\- Snowflake: sample rows during reverse-engineering only if table is suspected to contain JSON in VARIANT column(s)

\- SQL Server/Azure SQL: sample rows during reverse-engineering only if table is suspected to contain JSON in (N)VARCHAR(4000) column(s)

\- Synapse: awareness of serverless SQL pool and its restrictions

\- Synapse: sample rows during reverse-engineering only if table is suspected to contain JSON in (N)VARCHAR(4000) column(s)

&nbsp;

New features in v4.3.19 \[30-Apr-2021\]

\- ER diagram views: enabled functionality in Personal Edition

\- Plugin Manager: display all available plugins, even if upgrade of core application is required for compatibility

\- Internal definitions: added handling of dependencies in JSON Schema reverse-engineering

\- JSON Schema forward- and reverse-engineering: modified handling to leverage file name as technical name, and Title keyword as business name, if different.

\- JSON Schema: added handling of choices in array items

\- JSON Schema reverse-engineering: better detection of invalid JSON Schema, including invalid references

\- XSD reverse-engineering: fixed handling of minItems/maxItems

\- DynamoDB: relaxed logic to create sort key in secondary indexes

\- MongoDB: added handling of multikey index in forward- and reverse-engineering

&nbsp;

New features in v4.3.18 \[26-Apr-2021\]

\- MariaDB: added support with a new plugin, with full support for forward-engineering of DDL, and reverse-engineering including inference of JSON in longtext

\- Added icon in title of ERD entities so users can open in new tab with just one click

\- Avro with Confluent Schema Registry: added possibility to fetch and select specific version of a schema subject

\- Avro with Confluent Schema Registry: added possibility to minify schema to be applied via API

\- Hive: improved retrieval of views schema and SELECT AS statement

&nbsp;

New features in v4.3.17 \[16-Apr-2021\]

\- Avro: added support for SSL in reverse-engineering connection to Confluent Schema Registry

\- Avro: added forward-engineering to Confluent Schema Registry

\- Avro: combined doc and description properties

&nbsp;

New features in v4.3.16 \[09-Apr-2021\]

\- Find/replace: added possibility to search into properties of model objects.&nbsp; Requires to choose "properties" instead of "all objects"

\- Avro: added reverse-engineering of schemas on Confluent Schema Registry cloud or on-premises

\- Cassandra/ScyllaDB: enhanced display of columns data types when containing JSON documents

\- Cassandra/ScyllaDB: disabled check of naming restrictions for JSON fields

\- Hive forward-engineering: added handling of special characters in HiveQL script

\- Hive reverse-engineering: added handling of boolean types plus select statements of views.

&nbsp;

New features in v4.3.15 \[02-Apr-2021\]

\- Find/replace: added logic to detect if Object Browser is closed

\- Couchbase: added reverse-engineering of index information from a .n1ql file

\- Cassandra/ScyllaDB: allowed truststore only jks connection

\- Hive: adjusted reverse-engineering of views

\- YAML: added forward- and reverse-engineering of YAML Schema https://asdf-standard.readthedocs.io/en/1.5.0/schemas/yaml\_schema.html

&nbsp;

New features in v4.3.14 \[26-Mar-2021\]

\- YAML: added support for reverse-engineering of YAML files into any target, and inferring the corresponding JSON Schema

\- YAML: added Command-Line Interface command revEngYaml for automated reverse-engineering of YAML files&nbsp;

\- YAML: added possibility to forward-engineer data sample in YAML document format.&nbsp; Also available from the Command-Line Interface

\- External definitions: added dialog to confirm user's choice of whether or not to update references when opening model&nbsp;

\- Model API generation: added handling of custom properties from source model, provided that keywords match

\- Using the mouse wheel in both the ER Diagram and the hierarchical schema view:

\-- up/down: move up or down

\-- shift+up/down: move left or right

\-- ctrl+up/down: zoom in or zoom out

\- Cassandra/ScyllaDB: added SSH tunnel connection for cloud instances

\- Cassandra/ScyllaDB: now using consistency level when retrying connection and applying to instance

&nbsp;

New features in v4.3.13 \[19-Mar-2021\]

\- Added warning when opening a model if Naming Conventions file cannot be found

\- Renamed dbVendor from "Plain JSON--no DB" to "JSON"

\- Added $jsonschema format to MongoDB script, in GUI and CLI

\- MongoDB: update connection library, and enhanced srv string parsing

\- Redshift: renamed function properties keywords

\- SQL Server: updated drivers

&nbsp;

New features in v4.3.12 \[12-Mar-2021\]

\- Redshift: added support with a new plugin

\- Custom structure of model file name when saving: added \<dbVendor\> keyword

\- JSON Data preview and forward-engineering in case of choice (oneOf,...): except if NULL, the first subschema is always selected for the sample data

\- JSON Schema forward-engineering: added possibility to generate JSON Schema for model definitions

\- Cosmos DB with MongoDB API: added Control Pane tab in connection settings, added 3.6 protocol; added index creation; added possibility to commit sample documents to Azure instance as well as index definitions

\- Swagger/OpenAPI/EventBridge: added title property at the attribute level

\- Plain JSON target: deprecated RESTful API properties, as Swagger/OpenAPI are much more appropriate

&nbsp;

New features in v4.3.10 \[05-Mar-2021\]

\- Lineage: added possibility to enable lineage capture of model operations, including reverse-engineering from various sources, denormalization, API generation, references, copy/paste/duplicate

\- Tools \> Options \> General: added ability to specify the structure of model file names, using any combination and order of keywords: \<modelName\>, \<target\>, \<version\>, and \<author\>, plus fixed characters, e.g. "\<modelName\>-\<target\> \<version\>" or "\<target\> model \<modelName\>", etc.

\- Added ability to define Foreign Key relationship name and cardinality from the child attribute's properties pane

\- Cassandra/ScyllaDB: added analyzing of jks files, plus option to disable strict SSL

&nbsp;

New features in v4.3.9 \[26-Feb-2021\]

\- Tech refresh of Electron (v11.3.0), NodeJS (v12.18.3), Chromium (v87), and Electron-related modules, including support for Apple M1 chips

\- Command-Line Interface revEng command: deprecated --file argument and consolidated into --files which allows multiple

\- Cassandra/ScyllaDB: added truststore input parameters for Java keystore authentication

\- Hive: added reverse-engineering of HQL file

\- Snowflake: added full names for tables, and IF NOT EXISTS to DDL statements

&nbsp;

New features in v4.3.8 \[19-Feb-2021\]

\- JSON Schema: step 2 of extending support for draft-06, draft-07, and 2019-09 specs: reverse-engineering of new drafts. Still without support for additional functionality, i.e. conditional validations and other new keywords are currently ignored.

\- Reverse-engineering: added query request timeout parameter in Tools \> Options, and enabled for MongoDB, Couchbase, and DynamoDB.&nbsp; More targets coming progressively

\- Command-Line Interface forward-engineering: added choice of output format for MongoDB ("shell", "mongoose","js") and Couchbase ("ottoman", "n1ql")

\- MongoDB reverse-engineering: added handling of partialFilterExpression in indexes

\- MongoDB forward-engineering: added ability to generate JavaScript

\- MongoDB forward-engineering: added ability to optionally include JSON data document samples in apply to instance

\- MongoDB forward-engineering: fetch document size and total index size, then export report to CSV for sizing exercise

\- MongoDB forward-engineering to Mongoose schema: added date.now as default value for date data type

&nbsp;

New features in v4.3.7 \[12-Feb-2021\]

\- Enhanced email template in case of uncaught error so more details are provided

\- Reduced ambiguity in cardinality crows feet between 0...1 and 0..n

\- Activated plugin cache by default to speed up application startup in case of many plugins.&nbsp; Can be cleared in Tools \> Options \> General

\- Added possibility to collapse block properties

\- JSON Schema reverse-engineering with external references: added warning of no current support

\- JSON Schema: first step of extending support for draft-06, draft-07, and 2019-09 specs: forward-engineering without additional functionality.&nbsp; More steps to progressively appear in upcoming releases...

\- Connection settings: added possibility to export and import with .json files or encrypted binary files.&nbsp; Can be used to exchange with colleagues

\- Command-Line Interface: added possibility to reference a connection settings file

\- Avro reverse-engineering of JSON Schema: remove choice if there is only one record at the root level

\- Avro: added logicalType decorator in ERD and Object Browser

\- Cassandra/ScyllaDB: improved RetryPolicy and reverse-engineering logging

&nbsp;

New features in v4.3.6 \[05-Feb-2021\]

\- Added pattern field indicator (#) with tooltip in ERD and Object Browser

\- ER Diagram Views: added containers and entities in Object Browser under each respective ERDV

\- ER Diagram Views: selection with container picker is now specific to each ERDV; orthogonal distribution after creation; membership for Swagger/OpenAPI

\- Excel export/import: added disambiguation of primary key vs composite primary key for RDBMS plugins

\- Cassandra/ScyllaDB: added handling for composite clustering keys in reverse-engineering of .cql script file

\- Cassandra/ScyllaDB: removed SELECT COUNT(\*) from reverse-engineering absolute sampling, and added LIMIT for COUNT(\*) of relative&nbsp;

\- Hive: add use of krb5 library to retrieve Kerberos token using keytab in HTTP mode (Windows)

\- Snowflake: added support for case-sensitive quoted names, plus minor SQL adjustments in forward-engineering

&nbsp;

New features in v4.3.5 \[29-Jan-2021\]

\- Reverse-engineering from DB instances into existing model: added conflict resolution dialog letting user decide between keep both, replace, merge, or cancel

\- Command-Line Interface: added conflict resolution to revEng command

\- Apply script to Couchbase instance: added tolerance for existing documents and indexes

\- Avro: added handling of definitions in array items

\- Avro: added handling of JSON Schema pattern properties

\- Print Diagram: fixed empty preview for large models with PNG output

\- JSON Schema reverse-engineering: added handling of internal definition identical to existing external definition in model

&nbsp;

New features in v4.3.4 \[22-Jan-2021\]

\- Reverse-Engineering from JSON Schema, JSON documents, DDL, XSD: optionally designate the destination container for the entities.&nbsp; This will overwrite the entity name in the source file, if any.&nbsp; Available both in GUI and in CLI.

\- Couchbase: added support for primary and secondary indexes

\- Couchbase: added script tab in N1QL syntax with forward-engineering by example with sample documents by document type, plus indexes&nbsp;

\- Couchbase: added ability to apply forward-engineering script to instance

\- Cosmos DB with Gremlin API: added split pane display of Gremlin and CosmoS DB scripts

\- MarkLogic: added handling of indexes, in the Properties Pane, reverse-engineering, forward-engineering and apply to instance

\- Mongoose: added support for populate() foreign key relationships and references to include user-defined modules

\- ScyllaDB: enabled composite relationships

\- ScyllaDB: added reverse-engineering from CQL files

&nbsp;

New features in v4.3.3 \[15-Jan-2021\]

\- Object Browser: added a "Find in files" tab to search other Hackolade models of the same target

\- Forward-Engineering to JSON Schema: previously 2 modes were available: referenced or resolved definitions.&nbsp; A 3rd mode is introduced to convert external and model references into internal definitions

\- Command-Line Interface: added --performance argument to create log of timestamps to identify potential bottlenecks in application startup steps

\- XSD reverse-engineering: added support for conversion of xs:decimal with precision and scale to proper subtype in Avro

\- Avro: added non-required properties conversion to multiple with null as default when reverse-engineering from JSON Schema

\- Cosmos DB Gremlin: enhanced support of indexes via Properties Pane, plus forward-engineering of indexing script

\- Cosmos DB Gremlin: added button to apply to Azure instance the script to create graphs, nodes and edges, indexes, UDFs, stored procedures, and triggers

\- MongoDB: added button to apply to instance the script to create databases, collections with optional $jsonschema validator, indexes, and sharding configuration

&nbsp;

New features in v4.3.2 \[08-Jan-2021\]

\- Added ER Diagram Views: a subset of entities selected from the main ER diagram, to help manage large models by focusing on a smaller set of entities, by domain or subject.&nbsp; Entities may appear in multiple Diagram Views.&nbsp; Modifications made inside Diagram Views are immediately reflected in the main diagram and other views where present.&nbsp;

\- MongoDB reverse-engineering: added possibility to define sampling with a specific aggregation pipeline query

\- MongoDB: added a forward-engineering script tab at model level

\- Hive: added support for (materialized) views in Hive 3, and workload management entities

\- Cosmos DB with SQL API:forward-engineering of document by example

\- Cosmos DB with SQL API: apply to Azure instance the script to create containers, documents, indexes, UDFs, stored procedures, and triggers

&nbsp;

New features in v4.3.1 \[22-Dec-2020\]

\- Elasticsearch: new plugin for typeless indices in v7 and above

\- Added optional dark theme, set in Tools \> Options \> General \> Appearance

\- Added possibility to open models from OS, Confluence, etc... if default app for .json file extension is associated with Hackolade, using "Open with... Hackolade" from Windows Explorer or Mac Finder

\- Cosmos DB with SQL API: enhanced support of indexes via Properties Pane, plus forward-engineering of indexing script

\- MarkLogic: added preservation of field order during reverse-engineering

\- MongoDB and Cosmos DB with MongoDB API: disabled timestamp data type which is an internal data type

&nbsp;

New features in v4.3.0 \[11-Dec-2020\]

\- Reduced footprint of saved models by removing extraneous falsy values (*“false”*, empty *string "",* empty *array* and *object*)

\- Added detection of ISO 8601 date/time/timestamp/duration in JSON strings during reverse-engineering of database instances for MongoDB, Cosmos DB with MongoDB API, and Elasticsearch

\- DDL reverse-engineering: added conflict management dialog: choice of keep both (as previously) / replace / merge / cancel

\- Unsaved model backup: added support for multiple application instances

\- SQL Server and Azure SQL: added Azure Active Directory authentication

&nbsp;

New features in v4.2.15 \[04-Dec-2020\]

\- Suppressed extraneous message about unsaved model when opening multiple instances of application

\- Added last used file list in external definition dialog

\- Added warning sign in the title of ERD object when a container or an entity is deactivated

\- AWS services (S3 for Avro and Parquet, DynamoDB, EventBridge, Glue): added proxy cache clearing in case of CA SSL inspection

&nbsp;

New features in v4.2.14 \[01-Dec-2020\]

\- Increased logging for MongoDB SSH connections

\- Cassandra: added ability to reverse-engineer from a CQL script file

\- MarkLogic: added forward-engineering JSON Schema for validation and applying to schemas database instance

&nbsp;

New features in v4.2.13 \[28-Nov-2020\]

\- MongoDB: added optional detection of Foreign Key relationships during reverse-engineering

\- Cassandra: added ability to define composite foreign key relationships (for documentation purposes only, as not enforced by DB)

\- MarkLogic: added reverse-engineering by sampling documents in collection (or directories) followed by probabilistic schema inference

\- Graph plugins: added ability for subnodes to have multiple parents

\- Added automatic reverse engineering when just opening Swagger/OpenAPI files

&nbsp;

New features in v4.2.12 \[20-Nov-2020\]

\- Added automatic creation of second subschema when creating Choices

\- Added ability to save an obfuscated version of model from the File menu

\- Added .cer to list of file extensions for Certificate Authority selection dialog

\- API model generation: added mapping of sample property to Swagger/OpenAPI example property

\- Naming Conventions: added UPPER\_SNAKE and Snake\_Title case conversions to Business-to-Technical&nbsp;

\- Command-Line Interface: added revEngXSD command

\- XSD: added reverse-engineering of model and entity comments

\- XSD: added reverse-engineering of totalDigits and fractionDigits

\- SQL Server: added numeric data type descriptors for XSD reverse-engineering

\- Snowflake: added numeric data type descriptors for XSD reverse-engineering

\- Synapse: added numeric data type descriptors for XSD reverse-engineering

&nbsp;

New features in v4.2.11 \[13-Nov-2020\]

\- Suggest denormalization: added selection limitation to 2 entities per operation

\- Plugin Manager: added support for GitHub's replacement of master branch by main branch

\- Excel export/import: added support for custom properties in separate tabs

\- Cosmos DB Gremlin: added possibility to apply Gremlin script to Azure instance

\- MongoDB: added restrictions on creation of relationships for data types: null, boolean, binary, JavaScript, JS with scope, symbol, minKey, maxKey

\- All AWS plugins (S3 for Avro and Parquet, DynamoDB, EventBridge, Glue): added support for SSL Inspection in Reverse-Engineering protocol

\- Avro: added record-level doc to forward-engineering script and made script cosmetic changes for appearance of doc info

&nbsp;

New features in v4.2.10 \[06-Nov-2020\]

\- Added support for property graph Cosmos DB w/ Gremlin API&nbsp;

\- More forgiving mouse movements in sub options of contextual menus

\- Graph plugins (ArangoDB, Cosmos DB w/ Gremlin API, Neo4j, TinkerPop): added support for subclasses of nodes/vertices, for documentation only

\- Licensing: relaxed restrictions of Remote Desktop sessions to allow multiple domain logins when free seats are available

\- XSD reverse-engineering: added mapping of xs:date, time, and dateTime data types to corresponding target data types when available

\- MongoDB: added default JSON sample for BSON data types: binary, JavaScript, JS with scope, symbol, minKey and maxKey

&nbsp;

New features in v4.2.9 \[30-Oct-2020\]

\- Object Browser: scroll to last selected object when clearing search

\- Added validation to all file choosers in Tools \> Options

\- Network proxy settings: fixed environment variable option for Windows

\- Avro and Parquet: set AWS S3 as default connection type in cloud settings

\- Glue Data Catalog: added commenting in HiveQL script of foreign key constraint if underlying column is commented

\- Hive: added commenting of foreign key constraint in HQL script if underlying column is commented

\- Neo4j: added commenting of deactivated objects in Cypher script

\- SQL Server: added commenting of deactivated objects in DDL

\- Synapse: added commenting of deactivated objects in DDL

&nbsp;

New features in v4.2.8 \[27-Oct-2020\]

\- Plugin Manager: on update, takes into account custom properties additional tabs for customization migration

\- Network proxy: refactored Electron proxy settings plus fixed cloud/DynamoDB connection

\- Documentation: added warning if custom logo file does not exist

&nbsp;

New features in v4.2.7 \[23-Oct-2020\]

\- Added possibility to select nested attributes in internal and model definitions

\- Network proxy: added possibility to pick settings from HTTPS\_PROXY environment variables

\- Network proxy on Windows: added possibility to pick settings from Registry

\- Fixed converting internal JSON Schema definitions during Reverse-Engineering into OpenAPI model

\- Fixed generating default in DDLs when value is 0

\- Cassandra: added possibility for multiple select of columns for PK or CK

\- EventBridge Schema Registry: when reverse-engineering from JSON Schema, convert NULL data type to nullable property

\- Glue Data Catalog: added commenting of deactivated objects in HiveQL script

\- Neo4j: added tolerance for relationships without properties

\- ScyllaDB: added commenting of deactivated objects in CQL script

\- Snowflake: added commenting of deactivated objects in DDL

\- Synapse: restricted possibility to add Unique Key constraint if column already has a PK

\- Synapse: restricted possibility to add Primary Key constraint if table is marked for clustered indexes

\- Synapse: dropped PK check when adding foreign key relationships, as they are not enforced by DB

&nbsp;

New features in v4.2.6 \[16-Oct-2020\]

\- Markdown documentation generation: fine-tuning plus naming of images directory and overwrite behavior

\- Markdown: enabled feature in Command-Line Interface

\- Fix for documentation custom logo

\- Model-Driven API generation: convert NULL data type to nullable property

\- Swagger and OpenAPI 3.0.x: when reverse-engineering from JSON Schema, convert NULL data type to nullable property

\- Swagger/OpenAPI: added support for technical-to-business naming conventions with abbreviations file

\- Custom properties: allowed new tab at model level

\- ERD multiple select: added possibility to select annotation boxes

\- Referenced definitions: added support for pattern fields

\- Pattern fields: fixed resolution of referenced definitions in JSON Schema preview

&nbsp;

New features in v4.2.5 \[09-Oct-2020\]

\- Added documentation generation in Markdown format

\- Added a warning for dangling relationships in Object Browser and Properties Pane

\- Added propagation of Required property for external definitions

\- Excel import: added tolerance for dangling relationships

\- JSON Schema preview: added isActivated and refDescription properties to full/extended modes

\- JSON Schema reverse-engineering: added handling for internal references inside definitions

\- XSD reverse-engineering: added handling of custom namespaces

\- Neo4j and other graph plugins: added handling of long node label names

\- Swagger/OpenAPI: added dropdown to root hierarchical schema view tab to select request method or response code instead of text input

&nbsp;

New features in v4.2.4 \[03-Oct-2020\]

\- Pattern field detection: added parameter to control whether to combine similar patterns

\- Custom properties: added support for separate custom tab at attribute level for all data types

\- DDL reverse-engineering: added support for Teradata DDLs

\- JSON Schema: added support for JSON Schema definitions, when performing reverse-engineering as model definitions

\- XSD reverse-engineering: added handling for custom-defined types with multiple complexTypes

\- Fixed OpenAPI missing description when exporting to Excel

\- Disabled reserved words validation for Couchbase key

&nbsp;

New features in v4.2.3 \[25-Sept-2020\]

\- Pattern field recognition enhancements during schema inference of reverse-engineering: Levenshtein distance https://en.wikipedia.org/wiki/Levenshtein\_distance is used to measure name similarity of successive complex data types with identical structure.&nbsp; Levenshtein distance parameter can be changed in Tools \> Options \> Reverse-Engineering (default = 1)

\- JSON Preview of JSON Schema: added filtering of deactivated attributes for full and extended versions

\- Attribute name validation: enhanced handling in case of Naming Conventions; harmonized notification across Object Browser, ERD, and hierarchical schema view; plus added tootips to warning signs

\- Added meaningful title in email subject of uncaught exceptions

\- Added handling of Naming Conventions in Dependencies property

\- Sample JSON data: included complex attributes -- even if empty

\- Excel template import: added tolerance for Unicode character expressions

\- Cassandra: added commenting of deactivated objects in CQL script

&nbsp;

New features in v4.2.2 \[18-Sept-2020\]

\- Multiple scalar data types: added up/down control to change order of data types

\- JSON Preview of data sample and standard JSON Schema: added filtering of deactivated attributes

\- Excel import: added handling of absent parent or child in relationships

\- Model API generation: added handling of naming conventions

\- Hive: added commenting of deactivated objects in HiveQL script, if version allows (not Hive v1)

\- Swagger/OpenAPI: added possibility of external references to other Hackolade models and JSON Schemas

\- Swagger/OpenAPI: added commenting of deactivated parameters and schema attributes

&nbsp;

New features in v4.2.1 \[10-Sept-2020\]

\- API Model: added command-line interface command forwEngAPI

\- API Model: now possible also for views (when supported by target) and relationships/edges (for graph targets)

\- Naming Conventions when Business-to-Technical conversion is enabled : now prompting user for choice of importing source attribute names into business name or technical name

\- Command-Line Interface: added JSON Schema compliance argument (standard, full, or extended) to forwEng command

\- Added isActivated property to all objects (containers, entities, and attributes), ON by default.&nbsp; If unchecked,&nbsp; forward-engineered objects are commented (if the target script syntax allows it) or filtered.&nbsp; Currently only native targets, plus Hive have this functionality enabled.&nbsp; Other targets to follow with plugin update.

\- Added warning for attributes with duplicate name

\- Avro and Parquet: added Azure Data Lake (ADLS Gen2) as a Cloud source for reverse-engineering

&nbsp;

New features in v4.2.0 \[29-Aug-2020\]

\- Ability to generate a Swagger or OpenAPI model and documentation file from any target model, by merging with a template controlling API content.&nbsp; Available in Tools \> Forward-Engineering \> API Model.&nbsp; More info at [https://hackolade.com/help/APIModel.html](<https://hackolade.com/help/APIModel.html> "target=\"\_blank\"")

\- Added multi-select Shift+click for contiguous selection from/to in index key and reference selection dialogs

&nbsp;

New features in v4.1.15 \[25-Aug-2020\]

\- Excel import: allowed import of multiple data types without id or empty properties

\- Index key: allowed multiple selection

\- External definitions using relative path: allowed different drive than default path

\- Definitions (all): added toggle for case sensitive search

\- Naming conventions: fixed issue with digits after letter

\- DynamoDB: added null data type

\- MongoDB: updated driver

&nbsp;

New features in v4.1.14 \[14-Aug-2020\]

\- References to external definitions: allowed chaining of external definitions

\- References: added read-only mode for descriptions of definitions

\- Selection of index keys: allowed multiple selection of keys

\- DynamoDB: added support for network proxy settings

\- MongoDB: added handling of MongoError: Error in $cursor stage caused by operation exceeded time limit

\- Neo4j: added auto-height and auto-width for graph diagram properties of node labels and relationship types

\- Synapse: table option "with clustered index" for specific columns generated in DDL

\- Synapse: disabled varchar(max) data type for clustered columnstore index

\- Synapse: allowed compound primary and unique keys

&nbsp;

New features in v4.1.13 \[10-Aug-2020\]

\- Added reference description property for referenced definitions

\- XSD reverse-engineering: added support for references to complexTypes, and for group structures

\- JSON document reverse-engineering: added detection of ISO 8601 date/time/timestamp/duration in strings for Avro, Parquet, Cassandra, ScyllaDB, Glue, SQL Server, Snowflake, Synapse, Cosmos DB with MongoDB API, HBase, Neo4j, TinkerPop

\- Avro and Parquet: added support for network proxy settings when accessing files in Cloud storage (AWS S3, Azure Blob Storage, Google Cloud Storage)

&nbsp;

New features in v4.1.12 \[31-Jul-2020\]

\- JSON document reverse-engineering: added detection of ISO 8601 date/time/timestamp/duration in strings when target supports such data types: MongoDB, DynamoDB, Elasticsearch, Hive

\- MongoDB reverse-engineering: handling of multiple numeric subtypes: int32 \< int64 \< double \< decimal 128

\- Hive: added minify/beautify option to HQL script in UI and CLI

\- Hive: added handling of NULL data types in reverse-engineering of JSON Schema, as NULL is not a valid Hive data type

\- EventBridge: allowed registry with more than 100 schemas

&nbsp;

New features in v4.1.11 \[24-Jul-2020\]

\- Added support for new license type: Professional Edition - Concurrent Subscription

\- NDJSON: added reverse-engineering from stream, taking into account sampling options

\- EventBridge: soft launch of plugin

&nbsp;

New features in v4.1.10 \[18-Jul-2020\]

\- Properties pane: moved tabs to top to make presence more obvious

\- Added easy update of license identifier (no longer requires release then re-validate)

\- SQL Server: added handling of multi-type without oneOf choice

\- SQL Server: added parsing of connection string/URI in Connection Settings

\- Synapse: plugin soft launch

&nbsp;

New features in v4.1.9 \[09-Jul-2020\]

\- ERD entity auto-size, with auto-height and auto-width controls ON by default in Tools \> Options \> General. &nbsp;

\- Individual entity auto-height and auto-width can be decoupled from application setting with entity properties pane Options tab

\- XSD: added handling of &nbsp; &nbsp; element types and references

\- Cassandra: harmonize column order in Object Browser, ERD and hierarchical schema View

\- Hive: added table comments

\- Hive: added handling of references in arrays

\- Excel import/export for OpenAPI: handling of numeric response&nbsp;

\- Parquet: added reverse-engineering of RowGroup columns in separate message Properties Pane tab

\- SQL Server: added Windows Authentication

&nbsp;

New features in v4.1.8 \[27-Jun-2020\]

\- Creating reference to a definition (internal, model, external): added possibility to do multiple selections with shift/ctrl+click

\- Added spellcheck of textareas (description, comments, ...)

\- Added possibility to Collapse/Expand complex objects from contextual menu in ERD and hierarchical schema View

\- Documentation generation: improved performance

\- Forward-engineering of JSON documents and JSON Schema: added option to minify output

\- Command Line Interface revEngJSON and revEngDDL commands: added optional version argument

\- Hive: renamed properties Comments to Remarks, and Description to Comments, plus added handling of Comments in forward- and reverse-engineering for databases, tables and columns

\- Neo4j: added default timeout for reverse-engineering

\- OpenAPI: upgraded internal validator to handle spec version 3.0.3

\- SQL Server added option to choose batch separator (semi-column or GO)

&nbsp;

New features in v4.1.7 \[22-Jun-2020\]

\- Toggle Object Browser and Properties Pane default values for brand new installations

&nbsp;

New features in v4.1.6 \[19-Jun-2020\]

\- Object Browser and Properties Panes: added shortcuts to view/hide, respectively Ctrl/Cmd+F1 to toggle OB and Ctrl/Cmd+F2 to toggle PP.&nbsp; Same actions possible with double-click on 3-dots separator or via the View menu

\- Excel export/import: added handling of friendly display names for array items and choice subschemas

\- XSD: added reverse-engineering of common complexTypes

\- DynamoDB: added reverse-engineering of multi-region table replication metadata

\- DynamoDB: reverse-engineering of DDLs converts primary key constraints into partition/sort keys

&nbsp;

New features in v4.1.5 \[16-Jun-2020\]

\- Avro: keep sequence of fields when fields are not present in 100% of submitted data set

\- DynamoDB: added metadata choice of read/write capacity mode for on-demand instances

\- DynamoDB: added multi-region replica parameters

\- Swagger/OpenAPI: preserve resource components during merge of conflict resolution

&nbsp;

New features in v4.1.4 \[11-Jun-2020\]

\- Array items: added property for friendly descriptive name to be displayed in models instead of \[0\], \[1\]... \[n\]

\- oneOf/allOf/anyOf choices: added description and comments properties for documentation

\- Excel export: optionally resolve references to definitions for better readability.&nbsp; Changes to referencing attributes in Excel are ignored during reverse-engineering

\- JSON Document reverse-engineering: added support for NDJSON Newline Delimited JSON ([https://ndjson.org/](<http://ndjson.org/>))

\- JSON Schema and document reverse-engineering: added conflict management dialog: choice of keep both (as previously) / replace / merge / cancel

\- XSD reverse-engineering: added conflict management dialog: choice of keep both (as previously) / replace / merge / cancel- XSD reverse-engineering: added handling of references to common attribute types

\- Avro: when reverse-engineering a multi-line JSON document and a field appears in strictly less than 100% of of the occurrences, make it multi-data type with NULL as the first one and default of NULL.&nbsp; Works for both scalar and complex data types (with oneOf choice in case of complex.)

\- Cassandra \& ScyllaDB: added Advanced tab in connection settings dialog to set other truncate\_request\_timeout\_in\_ms limit than the default 60k milliseconds

&nbsp;

New features in v4.1.3 \[05-Jun-2020\]

\- Allowed references to definitions with multiple data types

\- Command Line Interface: allowed obfuscation for plugins with snippets

\- Community version: doubled limit to 50 objects

\- Documentation: added dynamic calculation of column width

\- Print diagram: increased image focus for large models in PNG and PDF

\- Glue and Hive: added handling of spaces in names for databases, tables, and columns

\- Neo4j, Tinkerpop: allowed Excel export of graph models, even if no edges are present

\- Neo4j, Tinkerpop: added title in JSON Schema forward-engineering

\- Neo4j, Tinkerpop: added ability to forward-engineer JSON Schema of edges

\- XSD reverse-engineering: added support for additional data types

&nbsp;

New features in v4.1.2 \[29-May-2020\]

\- Tech refresh of Electron (v8.3.0), NodeJS (v12.14.0), Chromium (v80), and Electron-related modules

\- Performance improvements for Print Diagram function, rendering of Object Browser and menu

\- Naming conventions: replaced global parameters by separate target-specific parameters to allow different behavior depending on target

\- Naming conventions: parameters are stored in a JSON file in the C:\\Users\\%usernames%\\.hackolade\\options\\\<targetname\> directory, so they can be shared with teammates via Git.

\- Added context menu with clipboard operations for text inputs, textareas (properties panes, modals, forward-engineering tabs)

\- Fixed exception when performing replace on references attribute definitions

\- Added possibility to replace any attribute with a reference: internal, model, or external

\- Added possibility to replace an attribute by an internal or external reference (previously, only model reference was possible)

\- Snowflake: added possibility to CREATE TABLE ... AS SELECT (CTAS)

&nbsp;

New features in v4.1.1 \[20-May-2020\]

\!\!\! Warning: non-backward-compatible change \!\!\!&nbsp; Models that include foreign key relationships, if saved with v4.1.1 or above, cannot be read with an earlier version \!\!\!

\- Added support for composite foreign keys in RDBMS targets

\- Hive: implemented support for composite foreign keys

\- Snowflake: implemented support for composite foreign keys

\- SQL Server: implemented support for composite foreign keys

&nbsp;

New features in v4.1.0 \[14-May-2020\]

\- Added sketchy ERD rendering when zoom out is such that it is impossible to read details anyway, for improved performance

\- Added Tools \> Options \> General parameter to control sketchy ERD zoom level range

\- Stopped rendering ERD for parts of the diagram outside visible area, for improved performance

\- Created additional zoom levels

\- Made OS file open/save dialogs modal and displayed on active screen when dual display

\- JSON Schema reverse-engineering and referencing of external definition: added handling of files containing only definitions and no other structure

\- Cosmos DB w/ SQL API: made primary key part of Partition Key with visuals in ERD and hierarchical schema view

\- Snowflake: added support for composite primary key and unique key constraints

&nbsp;

New features in v4.0.4 \[06-May-2020\]

\- Enable Edit \> Copy function in forward-engineering tabs

\- Suggest Denormalization: bypass function if relationship without child attribute

\- Snowflake: added external browser auth type for SSO

&nbsp;

New features with v4.0.3 \[27-Apr-2020\]

\- macOS Mojave: fixed copy/paste issue in connection settings

\- Object Browser: added tooltip for long object names

\- DDL reverse-engineering: added handling of HashTable

\- JSON Schema Preview and forward-engineering: added a new mode "Full" to show non-standard keyword including custom properties

\- AWS Glue and Hive: added constraints UNIQUE, NOT NULL, DEFAULT and CHECK to properties pane, forward- and reverse-engineering

\- Cassandra/ScyllaDB: allow only UDT data type in model definitions/user-defined types

\- Cosmos DB SQL API: connection settings name and address now mandatory, renamed autopilot to autoscale, removed storage capacity

\- Snowflake: added authentication integration with Okta Single Sign-On

\- Swagger/OpenAPI: added generation of x- path extensions in forward-engineering

&nbsp;

New features with v4.0.2 \[22-Apr-2020\]

\- Reverse-engineering of JSON documents: keep empty objects and arrays

\- Couchbase: circumvent error in Couchbase Community v6 to invoke N1QL INFER statement

\- MarkLogic: reverse-engineering of JSON objects as objects instead of triples

\- SQL Server: in reverse-engineering of JSON docs, set length of char data types on detected maxLength of string

&nbsp;

New features with v4.0.1 \[21-Apr-2020\]

\- Reverse-engineering of complex data types into SQL database targets: added option to automatically normalize structures imported from JSON documents, JSON Schema or XSDs.&nbsp; Sub-objects and arrays optionally result in separate entities

\- Snowflake added support for sequences and file formats

\- SQL Server: added support for full text and spatial indexes, filtered index expressions, views indexes and partitioned views, view definition AS SELECT statement, memory-optimized tables

\- Hive: allowed SSL declaration of multiple certificates from an enterprise Certificate Authority

&nbsp;

New features with v4.0.0 \[08-Apr-2020\]

\- \!\!\!\!\! Discontinued support for 32-bit Windows \!\!\!\!\!

\- Microsoft SQL Server and Azure SQL Database: plugin for data modeling, forward- and reverse-engineering, including JSON in (n)varchar(MAX) columns, cfr [https://docs.microsoft.com/en-us/sql/relational-databases/json/json-data-sql-server?view=sql-server-ver15](<https://docs.microsoft.com/en-us/sql/relational-databases/json/json-data-sql-server?view=sql-server-ver15>)

\- Snowflake: ability to reverse-engineer DDL into any target

\- Snowflake: plugin for data modeling, forward- and reverse-engineering, including JSON in VARIANT columns, cfr [https://docs.snowflake.com/en/sql-reference/data-types-semistructured.html#variant](<https://docs.snowflake.com/en/sql-reference/data-types-semistructured.html#variant>)

\- Added JSON Schema field description when reverse-engineering to definitions

\- Added ability to change order of objects in Object Browser

\- Added ability to insert or append objects in Object Browser

\- External definitions: improved opening model if definitions are absent or have moved

\- Orthogonal distribution: added topology-shape-metrics algorithms and Klay layout for small to medium size ERDs

\- DDL: improved handling of semi-columns in comments and defaults

\- DDL reverse-engineering: mapping comments to JSON Schema description property for consistency

\- Hive: added support for Hive v1.x

\- Hive reverse-engineering: removed limit of 100 databases, plus allowed specifying database name to limit scope of discovery

\- Neo4j: added support for Neo4j v4, including multi-database instances

\- Swagger/OpenAPI: added choice of layout, including new horizontal layout

&nbsp;

