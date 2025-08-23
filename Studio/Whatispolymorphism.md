# What is polymorphism?

## Choices

One of the great features of JSON as applicable to NoSQL and Big Data, is the ability to deal with evolving and flexible schemas, both at the level of the general document structure, and at the level of the type of a single field.

This is known as ‘schema combination’, and can be represented in JSON Schema with the use of subschemas and the keywords: anyOf, allOf, oneOf, not

Let's take the example of a field that evolves from being just a string type, to sub-document, or with the co-existence of both field types

Traditional ER tools have a hard time dealing graphically with subschemas, whereas with Hackolade:

![Polymorphism](<lib/Polymorphism.png>)

## Multiple data types

A simpler form of JSON's flexibility is for a field to have multiple simple types, i.e. a string in some documents and a numeric in others, or boolean, or null.  Hackolade Studio easily deals with that as well.&nbsp; An example is with [Union types in Avro Schema](<https://hackolade.com/help/Avroschema.html#Union%20types>).

&nbsp;

Combining a null type with a scalar data type (**boolean**, **int**, **long**, **float**, **double**, **bytes**, and **string**) is very simple, you must click on the + sign to the right of the type property to become:

![Multi-type creation](<lib/Multi-type creation.png>)

which results in multiple blocks of properties appearing below in the Properties Pane:

![Multiple-type block](<lib/Multiple-type block.png>)

&nbsp;

### Complex types

If at least one data type is complex (**record**, **enum**, **array**, **map**, **union**, or **fixed**), then you must use a oneOf choice, for example:

![Avro oneOf choice](<lib/Avro oneOf choice.png>)

