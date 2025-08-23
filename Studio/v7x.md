# v7.x

New features in v7.9.10 \[31-Jan-2025\]

\- Excel: added possibility to import simple primary keys into a model derived from Polyglot

\- PowerDesigner: added reverse-engineering of packages in .pdm files in Polyglot models

\- Joi: updated plugin for new build system and forward-engineering compatibility

\- Oracle: added "Default" property to json data type and reverse-engineer it if it appears in DDLs

\- Oracle: added reverse-engineering of MONITORING/NOMONITORING in DDLs

&nbsp;

New features in v7.9.9 \[24-Jan-2025\]

\- Copy/Paste/Duplicate: added composite PK/UK constraints and indexes to clipboard payload when copying entities

\- Excel import: added possibility to reverse-engineer (composite) primary keys into a model derived from Polyglot

\- Referenced definitions: added possibility to remove property value on a reference for a value declared in the definition

\- PowerDesigner reverse-engineering: added validation that the selected file is indeed a PowerDesigner file

\- Workgroup edition: added a shareable link URL in the Files screen of the repository context

\- Avro, BigQuery, Cassandra, Cosmos DB Gremlin, Cosmos DB Mongo, Cosmos DB SQL, Couchbase v7+, DeltaLake/Databricks, Elasticsearch (both), EventBridge, Glue, HBase, Hive, JanusGraph, Neptune Gremlin, Neo4j, OpenAPI, Parquet, Protobuf, ScyllaDB, Swagger: allow forward-engineering in browser

\- DeltaLake/Databricks: separated sort keys from clustering keys in DDL

&nbsp;

New features in v7.9.8 \[20-Jan-2025\]

\- Custom properties: allowed change of block property

&nbsp;

New features in v7.9.7 \[17-Jan-2025\]

\- Share model link URL: made logic more tolerant for presence or not of https:// in host domain name to match with existing connection for GitLab Server&nbsp;

\- Share model link URL: added possibility to create a shareable link for a model opened from a shared link

\- ERDV: fixed Y coordinate when adding edges with no parent and no child

\- Model validation: eliminated possible false positives with derived model definitions and derived attributes that depend on other attributes (parent or siblings)

\- Polyglot: applied order of attributes from polyglot model to derived model on update of polyglot definitions

\- Polyglot: added derive of custom properties from Polyglot when the field is converted from single type to multiple (e.g. in Avro)

\- Properties Pane for FK relationships: added possibility to perform multiple select to add parent or child columns in dialog

\- Avro: allowed doc property to be overwritten by reference description in Avro script

\- Avro: added taking custom properties, if different from reference field instead of definition

\- Avro: added custom properties of custom tabs when data type is multiple&nbsp;

\- DeltaLake/Databricks: added support for CLUSTER BY property and DDL clause

\- DeltaLake/Databricks: added ck marker in ERD for clustering key in CLUSTER BY

\- Oracle: added ability to deselect AS IDENTITY checkbox property when it should be disabled

\- Oracle: updated ANTLR grammar in reverse-engineering of DDL to ignore READ WRITE option TABLESPACE and TRANSITION in PARTITION statements

\- Oracle: allowed duality views to be cross-schema

\- SQL Server: added support for T-SQL computed columns in a table

&nbsp;

New features in v7.9.6 \[10-Jan-2025\]

\- Open data model: added possibility, both in browser and desktop, to open a model directly from GitLab Cloud \& Server repository without need for local clone, provided adequate license and repo credentials

\- Share model link URL: added ability to share link to view model in browser directly from GitLab Cloud \& Server \[assumes that users of the link have a valid license and proper access to the model repo\]

\- Installer packaging: removed unused trampoline pre-builds

\- Custom properties: allowed defaultValue in field-level custom tab

\- Custom properties: allowed cleanDependency for block properties

\- Object Browser: performance improvement by eliminating redundant rendering

\- PowerDesigner: added reverse-engineering of PDM file in Polyglot model

\- PowerDesigner: enabled reverse-engineering of LDM and PDM file from browser deployment&nbsp;

\- Reverse-Engineering from instance: added possibility to filter views in selection dialog

\- Avro: allowed forward-engineering when an internal definition references a model definition and they both have the same name

\- Couchbase v7+ Scopes \& Collections: use UPSERT when applying sample to instance

\- DeltaLake/Databricks: fixed generation of PK constraint when columns are also part of clustering key

&nbsp;

New features in v7.9.5 \[03-Jan-2025\]

\- Open From: added handling of non-existing organization in Azure DevOps Repos which resulted in endless connection loop

\- Open From: enhanced error dialog in Bitbucket Cloud in case of invalid read-only password permissions

\- Open From: reduced to single API call in case Bitbucket Cloud filter is used when navigating through the folders

\- Excel export: disabled workbook protection for PK/UK columns as too constraining for other features -- user is warned by column note to not edit these columns

\- Workgroup Git: added more explicit message if attempt to commit without commit message

\- DeltaLake/Databricks: filtered TBLPROPERTIES from DDL if undefined

\- Hive: removed secondary index tab in Properties Pane as no longer supported in Hive 3.0 and above

\- MariaDB: added ASC sort option to index DDL if specifically selected instead of default

\- MariaDB, MySQL: removed KEY index type from list of available options

\- Oracle: removed default ORGANIZATION HEAP LOGGING from DDL if not explicitly activated, and added dependency for storage logging option

\- Teradata: enhanced table-level validation

&nbsp;

New features in v7.9.4 \[27-Dec-2024\]

\- Open data model: added possibility, both in browser and desktop, to open a model directly from Bitbucket Cloud repository without need for local clone, provided adequate license and repo credentials

\- Share model link URL: added ability to share link to view model in browser directly from Bitbucket Cloud \[assumes that users of the link have a valid license and proper access to the model repo\]

\- License management: added use of Windows native API to retrieve UUID in case cmd and powershell have been disabled for user

\- Custom properties: added ability to create dependency on keyword value in any level with dot notation from objectRoot

\- PowerDesigner: added handling of reverse-engineering when subtypes are in a different container than supertype

\- PowerDesigner: added handling of reverse-engineering when subtype has 2 parent supertypes

\- Couchbase Scopes \& Collections: added fallback to secondary index if no primary index is enabled for fetching of sampling of \<key\> property

&nbsp;

New features in v7.9.3 \[20-Dec-2024\]

\- Browser deployment: allowed use of license keys for all editions except free trial.&nbsp; Warning: not all features of Personal, Pro, and Workgroup Editions are enabled yet in the browser.&nbsp; Desktop app remains the flagship with all feature capabilities

\- PowerDesigner LDM reverse-engineering: added handling of technical characters in non-string type of a passed parameter

\- PowerDesigner: moved subclasses in same container as their parent superclass

\- Collibra: added assignments for new custom properties in config

\- Avro: added assignment of type definition name to the created reference in oneOf choice

\- Avro: added doc property to schema when oneOf union type of complex data types

\- CockroachDB, Db2, DeltaLake/Databricks, Hive, MariaDB, MySQL, Oracle, PostgreSQL, SQL Server, Synapse, Teradata, YugabyteDB-YSQL: added a warning badge in the Properties Pane if an index does not have a name when required, plus column list

\- BigQuery, Cassandra, CockroachDB, Db2, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, ScyllaDB, Snowflake, SQL Server, Synapse, Teradata, YugabyteDB-YSQL: added commenting/filtering of DDL when schema is flagged as inactive

\- Oracle: disabled AS IDENTITY property when a column already has the flag enabled

\- PostgreSQL: added support for reverse-engineering of vector data types

\- PostgreSQL: fixed clearing dependency when number field is out-of-range

&nbsp;

New features in v7.9.2 \[13-Dec-2024\]

\- Tech refresh of Electron (v33.3.0), NodeJS (v20.18.1), Chromium (v130.0.6723.152), V8 (v13.0) and related modules

\- Docker image: released v0.0.21 on DockerHub with additional libraries due to Electron 33 upgrade

\- Welcome page and File menu: added models opened with "Open from..." to the list of of recent models

\- PowerDesigner: added support for reverse-engineering of shortcuts in LDM files to add modeling objects to ERDVs

\- Db2, DeltaLake/Databricks, Hive, Oracle, Teradata: added handling of default values with quotes

\- Delta/lake/Databricks: added Runtime 16 version

\- Delta/lake/Databricks: added ability to reverse-engineer Hive HQL file

\- Oracle: added support for GENERATED ALWAYS AS expression, in addition to existing identity

\- PostgreSQL: added support for vector data type and index types HNSW and IVFFlat with pgvector extension for PostgreSQL versions 11 and up.&nbsp; Includes maintenance and forward-engineering, while reverse-engineering will be coming next week

&nbsp;

New features in v7.9.1 \[06-Dec-2024\]

\- Tech refresh of Electron (v33.2.1), NodeJS (v20.18.1), Chromium (v130.0.6723.137), V8 (v13.0) and related modules

\- License enforcement: handled NodeJS spawn issues, when cmd.exe or powershell.exe are blocked by administrator, with an error modal redirecting to user doc

\- License validation: added message in case of Zscaler SSL inspection being detected as license tempering attempt

\- Shared model link: added opened models to recent models list

\- Markdown documentation: enhanced heading numbering to level+1

\- Erwin XSD import: added handling of conceptual models with FK relationships missing attributes on either side

\- JSON Schema: added import and reference of format property of string data type

\- BigQuery: added dialog to handle non-existing dataset and connection issues

\- Db2: added schema name before index name in CREATE INDEX script

\- Collibra: allowed re-connection with basic auth if user's OAuth token has expired

\- OpenAPI, Swagger: added possibility to create model-driven API schema components or definitions without a template, and choose the target version

\- Oracle: added schema name before index name in CREATE INDEX script

\- Snowflake: added possibility to export individual table scripts

\- SQL Server: optimized queries WHERE clause using selected tables

&nbsp;

New features in v7.9.0 \[29-Nov-2024\]

\- Share model link URL: added ability to share link to view model in browser directly from Git repo provider (currently only from github.com and GitHub Server, plus Azure DevOps Repos) \[assumes that users of the link have a valid license and proper access to the model repo\]

\- Browser deployment: added synchronization of license data across all tabs and instances when user validates/updates/releases license key

\- Excel import: added validation that the Excel file corresponds to the model GUID

\- License status: rearranged order of wmic and PowerShell checks to accommodate Windows deprecation of wmic and installations where PowerShell is disabled administrator

\- JSON Schema: added handling of reference resolution for custom properties with enableForReference=true&nbsp;

\- Polyglot: fixed display at different zoom levels for supertype/subtype half circle relationship connector

\- Save Obfuscated As: added taking into account the model name format in Tools \> Options \> General

\- Workgroup: allowed for background check of commits when SSH key is protected by a passphrase

\- Collibra: replaced JWT authentication with more generic OAuth for Microsoft Entra ID, Okta and other identity provider

\- DeltaLake/Databricks: added view column comments to column\_list

\- Graph targets (Cosmos DB Gremlin, Janusgraph, Neptune, Neo4j, Tinkepop): fixed disappearance of subnode arrow after changing relationship type

&nbsp;

New features in v7.8.6 \[22-Nov-2024\]

\- Polyglot impact analysis: added highlight legend plus ability to control whether highlights are displayed or not

\- Save Obfuscated As: added the word obfuscated in the model file name to avoid any desire to overwrite the original file

\- Save As: removed GUID changes when saving model as a new name

\- Model-Driven API generation: added possibility to create Swagger or OpenAPI file without specifying a template

\- Avro, JSON, Parquet, Protobuf: refactored to use our hackolade fetch http handler for S3 interactions in case of proxy

\- Elasticsearch: adjusted creation of default fields as children of \_source object instead of root

\- Oracle: added parsing grammar for quoted default directory names, plus parsing of default in TO\_DATE in index functions

\- SQL Server, Synapse: added reverse-engineering of cross-schema views

\- Synapse: enhanced robustness of partitions reverse-engineering

\- Synapse: removed extraneous logic for memory-optimized properties

&nbsp;

New features in v7.8.5 \[15-Nov-2024\]

\- Tech refresh of Electron (v33.1.0), NodeJS (v20.18.0), Chromium (v130.0.6723.91), V8 (v13.0) and related modules

\- Persisted data model files: decreased indent of .hck.json files to reduce model size on disk

\- DDL reverse-engineering: added warning dialog when syntax is invalid (Db2 dialect)

\- Excel import: ignored Display Name entries for data types where irrelevant

\- Amazon DocumentDB, DynamoDB, Neptune-Gremlin: upgraded related packages to latest, plus eliminated redundant setDependencies module

\- CockroachDB, Db2, Delta Lake/Databricks, Hive, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, YugabyteDB: added possibility to export composite primary keys and unique keys to Excel

\- CockroachDB, PostgreSQL, YugabyteDB: suppressed varchar default length when creating new column

\- SQL Server, Synapse: disabled connection test for MFA auth method to avoid confusion

\- SQL Server, Synapse: ignored default port number when parsing NamedInstance from connection string

\- Snowflake: filtered column definitions in DDLs for Iceberg tables when catalog is external (glue, iceberg files, iceberg rest, delta files)

\- Synapse: optimized queries for indexes and memory-optimized tables during reverse-engineering

\- Synapse: injected missing parameter for username/password auth method

\- Synapse: suppressed extraneous Windows authentication method

\- Synapse: added tolerance for missing table information during reverse-engineering process

&nbsp;

New features in v7.8.4 \[08-Nov-2024\]

\- Open data model: added possibility, both in browser and desktop, to open a model directly from Azure DevOps repository without need for local clone, provided adequate license and repo credentials

\- Command-Line Interface: added default (to All) for --selectedViews argument of polyglotDerive command

\- Compare \& Merge: increased speed of delta model generation for large models

\- DDL reverse-engineering: added warning dialog when syntax is invalid (Oracle dialect)

\- DDL reverse-engineering: adjusted reverse-engineering of Oracle DDL file when foreign-key relationship references a parent table missing the schema information

\- Excel template: disabled primary key, composite primary key, and composite unique key columns

\- JSON/YAML preview: improved performance of JSON Schema generation for huge entity

\- Object Browser: improved performance when navigating or searching plus right-click contextual menu

\- Polyglot: added possibility, when updating references, to select view not previously derived&nbsp;

\- Polyglot: suppressed false positive in Impact Analysis screen when updating references for inheritance of subtypes

\- Workgroup: enhanced UX to generate Azure DevOps Repos personal token in case of missing organization name

\- Azure SQL: added error handling to forward-engineering test button

\- Amazon EventBridge, Glue Data Catalog, Redshift: refactored connection to leverage own implementation to fetch proxy request handler

\- Synapse: optimized query to retrieve partitions, plus refactored connection logging

&nbsp;

New features in v7.8.3 \[01-Nov-2024\]

\- Open data model from Git repo provider: added a search box for repos and for files within repo folders

\- Open data model from GitHub: added rate limiting message if too many requests have been submitted

\- Excel import: added choice to automatically perform orthogonal distribution at end of process

\- Excel import: added handling of container-level primary keys

\- Graph view: allowed adjustment of node size without affecting container size

\- Polyglot impact analysis screen: removed false differences for technical names when deriving from polyglot with no coupling or technical-to-business naming convention

\- Naming conventions: eliminated false positives on object name validation when suppressing name coupling

\- XSD reverse-engineering: added default to the normalize XSD complex type control to better fit the structures of different sources

\- Command-Line Interface: added --source argument to revEngXSD command to leverage source-specific logic and default for the normalization of XSD complex type argument

\- Command-Line Interface: added --selectedViews argument to polyglotDerive command

\- RDBMS forward-engineering: adjusted DDL generation of data type for referenced definitions

\- Db2, Oracle, SQL Server: added escaping of quotes in DDL comments forward-engineering

\- Redshift: upgraded related packages to latest, eliminated redundant setDependencies module

\- SQL Server: allowed composite keys in out-of-line DDL to have only a single key declared

\- Azure SQL, Synapse: extended logging to include Azure Entra grant consent if declined

&nbsp;

New features in v7.8.2 \[25-Oct-2024\]

\- Open data model: added Tools \> Options \> General parameter so user can choose preferred source

\- Replaced deprecated WMIC library for retrieval of Machine ID by WMI execution via PowerShell

\- ERD: added ability to move multiple entities via drag-and-drop into a container

\- JSON Schema forward-engineering: added source keyword to Extended and compliance keyword to both Full and Extended

\- External references: added possibility to reference JSON Schema files if all data types are defined according to the specification (not extended)

\- Neo4j: updated SDK to v4.4 which includes support for Neo4j database versions **5.x, 4.4, 4.3, 4.2, 4.1, 4.0**, 3.5, and deprecates connections versions up to 3.4 included

\- Neo4j: refactored node labels fetching for better handling of empty node labels, plus added extra logging

\- Neo4j: refactored node label querying in case of multi-database instance

\- MongoDB: moved resolution of mongodb+srv connection string to separate library to handle empty URI parameters

\- Oracle Excel export-import: changed the column title for Business Name from JSON Key

\- Azure SQL, Synapse: allow username/password authentication without ClientId, with multi-tenant Hackolade Studio app in Azure requiring just admin consent

&nbsp;

New features in v7.8.1 \[18-Oct-2024\]

\- Open data model: added possibility, both in browser and desktop, to open a model directly from GitHub repository without need for local clone, provided adequate license and repo credentials

\- Performance: optimized rendering of entities with references in Object Browser and ER diagram

\- Table references: added possibility to deactivate a table which is a reference to an external definition while containing a foreign key relationship

\- Polyglot: added detection of change in view select statement to Impact Analysis screen when updating derived target model references

\- Polyglot: added dialog when converting target model with views to polyglot, asking user if views should be converted or not

\- Polyglot: enhanced handling of subtype primary keys during derive into target model if subtype contains a composite primary key

\- Collibra: added support for publishing of recursive model definitions and User-Defined Types

\- Collibra: added CSRF token to all requests where applicable

\- PowerDesigner: added support for reverse-engineering of root-level packages in LDM models&nbsp;

\- XSD reverse-engineering: added selection of source to better address the different XSD formats of different legacy data modeling tools

\- XSD: adjusted reverse-engineering of composite PKs and FKs in XSDs generated out of Erwin

\- Workgroup: changed GitLab link to new page for getting personal tokens

&nbsp;

New features in v7.8.0 \[11-Oct-2024\]

\- Desktop deployment: tech refresh of Electron (v32.2.0), NodeJS (v20.18.0), Chromium (v126.0.6613.178), V8 (v12.8) and related modules

\- Polyglot: re-introduced views so they could be derived into different target models (except for MongoDB and Duality views of Oracle 23ai)&nbsp;

\- Polyglot: enhanced handling of subtype primary keys during derive into target model&nbsp;

\- Collibra: created custom config with foreign master relationship assetTypeId

\- Collibra: temporarily skip recursive model definitions when publishing

&nbsp;

New features in v7.7.11 \[04-Oct-2024\]

\- Desktop deployment: tech refresh of Electron (v31.6.0), NodeJS (v20.17.0), Chromium (v126.0.6478.234), V8 (v12.6) and related modules

\- File watcher: isolated FileSystem watcher into dedicated utility process

\- ERD: added uk abbreviation when column has single unique constraint (already present for composite unique key constraints)

\- Collibra: added support for publishing model with duplicate FK relationship names

\- MongoDB: added tolerance in resolution of mongodb+srv connection string to handle empty URI parameters

\- CockroachDB, Db2, DeltaLake/Databricks, Hive, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, SQL Server, Snowflake, Teradata, YugabyteDB: added logic so unique key and primary key constraints are mutually exclusive

\- Snowflake: added support for dynamic tables

\- Snowflake: added reverse-engineering of Iceberg tables including column information when catalog is Snowflake

&nbsp;

New features in v7.7.10 \[27-Sept-2024\]

\- Installer: added support for Windows arm64 -- application not yet optimized for this processor architecture

\- Browser: added new option File \> Open From to allow future additions of opening models directly from Git repository providers

\- Browser: added&nbsp; ability to open a model by drag-and-drop into File \> Open From... screen

\- Excel import: added filtering of ERDVs from erwin when named \<model\>

\- PowerDesigner import: added conflict resolution with choices to merge, replace or keep both when importing into an existing model

\- Avro: added default in schema forward-engineering to enable resolving entity references

\- Glue Data Catalog: added reverse-engineering of table and column comments

\- Oracle: added timeout on fetching sequence DDL, and fallback to graceful degradation

\- Oracle: added filtering of sequences and synonyms that are not used by the tables or views being reverse-engineered

\- Oracle: added support for ON NULL clause for column default value&nbsp;

\- CockroachDB, Db2, DeltaLake/Databricks, Hive, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, SQL Server, Snowflake, Teradata, YugabyteDB: added possibility for a foreign key relationship to reference a parent column with a (composite) unique key constraint, even if it is not a primary key&nbsp;

\- Snowflake: normalized dependencies for external, iceberg, dynamic, and transient table options (requires core application upgrade)

\- Snowflake: added support for Snowflake and external Iceberg catalogs (AWS Glue, Iceberg files, Delta files, and Iceberg REST) in Iceberg tables

\- Snowflake: enhanced reverse-engineering log to display table types including Iceberg

&nbsp;

New features in v7.7.9 \[20-Sept-2024\]

\- Menu: added new option File \> Open From to allow future additions of opening models directly from Git repository providers

\- File watcher: added suspend/resume background git fetch and file watchers once the app loses/regains focus

\- Performance: removed Electron background throttling so that long running processes like large reverse-engineering could continue while app is in background

\- Performance: added sizable improvement when importing numerous erwin subject areas in Excel into ERDVs of an existing or new model, when importing large number of FK relationships in Excel into large models, and when importing large Excel into large models

\- Polyglot: added possibility to rearrange sequence of subtypes

\- ERDVs: fixed calculation of container size when views are on the edge

\- Collibra: added automatic configuration for missing custom Hackolade scope

\- Collibra: adjusted publishing of lineage creation resource IDs via collibraMetadata

\- Avro, JSON, Protobuf: adjusted creation of schema registry connections in reverse-engineering

\- Cassandra, CockroachDB, Db2, MariaDB, MySQL, PostgreSQL, ScyllaDB, Snowflake, SQLServer, Synapse, Teradata, YugabyteDB-YSQ: added commenting of trailing comma if last attribute is deactivated

\- CockroachDB, PostgreSQL, Redshift, YugabyteDB: disabled wrapping of CURRENT\_USER in quotes

\- Db2, DeltaLake/Databricks, Glue, Hive, MySQL, Redshift, Snowflake, Synapse, Teradata: added automatically mark of PK as Not Null

\- Oracle: enhanced support for auth with Oracle Wallet - no longer need to declare service name

&nbsp;

New features in v7.7.8 \[14-Sept-2024\]

\- Polyglot: added automatic setting of NOT NULL property if attribute is marked as Primary Key

\- PowerDesigner reverse-engineering: added the possibility to merge a PD LDM file into an existing model

\- Avro: suppressed false positive validation warning about missing default in choices (oneOf, anyOf, allOf)

\- Db2: added commenting of deactivated columns in forward-engineering of views

\- DeltaLake/Databricks: added support for Runtime 15, including support for Variant and Object data types

\- DeltaLake/Databricks: added commenting of deactivated columns in forward-engineering of views

\- DeltaLake/Databricks: added checkbox to activate DROP statements in ALTER scripts of delta model

\- MongoDB: added commenting of deactivated columns in forward-engineering of views

\- Oracle: upgraded to latest client SDK&nbsp;

\- Oracle: added automatic setting of NOT NULL property if column is marked as Primary Key

\- PostgreSQL: added support for new mandatory SSL setup when connecting to RDS or Aurora with SSH tunneling

\- ScyllaDB: added commenting of deactivated columns in forward-engineering of views

\- Snowflake: enhanced support of tags by adding a dropdown property listing tags previously created for the schema

\- Snowflake: added reverse-engineering of tags

\- Snowflake: added filter of empty tags in DDL generation if allowed\_values is specified

&nbsp;

New features in v7.7.7 \[06-Sept-2024\]

\- Browser: added possibility to open the Hackolade Studio Desktop application from link URL *hck://* when functionality is not available in browser

\- Forward-Engineering tab: added shortcut icon in top right corner linking to dialog to forward-engineer script to file without need to go through menus.

\- Oracle: defaulted new columns to data type varchar2

\- Snowflake: removed false positives in Impact Analysis screen when refreshing references to external definitions

\- Snowflake: added quoting around tag names in UNSET statement of ALTER script

&nbsp;

New features in v7.7.6 \[31-Aug-2024\]

\- Community Edition: added object count in banner, maintained as objects are added or deleted from model

\- External definitions: fixed type when object is replaced by table-level definition

\- Db2: added clearing of collation properties when locale is changed

\- Glue: upgraded to AWS SDK v3 in order to allow to use ElectronFetchHttpHandler in case of proxy\
\- Oracle: added WHERE clause at root table level of 23ai Duality Views

&nbsp;

New features in v7.7.5 \[23-Aug-2024\]

\- Browser deployment: disabled recent models for browsers without File System Access API support (Brave, Firefox, Safari)

\- Desktop deployment: fixed file watcher on Windows for paths where folder name starts with a number

\- Diagram Objects pane: added ? icon linking to online documentation

\- Object Browser: disabled replace tab in read-only viewer edition

\- PowerDesigner import: added summary dialog during reverse-engineering

\- Collibra: automatically configured default scopes based on choice of auth provider

\- Plugins: removed deprecated cleanDependecy keyword

\- Avro, Cosmos DB Gremlin, Delta Lake/Databricks, EventBridge, MariaDB, OpenAPI, Oracle, PostgreSQL, YugabyteDB: removed from persistence default options changed by user

\- Oracle: fixed issue with insufficient privileges when applying creation of Duality Views to instance

\- Snowflake: added support for CLUSTER BY property in materialized views

\- Snowflake: added support for dynamic tables

&nbsp;

New features in v7.7.4 \[16-Aug-2024\]

\- Browser deployment: added warning in Health Check screen about preferences not being preserved if user is in guest/private/incognito mode

\- Browser deployment: added warning modal when saving a model but browser does not support File System Access API (Brave, Firefox, Safari) and falls back to downloads&nbsp;

\- ERD: adjusted size of container according to toggling of Annotations in Display Options

\- ERDVs: adjusted size of container according to ERDV membership and moving of attributes

\- Command-Line Interface: adjusted folder name in forwEng command when structured path preference is selected

\- Foreign key constraint names: replaced blanks with underscores for compliance where necessary

\- External definitions: enhanced performance for refresh of references

\- Plugin Manager: added troubleshooting link in case list of plugins is empty due to blocking of our repos

\- Collibra: made connection settings entry easier for JWT authentication with Azure AD/Microsoft Entra ID or OKTA SSO authorization

\- Polyglot: added adapter and improved performance of undo/redo operations in models with external or polyglot references

\- Polyglot: fixed restoring attributes when deleted in source model but user chooses to keep them anyway during Impact Analysis

\- PostgreSQL: added support for SET DEFAULT in ALTER COLUMN script

&nbsp;

New features in v7.7.3 \[09-Aug-2024\]

\- Documentation generation: added support for rendering of Markdown inline images in textarea properties

\- Polyglot: added vector data type with subtype and dimension, currently derivable in Cassandra 5+, Elasticsearch 8+, Oracle 23ai+, and others to come

\- Compare \& Merge and Polyglot Impact analysis: added lineage tab

\- Polyglot Impact Analysis: added detection of name changes in UDTs/model definitions

\- Polyglot Impact Analysis: added handling of relationships deleted in Polyglot model but user chooses to retain them in derived model

\- Collibra: added support for JWT JSON Web Token authentication

\- BigQuery, Hive, PostgreSQL, YugabyteDB-YSQL: adjusted default names of Foreign Key relationships to avoid blanks - also native and other targets

\- Cassandra, CosmosDB-with-Gremlin-API, EventBridge, Glue, HBase, Hive, JanusGraph, MarkLogic, Neo4j, Neptune-Gremlin, ScyllaDB, Tinkerpop: added maintainable and reusable instance disconnect flow

\- Glue: changed entity-level config to allow partition keys not be primary keys if set so

\- Snowflake: added support for Cluster By property in materialized views

\- Snowflake: updated syntax highlighting in forward-engineering of DDL script tab due to Snowsight changes

&nbsp;

New features in v7.7.2 \[02-Aug-2024\]

\- CLI: added command to import diagrams into Hackolade models, starting with PowerDesigner

\- PowerDesigner: added possibility to bulk import files with the Command-Line Interface

\- PowerDesigner: set isActivated by default for attributes

\- Undo/Redo: stabilized Redo action when appending attribute

\- File Watcher: adjusted behavior of git actions when multiple instances, plus isolated in dedicated utility process

\- ERD: fixed error when moving an annotation box when Hide database views display option is enabled

\- ERD: fixed issue with dangling relationship lines when display options are changed back and forth

\- Collibra: replaced fetching of relations during reverse-engineering from REST API to GraphQL API to reduce number of calls to instance

\- Collibra: added conflict resolution logic when reverse-engineering into existing model

\- MongoDB: skipped resolution of index labels for model definitions

\- Delta Lake/Databricks: added forward-engineering of cross-schema foreign key relationship constraints

\- Hive: added forward-engineering of cross-schema foreign key relationship constraints

\- Oracle: added option to choose to generate DDL with either quoted identifiers or non-quoted identifiers

\- Oracle: added workload analysis form for 23ai Duality Views

\- Oracle: added relationship quantification form for array subqueries in 23ai Duality View

\- Snowflake: added choice for DDL script in either Snowsight syntax (default) or previous classicUI

\- Snowflake: added escaping of special characters in Snowsight syntax

\- Snowflake: added parsing of NULLS in ORDER BY view statements

\- Snowflake: added forward-engineering of cross-schema foreign key relationship constraints

&nbsp;

New features in v7.7.1 \[26-Jul-2024\]

\- Model validation: added handling of cross-target references to external definitions for entities and attributes

\- PowerDesigner import: added mapping determination for user-defined types with only length defined

\- Delta Lake/Databricks: added detection of whether Unity Catalog is enabled or not during reverse-engineering

\- Delta Lake/Databricks: reverse-engineering of column with nullable string, when it contains serialized JSON payload

\- Glue Data Catalog: added mapping of partition keys

\- Glue Data Catalog: added indicators in ERD for partition keys and clustering keys

\- Glue Data Catalog: enabled same target reference to external table at entity level

\- PostgreSQL: added tolerance for and filtering of empty indexes in forward-engineering of ALTER scripts

\- Snowflake: added support for tags in properties of tables, columns, and views, plus forward- and reverse-engineering, and alter scripts

&nbsp;

New features in v7.7.0 \[19-Jul-2024\]

\- Browser: added deployment of Read-Only Viewer Edition at https://studio.hackolade.com -- requires a Viewer Edition license

\- Desktop deployment: tech refresh of Electron (v31.2.1), NodeJS (v20.15.0), Chromium (v126.0.6478.127), V8 (v12.6) and related modules

\- Upgraded to latest version of parcel file watcher v2.4.1

\- ERD: automatically add entities when creating a container, and automatically add attributes when creating a new entity

\- ERD: allowed parameter to determine the number of attributes to automatically add when creating a new entity

\- BigQuery: adjusted generation of time unit partitioning for columns with DATE data type

\- Cosmos DB with SQL API: allowed to fetch target script during documentation generation

\- Glue Data Catalog: allowed to reverse-engineer columns specified with no data type

\- Glue Data Catalog: upgraded to the latest version of thee aws-sdk library

\- Snowflake: proper display of variant data type in ERD

&nbsp;

New features in v7.6.1 \[12-Jul-2024\]

\- Collibra: added publishing of lineage relations between logical Polyglot models and their derived physical targets for all their assets (model/schema, entity/table, attribute/column)

\- Collibra: added dialog to remind user to save the model after publishing in order to persist Collibra internal asset IDs for lineage purposes

\- Compare and Merge: adjusted handling of merging attributes with multiple data types

\- ERD: adjusted logic to display data type abbreviation when made of type+subtype+synonym

\- Entity JSON/YAML Preview: added shortcut buttons to access forward-engineering generation to file for JSON Schema and JSON sample data

\- Model validation: added rules and warning badges for polyglot references if applicable

\- Model validation: optimized performance for rendering of warning badges in very large models (thousands of FK relationships)

\- Polyglot: added adapter to auto-fix models converted from target models with erroneous custom properties configuration

\- BigQuery, Cassandra, CockroachDB, Db2, Hive, MariaDB, MySQL, Oracle, Parquet, PostgreSQL, Redshift, ScyllaDB, SQLserver, Synapse, YugabyteDB: enabled same target reference to external table at entity level

&nbsp;

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

\- ERD: added a collapsible Diagram Objects section above the Object Browser to easily add objects

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

