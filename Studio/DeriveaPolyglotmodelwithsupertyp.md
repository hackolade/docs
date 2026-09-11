# Derive a Polyglot model with supertype groups

The previous page showed where to set the materialization strategy of a supertype group, and what each strategy means.&nbsp; This page covers the derive operation itself: the dialog, and how you choose which entities reach the target physical data model.

## Derive dialog hint

When you derive from a Polyglot model with supertype groups, Hackolade Studio display a hint in the dialog:

&nbsp;

![Image](<lib/NewItem 74.png>)

&nbsp;

This is a&nbsp; reminder that the supertype groups are derived too, following the materialization set in the Polyglot model.&nbsp; When no strategy is set, the default of the target applies, and completeness and exclusivity can change the result.&nbsp;

&nbsp;

### Select what to derive

Let's take the Vehicle supertype group, with Vehicle as its supertype and Car, Truck and Motorcycle as its subtypes.&nbsp; Car is itself the supertype of the Propulsion group, with Combustion car and Electric car as its subtypes.

&nbsp;

![Image](<lib/NewItem 73.png>)

&nbsp;

When you derive from Polyglot and select the parent Polyglot data model, you are presented with a selection dialog.&nbsp; Under Polyglot objects to derive, the tree lists the entities of the model, including subtypes shown under their supertype.

&nbsp;

By default everything in the Polyglot model to derive from is pre-selected.&nbsp; And if you're happy with that, you can just click the Apply button.

&nbsp;

It is only if you want to choose a subset of the Polyglot model that you should adjust the selection, typically using multi-select with the Shift or Ctrl/Cmd button plus selection with your mouse.

&nbsp;

![Image](<lib/NewItem 72.png>)

&nbsp;

&nbsp;

The physical model we want in this example serves one purpose: tracking the company vehicles assigned to employees.&nbsp; In our example those are cars, and the application does not care how they are powered.&nbsp; So Truck, Combustion car and Electric car are not needed.

&nbsp;

Undesired subtypes in the derived model can be unselected via Ctrl/Cmd + click:

&nbsp;

![Image](<lib/NewItem 4.png>)

&nbsp;

The resulting derived model will only contain tables for Vehicle, Motorcycle, and Car:

&nbsp;

![Image](<lib/NewItem 22.png>)

\
**Note:** all subtypes, even if not selected for the derive operation, remain visible in the Object Browser tree.&nbsp; The OB tree lists what was defined in the Polyglot model, i.e. not the selection during the derive operation.\
&nbsp;

## Polyglot only property

An entity marked Polyglot only never reaches a derived model.&nbsp; Inside a supertype group the property behaves like an entity left out of the selection.

&nbsp;

## Derive into another Polyglot model

Polyglot is a target like the other physical targets.&nbsp; When you derive a Polyglot model into another Polyglot model, then the groups are materialized following their strategy, exactly as they would be on a relational or a document-oriented target.

