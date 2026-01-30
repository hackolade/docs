# Synapse DDL

As you develop the model for your Synapse instance schemas, tables, columns with their data types, as well as indexes and constraints, Hackolade dynamically generates the corresponding DDL scripts.

&nbsp;

The script can also be exported to the file system via the menu Tools \> Forward-Engineering, or via the [Command-Line Interface](<CommandLineInterface.md>).

&nbsp;

![Synapse DDL forward-engineering](<lib/Synapse DDL forward-engineering.png>)

&nbsp;

If you store JSON within (N)VARCHAR(MAX) or (N)VARCHAR(4000) columns, Hackolade allows for the schema design of those documents.&nbsp; However, the corresponding JSON structure is **not** forward-engineered in the DDL script, but is useful for developers, analysts and designers.

&nbsp;

&nbsp;

&nbsp;

## Known limitations of the DDL generation configuration

About the feature detailed [here](<https://hackolade.com/help/Target-specific.html#Script%20generation%20parameters>).

### DEFAULT constraint

Synapse requires a name for default constraint in alter statement. Default constraint name can be specified by the user in the PP.

&nbsp;

If the user chooses “in a separate statement” for default constraint and he doesn’t fill a default constraint name in PP, the unnamed default constraint won’t be present in the script, in order to avoid error on script execution.

&nbsp;

This remark is only applicable to default constraints. Synapse doesn’t require a name for the other constraints in alter statement (PK, UK, Not null).

&nbsp;

### DROPping constraints

Synapse requires a name constraint in the “drop” statement to remove a constraint. If a constraint must be removed in a delta model, the alter script will only contain the drop statement for the \*named\* constraints. As already discussed, user is currently not able to specify name for single UK and single PK. We decided to park this till a customer requests for it.

&nbsp;

