# JSON Document

Hackolade dynamically generates a sample document In JSON or YAML as you construct the document fields and structure.&nbsp; You may even define the sample data you wish to see appear in that sample document.&nbsp; The sample document can be viewed in the right-hand pane of the JSON Preview tab:

![JSON Document](<lib/JSON Document.png>)

&nbsp;

To create a JSON Schema file of your entity, choose the menu Tools \> Forward Engineering \> JSON Document:

&nbsp;

![Forward-Engineering - JSON Document](<lib/Forward-Engineering - JSON Document.png>)

&nbsp;

In case of a choice (oneOf or anyOf) the following logic is used for the JSON Data document generation:

Subschema for generation is choosing by priority:

1. Fields with user defined "sample"/"default" property
1. Non empty "array"/"object" fields 
1. Any other fields with not “null” JSON Data sample
1. “Null" fields

