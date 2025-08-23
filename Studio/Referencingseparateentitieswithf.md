# Referencing separate entities with foreign key relationships

# Fully normalized: separate entities with foreign key relationships

In this approach, entities remain fully independent, and relationships are explicitly modeled. This is the most familiar structure for modelers with a background in relational databases.

&nbsp;

Unlike nested structures, this modeling style provides full control over the definition of relationships and cardinalities from both sides.

&nbsp;

## Repository of examples

The sample models used in the examples below can be found in [this repository](<https://github.com/hackolade/demo-models-read-only/tree/main/Pragmatic%20data%20modeling> "target=\"\_blank\"").&nbsp; They can be opened in the browser with the following links, provided proper license:

\- [1-Polyglot.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/1-Polyglot.hck.json\&b=main> "target=\"\_blank\"")

\- [3-Referencing-Oracle.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/3-Referencing-Oracle.hck.json\&b=main> "target=\"\_blank\"")

&nbsp;

Note also the naming convention applied to transform business names in the Polyglot model with Pascal case and spaces, into technical names int he physical models with lowercase and underscores)

&nbsp;

## **Example of customer placing orders**

* A Customer entity exists as a standalone entity.
* An Order entity also exists separately.
* The relationship between them is explicitly defined, with clear cardinalities on both sides.

&nbsp;

This structure naturally fits relational modeling principles, where entities and their relationships are kept independent and precisely controlled.

![Pragmatic modeling - Referencing polyglot](<lib/Pragmatic modeling - Referencing polyglot.png>)

&nbsp;

The relational Physical Model after derivation, reflects the same structure, with primary keys and foreign keys in place.

&nbsp;

![Pragmatic modeling - Referencing physical](<lib/Pragmatic modeling - Referencing physical.png>)

&nbsp;

When the model is normalized in the Polyglot model, you cannot denormalize it during the derivation process. For this reason, this approach is recommended when all target technologies follow similar normalization principles, such as relational databases or other structured systems.

&nbsp;

In mixed environments, where document stores or API designs favor embedded structures, using a nested modeling approach at the logical level provides greater flexibility.

