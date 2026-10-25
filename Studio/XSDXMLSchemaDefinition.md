# XSD (XML Schema Definition)

> [!IMPORTANT]
> The purpose of this functionality is NOT to provide full compatibility with XSD syntax, but just to import models from other ER tools. As a a result, Hackolade does **not** currently support, among other things, mixed content types, deriving types by restriction, or XSD import and include.

&nbsp;

If you have logical or physical models in ER/Studio Architect, erwin, InfoSphere, PowerDesigner, or others, you may want to import them into Hackolade.

&nbsp;

To do so, you need to first export your model to an XSD schema. Please refer to your ER tool's documentation for more info.

&nbsp;

Then, go to Tools > Reverse-Engineer > XSD Schema and choose the file exported.

&nbsp;

![Tools - Reverse-Engineer - XSD Schema](<lib/Tools - Reverse-Engineer - XSD Schema.png>)

&nbsp;

The structure of an XSD can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

&nbsp;

![XSD RE dialog](<lib/XSD RE dialog.png>)

&nbsp;

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

Your next steps might be to start denormalizing and embedding, using this Hackolade [function](SuggestdenormalizationofaSQLsche.md).

&nbsp;

For specific instructions on configuration to export XSD, please refer to the respective pages:

- [erwin](Fromerwin.md)
- [ER/Studio](FromERStudio.md)

&nbsp;

XSDs can be imported in Hackolade:

- as entities in the ER diagram (not available for Swagger or OpenAPI targets)
- as model definitions to be reused anywhere in the model

&nbsp;

Sometimes with logical models exported from some ER tools likes erwin, they replace spaces in object names with underscores. When importing those models into a Hackolade Studio polyglot model, it might be desirable to restore object names to a regular business name. To that effect, we provide the option to perform a case conversion upon import. Proper Case or Title Case are likely candidates for this option.

&nbsp;

## XML Schema Definition conversion in Hackolade

An XSD defines the structure of an XML document. It specifies the elements and attributes that can appear in an XML document and the type of data these elements and attributes can contain.

&nbsp;

### XSD Elements

Element structures can be of *simpleType* or *complexType*, depending on whether the element is a leaf element or a parent element.

&nbsp;

XSD elements can be of type *simpleType*, *complexType*, or *anyType:*

- an element of type *simpleType* contains only text. It cannot have attributes and elements.
- an element of type *complexType* can contain text, elements, and attributes. An element of type complexType is parent to all the elements and attributes contained within it.
- an *any* element in an XSD specifies that any well-formed XML is allowed in its place in XML instance.

&nbsp;

XSD attributes are always of type *simpleType*.

&nbsp;

Elements can be *local* or *global*. An element declared as the direct child of an XML schema is called a *global* element and can be used throughout the schema. Elements declared within a *complexType* definition are *local* elements. So, you cannot use these elements anywhere else in the schema.

&nbsp;

### XSD Attributes

XSD attributes are always of type *simpleType*.

&nbsp;

Attributes are stored as member of the object created for the parent element. An attribute group defines an association between a name and a set of attribute declarations. You can reuse the attribute groups in complexType definitions.

&nbsp;

An attribute group defines an association between a name and a set of attribute declarations. Attribute groups can be reused in `complexType` definitions.

&nbsp;

### XSD Type Definitions

XSD Type definitions are used to create new *simpleType* data type or *complexType* data type. A type definition that is used as a base for creating new definitions is known as the base type definition. A *simpleType* or *complexType* type can be either named or anonymous. A named simpleType or complexType is always defined globally. You can define a named simpleType or complexType and refer it in schema document as type of an element. An anonymous simpleType or complexType type does not have a name. So, an anonymous simpleType or complexType type cannot be referenced.

&nbsp;

A *simpleType* type is derived from an XML schema built-in data type. A *complexType* type definition contains a set of element declarations, element references, and attribute declarations.A *complexType* type is first defined in the schema, and then the elements and attributes of this *complexType* type.

&nbsp;

Below is the data type conversion from XSD to JSON Schema. Some additional granularity is possible with some targets.

&nbsp;

<table>
<colgroup><col style="width:29%"><col style="width:71%"></colgroup>
<thead>
<tr>
<th>XML Schema Type</th>
<th>JSON Schema Representation</th>
</tr>
</thead>
<tbody>
<tr>
<td>anySimpleType</td>
<td>string, number, integer, boolean, null</td>
</tr>
<tr>
<td>anyType</td>
<td>string, number, integer, boolean, null, object, array</td>
</tr>
<tr>
<td>string</td>
<td>string</td>
</tr>
<tr>
<td>normalizedString</td>
<td>string</td>
</tr>
<tr>
<td>token</td>
<td>string</td>
</tr>
<tr>
<td>language</td>
<td>string</td>
</tr>
<tr>
<td>Name</td>
<td>string</td>
</tr>
<tr>
<td>NCName</td>
<td>string</td>
</tr>
<tr>
<td>ID</td>
<td>string</td>
</tr>
<tr>
<td>IDREF</td>
<td>string</td>
</tr>
<tr>
<td>IDREFS</td>
<td>array of strings</td>
</tr>
<tr>
<td>ENTITY</td>
<td>string</td>
</tr>
<tr>
<td>ENTITIES</td>
<td>array of strings</td>
</tr>
<tr>
<td>NMTOKEN</td>
<td>string</td>
</tr>
<tr>
<td>NMTOKENS</td>
<td>array of strings</td>
</tr>
<tr>
<td>boolean</td>
<td>boolean</td>
</tr>
<tr>
<td>base64Binary</td>
<td>binary | string</td>
</tr>
<tr>
<td>hexBinary</td>
<td>string</td>
</tr>
<tr>
<td>float</td>
<td>number</td>
</tr>
<tr>
<td>double</td>
<td>number</td>
</tr>
<tr>
<td>decimal</td>
<td>number</td>
</tr>
<tr>
<td>integer</td>
<td>integer</td>
</tr>
<tr>
<td>nonPositiveInteger</td>
<td>integer</td>
</tr>
<tr>
<td>negativeInteger</td>
<td>integer</td>
</tr>
<tr>
<td>long</td>
<td>integer</td>
</tr>
<tr>
<td>int</td>
<td>integer</td>
</tr>
<tr>
<td>short</td>
<td>integer</td>
</tr>
<tr>
<td>byte</td>
<td>integer</td>
</tr>
<tr>
<td>nonNegativeInteger</td>
<td>integer</td>
</tr>
<tr>
<td>unsignedLong</td>
<td>integer</td>
</tr>
<tr>
<td>unsignedInt</td>
<td>integer</td>
</tr>
<tr>
<td>unsignedShort</td>
<td>integer</td>
</tr>
<tr>
<td>unsignedByte</td>
<td>integer</td>
</tr>
<tr>
<td>positiveInteger</td>
<td>integer</td>
</tr>
<tr>
<td>anyURI</td>
<td>string with "format":"uri"</td>
</tr>
<tr>
<td>QName</td>
<td>object with "namespaceURI", "localPart", "prefix"</td>
</tr>
<tr>
<td>duration</td>
<td>string with ‘format: “duration”</td>
</tr>
<tr>
<td>dateTime</td>
<td>string with "format":"date-time"</td>
</tr>
<tr>
<td>date</td>
<td>string with "format":"date"</td>
</tr>
<tr>
<td>time</td>
<td>string with "format":"time"</td>
</tr>
</tbody>
</table>
