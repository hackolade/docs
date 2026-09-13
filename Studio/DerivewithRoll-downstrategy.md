# Derive with Roll-down strategy

This roll-down inheritance strategy is sometimes known as concrete table inheritance: each concrete subtype is stored in its own table, including both inherited and subtype-specific attributes.&nbsp; Generally, a separate supertype table is no longer required in the physical model (except if the group is partial.) &nbsp; Reading individual subtypes is simple, but common attributes are duplicated and querying across the hierarchy is harder.&nbsp; Roll-down means pushing the supertype attributes down into each subtype table.&nbsp; The supertype table disappears (unless completeness is partial), and each subtype contains both inherited and subtype-specific attributes.

&nbsp;

Roll-down is attractive when applications mostly work with concrete subtypes independently, and when applications rarely query the supertype across all subtypes.&nbsp; The roll-down strategy also avoids joins for subtype queries, but duplicates inherited attributes across subtype tables and makes cross-subtype queries more cumbersome.&nbsp; It is generally easier to use when specialization is total/complete, because otherwise there may be valid supertype instances that have nowhere to be stored.

&nbsp;

This roll-down strategy gives each subtype table everything it needs to stand alone.&nbsp; The attributes of the supertype are copied into every subtype, and the supertype entity itself usually disappears from the derived model, again unless completeness is partial.&nbsp; There is no foreign key to follow, and no join to write: a person is one row in one table.

&nbsp;

In the example, we work with the group built earlier: the Party entity as the supertype, with a party identifier attribute as primary key and an email attribute as unique key; the Person entity as a subtype, with a unique key constraint on its national identifier; the Organization entity as a subtype, with its own primary key, the tax registration number.&nbsp; Legal nature is total and disjoint.

&nbsp;

![Inheritance roll-down Party Polyglot model](<lib/Inheritance roll-down Party Polyglot model.png>)

&nbsp;

In the Properties Pane of the supertype group of the Polyglot data model, assuming you set the Strategy property to Roll-down&nbsp;

&nbsp;

![Inheritance roll-down Party group props](<lib/Inheritance roll-down Party group props.png>)

&nbsp;

Then you you create, for example here a PostgreSQL physical data model derived from the Polyglot model.

&nbsp;

## Derive operation result

In the physical data model, the derive operation results in 2 tables, Person and Organization, each carrying its own columns, plus those it inherited from the Party entity in the parent Polyglot model:

&nbsp;

![Inheritance roll-down Party derive result](<lib/Inheritance roll-down Party derive result.png>)

&nbsp;

The Party entity is gone, but nothing was lost: every party is a person or an organization, and each table contains the columns previously in the Party entity: Party identifier, Email, Name, Creation data, and Main contact identifier.

&nbsp;

### Primary and Unique keys

The supertype identifier, if any, is copied into each subtype, following a logic similar to the one in the Preserved hierarchy strategy:

* if the subtype has no primary key of its own, the rolled-down supertype identifier gets added as the primary key of the subtype table. This is the case for the Person table.
* if the subtype has its own primary key, that key is kept and the rolled-down supertype identifier becomes a unique key.&nbsp; This is the case for the Organization table, which keeps its tax registration number as primary key.

&nbsp;

The unique key for the email column is copied into both tables and stays a unique key in each of them.&nbsp; Attributes that were required remain required, since a value existed for every party.

\
**Note:** a unique key copied this way is enforced within each table, not across them.&nbsp; Nothing prevents a row of the Person table and a row of the Organization table from carrying the same email.&nbsp; Global uniqueness is what you give up when you choose this materialization strategy.\
&nbsp;

### Relationships that pointed at the supertype

A foreign key relationship attached to the supertype (which disappears) follows the roll-down to become foreign key relationship(s) into the subtype(s).

&nbsp;

Consider this example: parties have addresses.&nbsp; An Address entity contains a street, a postal code and a city, and it is linked to the party to which it belongs: an address always belongs to one party, and a party may have several addresses, so the relationship cardinality is 1 on the Party side and 0..n on the Address side.

&nbsp;

![Inheritance roll-down FK relationships](<lib/Inheritance roll-down FK relationships.png>)

&nbsp;

Because the Party entity disappears in the derived model, the foreign key relationship cannot be kept as it is.&nbsp; It becomes two foreign key relationships, one towards the Person table and one towards the Organization table:

&nbsp;

![Inheritance roll-down derived FK relationships](<lib/Inheritance roll-down derived FKrelationships.png>)

&nbsp;

&nbsp;

#### About cardinalities

You may have noticed that the cardinality changed during the operation: the 1 on the Party side becomes 0..1 in each of the two relationships.&nbsp; An address still belongs to exactly one party, but that party is now a row in one of the two tables only, so neither relationship can require a match on its own. &nbsp;

&nbsp;

The same happens to any relationship attached to the supertype, in either direction.&nbsp; A cardinality that was already optional remains as it was; a 1 becomes a 0..1, and a 1..n becomes a 0..n.

&nbsp;

#### About the names

Both relationships come from the same one you defined in the Polyglot model, so they keep that name, plus a suffix in parentheses is added to tell them apart.&nbsp; The suffix is the name of the subtype involved.&nbsp; Here, "Party to Address" becomes "Party to Address (Person)" and "Party to Address (Organization)". When the roll-down produces only one relationship, there is nothing to distinguish, and the name remains unchanged.

&nbsp;

## Completeness determines whether the supertype survives

Take another supertype group example: the Vehicle entity, with Car, Truck and Motorcycle as its subtypes.

&nbsp;

&nbsp;

![Image](<lib/Inheritance roll-down Polyglot completeness.png>)

&nbsp;

In this example the group is declared partial, because the fleet also contains trailers.&nbsp; A trailer is a vehicle, it has a registration number, a brand and a purchase date, and nothing more to record; it is none of the three declared subtypes.&nbsp; Another company modeling the same hierarchy might well declare the supertype group with a total completeness.&nbsp; This is a design choice, made case by case.

&nbsp;

&nbsp;

![Inheritance roll-down Polyglot props](<lib/Inheritance roll-down Polyglot props.png>)

&nbsp;

&nbsp;

When this model gets derived with the roll-down strategy, the Vehicle table remains in the derived model, next to the Car, Truck, and Motorcycle tables:

&nbsp;

![Inheritance roll-down completeness derived](<lib/Inheritance roll-down completeness derived.png>)

&nbsp;

The Vehicle table gets derived because the group says that vehicles belonging to no subtype exist, and those rows need a table.&nbsp; Nothing was decided at derivation time; the derivation only follows what the group declares.

&nbsp;

Note that there is no foreign key relationship between the subtype tables and the supertype table.&nbsp; The reason is as follows: given the roll-down strategy, each of the subtype table is self standing, with each containing all the necessary columns inherited from the supertype attributes.&nbsp; But because completeness was set as partial, there is a need for the Vehicle table so it can store rows related to vehicles that are specifically not a car, not a truck, and not a motorcycle.

&nbsp;

#### Major difference with the Preserved hierarchy strategy

The Vehicle table here is not the same as after the derive operation using the Preserved hierarchy strategy. &nbsp;

&nbsp;

With the materialization strategy "Preserved hierarchy", a car would occupy two rows: one in the Vehicle table for the common part, one in the Car table for the specific part, joined by a foreign key:

&nbsp;

![Inheritance roll-down vs preserved hierarchy](<lib/Inheritance roll-down vs preserved hierarchy.png>)

&nbsp;

So the question to ask yourself is not whether you want to keep the supertype table.&nbsp; The question is: which shape your data should take:

* one row per object, in the table matching its nature, with the common attributes repeated in each table
* or a normalized shape, with the common part in one place and a join to reach the specific part

&nbsp;

The first option corresponds to the roll-down strategy, the second to the Preserved hierarchy strategy.&nbsp; Both strategies keep a supertype table when the group is partial, but they do not result in the same rows.

