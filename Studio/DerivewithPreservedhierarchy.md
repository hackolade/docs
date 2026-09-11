# Derive with Preserved hierarchy

This inheritance strategy to preserve hierarchy is sometimes known as class table inheritance.&nbsp; The supertype is stored in one table and each subtype in its own table.&nbsp; A subtype row generally share the same key as its corresponding supertype row, unless the subtype has its own primary key.&nbsp; This strategy closely reflects the logical model and avoids unnecessary nulls.&nbsp; But it requires joins. &nbsp;

&nbsp;

Preserve hierarchy usually provides the most faithful physical translation of the logical model.&nbsp; The preserved hierarchy strategy is preferable when there are numerous subtype-specific attributes, when normalization matters, and when the hierarchy itself has business meaning.&nbsp; The downside is that retrieving a complete subtype instance often requires joins between the supertype and subtype tables.

&nbsp;

When deriving from a Polyglot model, the reserve hierarchy strategy keeps every entity of the group, and each of its subtypes become an entity of their own in the physical model, tied together by foreign keys.&nbsp; Nothing gets merged, nothing disappears, and the result in the derived model is the closest to what your Polyglot model looks like. The result is the same as what relational targets produce when the strategy is left empty.

&nbsp;

In the example, we work with the group built earlier: the Party entity as the supertype, plus the Person and Organization entities as its subtypes.&nbsp; The Party entity contains a party identifier attribute as primary key and an email attribute as unique key. The Person entity contains a national identifier attribute as unique key.&nbsp; The Organization entity contains a tax registration number attribute as primary key.

&nbsp;

![Image](<lib/NewItem 24.png>)

&nbsp;

In the Properties Pane of the supertype group of the Polyglot data model, assuming you set the Strategy property to Preserved hierarchy.&nbsp;

&nbsp;

![Image](<lib/NewItem 25.png>)

&nbsp;

Then you you create, for example here a PostgreSQL physical data model derived from the Polyglot model.

&nbsp;

## Derive operation result

In the physical data model, the derive operation results in 3 tables, one per entity of the Polyglot model, plus a foreign key relationship between the supertype and each subtype, with the subtype table as the child table:

&nbsp;

![Image](<lib/NewItem 27.png>)

&nbsp;

The Party table keeps the attributes it had. The Person and Organization tables keep theirs, and each receives the identifier of the Party table in order to create the FK relationship tying the attribute in the Person table to primary key attribute in the Party table.&nbsp; The attributes shared by every party remain in one place, the Party table, and the specific attributes remain with the subtype to which they belong.&nbsp; This is the shape most people have in mind when they encounter a generalization in an ERD.

&nbsp;

### Relationships between a supertype and its subtypes

In each of the two foreign key relationships created:

* the supertype is the parent.
* the subtype is the child.
* the cardinality reads 1..1 on the subtype side and 0..1 on the supertype side.

&nbsp;

You can read the relationship in plain words: a row of the Person table always corresponds to exactly one row of the Party table, since a person is a party; and a row of the Party table corresponds to at most one row of the Person table, since a given party may be an organization instead, or nothing yet.

&nbsp;

These two FK relationships did not exist in your source Polyglot model; the derive operation created them automatically.&nbsp; The operation also automatically defined a default name.&nbsp; The name follows your own default FK naming settings under Tools \> Options \> General.&nbsp; The names you see in your derived model may differ from the ones in the image above if your preferences are set differently.

&nbsp;

![Image](<lib/NewItem 29.png>)

&nbsp;

### Primary keys and unique keys

Since the subtype tables are linked to their supertype table by a foreign key, each subtype table must contain the party identifier. The derive operation applies the rule you designated in the Polyglot model:

* **if the subtype has no primary key of its own**, there is no identity; the supertype identifier gets added as the primary key of the subtype table, and is a also foreign key to the parent supertype table.&nbsp; The relationship is identifying: a row of the subtype is identified by the supertype identifier. This is illustrated by the Person entity in our example: the Person entity doesn't have a primary key in the Polyglot model, so it receives the party identifier as its primary key.
* **if the subtype has its own primary key**, it already has its own identity; that primary key is kept, and the supertype identifier is added as a foreign key in the subtype table, also marked as a unique key.&nbsp; The unique key is what preserves the 0..1 cardinality: without it, two rows of the subtype could point at the same supertype row.&nbsp; This is illustrated by the Organization entity in our example: the Organization entity has its own primary key, the tax registration number.&nbsp; An attribute gets created with a unique key constraint and a foreign key to the PK of the supertype table.

&nbsp;

Everything else stays where it was: the unique key on the email column remains in the Party table, the unique key on the national identifier column remains in the Person table, and columns that were required remain required.

&nbsp;

**Note:** if your supertype has no primary key at all, one gets generated during the derive operation, because this strategy needs something to reference.

&nbsp;

## Identity drives the shape of your derived model

The two situations above are worth reading twice, because they mean that the identity you set in your Polyglot model drives the shape of your physical model.

&nbsp;

There is no right or wrong answer here, and Hackolade Studio does not pick one for you.&nbsp; Putting the primary key only on the supertype means that a party has a single identity, and that being a person or an organization is a specialization of it.&nbsp;

&nbsp;

Giving each subtype its own primary key means the opposite: that these are independent objects which happen to share some attributes.&nbsp; Both are legitimate, and which one fits depends on your domain, not on the tool.

&nbsp;

What the derivation guarantees is that it will follow what you declared. So if the derived model surprises you, the answer is usually in the parent Polyglot model: look at where the primary keys are, and whether they say what you meant.

