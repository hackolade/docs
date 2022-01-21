# XSD of logical models

**Important note:** the purpose of this functionality is NOT to provide full compatibility with XSD syntax, but just to import models from other ER tools.&nbsp; As a a result, Hackolade does **not** currently support, among other things, mixed content types, deriving types by restriction, or XSD import and include.

&nbsp;

If you have logical or physical models in ER/Studio Architect, erwin, InfoSphere, PowerDesigner, or others, you may want to import them into Hackolade. &nbsp;

&nbsp;

To do so, you need to first export your model to an XSD schema.&nbsp; Please refer to your ER tool's documentation for more info. &nbsp;

&nbsp;

Then, go to Tools \> Reverse-Engineer \> XSD Schema and choose the file exported.

&nbsp;

![Tools - Reverse-Engineer - XSD Schema](<lib/Tools%20-%20Reverse-Engineer%20-%20XSD%20Schema.png>)

&nbsp;

The structure of an XSD can be imported either as an entity in the Entity Relationship Diagram, or alternatively as a model definition so it could be re-used in the model:

&nbsp;

![XSD reverse-engineering dialog](<lib/XSD%20RE%20dialog.png>)

If you wish to force the destination of the reverse-engineering operation, you may specify the container in which the entities should be inserted.

&nbsp;

Your next steps might be to start denormalizing and embedding, using this Hackolade [function](<SuggestdenormalizationofaSQLsche.md>). &nbsp;

&nbsp;

For specific instructions on configuration to export XSD, please refer to the respective pages:

\- [erwin](<Fromerwin.md>)

\- [ER/Studio](<FromERStudio.md>)

&nbsp;

XSDs can be imported in Hackolade:

\- as entities in the ER diagram (not available for Swagger or OpenAPI targets)

\- as model definitions to be reused anywhere in the model

&nbsp;

## XML Schema Definition conversion in Hackolade

&nbsp;

An XSD defines the structure of an XML document. It specifies the elements and attributes that can appear in an XML document and the type of data these elements and attributes can contain.

### XSD Elements

Element structures can be of *simpleType* or *complexType*, depending on whether the element is a leaf element or a parent element.

&nbsp;

XSD elements can be of type *simpleType*, *complexType*, or *anyType:*

* an element of type *simpleType* contains only text. It cannot have attributes and elements.&nbsp;
* an element of type *complexType* can contain text, elements, and attributes. An element of type complexType is parent to all the elements and attributes contained within it.&nbsp;
* an *any* element in an XSD specifies that any well-formed XML is allowed in its place in XML instance.

&nbsp;

XSD attributes are always of type *simpleType*.

&nbsp;

Elements can be *local* or *global*. An element declared as the direct child of an XML schema is called a *global* element and can be used throughout the schema. Elements declared within a *complexType* definition are *local* elements. So, you cannot use these elements anywhere else in the schema.&nbsp;

&nbsp;

### XSD Attributes

XSD attributes are always of type *simpleType*.

&nbsp;

Attributes are stored as member of the object created for the parent element.&nbsp; An attribute group defines an association between a name and a set of attribute declarations. You can reuse the attribute groups in complexType definitions.

&nbsp;

An attribute group defines an association between a name and a set of attribute declarations. Attribute groups can be reused in complexType definitions.

&nbsp;

&nbsp;

### XSD Type Definitions

XSD Type definitions are used to create new *simpleType* data type or *complexType* data type. A type definition that is used as a base for creating new definitions is known as the base type definition. A *simpleType* or *complexType* type can be either named or anonymous. A named simpleType or complexType is always defined globally. You can define a named simpleType or complexType and refer it in schema document as type of an element. An anonymous simpleType or complexType type does not have a name. So, an anonymous simpleType or complexType type cannot be referenced.

&nbsp;

A *simpleType* type is derived from an XML schema built-in data type.&nbsp; A *complexType* type definition contains a set of element declarations, element references, and attribute declarations.A *complexType* type is first defined in the schema, and then the elements and attributes of this *complexType* type.

&nbsp;

Below is the data type conversion from XSD to JSON Schema.&nbsp; Some additional granularity is possible with some targets.

&nbsp;

| **XML Schema Type** | **JSON Schema Representation** |
| --- | --- |
| anySimpleType | string, number, integer, boolean, null |
| anyType | string, number, integer, boolean, null, object, array |
| string | string |
| normalizedString | string |
| token | string |
| language | string |
| Name | string |
| NCName | string |
| ID | string |
| IDREF | string |
| IDREFS | array of strings |
| ENTITY | string |
| ENTITIES | array of strings |
| NMTOKEN | string |
| NMTOKENS | array of strings |
| boolean | boolean |
| base64Binary | binary \| string |
| hexBinary | string |
| float | number |
| double | number |
| decimal | number |
| integer | integer |
| nonPositiveInteger | integer |
| negativeInteger | integer |
| long | integer |
| int | integer |
| short | integer |
| byte | integer |
| nonNegativeInteger | integer |
| unsignedLong | integer |
| unsignedInt | integer |
| unsignedShort | integer |
| unsignedByte | integer |
| positiveInteger | integer |
| anyURI | string with "format":"uri" |
| QName | object with "namespaceURI", "localPart", "prefix" |
| duration | string with ‘format: “duration” |
| dateTime | string with "format":"date-time" |
| date | string with "format":"date" |
| time | string with "format":"time" |


&nbsp;

