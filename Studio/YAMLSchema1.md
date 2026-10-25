# YAML Schema

To create a YAML Schema file of your entity, choose the menu Tools > Forward Engineering > YAML Schema:

&nbsp;

![Forward-Engineering - YAML Schema](<lib/Forward-Engineering - YAML Schema.png>)

&nbsp;

then select the directory path and file name.

&nbsp;

The YAMLSchema for the entity can also be viewed in the left-hand pane of the JSON Preview tab:

&nbsp;

![Forward-Engineering - YAML Preview](<lib/Forward-Engineering - YAML Preview.png>)

&nbsp;

Several important options are available:\
1\) YAML Schema compliance:

- standard: only YAML Schema keywords and data types are used -- this output should pass validation with standard validators
- full: custom keywords are also listed for a full view of the schema, but only standard YAML data types are used -- this output should pass validation as long as additionalProperties are set to true
- extended: data types are specific to the target of the model, plus internal properties and keywords are also listed.

&nbsp;

> [!IMPORTANT]
> In extended compliance, it is normal that the exported YAML Schema does not pass the test of validators. This is because data types used for a given target may be non-YAML data types. For example ObjectId for MongoDB, or UUID in Cassandra, etc...

&nbsp;

2\) Definitions:

- referenced: definitions are referenced as described in the model, using $ref syntax
- resolved:: definitions are resolved to list the content of the reference.
- internal: references to external and model definitions are converted into internal definitions
