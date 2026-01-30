# Union types in Avro

In Avro, [union types](<https://avro.apache.org/docs/%20%20version%20%20/specification/#unions> "target=\"\_blank\"") are used to represent alternative data types for a field.&nbsp; They play a key role in [schema evolution and compatibility](<https://docs.confluent.io/platform/current/schema-registry/fundamentals/schema-evolution.html> "target=\"\_blank\""), and in modeling logical choices such as *oneOf*.

&nbsp;

Because Avro does not support explicit notions of “required” or “optional” fields, all fields are technically required.&nbsp; Logical optionality is expressed through unions, most commonly by allowing *null* as a polymorphic data type.&nbsp; When combined with a default value, this mechanism also supports [forward- and backward-compatibility](<https://developer.confluent.io/patterns/event-stream/schema-compatibility> "target=\"\_blank\""), enabling readers to safely handle data written with older versions of a schema that did not yet include the field.

&nbsp;

## Simple (scalar) union types

When working with scalar types (such as *boolean*, *int*, *long*, *float*, *double*, *bytes*, and *string*), compatibility is achieved by creating a union that combines *null* with one or more scalar types.&nbsp; In Hackolade Studio, this is achieved by adding multiple data types to the field.&nbsp; The field remains physically present in the schema, but its value may be *null* for example.

&nbsp;

For compatibility, a default value can be defined.&nbsp; The default is used only by readers when the field is missing in data written with an older schema.&nbsp; The default value must be compatible with the first type listed in the union.&nbsp; For this reason, when *null* is intended to be the default, it must appear as the first type in the union and the default value must be set to *null*.

&nbsp;

How unions are modeled in Hackolade Studio differs depending on whether only scalar types are involved or whether complex types are present, as explained in the following sections.

&nbsp;

## Union types and oneOf in Hackolade Studio

In Hackolade Studio, the *oneOf* choice is used to model an Avro union when at least one of the possible data types is complex type (meaning a *record*, an *array*, or a *map*);

&nbsp;

A *oneOf* construct represents an exclusive choice: at runtime, the value must conform to exactly one of the defined alternatives.

&nbsp;

## Named types and naming rules

According to the [Avro specification](<https://avro.apache.org/docs/%20%20version%20%20/specification/#names> "target=\"\_blank\""), only *named types* require a name.&nbsp; Named types are the data types: *record*, *enum*, and *fixed*.&nbsp; Whenever one of these types is used, a name is mandatory, regardless of whether the type is defined at the top level, inline, or inside a union.

&nbsp;

Other types such as primitive (scalar) types (*string*, *int*, etc.), *array*, and *map* are not named types. They do not require a name, and the Avro specification does not define a *name* attribute for them.

&nbsp;

In an Avro union, each branch must resolve to a distinct type.&nbsp; For named types, this distinction is based on the **full name**, which is the combination of the type name and its namespace.&nbsp; As a consequence, a union may contain multiple records, enums, or fixed types only if each of them has a unique full name.&nbsp; Two named types with the same full name (name and namespace) are considered identical by Avro and are not allowed in the same union.&nbsp; If multiple named types inside the same *oneOf* resolve to the same full name, the resulting Avro schema is invalid.&nbsp; The data modeler must ensure that all named types are unique to avoid a validation error.

&nbsp;

## Naming the union field

When generating an Avro schema, the union itself is always represented by a named field.

&nbsp;

If the *oneOf* choice has an explicit name, that name is used as the name of the union field in the Avro schema.&nbsp; If no name is provided at the *oneOf* level, Hackolade Studio deterministically uses the name of the first subschema in the *oneOf* choice.&nbsp; For clarity and maintainability, it is strongly recommended to explicitly assign a name to the *oneOf* field.

&nbsp;

## Naming the types inside a oneOf

For each subschema in a *oneOf* choice that corresponds to a named Avro type (*record*, *enum*, or *fixed*), Hackolade Studio must generate a valid Avro type name.

&nbsp;

If the user provides a **Type name** property on the subschema, that value is used as the Avro type name. If no explicit type name is provided, the name of the subschema is used.&nbsp; When a subschema is a reference to an existing definition, the name of the referenced definition is used.

&nbsp;

All named types within the same union must have distinct full names.&nbsp; If this condition is not met, the resulting Avro schema is invalid and must be corrected by the user.

&nbsp;

## Example: oneOf choice with multiple record variants

In the following example, let's focus on the **accountDetails** field.&nbsp; This *oneOf* choice illustrates a case, similar to relational supertype-subtype inheritance, where a sub record can take several alternative shapes, each represented by a different record type.&nbsp; Because these alternatives have different structures, this is a true *alternative shape* scenario and the *oneOf* must be explicitly named.&nbsp; The name **accountDetails** is used as the union field name in the Avro schema.

&nbsp;

![Avro oneOf choice with multiple variants](<lib/Avro oneOf choice with multiple variants.png>)

&nbsp;

![Avro oneOf choice with multi variants props](<lib/Avro oneOf choice with multi variants props.png>)

&nbsp;

![Avro oneOf choice with multi variants schema](<lib/Avro oneOf choice with multi variants schema.png>)

&nbsp;

Each subschema in the *oneOf* choice is a named record. These names (**Checking**, **Savings**, **Loan**) are used as the Avro type names for the corresponding union branches.&nbsp; All named types must be unique within the union.

&nbsp;

If a different Avro type name is required, the user can explicitly specify it in the Properties Pane using the **Type name** property.&nbsp; For example, the subschemas may be named **checking**, **savings**, and **loan** in the model, while the generated Avro types are named **CheckingType**, **SavingsType**, and **LoanType**.&nbsp; This allows the name of the subschema and the name of the Avro type to be controlled independently, while still producing a valid Avro union.

&nbsp;

![Avro oneOf with multi variants type names](<lib/Avro oneOf with multi variants type names.png>)

&nbsp;

![Avro oneOf with multi variants type names schema](<lib/Avro oneOf with multi variants type names sch.png>)

&nbsp;

## Example: oneOf choice with null and a record

In the following example, let's focus now on the **accountOrigin** field.&nbsp; This *oneOf* choice illustrates a different pattern, where the same logical concept can either be absent (*null*) or present with a defined structure. This is done for purposes of compatibility during evolution.&nbsp; Unlike the previous example, this is not a case of multiple alternative shapes, but a single concept with an optional structured value.

&nbsp;

![Avro oneOf choice with null and record](<lib/Avro oneOf choice with null and record.png>)

&nbsp;

In this case, it is not strictly necessary for the user to explicitly name the *oneOf* field.&nbsp; Both subschemas intentionally share the same name (**accountOrigin**), emphasizing that this is always the same concept, whether it is null or structured.

&nbsp;

When no explicit *oneOf* name is provided, Hackolade Studio uses the name of the first subschema as the name of the generated union field.&nbsp; This results in a consistent field name across the schema while still producing a valid Avro union.

&nbsp;

![Avro oneOf choice with null and record schema](<lib/Avro oneOf choice with null and record schema.png>)

&nbsp;

If the user wants a specific Avro type name without changing the subschema name, this can be done via the **Type name** property in the Properties Pane.&nbsp; This results in a consistent field name across the schema while allowing full control over the generated named types.

&nbsp;

![Avro oneOf with null and record type name](<lib/Avro oneOf with null and record type name.png>)

&nbsp;

![Avro oneOf with null and record type name schema](<lib/Avro oneOf with null and record type name sch.png>)

&nbsp;

## Polyglot derive operation and inheritance

In a Polyglot model, inheritance is expressed through a supertype–subtype relationship.&nbsp; A supertype defines the common structure, while each subtype represents a specialized form with its own attributes.&nbsp; When such an inheritance is derived to Avro, it is mapped to a *oneOf* choice (union) of complex types, because each subtype becomes a distinct Avro record.

&nbsp;

This derivation corresponds to the same pattern as the *oneOf with multiple record variants* example shown above.&nbsp; For instance, an inheritance where **Account** is specialized into **Checking**, **Savings**, and **Loan** will result in a union of record types, typically named **accountDetails** in the Avro schema.

&nbsp;

In this scenario, it is important that the supertype–subtype relationship itself has a clear and explicit name in the Polyglot model.&nbsp; That name is used to generate the union field name in Avro.&nbsp; If the inheritance is unnamed, or ambiguously named, the generated Avro schema may be unclear or invalid, because multiple alternative shapes are involved.

&nbsp;

![Avro polyglot derive and inheritance](<lib/Avro polyglot derive and inheritance.png>)

&nbsp;

![Avro polyglot inheritance derived](<lib/Avro polyglot inheritance derived.png>)

&nbsp;

