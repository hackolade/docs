# MariaDB

As you develop the model for your MariaDB databases, tables, columns with their data types, as well as indexes and constraints, functions and procedures, Hackolade dynamically generates the corresponding DDL scripts:

&nbsp;

![Image](<lib/MariaDB%20DDL%20Forward-Engineering.png>)

&nbsp;

If you store JSON within LONGTEXT columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

