# Handling technical names during convert and merge to an existing Polyglot

When converting a model into an **existing** Polyglot with **"merge”** strategy (and not overwrite), any technical names already present in that Polyglot are preserved.&nbsp; To determine which existing Polyglot modeling object corresponds to which original modeling object, the matching is performed exclusively on the business name.

&nbsp;

If the user chooses to make the models dependent, the original model becomes a derived model of the Polyglot.&nbsp; Let's illustrate the case.

&nbsp;

## Initial situation before the convert and merge

&nbsp;

![Convert and merge before](<lib/Convert and merge before.png>)

&nbsp;

## After the convert and merge

&nbsp;

![Derive after convert and merge](<lib/Derive after convert and merge.png>)

&nbsp;

If the original modeling object had no technical name, the technical name from the existing Polyglot is propagated into the derived model.&nbsp; This is the expected behavior when the Polyglot should drive technical naming.

&nbsp;

If the original object already had a technical name, its technical name is preserved as-is, but it becomes a deviation, since it no longer matches the technical name inherited from the Polyglot.&nbsp; This deviation behaves like any other overridden property in a derived model.

&nbsp;

The coupling - if any - is preserved.&nbsp; The technical name may be regenerated based on the physical model’s naming conventions, but it still becomes a deviation if the resulting value differs from the Polyglot’s technical name.

&nbsp;

**Important note:** if the Polyglot already contains technical names, merging it with a physical model will naturally introduce deviations for any object in the physical model that already had its own technical name.&nbsp; If the goal is for the Polyglot to fully control technical names after the merge, technical names must be cleaned from the physical model before running the convert \& merge, as described in [this page](<MakingthePolyglotmodelthesource-.md>).&nbsp; If the intent is to keep the physical model’s specific naming, simply leave the technical names in place -- they will be preserved as deviations.

&nbsp;

To facilitate understanding if name coupling is enabled in Polyglot, here is the diagram:

![Convert and merge after with coupling](<lib/Convert and merge after with coupling.png>)

