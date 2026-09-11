# Inheritance in Polyglot models

Polyglot models support inheritance through supertypes and subtypes, allowing you to describe hierarchical structures at the conceptual or logical level. This mechanism lets you define common attributes once in a supertype, and specialize them in subtypes.

&nbsp;

Inheritance defined in a Polyglot model does not directly define how data will be stored in the target database. The physical implementation depends on the inheritance strategy used when deriving from the Polyglot model into a physical model.

&nbsp;

This page is an overview. The [Supertype groups series](<Inheritancestrategies.md>) covers each topic in detail, with a complete example.

&nbsp;

## Supertypes and subtypes

Inheritance through supertypes and subtypes is a way of structuring a data model so that shared characteristics are defined once at a higher level, while specialized characteristics are defined in more specific entities.

&nbsp;

A **supertype** represents a general concept in the domain.&nbsp; It contains the attributes and relationships that are common across multiple variations of that concept. &nbsp; A **subtype** represents a more specific form of the supertype. Each subtype may automatically inherit attributes, identifiers, and relationships from the supertype, and can also define additional attributes that are unique to that specialization.

&nbsp;

For example, if you model a general concept such as “Vehicle,” you would place attributes like identifier, brand, and model in the supertype. More specific entities such as “Car”, “Train”, or "Bicycle" would be defined as subtypes. &nbsp; These subtypes inherit all common vehicle attributes but add their own specific properties, such as number of doors for cars or payload capacity for trucks.

&nbsp;

Take a general concept such as Vehicle.&nbsp; The attributes shared by every vehicle belong to the supertype:

* Vehicle identifier
* Registration number
* Brand
* Model
* Purchase date

&nbsp;

More specific entities such as Truck, Car, and Motorcycle are defined as subtypes.&nbsp; Each of them inherits all common vehicle attributes, and adds its own:

* Truck adds an axles number, a capacity and the identifier of the organization that owns it
* Car adds a doors number and a capacity
* Motorcycle adds an engine displacement

&nbsp;

A key aspect of this structure is how instances are assigned to subtypes.&nbsp; This is often controlled by a **discriminator**, an attribute in the supertype that indicates which subtype an instance belongs to.&nbsp; Depending on the business rules, the **exclusivity** of the specialization can be **disjoint**, where an instance can belong to only one subtype, or **overlapping**, where it can belong to multiple subtypes.&nbsp; Similarly, the **completeness** of the specialization can be **total** (or complete), meaning that every instance of the supertype must belong to a subtype, or **partial**, meaning that some instances may remain only at the supertype level.

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
* Truck, Car, Motorcycle (subtypes)

&nbsp;

Each subtype automatically inherits the attributes defined in the supertype.

&nbsp;

![Inheritance supertype subtype](<lib/Inheritance supertype subtype.png>)

&nbsp;

&nbsp;

Inheritance can span multiple levels. A subtype may itself become a supertype for other subtypes.

&nbsp;

In our example, a Car is either an Electric Car or a Combustion Car:

* Electric Car adds a battery capacity and a range
* Combustion Car adds a fuel type and a tank capacity

&nbsp;

&nbsp;

![Image](<lib/Inheritance supertype subtype multi level.png>)

&nbsp;

&nbsp;

## Supertype groups

In Hackolade Studio, a supertype and its immediate subtypes form a supertype group.&nbsp; The group is a hierarchical object with characteristics: Completeness (total or partial) and Exclusivity (disjoint or overlapping).&nbsp; Both characteristics are optional, but have a direct effect on the shape of the derived mode.&nbsp; So it is worth declaring them....

&nbsp;

In our example there are two groups:

* Vehicle type, with Vehicle as its supertype, and Truck, Car and Motorcycle as its subtypes
* Propulsion, with Car as its supertype, and Electric Car and Combustion Car as its subtypes

&nbsp;

![Image](<lib/NewItem 110.png>)

&nbsp;

Car is a subtype in the first group, and the supertype of the second group.&nbsp; Each group has its own characteristics and its own strategy. &nbsp;

&nbsp;

The same entity can also be the supertype of several groups at the same time, one per axis of specialization.&nbsp; See more details in the article [One supertype with multiple groups](<Onesupertypewithmultiplegroups.md>).

&nbsp;

On the ERD, a group is drawn as a half-circle between the supertype and its subtypes, and you may toggle the display of the group name above it:

* a cross inside the half-circle means that the group has a disjoint exclusivity, whereas no cross means an overlapping exclusivity
* a bar under the half-circle means that the group has a total completeness, whereas no bar means a partial completeness
* a dashed cross or a dashed bar means the corresponding property is still empty (and should be chosen...)

&nbsp;

## Create supertypes and subtypes in Hackolade Studio

To create a subtype under an existing entity (which will act as the supertype), use the action **Add subtype** which is available in the Action menu, in the contextual menu of the entity, and in the Toolbar or the keyboard shortcut Ctrl/Cmd+).&nbsp; This operation creates a new entity already linked as a subtype of the selected supertype.&nbsp; If the entity is not a supertype yet, the supertype group gets created.&nbsp; You can complete it with its name, its completeness, its exclusivity, and its materialization strategy.&nbsp; If the entity is already a supertype, a subtype is added to the existing supertype group.

&nbsp;

You can also work from the Properties Pane:

* on an entity, use the Supertype groups icon to add a subtype below it, or to create a supertype above it
* at the model level, use the Supertype groups tab, which lists every group and lets you create one from scratch: its name, its description, its completeness, its exclusivity, its materialization strategy, its supertype entity and its subtype entities.

&nbsp;

See more details in the article [Model a supertype group in Polyglot](<ModelasupertypegroupinPolyglot.md>).

&nbsp;

![Image](<lib/NewItem 111.png>)

&nbsp;

These actions define the inheritance structure in the Polyglot model.&nbsp; The physical implementation is determined later during derivation.

&nbsp;

## From inheritance to physical models

Defining inheritance in a Polyglot model describes the structure of your data, not how it is physically stored.

&nbsp;

When deriving from a Polyglot model in to your physical model, this inheritance must be translated into concrete structures such as tables or documents.&nbsp; There is no single standard way to do this.&nbsp; In data modeling, several well-established strategies exist, each with different trade-offs.

&nbsp;

The strategy is set on the supertype group itself, in the Materialization section of its Properties Pane, with the Strategy property.&nbsp; It applies to every derivation of that Polyglot model, whatever the target.&nbsp; Currently this strategy cannot be overwritten at derivation time.

&nbsp;

![Image](<lib/NewItem 112.png>)

&nbsp;

The property may remain empty, which is not a strategy.&nbsp; But in the absence of a choice, each target then applies the default of its own family, as described below.

&nbsp;

Each group is derived with its own strategy, level by level.&nbsp; In our example, the Vehicle type and Propulsion are set independently.&nbsp; See more details in the article [Hierarchy of multiple levels](<Hierarchyofmultiplelevels.md>).

&nbsp;

The strategy set for a supertype group is applied to all of its subtypes, but each subtype can also have its own Strategy property.&nbsp; It is set by default to Inherited from group strategy.&nbsp; If you change it, then that subtype alone stops following the group. &nbsp; This subtlety can be useful when one subtype is treated differently from the others: Truck, for instance, may have to be self-contained because it is maintained in a different system.&nbsp; The derive operation applies the strategy of each supertype-subtype pair independently.&nbsp; See more details in the article [Mixed strategies inside supertype group](<Mixedstrategiesinsidesupertypegr.md>).

&nbsp;

![Image](<lib/NewItem 113.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## Materialization strategies

### Preserved hierarchy (default for relational databases)

After the derive operation from a Polyglot model, each entity in the hierarchy becomes a separate table:

* the supertype becomes a table
* each subtype becomes its own table
* subtype tables reference the supertype using a foreign key relationship

&nbsp;

This is the default strategy for relational targets.&nbsp; It preserves normalization and keeps inheritance explicit in the physical model.&nbsp; In our example, a car occupies two rows: one row in the Vehicle table for the common part, and one row in the Car table for the specific part.

&nbsp;

![Image](<lib/NewItem 114.png>)

&nbsp;

What the subtype does with the supertype identifier depends on what you designed:

* a subtype with no primary key of its own receives the Vehicle identifier as its primary key
* a subtype that already has a primary key keeps it, and receives the Vehicle identifier as a unique key

&nbsp;

See more info in the article [Derive with Preserved hierarchy](<DerivewithPreservedhierarchy.md>).

&nbsp;

### Roll-up, flat with a discriminator

&nbsp;

&nbsp;

### Roll-up, nested (default for NoSQL document databases)

&nbsp;

&nbsp;

### Roll-down

&nbsp;

&nbsp;

## Exclude part of a hierarchy during derive operation

&nbsp;

&nbsp;

## Models created before version v8.13.0

## 