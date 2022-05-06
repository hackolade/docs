# v6.x

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

