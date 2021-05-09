# JSON Document

Hackolade dynamically generates a sample document In JSON or YAML as you construct the document fields and structure.&nbsp; You may even define the sample data you wish to see appear in that sample document.&nbsp; The sample document can be viewed in the right-hand pane of the JSON Preview tab:

![Image](<lib/JSON%20Document.png>)

&nbsp;

To create a JSON Schema file of your entity, choose the menu Tools \> Forward Engineering \> JSON Document:

&nbsp;

![Image](<lib/Forward-Engineering%20-%20JSON%20Document.png>)

&nbsp;

In case of a choice (oneOf or anyOf) the following logic is used for the JSON Data document generation:

Subschema for generation is choosing by priority:

1. Fields with user defined "sample"/"default" property
1. Non empty "array"/"object" fields 
1. Any other fields with not “null” JSON Data sample
1. “Null" fields


***
_Created with the Personal Edition of HelpNDoc: [Create help files for the Qt Help Framework](<https://www.helpndoc.com/feature-tour/create-help-files-for-the-qt-help-framework>)_
