# v8.x

New features in v8.9.1 \[30-Jan-2026\]&nbsp;

\- ERD: improved container resize when it contains derived annotations

\- Excel: added attributes and FK relationships creation based on name references when no GUID is present

\- Graph View: added resizing control for edge boxes

\- Mermaid: updated library to latest version 11.12.2

\- PowerDesigner: added support for reverse-engineering of sub-packages

\- PowerDesigner: added validation of PD extended attributes against Studio custom properties configuration

\- PowerDesigner: added warning for unsupported ExtendedComposition tags

\- Collibra: improved relation type recognition during forward-engineering

\- Cosmos DB with SQL API: suppressed partitionKey declaration if not specified in model

\- Cosmos DB with SQL API, Cosmos DB with Gremlin API: added explicit option "/\*" for included paths in index settings

\- Db2: added support for view changes in ALTER script of delta model

\- Db2: added support for table changes, inclusive columns, in ALTER script of delta model

\- Db2: added script with comments on Activated/Inactivated entities (table, view, column) successfully applies to DB2 instance&nbsp;

\- Oracle: added support for SUBPARTITION in Properties Pane, forward- and reverse-engineering

&nbsp;

New features in v8.9.0 \[23-Jan-2026\]&nbsp;

\- Polyglot: introduced flexible modeling for relationships, allowing gradual refinement from conceptual to logical phases.&nbsp; More info at https://hackolade.com/help/ConceptualtoLogicalwithPolyglotr.html

\- Relationships: changed Foreign Master relationship lines from dashed to dotted, so as to leave dashed lines for non-identifying relationships

\- Documentation generation: refactored to dynamically reflect the configuration in the Properties Pane

\- Excel: enabled reverse-engineering in unsaved models when the Excel file does not contain references to other models

\- Collibra: stopped running parallel GET requests to the Collibra API to ease load on customer server

\- Collibra: added retry logic if the fetch request runs into error net::ERR\_INCOMPLETE\_CHUNKED\_ENCODING

\- Avro: ensured appropriate name validation after derivation from Polyglot

\- BigQuery: added support for choice of file granularity when generating DDLs: per model, per schema, or per table

\- BigQuery: added support for defining Unique and Alternate Keys (Natural Keys) as modeling metadata documentation

\- Cosmos DB: improved reverse-engineering to ensure correct conversion of unsupported types within union definitions

\- CosmosDB with SQL API: removed extraneous Binary data type to ensure compliance with native JSON data types

\- CosmosDB with Gremlin API, JanusGraph, Neo4j, Neptune, Tinkerpop: updated for compatibility with new Polyglot references when derive from and convert to Polyglot

\- Snowflake: updated SDK and lodash libraries, plus replaced Axios with proxy fetch library, plus reordered log file

\- Synapse: added resolution of model definition references in DDL forward-engineering through hydration of objects

&nbsp;

New features in v8.8.5 \[16-Jan-2026\]&nbsp;

\- License: enabled offline validation for license keys when using Windows Remote Desktop (RDP)

\- Polyglot: added possibility to derive edge relationships into another Polyglot model

\- Polyglot added alternate key indexes in ERD entity box for referenced and derived entities

\- Collibra: added detection of pagination type for fetching configurations in Collibra

\- Collibra: improved relation type recognition during forward-engineering

\- Avro: added support for unresolved named type when the field references a record derived from Polyglot

\- Db2: enabled ALTER script in delta model

\- Db2: enabled feature to apply DDLs and ALTER scripts to instance

\- Db2: added support for reverse-engineering of constraints when specified separately

\- PostgreSQL: added CREATE VIEW statement in alter script of delta model

\- PostgreSQL: added support for comment on VIEW column in generated DDL

\- PostgreSQL: enhanced forward-engineering to escape special characters in comments using 'E' only when necessary

\- Snowflake: added extra logging and a default port value to the configuration to assist with browser redirection issues

&nbsp;

New features in v8.8.4 \[09-Jan-2026\]&nbsp;

\- ERDVs: ensured that symbols (annotations and rectangles) are preserved during reverse-engineering from Excel

\- Command-Line Interface: added support for converting models to Polyglot data models via polyglotConvert command and related arguments

\- Compare and merge: improved rendering and merging of supertype groups

\- Custom Properties: resolved false alert regarding undeclared custom property "multipleParentType" for array items

\- General: improved handling of default path location in file picker to select a file other than a data model (open and save)

\- Impact Analysis: enhanced rendering of entities in tree view when changed to a subtype

\- Impact Analysis: changed default checkbox state behavior when an entity is changed to a subtype

\- Object Browser: added a delete option in the contextual menu for relationships

\- Polyglot: enhanced handling of supertype groups during updates of Polyglot definitions

\- Polyglot: resolved error when updating Polyglot definitions after changing an entity to a subtype while also modifying existing attributes to references

\- Suggest Denormalization: enhanced flexibility in embedding options by leveraging relationship cardinalities to determine whether to use arrays or sub-documents

\- Collibra: introduced configurable attribute-level lineage mapping, allowing to choose between direct simple relation and the (default) complex mapping specifications

\- Cosmos DB with SQL API, Cosmos DB with MongoDB API: added support for multiple types with complex types to eliminate need for oneOf constructs, plus updated libraries and dependencies

\- Db2: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu, plus plus updated libraries and dependencies

&nbsp;

New features in v8.8.3 \[02-Jan-2026\]&nbsp;

\- General: refactored default path location in file picker when selecting SSL/SSH certificates

\- Forward-engineering: improved handling of default path location in file picker when selecting target files

\- Reverse-engineering: improved handling of default path location in file picker when selecting data model

\- Avro: improved forward-engineering by generating type as reference for referenced records in union branches

&nbsp;

New features in v8.8.2 \[26-Dec-2025\]&nbsp;

\- General: improved handling of default path location in file picker to select a data model

\- Object Browser: ensured that relationships name color matches those in ERD and Graph Diagram

\- ERD: added name of oneOf choices in entity boxes and object browser

\- ERDVs: ensured that relationships line style from ERD is preserved when creating new ERDV

\- Persistence: added adapter to remove extraneous empty arrays of complex props

\- Avro: added support for unions with named types, with unique names for records, enums, and fixed types to better comply with Avro specs during forward-engineering

\- Avro: improved derivation of Polyglot supertype-subtype into oneOf in Avro, using inheritance names as oneOf choice names

\- Cassandra: added adjustment for handling partitioning keys

\- Delta Lake/Databricks: added adjustment for handling clustering keys

\- ScyllaDB: added adjustment for handling partitioning and clustering partition keys

&nbsp;

New features in v8.8.1 \[19-Dec-2025\]&nbsp;

\- Tech refresh of ElectronJS (v39.2.7), NodeJS (v22.21.1), Chromium (v140.0.7444.235), V8 engine (v14.2.231.21), and related modules

\- Polyglot: introduced automatic generation of associative entities for many-to-many relationships during derive operations into Polyglot and RDMBS targets

\- References: enabled "Replace by Attributes" functionality in the Properties Pane for Internal, Model, and External references

\- Glue, Hive: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

\- Hive: added support for Hive 4.x as the default version

\- BigQuery, CockroachDB, Db2, DeltaLake/Databricks, Hive, MariaDB, MySQL, Oracle, PostgreSQL, Redshift, Snowflake, SQLServer, Synapse, Teradata, YugabyteDB-YSQ: introduced automatic generation of associative entities for many-to-many relationships during derive operations into Polyglot and RDMBS targets

&nbsp;

New features in v8.8.0 \[12-Dec-2025\]&nbsp;

\- Desktop application: achieved 30% performance increase when opening the first instance of the application, by migrating bundling

\- Linux: added SHA-256 checksum file in download S3 folder

\- Archimate: added support for forward-engineering of complex custom properties of derived modeling objects

\- Polyglot: added support for relationships custom color in Graph view

\- PowerDesigner: handled missing single primary keys during reverse-engineering of Physical Data Model files (pdm) when structure differs from previously encountered

\- PowerDesigner: added support for different format for cardinality during reverse-engineering of PDM files

\- References: added visible attribute level $ref property with path to a definition

\- References: allowed to create (also change, refresh, and open in a separate instance) a reference at attribute level via the $ref property in Properties Pane

\- Views: enhanced properties handling and rendering of attributes marked as Primary Keys in underlying table

\- XSD: improved handling of duplicated descriptions in Erwin XSD files

\- Oracle: corrected return type of view alter scripts function

\- Oracle: added support for named NOT NULL constraints in ALTER scripts

&nbsp;

New features in v8.7.2 \[05-Dec-2025\]&nbsp;

\- ArchiMate: added support for forward-engineering of scalar custom properties at model and entity level in Open Exchange file format

\- ArchiMate: added support for forward-engineering of complex custom props and relationships in both ArchiMate and Open Exchange file formats

\- Custom properties: added ability to declare them for relationships in modelLevelConfig file

\- Display options: added support for composite unique keys constrains

\- Excel: added support for cross-repository references in forward-engineering and in reverse-engineering, whereby $ref path is exported as defined in the model instead of being converted to absolute path

\- Forward-engineering: adjusted compliance in generated JSON sample data, addressing boolean property types, additional properties, and handling of \`oneOf\` constraints

\- Object Browser: added highlight of selected relationship, for consistency with other objects

\- Reverse-engineering: enhanced performances by optimizing number of parallel workers for JSON data parsing based on available memory and CPU resources

\- Workgroup: added support for sub-groups in GitLab (cloud \& server) across all features: Open From, Generate Shareable Link, Save To, and Remote References

\- Oracle: added support for removal of primary and unique key constraints in ALTER scripts

\- Oracle: added support for removal of comments in ALTER scripts

\- Oracle: added support for updating properties of datetime attributes in ALTER scripts

\- PostgreSQL: ensured that definition names (UDTs) with special characters (including forward slashes) are correctly resolved throughout DDL generation process

&nbsp;

New features in v8.7.1 \[01-Dec-2025\]&nbsp;

\- Documentation: suppressed sidecar windows consuming unnecessary processes and memory

&nbsp;

New features in v8.7.0 \[28-Nov-2025\]&nbsp;

\- Remote references: added possibility for cross-repository references to models (Polyglot or external) in a remote location, across different repositories and repository providers

\- Memory management: reduced memory footprint of application by 300 MB when opening a model

\- Browser: added possibility to create and refresh external and Polyglot references

\- ArchiMate: added support for forward-engineering of scalar custom properties at model and entity level in ArchiMate file format (not yet complex custom props, and not yet Open Exchange file format)

\- Command-Line Interface: enabled --properties argument in genDoc command

\- Documentation: added $ref for entities with external references

\- Documentation: eliminated race condition on old and slow Windows machines

\- ERD: improved performance for models with large number of relationships

\- Properties Pane: added message when number of relationships is greater than 250

\- PowerDesigner: added reverse-engineering of technical names ("code") of foreign key relationships

\- PowerDesigner: added support for reverse-engineering views based on views

\- PowerDesigner: enhanced reverse-engineering of view SELECT statements from Erwin models by cleaning unsupported characters and unnecessary CREATE statements

\- Undo/Redo: improved functionality after model conversion

\- Collibra: adapted forward-engineering to comply with new stricter configuration rules for complex relation types

\- Collibra: added handling of publishing when custom asset types are present

\- MariaDB, MySQL: improved reverse-engineering to handle reserved keywords in comments

&nbsp;

New features in v8.6.1 \[21-Nov-2025\]&nbsp;

\- Compare \& Merge: added support for preservation of layout and colors of graph views, ERD, and ERDVs from right-hand model

\- Compare \& Merge: adjusted color coding of deleted attributes

\- ERDV print diagram: adjusted to occupy entire print area

\- Forward-Engineering: added option to skip creation of root folder named after the model, allowing for direct export of files into selected folder

\- Object Browser: enhanced search to include ERDV names

\- Polyglot: added handling of technical names and naming conventions during conversion, preserving coupling in original model

\- PowerDesigner: enhanced reverse-engineering of views generated from Erwin models

\- PowerDesigner: added handling of enums without labels

\- Command Line Interface: added support for reverse-engineering of PowerDesigner .pdm physical model files

\- Undo/Redo: fixed issue where model objects could be created with duplicate IDs after exceeding action stack limit

\- Collibra: add new checks for relation types used in assignments

\- MongoDB: restored optional relationship inference during reverse-engineering

\- PostgreSQL: adjusted timestamp data type mapping when deriving from Polyglot and converting to Polyglot

&nbsp;

New features in v8.6.0 \[14-Nov-2025\]&nbsp;

\- Polyglot: added support for technical names and naming conventions, including handling during derive operations depending on the naming conventions in target

\- Polyglot: ensured that technical names in target are preserved when updating Polyglot references while naming conventions are inactive

\- Polyglot: ensured all technical names are preserved during convert and merge, plus added validation of the target model and improved overall convert performance

\- Command Line Interface: added argument applyTargetNamingConventions for polyglotDerive command to control whether to apply the target model’s naming conventions when deriving names

\- ERDV: improved performance for basic operations, including faster entity expand, resize, move, and undo actions, along with a delay for relationship line tooltips to reduce blinking during quick mouse movements

\- Naming Conventions: unchecked "remove vowels" option by default for all targets in Desktop and Browser

\- PowerDesigner: improved reverse-engineering of views in existing models for PDM files generated from Erwin

\- PowerDesigner: improved data type mapping to Delta Lake/Databricks and JSON targets, with enhanced warnings and email notifications for unmapped data type

\- Collibra: enriched logs when publishing assignment configs

\- Oracle, SQL Server: prevented changes in target model after conversion when dependent on Polyglot

\- Oracle: improved reverse-engineering from instance to identify new Oracle 26ai version

\- Snowflake: enhanced script generation options for alter script of delta models

\- Synapse: removed extraneous -- used for commenting

&nbsp;

New features in v8.5.5 \[07-Nov-2025\]&nbsp;

\- Tech refresh of ElectronJS (v39.1.0), NodeJS (v22.21.1), Chromium (v140.0.7444.59), V8 (v14.2.231.14) and related modules

\- Compare \& Merge: improved merging of ERDVs with conflicting names

\- ERD \& ERDVs: enhanced performance of Undo actions

\- Polyglot: preserved physical properties in derived models while maintaining dependencies when converting model

\- PowerDesigner: improved reverse-engineering to handle single column references as arrays

\- Collibra: removed articulation rules from pre-defined assignments configuration in forward-engineering to comply with new validation rules at Collibra side

\- Snowflake: fine-tuned several details when applying script generation options

\- Synapse: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

\- Teradata: improved handling of canceled reverse-engineering process, plus made host field required entry

\- Teradata: added handling of reverse-engineer aborting action

&nbsp;

New features in v8.5.4 \[31-Oct-2025\]&nbsp;

\- ERD: fixed minor error in entity color picker when color was unchanged

\- Db2: replaced query statement with environment variables during reverse-engineering, plus added query to log file

\- MongoDB: added aws4 library in public package to allow AWS IAM user authentication and credentials file

\- GraphQL: add type for entity during reverse-engineering from instance

\- GraphQL: refactored deviations indicators in Object Browser for higher performance

\- Snowflake: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

&nbsp;

New features in v8.5.3 \[24-Oct-2025\]&nbsp;

\- ERDVs: added possibility to duplicate an existing ER Diagram View via contextual menu, toolbar, shortcut, or application menu

\- ERD: added warning for generating documentation and printing diagrams with empty names in modeling objects

\- Workgroup: implemented lazy loading of assignable users for pull requests to handle slow networks with timeouts and enhance performance

\- Workgroup: improved error handling when missing Git client on Windows and encountering the "spawn git ENOENT" error and directing users to relevant documentation

\- Collibra: improved performance of forward-engineering of large models

\- Collibra: added preliminary check with warning if empty names in modeling objects or out-of-canvas-bounds objects prior to publishing

\- YugabyteDB: added support for column-level check constraints

&nbsp;

New features in v8.5.2 \[17-Oct-2025\]&nbsp;

\- Tech refresh of ElectronJS (v38.3.0), NodeJS (v22.20.0), Chromium (v140.0.7339.240), V8 (v14.0.365.10) and related modules

\- Compare \& Merge: improved global performance, particularly noticeable with lineage capture

\- ERD: improved performance for zooming, scrolling, selecting, and drag-and-drop actions when handling a large number of relationships

\- ERD: improved entity addition from ERDV to ensure new entities are positioned in ERD close to existing ones within the same container

\- Excel: added tolerance for primary keys missing their key

\- Reverse-engineering: enhanced performance of selection dialog to support displaying large number of entities

\- Oracle: added version 26ai

\- Oracle: added support for renaming entities and entities in ALTER script

\- Oracle:  improved application of script generation options in ALTER script

\- PostgreSQL: improved application of script generation options in ALTER script

\- SQL Server/AzureSQL: added support for reverse-engineering of Microsoft Fabric

\- SQL Server/AzureSQL: changed auth methods from Azure AD to Entra ID&nbsp;

\- SQL Server/AzureSQL: improved application of script generation options in ALTER script

\- Synapse: added support for reverse-engineering of Microsoft Fabric

\- Synapse: changed auth methods from Azure AD to Entra ID&nbsp;

\- YugabyteDB: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

&nbsp;

New features in v8.5.1 \[10-Oct-2025\]&nbsp;

\- ERD Display Options: added new display option to toggle display of deactivated objects

\- ERD Display Options: added keeping toolbar menu open after selection, until mouse is moved out of the fram

\- Object Browser: added option in contextual menu to sort ERDVs alphabetically

\- Compare \& Merge: removed extraneous Relationships tab in lower half of screen, as information is available in more details in upper half

\- Compare \& Merge: enhanced filter "Show only differences" to hide unchanged group properties in lower half of screen

\- Compare \& Merge: added collapsing of unchanged group properties, when filter is set to "Show all properties"

\- Documentation: added tolerance during generation for missing references to external definitions&nbsp;

\- Polyglot: added possibility to define enums in UDTs so that it could be derived in CockroachDB, PostgreSQL, and YugabyteDB physical models

\- Windows installer: enhanced to provide alternative installation folder and avoid that privileges force Inno Setup to install in AppData, plus updated for Windows 10+ and x64 compatibility&nbsp;

\- Workgroup: pass the matching repository root folder when retrieving stashes and tags

\- Oracle: added fallback query to fetch table columns meta information when reverse-engineering without SELECT permission

\- PostgreSQL: added support for column-level check constraints

\- PostgreSQL:  introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: "In CREATE statement", "In separate statement" or "Ignore"), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

\- YugabyteDB: removed enum, composite, range and domain data types from the data type list to enforce user-defined types for proper declaration in generated scripts

&nbsp;

New features in v8.5.0 \[03-Oct-2025\]&nbsp;

\- Tech refresh of ElectronJS (v38.2.0), NodeJS (v22.19.0), Chromium (v140.0.7339.133), V8 (v14.0.365.4) and related modules, including fixes for excessive WindowsServer GPU usage and high CPU usage with \<input\> tag on macOS Tahoe 26

\- Security: removed false positives in ReversingLabs evaluation scan of Windows installation package

\- Cloud providers: updated AWS, Azure, and GCP SDKs to latest

\- ERD Display Options: introduced clearer Tools \> Options \> Display parameters, toolbar dropdown toggles, and View menu

\- ERD Display Options: added new display options to show only foreign keys (FK) and unique keys (UK)

\- Faker: changed evaluation of FakerJS expressions to get rid of VM2 library

\- Workgroup: removed custom commit message for squash merges, allowing the git provider to generate commit messages based on repository settings

\- Collibra: added publishing of multi-select custom properties

\- Collibra: added publishing custom properties from custom tab

\- PostgreSQL: added fallback query to fetch table columns meta information without SELECT permission

\- Snowflake: added handling of tables created from SELECT statements during reverse-engineering

\- Synapse: enhanced reverse-engineering to tolerate missing square brackets in partitioning statements

\- Synapse: adapted connection screen to replace AAD (Azure Active Directory) by Azure Entra ID, plus replaced Axios with proxy fetch library

&nbsp;

New features in v8.4.4 \[26-Sept-2025\]&nbsp;

\- Relationships: added possibility to configure in Tools \> Options \> General how business names are assembled when creating FK relationships via drag-and-drop

\- Command-Line Interface: added argument --pkAtTop to commands forwEng, forwEngAPI, forwEngXLSX

\- Diagram Objects pane: consolidated annotations and rectangles under a single symbols entry with sub-menu, plus a help icon lining to the documentation page

\- ERD/ERDV: added a placeholder in entity boxes to indicate, when display options are set hide attributes in favor of description, but description is empty

\- ERD/ERDV/Object Browser: added badge to visually indicate when an entity or attribute is deactivated

\- ERD/ERDV/Object Browser: added badge to visually indicate deviation when adding attributes in entities derived from polyglot

\- ERDV: ensured that layout remains unchanged when adding new entity via membership dialog

\- Excel: added update of container custom properties values during reverse-engineering

\- Excel: enhanced handling of numeric properties so that cleared numeric values in Excel are emptied in the model during reverse-engineering, when the model is derived from polyglot

\- Object Browser: added Symbols (currently: annotations and rectangles) in search results, and in search scope dropdown

\- PowerDesigner: added handling of geopoint attributes during reverse-engineering into Polyglot and other targets supporting that datatype; to allow array of coordinates

\- Collibra: added possibility to configure assetType mapping with custom Collibra IDs

\- Oracle: added reverse-engineering of additional table properties

\- PostgreSQL: added normalization of arrays of objects when deriving from Polyglot

&nbsp;

New features in v8.4.3 \[19-Sept-2025\]&nbsp;

\- Command-Line Interface: added revEng command argument to use index columns in sort criteria for MongoDB reverse-engineering --useIndexInSort=\< true \| false \>

\- Custom props: allowed defaultValue property for non-complex custom properties for all modeling objects in native targets

\- Documentation: improved robustness by ignoring empty custom tabs

\- ERD: created adapter to render visible hidden entities linked to non-existent containers after erroneous user manipulation in Excel

\- Excel: added support for custom properties for view attributes that can have distinct values from their underlying referenced entity attributes

\- PowerDesigner: added reverse-engineering of view technical names

\- PowerDesigner: added mapping of data type timestamptz to "timestamp with time zone" when reverse-engineering into PostgreSQL models

\- Views: enabled the creation of Views on existing View attributes that lack underlying reference, by extracting data type from SELECT statement

\- Avro: resolved schema validation about default: null when resolving reference in model derived from polyglot

\- Avro: used technical name of namespace references in schema generation

\- Avro: avoid infinite spinner due to race condition when clicking on controls before schema has been generated

\- EventBridge: enabled extensions on references

\- Snowflake: improved robustness of forward-engineering with view attributes without underlying references

\- Synapse: enabled the selection of a column as both an index column and a distribution column

&nbsp;

New features in v8.4.2 \[12-Sept-2025\]&nbsp;

\- Relationships: added technical name property with support for naming conventions

\- ERD: improved display of rectangle names when positioned at the top of a container

\- JSON Schema: mapped business names of view objects to title when technical name is present

\- Polyglot: preserved original graph view nodes layout when deriving into a graph target or into another polyglot model

\- Polyglot: added handling of relationships marked as polyglot-only when deriving

\- PowerDesigner: added support for database views

\- PowerDesigner: added disclaimer if source PDM indexes are not compatible with model target

\- PowerDesigner: added handling of tag \<a:Mandatory\> and mapped to required/not null in addition to already handled tag \<a:Column.Mandatory\>

\- Print Diagram: added attribute color coding in Hi-Res PDF

\- Workgroup: added segregation of local commits from remote commits in Review Changes screen in respectively Push and Pull screen

\- Workgroup: added support for Bitbucket Cloud connection via API tokens with scopes

\- Workgroup: added expiration date for Bitbucket Cloud deprecated connections with app password (June 9, 2026)

\- CockroachDB, CosmosDB-with-Gremlin-API, DeltaLake/Databricks, Glue, Hive, JanusGraph, MariaDB, Neo4j, Neptune, Oracle, PostgreSQL, SQLServer, Tinkerpop, YugabyteDB-YSQL: added a technical name property with support for naming conventions

\- PostgreSQL, YugabyteDB: mapped empty index method to btree during reverse-engineering

&nbsp;

New features in v8.4.1 \[05-Sept-2025\]&nbsp;

\- Compare \& Merge: introduced the ability to merge any model into previously derived models while maintaining the Polyglot link and creating deviations based on user merge choices

\- ERD and DDLs: introduced display option to disable the automatic positioning of primary keys as first columns, allowing users to arrange columns in their preferred sequence

\- ERD: introduced new color palette for objects

\- Excel: moved column subtype between columns type and logical type when exporting for an Avro model&nbsp;

\- Excel: allowed groups with absent composite keys when importing into an empty model

\- Polyglot adjusted array type adapter when converting model from PostgreSQL

\- PowerDesigner: enabled reverse-engineering of indexes from Physical Data Model (PDM) files

\- Avro: sanitized use of avsc library across components by extracting customizations and aligning the lib version to latest

\- OpenAPI: enabled extensions on references

\- OpenAPI: fine-tuned performance for reverse-engineering of larger files

\- OpenAPI: introduced an entity number threshold for collapsing reverse-engineered entity fields, enhancing performance for large schemas with over 250 entities

\- Oracle: introduced flexibility in script generation for controlling constraints in CREATE scripts (3 choices: “In CREATE statement”, “In separate statement” or “Ignore”), controllable from Tools \> Options \> Forward-Engineering parameters, plus from forward-engineering lower tab and via Tools \> Forward-Engineer menu

&nbsp;

New features in v8.4.0 \[29-Aug-2025\]&nbsp;

\- ERD: added possibility to enrich organization of diagrams with rectangle symbol, for example for visual grouping of entities

\- ERD: enabled zoom shortcuts to also work with numeric keypad keys (Ctrl++ and Ctrl+-)

\- ERDV: prevented orthogonal distribution when adding an entity to existing selection

\- Polyglot: allowed custom properties of view attributes derived from Polyglot to deviate from the props of the underlying table

\- Avro: added possibility to resolve namespace references also for external references to other Avro models

\- CockroachDB, Delta Lake/Databricks, MariaDB, PostgreSQL, SQL Server, Synapse, YugabyteDB: improved generation of ALTER script in forward-engineering when an attribute is added or removed to a composite key

\- Db2, Teradata: removed devDependencies from package-lock.json in release artifact

\- Glue Data Catalog: added support for AWS Glue 3.0, plus added support for Iceberg tables

\- OpenAPI: improved performance on reverse-engineering

\- Oracle, PostgreSQL: fixed double index statement in generation of ALTER script in case of new composite key&nbsp;

\- PostgreSQL: enhanced sequence of generated ALTER script in forward-engineering

&nbsp;

New features in v8.3.9 \[22-Aug-2025\]&nbsp;

\- Delta Lake/Databricks: aligned global option for Request Timeout with the custom deferred requests to Databricks API

\- Delta Lake/Databricks: included cluster metadata in logs while fetching the databases info

\- ERD: ensured that UK and AK markers remain for attributes involved in multiple composite keys, when composite keys are removed or updated

\- ERDVs: added possibility to select only a subset of all subtypes of a supertype

\- ERDVs: adjust container size when relationship is manually extended beyond container boundaries

\- Excel: hardened checks during import for key constraints referring to non-existent attributes

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

