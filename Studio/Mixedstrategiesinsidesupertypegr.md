# Mixed strategies inside supertype group

Setting the strategy at the level of the supertype group is a convenience: you set the value once, and it gets applied to all of its subtypes. They are all treated identically.&nbsp;

&nbsp;

But it may wish to configure them differently, so that a given subtype gets materialized differently from the others.&nbsp; The strategy can then be set at the level of a single subtype.

&nbsp;

## Setting an exception

Every subtype of a group contains its own Strategy property, set by default to Inherited from group strategy.&nbsp; If you change it, that subtype alone stops following the group adopts the specified strategy:

&nbsp;

![Inheritance mixed strategies in supertype group](<lib/Inheritance mixed strategies in supertype grp.png>)

&nbsp;

The value set for a subtype always wins over the one set at the level of the group.

&nbsp;

### Our example

Take the Vehicle supertype group.&nbsp; The entity Vehicle is the supertype, with the entities Car, Truck, and Motorcycle as subtypes:

&nbsp;

![Inheritance mixed strategies Polyglot model](<lib/Inheritance mixed strats Polyglot model.png>)

&nbsp;

&nbsp;

In this example, cars and motorcycles are company vehicles assigned to employees, and they are managed together, alongside the rest of the fleet.&nbsp; Trucks, on the other hand, are handled by another system, which expects one self-contained table, and knows nothing about our own hierarchy.

&nbsp;

So the group default is set to a Preserved hierarchy strategy, while the Truck entity alone is set to Roll-down strategy.

&nbsp;

![Inheritance mixed strategies Polyglot props](<lib/Inheritance mixed strats Polyglot props.png>)

&nbsp;

&nbsp;

## Derive operation result

In the physical data model, the derive operation results in 4 tables still. &nbsp;

&nbsp;

The Car and Motorcycle tables behave as described on the Preserved hierarchy strategy page: each keeping its own columns and receiving the identifier of the Vehicle table as a foreign key.

&nbsp;

The Truck table behaves as described on the Roll-down strategy page:&nbsp; it contains the vehicle columns as its own columns, and it has no foreign key towards the Vehicle table.&nbsp; As expected, nothing links the Truck table to the rest anymore, given the Roll-down strategy set in the parent Polyglot model.

&nbsp;

![Inheritance mixed strategies derive result](<lib/Inheritance mixed strats derive result.png>)

&nbsp;

&nbsp;

The derive operation applies the strategy of each supertype-subtype **pair** independently.&nbsp; Setting an exception on the Truck entity has no effect for the Car and Motorcycle tables.

