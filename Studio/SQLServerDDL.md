# SQL Server DDL

As you develop the model for your SQL Server database schemas, tables, columns with their data types, as well as indexes and constraints, Hackolade dynamically generates the corresponding DDL scripts:

&nbsp;

![Image](<lib/SQL%20Server%20DDL%20Forward-Engineering.png>)

&nbsp;

If you store JSON within (N)VARCHAR(MAX) or (N)VARCHAR(4000) columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

***
_Created with the Personal Edition of HelpNDoc: [Single source CHM, PDF, DOC and HTML Help creation](<https://www.helpndoc.com/help-authoring-tool>)_
