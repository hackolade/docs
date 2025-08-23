# v6.x

New features in v6.11.9 \[10-Nov-2023\]

\- Command-Line Interface: added Git awareness to compMod command so you can models in a specific commit hash or in a path location, with argument --model1=\[commit:\]\[path\]\<file name\>

\- Command-Line Interface: allowed for selection of multiple containers in argument --selectedObject of command forwEngDataDictionary

\- Compare \& Merge: added ability to manage attributes moved via drag-and-drop

\- Cosmos DB with Core API: added new script format for Azure CLI so database and container creation can be executed with azureCLIPowerShell, azureCLIZsh, and azureCLIBash.&nbsp; Available on screen of GUI, forward-engineered to file, or Command-Line Interface

\- Delta Lake/Databricks: added support for DEFAULT column value in ALTER script of delta models

\- Delta Lake/Databricks: split of ADD COLUMN and SET NOT NULL in ALTER scripts of delta models

\- Snowflake: added support for parsing of QUALIFY keyword in SELECT statement defining views

&nbsp;

New features in v6.11.8 \[03-Nov-2023\]

\- MongoDB: added reverse-engineering of Relational Migrator relmig files

\- Command-Line Interface: allowed for selection of multiple containers in argument --selectedObject of commands forwEng, forwEngAPI, forwEngXLSX, polyglotDerive, polyglotUpdate, revEng

\- External references: fixed bug when lineage capture was enabled

\- Subtype/supertype: adjusted behavior so deletion of relationship no longer deletes the subtype entities

\- Avro: added possibility to generate Schema Registry script in JSON format via CLI or Tools \> Forward-Engineering

\- Delta Lake/Databricks: added support for MANAGED LOCATION argument in CREATESCHEMA statements

\- Elasticsearch: added support for flattened data type

\- Oracle: added ability to compare and merge 23c duality views

\- Snowflake: extended the UDF pane config with additional languages - java, scala, python

&nbsp;

New features in v6.11.7 \[27-Oct-2023\]

\- ERD and ERDVs: added further independence of box dimensions

\- Excel: added more detailed logging when importing ERDVs

\- Excel: added case insensitive matching of entity names when importing ERDVs

\- Command-Line Interface suppressed the need for argument --scriptType=update when model is a delta model

\- Command-Line Interface: added possibility to be invoked from Azure DevOps (requires a concurrent license key)

\- Documentation generation: added DDL of views where applicable

\- External references: changed default of file path from absolute to relative

\- Polyglot references: changed default of file path from absolute to relative

\- Model-driven API generation: changed default of file path from absolute to relative

\- Delta Lake/Databricks: added encoding names containing accented or special characters with backticks

&nbsp;

New features in v6.11.6 \[20-Oct-2023\]

\- Check for Application Update dialog: suppressed sporadic Promise Rejection Error message in some Windows 11 instances when clicking Download Now link

\- Compare and Merge: added handling of custom properties in custom tabs

\- Excel: added export/import of ERD views to allow, among other things, for migration of subject areas from erwin

\- Excel: added taking into account PKs when sorting attributes during export

\- Polyglot: added Title Case conversion option during reverse-engineering of XSD files

\- Print diagram: adjusted preview of PNG format

\- Workgroup Edition: allowed author to self-approve change request if platform allows it, as well as other actions (reject, abandon, etc.)

\- Workgroup: added display of username of timeline events in Azure DevOps Repos pull requests

\- Workgroup: added opening of models from comparison pane of change request review

\- Delta Lake/Databricks: adjusted generation of Alter script from delta model

\- Oracle: added support for partition by range with interval

\- Oracle: added support for JSON data type in versions 21c and higher

&nbsp;

New features in v6.11.5 \[13-Oct-2023\]

\- Polyglot: added possibility to set case conversion during reverse-engineering of XSD files

\- Polyglot: added warning if parent file cannot be found

\- Collibra: added custom config pushed automatically so field-level custom properties get displayed in Details tab

\- Delta Lake/Databricks: allowed Generated As properties for integer type

\- Delta Lake/Databricks: allowed nullable value in default property for DDL generation

\- Elasticsearch: added config for language analyzers, index blocks, index routing, index normalizers, and many other index properties

\- Swagger: added sorting keys for enums and required

&nbsp;

New features in v6.11.4 \[06-Oct-2023\]

\- Polyglot: added ability to handle cross-target references to external definitions

\- Polyglot: added ability to handle ambiguity in multiple data types of attributes

\- External references: added warning if definition file cannot be found

\- Excel export/import: added possibility to update custom tabs' properties&nbsp;

\- Avro: added support for namespaces in external references

\- Delta Lake/Databricks: added name property for column-level check constraints

\- Delta Lake/Databricks: added support for identity in Generated As statement, with start and increment

\- Delta Lake/Databricks: changed SQL formatter to SQLtools

&nbsp;

New features in v6.11.3 \[29-Sept-2023\]

\- Workgroup for GitHub: in addition to previously available support for shared repo strategy, added support for Fork and Pull strategy in the context of innersource methodology, with the ability to contribute PRs to an upstream parent repo

\- ERDVs: added ability to share annotations across multiple ERDVs

\- Object Browser: added decorative symbols to tree

\- Polyglot: adjusted data type conversion to JSON Schema for integer, date, time, and uuid

\- Cloud storage reverse-engineering: modified default behavior to not combine schemas

\- Excel: added export of empty columns if selected in options

\- Excel: added export of Avro doc property derived from polyglot

\- Excel: suppressed misleading warning during import&nbsp;

\- Markdown documentation: added display of key path for partition keys when derived from Polyglot

\- Databricks: added support for sequence property of integer data types plus derive from Polyglot autoincrement

\- Databricks: added support for column-level inline check constraints

\- Elasticsearch: added support for copy\_to property

\- Oracle: added support for naming conventions in Duality Views for JSON keys and subqueries

\- Oracle: added support for newly introduced IF NOT EXISTS in 23c DDL script forward-engineering

\- Snowflake: added mapping of Polyglot autoincrement to Snowflakes's identity property of integer data types

\- SQL Server: adjusted forward-engineering of ALTER script in delta models for absent properties

&nbsp;

New features in v6.11.2 \[22-Sept-2023\]

\- ERDV: disconnected resizing of entity boxes between different ERDVs when activating display option "Hide data types"

\- Command-Line Interface: suppressed requirement for Git client in Docker image

\- Polyglot: enhanced generation of JSON Schema for the multiple data types of an attribute

\- Avro: adjusted positioning of labels in dialog for forward-engineering to file

\- BigQuery: added support for extended ASCII characters

\- Elasticsearch: added runtime option in dynamic property, plus changed default value

\- Elasticsearch: allowed reverse-engineering of fields absent in document sampling but present in mappings

&nbsp;

New features in v6.11.1 \[19-Sept-2023\]

\- Oracle 23c Duality Views: added forward-engineering script generation in SQL syntax of duality views

\- Oracle 23c Duality Views: added possibility to apply duality views DDL script to instance&nbsp;

\- Oracle 23c Duality Views: added reverse-engineering of DDL file with duality views in SQL syntax

\- Oracle 23c Duality Views: added reverse-engineering from instance with duality views in SQL syntax

&nbsp;

New features in v6.11.0 \[15-Sept-2023\]

\- Oracle: added support for JSON-Relational Duality Views in version 23c

\- ERD: synchronized display in ERD when changing order of columns in composite keys

\- ERDVs: fixed condition leading to an entity belonging to more than one container after a change of container followed by a Git merge

\- ERDVs: enhanced Diagram View Editor to handle empty containers and entities

\- Excel export: added relationship parent and child attribute names in case of composite keys

\- Excel export: suppressed extraneous auto-increment setting for polyglot models

\- Lineage capture: added event for renaming objects

\- Performance enhancements: fine-tuned undo/redo logging and localization

\- Polyglot: fixed an issue with polyglot definitions making an external reference to model definitions in other polyglot models

\- Properties Pane: FK relationships dropdown lists of parent and child entities display business vs technical name according to Display Options choice

\- Avro: enhanced reverse-engineering to handle possible collisions with field names "properties" or "items that collide with syntax keywords

\- BigQuery: added tolerance for absence of PKs and FKs in public datasets

\- BigQuery: added support for allow\_non\_incremental\_definition option in materialized views

\- Delta Lake/Databricks: added escaping clause for extended ascii characters

&nbsp;

New features in v6.10.20 \[08-Sept-2023\]

\- Schema tree view: allowed drag-and-drop of reference attributes to different level in the tree

\- Compare and Merge: added support for C\&M of subtypes

\- Compare and Merge in Git conflict resolution: added handling of entities in ERDVs

\- External references: removed some false positives of additions in Impact Analysis screen

\- Polyglot: added handling of update of inserted references in target model

\- Workgroup edition: added parsing of repository URLs containing spaces

\- Avro: added support for recursive schema references for Confluent Schema Registry

\- BigQuery: added support for max\_staleness option materialized views

\- BigQuery reverse-engineering: added ability to retrieve tables separately by dataset

\- Cosmos DB with SQL API: added support for hierarchical partition keys

\- EventBridge Schema Registry: added support for OpenAPI 3.0.x extensions

\- OpenAPI: added support for extensions in array data type and components schema root items

\- Snowflake: added support for procedures in modeling, forward- and reverse-engineering

\- SQL Server: added support for PK options changes in ALTER scripts

&nbsp;

New features in v6.10.19 \[01-Sept-2023\]

\- Object Browser: added possibility to modify order of database views (where applicable) using toolbar up/down arrows

\- Foreign key relationships: added validation of technical name with Regular Expression, in particular to control max length in RDBMS targets

\- Polyglot: added default use of technical names of entities and attributes when deriving foreign key relationships

\- Polyglot: reverted transitive references to go back to direct references

\- External references: added handling of reference name changes ancestor

\- Avro: allowed absence of a Subject Name Strategy for record in Confluent Schema Registry, with possibility to edit the subject name

\- Avro: dropped validation of business name if technical name of namespace is valid

\- Elasticsearch: added support for configuration of built-in and custom text analyzers

\- PostgreSQL: removed escaping of default values of array columns in DDL generation

\- OpenAPI/Swagger: added ability to select resources and requests in yaml format forward-engineering

&nbsp;

New features in v6.10.18 \[24-Aug-2023\]

\- Object Browser: added handling of technical names for entities copied in a target model that is derived from polyglot

\- Documentation: changed image path to relative in Markdown format

\- Documentation: added possibility to filter out empty properties for all objects and Properties Pane tabs

\- Excel export: added possibility to deselect color and font properties

\- Excel export: added filtering of deselected properties for attributes of entities and views

\- Print diagram: added handling of custom canvas background color

\- Schema tree view: added preventing drag-and-drop of root

\- Avro: implemented topological sort during reverse-engineering of .avsc files with namespace references

\- Avro: adjusted filtering of special characters in forward-engineering

\- Delta Lake/Databricks: added enhancement to parsing of SELECT statement in views for jinja variables in double curly braces

\- MariaDB, MySQL, Oracle, PostgreSQL, SQL Server: added technical name max length verification for schemas, tables, and columns

&nbsp;

New features in v6.10.17 \[18-Aug-2023\]

\- ERD: added enabling auto-width and auto-height when clicking "Resize box to fit to content" button on the entity box title bar

\- Object Browser: added ability to modify order of ERDVs using toolbar up/down arrows

\- Foreign Key relationships: changed default naming logic to use technical name of entities and attributes if present, otherwise use business name

\- Properties Pane for relationships: now uses the order set in the Object Browser for both parent and child entities

\- Documentation generation: changed the order of objects to reflect order in Object Browser

\- JSON Schema forward-engineering: made array's "contains" property an object type in draft-07, 2019-09, and 202-12 specs

\- JSON Schema forward-engineering: added filtering of deactivated objects derived from polyglot

\- Polyglot: added ability to move an inserted attribute in a target model derived from polyglot

\- Polyglot: added possibility to multi-select attributes in a target model derived from polyglot

\- Avro schema preview: added split panes to display generated sample data

\- BigQuery: added replacement of illegal characters in names of FK relationships with underscores

&nbsp;

New features in v6.10.16 \[11-Aug-2023\]

\- ERD: added automatic disabling of auto-height and auto-width when adjusting entity box size

\- Plugin Manager: added plugin version in new model target picker

\- BigQuery reverse-engineering: added support for single dataset filtering

\- BigQuery: added support for derive from polyglot required property

\- MySQL: added support for fractional seconds for TIME, DATETIME, and TIMESTAMP data types

\- MySQL: added support for property and reverse-engineering of DEFAULT ON UPDATE statements

\- Parquet: added support for derive from polyglot required property

&nbsp;

New features in v6.10.15 \[04-Aug-2023\]

\- ERD: fixed reset of custom relationships when adding attributes

\- Polyglot: added possibility to add/insert/append choices into derived target models&nbsp;

\- Polyglot Impact Analysis: added possibility to (de)select deletions in Polyglot model

\- Avro: added support for namespace references

\- BigQuery: added support for Foreign Key constraints

\- Databricks: added support for PK and FK constraints in Unity Catalog, in other catalogs than hive\_metastore which does not support PKs and FKs

\- MySQL: added support for property and forward-engineering of DEFAULT ON UPDATE statements

\- OpenAPI: added possibility to forward-engineer component schemas to YAML Schema file

\- Oracle DDL reverse-engineering: adjusted mapping of NUMBER with no precision for SQL-like targets

\- PostgreSQL/YugabyteDB: added support for check constraints with multiple statements

\- PostgreSQL/YugabyteDB: added Array Type property for non-reference enums, composite, range\_udt, and domain types

\- SQL Server: added SSL Options for Windows Auth method

&nbsp;

New features in v6.10.14 \[27-Jul-2023\]

\- Polyglot: added support for naming conventions in impact analysis dialog

\- Polyglot: added support for recursive references when converting a target model to polyglot

\- Cassandra: added handling in ALTER script of delta model for changes in table comments

\- Databricks: added support for Unity Catalog

\- OpenAPI: added support for extensions at scalar field level

\- Oracle: added support for Apple Silicon chips (M1 and M2) for reverse-engineering from instance, plus updated SDK to latest version

&nbsp;

New features in v6.10.13 \[21-Jul-2023\]

\- ERD: added possibility to change the background color of the canvas

\- ERD and ER Diagram Views: added display option to show descriptions (comments for SQL targets) instead of attributes

\- ERD and Object Browser: added possibility to display incoming and outgoing relationships of an attribute via contextual menu

\- Polyglot: added fit-to-pane after derive operation

\- Workgroup: fixed commit counter after switching repo

\- Collibra: added possibility to sync descriptions of edge labels of Labeled Property Graph targets

&nbsp;

New features in v6.10.12 \[14-Jul-2023\]

\- ERD \& Object Browser: added scroll bar in contextual menu display of model definitions/UDTs

\- Excel export: added prefix to attribute tab column for custom properties tab

\- Polyglot and reverse-engineering normalization: added logic to determine cardinality based on required/not null property

\- Personal edition: added annual subscription plan

\- Avro: changed separator between namespace and name from a dash to a dot

\- BigQuery: added support for simple Primary Key and composite PK constraints

\- Collibra: added read-only license key (no publication to Collibra)

\- Delta Lake/Databricks: relaxed logic to allow selection of a column in a composite unique key even if the column is part of a partition

\- Delta Lake/Databricks: do not move columns that are part of a composite unique key constraint above the primary key line in ERD box

\- Oracle: added ability to convert auto-increment into identity for Polyglot, and for deriving auto-increment from Polyglot

\- SQL Server/Azure SQL: added support for modifications in constraints (Primary Keys, Foreign Key, check, and not null) in ALTER scripts of delta models

\- Synapse: added ability to convert auto-increment into identity for Polyglot, and for deriving auto-increment from Polyglot

&nbsp;

New features in v6.10.11 \[07-Jul-2023\]

\- Object Browser: added possibility to open entities derived from Polyglot

\- Polyglot: fixed add/insert if entity derived and selected field is a reference

\- External definitions: added handling of choices in impact analysis when refreshing references

\- Model obfuscation: added possibility to obfuscate even if model has invalid schema

\- Workgroup: silenced Git client's git-timeout error after sleep mode and machine unplugged from power supply

\- Workgroup: handled updating a Pull Request on an outdated branch

\- Avro: added detection of enums with similar names to handle them as references in avsc scripts

\- Avro: added possibility to mark reference to other CSR schema as nullable

\- Cassandra: added handling of table comment modifications in ALTER scripts

\- Collibra: added support for publication and reverse-engineering of edge labels of Labeled Property Graph targets

\- MariaDB: added generation of ALTER script for changes in comments and constraints: not null, check, primary key, and foreign key

\- SQL Server/Azure SQL: added option to forward-engineer .sql in separate file per database or per table

\- SQL Server/Azure SQL: added ability to convert auto-increment into identity for Polyglot

&nbsp;

New features in v6.10.10 \[30-Jun-2023\]

\- External definitions: added impact analysis dialog when opening model with references to external definitions (or refreshing references)&nbsp;

\- Internal and model definitions: disabled primary key and unique key properties, as this should be set at the reference level

\- Workgroup: removed redundant prompt to update open model after commit action

\- Avro: added handling of null and not null constraints when reverse-engineering DDL

\- Avro: added handling of null and not null constraints when reverse-engineering XSD

\- OpenAPI/Swagger: added template validation check when deriving from a polyglot model

\- Oracle: added reverse-engineering of synonyms from DDL

&nbsp;

New features in v6.10.9 \[23-Jun-2023\]

\- Document generation with CLI: added tolerance for markdown properties with null value

\- FK relationship creation: added tolerance for when the foreign attribute is a reference to a definition

\- Avro: handled cases when root schema replaced by string reference

\- Delta Lake/Databricks: added detection of subtype for child properties of arrays

\- Model-driven OpenAPI: added info block from template when deriving from polyglot

\- Polyglot: added handling of complex data type in field derived from Polyglot model and it is conflicting with a reserved name

\- Oracle: added support for CREATE SYNONYM syntax in forward- and reverse-engineering

\- PostgreSQL and YugabyteDB: added handling of transition between individual and composite PKs in ALTER scripts

\- SQL Server and Azure SQL: added support for deriving auto-increment from Polyglot

&nbsp;

New features in v6.10.8 \[16-Jun-2023\]

\- Print diagram: added possibility to export images to SVG format

\- Properties Pane: disabled isAvtivated property if attribute is a PK or part of composite PK

\- Faker: upgraded to latest library version 8.0.2.&nbsp; Beware of breaking changes in Faker functions https://github.com/faker-js/faker/blob/next/CHANGELOG.md

\- Avro: moved handling of custom properties at field level

\- Delta Lake/Databricks: adjusted mapping of array when deriving from polyglot without normalization

\- Oracle: added generating index script if index name is undefined

\- PostgreSQL: added support for modifications in Primary Keys and Foreign Key relationships in ALTER scripts of delta models

\- YugabyteDB: added support for modifications in Primary Keys and Foreign Key relationships in ALTER scripts of delta models&nbsp;

&nbsp;

New features in v6.10.7 \[09-Jun-2023\]

\- SQL Server and Azure SQL: added support for comments in forward- and reverse-engineering, leveraging sp\_addextendedproperty syntax

&nbsp;

New features in v6.10.6 \[07-Jun-2023\]

\- Excel: added tolerance for export of attributes with empty business name

\- MongoDB, Cosmos DB w/ Mongo API, and DocumentDB: adjusted EJSON to BSON mapping during reverse-engineering inference of ISODate

&nbsp;

New features in v6.10.5 \[02-Jun-2023\]

\- Properties Pane: added warning validation after data type change

\- Foreign Key relationships creation: added tolerance for matching of data type when child attribute has multiple types

\- Reverse-Engineering: increased sample size limit to over 800 Mb

\- XSD: added reverse-engineering of complexTypes for Sparx Enterprise Architect

\- Avro: added custom property keyword includeInScript = true if user wishes for custom property to be added to AVSC schema.&nbsp; Also handled in Reverse-Engineering from schema registry and avsc files

\- Avro forward-engineering: added resolving of schema references when generating AVSC schema outside of Confluent Schema Registry

\- Oracle: added support for materialized views, including view properties, and indexes on materialized view columns

\- Teradata: added logic to generate ALTER scripts from delta model

&nbsp;

New features in v6.10.4 \[31-May-2023\]

\- ERD: enhanced copy/paste of containers with FK composite relationships

\- ERD: adjusted copy/paste of relationships

&nbsp;

New features in v6.10.3 \[26-May-2023\]

\- Object Browser: added search by Regular Expression

\- Reverse-Engineering performance: refactored rendering to handle larger sample faster, as well as multiple JSON columns in RDBMS rows

\- Custom properties: allowed propagation when converting to Polyglot with external references

\- Custom properties: allowed custom tab at model level for Polyglot

\- Workgroup: added Merge \& Push button to branch merge (other actions) screen to simplify process

\- Workgroup: added custom message with documentation link when attempting to push to a protected branch in Azure DevOps Repos

\- Avro: removed API command from .avsc file forward-engineered when Schema Registry is not empty

\- Delta Lake/Databricks: added forward-engineering of Primary Key and Foreign Key constraints in Runtime 11 and above

\- Delta Lake/Databricks: added handling of changes in PK and FK constraints in ALTER script generation of delta models

\- Delta Lake/Databricks: added property for relationships so they appear commented in DDL forward-engineering when isActivated property is disabled

\- OpenAPI: allowed change of OpenAPI version within 3.0.x range

&nbsp;

New features in v6.10.2 \[19-May-2023\]

\- Reverse-engineering: updated tree view in selection modals

\- Reverse-engineering conflict detection: adjusted behavior of "apply to all"

\- Avro: added property "default" to complex data types

\- Databricks: added option to forward-engineer .hql in separate file per database and per table

\- Databricks: adjusted reverse-engineering of views when naming conventions enabled

\- Databricks: added handling of map\<txt\> when converting from Polyglot

\- JSON Schema: added possibility to reverse-engineer JSON file with just an empty array

\- MongoDB: updated workload analysis parameter capture form for collections in light of feedback from MongoDB solution Architects team

\- Teradata: added property for relationships so they appear commented in DDL forward-engineering when isActivated property is disabled

&nbsp;

New features in v6.10.1 \[12-May-2023\]

\- Verify Data Model: added column in report for glossary synonyms

\- Verify Data Model: expanded list of rules by default

\- Polyglot data models: added possibility to mark a (composite) unique key as an Alternate Key, and display in ERD

\- XSD reverse-engineering into Polyglot target: added interpretation of structures declared with substitutionGroup as subtypes&nbsp;

\- XSD reverse-engineering into physical targets: added interpretation of structures declared with substitutionGroup as inheritance tables

\- Documentation: fixed Windows 11 issue with schema tree diagram images

\- Delta Lake/Databricks: added handling of truncated responses in reverse-engineering with Runtime 11 and above

\- MongoDB: added workload analysis parameter capture form for collections

\- MongoDB: added cardinality parameter capture form for array data type

\- MongoDB: added reverse-engineering of text indexes

\- Protobuf: fixed conversion of object type when deriving from Polyglot

&nbsp;

New features in v6.10.0 \[05-May-2023\]

\- Verify Data Model: added tool to verify the consistency and quality according to a glossary of class and primary terms, and target-specific attribute rules such as precision/scale for numeric, and length for string data types

\- OpenAPI: added support for OAS 3.1

\- OpenAPI: updated SwaggerUI panel to latest library version

\- Properties Pane for relationships: added synchronization of entity order in dropdown lists with order of these entities in Object Browser

\- Model Definitions and UDTs: added logic to comment definitions in DDL forward-engineering if they don't have any activated references in model

\- Avro for Confluent Schema Registry: added logic to recursively reverse-engineer all references in a union schema, even if not explicitly selected

\- Redshift: added support for JSON arrays as root of payload

\- Teradata: added escaping of UDT names when used as types

&nbsp;

New features in v6.9.14 \[02-May-2023\]

\- ERD: allowed null values for relationship sides property in persistence schema

\- Print diagram: initialized diagram header and footer

\- Oracle: added support for JSON arrays and scalar types as root of payload

&nbsp;

New features in v6.9.13 \[28-Apr-2023\]

\- Avro for Confluent Schema Registry: added support for schema references (https://docs.confluent.io/platform/current/schema-registry/fundamentals/serdes-develop/index.html#schema-references), and so-called "union schemas"

\- BigQuery, Databricks, Hive, Redshift, Snowflake, Synapse, Teradata targets: added modeling methodology at model level plus dimensional table roles and Data Vault 2.0 components at entity level

\- MariaDB: enhanced reverse-engineering of composite Primary Keys and Unique Keys, plus indexes

\- MongoDB: added support for references to definitions in embedded objects when forward-engineering Mongoose schema

\- OpenAPI: added auto-detection of YAML file to trigger reverse-engineering

\- PostgreSQL: enhanced log messages when sampling rows for JSON/JSONB columns and alert user to reduce sample size if memory full

\- PostgreSQL: enhanced ALTER script generation from delta model to include comments for schemas, tables and attributes, views

\- Snowflake: updated vm2 library to latest

\- Teradata: added logic to comment deactivated database

\- YugabyteDB: enhanced ALTER script generation from delta model to include comments for schemas, tables and attributes, views&nbsp;

&nbsp;

New features in v6.9.12 \[21-Apr-2023\]

\- ERD: improved rendering performance for models with large tables

\- Documentation: added handling of custom relationship lines in ERVs

\- Workgroup: added personal token authentication on Azure DevOps Repos when "Allow public projects" is disabled

\- Workgroup: added handling of revoked or renewed personal token on Azure DevOps Repos&nbsp;

\- Oracle: added meaningful error message when user is missing SELECT\_CATALOG\_ROLE for reverse-engineering

\- PostgreSQL: added support in ALTER script for changes in check constraints

\- PostgreSQL: increased logging when fetching functions, triggers and procedures

\- PostgreSQL: added option to ignore reverse-engineering of functions, procedures, and triggers

\- Synapse: added logic to fetch table info when referenced in views

\- Teradata: changed library to fetch JAVA\_HOME environment variables in Windows and get correct path

\- Teradata: added default port if user does not specify

\- Teradata: added escaping of paths

\- YugabyteDB: added generation ALTER script for changes of precision/scale in numeric and length in strings

&nbsp;

New features in v6.9.11 \[14-Apr-2023\]

\- Polyglot: added option to merge into an existing polyglot model when converting a target model

\- ERD and graph view in polyglot: added adapter to restore lost entity coordinates

\- ERD: fixed auto-scrolling of canvas when mouse button was not pressed

\- Excel export: added export of custom properties when common to different data types

\- Cassandra: added possibility to select multiple CQL files to reverse-engineer

\- Delta Lake/Databricks: enhanced ALTER script generation of comments from delta model so the delete of a comment is disabled by default

\- Delta Lake/Databricks: added possibility to select multiple HQL files to reverse-engineer

\- Delta Lake/Databricks: added handling of serde properties

\- Glue Data Catalog: added button to fetch additional databases beyond the standard Glue limit of 100 databases per request

\- Glue Data Catalog: added possibility to select multiple HQL files to reverse-engineer

\- Glue Data Catalog: added handling of serde properties

\- Hive: added possibility to select multiple HQL files to reverse-engineer

\- Hive: added handling of serde properties

\- MongoDB: added reverse-engineering of wiildcard indexes

\- MySQL: inline/out-of-line primary/unique keys enhancements

\- OpenAPI: added inclusion of default display options in Schema ERD tab

\- PostgreSQL: added generation ALTER script for changes of precision/scale in numeric and length in strings

\- ScyllaDB: added possibility to select multiple CQL files to reverse-engineer

&nbsp;

New features in v6.9.10 \[07-Apr-2023\]

\- ERD: improved rendering performance for models with many relationship lines

\- ERD: for composite primary keys made of a JSON object, display separator line to include entire object

\- Properties Pane: added restriction so nested fields aren't accidentally selected as Primary Key

\- Custom path for custom properties: suppressed extraneous config migration

\- Excel export: added possibility to include custom properties that are repeated in complex data types

\- Excel export: added absolute reference for validation rules in empty lines

\- Model definitions: fixed conversion when attributes are part of composite primary key

\- Print diagram: fixed issue with disappearing relationship lines

\- Delta Lake/Databricks: enhanced ALTER script generation from delta model to include comments for schemas, tables and attributes

\- MongoDB: added support for wildcard indexes

\- MariaDB/Oracle/PostgreSQL/SQL Server/YugabyteDB: inline/out-of-line primary/unique keys enhancements

\- Snowflake: enhanced table detection logic to accommodate recent shortcomings in Snowflake's showTables() function

\- Synapse: added logging for Azure Active Directory authentication with MFA

&nbsp;

New features in v6.9.9 \[31-Mar-2023\]

\- ERD: added drag-sand-scroll possibility towards left and top of canvas

\- Compare and merge: added merging of ERDV container properties

\- Polyglot: disabled possibility to add views which should only appear in physical target models

\- Workgroup: added handling of legacy Azure DevOps DNS and URLs when matching remote origin of repo

\- Workgroup: added handling of fatal git client error wrongly identifying "not a git repository" in history screen

\- Workgroup: added warning badge in Tools \> Options \> Default Paths \> Models as path is overwritten by selected repo location

\- Avro: added default null when multiple data types in oneOf choices

\- Oracle: added parsing and storing of table properties in DDL reverse-engineering

\- PostgresSQL: added tolerance for nextval and other functions in default of columns

\- YugabyteDB: added tolerance for nextval and other functions in default of columns

&nbsp;

New features in v6.9.8 \[24-Mar-2023\]

\- Polyglot: allowed derive of multiple data types to RDBMS when JSON column is supported

\- Polyglot: enabled ability to infer PKs and FKs

\- Cassandra: adjusted comparison to handle missing properties

\- Amazon AWS DynamoDB and S3: harmonized support for HTTP(S) proxies and company-issued certificates (self-signed)

\- MongoDB: added connection to serverless cluster on Atlas

\- MongoDB: added parsing of ISODate sample when simple date format without time/timezone

\- MongoDB: added validation for JSON Schema drafts later than draft-04 when multiple data types with string and date

\- Oracle reverse-engineering: added parsing of supplemental log data and group syntax in DDL

\- ScyllaDB: adjusted comparison to handle missing properties

\- Snowflake: relaxed URL checks to accommodate change in non-VPS account locator formats with some regions missing a cloud provider extension

&nbsp;

New features in v6.9.7 \[17-Mar-2023\]

\- Compare and merge: added granular selection in merge dialog for ERDVs

\- Custom path for custom properties: adjusted directory structure to match default setup and allow for ExcelOptions

\- ERD: added scrolling when dragging objects outside canvas

\- Added warning badge when duplicate technical names detected in same entity regardless of naming conventions settings

\- Avro: adjusted data type conversion when reverse-engineering Oracle DDL for numbers with no precision specified to DECIMAL(38)

\- Azure Blob Storage and Azure Data Lake Storage for Avro, JSON Schema and Parquet: harmonized support for HTTP(S) proxies and company-issued certificates (self-signed)

\- JSON Schema preview and forward-engineering: filter deactivated objects

\- MongoDB: added Load Balanced option in Advanced tab of connection settings to connect to cluster with such topology

\- PostgreSQL: added escaping of special characters in DDL generation for views

\- SQL Server: allowed self-signed certificates for all authentication methods

\- YugabyteDB: added escaping of special characters in DDL generation for views

&nbsp;

New features in v6.9.6 \[12-Mar-2023\]

\- ERD annotations for graph models

&nbsp;

New features in v6.9.5 \[10-Mar-2023\]

\- Polyglot: added subclass relationship connector for logical modeling use cases

\- Undo/redo: now also takes into account changes in Display Options toggle hide/display attributes

\- Excel import into Avro: unmuted error caused by container-level dependency to avoid hanging dialog

\- FK relationship creation from Properties Pane: allowed same flexibility as drag-and-drop when concerning nested references to definitions

\- Tech stack: replaced AWS SDK library v2 with v3 plus @aws-sdk/client-s3 and @aws-sdk/client-dynamodb to reduce bundle size

\- Documentation generation: fixed error for cases when ERDVs contain custom relationship style

\- XSD reverse-engineering: improved handling of cardinality in normalization when PowerDesigner XSD nested entities to represent FK relationships

\- Avro: adjusted data type conversion to decimal when reverse-engineering Oracle DDL for numbers with precision larger than 18&nbsp;

\- MongoDB: added possibility for direct connection to Atlas by force dispatching&nbsp;

\- PostgreSQL: added db version check for security\_invoker to determine whether to include in DDL script

\- PostgreSQL: adjusted sequence of DDL statements when table index is defined with "Concurrent build" enabled

&nbsp;

New features in v6.9.4 \[03-Mar-2023\]

\- XSD reverse-engineering: added support for xpath declaration of FK relationships

\- XSD reverse-engineering: added support for \<xs:unique\> tags to create corresponding constraints

\- Avro: adjusted data type conversion (int vs long) when reverse-engineering Oracle DDL for numbers with precision larger than 9&nbsp;

\- Delta Lake/Databricks: adjusted default text mode to string when deriving char/varchar from Polyglot

\- Elasticsearch v7 and above: added Faker function-based mock sample generation in bulk

\- Elasticsearch v7 and above: added possibility to apply mappings to instance

\- Glue Data Catalog: disallowed "Clustered By" in forward-engineering if no "Number of Buckets" is declared

&nbsp;

New features in v6.9.3 \[27-Feb-2023\]

\- Relationship line adjustment preservation: stopped triggering orthogonal distribution after import from Excel when no container in model

&nbsp;

New features in v6.9.2 \[24-Feb-2023\]

\- ERD and ERD Views: added separation of Display Options for each and store in model file

\- ERD: adjusted display option Hide Data types to not hide key indicator

\- ERD: many minor enhancements to adjust relationship lines

\- ERD relationship lines adjustments: disallowed oblique lines on recursive relationships

\- Avro: adjusted data type conversion when reverse-engineering Oracle DDL for numbers with precision and scale

\- Polyglot and non-RDBMS targets: added possibility to choose normalization option when reverse-engineering XSDs, JSON Schema or YAML Schema

\- Glue Data Catalog: added logic to fetch table list by chunk beyond the standard Glue limit of 100 tables&nbsp;

\- Google Storage SDK: harmonized support for HTTP(S) proxies and company-issued certificates

\- Synapse: added support for "Masked by function" property

\- Teradata: enabled export/import with Excel

&nbsp;

New features in v6.9.1 \[17-Feb-2023\]

\- Teradata: added plugin with full data modeling, support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON data types

\- Polyglot: added possibility to declare subtypes/subclasses, kept normalized when deriving into RDBMS targets, and converted to oneOf choice subschemas when deriving into targets supporting nested objects

\- ERD: separated position and adjustments of relationship lines in ERD Views from those in the main ERD

\- Undo/redo after copy/paste: adjusted behavior of the undo stack

\- MongoDB: updated driver to latest version, including all dependencies

\- PostgreSQL: added support for security invoker

&nbsp;

New features in v6.9.0 \[10-Feb-2023\]

\- ERD: added possibility to adjust relationship lines by moving anchors and segments, in addition to the previously available moving of entity boxes.&nbsp; See more info at https://hackolade.com/help/RelationshiplinksinERdiagram.html#Adjust%20relationship%20lines

\- Polyglot: enhanced behavior when deriving from polyglot and an attribute that is part of a FK relationship is marked as "Polyglot only"

\- Network proxy: harmonized support for HTTP(S) proxies and company-issued certificates

\- Workgroup edition: added user notification that stash is being preserved after conflict during stash application (pop)

\- Avro: handling converting choices with subtypes with different fields

\- OpenAPI: added handling for discriminator objects

\- OpenAPI/Swagger: fixed cosmetic overlapping of labels for low-res screens in forward-engineering tab

\- Protobuf: fixed issue when empty options generated undefined results in script

&nbsp;

New features in v6.8.6 \[03-Feb-2023\]

\- Polyglot: disabled PK restriction on foreign master relationships

\- Workgroup Edition: added deletion of source branch after merging a Pull Request in Bitbucket Server

\- Workgroup Edition: allowed opening a Pull Request in Bitbucket Server when it is in status UNAPPROVED

\- Delta Lake/Databricks/Hive: added tab with DDL of view

\- Neo4j: added possibility to apply Cypher scrip to instance in forward-engineering use case

\- Neo4j: updated to v4.4.10 of SDK

&nbsp;

New features in v6.8.5 \[27-Jan-2023\]

\- Compare and Merge Models: generation of delta model for ALTER script when a model has no technical names, while the other has both business names and technical names: fallback on the business names of the model with no technical names

\- Custom properties: added validation and warning badge for multipleCheckboxSelect property

\- JSON document and Schema reverse-engineering: added trimming of invisible characters

\- ERD: prevented duplication of of references during drag-and-drop operations

\- Foreign key relationships: preserve when replacing an attribute by a reference to a definition (internal, model, or external)

\- JSON in RDBMS: enabled simple polymorphism with multiple data types in JSON fields (complex polymorphism was already allowed with oneOf choices)

\- Avro/Parquet: upgrade Azure Blob Storage SDK

\- Avro/Parquet: shortened delay in display of progress bar

\- Avro/Parquet: allowed to open branches without losing previously selected files in other branches

\- Delta Lake/Databricks: added database name to columns in select statement when there is no select statement and columns reference tables in different databases

\- Neo4j: added support for Neo4j v5 and AuraDB, including new indexes and constraints

&nbsp;

New features in v6.8.4 \[20-Jan-2023\]

\- Workgroup Edition: added ability to STASH local changes from the commit screen, plus review, apply, drop, handle conflicts

\- PDF documentation and PDFdiagram print: replaced PhantomJS library for enhanced performance and increased stability

\- JSON Schema: added user-friendly "Display name" property for conditionals for documentation purposes (not forward-engineered, as not part of spec)

\- JSON Schema: prevented possibility to use copy/paste workaround to create multiple conditionals at same level

\- Avro/Parquet reverse-engineering from cloud storage: set default to combine schemas

\- Avro/Parquet reverse-engineering from cloud storage: increased logging of critical operations

\- BigQuery: added configuration of external table options, plus forward- and reverse-engineering of external table options&nbsp;

\- BigQuery: added support for new JSON data type

\- BigQuery: disabled ability to create multiple data types for a columns

\- BigQuery: disabled possibility to create pattern columns, while leaving the possibility inside a column with JSON data type

\- Couchbase: enabled possibility for numeric fields to be marked as primary key of document type for documentation purposes

\- Couchbase: adjusted reverse-engineering logic to continue process after failure to fetch documents from N1QL query

\- MariaDB: added validation warning for empty index names

\- MySQL: added handling of tablespaces

\- MySQL: added Blackhole engine

\- MySQL: added validation warning for empty index names

\- PostgreSQL: added array type for domain data type

\- PostgreSQL: added forcing user to create UDT according to spec for data types domain, enum, composite, and range\_udt https://www.postgresql.org/docs/current/datatype-enum.html

&nbsp;

New features in v6.8.3 \[13-Jan-2023\]

\- References: added shortcut to root level objects or dialog for nested objects in internal and model definitions when adding, inserting, appending

\- Azure Data Lake Storage: improved performance when reverse-engineering Avro, JSON or Parquet files in nested sub-folders

\- Avro: added name property when resolving UDTs

\- Avro: adjusted resolution of references with multiple data types

\- Couchbase: allowed fallback on N1QL for index retrieval if issues encountered in retrieval via REST API

\- MySQL: implemented generation of ALTER script from delta model

\- OpenAPI/Swagger/EventBridge:allowed additional ways to create FK relationships (for documentation purposes) in Schema ERD View tab

\- PostgreSQL: added visual display for array types in ERD

\- Synapse: added handling for empty tableInfo data and null table\_type

&nbsp;

New features in v6.8.2 \[05-Jan-2023\]

\- JSON Schema forward-engineering: adjusted filtering of nested definitions when one is undefined

\- Avro: allowed Doc property of a definition to be replaced by reference description

\- Databricks: adjusted count of number of table buckets when reverse-engineering from HQL file

\- Elasticsearch: added reverse-engineering from cloud instance

\- Glue Data Catalog: adjusted count of number of table buckets when reverse-engineering from HQL file

\- Hive: adjusted count of number of table buckets when reverse-engineering from HQL file

\- Parquet: improved speed of reverse-engineering on Azure Data Lake Storage

\- Synapse: improved detection of parent schema of views

&nbsp;

New features in v6.8.1 \[30-Dec-2022\]

\- Excel: added full path in technical names of nested objects

\- Delta Lake/Databricks: added handling of view table properties, plus added numBuckets cast to number

\- Glue Data Catalog: added handling of view table properties, plus added numBuckets cast to number

\- Hive: added numBuckets cast to number

\- PostgreSQL: added support for v15, including new property NULLS \[NOT\] DISTINCT for columns, table constraints and table indexes

\- PostgreSQL: added support for array types

\- Synapse: added reverse-engineering of views referencing tables in other schemas, and of views in schemas without tables

&nbsp;

New features in v6.8.0 \[23-Dec-2022\]

\- MySQL: added plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in LONGTEXT data types

\- Tech refresh of Electron (v22.0.0), NodeJS (v16.17.1), Chromium (v108.0.5359.62), V8 (v10.8) and Electron-related modules

\- Mac: fixed shortcut key conflict on Ventura MacOS after screen capture

\- Schema Registries: fixed issue in selection modal when version labels sometimes overlapped when filter is active

\- Cassandra/ScyllaDB: adjusted ALTER script in case of change in Clustering Key

\- MongoDB/DocumentDB/Cosmos DB with MongoDB API: enhanced BSON parser

\- Neo4j and other graph targets: fixed alignment of nodes when not using forced-directed layout

\- PostgreSQL: adjusted parsing of SELECT statements to allow view columns with no underlying table columns (NULL::character varying AS...)

\- PostgreSQL: enhanced reverse-engineering in case of duplicate views in same DDL

\- Redshift: enhanced handling of deactivated columns in forward-engineering

\- Swagger/OpenAPI/EventBridge: enabled copy/paste in responses of interactive SwaggerUI pane

&nbsp;

New features in v6.7.3 \[16-Dec-2022\]

\- Tools \> Options \> Forward-Engineering: added parameter to skip COMMENT in DDL for SQL and SQL-like targets

\- Reverse-Engineering selection dialog: adjusted filter so schema versions don't require matching

\- Undo/Redo: various enhancements

\- Workgroup: added basic support for git subtrees

\- Workgroup: added possibility to commit and push in a single step, provided that there are commits to be pulled first

\- Workgroup: updated simple-git library to latest version

\- Workgroup: adjusted SSH password prompt modal

\- Workgroup: added logging of git configuration when opening a repository

\- Avro: added inference of Subject Name Strategy during reverse-engineering of Confluent Schema Registry

\- Cassandra: added determination of PROFILE value from DESCRIBE SEARCH INDEX during reverse-engineering

\- Cassandra: removed from ‘Profile’ *\<spaceSavingNoTextfield\>* for CQL if DSE version is 6 and higher

\- Cassandra/ScyllaDB: added tolerance for empty lists in reverse-engineering of UDTs

\- Cassandra/ScyllaDB: moved data transfer to UDThelper

\- Cassandra: added check ‘Profile’ values - \<spaceSavingNoTextfield\> and \<spaceSavingSlowTriePrecision\> if they are missing in the reference model

\- PostgreSQL: improved parsing of complex functions during reverse-engineering

\- Protobuf: added conversion of array attributes from Polyglot

\- Swagger/OpenAPI: enabled auto-height and auto-width for entities in Schema ERD View

&nbsp;

New features in v6.7.2 \[09-Dec-2022\]

\- Added validation warnings in ObjectBrowser and ERD for deeply nested attributes

\- Workgroup Edition: after creation of Pull Requests, redirect user to My Pull Requests screen

\- Workgroup Edition: added provider-specific help links in Repository Connections dialog

\- Workgroup Edition: added rendering of Pull Request timeline in ascending order for GitHub and GitLab

\- Avro: refactored integration with Confluent Schema Registry to better handle different subject name strategies

\- Avro: added capture of Schema Registry URL during reverse-engineering from Confluent

\- Avro: added generation of subject name according to strategy and schema type unless specified manually

\- Avro: added validation for Topic and Subject properties

\- Collibra: added more user-friendly dialog when attempting to connect with an erroneous URL

\- Delta Lake/Databricks: added support for columns GENERATED AS

\- Swagger/OpenAPI: allowed display options in Schema ERD View

\- Swagger/OpenAPI: added import of FK relationships when deriving Polyglot model into Schema ERD View

&nbsp;

New features in v6.7.1 \[02-Dec-2022\]

\- Polyglot: added normalization of Polyglot choices during derivation into super-type/sub-type for RDBMS targets

\- Polyglot: added creation of references to Polyglot model when converting a target model to Polyglot

\- Compare and Merge: disabled rendering of properties for ghost objects

\- Workgroup Bitbucket Server: enabled network proxy settings, so self-signed certificates in local store are automatically recognized

\- Avro: added support for newly introduced Avro spec feature of symbol default property for enum data type

\- Delta Lake/Databricks: added Azure URL suffix in connections dialog for Azure Storage Access

\- ScyllaDB: applied recent ALTER script logic enhancements from Cassandra plugin for partitioning/clustering keys

\- Snowflake: updated snowflake-sdk package in plugin

\- SQL Server: allowed creation of Foreign Relationships referencing columns that are non-PK as long as they have a UNIQUE constraint

\- Swagger/OpenAPI/EventBridge: added parsing of yaml values as JSON

\- Swagger/OpenAPI/EventBridge: added validation of objects after reverse-engineering to display warning badges in Object Browser

&nbsp;

New features in v6.7.0 \[25-Nov-2022\]

\- Workgroup: added support for GitLab Cloud (gitlab.com) and GitLab Server (self-hosted) for workflow to submit and review Merge Requests

\- Workgroup: added showing username and display name for change requests

\- Workgroup Bitbucket Cloud: enabled network proxy settings

\- Network proxy: added possibility to specify a .pac file URL for backend functions such as forward- and reverse-engineering

\- Compare and Merge: adjusted matching for objects inside moved objects

\- Excel: adjusted handling of multiple JSON complex types

\- Avro: reverted mapping of date/time/timestamp fields to semantic meaning when converting from DDL and JSON Schema and inference of JSON data

\- Cassandra: removed duplicated udt in list/set/tuple when reverse-engineering from instance

\- Cassandra: removed business and technical names from array items to keep just display name

\- Delta Lake/Databricks: allowed column lists to be used for aliases as well as filter of columns from SELECT statements when reverse-engineering from instance

\- Hive: added forward- and reverse-engineering of AS SELECT statement for views

\- Hive: added forward-engineering of comments

\- OpenAPI/Swagger: added lower tab "Schema ERD view" to enhance visualization of definitions/component schemas

\- Parquet: reverted mapping of date/time/timestamp fields to semantic meaning when converting from DDL and JSON Schema and inference of JSON data

\- ScyllaDB: removed duplicated udt in list/set/tuple when reverse-engineering from instance

\- ScyllaDB: removed business and technical names from array items to keep just display name

&nbsp;

New features in v6.6.4 \[18-Nov-2022\]

\- Polyglot: added possibility to insert attributes in entities of target model derived from Polyglot

\- Polyglot added impact analysis when calling references refresh from entities

\- Network proxy: added possibility to specify a .pac file URL for access to license server and plugin manager

\- Network proxy: enhanced logging of proxy settings on application startup

\- Workgroup Bitbucket Server: added tolerance for slashes in usernames when displaying Pull Requests

\- Custom properties: allowed defaultValue property in custom tabs

\- Cassandra: adjusted reverse-engineering of list\<udt\>, and adjusted ALTER script generation in case of list\<udt\>

\- Cassandra: fix over eager drop/create table when business names are different but technical names are similar

\- Databricks on Azure: added connection tab to declare ADLS storage passthrough credentials

\- Neo4j and other graph targets: allowed dragging graph nodes with force-directed layout if node has edge is dangling

&nbsp;

New features in v6.6.3 \[11-Nov-2022\]

\- Command-Line Interface: added command polyglotDerive to derive a target model from multiple polyglot models

\- Compare and Merge: allowed comparison by name to take array display names into account

\- Polyglot: added possibility to derive target model when FK relationships involve attributes in nested objects

\- Workgroup for Azure DevOps Repos: added ability to automatically detect and use proxy settings

\- Workgroup Bitbucket Server: detect Server version to adapt required connection parameters accordingly

\- Workgroup Bitbucket Server: show detailed message in logs in case or API errors

\- Cassandra: adjusted ALTER script generation when change in PK

\- Delta Lake/Databricks: added property Column List in view Properties Pane to achieve round-trip engineering

\- Delta Lake/Databricks: added parsing of column list from CREATE VIEW statement in HQL file

\- Delta Lake/Databricks: allowed column lists to be used for aliases as well as filter of columns from SELECT statements when reverse-engineering from HQL files

\- Delta Lake/Databricks: added handling of jinja double curly braces in forward-engineering and ALTER scripts

&nbsp;

New features in v6.6.2 \[04-Nov-2022\]

\- Command-Line Interface: added command polyglotDerive to derive a target model from a polyglot model

\- Command-Line Interface: added command polyglotUpdate to update a target model for modifications made to the referenced polyglot models

\- Command-Line Interface: added possibility to forward-engineer schema to schema registries (Confluent, Azure, Pulsar)

\- Documentation: fixed issue generating PDF on Ubuntu 24.04

\- Model API generation: added validation of the template to ensure presence of entity/entities in schema components and resources

\- MongoDB: fixed issue with $jsonschema generation when descriptions include Regex-like expressions

\- Workgroup: enhanced handling of user permission errors when submitting change request for review

&nbsp;

New features in v6.6.1 \[28-Oct-2022\]

\- Workgroup: added display of required permissions in the connection manager when issues with the Personal Access Token

\- Workgroup: changed check of repository permission to circumvent lack of proper decoding of slashes in usernames by Bitbucket Server

\- Workgroup: added check for repo permissions when opening Submit for review page, and when switching repos

\- Workgroup: streamlined flow after repo provider authentication error&nbsp;

\- Workgroup: added input auto-height when typing multi-line comments in change requests creation and review

\- Workgroup: harmonized icons for closed and reopened Change Requests in timeline and status badge

\- Workgroup: added preserving reviewers when switching panes during Change Requests

\- Workgroup: improved SSH keys errors and SSH URLs handling

\- Polyglot: fixed refresh of cross-target external reference after conversion to local objects

\- Polyglot: default to ER Diagram tab when opening previously save model

\- Avro: adjusted mapping of detected ISO-8601 dates in JSON data reverse-engineering

\- EventBridge: added ability to add recursive references to resource schemas

\- OpenAPI: added ability to add recursive references to resource schemas

\- Parquet: adjusted mapping of detected ISO-8601 dates in JSON data reverse-engineering

\- PostgreSQL: adjusted mapping of timestamps without timezone

\- Redhift: adjusted mapping of detected ISO-8601 dates in JSON data reverse-engineering

\- YugabyteDB: adjusted mapping of detected ISO-8601 dates in JSON data reverse-engineering

&nbsp;

New features in v6.6.0 \[21-Oct-2022\]

\- Workgroup: added support for Azure DevOps Repos for workflow to submit and review Pull Requests

\- Polyglot: added lower tab Graph Diagram view for conceptual modeling

\- Collibra: added storage of Asset URL for objects during reverse-engineering

\- Avro: refactoring of forward-engineering to facilitate enhancements

\- Avro: added detection of conflict in names of references and records

\- Avro: added detection of missing type name for fixed fields

\- Avro: adjusted level for generation of alias of arrays

\- Avro: adjusted resolution of array references

\- Avro: adjusted order of doc property in case of array with aliases

\- Avro: added possibility to create complex schemas to fields with map data type

\- Avro: added handling of choices with empty names

\- Avro: resolved duplicate named complex types with different structures

\- Cassandra: added filtering in views of columns that have been deactivated in the underlying table

\- Delta Lake/Databricks: added warning dialog when views are invalid due to discrepancy with underlying table structure, and need to be refreshed

&nbsp;

New features in v6.5.5 \[14-Oct-2022\]

\- ERD: added logic to automatically create PK in parent table if not exists, when FK relationship is created via drag-and-drop

\- Test data generation: upgraded to FakerJS v7.6.0 library

\- Test data generation: added tolerance for wrapping functions with quotes instead of backticks

\- Markdown documentation generation: fixed to take out link rule in turndownHelper to speed up generation

\- Workgroup Edition: added handling of non-scp syntax for SSH protocol in remote URL of git config file

\- DDL reverse-engineering: added handling of integer and decimal type of SQL Server T-SQL dialect

\- Collibra: added handling for deactivated objects in publishing and reverse-engineering

\- Avro: added handling of fixed type when size is zero

\- BigQuery: added filtering in views of columns that have been deactivated in the underlying table

\- Delta Lake/Databricks: added parsing of properties pane SELECT statement to determine view columns

\- Hive: added filtering in views of columns that have been deactivated in the underlying table

&nbsp;

New features in v6.5.4 \[07-Oct-2022\]

\- YugabyteDB with YSQL API: added plugin with full support for forward-engineering of DDL, and reverse-engineering including inference of schemas in JSON and JSONB data types

\- Workgroup: added filter by file extension for custom certificate selector

\- Workgroup: pre-filled host domain for self-hosted providers with info from opened git repo

\- Workgroup: only allow pem,crt,key,cer file extensions when specifying custom SSL Certificate Authority for Git and Git provider API

\- Delta Lake/Databricks: enhanced reverse-engineering by querying long list of properties in struct data type

\- Delta Lake/Databricks: added possibility to reverse-engineer a view that references tables in another Databricks database

\- MongoDB: added choice between JSON or BSON serialization in data sample of Preview, forward-engineering, and Command-Line Interface

&nbsp;

New features in v6.5.3 \[30-Sept-2022\]

\- Workgroup: added support for Bitbucket Cloud for workflow to submit and review Pull Requests

\- Workgroup: improved handling of custom Certificate Authority

\- Enum and other multi-text inputs: added bulk edit functionality

\- JSON Schema reverse-engineering: added detection and tolerance for UTF-16 encoding

\- JSON Schema: added support in choice subschemas to convert to definition, replace by attributes, and replace by attributes

\- Avro: adjusted type for references in array items

\- Cassandra: added filtering of solr\_query column during reverse-engineering

\- Cassandra: added searchIndexProfiles to excluded keys in model comparison and generation of delta model

\- Delta Lake/Databricks: made "if not exists" and "or replace" mutually exclusive

\- Delta Lake/Databricks: added filtering in views of columns that have been deactivated in the underlying table

\- Delta Lake/Databricks: enhanced representation of table properties, converting from textarea to key-value pairs

\- Hive: made "if not exists" and "or replace" mutually exclusive

\- MongoDB: enhanced forward-engineering to Mongoose schema so only relevant definitions are included when choosing separate files option

\- OpenAPI/Swagger/EventBridge: added possibility to resolve external references when forward-engineering, in GUI and Command-Line Interface

&nbsp;

New features in v6.5.2 \[23-Sept-2022\]

\- Polyglot: added an impact analysis screen when updating references from polyglot in a target model, based on the model compare screen

\- Workgroup: added possibility to specify custom SSL Certificate Authority for Git and Git provider API

\- Enum and other multi-text inputs: added up/down controls to re-order list

\- ERD annotations: added an Options tab to control color and font style

\- Forward-engineering of ALTER script from delta model: added user-friendly message if script is empty

\- DDL reverse-engineering: adjusted mapping of timestamp, time, and numeric data types for DB2 dialect

\- Delta Lake/Databricks: enhanced reverse-engineering of cross-database views when script does not include related tables

\- Delta Lake/Databricks: improved parser of view statements with CAST of STRUCT when reverse-engineering from HQL file

\- Delta Lake/Databricks: improved parser of view statements with subqueries in FROM section of SELECT statement

\- MongoDB: enhanced forward-engineering of numerics (int32, long, double, decimal128) to be formatted as BSON instead of JSON

\- Redshift: added possibility to connect to instance without region if stored by AWSCLI

\- Snowflake: added to ALTER script from delta model: schema and table rename, comment set/unset, view add, drop and rename

&nbsp;

New features in v6.5.1 \[16-Sept-2022\]

\- Changed some icons of Display options to be more intuitive and consistent

\- JSON Schema: added support for "dependent schemas" property when both business/technical names are present

\- JSON Schema: added tolerance for "example" keyword during reverse-engineering for draft-06 and above, when the keyword should have been "examples"

\- JSON Schema: added support for references in choice subschemas

\- DDL reverse-engineering into Avro target: adjusted mapping of dates and decimal numbers data types&nbsp;

\- DDL reverse-engineering: adjusted handling of $$ comments for Snowflake dialect

\- Workgroup edition: implemented automatic transparent use of of repository connection credentials in Git clone, if previously provided for provider

\- Workgroup edition: added tooltip next to Clone button to describe URL pattern

\- Workgroup edition: update styles and layout of history details to match the "Repository files" screen

\- Cassandra: adjusted handling of ALTER script for default values in search index

\- Delta Lake/Databricks:added extra logging, plus stopped querying count in case of absolute sampling in reverse-engineering

\- Redshift: added possibility to connect to instance without credentials if stored by AWSCLI

\- Snowflake: added filtering of metadata columns for external tables during reverse-engineering

&nbsp;

New features in v6.5.0 \[09-Sept-2022\]

\- Workgroup: added support for Bitbucket Server for workflow to submit and review Pull Requests

\- JSON Schema: added support for "dependent required" property when both business/technical names are present

\- Collibra: added handling of multiple choice subschemas during reverse-engineering

\- Delta Lake/Databricks: enhanced parsing of views to handle CAST statements

\- Redshift: added support for serverless instances

\- Snowflake: added detection of insufficient rights to perform reverse-engineering and display user-friendly dialog

&nbsp;

New features in v6.4.3 \[02-Sept-2022\]

\- FK relationships: added display option to toggle relationship names in ERD

\- Compare and Merge: added user-friendly dialog if user chooses models for different targets

\- Compare and Merge: if comparison by GUIDs is not possible, changed default to comparison by technical name (if exist) when generating delta model, instead of business names

\- Compare and Merge: display placeholder when models only differ by their metadata

\- Compare and Merge: difference pager count takes display filter into account

\- Compare and Merge: when invoked from the Commits History view, added possibility to Open model in new instance

\- Cassandra: added filter for table options in ALTER script of delta model

\- Oracle: added support for ON DELETE for FK relationships

&nbsp;

New features in v6.4.2 \[26-Aug-2022\]

\- Infer Primary Keys and Foreign Key relationships: increased probability to infer FKs in some conditions, while restricting other conditions to reduce false positives

\- Foreign Key relationship: swapped order of entities in automatic naming to follow a more common convention: fist table is the FK table, and second table is the PK table

\- Model API: added user-friendly dialog if user chooses inadequate file for API template

\- Collibra: added support for multiple JSON Schema choices in same table

\- Workgroup: made column width adjustable in Explore Repository Files screen

\- Workgroup: allowed to review closed Change Requests when remote branch has been deleted

\- Workgroup: added visual clue that a copy icon is being clicked

\- BigQuery: added filtering of deactivated objects in forward-engineering of DDL in JSON Schema format

\- Delta Lake/Databricks: added support for table options reverse-engineered from instance

\- Delta Lake/Databricks: added maintaining order of fields when detecting JSOn in string columns

\- Delta Lake/Databricks: added filtering of extraneous Scala metadata when reverse-engineering bloom filters

\- Snowflake: added reverse-engineering of stages and external tables

&nbsp;

New features in v6.4.1 \[19-Aug-2022\]

\- Apple Silicon ARM64: added application build optimized for M1 and M2 processors and achieve unprecedented performance

\- Read-Only Viewer: added edition to allow navigation through models for consultation purposes only -- no creation or editing, no forward-engineering (except JSON Schema and Excel) or reverse-engineering.&nbsp; When connected to Git repositories, also allows pull operations and commenting on change requests.&nbsp; Request pricing at sales@hackolade.com

\- Polyglot: adjusted behavior so external references in polyglot are derived into target physical models as direct external references, instead of transitive via polyglot model

\- References: added handling if a parent object, being converted to a reference, contains a child attribute itself with a prior reference

\- References: added detection of technical name collision when renaming references after copy/paste

\- Workgroup: added ability to detect and visually resolve conflicts affecting change requests when the source branch becomes out-of-sync with the target branch

\- Workgroup: added handling of multiple worktrees by filtering out their branches

\- Workgroup: merged screens for Explore Models and Explore All Files, plus enhanced aesthetics&nbsp;

\- Workgroup: enhanced UX for local-only repositories

\- Workgroup: enhance logging to reduce file size and redundancies, enhanced logging with git provider API call details&nbsp;

\- Avro: enhanced handling of enum symbols when deriving from polyglot

\- BigQuery: added handling of typeMode=required in documentation

\- Collibra: added publishing and reverse-engineering of foreign master relationships in denormalized models

\- Delta Lake/Databricks: throttled fetching databases to accommodate API rate limiting

\- Delta Lake/Databricks: added support for table options reverse-engineered from HQL files

\- DynamoDB: added default JSON data for data types binary and binarySet

\- DynamoDB: added Faker function-based (bulk) sample generation in script tab to apply to instance

\- YAML: added possibility to choose quoting style (unquoted, single-quote, double-quotes) in preview and forward-engineering, including new argument quotingType in CLI forwEng command

&nbsp;

New features in v6.4.0 \[12-Aug-2022\]

\- Tech refresh of Electron (v19.0.10), NodeJS (v16.14.2), Chromium (v102.0.5005.167), V8 (v10.2) and Electron-related modules.&nbsp; Includes backported fix for CVE-2022-2162 vulnerability

\- WARNING: support for Windows 7 is discontinued with this version

\- Workgroup Edition: improved error handling dialog when user has limited or no access to repository

\- Workgroup Edition: harmonized access to Repository options and hub connections

\- Cassandra/ScyllaDB: as ALTER TYPE syntax has been deprecated starting with Cassandra 3.10 and DataStax 5.0.6, replaced with DROP + CREATE column statements in ALTER script of delta model, plus added display of warning badge for incompatible data type change in Compare \& Merge dialog

\- MongoDB reverse-engineering: added timeout in probabilistic schema inference process plus enhanced logging

\- YAML forward-engineering: added double-quote encoding of strings when necessary (semicolons, hash signs, and unicode characters)

&nbsp;

New features in v6.3.1 \[05-Aug-2022\]

\- Detection of outside changes in open model: added handling of models stored and synched on OneDrive

\- Collibra: added handling of relationships when when parent and/or child are in nested objects

\- Compare and merge: enhanced handling when one model has technical names and the other doesn't

\- Compare and merge: enhanced named-based detection to better detect names when differences are minor (underscores between words instead of spaces, etc.)

\- Custom properties: added migration of data models when changing a property from propertyType="select" to propertyType="multipleCheckboxSelect"

\- Workgroup: use commit short hash in model name when opening model from commit history view

\- Workgroup: preserve state and select row of history view when changing context then returning to repository context

\- Workgroup: added auto-refresh of history view when creating or deleting a branch

\- Workgroup: added auto-refresh of history view when discarding local changes from uncommitted row

\- Workgroup: enhanced up and down arrow key navigation in history view to go to previous/next page when available

\- Workgroup: enhanced GitHub OAuth user experience to clarify steps

&nbsp;

New features in v6.3.0 \[29-Jul-2022\]

\- Infer Primary Keys and Foreign Key relationships: for RDBMS targets and related, new feature to automatically help identify candidate PKs and FKs in a model, if not yet explicitly reverse-engineered or declared, based on machine learning and probabilities.&nbsp; Available in BigQuery, Delta Lake/Databricks, Hive, MariaDB, Oracle, PostgreSQL, Redshift, SQL Server, Snowflake, and Synapse plugins.

\- Compare and Merge: refactored dialogs to allows for all permutations of the Workgroup Edition's screens for review changes, merge conflict, and comparisons between different commits

\- Custom properties: added tolerance for presence of unrelated json files (or backups) in properties\_pane/\<level\> directories

\- Tools \> Options \> General: added possibility to backup and restore user parameters and connection settings.&nbsp; Useful also when moving to another machine

\- Workgroup Edition: added repository history screen, including filters by data model, branch, or author

\- BigQuery: added primary key property for documentation purposes only

\- MongoDB: added possibility to reverse-engineer fields declared in validator script but no data type is defined

\- MongoDB: added default creation of \_id field when not present in validator script and collection is empty

\- OpenAPI: adjusted validations of text inputs in block inputs

\- Swagger/OpenAPI: added default opening of components if no resources are reverse-engineered

&nbsp;

New features in v6.2.5 \[23-Jul-2022\]

\- Excel:enhanced validation when exporting graph models

\- Model API generation: added help link next to template selection, plus enhanced error message when selected file is not a template

\- Polyglot: added spinner when large model is being derived

\- Polyglot: enhanced handling when replacing a reference to a definition by its attributes

\- Workgroup: reload data model if changes detected after pull operation

\- Workgroup: leverage GitHub GraphQL API to populate list of Pull Requests screen

\- Workgroup: enhanced conflict resolution after merge of local branches

\- Parquet: fixed issue causing 'Too many files opened" message

&nbsp;

New features in v6.2.4 \[17-Jul-2022\]

\- Command-Line Interface: reordered commands

\- Multiple data types: enhanced removal when complex data type is last one left

\- Polyglot: added possibility to give a name to the polyglot link.&nbsp; Can be helpful when making multiple links to the same polyglot model, for different profiles

\- ArangoDB: allowed custom properties in relationships

\- Avro: enhanced schema validation messages

\- JanusGraph: allowed custom properties in relationships

\- Oracle: enhanced parsing of view SELECT statement

\- Snowflake: enhanced reverse-engineering when data sampling enabled

&nbsp;

New features in v6.2.3 \[08-Jul-2022\]

\- Command-Line Interface: added commands to export and import with Excel from the CLI

\- Polyglot: allowed deviations in attribute business and technical names in target model when deriving from Polyglot

\- Polyglot: adjusted mapping of binary type when reverse-engineering XSD

\- Workgroup: added possibility to link Change Request to assignees from the Submit for review screen

\- Workgroup: added possibility to link GitHub Pull Request to reviewers from the Submit for review and the Check pR screens

\- Cosmos DB with MongoDB API: added possibility to generate synthetic/mock/fake documents and applied in bulk to the instance

\- DocumentDB: added possibility to generate synthetic/mock/fake documents and applied in bulk to the instance

\- Couchbase: added possibility to generate synthetic/mock/fake documents and applied in bulk to the instance

\- Oracle: added tolerance for GET\_DDL returning concatenated statements without delimiter

\- Oracle: added SQL terminator to view DDL retrieval

\- PostgreSQL: changed escaping from $ to C-style

\- SQL Server: adjusted mapping of data types when deriving from Polyglot to convert string sizes greater than 8000 to (n)varchar(MAX)

&nbsp;

New features in v6.2.2 \[04-Jul-2022\]

\- JSON Schema: added possibility to declare multiple data types including at least one complex data type without oneOf choice

\- Excel import: added support for relationships on nested attributes

\- Excel import: added support for cross-target references

\- Polyglot: allowed modification of business and technical names for attributes and UDTs/model references

\- Polyglot: added handling of references when multiple derivations from the same polyglot model

\- Workgroup: added auto reuse of provider credentials for Git authentication

\- Workgroup: added GitHub OAuth device flow method

\- Workgroup: added possibility to assign a Pull Request by picking from a list of possible assignable users

\- Workgroup: added handling for Pull Request comments deleted on web console

\- Oracle: added tolerance for GET\_DDL returning concatenated statements without delimiter

\- SQL Server: added support for MATCH, ON UPDATE, and ON DELETE for FK relationships

\- SQL Server: allowed use of named instance in connection host parameter

&nbsp;

New features in v6.2.1 \[24-Jun-2022\]

\- Azure Blob Storage and Azure Data Lake Storage (for JSON, Parquet, Avro...): collapsed hierarchical folders so they only get discovered when node is expanded

\- Azure Blob Storage and Azure Data Lake Storage (for JSON, Parquet, Avro...): increased limit of discovered objects to 1000

\- JSON data sample for pattern fields: generate default name by regular expression

\- JSON data sample for fields with data type "any": added handling using sub-object if exists or string

\- JSON Schema: allowed root to be an array (in addition to historic possibility for root to be a document)

\- Polyglot: fixed inconsistency when deriving model definitions/UDTs into a target model

\- Test data generation: upgraded to FakerJS v7.3.0 library

\- Workgroup: adjusted finding consistent source branch during resolution of conflicts during discard

\- Workgroup: prevented lock during background check for remote commits

\- Workgroup: enhanced UX and handling of token expiration state

\- Workgroup: enabled caching for some GitHub API requests

\- Workgroup: enhanced GitHub credentials setup to favor personal tokens, as passwords are now deprecated

\- Workgroup: disabled forbidden actions for users with GitHub read-only tokens

\- Workgroup: added column for authors in lists of change requests

\- Workgroup: added submit and review actions to Repository menu

\- Workgroup: added timestamp tooltip to all screens with relative dates

\- Workgroup: added handling of blocked Pull Requests

\- Hive: adjusted forward-engineering "apply to instance" script with deactivated objects

\- MariaDB: adjusted conversion of sample and default properties when deriving from Polyglot Boolean into tinyint(1)

\- Parquet: enabled primary key property for documentation purposes only

\- PostgreSQL: adjusted mapping when deriving nvarchar from Polyglot to varchar

\- PostgreSQL: added support for MATCH, ON UPDATE, and ON DELETE for FK relationships

\- SQL Server: adjusted conversion of sample and default properties when deriving from Polyglot Boolean into bit

\- SQL Server: adjusted mapping when deriving timestamp from Polyglot to Datetime2

\- Synapse: adjusted conversion of sample and default properties when deriving from Polyglot Boolean into bit

\- Synapse: adjusted mapping when deriving timestamp from Polyglot to Datetime2

\- Synapse: added possibility apply DDL to instance

&nbsp;

New features in v6.2.0 \[17-Jun-2022\]

\- Workgroup: added support for GitHub (.com as well as Enterprise Server) for workflow to submit and review Pull Requests

\- Workgroup: added possibility to authenticate on GitHub using personal token

\- MongoDB synthetic data generation: added progress bar when generating in bulk

\- Documentation generation: added support for recursive references

\- Excel import: added support of string formats

\- JSON Schema: added possibility to generate JSON Schema when subschema of choice inside a data type "any" is scalar

\- Polyglot: fixed selection of multiple keys when they are references to model definitions/UDTs

\- Polyglot: fixed rendering of group input properties when referencing definitions

\- Azure Data Lake Storage (for JSON, Parquet, Avro...): enhanced discovery nested sub-folders when empty&nbsp;

\- Azure Data Lake Storage: added Advanced tab in Connection Settings for Prefix selection

\- Hive: enhanced apply to instance with commented drop statement

\- PostgreSQL: added validation of primary/unique keys, plus added warnings in forward-engineering script when primary/unique constraints have no keys

\- Redshift: enhanced fetching of tables/views if schema has more than 500 of entities

&nbsp;

New features in v6.1.3 \[10-Jun-2022\]

\- Network proxy: increased logging and error details

\- Polyglot: added enforcement that only a single column can be a primary key, or it should be part of of a compound key

\- Polyglot: added possibility to edit required property in UDTs

\- Polyglot: fixed resolution of references before normalization when applicable

\- XSD: added translation of mxOccurs=1 into required/not null during reverse-engineering

\- Workgroup: added Git status icons to repository explorer tables

\- Workgroup: disabled Pull button when there is no remote tracking branch

\- Avro: forward-engineer Confluent subject name from schemaGroupName property

\- Hive: added the possibility to apply forward-engineering HQL script to instance

\- Hive: adjusted v2 HQL script to filter out v3-specific features

\- MongoDB synthetic data generation: added possibility to specify the number of mock/fake documents to be created and applied to the instance

\- Parquet on Azure Data Lake Storage: enhanced discovery when many non-parquet files are also present

\- Protobuf: updated protobufjs libraries

&nbsp;

New features in v6.1.2 \[03-Jun-2022\]

\- Redrew toolbar and contextual menu icons with SVG for cleaner hi-res displays

\- Workgroup: added possibility to end or continue merge branch process

\- Polyglot: adjusted warning for UUID enums, sample, and examples properties

\- Added "Apply to instance" button for all remaining RDBMS and SQL-like targets: Databricks, Hive, MariaDB, Oracle, PostgreSQL, Redshift, Snowflake, SQL Server, Synapse

\- OpenAPI/Swagger models derived from Polyglot: added ability to edit properties of references

\- RDBBMS and SQL-like targets: added enforcement that only a single column can be a primary key, or it should be part of of a compound key

\- Hive: enhanced handling of constraints rely/no rely, disable novalidate

&nbsp;

New features in v6.1.1 \[27-May-2022\]

\- ERD: added display option in toolbar and Tools \> Options \> Display to show/hide attribute data types

\- Application log files: enhanced so logs are no longer reset with start of additional application instances -- only when first instance gets started

\- Test data generation: added possibility to specify the number of documents to generate in Tools \> Forward-Engineer \> JSON documents

\- Test data generation: added Faker function-based sample generation in script tab to apply to instance of concerned targets (MongoDB, Couchbase, Cosmos DB, DocumentDB, JanusGraph, Neo4j, Neptune, TinkerGraph)

\- Test data generation: upgraded to FakerJS v7 library

\- Workgroup: added action to merge branches

\- Couchbase: added ability to reverse-engineer buckets with no N1QL primary index, by automatically falling back to REST API for sampling and schema inference

&nbsp;

New features in v6.1.0 \[20-May-2022\]

\- Generate fake but realistic data for development, testing or demos.&nbsp; More info at https://hackolade.com/help/Generatemockdatafortesting.html

\- Compare and Merge: added auto-selection of matching method when comparing models with different GUIDs

\- Compare and Merge: added display option to only show conflicts

\- Reference definitions: added support in RDBMS targets for definitions containing polymorphic choices

\- License key validation: enabled Tools \> Options so the network proxy settings can be adjusted

\- Workgroup: added auto-discovery of git.exe on Windows in likely places if not specified in system PATH

\- Workgroup: added app version, system info, git version at the top of the git log

\- Workgroup: minimized chatty git logging when auto-checking for remote commits

\- Workgroup: disallowed Review Changes in Push screen if remote branch does not exist

\- Cassandra: added generation of WHERE clause with IS NOT NULL for partition keys, clustering keys, and other selected columns in materialized views

\- MariaDB: added forward-engineering of table comments

\- MongoDB: added possibility to apply to instance Field-Level Encryption parameters in createCollection scripts

\- MongoDB: added detection of Field-Level Encryption during reverse-engineering

\- Oracle: added support for reverse-engineering of identity column

\- Snowflake: added support of identity column in properties and forward-engineering of DDL

\- Synapse: added support for forward- and reverse-engineering of partition keys

&nbsp;

New features in v6.0.8 \[13-May-2022\]

\- References to external definitions: fixed display of relative path

\- Polyglot: added creation of many-to-many join table when normalizing on-the-fly to an RDBMS target during deriving from denormalized polyglot model

\- Workgroup: added Tools \> Options Repository check for adequate Git executable when specifying a custom path

\- Workgroup: fixed refresh of model list when checking out a new branch

\- Avro: added min/max length properties for string data type, for documentation purposes only

\- Avro: added support for reverse-engineering of schemas with empty records

\- Delta Lake/Databricks: added fallback for getting view names and improve logging

\- Delta Lake/Databricks: added handling for syntax of USING, BLOOMFILTER, TBLPROPERTIES, and PARTITIONED BY when reverse-engineering from HQL file

\- Delta Lake/Databricks:&nbsp; added support for forward- and reverse-engineering of DISABLE NOVALIDATE

\- Hive:&nbsp; added support for forward- and reverse-engineering of DISABLE NOVALIDATE

\- MongoDB version 5 and higher: added support for Time-Series collections

\- OpenAPI and EventBridge Schema Registry: added support for media type including dots

\- Redshift: added support for forward- and reverse-engineering of schema, table, and column comments

\- Synapse: added support for partitioning

&nbsp;

New features in v6.0.7 \[06-May-2022\]

\- Added handling of circular external references in JSON Schema&nbsp;

\- Added warning when enumerations are not unique

\- Compare \& Merge: added dialog asking user to handle unsaved changes

\- Compare \& Merge: moved button to generate delta model to the Compare panel

\- Introduced a Read-Only mode for delta models (and future use in model history view of Workgroup Edition)

\- Workgroup Edition: disabled auto-loading of last repository when using the Command-Line Interface

\- Delta Lake: fixed issue when Partition Key was a reference to a definition/UDT

\- MongoDB: re-enabled relationship properties for binary data type

\- Oracle: added generation of constraint names in DDL for composite primary and unique keys

\- Oracle: added support for identity start and increment

&nbsp;

New features in v6.0.6 \[29-Apr-2022\]

\- Excel export/import: added handling of font size and colors for entities and views

\- Excel export: added to the relationships tab the names of parent \& child entities and attributes to illustrate GUIDs

\- External references: added a warning when user attempts to self-reference the model, given the risks of circular references

\- License validation: added version number to UserData1

\- Polyglot: enabled composite Primary Keys and Unique Keys

\- Workgroup: added author and date of last commit to Explore \> Models and All Files table

\- Azure Blob Storage and Azure Data Lake Storage for JSON and Avro: added 3 authentication methods: Anonymous, Shared Access Signature, and Shared Access Token per container

\- Delta Lake: removed unused modules async and thrift from plugin

\- Synapse forward-engineering of ALTER scripts from delta model: added a flag to explicitly un-comment DROP statements, signifying the understanding of the possible consequences

&nbsp;

New features in v6.0.5 \[22-Apr-2022\]

\- Improved application startup performance with streamlined license validation process on Windows

\- Custom properties: added handling of property names collision with reserved JSON Schema keywords

\- JSON Schema Preview: added resolution of references in choices

\- Tools \> Options: added preservation of changes when changing tabs until applied or exist with OK

\- Polyglot: added composite Foreign Key relationships

\- Workgroup: added Review Changes capability to Commit, Pull, and Push screens

\- Workgroup: added display of Git badges on Welcome Page if recent files or recent folders are git-enabled

\- Workgroup: updated simple-git library to latest version 3.6.0

\- Cosmos DB Gremlin: added validation of endpoint in connection settings

\- Delta Lake/Databricks: added reverse-engineering of database location

\- Delta Lake/Databricks: added forward-engineering of reference descriptions in column comments

\- ScyllaDB: caught up with latest Cassandra plugin developments

&nbsp;

New features in v6.0.4 \[18-Apr-2022\]

\- Tech refresh of Electron (v17.4.0), NodeJS (v16.13.0), Chromium (v98.0.4757.141), and Electron-related modules.&nbsp; Addresses Chromium V8 CVE-2022-1096 vulnerability

\- ERD: added shortcut Ctrl+Shift+T (Cmd+Shift+T on Mac) to open the selected entity(ies) in a new tab&nbsp;

\- Compare \& Merge: improved visibility of display options

\- Excel options: moved loading of parameters from application start to forward- and reverse-engineering actions

\- Polyglot: made it more obvious that deriving a target model must be done by first creating a target model from which the pulling action must be performed

\- Polyglot: added possibility to derive a polyglot model from another polyglot model

\- References: added possibility for entities to reference model and external definitions

\- Cassandra: adjusted sequence of ALTER statements from delta model to RELOAD SEARCH INDEX after DROP

\- Hive forward-engineering of ALTER scripts from delta model: added a flag to explicitly un-comment DROP statements, signifying the understanding of the possible consequences

\- Neo4j: updated plugin to latest driver version 4.4.5

\- Redshift forward-engineering of ALTER scripts from delta model: added a flag to explicitly un-comment DROP statements, signifying the understanding of the possible consequences

&nbsp;

New features in v6.0.3 \[08-Apr-2022\]

\- Added shortcuts to move between contexts (Data Modeling, Repository, etc...- as well as in View menu

\- Compare \& Merge: added display option to filter negligible properties (descriptions, comments, samples, defaults)

\- DDL reverse-engineering: added handling of not-encoded special characters in comments

\- Plugin Manager: added logging for steps plugin installation for better troubleshooting

\- Workgroup: added list of recent repositories in Welcome screen

\- Workgroup: added auto-detect of remote commits

\- Workgroup: added Discard action in commit local changes pane

\- Workgroup: added support for multiple selection in commit local changes pane

\- Workgroup: ensured auto-commit of pulled changes if default changed in Git global config

\- Workgroup: added binding of Enter key to primary action in Repository Context

\- Workgroup: added conflict resolution on repos without remote

\- Workgroup: enhanced Git error dialog to allow copy/paste of message and opening of log file

\- Workgroup: added message when push/pull actions are attempted while offline

\- BigQuery: updated library for parsing views

\- Cassandra: added property and CQL script for search index column option {lowercase: true} &nbsp;

\- Cassandra: adjusted alter index search and alter column statements logic

\- Databricks: added support for Runtime v10

\- Delta Lake/Databricks: replaced Scala commands in forward- and reverse-engineering by Python commands, to allow more flexible security settings

\- Delta Lake forward-engineering of ALTER scripts from delta model: added a flag to explicitly un-comment DROP statements, signifying the understanding of the possible consequences

\- MarkLogic: updated SDK driver version

\- MongoDB Field-Level Encryption: added rule to linter so as to identify cases when encryptMetadata keyId is missing in parent

\- Protobuf: added reverse-engineering of top-level messages as separate entities created from model definitions when "separate schemas" option is chosen

\- Snowflake: added inference of case-sensitive object names in reverse-engineering of file and instance

&nbsp;

New features in v6.0.2 \[04-Apr-2022\]

\- BigQuery forward-engineering of ALTER scripts from delta model: added a flag to explicitly un-comment DROP statements, signifying the understanding of the possible consequences

&nbsp;

New features in v6.0.1 \[01-Apr-2022\]

\- Workgroup: added auto-resolution of Git conflicts affecting data model metadata

&nbsp;

New features in v6.0.0 \[31-Mar-2022\]

\- \[Optional\] Workgroup Edition: for teams to collaborate on data models, with versioning, branching, peer reviews, and DevOps integration through Git repositories.&nbsp; More info at https://hackolade.com/help/Repository.html&nbsp; Requires the purchase of an upgrade license key from Professional to Workgroup.

\- Stopped including .chm user documentation in Windows installer -- up-to-date user doc online at https://hackolade.com/help

