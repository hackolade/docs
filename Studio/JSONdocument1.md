# JSON document

If you open a JSON document from the file system, Hackolade will detect its nature and will execute the reverse-engineering of that document.&nbsp; You will need to choose a database target for your model.

&nbsp;

If you wish to include the schema for a JSON document in an existing model, the process is slightly different.&nbsp; With your model already opened, choose Tools \> Reverse-Engineer \> JSON document. &nbsp;

![Image](<lib/Tools%20-%20Reverse-Engineer%20-%20JSON%20document.png>)

&nbsp;

&nbsp;

The process includes detection of ISO 8601 date/time/timestamp/duration in strings when target supports such data types.\
\
Hackolade also supports Newline Delimited JSON as described in [https://ndjson.org/](<http://ndjson.org/> "target=\"\_blank\"")

&nbsp;

The structure of a JSON document can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

![Image](<lib/JSON%20Doc%20RE%20dailog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

&nbsp;

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

&nbsp;

![Image](<lib/JSON%20Schema%20RE%20dialog%20-%20normalization.png>)

