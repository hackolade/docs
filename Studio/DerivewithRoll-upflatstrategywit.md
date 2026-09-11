# Derive with Roll-up flat strategy with discriminator

This roll-up inheritance is sometimes known as single table inheritance:&nbsp; the entire hierarchy is stored in one table, with columns for the supertype and all subtype-specific attributes, usually with a discriminator column identifying the subtype.&nbsp; Simple and efficient, but can produce many nullable columns.&nbsp; Roll-up means collapsing subtype attributes into the supertype table.&nbsp; The subtype tables disappear, and a discriminator is typically used to indicate the subtype.&nbsp;

&nbsp;

Roll-up is attractive when subtypes are relatively similar, when the hierarchy is shallow, and when applications frequently query the supertype as a whole.&nbsp; The roll-up strategy avoids joins and gives simple polymorphic queries, but can create many nullable subtype-specific columns.&nbsp; It works especially well when the hierarchy is exclusive and there is a clear discriminator.

&nbsp;

The Roll-up strategy brings the subtypes' attributes inside the supertype: instead of several entities, you get just one.

&nbsp;

With Hackolade Studio when performing a derive operation with the Roll-up strategy, there are two ways to merge the subtypes into the supertype, as set in the Merge option property:

* the traditional way in relational databases with the option Flat with discriminator puts all the attributes at the same level, with a column telling the rows apart
* Nested keeps each subtype as an object inside the supertype, typically useful with NoSQL document databases.

&nbsp;

This page covers the first option; while the next page covers the second.

&nbsp;

Where Nested keeps each subtype as an object of its own, flattening puts every attribute at the same level, in a single table, and adds a column that tells the rows apart.

&nbsp;

In the example, we work with the group built earlier: we keep the Legal nature group: the Party entity, with the Person and Organization entities as its subtypes. The group has total completeness and disjoint exclusivity.

&nbsp;

&nbsp;

![Image](<lib/NewItem 83.png>)

&nbsp;

&nbsp;

In the Properties Pane of the supertype group of the Polyglot data model, assuming you set the Strategy property to Roll-up with the Merge option to Flat with discriminator.

&nbsp;

## The discriminator

After the derive operation, all attributes of all subtypes end up in a single table.&nbsp; So nothing in a row would tell whether a party describes a person or an organization.&nbsp; Adding a column with this information is common practice; it is called a discriminator, and it tells, for a given supertype group (axis of specialization), which subtype a row belongs to.

&nbsp;

The data type of the discriminator depends on the exclusivity of the supertype group:

* in a **disjoint** group, a row belongs to only one subtype, so a single column holding one value per subtype is enough. You choose the name for the discriminator, usually the name of the axis: for example nature.
* in an **overlapping** group, a row may belong to several subtypes at once.&nbsp; The derive operation generates a boolean column per subtype, automatically named is\_\<subtype name\>.&nbsp; .

&nbsp;

The Discriminator name property therefore appears in the merge option when you choose value disjoint in the exclusivity property.&nbsp; The Discriminator name is optional, but it is useful:

* **if filled, then** the derive operation creates a column for the discriminator, with that name and the default type of the target
* **if left empty, then** the derive operation creates nothing, either because you declared the attribute yourself in the supertype, or because you do not want a discriminator at all

&nbsp;

In other words, a discriminator is generated only when you specify a name.

&nbsp;

The subtype group Legal nature is disjoint.&nbsp; Enter the name nature as a Discriminator name, then derive into a physical target. &nbsp;

&nbsp;

![Image](<lib/NewItem 84.png>)

&nbsp;

&nbsp;

## Derive operation result

In the physical data model, the derive operation results in a single table, Party, containing the attributes of the supertype plus those of both subtypes:

&nbsp;

![Image](<lib/NewItem 85.png>)

&nbsp;

&nbsp;

The Nature discriminator column you named is included, and the columns coming from a subtype are nullable: a row describing an organization has no birth date, and a row describing a person has no legal form.&nbsp; This is the trade-off of this shape: a single table, no join, and a list of empty values that grows with the number of subtypes.

&nbsp;

The group Legal nature has completeness set to total, so every row belongs to a subtype and the discriminator always has a value.&nbsp; In a group with completeness set to partial, it also has to accommodate the rows belonging to no subtype, either with a null value or with a value of your own meaning "none".

&nbsp;

### Primary and unique keys

The merged table keeps the identity of the supertype: its primary key, its unique keys and its required attributes remain unchanged.&nbsp; If the supertype has no primary key, the merged table has none either; the identity of a subtype is never promoted to replace it.

&nbsp;

Coming up from the subtypes:

* a primary key of a subtype becomes a unique key.&nbsp; There should already be an identity in the merged table, and it is the one of the supertype.
* a unique key of a subtype remains a unique key
* a required attribute of a subtype becomes nullable in the single table, as the rows of the other subtypes would carry no value for it

&nbsp;

In our example, the tax registration number of Organization was its primary key and becomes a unique key on a nullable column; the national identifier of Person keeps its unique key the same way.

\
**Note:** a unique key on nullable columns is not read the same way by every database. Check what your target does with missing values in a unique constraint before relying on it.\
&nbsp;

### Relationships that pointed at the subtypes

A foreign key relationship attached to the subtypes (which disappear) follows the roll-up to become foreign key relationship(s) into the supertype table.

&nbsp;

Consider this example: an organization owns trucks.

&nbsp;

![Image](<lib/NewItem 86.png>)

&nbsp;

With the roll-up, the foreign key relationship would no longer connect the Truck table to the Organization, as there is no Organization table.&nbsp; But the derive operation creates a foreign key relationship from the Truck table to the Party table, anchored on the tax registration number, which was the primary of the Organization subtype entity, and is now a unique key in the rolled-up table:

&nbsp;

![Image](<lib/NewItem 87.png>)

&nbsp;

**Note: a**ny mandatory cardinality (1 or 1..n) on the side of the "other" entity linked to the subtype is relaxed to become optional (0..1 or 0..n).&nbsp; The foreign key relationship connects to the supertype, which may represent a different subtype than the one that originally includes the relationship in the Polyglot model.&nbsp; If the cardinality is already optional (0..1 or 0..n), as in our example, no modification occurs.\
&nbsp;

## Exclusivity determines the discriminator type

Take another supertype group example: the Party entity again, but along its other axis, Business role, with Customer and Supplier entities as its subtypes.

&nbsp;

&nbsp;

![Image](<lib/NewItem 88.png>)

&nbsp;

In this example the group is declared overlapping, because a party you sell to may also be a party you buy from.&nbsp; The Legal nature group was disjoint: a party is a person or an organization, never both.&nbsp; Here we decide to model things so that the same party can legitimately be a customer and a supplier at the same time. (Note that there are other ways to model this case.)

&nbsp;

You may choose the Merge option for this group to be Flat with discriminator, and you may choose to leave empty the Discriminator name (because it is not relevant for an overlapping supertype group.)&nbsp; The derive operation automatically generates a boolean column per subtype, named is\_\<subtype name\>:

&nbsp;

![Image](<lib/NewItem 89.png>)

&nbsp;

The boolean columns are generated because a single column can only contain a single value, and the group says that a row may belong to several subtypes at once.&nbsp; A row that is both a Customer and a Supplier gets both boolean columns set to true; in a partial group.&nbsp; Whereas a row belonging to no subtype gets them both set to false.&nbsp; The derivation simply follows how the supertype group is designed in the subtype group properties of the parent Polyglot model.

