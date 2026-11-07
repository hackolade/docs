---
description: Hackolade Studio generates the HiveQL script for Delta Lake databases, tables, columns and views, and applies it to a Databricks instance.
seoTitle: Generate Delta Lake scripts for Databricks
image: lib/Delta Lake forward-engineering.png
---
# Delta Lake scripts

Hackolade dynamically generates the HiveQL script to create databases, tables, columns and their data types, as well as views for the structure created with the application.

The script can also be exported to the file system via the menu Tools > Forward-Engineering, or via the [Command-Line Interface](CommandLineInterface.md).

![Delta Lake forward-engineering](<lib/Delta Lake forward-engineering.png>)

By pressing the button "Apply to instance" the system will automatically creates the database, tables, views, columns, including constraints and indexes.

> [!NOTE]
> As foreign keys and primary keys are not supported in Delta Lake, they can be used in Hackolade for informational purposes, but are not generated in the HQL script.

As many people store JSON within text columns, Hackolade allows for the schema design of those documents. That JSON structure is not forward-engineered, but is useful for developers, analysts and designers. It is often integrated into a CI/CD pipeline, using the [Command-Line Interface](CommandLineInterface.md).
