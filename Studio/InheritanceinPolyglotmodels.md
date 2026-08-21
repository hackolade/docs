# Inheritance in Polyglot models

Polyglot models support inheritance through supertypes and subtypes, allowing you to describe hierarchical structures at the conceptual or logical level. This mechanism lets you define common attributes once in a supertype, and specialize them in subtypes.

&nbsp;

Inheritance defined in a Polyglot model does not directly define how data will be stored in the target database. The physical implementation depends on the inheritance strategy used when deriving from the Polyglot model into a physical model.

&nbsp;

## Supertypes and subtypes

Inheritance through supertypes and subtypes is a way of structuring a data model so that shared characteristics are defined once at a higher level, while specialized characteristics are defined in more specific entities.

&nbsp;

A **supertype** represents a general concept in the domain.&nbsp; It contains the attributes and relationships that are common across multiple variations of that concept. &nbsp; A **subtype** represents a more specific form of the supertype. Each subtype may automatically inherit attributes, identifiers, and relationships from the supertype, and can also define additional attributes that are unique to that specialization.

&nbsp;

For example, if you model a general concept such as “Vehicle,” you would place attributes like identifier, brand, and model in the supertype. More specific entities such as “Car”, “Train”, or "Bicycle" would be defined as subtypes. &nbsp; These subtypes inherit all common vehicle attributes but add their own specific properties, such as number of doors for cars or payload capacity for trucks.

&nbsp;

A key aspect of this structure is how instances are assigned to subtypes.&nbsp; This is often controlled by a **discriminator**, an attribute in the supertype that indicates which subtype an instance belongs to.&nbsp; Depending on the business rules, the relationship between subtypes can be **disjoint**, where an instance can belong to only one subtype, or **exclusive** (or overlapping°, where it can belong to multiple subtypes.&nbsp; Similarly, **specialization** can be **complete** (or total), meaning that every instance of the supertype must belong to a subtype, or **partial**, meaning that some instances may remain only at the supertype level.

&nbsp;

This approach improves clarity and consistency in a data model. It avoids duplication by centralizing shared attributes, while still allowing precise representation of differences.&nbsp; It also makes the model more expressive of business semantics, which is particularly valuable in domain-driven modeling and in contexts where metadata is used to drive downstream artifacts such as schemas, APIs, or semantic layers.

&nbsp;

When implemented in physical databases, this logical structure can be mapped in different ways, such as storing everything in a single table, splitting into multiple related tables, or creating separate tables per subtype, depending on performance, normalization, and system constraints.

&nbsp;

Different data modeling tools and disciplines use a variety of terms to describe what is fundamentally the same concept as supertype/subtype inheritance.&nbsp; In traditional ER modeling, the terms “supertype” and “subtype” are common, while object-oriented and UML contexts more often use “superclass” and “subclass,” or “base class” and “derived class.”&nbsp; More informal language such as “parent” and “child” is also widely used. In semantic and ontology-based modeling, the same idea appears as “class” and “subclass,” typically expressed through relationships like subClassOf, enabling not just structural reuse but logical inference.&nbsp; Some tools and methodologies instead emphasize the relationship itself, referring to “generalization” and “specialization” or simply an “IS-A hierarchy.”&nbsp; Despite these variations in terminology, they all describe the same underlying principle: defining shared characteristics at a higher level and inheriting them into more specialized entities, allowing models to remain both concise and semantically expressive.

&nbsp;

A supertype represents a generalized entity that contains attributes shared by several specialized entities.&nbsp; A subtype is a specialized entity that inherits attributes from its supertype and may define additional attributes.

&nbsp;

Example:

* Vehicle (supertype)
* Car, Train, Bicycle (subtypes)

&nbsp;

Each subtype automatically inherits the attributes defined in the supertype.

&nbsp;

![Inheritance supertype subtype](<lib/Inheritance supertype subtype.png>)

&nbsp;

&nbsp;

Inheritance can span multiple levels. A subtype may itself become a supertype for other subtypes.

&nbsp;

![Inheritance supertype subtype multi level](<lib/Inheritance supertype subtype multi level.png>)

&nbsp;

&nbsp;

## Creating supertypes and subtypes in Hackolade Studio

To create a subtype under an existing entity (which will act as the supertype), use the action **Add subtype** which is available in the Action menu, in the contextual menu of the entity and in the Toolbar.&nbsp; This operation creates a new entity already linked as a subtype of the selected supertype.

&nbsp;

You can also define the relationship from the Properties Pane

* use **Child entity** to add a subtype to the current entity
* use **Parent entity** to link the current entity to an existing entity that will become its supertype

&nbsp;

![Inheritance supertype subtype properties pane](<lib/Inheritance supertype subtype properties pane.png>)

&nbsp;

These actions define the inheritance structure in the Polyglot model. The physical implementation is determined later during derivation.

&nbsp;

## From inheritance to physical models

Defining inheritance in a Polyglot model describes the structure of your data, not how it is physically stored.

&nbsp;

When deriving from a Polyglot model in to your physical model, this inheritance must be translated into concrete structures such as tables or documents.&nbsp; There is no single standard way to do this.&nbsp; In data modeling, several well-established strategies exist, each with different trade-offs.

&nbsp;

Hackolade Studio currently supports some of these strategies.&nbsp; Additional options are planned and will be introduced progressively.

&nbsp;

## Currently supported strategies

### Separate entities for supertype and subtypes (default for relational databases)

Each entity in the hierarchy becomes a separate table:

* the supertype becomes a table
* each subtype becomes its own table
* subtype tables reference the supertype using a foreign key

&nbsp;

This is the default strategy for relational targets. It preserves normalization and keeps inheritance explicit in the physical model.

&nbsp;

![Inheritance supertype subtype separate tables](<lib/Inheritance supertype subtype separate tables.png>)

&nbsp;

&nbsp;

If you do not want this behavior, you can disable it by unchecking **Normalize Complex Data Type in Separate Entities** in the Polyglot entity selection dialog during derivation.

&nbsp;

![Inheritance supertype subtype normalize](<lib/Inheritance supertype subtype normalize.png>)

&nbsp;

&nbsp;

### Nested objects in supertype (non-relational databases)

Subtypes are embedded within the supertype entity as nested structures.

&nbsp;

The supertype is stored as a single entity, and subtype-specific attributes are represented using a \*\*oneOf\*\* structure that captures the different subtype variations.

&nbsp;

![Image](<lib/Inheritance supertype subtype nested.png>)

&nbsp;

This is the strategy applied for all the non-relational targets.

&nbsp;

## Upcoming enhancements

Additional inheritance capabilities are planned to give you more control over how supertypes and subtypes are defined and derived.

&nbsp;

At the modeling level, Polyglot will be extended with:

* **Completeness** (total vs partial)
* **Exclusivity** (disjoint vs overlapping)

&nbsp;

### Multiple subtype groups

It will also be possible for a single entity to act as the supertype of multiple independent groups.

&nbsp;

For example, a "Vehicle" entity may define:

* one group with subtypes such as Car, Train, Bicycle (based on usage or structure)
* another group with subtypes such as Electric Vehicle, Hybrid Vehicle, Combustion Vehicle (based on energy type)

&nbsp;

These groups represent different specialization axes applied to the same concept.&nbsp; These characteristics allow more precise control over how inheritance is translated during derivation.

&nbsp;

At the derivation level, additional strategies are introduced.&nbsp; It is possible to apply different derivation strategies per supertype-subtype pair, allowing finer control within the same group.&nbsp; These enhancements provide more flexibility in how inheritance is materialized.

&nbsp;

### Push supertype into subtypes (roll-down)

Each subtype becomes a standalone entity containing:

* its own attributes
* inherited attributes from the supertype

&nbsp;

![Inheritance supertype roll-down](<lib/Inheritance supertype roll-down.png>)

&nbsp;

The supertype may be:

* removed from the physical model
* or kept as a separate entity

&nbsp;

### Merge subtypes into supertype (roll-up)

All subtypes are merged into the supertype.

&nbsp;

A nested variant is already supported for document models, where subtype structures are embedded using **oneOf**.

&nbsp;

An additional variant for relational targets, allows for all attributes to be flattened into a single table, using a discriminator column to identify the subtype.&nbsp; This approach reduces joins but may introduce sparse or nullable attributes.

&nbsp;

![Inheritance supertype roll-up](<lib/Inheritance supertype roll-up.png>)

&nbsp;

### Ignore supertype or subtypes

Some derivation scenarios may exclude parts of the hierarchy:

* ignore the supertype and keep subtypes
* ignore some subtypes

&nbsp;

Only selected elements would be derived in the target model.

&nbsp;

These strategies correspond to common modeling patterns in Hackolade Studio.

&nbsp;

