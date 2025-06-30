# Delta Lake scripts

Hackolade dynamically generates the HiveQL script to create databases, tables, columns and their data types, as well as views for the structure created with the application.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Delta Lake forward-engineering](<lib/Delta Lake forward-engineering.png>)

&nbsp;

By pressing the button "Apply to instance" the system will automatically creates the database, tables, views, columns, including constraints and indexes.

&nbsp;

**Note:** As foreign keys and primary keys are not supported in Delta Lake, they can be used in Hackolade for informational purposes, but are not generated in the HQL script.

&nbsp;

As many people store JSON within text columns, Hackolade allows for the schema design of those documents.  That JSON structure is not forward-engineered, but is useful for developers, analysts and designers.&nbsp; It is often integrated into a CI/CD pipeline, using the [Command-Line Interface](<CommandLineInterface.md>).

