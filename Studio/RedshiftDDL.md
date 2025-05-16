# Redshift DDL

As you develop the model for your Amazon Redshift&nbsp; database schemas, tables, columns with their data types, as well as columns-level constraints, Hackolade dynamically generates the corresponding DDL scripts.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Redshift DDL forward-engineering](<lib/Redshift DDL forward-engineering.png>)

&nbsp;

&nbsp;

A button lets the user apply to a selected instance the script to create schemas, tables and views.

&nbsp;

If you store JSON within SUPER columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
