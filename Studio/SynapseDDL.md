# Synapse DDL

As you develop the model for your Synapse instance schemas, tables, columns with their data types, as well as indexes and constraints, Hackolade dynamically generates the corresponding DDL scripts:&nbsp;

&nbsp;

![Image](<lib/Synapse%20DDL%20forward-engineering.png>)

&nbsp;

If you store JSON within (N)VARCHAR(MAX) or (N)VARCHAR(4000) columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
