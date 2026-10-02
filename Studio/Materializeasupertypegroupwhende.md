# Materialize a supertype group when deriving from Polyglot

A supertype group describes a hierarchy.&nbsp; A database must physically store that hierarchy in a concrete shape, and several shapes are possible for the same group.&nbsp; The transformation happens during the derive operation from Polyglot.&nbsp; That's when your supertype group stops being a hierarchy and becomes physical tables with columns and constraints that the target understands.

&nbsp;

The Materialization section of the group, in the Polyglot model, is where you tell the shape you expect from the derive operation.&nbsp; .

&nbsp;

![Inheritance materialization strategy](<lib/Inheritance materialization strategy.png>)

&nbsp;

## The strategy property

Select a supertype group and open its Materialization section. The Strategy property is where you choose the strategy that defines the shape downstream:

&nbsp;

![Inheritance materialization strategies list](<lib/Inheritance materialization strategies list.png>)

&nbsp;

Three values (yes, 3...) are available:

* Preserved hierarchy keeps the supertype and each subtype as entities of their own, tied together by foreign keys
* Roll-down removes the supertype and copies its attributes into each subtype
* Roll-up does the opposite, and brings the attributes of the subtypes into the supertype

&nbsp;

The property can also remain empty, which is not a fourth shape but the absence of a choice.&nbsp; When the Strategy property is left empty, each target applies the default of its own family: relational targets keep the supertype and its subtypes as separate entities linked by foreign keys, and document-oriented targets nest the subtypes inside the supertype (nested roll-up).

&nbsp;

A fourth value, Legacy, appears in the list but cannot be selected.&nbsp; It only concerns data models build with Hackolade Studio versions v8.12.11 or before, when a simpler parent-child implementation was in place.&nbsp; See more details in [this page](<Inheritancecreatedbeforeversionv.md>).

&nbsp;

The next pages detail each strategy with a concrete example, to showcase the effects: the entities you get, what happens to your primary and unique keys, and what the existing relationships involving supertypes and subtypes become.

&nbsp;

## Where to set the strategy

The property belongs to the subtype group, in the Polyglot model. What you set there is the strategy used when you derive, unless you pick a different fallback in the derive dialog.

&nbsp;

See [Derive a Polyglot model with supertype groups](<DeriveaPolyglotmodelwithsupertyp.md>) for Fallback materialization (if not set in Polyglot) and Apply fallback to all supertype groups.

