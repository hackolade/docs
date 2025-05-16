# SQL Server DDL

As you develop the model for your SQL Server database schemas, tables, columns with their data types, as well as indexes and constraints, Hackolade dynamically generates the corresponding DDL scripts.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![SQL Server DDL Forward-Engineering](<lib/SQL Server DDL Forward-Engineering.png>)

&nbsp;

If you store JSON within (N)VARCHAR(MAX) or (N)VARCHAR(4000) columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
