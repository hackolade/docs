# Compare and merge models

Before using this feature, you may want to read the [versioning concept page](<Modelversioning.md>) as it is useful to understand the philosophy behind our approach to comparing and merging.

&nbsp;

&nbsp;&nbsp; &nbsp;

A compare and merge operation may involve a combination of: a previous reference model, a model issued from the reverse-engineering of a database instance or some other source, a model that has evolved in a separate branch, etc...

&nbsp;

The comparison in Hackolade handles the synchronized scrolling of hierarchical structures for easy merging of additions, deletions, modifications and moves.&nbsp; The user may toggle between 2 distinct views: the compare view with 2 side-by-side panes, and the merge view which displays 3 panes including a merged model pane in between the left- and right-hand models.

&nbsp;

**Important note:** the approach adopted by Hackolade for its compare and merge operation is quite different from other data modeling tools. The motivation was to accommodate modern processes and tools, for example the fact that Git handles immutable versions of artifacts.&nbsp; Specifically with Hackolade, this feature does NOT apply modifications to the selected models.&nbsp; Instead it allows for the creation of a separate "merged model" in which the user is able to choose individually which differences are kept or rejected.&nbsp; It is still possible, if desired and with full understanding of the impacts, to use the merged model to write over an existing model file.

&nbsp;

Model comparison can be initiated from the Welcome page of the application without any model being previously opened in the application

![Welcome page with compare and merge models](<lib/Welcome page with compare and merge models.png>)

&nbsp;

or from the Tools \> Compare and Merge Models menu option:

![Tools - Compare and Merge Models](<lib/Tools - Compare and Merge Models.png>)

&nbsp;

&nbsp;

## Select the models

The operation is started by selecting the 2 models to be compared.&nbsp; Both files need to be valid Hackolade data models for the same target.

![Compare and merge - model selection](<lib/Compare and merge - select models.png>)

&nbsp;

Left and right models can be swapped at this stage, or later on as well.

&nbsp;

## Compare models

The comparison handles the synchronized scrolling of hierarchical structures for easy merging of additions, deletions, modifications and moves.&nbsp; All objects (containers, entities, views, relationships, definitions, attributes, etc...) and their properties in a Hackolade data model are compared, and if necessary marked as an addition, a deletion, a modification or a move.&nbsp; Separate colors and corresponding badge icons help identify the differences.&nbsp; The display can be filtered by category of differences.&nbsp; Objects are shown in the upper part of the display, whereas properties for the selected object are shown in the lower part of the display.&nbsp; By default, matching properties are filtered, but an option on the left enables their display.

&nbsp;

**Note:** the convention is to take the left model as the basis for the comparison.&nbsp; Is considered an "addition", any object present in the right model whereas it is not present in left model.&nbsp; Conversely, is considered a "deletion", any object present in the left model, whereas it is not present in the right model.&nbsp; This convention in the application is independent of the lifecycle of the models being compared.&nbsp; It can easily be reversed by swapping sides.

&nbsp;

The term "deletion", i.e. when an object is present in the left model but not in the right model, also includes cases where the left model evolved in parallel with the right model.&nbsp; In such case, the term "deletion" may be semantically debatable, as it really represents an addition versus an earlier version of the left model.&nbsp; But the application has no way to know such state.&nbsp; And convention was necessary.

&nbsp;

While field order may not be important in JSON or even enforced in some database systems, it is convenient for humans to maintain attributes in a logical order.&nbsp; Therefore, moves are tracked as differences during comparison. &nbsp;

&nbsp;

Modifications are typically differences in properties of the model objects.

&nbsp;

The user may navigate through the differences using the navigation buttons to move forward or back within the differences.&nbsp; It is possible to make models swap sides, and to reload the models if changes have been applied separately since the time they were first loaded, or open each model in a separate instance.&nbsp;

&nbsp;

&nbsp;

![Compare and merge - compare view](<lib/Compare and merge - compare view.png>)

&nbsp;

Added, deleted, and modified objects have blue, yellow, green or red colors.&nbsp; Color coding and badges help you understand additions, deletions, and modifications:&nbsp;

* pale blue for addition: an attribute is present in the right pane, but not in the left pane
* yellow for modification: an attribute appears on both sides, but has different properties on each side
* green for move: an attribute is present on both sides, but in a different position
* red for deletion: an attribute is present in the left pane, but not in the right pane

&nbsp;

If you are not sure what type of difference it is and whether it is changed in the left or right model, you can hover on the icon and read the tooltip.&nbsp;

&nbsp;

A dark blue bar across both panes indicates the selected object, triggering the display of the object's properties in the lower part of the screen.

&nbsp;

In the Display Options column on the left, the application shows only difference by default.&nbsp; If an object in a branch has a difference, all its ancestors in the tree are displayed.&nbsp; It is possible change the display options on the left, depending on what you are trying to understand.

![Compare and merge display options](<lib/Compare and merge display options.png>)

&nbsp;

Further below in the same column, the application displays the selected matching criteria.&nbsp; **Important:** Typically, models are compared using the internal Hackolade ID for the objects in the model.&nbsp; That works well if both models have evolved from the same Hackolade base data model.&nbsp; However, if you compare a reference Hackolade model with a new model derived from the reverse-engineering of a database instance for example, then this new model will have generated new internal GUID for the objects.&nbsp; As a result, matching must be made based on object names matching.&nbsp; In the absence of matching internal IDs, the application automatically falls back to matching on technical names.&nbsp; And if technical names are absent, the application falls further back to matching on business names.&nbsp; You may manually choose in the left column a different matching criteria than the automatically assigned one.

![Compare and merge matching criteria](<lib/Compare and merge matching criteria.png>)

&nbsp;

Further below in the same column, the application shows the display options, in the lower part of the screen, for the properties of the selected object.&nbsp; By default, only the differences are displayed.

![Compare and merge properties display options](<lib/Compare and merge properties display options.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

**Note:** the model compare feature assumes 2 model files saved on the file system.  Hence the process requires a prior step to reverse-engineer and save the result.  Then compare with a baseline.  Note also that when comparing, because models are of different sources which by definition will have different object IDs, it is required to compare based on object names.  This may require some preparation of the models so objects are comparable, e.g. identical container names and entity names.

&nbsp;

Optionally, you can have the application generate a delta model, which for targets that support it, can be used to create ALTER statements.

&nbsp;

## Merge models

Toggling the display brings up the 3-pane merge view.&nbsp; While the left- and right-hand models remain in their places, a middle pane proposes the result of the merge operation, and displays the colors and badge icons previously found in the compare models view.

&nbsp;

Merge proposals can be unchecked (deselected) globally per type of difference using the action buttons at the top, or individually by clicking the corresponding checkbox in the middle pane of the the upper part of the display.&nbsp; When multiple differences occur on a given object, checkboxes also appear next to the impacted properties in the lower part of the display.

&nbsp;

When differences are conflicting, the merge proposal uses the right-hand model value.

&nbsp;

**Note:** be aware that differences marked as a "deletion", i.e. an object present in the left model but not in the right model, result in the object being kept in the proposed merged model. If the object marked as "deleted" should not be retained in the merged model, the user should uncheck the corresponding checkbox. &nbsp;

&nbsp;

&nbsp;

![Image](<lib/Compare and merge - merge.png>)

&nbsp;

See Compare Models section above for an explanation of the display options, matching criteria, color coding and badges.

&nbsp;

Action buttons above the Merged model pane allow you to batch check or uncheck boxes to include objects, or not in the merged model.&nbsp; You may also manually check or uncheck individual objects.

&nbsp;

## Save the merged model

By clicking the Save button, the user has the possibility to save the merged model with only the selected merge proposals.&nbsp; This merged model can be saved as a new Hackolade data model file name (recommended if you're not using Git for versionning), or be used to write over an existing model on the file system (for example in a Git-enabled environment.)&nbsp; If using the latter method, beware of impacts of writing over an existing file.

&nbsp;

Optionally, the saved merged model can be opened in a separate instance of the application.

