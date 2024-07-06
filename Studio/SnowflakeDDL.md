# Snowflake DDL

As you develop the model for your Snowflake database schemas, tables, columns with their data types, as well as columns-level constraints, Hackolade dynamically generates the corresponding DDL scripts.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Snowflake DDL forward-engineering](<lib/Snowflake%20DDL%20forward-engineering.png>)

&nbsp;

If you store JSON within VARIANT columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
