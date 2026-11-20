---
description: Forward-engineer a Polyglot model into an xDBML document, and see which objects and properties Hackolade Studio currently exports.
seoTitle: Forward-engineer a Polyglot model to xDBML
---
# xDBML

[xDBML](<https://xdbml.org> "target=\"_blank\"") is an open specification to describe a data model as text. It goes beyond DBML, with nested objects and arrays, conceptual relationships and AI-readiness metadata. Its syntax is described in the [xDBML specification](<https://xdbml.org/spec/current> "target=\"_blank\""), and the topic [Gen-AI created xDBML](Gen-AIcreatedxDBML.md) shows a complete xDBML document.

Hackolade Studio writes xDBML in two situations: when you forward-engineer your model from the menu, and automatically "behind the scenes" when the [AI chat panel](AIchatpanel.md) reads your model to answer your prompt. Both use the same export, so the same objects are supported.

> [!IMPORTANT]
> xDBML forward-engineering currently works in Polyglot models only.

## Forward-engineer a model to xDBML

Open a Polyglot model, then go to **Tools > Forward-Engineer > xDBML...**. The **xDBML...** menu item currently appears only when the target of the model is Polyglot.

1. In the **Objects selection** dialog, choose what to export. Under the model, the dialog lists **Containers**, with the entities of each container, then **Relationships** and **Views**. Everything is selected by default. Entities that do not belong to a container are listed under **Undefined Bucket**.
2. Click **Submit**.
3. Choose the folder and the name of the file. The default file name is the technical name of the model, or its name when it has no technical name, with the extension `.xdbml`. In the browser version of Hackolade Studio, the file is downloaded instead.

The progress window confirms when the xDBML file is generated.

In the xDBML file, the data type of an attribute is its mode when it has one, such as `int32` for an integer, otherwise its Polyglot data type, such as `varchar`.

**Relationships** and **Views** export all the relationships or all the views of the model, or none. A relationship is exported only when you export both its parent entity and its child entity. A view that belongs to a container is exported only when you select that container, or some of its entities.

xDBML cannot currently be generated with the [Command-Line Interface](CommandLineInterface.md).

## Supported objects and properties

Hackolade Studio currently supports the forward-engineering of the following objects, from the menu and in the [AI chat panel](AIchatpanel.md):

- the model name and description;
- containers, with their name, description and color;
- entities, with their name, description and header color in the main ERD;
- attributes with a scalar type, an object or an array, nested at any depth, with their name, description, data type, length, precision, scale and the **Required** property;
- primary keys and unique keys, single or composite;
- foreign key, foreign master and conceptual relationships, between two entities or between their top-level attributes;
- views, with their name, description, query and the **Materialized** property.

Relationships are exported with their name, description, cardinality at each end, roles, verbs and color, and with the constraint type of a foreign key: identifying or non-identifying.

Deactivated containers, entities, attributes and views are left out of the xDBML document. A deactivated relationship is exported with the `inactive` setting.

Hackolade Studio does not support the forward-engineering of the following objects yet:

- relationships to or from a nested attribute;
- the attributes of a view;
- indexes and check constraints;
- model definitions;
- supertypes and subtypes, ERD views and annotations;
- data lineage.

For the supported objects, Hackolade Studio does not support the forward-engineering of the following properties yet:

- default values, and validation settings such as pattern, minimum or maxItems;
- the delete and update actions of a relationship;
- the header color of views, and header colors set in ERD views other than the main ERD;
- custom properties.

For a complete view, refer to the table below. The first column gives the name in Hackolade Studio, the second the name in the xDBML specification:

<table>
<colgroup><col style="width:72%"><col style="width:19%"><col style="width:9%"></colgroup>
<thead>
<tr>
<th>Hackolade Studio</th>
<th>xDBML</th>
<th>Exported</th>
</tr>
</thead>
<tbody>
<tr>
<td>Model name and description</td>
<td>project</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Container</td>
<td>container</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Entity</td>
<td>entity</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Attribute with a scalar type, an object or an array</td>
<td>field</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Primary key, single or composite</td>
<td>primary key</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Unique key, single or composite</td>
<td>unique key</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Foreign key, foreign master or conceptual relationship, between two entities or between top-level attributes</td>
<td>relationship</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>Relationship to or from a nested attribute</td>
<td>relationship</td>
<td>TBA</td>
</tr>
<tr>
<td>View, with its name, description, query and Materialized property</td>
<td>view</td>
<td>✅ Yes</td>
</tr>
<tr>
<td>View attribute</td>
<td>view field</td>
<td>Not yet</td>
</tr>
<tr>
<td>Index</td>
<td>index</td>
<td>TBA</td>
</tr>
<tr>
<td>Check constraint</td>
<td>check</td>
<td>TBA</td>
</tr>
<tr>
<td>Model definition</td>
<td>named type</td>
<td>TBA</td>
</tr>
<tr>
<td>Supertype and subtypes</td>
<td>supertype group</td>
<td>TBA</td>
</tr>
<tr>
<td>ERD view</td>
<td>diagram view</td>
<td>TBA</td>
</tr>
<tr>
<td>Annotation</td>
<td>sticky note</td>
<td>TBA</td>
</tr>
</tbody>
</table>
