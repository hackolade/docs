# What is "polymorphism"?

**What do you mean with "polymorphism"?**

&nbsp;

One of the great features of JSON as applicable to NoSQL and Big Data, is the ability to deal with evolving and flexible schemas, both at the level of the general document structure, and at the level of the type of a single field.

This is known as ‘schema combination’, and can be represented in JSON Schema with the use of subschemas and the keywords: anyOf, allOf, oneOf, not

Let's take the example of a field that evolves from being just a string type, to sub-document, or with the co-existence of both field types

Traditional ER tools have a hard time dealing graphically with subschemas, whereas with Hackolade:

![Image](<lib/Polymorphism.png>)

A simpler form of JSON's flexibility is for a field to have multiple simple types, i.e. a string in some documents and a numeric in others, or boolean, or null.  Hackolade easily deals with that as well.

***
_Created with the Personal Edition of HelpNDoc: [Easily create Web Help sites](<https://www.helpndoc.com/feature-tour>)_
