# Generate SQL views from a SELECT AS statement

When modeling views for RDBMS or a SQL-like target, you can manually select the columns to be included in the view, by following the instructions in [this page](<Read-onlyviews.md>).

&nbsp;

You may also specify a SELECT AS statement in the corresponding property in the Properties Pane.&nbsp; This information is stored as text and used to generate the appropriate script in forward-engineering. &nbsp;

&nbsp;

![View SELECT statement](<lib/View SELECT statement.png>)

&nbsp;

However, it does not automatically create the view attributes in the model.

&nbsp;

&nbsp;

![View with no columns despite SELECT statement](<lib/View with no columns despite SELECT statement.png>)

&nbsp;

&nbsp;

If you want the view attributes to appear in your model (ERD and ERDVs), you can use the following steps:

&#49;. Perform a forward-engineering to generate the script to file, via Tools \> Forward-Engineer \> DDL.&nbsp; Make sure that all the tables referenced by the view are included in the script — this is required for the process to work.

&#50;. Perform a reverse-engineering **in the same model**, with Tools \> Reverse-Engineer \> Data Definition Language File..., then select the matching database, choose the DDL file created in step 2, and select the same schema:

&nbsp;

![View reverse-engineer from DDL select schema](<lib/View reverse-engineer from DDL select schema.png>)

&nbsp;

&#51;. During the reverse operation, a conflict detection dialog appears, where you must choose to Merge (plus it is suggested that you check the Apply to all option.)

![View reverse-engineer conflict resolution](<lib/View reverse-engineer conflict resolution.png>)

&nbsp;

&nbsp;

This process recreates the view in the model, with its columns properly represented as attributes, based on the SELECT statement originally submitted:

![View reverse-engineer SELECT AS statement](<lib/View reverse-engineer SELECT AS statement.png>)

&nbsp;

