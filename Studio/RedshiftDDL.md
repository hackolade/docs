# Redshift DDL

As you develop the model for your Amazon Redshift&nbsp; database schemas, tables, columns with their data types, as well as columns-level constraints, Hackolade dynamically generates the corresponding DDL scripts:

![Image](<lib/Redshift%20DDL%20forward-engineering.png>)

&nbsp;

&nbsp;

A button lets the user apply to a selected instance the script to create schemas, tables and views.

&nbsp;

If you store JSON within SUPER columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
