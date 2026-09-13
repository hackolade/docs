# Derive with Roll-up nested strategy

As discussed in the previous page with Hackolade Studio when performing a derive operation with the Roll-up strategy, there are two ways to merge the subtypes into the supertype:

* the traditional way in relational databases with the option Flat with discriminator puts all the attributes at the same level, with a column telling the rows apart -- this method is reviewed in the previous page
* Nested keeps each subtype as an object inside the supertype, typically useful with NoSQL document databases.

&nbsp;

This page covers the second option.

&nbsp;

In the example, we work with the group built earlier: we keep the Legal nature group: the Party entity, with the Person and Organization entities as its subtypes. The group has total completeness and disjoint exclusivity.

&nbsp;

![Inheritance roll-up nested Party Polyglot model](<lib/Inheritance roll-up nestedParty Polyglotmodel.png>)

&nbsp;

In the Properties Pane of the supertype group of the Polyglot data model, assuming you set the Strategy property to Roll-up with the Merge option to Nested, and derive to a physical model.&nbsp; In our example, we derive into a MongoDB model.

&nbsp;

![Inheritance roll-up nested Party group props](<lib/Inheritance roll-up nested Party group props.png>)

&nbsp;

&nbsp;

## Derive operation result

In the physical data model, the derive operation results in a single collection, Party, containing the common fields and a choice between two nested objects, one per subtype:

&nbsp;

![Inheritance roll-up nested Party single table](<lib/Inheritance roll-up nested Party single table.png>)

&nbsp;

Two properties of the supertype group drive the JSON Schema choice:

* **exclusivity** determines the type of choice: a disjoint group translates to oneOf choice as exactly one subtype is possible.&nbsp; An overlapping group translates to an anyOf choice, as several subtypes may apply at once
* **completeness** determines whether it can be left empty: in a total group the subtype objects are required, in a partial group they are optional, so a document may hold only the common attributes

&nbsp;

In our example, the Legal nature group being total and disjoint, a Party document contains exactly one of the two sub-objects.

&nbsp;

### Primary and unique keys

The Party collection keeps its primary key, its unique keys, and its required attributes.

&nbsp;

The keys of the subtypes move with their attributes, inside their nested object:

* a primary key of a subtype becomes a unique key in the nested fields.&nbsp; Only one identity remains in the merged entity, the one coming from the supertype.
* a unique key of a subtype should remain a unique key in the nested fields, except that such constraint of uniqueness in objects exists in JSON Schema -- if necessary, it would have to be built in application code
* a required attribute of a subtype remains required inside its object

&nbsp;

**Note:** what a key becomes physically depends also on the target. In targets where keys are not enforced, they are not derived.\
&nbsp;

### Relationships that pointed at the subtypes

A foreign key relationship attached to the subtypes (which disappear) follows the roll-up to become foreign key relationship(s) into the supertype collection.

&nbsp;

A relationship attached to a subtype follows the roll-up into the supertype.

&nbsp;

Consider this example: an organization owns trucks.

&nbsp;

![Inheritance roll-up nested FK relationships](<lib/Inheritance roll-up nestedFK relationships.png>)

&nbsp;

In this scenario, we establish the relationship between the Organization sub-object and Truck collection by anchoring it to the nested object in the Party collection.

&nbsp;

![Inheritance roll-up nested derived relationships](<lib/Inheritance roll-upnestedderivedrelationships.png>)

&nbsp;

**Note:** Any mandatory cardinality (1 or 1..n) at the side of the "other" entity linked to the subtype is relaxed to make it optional (0..1 or 0..n). The relationship then connects to the supertype, which may represent a different subtype than the one that originally carries the relationship in the Polyglot model. If the cardinality is already optional (0..1 or 0..n), as in our example, no modification occurs.\
&nbsp;

### Nested merge option results in relational targets

The derive dialog provides the option to Normalize complex data types in separate entities, checked by default when deriving into RDBMS-like targets.&nbsp; The option applies to every complex data type of the model, and a nested subtype is one of them.

&nbsp;

![Inheritance roll-up nested derive options](<lib/Inheritance roll-up nested derive options.png>)

&nbsp;

With such a target, leaving the box checked means that the nesting you asked for gets normalized.&nbsp; You end up with one entity per subtype, which looks like what Preserved hierarchy produces. &nbsp;

&nbsp;

The result is the outcome of two steps, in this order:

* the roll-up runs first; each subtype becomes a complex property of the supertype
* the normalization runs next; each complex property is extracted into an entity of its own, linked back to the supertype

&nbsp;

The second step knows nothing about supertypes and subtypes.&nbsp; It extracts each complex object or array, and makes it its own table.&nbsp; The cardinality between the supertype and the extracted entity depends on whether the nested structure is an object or an array.

&nbsp;

![Inheritance roll-up nested derive normalized](<lib/Inheritance roll-up nested derive normalized.png>)

&nbsp;

Uncheck the option Normalize complex data types in separate entities if you want the subtypes to stay nested inside the supertype.

