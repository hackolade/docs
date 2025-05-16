# PostgreSQL DDL

Hackolade dynamically generates the DDL script to create databases, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![PostgreSQL DDL forward-engineering](<lib/PostgreSQL DDL forward-engineering.png>)

&nbsp;

If you store documents in JSON or JSONB columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
