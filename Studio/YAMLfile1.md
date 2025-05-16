# YAML file

Hackolade dynamically generates a sample document in JSON or YAML as you construct the document fields and structure.&nbsp; You may even define the sample data you wish to see appear in that sample document.&nbsp; The sample document can be viewed in the right-hand pane of the JSON Preview tab:

![YAML Document](<lib/YAML Document.png>)

&nbsp;

To create a YAML document file of your entity, choose the menu Tools \> Forward Engineering \> YAML Document:

&nbsp;

![Forward-Engineering - YAML Document](<lib/Forward-Engineering - YAML Document.png>)

&nbsp;

In case of a choice (oneOf or anyOf) the following logic is used for the YAML Data document generation:

Subschema for generation is choosing by priority:

1. Fields with user defined "sample"/"default" property
1. Non empty "array"/"object" fields 
1. Any other fields with not “null” YAML Data sample
1. “Null" fields

