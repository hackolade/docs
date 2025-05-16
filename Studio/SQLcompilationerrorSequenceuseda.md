# SQL compilation error:Sequence used as a default value in table... was not found or could not be accessed

During reverse-engineering of a Snowflake instance, you may be surprised to find that, while the operation worked very well for most tables, one or more tables do not display the expected columns.

&nbsp;

You should first check the reverse-engineering log HackoladeRE.log that can he found:

\- Windows: in the C:\\Users\\%username%\\AppData\\Roaming\\HackoladeLogs directory

\- Mac/Linux: in the Users/$USER/Documents/HackoladeLogs folder.

&nbsp;

Please read the information below if the log file contains one or more lines like this:

> SQL compilation error: Sequence used as a default value in table '\<table-name\>' column '\<column-name\>' was not found or could not be accessed.

> &nbsp;

This is not a Hackolade issue, but rather the sign of an issue in your Snowflake instance, with cause and solution well documented in [this Snowflake Community article](<https://community.snowflake.com/s/article/ERROR-SQL-compilation-error-Sequence-used-as-a-default-value-in-table-table-name-column-column-name-was-not-found-or-could-not-be-accessed> "target=\"\_blank\"").

&nbsp;

This error happens while calling GET\_DDL() function for a table if a Sequence, referenced in a column for its Default value, has been dropped. Our reverse-engineering process relies on the proper response to our calling the GET\_DDL() Snowflake function.

&nbsp;

The most important thing to avoid this error is to be careful when dropping a Sequence. It is recommended to verify the Sequence to be dropped is not referred to in any of the columns of any of the tables.

&nbsp;

If the Sequence has already been dropped and the above error is returned, alter the table to remove the default value from the column or change the referring sequence to any new sequence as shown below to fix the issue:

&nbsp;

> \-- Remove the default value\
alter table \<table-name\> modify column \<column-name\> drop default;

&nbsp;

> \-- Or, change the referring sequence to new one\
create or replace sequence \<new-sequence-name\>\
alter table \<table-name\> modify column \<column-name\> default \<new-sequence-name\>.nextval;

> &nbsp;

Once the change has taken place, you may restart the reverse-engineering process which should now succeed, provided that Snowflake encounters no additional issues. &nbsp;

