# YAML Schema

To create a YAML Schema file of your entity, choose the menu Tools \> Forward Engineering \> YAML Schema:

&nbsp;

![Image](<lib/Forward-Engineering%20-%20YAML%20Schema.png>)

&nbsp;

then select the directory path and file name.

&nbsp;

The YAMLSchema for the entity can also be viewed in the left-hand pane of the JSON Preview tab:

&nbsp;

![Image](<lib/Forward-Engineering%20-%20YAML%20Preview.png>)

&nbsp;

&nbsp;

Several important options are available:

&#49;) YAML Schema compliance:

\- standard: only YAML Schema keywords and data types are used -- this output should pass validation with standard validators

\- full: custom keywords are also listed for a full view of the schema, but only standard YAML data types are used -- this output should pass validation as long as additionalProperties are set to true

\- extended: data types are specific to the target of the model, plus internal properties and keywords are also listed. &nbsp;

&nbsp;

**Important note:** in extended compliance, it is normal that the exported YAML Schema does not pass the test of validators.&nbsp; This is because data types used for a given target may be non-YAML data types.&nbsp; For example ObjectId for MongoDB, or UUID in Cassandra, etc...

&nbsp;

&#50;) Definitions:

\- referenced: definitions are referenced as described in the model, using $ref syntax

\- resolved:: definitions are resolved to list the content of the reference.

\- internal: references to external and model definitions are converted into internal definitions


***
_Created with the Personal Edition of HelpNDoc: [Easily create PDF Help documents](<https://www.helpndoc.com/feature-tour>)_
