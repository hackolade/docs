# YAML file

If you wish to include the schema for a [YAML](<https://blog.stackpath.com/yaml/> "target=\"\_blank\"") file in an existing model, with your model already opened, choose Tools \> Reverse-Engineer \> JSON document. &nbsp;

&nbsp;

![Image](<lib/Tools%20-%20Reverse-Engineer%20-%20JSON%20document.png>)

&nbsp;

&nbsp;

The process includes detection of ISO 8601 date/time/timestamp/duration in strings when target supports such data types.\
&nbsp;

The structure of a [YAML](<https://yaml.org/spec/1.2/spec.html> "target=\"\_blank\"") file can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

&nbsp;

![Image](<lib/JSON%20Doc%20RE%20dailog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

More information on YAML and JSON Schema [here](<https://json-schema-everywhere.github.io/yaml> "target=\"\_blank\"") and [here](<https://asdf-standard.readthedocs.io/en/1.5.0/schemas/yaml\_schema.html#yaml-schema-draft-01> "target=\"\_blank\"").&nbsp;

&nbsp;

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

&nbsp;

![Image](<lib/JSON%20Schema%20RE%20dialog%20-%20normalization.png>)

***
_Created with the Personal Edition of HelpNDoc: [Create HTML Help, DOC, PDF and print manuals from 1 single source](<https://www.helpndoc.com/help-authoring-tool>)_
