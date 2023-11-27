# v7.x

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

