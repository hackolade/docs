---
description: Import a YAML Schema file into a new or existing Hackolade Studio model, as an entity or as definitions.
seoTitle: Reverse-engineer YAML Schema files
image: lib/JSON Schema RE dialog.png
---
# YAML Schema

If you wish to include the schema for a YAML Schema file in an existing model, the process is slightly different. With your model already opened, choose Tools > Reverse-Engineer > YAML Schema.

![Tools - Reverse-Engineer - YAML Schema](<lib/Tools - Reverse-Engineer - JSON Schema.png>)

The structure of a JSON Schema can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

![YAML Schema reverse-engineering dialog](<lib/JSON Schema RE dialog.png>)

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

For RDBMS targets, an additional option appears, that allows automatic normalization of complex data types:

![YAML Schema reverse-engineering dialog - normalization](<lib/JSON Schema RE dialog - normalization.png>)
