# v6.x

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

