---
description: Hackolade Studio generates a sample JSON or YAML document from your model, with sample data you define for each field.
seoTitle: Generate sample JSON or YAML documents
image: lib/JSON Document.png
---
# JSON Document

Hackolade dynamically generates a sample document In JSON or YAML as you construct the document fields and structure. You may even define the sample data you wish to see appear in that sample document. The sample document can be viewed in the right-hand pane of the JSON Preview tab:\
![JSON Document](<lib/JSON Document.png>)

To create a JSON Schema file of your entity, choose the menu Tools > Forward Engineering > JSON Document:

![Forward-Engineering - JSON Document](<lib/Forward-Engineering - JSON Document.png>)

In case of a choice (oneOf or anyOf) the following logic is used for the JSON Data document generation:\
Subschema for generation is choosing by priority:

1. Fields with user defined "sample"/"default" property
2. Non empty "array"/"object" fields
3. Any other fields with not “null” JSON Data sample
4. “Null" fields
