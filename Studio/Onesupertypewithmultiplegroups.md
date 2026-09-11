# One supertype with multiple groups

The same supertype can be split along several axes of specialization at once.&nbsp; Each axis is a group of its own, with its own subtypes, its own characteristics, and its own strategy.

## Two supertype groups sharing the same entity as supertype

A Party has a legal nature, a Person or an Organization, and it can also have a business role, a Customer or a Supplier.&nbsp; These are two groups sharing the same supertype, and they answer different questions: knowing that a party is a person says nothing about whether it buys from you or sells to you.

&nbsp;

![Image](<lib/NewItem 101.png>)

&nbsp;

In our example, the supertype group Legal nature is total and disjoint, while supertype group Business role is partial and overlapping.&nbsp; One group says nothing about the other, and a party is classified on each axis independently.

&nbsp;

## Deriving several axes

Each group is derived with its own strategy, independently of the other.&nbsp; Below, the same two axes illustrate different combinations.

### When all axes are set to Preserved hierarchy

With both groups on Preserved hierarchy, the Party table ends up with four child tables: Person, Organization, Customer and Supplier.

&nbsp;

![Image](<lib/NewItem 102.png>)

&nbsp;

A party that is a person and a customer has a row in Party, one in Person and one in Customer.

&nbsp;

### When all axes are set to Roll-up

Both groups merge into the same entity, so the Party table contains the two classifications at once.

&nbsp;

With the merge option set to Flat with Discriminator, you get the columns of the four subtypes together, with one discriminator per axis: the column you named for Legal nature, and the is\_customer and is\_supplier booleans for Business role, which is overlapping.

&nbsp;

The merge option set to Nested is particular case. &nbsp; Each group produces its own choice inside the Party collection, with a oneOf choice for a disjoint group and an anyOf choice for an overlapping group, so two choices have to sit on the same node.&nbsp; JSON Schema does not allow two keys of the same name on one node, so Hackolade Studio groups them under an allOf, with one member per group:

&nbsp;

![Image](<lib/NewItem 103.png>)

&nbsp;

The allOf choice means that all the rules within it must be satisfied: the document must respect the legal nature choice and the business role choice.&nbsp; Each axis keeps its own completeness and its own exclusivity.

&nbsp;

### Mixing strategies across axes

It is not required for the two axes to be identical, whether in terms of strategy, completeness, or exclusivity.&nbsp; You may set Business role to Roll-up with the flat option, while Legal nature is set to Roll-down.

&nbsp;

![Image](<lib/NewItem 104.png>)

&nbsp;

The Customer and Supplier table are absorbed within into the Party table, which now contains their attributes and the discriminator.&nbsp; The Party attributes are copied into the Person and Organization table.

&nbsp;

### One supertype per subtype

An entity can be the supertype of as many groups as your model needs. But an entity cannot have more than one supertypes.

&nbsp;

A subtype is a particular case of the entity above it, and being the particular case of two different entities, each with its own axis, says something confused about what the entity is.&nbsp; If such a need appears, it usually reveals a modeling problem, and the answer is generally to keep one inheritance link and to express the other one as a plain relationship.

