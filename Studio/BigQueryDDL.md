---
description: Hackolade Studio generates BigQuery DDL for datasets, tables, columns and views, or JSON schema, and applies it to an instance.
seoTitle: Generate BigQuery DDL from a data model
image: lib/BigQuery DDL forward-engineering.png
---
# BigQuery DDL

Hackolade dynamically generates the DDL script to create datasets, tables, columns and their data types, for the structure created with the application.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![BigQuery DDL forward-engineering](<lib/BigQuery DDL forward-engineering.png>)

A button lets the user apply to a selected instance the script to create datasets, tables and views. Scripts can be generated in JSON Schema format as well.
