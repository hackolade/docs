# Inheritance strategies

**Note: inheritance strategies and the related features described below are limited to Polyglot data models.&nbsp; Characteristics defined here do impact how physical data models are derived from Polyglot models with supertypes and subtypes.**

&nbsp;

**Inheritance** is a data modeling relationship in which a more specific type derives from a more general type and inherits its common properties, while adding or refining characteristics of its own.

&nbsp;

A Party is either a Person or an Organization. Both have a name, an email and a creation date, but only a Person has a birth date, and only an Organization has a legal form. You can model this as one entity carrying every attribute, with many empty values; or as two unrelated entities repeating the common part.

&nbsp;

In Hackolade Studio, we represent inheritance with a supertype group where the **supertype** carries what is common, each **subtype** carries what is specific.&nbsp; The group records that a Person *is a* Party, and that Organization *is* a Party as well:

&nbsp;

![Image](<lib/NewItem 38.png>)

&nbsp;

This page covers the concept of inheritance and introduces sub-pages that detail various options. You can find in many details in these sub-pages about working with supertype groups in Hackolade Studio, from building them to deriving them.&nbsp;

&nbsp;

**Note:** the examples used across this series are teaching examples.&nbsp; They are kept small on purpose, they leave out attributes and rules that a real model would carry, and they are not a recommendation on how to model a party, a vehicle or a payment method.&nbsp; The same business concept is legitimately modeled in different ways depending on the organization, the level of abstraction and the use cases.&nbsp; The following pages describe how these structures are handled in Hackolade Studio.\
&nbsp;

## Supertype, subtype, and supertype group

A supertype and its subtypes are sometimes called respectively **superclass** and **subclass**, **parent** and **child**, or **generalization** and **specialization**.&nbsp; These pairs of terms describe the same idea, mainly that one entity is the general form of another one.&nbsp; Hackolade Studio uses supertype and subtype in Polyglot data models.

&nbsp;

What we call a **supertype group** is one supertype together with its **immediate** subtypes.

&nbsp;

## A hierarchy can have as many levels as you need

A subtype can itself become the supertype of another group.&nbsp; A *Person is a Party*, and a Person can also be an Employee or a Contractor:

&nbsp;

![Image](<lib/NewItem 41.png>)

&nbsp;

There are two groups here, not one. Party with its subtypes is the first group,&nbsp; Person with its subtypes is the second group, and Person plays both roles: subtype in the first group, supertype in the second.

&nbsp;

Inheritance follows the levels. An Employee is a Person, and since a Person is a Party, an Employee is a Party as well.&nbsp; Employee therefore holds the attributes of both levels above it. There is no limit to the number of levels you can stack this way.

&nbsp;

## A group is one axis of specialization

The same supertype can also be split along several axes at the same time. A Party is a Person or an Organization by legal nature, and it can **also be** a Customer or a Supplier by business role:

&nbsp;

![Image](<lib/NewItem 42.png>)

&nbsp;

&nbsp;

Legal nature and business role are two **independent** groups sharing the same supertype, instead of one group with four subtypes.&nbsp; Having 2 groups clarifies the situation.&nbsp; Knowing that a party is a Person tells you nothing about whether it buys from you or sells to you.&nbsp; And having multiple groups allows to represent the different permutations of reality: a Person who is a Customer, a Person who is a Supplier, an Organization who is a Customer. Each party is classified once on each axis.

&nbsp;

Here is a test to apply to your own data models: if you can pick a value on one side and still be free to pick any value on the other, you probably need two axes represented by two groups.

&nbsp;

## Every group carries two characteristics: completeness and exclusivity

Two conceptual characteristics describe a supertype group. They are classic in data modeling literature, and they are the two questions a modeler has to answer about any generalization.

### Completeness: total or partial

**Completeness** specifies whether every instance of a supertype must belong to at least one of its subtypes.

&nbsp;

* **Total:** every supertype instance belongs to a subtype, e.g. Legal nature: every party has a legal nature, so every Party is either a Person or an Organization. A party that is neither does not exist.
* **Partial:** some supertype instances may belong to no subtype, e.g. Business role: a party can be neither a Customer nor a Supplier. A prospect you have not sold to yet, or the employer of one of your contacts, is recorded as a Party and belongs to no subtype of that axis.

&nbsp;

### Exclusivity: disjoint or overlapping

**Exclusivity** specifies whether an instance of a supertype may belong to more than one subtype.

&nbsp;

* **Disjoint (aka exclusive):** a supertype instance can belong to only one subtype, e.g. Legal nature: a party is a Person or an Organization, never both at once.
* **Overlapping (aka non-exclusive):** a supertype instance may belong to multiple subtypes, e.g. Business role: a party can be a Customer and a Supplier at the same time. You sell to them, and you also buy from them.

&nbsp;

Both completeness and exclusivity characteristics are set at the level of the group, and not at the level of the supertype, to provide the adequate granularity. That is why the same Party entity carries a total and disjoint axis on one side, and a partial and overlapping one on the other; each group answers the two questions on its own.

&nbsp;

## Materialization strategies

Completeness and exclusivity describe your domain.&nbsp; How the hierarchy actually lands in a physical database is a separate question, with a separate answer, and one that data modeling literature has been discussing for decades.&nbsp;

&nbsp;

**Materialization** specifies how an inheritance hierarchy is represented in the physical data model, particularly how supertype and subtype instances are stored.&nbsp; The commonly recognized options are:

* **Preserved hierarchy inheritance (aka class table):** the supertype is stored in one table and each subtype in its own table.&nbsp; A subtype row generally share the same key as its corresponding supertype row, unless the subtype has its own primary key.&nbsp; This strategy closely reflects the logical model and avoids unnecessary nulls.&nbsp; But it requires joins. &nbsp;
* **Roll-up inheritance (aka single table):**&nbsp; the entire hierarchy is stored in one table, with columns for the supertype and all subtype-specific attributes, usually with a discriminator column identifying the subtype.&nbsp; Simple and efficient, but can produce many nullable columns.&nbsp; **Roll-up** means collapsing subtype attributes into the supertype table.&nbsp; The subtype tables disappear, and a discriminator is typically used to indicate the subtype.&nbsp;
* **Roll-down inheritance (aka concrete table):** each concrete subtype is stored in its own table, including both inherited and subtype-specific attributes.&nbsp; Generally, a separate supertype table is no longer required in the physical model (except if the group is partial.)&nbsp; Reading individual subtypes is simple, but common attributes are duplicated and querying across the hierarchy is harder.&nbsp; **Roll-down** means pushing the supertype attributes down into each subtype table.&nbsp; The supertype table disappears (unless completeness is partial), and each subtype contains both inherited and subtype-specific attributes.

&nbsp;

&nbsp;

The materialization strategy determines how an inheritance hierarchy is transformed into physical structures, based on normalization, expected query patterns, performance requirements, and the completeness and exclusivity constraints of the hierarchy.&nbsp; The choice is mainly driven by a trade-off between **semantic fidelity, storage efficiency, query patterns, and performance**.

**Preserve hierarchy** usually provides the most faithful physical translation of the logical model.&nbsp; The preserved hierarchy strategy is preferable when there are numerous subtype-specific attributes, when normalization matters, and when the hierarchy itself has business meaning.&nbsp; The downside is that retrieving a complete subtype instance often requires joins between the supertype and subtype tables.

**Roll-up** is attractive when subtypes are relatively similar, when the hierarchy is shallow, and when applications frequently query the supertype as a whole.&nbsp; The roll-up strategy avoids joins and gives simple polymorphic queries, but can create many nullable subtype-specific columns.&nbsp; It works especially well when the hierarchy is **exclusive** and there is a clear discriminator.

**Roll-down** is attractive when applications mostly work with concrete subtypes independently, and when applications rarely query the supertype across all subtypes.&nbsp; The roll-down strategy also avoids joins for subtype queries, but duplicates inherited attributes across subtype tables and makes cross-subtype queries more cumbersome.&nbsp; It is generally easier to use when specialization is **total/complete**, because otherwise there may be valid supertype instances that have nowhere to be stored.

&nbsp;

Completeness and exclusivity matter:

* **Total + exclusive** often makes the roll-down strategy particularly natural
* **Partial specialization** generally favors the roll-up strategy or the strategy to preserve hierarchy
* **Overlapping subtypes** make the roll-down and roll-up strategies more complicated because one instance may belong to multiple subtypes
* **Frequent polymorphic queries** favor the roll-up strategy or preserving the supertype
* **Frequent subtype-specific queries** favor the roll-down strategy or the strategy to preserve hierarchy.

&nbsp;

Hackolade Studio does not decide for you.&nbsp; The decision remains for the data modeler to make.&nbsp; We just explain each strategy and show how to apply it.

&nbsp;

A same Polyglot model can be materialized differently from one derivation to the next.&nbsp; Different targets, of course, but also two applications on the same target: an application dealing only with people has no reason to carry the structure of the one dealing with every kind of party.

&nbsp;

The following sub-pages cover how you design that choice in Hackolade Studio, and what each strategy produces at derivation.

