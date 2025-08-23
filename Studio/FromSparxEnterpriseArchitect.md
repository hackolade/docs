# From Sparx Enterprise Architect

If you have data models in Sparx Enterprise Architect and want to leverage them in Hackolade Studio, you need to fist export them to XSD, following the instructions below.&nbsp; You should first consult [this page](<XSDXMLSchemaDefinition.md>) for an overview of the import functionality in Hackolade Studio.

&nbsp;

By default Enterprise Architect does not export primary key and foreign key constraints.&nbsp; If the XSD does not contain this information, this reverse-engineering process cannot import them, but it is still possible to use the functionality to [Infer PKs \& FKs](<InferPrimaryKeysandForeignKeyRel.md>).

&nbsp;

The XSD generation is a package-level operation in EA. &nbsp;

&nbsp;

***Getting Started***\
To use the schema generation facility you will require the following:

* EA Professional or Corporate edition
* [XSDDataTypes](<https://sparxsystems.com/downloads/profiles/XSDDataTypes.xml>) Package: This package contains classes representing XSD primitive data types. This package is available as an XMI file. To import the file as a UML Package, use EA's XMI import facility which is available from the menu item: Project \| Import/Export \| Import Package from XMI.
* [UML Profile for XML](<https://sparxsystems.com/downloads/profiles/XSDProfile.xml>): This resource file contains the stereotyped classes which allow the schema generation to be customized. The UML Profile for XML can be imported into a model using the Resource View (see [Importing Profiles](<https://sparxsystems.com/resources/developers/uml\_profiles.html>) for details on importing UML profiles into EA).

## Steps to Generate XSD

1. Select the package to be converted to XSD by right-clicking on the package in the Project Browser.
1. Select Project \| Generate XML Schema from the main menu.
1. Set the desired output file using the Filename field.
1. Set the desired xml encoding using the Encoding field.
1. Click on the Generate button to generate the schema.
1. The progress of the schema generator will be shown in the Progress edit box.

&nbsp;

More information can be found [here](<https://sparxsystems.com/resources/xml\_schema\_generation.html> "target=\"\_blank\"").

&nbsp;

After the successful export of your model to XSD, use the instructions in [this page](<XSDXMLSchemaDefinition.md>) to import the XSD into a Hackolade Studio model for the target of your choice.

&nbsp;

&nbsp;

## JSON Schema representation of UML models

UML (Unified Modeling Language) and JSON Schema target slightly different domains: UML is a general-purpose modeling language (often used for object-oriented system design), while JSON Schema is a formal vocabulary for describing JSON data structures.

However, JSON Schema *can* be used to achieve many of the **same modeling objectives** as UML class diagrams, particularly if your system’s "classes" correspond to structured JSON objects.

### High-level parallels

| **UML Concept** | **JSON Schema Equivalent** |
| --- | --- |
| Class | Schema definition for an object type (type: "object", properties) |
| Attributes | Properties in properties with types, constraints |
| Associations | Properties whose values are other object schemas ($ref) |
| Inheritance (specialization/generalization) | Use of allOf or oneOf to combine a base schema with extensions |
| Multiplicity | Arrays with minItems / maxItems |
| Composition / Aggregation | Object properties with embedded schemas (composition: required; aggregation: optional) |
| Constraints (like invariants) | pattern, minimum, maximum, enum, custom keywords |


&nbsp;

### Achieving UML Objectives with JSON Schema

UML Class Diagrams aim to:

1. **Define structure** → JSON Schema defines object structure (properties, type, constraints).
1. **Specify constraints** → JSON Schema constraints (enum, pattern, numeric limits).
1. **Model relationships** → JSON Schema uses $ref, anyOf, oneOf, arrays, and required to express associations, inheritance, and ownership.
1. **Support validation** → JSON Schema is directly machine-validated against JSON instances, so it adds *runtime enforceability* that UML lacks without code generation.

&nbsp;

### Relationship types in JSON Schema

For each UML relationship type, we describe below how to represent them using JSON Schema:

#### a) Composition

**UML Meaning**: "Has-a" relationship where the contained object is strongly owned by the container.&nbsp; If the container is destroyed, so is the part.

**JSON Schema Representation**: model the part **as a required property** with an embedded or referenced schema.&nbsp; Note that cardinality can be specified with the object type representing a 1-to-1 relationship, whereas an array type represents a \&-to-many relationship.

> {\
&nbsp; "$schema": "https://json-schema.org/draft/2019-09/schema",\
&nbsp; "type": "object",\
&nbsp; "properties": {\
&nbsp; &nbsp; "engine": { "$ref": "#/$defs/Engine" }\
&nbsp; },\
&nbsp; "required": \["engine"\],\
&nbsp; "$defs": {\
&nbsp; &nbsp; "Engine": {\
&nbsp; &nbsp; &nbsp; "type": "object",\
&nbsp; &nbsp; &nbsp; "properties": {\
&nbsp; &nbsp; &nbsp; &nbsp; "horsepower": { "type": "number" }\
&nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; "required": \["horsepower"\]\
&nbsp; &nbsp; }\
&nbsp; }\
}

Here, the engine is **required**, meaning the composition is mandatory.

&nbsp;

#### b) Aggregation

**UML Meaning**: "Has-a" relationship but with weaker ownership: the part can exist independently of the whole.

**JSON Schema Representation**: the part is **optional**, but still linked via schema reference.&nbsp; Note that cardinality can be specified with the object type representing a 1-to-1 relationship, whereas an array type represents a \&-to-many relationship.

> {\
&nbsp; "$schema": "https://json-schema.org/draft/2019-09/schema",\
&nbsp; "type": "object",\
&nbsp; "properties": {\
&nbsp; &nbsp; "gpsModule": { "$ref": "#/$defs/GpsModule" }\
&nbsp; },\
&nbsp; "$defs": {\
&nbsp; &nbsp; "GpsModule": {\
&nbsp; &nbsp; &nbsp; "type": "object",\
&nbsp; &nbsp; &nbsp; "properties": {\
&nbsp; &nbsp; &nbsp; &nbsp; "coordinates": { "type": "string" }\
&nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; "required": \["coordinates"\]\
&nbsp; &nbsp; }\
&nbsp; }\
}

Here, gpsModule is **not required**, showing that the relationship is looser.

&nbsp;

#### c) Specialization (inheritance)

A **specialization relationship** *is* essentially the same thing as **inheritance**, just described from a different perspective. &nbsp;

&nbsp;

**Specialization** is the *conceptual* view: you take a general concept (the "superclass") and create a more specific concept (the "subclass") by adding extra properties or constraints.&nbsp; Example: *Vehicle* → specialized into *Car* and *Truck*.&nbsp; This focuses on *meaning*: "Car is a kind of Vehicle."

&nbsp;

**Inheritance** is the *technical / implementation* view: in programming or schema design, the subclass **inherits** the attributes and behavior of its parent, and may add more.&nbsp; In JSON Schema, this is modeled with allOf combining the base schema and the subclass’s additions.

&nbsp;

In relational data modeling, the logical representation is with the supertype/subtypes construct whereby the **supertype** (or superclass in UML) holds attributes common to all members of the family, and each **subtype** (or subclass in UML) inherits those common attributes and can define its own specific ones.

&nbsp;

**UML meaning**: one class extends another, inheriting attributes and possibly adding new ones.

**JSON Schema Representation**: use anyOf or oneOf to combine a base type with additional constraints/properties. &nbsp; In this example, Car **inherits** make and model from Vehicle and adds doors.

> {\
    "$schema": "https://json-schema.org/draft/2019-09/schema",\
    "type": "object",\
    "properties": {\
        "Vehicle": {\
            "type": "object",\
            "properties": {\
                "make": { "type": "string" },\
                "model": { "type": "string" }\
            },\
            "anyOf": \[\
                {\
                    "type": "object",\
                    "properties": {\
                &nbsp; &nbsp; &nbsp; &nbsp; "Car": {\
                    &nbsp; &nbsp; &nbsp; &nbsp; "type": "object",\
                    &nbsp; &nbsp; &nbsp; &nbsp; "properties": {\
                        &nbsp; &nbsp; &nbsp; &nbsp; "doors": { "type": "integer", "minimum": 2 }\
                    &nbsp; &nbsp; &nbsp; &nbsp; }\
                        }\
                    }\
                },\
                {\
                    "type": "object",\
                    "properties": {\
&nbsp; &nbsp;               &nbsp; &nbsp; "Truck": { "type": "object" }\
                    }\
                }\
            \],\
            "required": \[ "make", "model" \]\
        }\
    }\
}

&nbsp;

#### d) Association

**UML meaning**: a structural relationship between classes without strong ownership.

**JSON Schema representation**: simply refer to other object schemas without implying containment.

> {\
&nbsp; "$schema": "https://json-schema.org/draft/2019-09/schema",\
&nbsp; "type": "object",\
&nbsp; "properties": {\
&nbsp; &nbsp; "driver": { "$ref": "#/$defs/Person" }\
&nbsp; },\
&nbsp; "$defs": {\
&nbsp; &nbsp; "Person": {\
&nbsp; &nbsp; &nbsp; "type": "object",\
&nbsp; &nbsp; &nbsp; "properties": {\
&nbsp; &nbsp; &nbsp; &nbsp; "name": { "type": "string" }\
&nbsp; &nbsp; &nbsp; },\
&nbsp; &nbsp; &nbsp; "required": \["name"\]\
&nbsp; &nbsp; }\
&nbsp; }\
}

&nbsp;

You could further indicate multiplicity by making it an array of $refs.

&nbsp;

&nbsp;

### Full example

If we put all these examples together, we get the diagram below and [Mermaid code](<https://www.mermaidchart.com/play#pako:eNp1kcFOwzAQRH\_FyhGUH4gQBwrihMSh4pTLYq\_cVeNda-0IVaX\_jtNQJbTGx\_Gb9ez42Fhx2HSNHSClZwKvEHp2pGgzCZvtU8-mnPO9-cAd2QHNsec-T\_J9ykrsTYA93mhl8jC7T-shG9DVAOJsnIimCrnV0e5XLI\_hE9VEOAwCbgMRLOVDxfjCnhivXtmVRzDKF2rF8RrTm7ixtpst6RwxZKxlfEdNpacbF0PAP\_ilu4fvtp06qKjnfWd9KkmKtOTqDHiv6GH6lwVq28dLhkKkJJauiLsy5reQriwToiRaiLnj\_5jm9AM5oLB7> "target=\"\_blank\""), the JSON Schema equivalent, and the representation in Hackolade Studio.

&nbsp;

**Vehicle** acts as the **generalized superclass** for all vehicle types in the diagram. It defines attributes that are *common to all vehicles*.  **Car** is a specialized form of **Vehicle**.  It inherits all properties of **Vehicle** (make, model) and adds car-specific features.  A car must have has a minimum of 2 **doors**.  A Car **must have exactly one Engine**.  A Car **may have a GPS module**, but it’s optional.  A Car is **associated** with a Person who drives it.

&nbsp;

**Truck** is another specialized form of **Vehicle**. It also inherits make and model from **Vehicle**.&nbsp; The maximum load the truck can carry is indicated with the **payloadCapacity** attribute. A **Truck**, like a **Car**, has an **Engine** that is part of it and does not exist independently of it.

&nbsp;

**Engine** exists only as a **part** of either a **Car** or a **Truck** (composition).&nbsp; It indicates an engine power rating with the **horsepower** attribute.&nbsp; **GpsModule** exists independently, used in **aggregation** with **Car**.&nbsp; **Person** is linked to Car through an **association** using the driver’s **name** attribute.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

![UML diagram with different relationships](<lib/UML diagram with different relationships.png>)

&nbsp;

&nbsp;

The above diagram is drawn from the Mermaid code:

> **classDiagram**\
direction TB\
    **class** Vehicle **{**\
        **+**&#8202;string make\
        **+**&#8202;string model\
    **}**\
    **class** Car **{**\
        **+**&#8202;int doors\
    **}**\
    **class** Truck **{**\
        **+**&#8202;number payloadCapacity\
    **}**\
    **class** Engine **{**\
        **+**&#8202;int horsepower\
    **}**\
    **class** GpsModule **{**\
        **+**&#8202;string coordinates\
    **}**\
    **class** Person **{**\
        **+**&#8202;string name\
    **}**\
    Vehicle **\<\|--** Car\
    Vehicle **\<\|--** Truck\
    Car o#8202;**--** GpsModule **:** aggregation\
    Car **--\>** Person **:** association\
    Car **\*--** Engine **:** composition\
    Truck **\*--** Engine **:** composition

&nbsp;

&nbsp;

It can all be represented in this JSON Schema:

> {\
    "$schema": "https://json-schema.org/draft/2019-09/schema",\
    "type": "object",\
    "title": "Vehicle",\
    "properties": {\
        "Vehicle": {\
            "type": "object",\
            "properties": {\
                "make": { "type": "string" },\
                "model": { "type": "string" }\
            },\
            "anyOf": \[\
                { "$ref": "#/$defs/Car" },\
                { "$ref": "#/$defs/Truck" }\
            \],\
            "required": \[ "make", "model" \]\
        }\
    },\
    "$defs": {\
        "Car": {\
            "type": "object",\
            "properties": {\
                "doors": { "type": "integer", "minimum": 2 },\
                "engine": { "$ref": "#/$defs/Engine" },\
                "gpsModule": { "$ref": "#/$defs/GpsModule" },\
                "driver": { "$ref": "#/$defs/Person" }\
            },\
            "required": \[ "doors", "engine" \]\
        },\
        "Engine": {\
            "type": "object",\
            "properties": {\
                "horsepower": { "type": "integer" }\
            },\
            "required": \[ "horsepower" \]\
        },\
        "GpsModule": {\
            "type": "object",\
            "properties": {\
                "coordinates": { "type": "string" }\
            },\
            "required": \[ "coordinates" \]\
        },\
        "Person": {\
            "type": "object",\
            "properties": {\
                "name": { "type": "string" }\
            },\
            "required": \[ "name" \]\
        },\
        "Truck": {\
            "type": "object",\
            "properties": {\
                "payloadCapacity": { "type": "number" },\
                "engine": { "$ref": "#/$defs/Engine" }\
            },\
            "required": \[ "payloadCapacity", "engine" \]\
        }\
    }\
}

&nbsp;

In Hackolade Studio, this would be modeled (possibly via reverse-engineering of the above JSON Schema):

![Image](<lib/UML to JSON Schema.png>)

