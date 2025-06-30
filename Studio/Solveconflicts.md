# Solve conflicts

When several users make simultaneous edits to their local copy of the same data model, there is a risk that some changes could cause conflicts. The first user to push changes to the remote repository has no problem.&nbsp; However, other user(s) may have to solve such conflicts when pulling commits from the remote repository.

&nbsp;

## When do conflicts appear in Hackolade data models?

Chances for conflicts are minimized by the structure of Hackolade data model files, whereby each property, of each attribute, of each entity, of each container is its own line in a data model file. &nbsp;

&nbsp;

### Merged automatically

The following cases are examples of non-conflicting changes which are therefore merged automatically:

* users add an entity or an attribute to the same model in their respective environments.&nbsp; The first user pushes the data model to the remote, and encounters no issue.&nbsp; The second users must pull from the remote first, but since there are no conflicts, merges are performed automatically, and the user has no problem pushing the latest version to the remote.\
Maybe semantically, the intent was conflicting, for example one user created an entity called "person" while the other user created one called "party".&nbsp; Or one user added an attribute called "zipCode", while another user added "postalCode".&nbsp; But to Git and Hackolade Studio, these are separate objects, and both will be kept during an automatic merge. &nbsp;
* users make changes on the same objects (container, entity, attribute, view, relationship, definition, etc.) but the changes are made on different properties.&nbsp; For example one user changes the name of an entity, while another user adds an index to that entity.&nbsp; Different properties of a same object are non-conflicting changes in Hackolade data models, so these changes are merged automatically.
* users move entities in the ERD. The x-y coordinates of entities in the ERD are automatically merged, even if conflicting per se, as well as the timestamp of last modifications, and internal model cross references.&nbsp; These are considered model metadata that Hackolade automatically arbitrates based on the strategy chosen in Tools \> Options \> Repository \> Default strategy for merging conflicts: either "Keep only incoming changes" (from the remote) or "Keep only local changes".

&nbsp;

**Note:** automatic merge can sound a bit scary.&nbsp; This is why we strongly recommend to leverage the standard workflow feature of Git platforms for Change Requests (called Pull Requests in GitHub and Bitbucket) and Reviews.&nbsp; Humans who understand the context and purpose of changes can easily review, then approve or reject changes that, while not conflicting technically, may be unnecessary or even undesirable.&nbsp; Hackolade provides a powerful screen to support this workflow to [submit changes for review](<Submitforreview.md>).&nbsp;

&nbsp;

Also useful is the ability in Hackolade Studio Workgroup to review model history, compare commits on a data model, compare branches, etc.&nbsp;

### Requires human intervention

Here is an example of a conflicting change which requires human arbitration:

* a user makes a change locally to the name of an entity, while another user made a different change to the same name property of the exact same entity and pushed it to the remote.&nbsp; That's a conflict which must be resolved by a human, to choose which name must be kept.&nbsp; This example is illustrated below.

&nbsp;

Fortunately, conflict resolution of data models is made easy by a powerful interactive merge dialog.

&nbsp;

## Normal process

As a user, you generally don't even know that changes may have occurred elsewhere, and even less whether some of these changes might cause a conflict. No worries, this is a normal use case. The regular process to publish your changes is as follows:

* save your changes (in your locally-cloned repo);
* commit your local changes;
* pull remote commits, and solve conflicts, if any;
* push local commits.

&nbsp;

The last step ensures that the remote repository contains your latest changes, including resolved conflicts.

&nbsp;

For example, you have 1 data model to commit with your own changes, and 1 remote commit to pull, with the conflicting changes made by your teammate in their local copy of that same model.&nbsp; Your teammate pushed their local commit first to the remote.&nbsp;

&nbsp;

### Commit local changes

Although not strictly necessary (but always a good idea), it is mandatory in this case to commit before pulling.&nbsp; That's because Git is not able to merge remote changes into a local file that contains *uncommitted* changes.&nbsp; If you forget to commit first, a Git message will remind you. So let's [commit the changes](<Commitlocalchanges.md>).

&nbsp;

![Workgroup pull uncommitted changes](<lib/Workgroup pull uncommitted changes.png>)

&nbsp;

### Pull remote commits

After committing the changes, the next step is to pull the remote commits:

![Workgroup pull unpushed changes](<lib/Workgroup pull unpushed changes.png>)

&nbsp;

Git prevents you from pushing your local commits if you have remote commits to pull, as you are not up-to-date with the remote repository. So let's [pull the remote commits](<Pullremotecommits.md>).

![Workgroup pull conflict](<lib/Workgroup pull conflict.png>)

In this case, pulling remote commits triggers a conflict because the changes you made and committed conflict with the ones in the remote pushed by your teammate. The screen displays the files concerned.&nbsp;

&nbsp;

Hackolade Studio provides different options for solving conflicts...

&nbsp;

* **Solve conflicts:** open a merge dialog and choose interactively how to resolve each individual conflict.\
![Image](<lib/Workgroup merge dialog.png>)

&nbsp;

In the example above, there is a conflict between 2 commits that altered differently the name of a table:

* &nbsp;
  * The left-hand pane contains your local version of the data model;
  * The right-hand pane contains the remote version of the data model, as previously modified by your teammate (you may swap the RH and LH panes);
  * The center pane shows the proposed merged data model. By default, all changes are merged together. In case of conflict, the default proposal in the middle pane retains the changes in the right-hand model. You may uncheck the corresponding checkbox in the middle pane if want to retain the change from the left-hand pane instead.&nbsp; You can find more information on the [Compare \& Merge dialog](<Compareandmergemodels.md>).

&nbsp;

* **Keep only incoming changes:** you want to discard your local changes that are in conflict, and apply the incoming changes instead.
* **Keep only local changes:** you want to discard the incoming changes that are in conflict, and apply your local changes instead.
* **Undo operation:** you want to abort the operation that lead to the conflicts and go back to the state you were in prior to triggering it.&nbsp; Note that the conflicts don't go away, and will reappear when you re-trigger the pull operation again.
* **Mark conflicts as resolved:** you have resolved the conflicts outside Hackolade (e.g. using a text editor) and want to proceed.

&nbsp;

Note that, if you (re-)open a repository that has conflicts, you get a different screen but offering similar options.

![Workgroup conflict](<lib/Workgroup conflict.png>)

### &nbsp;

### Push local commits

After resolution of all conflicts, you are now able to [push your local commits](<Pushlocalcommits.md>) to the remote repository.

&nbsp;

## Special case

So far, we dealt with data model conflicts inside a repository. But what happens if you try to open a data model containing conflicts, but it was received via email for example, instead of from a pull operation in a repository context.

&nbsp;

If you try to open a data model that contains conflicts, you get the dialog below.

&nbsp;

![Workgroup open model conflict](<lib/Workgroup open model conflict.png>)

&nbsp;

The dialog offers familiar options for solving the conflicts:

* **Keep only incoming changes:** you want to discard the original changes that are in conflict, and apply the incoming changes instead;
* **Keep only local changes:** you want to discard the incoming changes that are in conflict, and apply the original changes instead.

