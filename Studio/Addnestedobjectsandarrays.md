# Add nested objects and arrays

In the previous tutorial, we saw how to create a first data model, which was quite basic but allowed us to review different ways to enter information in Hackolade Studio, as well as different ways to visualize structures.&nbsp; By the end of this tutorial, you will master the creation of more complex data structures.

&nbsp;

You may also [view this tutorial](<https://youtu.be/uk-K3aNosJg> "target=\"\_blank\"") on YouTube.&nbsp; Summary slides can be found [here](<https://www.slideshare.net/PascalDesmarets1/hackolade-tutorial-part-5-add-nested-objects-and-arrayspdf> "target=\"\_blank\"").

&nbsp;

**Note:** complex data types are not available in all target technologies supported by Hackolade, in which case the feature is disabled.&nbsp; Or they may use a different terminology: map, struct, list, tuple, enumeration, ...&nbsp; Hackolade uses the terminology and data types supported by the target technology.

## Object

To append a sub-object in an ERD entity, we can right-click in the entity

![Tutorial - add an object in ERD](<lib/Tutorial - add an object in ERD.png>)

&nbsp;

We can do the same thing in the entity's tab:

![Tutorial - add an object in tab](<lib/Tutorial - add an object in tab.png>)

&nbsp;

While it is not possible to add a child attribute to a scalar data type, a complex (non-scalar) data type such as objects and arrays hold a sub-structure, for example:

![Tutorial - add an address object](<lib/Tutorial - add an address object.png>)

&nbsp;

&nbsp;

## Array

Similarly, you can add an array where each item matches the same schema:

![Image](<lib/Tutorial - add an array item.png>)

&nbsp;

or tuples, with a sequence of ordered items with possibly different schemas

![Image](<lib/Tutorial - add a tuple.png>)

&nbsp;

Note that in Hackolade for documentation purposes, you may assign a friendly name to an array item:

![Image](<lib/Tutorial - array item friendly name.png>)

&nbsp;

As expected, Hackolade Studio continues to generate the JSON Schema and sample JSON Data document.&nbsp; They are visible in the JSON Preview lower tab for each entity upper tab.

&nbsp;

In this tutorial, we reviewed how to create more complex structures with objects and arrays.&nbsp; In the next tutorial, we will cover JSON Schema choices (oneOf, allOf, anyOf) as well as conditional application of subschemas, and pattern fields.

