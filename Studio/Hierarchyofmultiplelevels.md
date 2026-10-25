# Hierarchy of multiple levels

A supertype group has one supertype and its immediate subtypes. A subtype can itself become the supertype of its own group, which gives a hierarchy of several levels.

&nbsp;

Let's illustrate with an example. A Person is a Party, and a Person can also be an Employee or a Contractor. That gives us two groups: Legal nature, with Party as its supertype, and Person role, with Person as its supertype.

&nbsp;

![Inheritance multi-level Party Polyglot model](<lib/Inheritance multi-level Party Polyglot model.png>)

&nbsp;

## Two distinct supertype groups

The Person entity is a subtype in the first group and the supertype in the second. Each supertype group carries its own completeness, its own exclusivity, and its own strategy. Nothing is shared between them except the entity that they have in common.

&nbsp;

![Inheritance multi-level Party Polyglot props](<lib/Inheritance multi-level Party Polyglot props.png>)

&nbsp;

During a derive operations, attributes cascade through the levels according to the strategy of each of the groups. An Employee contains its own attributes, those of Person, and through Person those of Party.

&nbsp;

There is no limit to the number of levels you can stack this way.

&nbsp;

## Derive a hierarchy

Each group is derived with its own strategy, level by level. If you set both groups to `Preserved hierarchy`, then you get five tables chained by foreign keys: The Employee and Contractor tables point at the Person table, which points at the Party table.

&nbsp;

![Inheritance multi-level derived hierarchy](<lib/Inheritance multi-level derived hierarchy.png>)

&nbsp;

There is no obligation for cascading groups to be set to identical strategies. Keep the group Legal nature set to a `Preserved hierarchy` strategy, and set the Person entity role to `Roll-up` for example, and you get a Person table containing the employee and contractor columns, still linked to the Party table by a foreign key:

&nbsp;

![Inheritance multi-level derived partial roll-up](<lib/Inheritance multi-level derived part roll-up.png>)

&nbsp;

The rules described with each strategy properties apply to its own level. What gets inherited from a level above is treated like any other attribute of the entity that receives it: with both groups with a `Roll-down` strategy, an Employee table ends up containing the party columns, the person columns, and of course its own columns.

&nbsp;

> [!NOTE]
> In our example, completeness for the Person role is partial. So the Person table is kept for those instances for when a Person that can be neither an Employee nor a Contractor. You can find more info on the page dedicated to the [roll-down strategy](DerivewithRoll-downstrategy.md).

&nbsp;

![Inheritance multi-level derived partial roll-down](<lib/Inheritance multi-level derived partroll-down.png>)
