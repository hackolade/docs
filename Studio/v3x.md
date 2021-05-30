# v3.x

New features with v3.6.10 \[24-Mar-2020\]

\- JSON Data preview: enhanced validation for numbers with exponential notation

\- Command-Line Interface: added tolerance for broken relationships when obfuscating model

\- MongoDB script: included enums when multiple data type

&nbsp;

New features with v3.6.9 \[19-Mar-2020\]

\- Added prompt for UUID if required, plus additional logging

\- Added documentation timeout and uncaught error

&nbsp;

New features with v3.6.8 \[6-Mar-2020\]

\- Added horizontal scrollbar in Object Browser

\- Fixed event handling (undo/redo conflicting with typed letters "z" and "y" if Ctrl+Tab had been pressed inadvertently)

\- Undo no longer Closes all in Object Browser

\- When updating external references for refresh button, a dialog now offers option to refresh all external references in the model

\- Avro: added subtype and logicalType properties to extended JSON Schema

\- Cassandra/ScyllaDB: added handling of nested UDTs

\- Many Swagger/OpenAPI improvements:

\-- documentation no longer lists unused structures

\-- documentation: fixed ERD image

\-- added validations for semantic and structural conditions

\-- added visual mark for nested references in hierarchical schema view, plus option to Go to definition

\-- extended structure pre-creation for request body/response content

\-- added dropdown for media types, plus option to create not-listed values in hierarchical schema view

\-- added description and tooltip for response codes in Properties Pane dropdown

\-- fixed inconsistent contextual menu for definitions/componenents in Object Browser

\-- added possibility to add and remove responses from Properties Pane of request

\-- removed the naming convention "couple" button for media-type name

\-- fixed copy/duplicate-paste validation errors

\-- added layout options to display request/responses structure horizontally

&nbsp;

New features with v3.6.7 \[26-Feb-2020\]

\- ScyllaDB: added new plugin

\- CLI: added spinner

\- Plugin Manager: suppressed Remove button for native targets

\- Plugin Manager: propose to save model prior to restart

\- MacOS: performance improvement for slow URL opening on Mojave

\- JSON Preview: fixed tab persistence in localStorage&nbsp;

&nbsp;

New features with v3.6.6 \[24-Feb-2020\]

\- backward compatibility for JSON and Couchbase models

&nbsp;

New features with v3.6.5 \[22-Feb-2020\]

\- CLI obfusc command: added statistics report at end of process, plus fine-tuned nested properties handling

\- Naming conventions conversion: apply changes no longer requires default coupling to be modified

\- Added capture of exception if collectionId is null

\- Added re-calculation of container size when pasting entities

\- ArangoDB: added foreign-key relationship cardinality display in graph view

\- ArangoDB: added FK and edge relationship selection in object selection menu

&nbsp;

New features with v3.6.4 \[19-Feb-2020\]

\- Soft release of ArangoDB plugin, without forward- or reverse-engineering

\- Fixed paste function in license validation modal for some Mac versions

\- Added paste icon in license validation modal

&nbsp;

New features with v3.6.3 \[17-Feb-2020\]

\- Added Migrate button if native target customProperties plugin is not in plugin registry

\- Added Migrate button if native target customProperties plugin is not installed

\- Changed description of native target customProperties plugin

\- Changed order of plugin listing in Plugin Manager

&nbsp;

New features with v3.6.2 \[15-Feb-2020\]

\- All plugins: separated customizations from corresponding plugin, to facilitate plugin updates

\- Link to show plugin directory removed from Help menu and moved to customization of each plugin of Help \> Plugin Manager \> Installed tab

\!\!\!\! if you have defined custom properties for Hackolade targets, you should read these instructions: [https://hackolade.com/help/Migrationtoenhancedcustompropert.html](<https://hackolade.com/help/Migrationtoenhancedcustompropert.html>)

&nbsp;

New features with v3.6.1 \[13-Feb-2020\]

\- Avro: added forward-engineering of namespace for references

\- Mongoose: fixed handling of default value conflicting with eval() suppression for Electron security

&nbsp;

New features with v3.6.0 \[11-Feb-2020\]

\- Tech refresh of Electron (v6.1.4), NodeJS (v12.4.0), Chromium (v76), and Electron-related modules, plus MongoDB, Couchbase and DynamoDB drivers

\!\!\!\!\! Discontinued support for 32-bit Linux (https://electronjs.org/blog/linux-32bit-support) \!\!\!\!\!

\!\!\!\!\! Discontinued support for MacOS X 10.9 (Mavericks) or before&nbsp; (https://github.com/electron/electron/pull/15357) \!\!\!\!\!

\!\!\!\!\! For Linux upgrade, it is advised to delete first the directory where Hackolade is currently installed, prior to unzipping the new version

&nbsp;

New features with v3.5.11 \[4-Feb-2020\]

\- Avro: added support for reverse-engineering from AWS S3, Azure Blob Storage, Google Cloud Storage

\- Cassandra: added support for materialized views

\- AWS DocumentDB: adjusted MongoDB connections to also support the SSH/SSL combination needed for AWS DocumentDB: [https://docs.aws.amazon.com/documentdb/latest/developerguide/connect-from-outside-a-vpc.html](<https://docs.aws.amazon.com/documentdb/latest/developerguide/connect-from-outside-a-vpc.html>)

\- Parquet: added support for reverse-engineering from Google Cloud Storage

&nbsp;

New features with v3.5.10 \[22-Jan-2020\]

\- DDL: allowed SQL syntax from LucidChart (i.e. without CONSTRAINT keyword for PRIMARY KEY) for Oracle, SQL Server, MySQL, and Postgres

\- DDL: allowed reverse-engineering of business names with spaces

\- Excel: allowed import of Excel without container GUID

\- Parquet: added support for reverse-engineering from Azure Blob Storage

&nbsp;

New features with v3.5.9 \[16-Jan-2020\]

\- Consistent positioning of dialog OK/Cancel buttons according to Windows UI standard

\- CLI model comparison no longer requires a container

\- Cassandra: reverse-engineering filters out system tables

\- Cosmos DB with SQL API: support for Control Pane via REST API in addition to Data Pane via new SDK

\- Glue: added Set data type, classification property, SerDe parameters, and table properties

\- Hive: NoSasl connection no longer requires Kerberos modules on Mac

\- Parquet: added possibility to reverse-engineer files from AWS S3

\- Swagger/OpenAPI: added possibility to de-activate resource/request/response so it appears commented in documentation file

&nbsp;

New features with v3.5.8 \[11-Jan-2020\]

\- Added collapse/expand all options to Object Browser contextual menu

\- Fixed width of keys in ERD for Cassandra when partition key is also a foreign key

\- Respect sequence keys in Cassandra hierarchical schema view

\- Fixed Kerberos library for Hive on Mac

&nbsp;

New features with v3.5.7 \[6-Jan-2020\]

\- Fixed reverse-engineering from database instances

&nbsp;

New features with v3.5.6 \[3-Jan-2020\]

\- Added display of index info in hierarchical schema view

\- When generating JSON Data numeric with no sample, now uses pseudo-random function so data does not change each time

\- Created plugin for Apache Parquet

\- Cassandra: added connection to DataStax Apollo on Constellation&nbsp;

\- Neo4j and TinkerPop plugins: added reverse-engineering of JSON documents and JSON Schema

\- Swagger/OpenAPI: added possibility to reference another API file

&nbsp;

New features with v3.5.5 \[13-Dec-2019\]

\- Created plugin for AWS Glue Data Catalog

\- Added reverse-engineering of DDLs, XSDs, JSON docs, and JSON Schema as model definitions (in case of OpenAPI as schema components)

\- Added CLI command revEngDDL for reverse-engineering of DDLs from command line

\- Swagger/OpenAPI: added reverse-engineering of definitions/components not referenced in API

&nbsp;

New features with v3.5.4 \[30-Nov-2019\]

\- Graph plugins: implemented force-directed layout algorithms with spring-like attractive forces, see example: https://bit.ly/341x5l0

\- Graph plugins: enhanced orthogonal distribution of ERD view

\- Avro: added support for namespaces in data types

\- Avro: corrected name of record data type

\- OpenAPI: improvement of components reverse-engineering for ISO20022 Payment Processing APIs

\- DDL: added support for Informix dialect

&nbsp;

New features with v3.5.3 \[21-Nov-2019\]

\- Graph plugins: added graph toolbar toggles to View menu

\- Implemented Electron security recommendations for framework foundation

\- Oracle DDL: improved handling of Foreign Keys so as to allow importing of Informix DDLs as well

\- Excel: fix 'cannot read property reduce of null' error on import

\- MongoDB: add use \<dbs\> to script

\- Swagger/OpenAPI: add validation prior to reverse-engineering

&nbsp;

New features with v3.5.2 \[15-Nov-2019\]

\- Command-Line Interface: added command to reverse-engineer JSON Schema and JSON documents

\- CLI: added argument to reverse-engineer script files (MongoDB validator, Cassandra CQL, Hive HQL, Avro schema, Neo4j Cypher, Swagger documentation, etc...)

\- CLI: added argument to forward-engineer JSON Schema or sample JSON document.&nbsp; For JSON Schema, included choice to reference or resolve definitions, and optionally to update external references

\- ERD view: increased size of of horizontal and vertical scroll bar handles

\- Avro: added possibility to display and forward-engineer schema or encoded for Confluent Registry

\- Avro: added possibility to display and forward-engineer schema with standard indentation or minified

\- Avro: added handling of Java-generated classes&nbsp;

\- JSON Schema: added possibility to display and forward-engineer schema with standard indentation or minified

\- Graph plugins (Neo4j and TinkerPop): added possibility to reverse-engineer: DDLs, XSDs, and Excel template

\- Graph plugins: implemented separate positioning of objects for graph view and ERD view

&nbsp;

New features with v3.5.1 \[30-Oct-2019\]

\- Added possibility to duplicate a node/vertex label to represent recursive relationship/edge type as a line instead of a loop

\- Added decorative symbols (annotation) to the graph diagram (Neo4j \& TinkerPop)

\- Added copy/paste of related relationship/edge labels when copying/pasting node/vertex labels

\- Added toggle to display relationship type names along the lines vs always horizontal

\- Added ability to select all node labels to move to another database

\- All targets: added indicator in ERD when an attribute is a reference to a definition: i for internal, m for model, and e for external

\- Improved rendering performance of hierarchical schema view for large models

\- Added refresh button in Properties Pane for external reference

\- Added support for custom $schema&nbsp;

\- Fixed release of concurrent seat in case of orphan processes

\- All plugins: mapped plugin data types to standard JSON data types for JSON Schema forward-engineering

\- Avro: fixed field order of Avro schema in case of complex data types with choices

\- Avro: JSON data sample: now takes into account logicalTypes

\- Avro: JSON data sample: when null is first data type, take into account next data type, including in case of complex data type

\- OpenAPI: fixed deletion of resource/request/response

\- TinkerPop: added support for SSL and SSH in reverse-engineering

&nbsp;

New features with v3.5.0&nbsp; \[20-Oct-2019\]

\- Added support for TinkerPop graph computing framework with Gremlin graph traversal

\- Many graph database UI enhancements, for Neo4j and upcoming TinkerPop, Amazon Neptune, and others...

\- Display node label controls on mouse hover only

\- Added tooltips to node label controls

\- Added relationship type highlight and controls on hover

\- Added control to reverse relationship direction

\- Added focus on relationship type name in properties pane when creating

\- Added possibility to create node label together with relationship type by clicking on relationship button then clicking again in workspace

\- Fixed centering of relationship type name

\- Added selection of relationship type by clicking on its name

\- Added default node label size, node label color, and relationship type line thickness in Tools \> Options

\- Added checkbox "Apply to all in model" to the popups for node label size, node label color, and relationship type line thickness&nbsp;

\- Added toolbar button to toggle opening of all property boxes

\- Added independent opening/closing of properties boxes

\- Added toolbar button to toggle showing all relationship names

\- Added graph diagram to Print Diagram

\- Added opening of properties boxes with fit to content

\- Added easy copy/paste of all properties between 2 node labels

\- Added decorative symbols to the graph view

\- Avro: changing data type maintains description and comments

\- Avro: added precision and scale to script

&nbsp;

New features with v3.4.12:

\- Enhanced undo/redo performance, handling in Object Browser, moving containers in graph view

\- Added handling of undo/redo in reference definitions

\- Added handling of copy/paste of external definitions

\- Improved performance opening large models and rendering ERD with large number containers and nested structures (still needs improvements on hierarchical schema view)

\- Added last 10 actions of undo stack to uncaught error reporting

\- Fixed an issue when a simple JSON Schema data types reversed with properties

\- Fixed multiple copy-pasted collections haven’t colors from source collections

\- Avro: added forward-engineering of logicalType when multiple data types

\- Avro: filtered redundant pattern property in forward-engineering

\- Cassandra: split table options blob into separate properties

&nbsp;

New features with v3.4.11:

\- JSON Schema reverse-engineering: added handling of array items with empty objects

\- JSON Schema/JSON Doc/DDL/XSD/Mongoose reverse-engineering: extended error modal with log information

\- Hierarchical schema view: fine-tuning of right-click for contextual menu

\- Avro: added display of non-null data type sample in JSON Data&nbsp;

&nbsp;

New features with v3.4.10:

\- Print Diagram: made generation independent of Windows DPI display settings (scale and layout)

\- MongoDB: updated view pipeline when referencing a definition

\- Swagger: use example property to generate Swagger samples

&nbsp;

New features with v3.4.9:

\- Added scrolling for long lists of definitions

\- Avro: removed false positive on validation of records

\- Avro: enhanced JSON Data sample generation logic

\- Avro: replaced spaces by underscore during reverse-engineering of JSON Schema title and field names

\- Excel: adjusted import logic of definitions when target is Swagger/OpenAPI

&nbsp;

New features with v3.4.8:

\- Print Diagram: added headers and footers to PDF

\- Print Diagram: added selection and/or range of pages to print

\- Print Diagram: added zoom control and fit to single page

\- Excel: improved handling of entity/attribute name split

&nbsp;

New features with v3.4.7:

\- Enhanced error logging to include undo actions

\- ERD: added text decorative symbol

\- Avro: added data type mapping when forward-engineering JSON Schema

&nbsp;

New features with v3.4.6:

\- Added contextual menu on multiple selections

\- Object Browser: added single level expansion for relationships, and definitions

\- Undo/Redo: added handling of copy/paste of views and graph node labels

\- Avro: added handling of required property for choices

\- Avro: adjusted mapping of data types when reverse-engineering of JSON Schema

\- Avro: automatically make default property null when null data type is first of multiple data types

&nbsp;

New features with v3.4.5:

\- Object Browser: added single level expansion for containers, entities, attributes, and views

\- Avro: added mapping of JSON Schema string formats to corresponding Avro logical types

&nbsp;

New features with v3.4.4:

\- Avro: enhanced approach for nullable fields by re-introducing null data type, see [Avro schema](<Avroschema.md>) for more info

\- Avro: added handling of multi-type fields during reverse-engineering of JSON Schema and JSON documents

&nbsp;

New features with v3.4.3:

\- Added Undo (Ctrl+Z) and Redo (Ctrl+Y) functions

\- Added AutoSave toggle switch (OFF by default) with parameter in Tools \> Options \> General to control time interval in minutes &nbsp;

\- Added recovery of new unsaved model

\- Added release notes in application update dialog

\- Enriched error details in reverse-engineering connection dialog&nbsp;

\- Hive: support for http transport mode for LDAP and Kerberos authentication

\- Swagger: added handling of null data type during reverse-engineering of JSON/JSON Schema, and converting to string with default = "null"

\- OpenAPI: added handling of null data type during reverse-engineering of JSON/JSON Schema, and converting to string with nullable = true

&nbsp;

New features with v3.4.2:

\- Extended drag \& drop capability to multiple selections

\- Enhanced Find function to add match case, match whole word, beginning/end/anywhere in word, type of object, next/previous navigation, session history

\- Added Find-and-Replace function

\- Mongoose reverse-engineering: added handling of sub-documents as internal definitions

\- Mongoose reverse-engineering: added support for Buffer and Decimal128 data types

\- License key status: added refresh button

\- MongoDB: added generic processing of different SRV record formats

\- MongoDB: replaced deprecated document counts method impacting performance

\- Mac: fixed selection of reverse-engineering files

\- Hive: added support for Kerberos Quality of Protection (QOP) values auth-int (integrity) and auth-conf (confidentiality) \[[https://tools.ietf.org/html/rfc1964\]](<https://tools.ietf.org/html/rfc1964>)

&nbsp;

New features with v3.4.1:

\- Save/Open: use default path locations first time only in a session, then remember last location used in session

\- Fixed reverse-engineering of JSON data when special symbols are present

\- Mongoose forward-engineering: added handling of definitions (reverse-engineering will be available in the next version)

\- Mongoose forward- and reverse-engineering: added choice to output in object notation

&nbsp;

New features with v3.4.0:

\- Added multiple selection in Object Browser, ERD and hierarchical schema view for more productive copy/paste and delete: Shift+Right-click for contiguous, Ctrl+Right-click for non-contiguous

\- Added drag-and-drop from/to complex data types at a different level

\- Added lineage (aka impact analysis, aka where-used) for references plus denormalized keys and denormalized attributes

\- Added ERD visual for denormalized keys (targets of foreign keys) and denormalized attributes (targets of foreign masters)

\- Reformatted attribute path in JSON Preview validation pane

\- Added check for plugin updates at startup

\- Excel: split name of attribute in a column for entity name and a column for attribute name

\- Cassandra: added authentication through Java Key Store &nbsp;

\- Cassandra: filtered CQL script in documentation generation if table not selected

\- Hive: added authentication through Java Key Store&nbsp;

\- Avro: default must match enum values

\- Avro: display warning in ERD and hierarchical schema view if default value does not match data types

&nbsp;

New features with v3.3.2:

\- Added target script (CQL, Avro Schema, etc.) to documentation, with toggle in Options

\- Added possibility to perform Reverse-Engineering from Menu in Overview screen

\- MongoDB: added possibility to import URI with SRV record

\- Excel: added merging of nested fields

\- Excel: converted erroneous boolean values to false

\- Excel: handled empty technical names during reverse-engineering

\- Avro: handled inline comments in configs&nbsp;

\- Avro: correctly handled spaces in attribute names during forward-engineering

\- Avro: enhanced logic for required fields with null allowed

\- Neo4j: fixed bug when right-click on node in hierarchical schema view

&nbsp;

New features with v3.3.1:

\- Object with a validation error (default or example not respecting data type, invalid names, etc...) appear in red in Object Browser, ERD and hierarchical schema view

\- Avro: integrated Avro schema validator to Avro Schema tavb

\- Avro: added 'Null allowed' property to complex types

\- MongoDB reverse-engineering: added logging and default for read preference parameter

&nbsp;

New features with v3.3.0:

\- Added support for OpenAPI 3 (plugin download required)

\- Excel: handling of column title for empty sheets

\- Avro: added styles for "null allowed" properties in ERD and hierarchical schema view

&nbsp;

New features with v3.2.3:

\- DDL reverse-engineering: allow that Create Table statements are absent and that only Alter Table statements are present

\- When multiple data types, there should only be a single default property

\- Avro: added a property 'null allowed' so multiple data types (scalar) are not necessary to allow for backward/forward compatibility.&nbsp; For multiple data type with complex types, it even simpler: no Choice necessary

\- Avro: added handling via definitions for named types (records, enums, and fixed)

&nbsp;

New features with v3.2.2:

\- Excel export/import: added support for definitions (internal, model, and external) plus references to definitions

\- Swagger: added ERD toggle of details to filter out unused structures

&nbsp;

New features with v3.2.1:

\- Excel export: added checkbox for each config section

\- Excel import - Cassandra: added handling for primary and clustering keys&nbsp;

\- Added handling for collapsed nodes in hierarchical schema view and model definitions

\- Cassandra: fixed losing keys separator

\- Swagger: removed CommonMark in extension values

&nbsp;

New features with v3.2.0:

\- Added generic export/import with Excel for all targets

\- Added multiple file selection in Reverse-Engineering of JSON documents, JSON Schema, DDLs \& XSDs

\- Added using technical model name for file name in Forward-Engineering of JSON documents, JSON Schema

\- Fixed picking from field list on definitions tab

\- Cosmos DB w/ Mongo API: added reverse-engineering support for unique items, TTL indexes, stored procs, and UDFs

\- Cosmos DB w/ Mongo API: added reverse-engineering from Azure Cosmos DB Emulator via REST API

\- Filtered GUIDs from pattern properties in forward-engineering of JSON Schema

\- Single click to collapse expand complex structures in hierarchical schema view

&nbsp;

New features with v3.1.2:

\- Allowed multiple selections in reverse-engineering of JSON documents, JSON Schema, DDLs, and XSDs

&nbsp;

New features with v3.1.1:

\- Added support for CommonMark (a.k.a. Markdown) in description and comment properties

\- Fixed handling of custom-defined properties in native targets

\- Fixed uncaught error in repetitive reverse-engineering of JSON documents

\- Added Unique Items in Cosmos DB collection properties (SQL API)

\- Fixed Neo4j uncaught error

&nbsp;

New features with v3.1.0:

\- Hive: added LDAP and Kerberos authentication support, plus SSL

\- Elasticsearch: added specialized and range datatypes

\- Swagger: added Interactive API pane to Swagger Definition tab

\- Added visuals in ERD for required and indexed attributes&nbsp;

&nbsp;

New features with v3.0.2:

\- MongoDB: added support for LDAP roles

\- MongoDB: added handling of replica read preference

\- Elasticsearch: added handling of default index options

\- Cassandra: fixed generation of CQL script for only selected tables

\- Neo4j: fixed actions menu for graph view tab

&nbsp;

New features with v3.0.1:

\- Sync with v2.5.7

&nbsp;

New features with v3.0.0:

\- Added support for REST APIs, starting with Swagger 2 (openAPI 3 will follow in a few weeks)

\- Added zoom on container when selected from picker

\- Cassandra: added LDAP authentication support

