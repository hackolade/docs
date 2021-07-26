# v5.x

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

