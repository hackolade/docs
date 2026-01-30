# Target-specific

Forward-engineering scripts vary widely between target technologies, as each one has developed its own storage model, terminology, syntax, data types, indexing and partitioning, etc.For details, you should consult the applicable page&nbsp;

&nbsp;

**Note:** this capability is only available in the Professional, Workgroup, and Free Trial editions of Hackolade Studio.

&nbsp;

&nbsp;

## Script generation parameters

With v8.2.3, we started to introduce parameters to allow you to adjust the DDL script generation according to your preferences.&nbsp; This may be for styling purposes, or more importantly for data loading or performances reasons.&nbsp; Additionally, it may allow you to document data models constraints that you do not want to have enforced by the database engine.

&nbsp;

The configuration is available from Tools \> Options \> Forward-Engineering \> Script Generation:

&nbsp;

![Script generation options](<lib/Script generation options.png>)

&nbsp;

&nbsp;

It is also available from a button at the bottom of the DDL script tab, and from a button at the bottom of the forward-engineering table selection dialog.

&nbsp;

![Script generation parameters](<lib/Script generation parameters.png>)

&nbsp;

Script generation parameters are persisted in a JSON file script-generation-options.json stored in the C:\\Users\\Pascal\\.hackolade\\options\\\<target\> folder.

&nbsp;

## Script generation parameters when using the CLI

When running the [Command-Line Interface](<CommandLineInterface.md>) locally, it accesses the same configuration file as persisted by editing your preferences in the GUI application, i.e., the file script-generation-options.json stored in the C:\\Users\\Pascal\\.hackolade\\options\\\<target\> folder.

&nbsp;

When running the CLI on a server, you must copy the script-generation-options.json file and paste in the appropriate .hackolade\\options\\\<target\> folder of the CLI instance. &nbsp;

&nbsp;

If running the [CLI in Docker](<https://github.com/hackolade/docker/blob/main/Studio/README.md> "target=\"\_blank\""), you must paste the script-generation-options.json file in the appropriate location, as described [here](<https://github.com/hackolade/docker/blob/main/Studio/README.md#custom-properties-naming-conventions-excel-export-options> "target=\"\_blank\"").

&nbsp;

&nbsp;

