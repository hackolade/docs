# v8.x

New features in v8.3.9 \[22-Aug-2025\]&nbsp;

\- Delta Lake/Databricks: aligned global option for Request Timeout with the custom deferred requests to Databricks API

\- Delta Lake/Databricks: included cluster metadata in logs while fetching the databases info

\- ERD: ensured that UK and AK markers remain for attributes involved in multiple composite keys, when composite keys are removed or updated

\- ERDVs: added possibility to select only a subset of all subtypes of a supertype

\- ERDVs: adjust container size when relationship is manually extended beyond container boundaries

\- Excel: hardened checks during import for key constraints referring to non-existent attributes

\- Glue Data Catalog: added support for AWS Glue 3.0, plus added support for Iceberg tables

&nbsp;

New features in v8.3.8 \[15-Aug-2025\]&nbsp;

\- Compare \& Merge: improved message to clarify when no alter script is generated in delta model via CLI due to no changes impacting the database

\- ERDV: adapted all ERDVs to accurately reflect changes when an entity is moved to another container which is initially not present in the ERDV

\- ERDV: added adapter to redraw relationships based on shortest path between entities while keeping the anchor position on each entity boxes

\- Polyglot: added display of block and group custom properties for derived relationships

\- XSD reverse-engineering: set “resolve references” to true by default for Erwin source

\- Avro: added use of UDT technical name for schema forward-engineering when referencing UDT Enums

\- BigQuery, CockroachDB, Db2, Hive, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, SQL Server/Azure SQL, Synapse, Teradata, YugabyteDB: added possibility for views to be based on another view (not just on a table)

\- PostgreSQL: added support for single unique constraint options in the alter script of delta models

\- SQL Server/Azure SQL: removed extraneous space in comment formatting of DDL forward-engineering

\- Snowflake: extend ability to select more file extensions (.pem, .p8, .crt, .cert) when setting up key-pair authentication

\- Snowflake: added more user-friendly message in case of missing or invalid passphrase when setting up key-pair authentication

\- Synapse: removed extraneous ASC keyword in generated script

\- Synapse: added reverse-engineering of (composite) Unique Key constraints

&nbsp;

New features in v8.3.7 \[12-Aug-2025\]&nbsp;

\- Print Diagram: added rendering of relationships in ERDV when generating PDF Hi-Res image

\- SQL Server/AzureSQL: added adapter when DB version is downgraded from 2025, converting JSON data type into nvarchar with hasMaxLength:true

\- Synapse: removed extraneous ASC keyword in Primary Key DDL statement

&nbsp;

New features in v8.3.6 \[08-Aug-2025\]&nbsp;

\- Collibra: added support for integration with non-Ultimate Collibra instances (those with Scopes disabled) allowing model publishing through extended global assignments and custom attribute types

\- Custom properties: fixed false positive undeclared for native property “error”

\- Documentation: improved ERD diagram views to utilize the full page and fit document

\- ERDV: improved container resizing behavior when entity is moved to another container

\- Polyglot: added display of block and group custom properties for derived objects

\- Delta Lake/Databricks: added tolerance for MASK and RELY keyword in column constraints

\- Snowflake: added support for key-pair authentication in connection to instances

\- SQL Server/Azure SQL: display attribute data type "json" in ERD

&nbsp;

New features in v8.3.5 \[01-Aug-2025\]&nbsp;

\- Mermaid added reverse-engineering of attributes on both sides of FK relationships through inference, given that they are not specified in Mermaid ER code

\- Mermaid: added Command-Line Interface support with command -revEngDiagram and argument --source=mermaid

\- ERD: adjusted font of entity title bar when zooming out to sketchy level

\- Polyglot: enhanced handling of name coupling during updates of references

\- Polyglot: enhanced model derive process to prevent multiple references to the same Polyglot model, and prompt user for Impact Analysis screen

\- Print Diagram: improved performance of PDF generation for large models by reducing the SVG file size significantly

\- Print Diagram: adjusted positioning of relationship names in SVG exports to ensure that all names are displayed above the relationship lines

\- Print Diagram: added auto-zoom of Graph Diagrams to fit full page

\- Delta Lake/Databricks: added possibility for views to be based on another view (not just on a table)

\- Delta Lake/Databricks: added support for CLUSTER BY keyword in reverse-engineering

\- SQL Server/Azure SQL: added support for v2025, including native JSON data type

\- SQL Server/Azure SQL: added automatic generation of FK constraint name if none is specified by user

&nbsp;

New features in v8.3.4 \[25-Jul-2025\]

\- ArchiMate: added forward-engineering of object descriptions (models, containers, entities, relationships, ERDVs)

\- Mermaid: added possibility to reverse-engineer ER diagram code from copy/paste with Clipboard

\- Mermaid: added possibility to reverse-engineer ER diagram code from Git remote location

\- Mermaid: added possibility to reverse-engineer ER diagram code from drag-and-drop of one or more .mmd files

\- Mermaid: added reverse-engineering of entity and attribute comments that start with %%

\- Mermaid: added possibility to reverse-engineer Mermaid ER diagram code files with .mmd extension with the Command-Line Interface revEngDiagram --source=mermaid

\- PowerDesigner import: added tolerance for inconsistencies with PD specification when PDM file is generated from Erwin

\- PowerDesigner import: added support for physical diagrams within packages

\- Print Diagram: added possibility to generate vector image in Hi-Resolution PDF, allowing legible output even at 6400% zoom in Acrobat Reader

\- Print Diagram: improved empty canvas space trimming

\- Constraints: added an adapter to set properties correctly after a PK/unique constraint ambiguity was created by user in Excel, plus added verification during Excel import to prevent such cases

\- Avro: added handling of JSON Schema enum values when field is converted into an Avro enum

\- CockroachDB: enhanced JSON Schema forward-engineering to only expose additionalProperties property when its value is false; added support for v24.x and v25.x

\- Db2: enhanced JSON Schema forward-engineering to only expose additionalProperties property when its value is false; added support for v12.x

\- MariaDB: enhanced JSON Schema forward-engineering to only expose additionalProperties property when its value is false; added support for v11.x

\- MySQL: enhanced JSON Schema forward-engineering to only expose additionalProperties property when its value is false; added support for v9.x

\- PostgreSQL: added support for v17.x

\- Snowflake: added possibility for views to be based on another view (not just on a table)

\- SQL Server/Azure SQL: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: “In CREATE statement”, “In separate statement” or “Ignore”), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

&nbsp;

New features in v8.3.3 \[18-Jul-2025\]

\- ERD: enhanced ERD performance when scrolling/zooming/moving entities and rendering large number of relationships

\- ArchiMate: added forward-engineering of supertype/subtype relationships as a Specialization relationship type

\- Collibra: added handling of conflicting signature when creating relation type

\- Mermaid: added handling for conflict resolution when importing entities with same name as existing

\- Avro: added handling for reverse-engineering of JSON Schema with multi-type complex types that are required

\- Delta Lake/Databricks: adjusted encoding of dots and spaces in FK relationship names in DDL forward-engineering

\- Delta Lake/Databricks: added PK constraints in separate statements as part of script generation configuration

&nbsp;

New features in v8.3.2 \[11-Jul-2025\]

\- Mermaid: added possibility to import (reverse-engineer) models in Mermaid ER diagram code, often created from GenAI prompts, cfr https://hackolade.com/help/GenAI-createdMermaidERdiagram.html

\- Licensing: added seat synchronization with desktop so that browser does not validate an extra seat on same machine

\- ArchiMate: added possibility to select ER Diagram views to be generated in ArchiMate file

\- Browser: added tolerance for opening models saved with a later plugin version than deployed

\- JSON Schema: added tolerance for http in $schema keyword when resolving references across different drafts&nbsp;

\- Polyglot: added warning badge in case of constraint with empty name

\- EventBridge, GraphQL, OpenAPI, Swagger, PostgreSQL, YugabyteDB: moved comma position in forward-engineered DDL in case of warning comment about invalid constraint name

\- Delta Lake/Databricks: added tolerance for special characters and formats in Unity Catalog tags

\- Delta Lake/Databricks: placed NOT NULL constraints in ALTER statements before PK constraints

\- Delta Lake/Databricks: applied script generation options also to views and schema comments

\- Delta Lake/Databricks: resolved schema name on using the ALTER Schema COMMENT

\- Delta Lake/Databricks, PostgreSQL, YugabyteDB: enhanced JSON Schema forward-engineering to only expose additionalProperties property when its value is false

\- Glue Data Catalog: enabled feature to infer PKs and FKs

\- Snowflake: added properties IF NOT EXISTS and OR REPLACE for views and linked to forward- and reverse-engineering processes

&nbsp;

New features in v8.3.1 \[04-Jul-2025\]

\- ArchiMate: added shared model link URL in output file to easily open models in Browser directly from third-party interface

\- ArchiMate: added generation of an ArchiMate view for main ERD

\- ArchiMate: added Command-Line Interface possibility with forweng command to generate data object file in .archimate format (argument --outputtype=archimatemodel) or Open Exchange .xml format (argument --outputtype=openexchange)

\- ERDV: allowed users to expand style block and disable auto-positioning

\- Open From: added ability to search for repositories in Bitbucket Data Center

\- Workgroup: added support for Azure DevOps Repos cross-organization token management

\- BigQuery: added authentication through GCP Application Default Credentials

\- Collibra: added to Command-Line Interface command forwEngDataDictionary the support for selective configuration publication and updates based on whether the Guided Stewardship feature is enabled in Collibra instance

\- Delta Lake/Databricks: introduced flexibility in script generation for controlling constraints in ALTER scripts of delta models

\- Delta Lake/Databricks: added ability to change global script generation options directly from the forward-engineering features (lower tab and via Forward-Engineer menu).

\- OpenAPI: enhanced forward-engineering to only expose additionalProperties property when its value is false

&nbsp;

New features in v8.3.0 \[27-Jun-2025\]

\- Archimate: added possibility to generate data object file in .archimate format or Open Exchange .xml format for containers, entities, and relationships of any model, to be imported in Enterprise Architecture tools

\- Licensing: refactored logic as a library so it can be shared across Studio Desktop, Studio Browser, and Model Hub

\- Open From: added ability to check for remote changes to retrieve latest changes, if any, to model opened directly from remote repo

\- Open From/Save To: added possibility to save model in different location than where it was originally opened from

\- Save To: added possibility, both in browser and desktop, to save a model directly to Bitbucket Data Center repository without need for local clone, provided adequate license and repo credentials

\- Polyglot: enhanced visibility of annotations on the Entity-Relationship Diagram after adding them via the impact analysis

\- Verify Data Model: added possibility to select specific user-defined regular expression rules for verification

\- Relationships: allowed removal of FK constraints from Properties Pane of child attribute

\- Relationships: added metadata in the Properties Pane for all data types that could be in a PK or FK constraint

\- Workgroup: added support for AzureDev Ops cross-organization connection tokens

\- Collibra: updated publishing configurations to comply with new validation rules

\- Collibra: added selective configuration publication and updates based on whether the Guided Stewardship feature is enabled in Collibra instance

\- Delta Lake/Databricks: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: “In CREATE statement”, “In separate statement” or “Ignore”), controllable from Tools \> Options \> Forward-Engineering parameters

&nbsp;

New features in v8.2.3 \[20-Jun-2025\]

\- Open data model: added possibility, both in browser and desktop, to open a model directly from Bitbucket Data Center repository without need for local clone, provided adequate license and repo credentials

\- Share model link URL: added ability to share link to view model in browser directly from Bitbucket Data Center assumes that users of the link have a valid license and proper access to the model repo\]

\- Share model link: enabled creation of shareable links for models in the Files screen and History screen of the repository context

\- Polyglot: enhanced Convert \& Merge feature to maintain derived objects in target model

\- Polyglot: added confirmation checkbox for breaking the link with Polyglot, ensuring users acknowledge the irreversible nature of this action before proceeding

\- PowerDesigner: enabled bulk resizing of entity boxes after reverse-engineering to ensure full visibility of all entities

\- Verify Data Model: added new out-of-the-box rule for detecting missing primary keys in entities

\- Verify Data Model: added new out-of-the-box rules for annotations

\- Workgroup: added OAUTH authentication with Azure EntraID for Azure DevOps Repos

\- Teradata: clarified error message when unable to connect to instance

&nbsp;

New features in v8.2.2 \[13-Jun-2025\]

\- Browser deployment: added possibility to forward- and reverse-engineer with BigQuery instance (given the proper license key)

\- Workgroup with GitLab (Cloud \& Server): added possibility to save data model directly to remote repository (i.e. without need for a locally-cloned repo) either by committing to the current branch or to a new branch

\- Workgroup with Bitbucket Cloud: added possibility to save data model directly to remote repository (i.e. without need for a locally-cloned repo) either by committing to the current branch or to a new branch

\- Workgroup: added possibility to create, push, and delete tags for Viewer Edition users

\- Open From/Save To: added memory of last location and filter used when same action was last executed

\- Verify Data Model: added ability to define custom rules using regular expressions (regex) for out-of-the-box and custom root scalar properties of objects: model, container, entity, view, relationship, and attribute

\- PostgreSQL: added handling for derive of arrays from Polyglot as columns with Array type in PostgreSQL

\- Snowflake: improved reverse-engineering of Views in DDL to support FULL JOIN and FLATTEN() in the SELECT AS statement

\- Teradata: added logging information to facilitate troubleshooting when connecting to an instance

&nbsp;

New features in v8.2.1 \[06-Jun-2025\]

\- Verify Data Model: added more than a dozen new out-of-the-box rules, at various levels: model, container, entity, view, and attribute

\- Browser deployment: added possibility to open current model in the Desktop client.&nbsp; Requires that model was opened via shareable link or directly from the remote repo with Open From \[works only for WIndows and Mac -- not Linux\]

\- Share Model link: added possibility to open model link in the Desktop client.&nbsp; Requires that model was opened via shareable link or directly from the remote repo with Open From \[works only for WIndows and Mac -- not Linux\]

\- Workgroup with Azure DevOps Repos: added possibility to save data model directly to remote repository (i.e. without need for a locally-cloned repo) either by committing to the current branch or to a new branch

\- Save To: added possibility to save new model to an empty repo to facilitate first commit process

\- Save To dialog: added clickable link to remote repo to easily access the remote repository

\- External references: added option to view and forward-engineer JSON Schema with resolved or internal definitions for entity references

\- Polyglot: added conversion of JSON Schema pattern fields from a target physical model to polyglot

\- Polyglot: promoted variant to its own data type so that it can be derived in Snowflake with embedded structure

\- Polyglot: promoted JSON to its own data type so that it can be derived in PostgreSQL and Oracle with embedded structure

\- Polyglot: clean-up irrelevant dependent properties in persisted model file when changing data type

\- Collibra: enhanced publishing to accommodate handling of complex relationships

\- Delta Lake/Databricks: added timezone\_ntz data type in Runtime 15 and up

\- GraphQL: optimized rendering performance of Object Browser

\- Snowflake: enhanced conversion of Object and Array data types to maintain their original structure during the Polyglot convert

&nbsp;

New features in v8.2.0 \[30-May-2025\]

\- Tech refresh of ElectronJS (v36.3.1), NodeJS (v22.15.1), Chromium (v136.0.7103.113), V8 (v13.6.233.10) and related modules

\- Excel: enhanced reverse-engineering so that cleared custom properties update model

\- Polyglot: allowed to convert to Polyglot from an ERDV tab

\- Open From/Save To: added warning when saving a model if it has been removed on the remote in the meantime

\- Open From/Save To: adjusted auto-merge of model metadata to reduce chances for conflicts

\- Open From/Save To: adjusted auto-merge to keep by default the remote model metadata (right-hand pane in conflict resolution screen)

\- Collibra: updated disclaimer text to clarify that existing assets will be updated with model information, emphasizing the need for reverse-engineering from Collibra before proceeding with forward-engineering

\- Delta Lake/Databricks: added handling for NaN (Not a Number) when applying bulk test data to instance

\- Snowflake: adjusted derive and convert of variant data type from and to Polyglot for new derived models only

&nbsp;

New features in v8.1.8 \[23-May-2025\]

\- Workgroup: added possibility in Bitbucket Data Center (previously known as Bitbucket Server) to follow a Fork \& Pull innersourcing strategy&nbsp;

\- Workgroup: improved model refresh in editor after resolving merge conflicts

\- Workgroup: added fetching remote tags when executing PULL action

\- Open From/Save To: enabled review of changes when newer remote modifications are detected, with possibility to merge current changes with remote changes&nbsp;

\- Open From/Save To: extended functionality to manage conflicting remote changes by introducing several options: Solve conflicts, Keep only incoming changes, Keep only local changes, and Create new branch

\- Open From: added title indication (remote) or (remote, read-only) for models opened from remote sources

\- Core application: introduced possibility to define a deployment policy configuration allowing to disable user access to the application updates dialog

\- Excel: enhanced reverse-engineering to allow changes in relationship custom properties

\- Model validation: added detection of duplicated object names inside an entity at model opening

\- Polyglot: made app tolerant to the absence of refIdPath in view column when deriving from polyglot

\- Polyglot: enhanced impact analysis screen to detect and allow addition of subtypes during update of references, as well as removal of supertypes

\- Polyglot: improved visibility of superclasses properties in relationships Properties Pane when custom properties are added

\- Relationships: improved registration of nested parent/child attributes in Properties Pane, plus enhanced consistency when using drag-and-drop

\- Collibra: normalized logging of publishing flows

\- Cassandra, CosmosDB-with-Mongo-API, CouchbaseV7Plus, DeltaLake/Databricks, GraphQL, JanusGraph, Neo4j, ScyllaDB, Snowflake: enhanced IPv6 compatibility in URL parsing

\- Cassandra, CouchbaseV7Plus, DocumentDB, Glue, Hive, MarkLogic, Neo4j, Oracle, SQLServer, ScyllaDB, Snowflake, Synapse: moved system and connection logging from each plugin and consolidated into core application

\- Delta Lake/Databricks: increased reliability of bulk test data generation on Windows when temporary file in removed during the process of applying to instance

\- GraphQL: optimized rendering performance of ERD and type definitions tab by reducing memory usage and handling of deeply nested definition attributes

\- GraphQL: improved performance of SDL generation for large models

&nbsp;

New features in v8.1.7 \[16-May-2025\]

\- Workgroup: added possibility in Azure DevOps Repos to follow a Fork \& Pull innersourcing strategy&nbsp;

\- Workgroup: added possibility in Bitbucket Cloud to follow a Fork \& Pull innersourcing strategy (support for this feature with Bitbucket Data Center will be added in an upcoming release)

\- GraphQL: added possibility to reverse-engineer, from the Studio browser deployment, SDL files and introspect from URLs

\- PowerDesigner: added reverse-engineering of Abstract Data types of PDM files into user-defined types/model definitions

\- Collibra: added publishing of shared model link in URL attribute of logical model or physical schema asset type, provided that the published model version has been pushed to the Git repo (Workgroup Edition only)

\- Collibra: enriched logging of authentication and other connection events

&nbsp;

New features in v8.1.6 \[09-May-2025\]

\- Browser deployment: added possibility to forward- and reverse-engineer with Delta Lake/Databricks instance (given the proper license key)

\- Documentation: added further performance enhancements by using React Server-Side Rendering and closing intermediary windows when no longer needed

\- ERD: added keyboard shortcut and View menu option to resize all visible (Windows: Alt+Shift+Right Arrow, Mac: Option+Shift+Right Arrow) or selected entity boxes (Windows: Alt+Right Arrow, Mac: Option+Right Arrow) to fit to content

\- Forward-Engineering: added logging for connection test

\- Graph View: enhanced positioning of edge-less nodes so they appear closer in the canvas to other nodes in the same container, as force-directed layout cannot apply to edge-less nodes

\- Polyglot: added support for derived identity properties in blocks

\- Print diagram: enhanced to handle ERDVs without relationships

\- Save To: forced creation of branch when changes on remote have been detected since model was loaded

&nbsp;

New features in v8.1.5 \[02-May-2025\]

\- DDL: enhanced reverse-engineering of DDLs when AsSelect statement contains more than CREATE VIEW statements

\- Documentation: added handling of maximum call stack due to recursion

\- ERD: added performance enhancements to take into account view/hide of Object Browser Pane and Properties Pane

\- License Status: added meaningful error message for when computerId does not match

\- License Status: show proper error message when key is validated using Windows Remote Desktop RDP

\- PowerDesigner: enabled where-used option in contextual menu for user-defined types/model definitions reverse-engineered from domains

\- PowerDesigner: added mapping of extendedAttributes of domains to custom properties of user-defined types/model definitions

\- UX: added keyboard shortcut to move between tabs of the add/modify connections dialog and in the Plugin Manager: Windows/Linux: fwd: Ctrl+Tab, rev: Ctrl+Shift+Tab; Mac: fwd: Cmd+Option+right arrow, rev: Cmd+Option+left arrow

\- Workgroup: renamed "Bitbucket Server" into "Bitbucket Data Center", still using v1 of the Bitbucket APIs

\- MongoDB: updated driver to latest version of SDK v6.16.0 and BSON v6.10.3 libraries, which disable Field-Level Encryption and Kerberos support -- contact support@hackolade.com if needed

\- MongoDB: added support for using AWS IAM for MongoDB Atlas authentication to reduce the number of authentication mechanisms and number of secrets to manage

\- SQL Server: added encryptConnection and ssh values to reverse-engineering log file

&nbsp;

New features in v8.1.4 \[25-Apr-2025\]

\- Share model link: made all shareable models editable, relying on the license key to enforce whether the model is editable or not, and on the Git repo right to enforce whether the commit should be allowed or not

\- Share model link: modified URL structure so that models are no longer in read-only mode

\- Save To: allowed saving models with Cyrillic and other special characters

\- DDL reverse-engineering: added tolerance for missing semi-column (";") at the end of the last statement

\- ERD: added 25% performance enhancements for models with large number of entities

\- Polyglot: added handling of relationships deletion through removal of parent entity prior to deriving into physical model

\- PowerDesigner: added reverse-engineering of domains in CDM, LDM, and PDM files into user-defined types/model definitions

\- DDL reverse-engineering: added tolerance for missing semi-column (";") at the end of the last statement

\- Cosmos DB w/ Gremlin API, JanusGraph, Neptune, Tinkerpop: updated Gremlin client API and patched it to make it compatible with NodeJS 22, plus added ipv6 ssh URL wrapping

\- GraphQL: enhanced logging for reverse-engineering

\- Hive: added validation of Composite Unique Key name

\- Snowflake: added possibility to narrow down selection to a single schema when configuring reverse-engineering connection, to avoid fetching entire warehouse

&nbsp;

New features in v8.1.3 \[18-Apr-2025\]

\- Workgroup: added possibility to create a sub-folder on the remote repo during the Save To operation

\- Workgroup: improved breadcrumbs with truncating and ellipses in Open From and Save To dialogs to accommodate for lengthy folder names and deep nesting

\- Workgroup: added display of full names of remote repositories in the drop-down of local repositories

\- Workgroup: changed icon for removing repositories from the list, to clarify that the repo is not deleted

\- Documentation: enhanced image generation to include relationships in ERDVs drawn outside container perimeter

\- Suggest denormalization: added support for case when multiple relationships to/from one attribute and lineage capture is enabled

\- Polyglot: enhanced Impact Analysis screen in OpenAPI derived model when model definition is removed in parent model

\- XSD: added handling of primary keys and data types in polyglot models when reverse-engineering from Erwin XSD

\- CockroachDB, Db2, Delta Lake/Databricks, Hive, Oracle, PostgreSQL, Teradata, YugabyteDB: added support for Alternate Keys

&nbsp;

New features in v8.1.2 \[11-Apr-2025\]

\- Workgroup: added possibility to save data model directly to remote repository (i.e. without need for a locally-cloned repo) either by committing to the current branch or to a new branch.&nbsp; Currently only with GitHub (.com and Enterprise on-prem server).&nbsp; Other providers in upcoming releases.

\- Workgroup: added possibility in GitLab to follow a Fork \& Pull innersourcing strategy&nbsp;

\- Workgroup: added possibility to compare from the tags screen the commits associated with 2 arbitrary tags&nbsp;

\- Workgroup: added deletion of&nbsp; local Git tag when deleting it on remote

\- Workgroup: enhanced tags screen so table titles don't disappear when scrolling

\- Workgroup: added possibility to resize Commit Hash and Commit Date columns in tags screen

\- Workgroup: added automatic selection of specific commit in history screen when selecting Show in History View from tags screen

\- Workgroup: don't subscribe to model changes if file is opened from history screen

\- Command-Line Interface: added command extRefUpdate to update external references of a selected model

\- Custom properties: added handling of defaultValue in cross-level dependencies

\- DDL reverse-engineering: added performance enhancements&nbsp;

\- ERD orthogonal distribution: added performance enhancements and reduction of memory requirements

\- PowerDesigner: added a more tolerant data type matching with Levenshtein algorithm (level 2) when importing PDM files with custom data types or for unsupported targets

\- Polyglot: added handling of enum data type and its values when deriving into physical targets with enum data type

\- Polyglot: added conversion into model definitions when deriving into physical targets that don't support internal definitions&nbsp;

\- DocumentDB: added extra helper information in reverse-engineering Collection Selection dialog when AWS credentials do not allow to establish connection

\- GraphQL: added reverse-engineering from .graphql (or .gql) files

\- GraphQL: added reverse-engineering with schema introspection of URL endpoint

\- Snowflake forward-engineering: adjusted statement sequence for dynamic tables based on SELECT AS

&nbsp;

New features in v8.1.1 \[04-Apr-2025\]

\- Browser: reduced loading time substantially when opening model from Open Shared Link

\- License management: refactored to clean up old Software Key Validation screen replaced by License Status screen, including RDP fine-tuning of computerID

\- Polyglot: implemented taking into consideration custom defaultData when deriving from Polyglot

\- PowerDesigner: added support for reverse-engineering CDM files

\- Workgroup: enhanced the error dialog when creating illegal branch names or tag names, to display the validation rules having failed evaluation

\- Workgroup: enriched tag screen with additional metadata: commit hash, author, timestamp, and message

\- Workgroup: added possibility to push, delete, and checkout a tag as a new branch

\- Workgroup: adjusted connection creation host placeholder to better match the known online Git provider domains

\- CockroachDB, Db2, MariaDB, MySQL, Oracle, PostgreSQL, Snowflake, YugabyteDB-YSQL: added mapping to target-specific maximum length when importing from DDL, referencing external definition, or deriving from Polyglot where char or nchar has MAX length

\- DocumentDB: enhanced extended logging for AWS-related credentials

\- Snowflake: changed sequence of CREATE TABLE statements in DDLs so that regular tables are created first, and before dynamic tables

&nbsp;

New features in v8.1.0 \[28-Mar-2025\]

\- Tech refresh of ElectronJS (v35.0.3), NodeJS (v22.14.0), Chromium (v134.0.6998.44), V8 (v13.4) and related modules

\- Workgroup: added support for creation of Git tags from Tags screen and from History screen

\- Workgroup: added possibility to show tags and consult tag metadata in History screen

\- Open From repository: restricted possibility to trial, Workgroup, and Viewer editions

\- BigQuery, CockroachDB, Db2, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, Teradata, YugabyteDB-YSQL: added mapping to target-specific maximum length when importing from DDL, referencing external definition, or deriving from Polyglot where varchar or varbinary has MAX length

\- DocumentDB: added tolerance for missing credentials when fetching instance metadata

\- DocumentDB: added ipv6 addresses enclosing in square brackets

\- MongoDB: adjusted parsing of mongodb+srv string

\- Oracle: enhanced reverse-engineering of column comments when referencing schema in name

\- Snowflake: enhanced reverse-engineering to accommodate dynamic tables

\- Teradata: added maximum length of 64000 to char, varchar and varbyte

&nbsp;

New features in v8.0.6 \[21-Mar-2025\]

\- dbt: added forward-engineering via Command-Line Interface forwEng command&nbsp;

\- Generate documentation: changed default parameters in Tools \> Options \> Documentation to reduce size by deselecting less often used sections

\- Command-Line Interface gendoc: changed command default arguments: --attribTree (complex only), --properties (not empty), --sepContDiag (false), --jsonSchema (false), --jsonData (false)

\- PowerDesigner: added reverse-engineering of user tag, mapping it to Hackolade container/schema/group/bucket/database/namespace/keyspace/...

\- PowerDesigner: added mapping from SAP SQL Anywhere data types long binary, double, and variable characters to SQL Server

\- PowerDesigner: added more information about reverse-engineering progress, plus enhanced performance of ERDV rendering

\- Print diagram and Documentation generation: disabled GPU hardware acceleration for rendering diagrams in PNG and SVG formats

\- Avro: enhanced user experience in browser when configuring connection to a schema registry instance in the cloud (CORS reverse-proxy)

\- Avro: added possibility to reverse-engineer .avro binary files in browser

\- BigQuery: added connection enhancement to accommodate self-signed certificates in proxies

\- Hive: adjusted adjusted complex datatype and array datatype column in dbt forward-engineering

\- Snowflake: added tolerance in DDL reverse-engineering for non-compliant syntax declaring a column NULL property

&nbsp;

New features in v8.0.5 \[14-Mar-2025\]

\- Model opening: handled additional causes for false positives of model metadata changes

\- JSON Schema: added reference resolution for modified UDT properties

\- JSON Schema: fixed mapping of exclusiveMin/Max boolean across draft-04 and later drafts with numeric representation

\- Polyglot: fixed derive of exclusiveMin/Max properties when target JSON Schema spec is draft-06 and higher

\- PowerDesigner: added reverse-engineering of .pdm files for targets not supported by Hackolade (e.g.: SAP SQL Anywhere)

\- XSD reverse-engineering: added tolerance for missing xs: namespace prefixes

\- DeltaLake/Databricks: added reverse-engineering of materialized views from file and from instance&nbsp;

\- EventBridge, OpenAPI, Swagger: prevented referencing of external definitions at request and response level to force using component schemas

\- GraphQL: enabled append/insert options in contextual menu for scalar and enum types

\- PostgreSQL: added support for materialized views

&nbsp;

New features in v8.0.4 \[07-Mar-2025\]

\- dbt: enabled forward-engineering of models properties schema.yml files for Hive, MySQL, Oracle, SQL Server, and Teradata tables

\- dbt: added materialization strategy in model property files

\- dbt: forward-engineer only root attributes for complex data type in BigQuery, Databricks, Glue Data Catalog, and Hive

\- Model opening: fixed model change false positives caused by validation of selected objects

\- PowerDesigner reverse-engineering: added mapping of MAX length for varchar data type in MySQL, Redshift, SQL Server, and Synapse

\- Tech: added ESM enforcement by webpack for CI-CD folder

\- Avro: allow main app to control the root type behavior and handle multiple data types

\- Avro: added display of array item name in ERD

\- Avro: added \* in ERD for not-nullable union schemas

\- Avro: adjusted data type of default value of numeric fields when derived from Polyglot

\- DeltaLake/Databricks: added support for materialized views

&nbsp;

New features in v8.0.3 \[28-Feb-2025\]

\- browser deployment: added possibility to forward- and reverse-engineer with Confluent Schema Registry in Avro plugin (given the proper license key)

\- dbt: enabled forward-engineering of models properties schema.yml files for BigQuery, Amazon Glue Data Catalog, PostgreSQL, Redhift, and Synapse tables

\- dbt: added possibility to generate a single models property file per schema/container/dataset

\- GraphQL: prevented appending or inserting a field in a choice of a union

\- Documentation generation: improved performance and reduced memory footprint for large models

\- PowerDesigner: reverse-engineer of .pdm files into Hackolade physical models of any target, currently except for API targets: EventBridge, GraphQL, OpenAPI, and Swagger that require additional development

\- PowerDesigner reverse-engineering: added fractional seconds precision for datetime attributes

\- Tech: added ESM enforcement by webpack for app folder

\- Tech: ensured that software is fully functional in IPv6-only environments.&nbsp; And no claimed capabilities are invalidated if operated in a dual stack (Ipv6 and IPv4) network environment

\- Avro: re-ordered properties when data type is multiple for a more logical sequence

\- DeltaLake: changed plugin logo to Databricks for better recognition

\- Snowflake: improved character escaping in comments when characters are already escaped

&nbsp;

New features in v8.0.2 \[21-Feb-2025\]

\- dbt: enabled forward-engineering of models schema.yml files for DeltaLake/Databricks tables

\- dbt: add constraints at table and column levels when forward-engineering of models schema.yml files

\- GraphQL: enabled auto-generation of SDL in Browser deployment

\- GraphQL: added Append/Insert/Add field for union type via contextual menu

\- Custom properties: added validator of proper JSON upon loading application

\- Polyglot: added representing in ERD the configured sequence of reordered keys in composite primary key for models derived from polyglot

\- Polyglot: updated relationships in target model on update of Polyglot definitions if they were changed in the Polyglot model

\- MacOS: fix for rendering of a complex ERD image in documentation

\- Oracle: added handling of additional keywords to ANTLR grammar for reverse-engineering: GREAD ONLY, GENERATED BY DEFAULT, EDITIONABLE

\- Snowflake: added tolerance for escaped single quote inside table comments during reverse-engineering

&nbsp;

New features in v8.0.1 \[14-Feb-2025\]

\- dbt: first release of basic forward-engineering of models schema.yml files for Snowflake tables.&nbsp; Will be enhanced with additional features and additional targets in upcoming releases

\- Docker: enhanced detection that application is running in Docker image for latest Linux versions and distributions, and alternate container management tools

\- Excel: enhanced adapter handling more permutations of (composite) primary keys during reverse-engineering

\- Faker: upgraded to latest library version v9.5.0.&nbsp; Beware of breaking changes in Faker functions https://github.com/faker-js/faker/blob/next/CHANGELOG.md and https://fakerjs.dev/guide/upgrading.html#breaking-changes-to-specific-methods

\- Tech: finished migration of all modules to ESM

\- DynamoDB: allowed views (used for facets and secondary indexes) to have partition and sort keys that are different than for the underlying table

\- GraphQL: added grouping of root types (Query, Mutation, Subscription)&nbsp;

\- GraphQL: adjusted order of types in forward-engineered SDL

\- GraphQL: added possibility to define structured directives

\- GraphQL: adjusted order of directive locations&nbsp;

\- Oracle: added generation of ALTER script for changes in table-level check constraints

\- Oracle: added generation of ALTER script for changes in column data type changes as well as changes in properties: length, precision, offset…

\- Oracle: extended the commenting in ALTER scripts to more potentially destructive statements such as modification of data type, shorter columns, etc.

\- PostgreSQL: moved sequence creation statements to the beginning of the DDL script

\- Snowflake: moved sequence creation statements to the beginning of the DDL script

\- Synapse: updated config with synonyms for proper reverse-engineering from PowerDesigner

&nbsp;

New features in v8.0.0 \[07-Feb-2025\]

\- GraphQL: added plugin which is currently limited to allowing definition of non-root types and auto generation of GraphQL Schema Definition Language SDL.&nbsp; More enhancements in the coming weeks to achieve model-driven GraphQL API generation

\- Excel export/import: implemented composite key constraint definitions at entity level

\- Polyglot: allowed to disable Bold font option in derived models

\- PowerDesigner: reverse-engineer of .pdm files into Hackolade physical models of the same target, or in a Polyglot model

\- Properties Pane: enabled apply button in textarea when copy/paste

\- Properties Pane: allowed display of business name in dropdown of parent/child entity of relationships, when technical name display option is selected but entity has no technical name

\- Collibra: adjusted reverse-engineering to accommodate Collibra API return code changes

\- Avro: adjusted resolution of references on definitions with multiple types.  

\- Avro: arranged order of field properties when it is a reference on definition with multiple type

\- Couchbase v7+: added tolerance to reverse-engineering parsing for unmanaged (undefined) statements

\- SQL Server: added synonyms to improve data type mapping for PowerDesigner PDM files

\- Snowflake: eliminated redundant table joins in views DDLs

\- Snowflake: added support for templates in view Select statement property with SELECT ${viewColumns} for dynamic list of columns

\- Snowflake: added support for views \<column\_list\> to allows column name alias and comments

&nbsp;

&nbsp;

&nbsp;

&nbsp;

