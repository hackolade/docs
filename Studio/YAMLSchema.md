# YAML Schema

If you wish to include the schema for a YAML Schema file in an existing model, the process is slightly different.&nbsp; With your model already opened, choose Tools \> Reverse-Engineer \> YAML Schema. &nbsp;

&nbsp;

![Tools - Reverse-Engineer - YAML Schema](<lib/Tools - Reverse-Engineer - JSON Schema.png>)

&nbsp;

&nbsp;

&nbsp;

The structure of a JSON Schema can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

&nbsp;

![YAML Schema reverse-engineering dialog](<lib/JSON Schema RE dialog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

&nbsp;

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

&nbsp;

![YAML Schema reverse-engineering dialog - normalization](<lib/JSON Schema RE dialog - normalization.png>)

