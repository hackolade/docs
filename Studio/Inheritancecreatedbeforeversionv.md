# Inheritance created before version v8.13.0

Inheritance is not new in Hackolade Studio.&nbsp; Before version v8.13.0, inheritance was modeled as a superclass: a named object holding a parent entity and its child entities, declared in the Relationships tab of the Properties Pane of the model.

&nbsp;

![Image](<lib/NewItem 105.png>)

&nbsp;

Properties also showed on the entities themselves, through the Parent entity and Child entity properties of their Details tab:

&nbsp;

![Image](<lib/NewItem 106.png>)

&nbsp;

Version v8.13.0 did not replace that object, it extended it.&nbsp; A superclass has become a supertype group, with a tab of its own, and with more properties than a superclass had previously: a description, Completeness, Exclusivity, and a materialization strategy.&nbsp; A supertype can also take part in several groups now, one per axis of specialization.&nbsp; The vocabulary evolved as well: the parent entity is now the supertype, and the child entities are now the subtypes.

&nbsp;

Your existing models get automatically adapted when opening them with Hackolade Studio v8.13.0 and after.&nbsp; Everything you had declared in a superclass is now a supertype group.

&nbsp;

## When you open the model

Let's take a data model used earlier in this series of articles, but built with an earlier version: Party is the parent entity, while entities Organization and Person are its child entities, in a superclass named Legal nature.

&nbsp;

Open it in version v8.13.0 and select the group in the Supertype groups tab:

&nbsp;

![Image](<lib/NewItem 107.png>)

&nbsp;

What you had declared previously is still there: the name Legal nature, Party as the Supertype entity, the entities Organization and Person as its subtypes.&nbsp; Two properties are empty however, since a superclass had no equivalent for them: Completeness and Exclusivity.&nbsp; The dashed parts of the group symbol on the ERD alert you to the fact that they should be set.

&nbsp;

The Materialization section is new as well, and its Strategy property is set to the value Legacy.

&nbsp;

![Image](<lib/NewItem 108.png>)

&nbsp;

&nbsp;

### Legacy defines the derive operation behavior

The Legacy materialization strategy tells the derivation to treat the supertype group the way earlier versions did.&nbsp; That is what protects the PostgreSQL model of our example: refresh it, or derive a new physical model, and the shape you get is the one you had previously.&nbsp; Open your Polyglot model in version v8.13.0 does not change the downstream behavior.

&nbsp;

The Legacy materialization strategy is a starting point, not a real strategy.&nbsp; Your groups carry it because they were built before strategies existed, and it appears greyed out in the list of every group, because it shows where a group comes from rather than a behavior that you specified.&nbsp; While a group remains set to Legacy, it keeps the limits of the old implementation:

* Completeness and Exclusivity remain read-only
* the Strategy set for an individual subtype is ignored, so the group cannot mix strategies
* on a Polyglot target, the group is copied as it is, and whatever you change in the derived model is overwritten on the next update

&nbsp;

### Upgrading the inheritance to supertype group with a strategy

Select the group, open Materialization, and set the Strategy to a value that shows as enabled:

&nbsp;

![Image](<lib/NewItem 109.png>)

&nbsp;

Changing the strategy might change the shape of the models derived from your Polyglot model, so give yourself a way back before you start:

* keep a copy of your Polyglot model and of the physical models derived from it
* or, if you work with Git as we recommend, work on a separate branch and review the changes before you commit them

&nbsp;

You can then set a strategy, derive, compare with the physical model you had, try another one, and keep the shape that fits your needs.&nbsp; In a model containing several groups, take them one at a time.

&nbsp;

**Important:** once a group is not longer set to Legacy, the value Legacy can no longer be selected.

&nbsp;

Hackolade Studio does not decide for you what strategy is the best fit for your needs.&nbsp; It depends on how your applications read the data, and the same Polyglot model may legitimately deserve different shapes in different physical models.

&nbsp;

### Opening a model with supertype groups in a version earlier than v8.13.0

A Polyglot model with supertype groups (saved with version v8.13.0) an be opened without errors in an earlier version.&nbsp; The supertype groups are simply not displayed: no Supertype groups tab, and a simplified group symbol on the ERD (no representation for completeness or exclusivity.)&nbsp;

