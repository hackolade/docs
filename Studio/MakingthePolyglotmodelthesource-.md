# Making the Polyglot model the source-of-truth for technical names

By default, technical names from a physical model are not transferred to the Polyglot during conversion, and the Polyglot naming conventions are not applied automatically.

&nbsp;

However, you may want the Polyglot to hold the technical names when:

* several physical models must share a single naming strategy to manage at the logical / technology-agnostic layer,
* you want to centralize naming decisions instead of repeating them per target,
* you want the Polyglot to act as the master for technical names so that all derived models remain aligned.

&nbsp;

If you want the Polyglot to be the master for technical names after conversion, and have all derived physical models follow them, you must prepare the source model before converting it.&nbsp; This section explains how to do it.

&nbsp;

## &#49;. Clear technical names in the model to be converted

Remove all technical names from the model before performing the conversion.&nbsp; If you want to keep a backup of some values, consider forward-engineering your model to Excel beforehand (and later on use a vlookup function.)

&nbsp;

Clearing technical names can be done in bulk, simply by following instructions in this [use case](<https://hackolade.com/help/NamingConventionsusecases.html#Use%20Case%20#%202:%20clear%20all%20technical%20names%20in%20a%20data%20model>).&nbsp; It is most likely desirable to keep the Naming Conventions disabled for this source model so that the Polyglot becomes the master for technical names, since that's the use case in question here.&nbsp; Unless you specifically want to be in the strategy described in Case 3 of [this page](<https://hackolade.com/help/HandlingoftechnicalnamesduringIm.html#Case%203:%20technical%20names%20exist%20in%20Polyglot,%20but%20target%20applies%20its%20own%20naming%20conventions>).

&nbsp;

Clearing technical names in the original model ensures that it will later accept the technical names coming from the parent Polyglot model.&nbsp; During conversion, Hackolade Studio treats all existing technical names in the original model as target-level enrichments.&nbsp; And enrichments are *never* overwritten by Polyglot values.

&nbsp;

## &#50;. Convert the original model

Perform the Convert operation and choose "Keep models dependent".&nbsp; This makes the generated Polyglot model the source-of-truth, and the original model becomes a derived model.

&nbsp;

At this stage, the Polyglot model created by conversion contains no technical names yet.

&nbsp;

## &#51;. Add technical names in the Polyglot

You can create technical names:

* manually,
* or automatically using naming conventions (recommended, especially with abbreviation files).&nbsp; See [this page](<Namingconventions.md>) for more details.

&nbsp;

## &#52;. Update the dependent physical model

Open the derived (original) model and update the Polyglot references to pull changes from the Polyglot model.&nbsp; The technical names defined in the Polyglot are now:

* propagated into the physical model,
* aligned with the Polyglot,
* treated as derived properties without deviation.

&nbsp;

This establishes the Polyglot as the single source-of-truth for technical names.

&nbsp;

## (Optional) Apply target-specific adjustments

If the physical model requires some exceptions or specialized naming:

* edit individual technical names locally,
* those technical names will automatically become deviations,
* deviations are preserved on future Polyglot definitions updates.

&nbsp;

This allows the physical model to follow the Polyglot *except* where explicit exceptions are required.

