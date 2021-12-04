# Compare and merge models

Before using this feature, you may want to read the [versioning concept page](<Modelversioning.md>) as it is useful to understand the philosophy behind the compare and merge functionality.&nbsp;

&nbsp;

An organization may create several different versions through the lifecycle of a model.&nbsp; That may be because of the natural evolution of the application in a design-first process, or just to keep up with changes being applied to the database instance.&nbsp; In any case, it is often required to compare different versions of a model to understand the differences, and optionally to merge these differences and create a new reference model.

&nbsp;

A compare and merge operation may involve a combination of: a previous reference model, a model issued from the reverse-engineering of a database instance or some other source, a model that has evolved in a separate branch, etc...

&nbsp;

The comparison in Hackolade handles the synchronized scrolling of hierarchical structures for easy merging of additions, deletions, modifications and moves.&nbsp; The user may toggle between 2 distinct views: the compare view with 2 side-by-side panes, and the merge view which displays 3 panes including a merged model pane in between the left- and right-hand models.

&nbsp;

**Important note:** the approach adopted by Hackolade for its compare and merge operation is quite different from other data modeling tools. The motivation was to accommodate modern processes and tools, for example the fact that Git handles immutable versions of artifacts.&nbsp; Specifically with Hackolade, this feature does NOT apply modifications to the selected models.&nbsp; Instead it allows for the creation of a separate "merged model" in which the user is able to choose individually which differences are kept or rejected.&nbsp; It is still possible, if desired and with full understanding of the impacts, to use the merged model to write over an existing model file.

&nbsp;

Model comparison can be initiated from the Welcome page of the application without any model being previously opened in the application

![Welcome page with compare and merge models](<lib/Welcome%20page%20with%20compare%20and%20merge%20models.png>)

&nbsp;

or from the Tools \> Compare and Merge Models menu option:

![Tools - Compare and Merge Models](<lib/Tools%20-%20Compare%20and%20Merge%20Models.png>)

&nbsp;

&nbsp;

## Select the models

The operation is started by selecting the 2 models to be compared.&nbsp; Both files need to be valid Hackolade data models for the same target.

![Compare and merge - model selection](<lib/Compare%20and%20merge%20-%20model%20selection.png>)

&nbsp;

Left and right models can be swapped at this stage, or later on as well.

&nbsp;

## Compare models

The comparison handles the synchronized scrolling of hierarchical structures for easy merging of additions, deletions, modifications and moves.&nbsp; All objects (containers, entities, views, relationships, definitions, attributes, etc...) and their properties in a Hackolade data model are compared, and if necessary marked as an addition, a deletion, a modification or a move.&nbsp; Separate colors and corresponding badge icons help identify the differences.&nbsp; The display can be filtered by category of differences.&nbsp; Objects are shown in the upper part of the display, whereas properties for the selected object are shown in the lower part of the display.&nbsp; By default, matching properties are filtered, but a checkbox at the bottom enables their display.

&nbsp;

**Note:** the convention is to take the left model as the basis for the comparison.&nbsp; Is considered an "addition", any object present in the right model whereas it is not present in left model.&nbsp; Conversely, is considered a "deletion", any object present in the left model, whereas it is not present in the right model.&nbsp; This convention in the application is independent of the lifecycle of the models being compared.&nbsp; It can easily be reversed by swapping sides.

&nbsp;

The term "deletion", i.e. when an object is present in the left model but not in the right model, also includes cases where the left model evolved in parallel to the right model.&nbsp; In such case, the term "deletion" may be semantically inappropriate as it really represents an addition versus an earlier version of the left model.&nbsp; But hte application has no way to know such state, and convention was necessary.

&nbsp;

While field order may not be important in JSON or even enforced in database systems, it is convenient for humans to maintain attributes in a logical order.&nbsp; Therefore moves are tracked as differences during comparison. &nbsp;

&nbsp;

Modifications are typically differences in properties of the model objects.

&nbsp;

The user may navigate through the differences using the navigation buttons to move forward or back within the differences.&nbsp; It is possible to make models swap sides, and to reload the models if changes have been applied separately since the time they were first loaded. &nbsp;

&nbsp;

Typically, models are compared using the internal Hackolade ID for the objects in the model.&nbsp; That works well if both models have evolved from the same Hackolade base data model.&nbsp; However, if you compare a reference Hackolade model with a new model derived from the reverse-engineering of a database instance for example, then this new model will have generated new internal GUID for the objects.&nbsp; As a result, matching must be made based on object names matching.

&nbsp;

![Compare and merge - compare view](<lib/Compare%20and%20merge%20-%20compare%20view.png>)

&nbsp;

**Note:** the model compare feature assumes 2 model files saved on the file system.  Hence the process requires a prior step to reverse-engineer and save the result.  Then compare with a baseline.  Note also that when comparing, because models are of different sources which by definition will have different object IDs, it is required to compare based on object names.  This may require some preperation of the models so objects are comparable, e.g. identical container names and entity names.

&nbsp;

## Merge models

Toggling the display brings up the 3-pane merge view.&nbsp; While the left- and right-hand models remain in their places, a middle pane proposes the result of the merge operation, and displays the colors and badge icons previously found in the compare view.

&nbsp;

Merge proposals can be unchecked (unselected) globally per type of difference using the action buttons at the top, or individually by clicking the corresponding checkbox in the middle pane of the the upper part of the display.&nbsp; When multiple differences occur on a given object, checkboxes also appear next to the impacted properties in the lower part of the display.

&nbsp;

When differences are conflicting, the merge proposal uses the right-hand model value.

&nbsp;

**Note:** be aware that differences marked as a "deletion", i.e. an object present in the left model but not in the right model, result in the object being kept in the proposed merged model. If the object marked as "deleted" should not be retained in the merged model, the user should uncheck the corresponding checkbox. &nbsp;

&nbsp;

&nbsp;

![Compare and merge - merge view](<lib/Compare%20and%20merge%20-%20merge%20view.png>)

## Saving the merged model

By clicking the Save button, the user has the possibility to save the merged model with only the selected merge proposals.&nbsp; This merged model can be save as a new Hackolade data model file name (recommended), or be used to write over an existing model on the file system (for example in a Git-enabled environment.)&nbsp; If using the latter method, beware of impacts of writing over an existing file.

&nbsp;

Optionally, the saved merged model can be opened in a separate instance of the application.

