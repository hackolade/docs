# Recreate broken reference link to a Polyglot model

When working with derived models, it may happen that the reference link to the source Polyglot model is accidentally deleted.&nbsp; As a result, the derived model is disconnected and cannot be updated anymore from the Polyglot model.

&nbsp;

This article explains how to repair a derived physical model that has lost its reference link to a Polyglot model. At a high level, the process consists of creating a new derived physical model from the Polyglot, then using Compare \& Merge with the broken model, so that the merged result recovers both the content of the broken model and the valid reference link.

&nbsp;

![Repair polyglot broken ref link flow](<lib/Repair polyglot broken ref link flow.png>)

&nbsp;

You should follow the steps below:

1. Derive the Polyglot into a new temporary physical model of the same target as the broken one. This new model contains a valid reference link to the Polyglot model.
1. Compare \& Merge the new derived model with the broken one:
- &nbsp;

  - On the left, place the broken physical model whose reference link was removed.
  - On the right, place the newly derived physical model that is linked to the Polyglot model (the result of the compare \& merge inherit the derivation links from the model on the right).

3. Select to perform the comparison based on Business names.
3. Select the objects and properties from the left (the broken model) that you want to keep. For example, if the broken model contains additional attributes in an entity, you can bring them into the merged result.

The repaired physical model contains the content from the broken model while restoring its reference link to the Polyglot.

![Repair polyglot broken ref link steps](<lib/Repair polyglot broken ref link steps.png>)

When all steps are completed, we suggest to rename the old model file (the one with the broken link) to an archive name, and to rename the merged model to the previous name.&nbsp; You should not need the right-hand model, which was only useful for this exercise.

&nbsp;

&nbsp;

&nbsp;

