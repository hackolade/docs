# JSON Schema

To create a JSON Schema file of your entity, choose the menu Tools \> Forward Engineering \> JSON Schema:

![Image](<lib/Forward-Engineering%20-%20JSON%20Schema.png>)

&nbsp;

then select the directory path and file name.

&nbsp;

The JSON Schema for the entity can also be viewed in the left-hand pane of the JSON Preview tab:

&nbsp;

&nbsp;

![Image](<lib/Forward-Engineering%20-%20JSON%20Preview.png>)

&nbsp;

&nbsp;

Several important options are available:

&#49;) JSON Schema compliance:

\- standard: only JSON Schema keywords and data types are used -- this output should pass validation with standard validators

\- full: custom keywords are also listed for a full view of the schema, but only standard JSON data types are used -- this output should pass validation as long as additionalProperties are set to true

\- extended: data types are specific to the target of the model, plus internal properties and keywords are also listed. &nbsp;

&nbsp;

**Important note:** in extended compliance, it is normal that the exported JSON Schema does not pass the test of validators.&nbsp; This is because data types used for a given target may be non-JSON data types.&nbsp; For example ObjectId for MongoDB, or UUID in Cassandra, etc...

&nbsp;

&#50;) JSON Schema specification:output is dynamically adapted to the selected specification:

\- [draft-04](<https://json-schema.org/specification-links.html#draft-4> "target=\"\_blank\"")

\- [draft-06](<https://json-schema.org/specification-links.html#draft-6> "target=\"\_blank\"")

\- [draft-07](<https://json-schema.org/specification-links.html#draft-7> "target=\"\_blank\"")

\- [2019-09](<https://json-schema.org/specification-links.html#2019-09-formerly-known-as-draft-8> "target=\"\_blank\"")

&nbsp;

&#51;) Definitions:

\- referenced: definitions are referenced as described in the model, using $ref syntax

\- resolved:: definitions are resolved to list the content of the reference.

\- internal: references to external and model definitions are converted into internal definitions

