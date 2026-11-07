---
description: Hackolade Studio generates Redshift DDL for schemas, tables, columns and constraints, to export or apply to an instance.
seoTitle: Generate Amazon Redshift DDL
image: lib/Redshift DDL forward-engineering.png
---
# Redshift DDL

As you develop the model for your Amazon Redshift database schemas, tables, columns with their data types, as well as columns-level constraints, Hackolade dynamically generates the corresponding DDL scripts.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![Redshift DDL forward-engineering](<lib/Redshift DDL forward-engineering.png>)

A button lets the user apply to a selected instance the script to create schemas, tables and views.

If you store JSON within SUPER columns, Hackolade allows for the schema design of those documents. However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
