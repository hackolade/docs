# JSON Schema

If you open a JSON Schema from the file system, Hackolade will detect its nature and will execute the reverse-engineering of that JSON Schema.&nbsp; You will need to choose a database target for your model.

&nbsp;

If you wish to include the schema for a JSON Schema file in an existing model, the process is slightly different.&nbsp; With your model already opened, choose Tools \> Reverse-Engineer \> JSON Schema. &nbsp;

&nbsp;

![Image](<lib/Tools%20-%20Reverse-Engineer%20-%20JSON%20Schema.png>)

&nbsp;

&nbsp;

&nbsp;

The structure of a JSON Schema can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

![Image](<lib/JSON%20Schema%20RE%20dialog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

&nbsp;

![Image](<lib/JSON%20Schema%20RE%20dialog%20-%20normalization.png>)


***
_Created with the Personal Edition of HelpNDoc: [Easy to use tool to create HTML Help files and Help web sites](<https://www.helpndoc.com/help-authoring-tool>)_
