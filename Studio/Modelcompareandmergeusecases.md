# Model compare and merge use cases

No matter how convenient we can make our side-by-side compare and merge screens, the process always requires figuring out first what needs to be compared, and the desired outcome.&nbsp;

&nbsp;

There are many subtleties in this compare and merge process.&nbsp; We introduce the principles in this how-to guide, then you can apply them in the GUI, following [these instructions](<Compareandmergemodels.md>), before you attempt to optionally automate the process with the CLI.

&nbsp;

You may already know that, when performing a Compare \& Merge operation with Hackolade Studio, the operation does not modify either of the two models being compared.&nbsp; Instead, the process creates a third model -- the merged model.&nbsp; While it may sound counter-intuitive, it is a benefit of using Git technology as a repository.&nbsp; Immutable versions make it super easy to track changes, merge, branch, version, etc. &nbsp;

&nbsp;

A few reminders:

* the convention is to take the left model as the basis for the comparison.&nbsp; It is typical to place the original model in the left pane, and the evolution of that model in the right pane.&nbsp; In more advance use cases, as discussed in the sub pages, the choice of which models is kept on the right-hand side can be critical.
* separate colors and corresponding badge icons help identify the differences.  The display can be filtered by category of differences."  To see the tooltip of a badge, like everywhere else in the application, all you need is to hover your mouse pointer over the badge.

![Image](<lib/Compare and merge color coding.png>)

&nbsp; &nbsp; &nbsp; Color coding and badges help you understand additions, deletions, and modifications:&nbsp;

* &nbsp;
  * pale blue for addition: an attribute is present in the right pane, but not in the left pane
  * yellow for modification: an attribute appears on both sides, but has different properties on each side
  * green for move: an attribute is present on both sides, but in a different position
  * red for deletion: an attribute is present in the left pane, but not in the right pane

&nbsp;

* **Important:** Typically, models are compared using the internal Hackolade ID for the objects in the model.&nbsp; That works well if both models have evolved from the same Hackolade base data model.&nbsp; However, if you compare a reference Hackolade model with a new model derived from the reverse-engineering of a database instance for example, then this new model will have generated new internal GUID for the objects.&nbsp; As a result, matching must be made based on object names matching.&nbsp; In the absence of matching internal IDs, the application automatically falls back to matching on technical names.&nbsp; And if technical names are absent, the application falls further back to matching on business names.&nbsp; You may manually choose in the left column a different matching criteria than the automatically assigned one.

&nbsp;

There are many permutations possible.&nbsp; Inside this section of our online documentation, we expose some advanced use cases that should inspire users.

