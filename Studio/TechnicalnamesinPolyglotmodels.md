# Technical names in Polyglot models

For physical data models it has been possible, for a long time with Hackolade Studio, to maintain both business and technical names for each object: schemas, tables, columns.&nbsp; A technical name is not mandatory, but it can be useful if you want to distinguish between a business-friendly label and the actual identifier used in scripts or schema generation.&nbsp; If you choose not to define a technical name, Hackolade Studio uses the same name property for both visual representation and script generation.&nbsp; In that case, the name is considered to serve both purposes -- business and technical.

&nbsp;

[Naming Conventions](<Namingconventions.md>) are useful if you choose to automate and standardize the conversion of business names to technical names, optionally using an abbreviations file.

&nbsp;

## Polyglot models can be used for different purposes

Hackolade Studio's Polyglot data models are not limited to conceptual or logical modeling.&nbsp; They can be used at different levels of abstraction depending on your needs:

* as a **conceptual model** to structure business terminology, clarify key entities, and align stakeholders using a shared vocabulary
* as a **logical model** to explore relationships and constraints between data elements, independent of technical implementation
* as a technology-agnostic **common physical model**, capturing a common structure shared across different target technologies (e.g. SQL, Avro, OpenAPI, etc.)

&nbsp;

Because of this flexibility, it is valid - and sometimes useful - for Polyglot modeling objects to include both a business name and a technical name.

&nbsp;

### Why use technical names in a Polyglot model?

We originally did not enable technical names in Polyglot models, based on the strict theory that logical models should be technology-independent, and that users might want different case conversions when deriving Polyglot models in models of different targets, e.g.: snake\_case in RDBMS, camelCase in MongoDB, PascalCase in Avro, etc.

&nbsp;

But given the different ways that Polyglot models are being used, it made sense to open up the option to use technical names in Polyglot models too.

&nbsp;

Including technical names in Polyglot can be useful in scenarios where:

* you want to reuse the same technical names across different target technologies
* you prefer to define names once and propagate them automatically during derive operations
* you want to manage naming conventions at the logical or cross-platform level, rather than repeating them in each physical model

&nbsp;

This can be especially relevant when the target models are expected to use consistent naming across systems, or when there are cross-technology constraints that require harmonized names.

&nbsp;

### Naming conventions in Polyglot

Just like in target models, Polyglot supports name coupling: a mechanism that allows automatic calculation of one name (e.g. technical) from the other (e.g. business) using transformation rules and abbreviation files.

&nbsp;

You may choose to activate coupling in the Polyglot model if you want to enforce a consistent naming strategy.&nbsp; Alternatively, you can leave the names independent.&nbsp; More information on this feature is available in the corresponding [documentation page](<Namingconventions.md>).

&nbsp;

If you do enable this functionality in the Polyglot target, it is important to understand its behavior...

&nbsp;

&nbsp;

## How technical names in Polyglot interact during derivation

This section explains what happens to business and technical names when deriving a model from Polyglot into a physical target, especially when naming conventions are defined in either the Polyglot model, the target model, or both.

&nbsp;

It also clarifies how Hackolade Studio handles potential overlaps or conflicts in naming logic — and what decisions are expected from the user.

&nbsp;

For additional reference, see also the [Naming Conventions documentation](<Namingconventions.md>) and the [Polyglot Data Modeling documentation](<PolyglotDataModeling.md>).

&nbsp;

### Understanding name derivation between Polyglot and Target

When deriving a target model from a Polyglot model, Hackolade Studio needs to determine how to populate the technical name field in the derived objects. This behavior depends on two key parameters:

&#49;. Are technical names defined in the **Polyglot** model?

&#50;. Are naming conventions configured and active for the **target** model?

&nbsp;

This creates four possible base scenarios for how technical names are propagated during derivation:

|  | **No naming conventions in target** | **Naming convention in target** |
| --- | --- | --- |
| **No technical names in Polyglot** | Technical names in the target are empty after derivation | Naming conventions are applied to generate the technical name in the target, based on the derived Polyglot business name |
| **Technical names in Polyglot** | Technical names in the target are derived from the technical names in Polyglot | A potential conflict exists between the technical names from Polyglot and those generated with the target naming conventions |


&nbsp;

### A note about naming convention direction

Hackolade Studio supports naming conventions in both directions:

\- from business name --\> technical name (typical in forward modeling),

\- from technical name --\> business name (useful in reverse-engineering existing databases).

&nbsp;

There is generally no good reason to use technical-to-business coupling during normal operations, except for ad-hoc manipulations.

&nbsp;

For the sake of clarity and consistency throughout this documentation, we assume the business-to-technical direction when naming conventions are applied. This is the most common approach in data modeling, where technical names are derived from business terms using naming rules.

&nbsp;

If your use case follows the opposite direction, the same logic applies — simply mentally swap the roles of “business name” and “technical name” when reading the examples and explanations.

&nbsp;

