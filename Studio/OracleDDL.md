# Oracle DDL

Hackolade dynamically generates the DDL script to create schemas, tables, columns and their data types, indexes and constraints for the structure created with the application, as well as functions and procedures.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Oracle DDL forward-engineering](<lib/Oracle DDL forward-engineering.png>)

&nbsp;

In order to apply scripts to an instance, it is necessary for the user to be granted at least the proper privileges:

CREATE USER

CREATE TABLE or CREATE ANY TABLE

CREATE VIEW or CREATE ANY VIEW with READ ANY TABLE or SELECT ANY TABLE system privilege, possibly with SELECT ON schema tables for cross-schema views

CREATE MATERIALIZED VIEW&nbsp; or CREATE ANY MATERIALIZED VIEW

CREATE SYNONYM or CREATE ANY SYNONYM or CREATE PUBLIC SYNONYM

CREATE INDEX or CREATE ANY INDEX 

CREATE REFERENCES

&nbsp;

&nbsp;

If you store documents in JSON columns (21c and above) or for 12c thru 19c in BLOB columns, as well as VARCHAR2 or CLOB, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.
