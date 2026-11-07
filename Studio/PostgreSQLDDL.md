---
description: Hackolade Studio generates PostgreSQL DDL for databases, tables, indexes, constraints, functions and procedures, to export or apply.
seoTitle: Generate PostgreSQL DDL from a data model
image: lib/PostgreSQL DDL forward-engineering.png
---
# PostgreSQL DDL

Hackolade dynamically generates the DDL script to create databases, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![PostgreSQL DDL forward-engineering](<lib/PostgreSQL DDL forward-engineering.png>)

If you store documents in JSON or JSONB columns, Hackolade allows for the schema design of those documents. However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
