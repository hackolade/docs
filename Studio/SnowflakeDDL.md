# Snowflake DDL

As you develop the model for your Snowflake database schemas, tables, columns with their data types, as well as columns-level constraints, Hackolade dynamically generates the corresponding DDL scripts:

&nbsp;

![Image](<lib/Snowflake%20DDL%20forward-engineering.png>)

&nbsp;

If you store JSON within VARIANT columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

***
_Created with the Personal Edition of HelpNDoc: [News and information about help authoring tools and software](<https://www.helpauthoringsoftware.com>)_
