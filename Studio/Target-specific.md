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

![Script generation parameters](<lib/Script generation parameters.png>)

&nbsp;

It is also available from a button at the bottom of the DDL script tab, and from a button at the bottom of the forward-engineering table selection dialog:

&nbsp;

![Image](<lib/Script generation options.png>)

&nbsp;

&nbsp;

