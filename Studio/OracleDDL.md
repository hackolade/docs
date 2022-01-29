# Oracle DDL

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

![Oracle DDL forward-engineering](<lib/Oracle%20DDL%20forward-engineering.png>)

&nbsp;

If you store documents in JSON columns (21c and above) or for 12c thru 19c in BLOB columns, as well as VARCHAR2 or CLOB, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
