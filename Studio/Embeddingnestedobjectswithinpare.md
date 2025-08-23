# Embedding nested objects within parent entities

# Fully embedded: nested objects within parent entities

This modeling style is particularly recommended when your ecosystem includes document-oriented databases, APIs, or other technologies that favor nested structures. In Polyglot modeling, when different paradigms must coexist, nesting generally takes precedence because it maximizes compatibility and flexibility across heterogeneous targets.

&nbsp;

Different modeling situations can arise with this approach, each introducing its own considerations. Let’s explore them progressively.

&nbsp;

## Repository of examples

The sample models used in the examples below can be found in [this repository](<https://github.com/hackolade/demo-models-read-only/tree/main/Pragmatic%20data%20modeling> "target=\"\_blank\"").&nbsp; They can be opened in the browser with the following links, provided proper license:

\- [1-Polyglot.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/1-Polyglot.hck.json\&b=main> "target=\"\_blank\"")

\- [2a-Embedding to normalization before modeler intervention-Oracle.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/2a-Embedding%20to%20normalization%20before%20modeler%20intervention-Oracle.hck.json\&b=main> "target=\"\_blank\"")

\- [2b-Embedding to normalization after modeler intervention-Oracle.hck.json](<https://studio.hackolade.com/?g=github\&o=hackolade\&r=demo-models-read-only\&f=Pragmatic%20data%20modeling/2b-Embedding%20to%20normalization%20after%20modeler%20intervention-Oracle.hck.json\&b=main> "target=\"\_blank\"")

&nbsp;

Note also the naming convention applied to transform business names in the Polyglot model with Pascal case and spaces, into technical names int he physical models with lowercase and underscores)

&nbsp;

## Nesting object and array

In this first example, related objects are fully embedded within the parent entity in a straightforward structure. The Customer entity contains:

* An Address object (simple nested structure)
* An Orders array (list of nested objects)

&nbsp;

![Pragmatic modeling - nesting object and array](<lib/Pragmatic modeling - nesting object and array.png>)

&nbsp;

&nbsp;

This structure naturally fits document-oriented targets or API designs where hierarchical data is standard.

&nbsp;

By deriving this Polyglot Model to a relational physical model with normalization, the structure transforms as follows:

* The Address **object** becomes a separate entity, linked to Customer with a **1-to-1 relationship**.
* The Orders **array** becomes a separate entity, linked to Customer with a **1-to-many relationship**.
* The Ordered product **array**, originally nested inside Order, also become a separate entity with a **1-to-many relationship**.

&nbsp;

![Pragmatic - physical derived normalized](<lib/Pragmatic - physical derived normalized.png>)

&nbsp;

For illustration purposes, entities generated from nested objects are displayed in blue in the screenshot to highlight their origin. You will also notice that primary keys and foreign keys have been automatically added to the physical model as part of the normalization process.

&nbsp;

## Handling shared nested objects across multiple entities

Let’s now extend our previous example to a slightly more complex but common scenario: the same nested object appears in multiple parent entities.

In this case:

* The Customer entity contains an embedded Address object
* The Supplier entity also contains an embedded Address object

&nbsp;

This approach remains consistent with a Polyglot Logical Model that favors embedded structures, especially when document-oriented or API targets are involved.

![Pragmatic -Nested object shared in 2 entities](<lib/Pragmatic -Nested object shared in 2 entities.png>)

&nbsp;

&nbsp;

When deriving this model to a relational physical target with normalization, the structure unfolds as follows:

* Each nested Address generates a corresponding entity, resulting in two separate Address entities in the physical model.

&nbsp;

![Pragmatic modeling - same object nested twice](<lib/Pragmatic modeling - same object nested twice.png>)

&nbsp;

&nbsp;

This is expected behavior in the derivation process, as the Polyglot Model remains agnostic to the technical constraints of specific targets.&nbsp;

&nbsp;

After derivation, the modeler must adjust the physical model to avoid unnecessary duplication:

* removing the superfluous Address entity — for example, the one generated from the Supplier nested object.
* creating a relationship between Supplier and the remaining shared Address entity, which originated from the nested object in Customer.

&nbsp;

![Image](<lib/Pragmatic modeling - same object nested adjus.png>)

&nbsp;

This illustrates a key trade-off in Polyglot Modeling:

* The logical model stays abstract and compatible with diverse targets.
* Minor adjustments are sometimes necessary in physical models to align with relational best practices.

&nbsp;

## Impact of nesting on inverse cardinalities

In a nested structure, the relationship between entities is always modeled from the **perspective of the containing entity**.

* If you nest a simple object: it results in a **1-to-1** relationship.
* If you nest an array: it results in a **1-to-many** relationship.

&nbsp;

However, this perspective does not always fully reflect the business reality, especially when the nested entity is shared across multiple occurrence of the containing entity. Let's illustrate with an example. The Customer entity contains a nested Membership plan object, which includes details like its name, its description...

&nbsp;

![Pragmatic modeling - nesting inverse cardinal](<lib/Pragmatic modeling - nesting inverse cardinal.png>)

&nbsp;

&nbsp;

From the Customer perspective, this looks like a simple **1-to-1** relationship: each customer has a single membership plan.

&nbsp;

But in reality:

* Multiple customers can share the same Membership plan.
* The true relationship is **many-to-1** from Customer to Membership plan.

&nbsp;

When deriving this Polyglot Model to a relational physical model with normalization:

* The nested Membership plan becomes a separate entity.
* By default, the relationship generated reflects the original nesting: **1-to-1** between Customer and Membership plan.

&nbsp;

![Pragmatic modeling - phys inverse card](<lib/Pragmatic modeling - phys inverse card.png>)

&nbsp;

This behavior is expected and consistent with the model's structure. Since the relationship is only modeled from the perspective of the containing entity (Customer) in the Polyglot model, the system cannot infer the true business cardinality in the opposite direction.

&nbsp;

This is where the expertise of the data modeler is essential to manually adjust the cardinality to **many-to-1**, ensuring the physical model accurately represents the shared nature of membership plans.

&nbsp;

![Pragmatic modeling - phys inverse card adj](<lib/Pragmatic modeling - phys inverse card adj.png>)

&nbsp;

This example highlights the importance of validating and adjusting relationships after derivation, especially when nested structures simplify the logical model but do not fully capture complex cardinalities required in certain physical implementations.

&nbsp;

