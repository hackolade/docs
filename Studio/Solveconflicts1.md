# Solve conflicts

When you perform changes in a model opened directly from the remote repository, you are not using the distributed nature of Git repositories. This way of interacting with Git results in an experience that is quite different than if you leverage a [locally-cloned repository](Workingdirectlywitharemoterepo.md). In particular, if other users make changes at the same time to that same model. The reasons is that, by making your changes "online", you have no way to separate 4 usual steps of the Git process: save, commit, pull, and push. And in order to push, you must have pulled all parallel changes, which means that, in case of conflict, you must resolve them before you are able to push your own changes.

&nbsp;

Here, when working directly on a model opened from the remote repository, all these steps must somehow take place in a single action. Well, ideally when making changes to a model, you should do so in a separate branch, which allows to save, commit, and push, so that your changes have no risk of being lost. Then you can take your time to merge the branch and resolve any possible conflict. Or you can have someone review your changes prior to merging the branch.

&nbsp;

When several users make simultaneous edits on the same data model, there is a risk that some changes could cause conflicts. The first user to push changes to the remote repository has no problem. However, other user(s) may have to solve such conflicts when pulling commits from the remote repository.

&nbsp;

## When do conflicts appear in Hackolade data models?

Chances for conflicts are minimized by the structure of Hackolade data model files, whereby each property, of each attribute, of each entity, of each container is its own line in a data model file.

&nbsp;

### Merged automatically

The following cases are examples of non-conflicting changes which are therefore merged automatically:

- users add an entity or an attribute to the same model in their respective environments. The first user pushes the data model to the remote, and encounters no issue. The second users must pull from the remote first, but since there are no conflicts, merges are performed automatically, and the user has no problem pushing the latest version to the remote.\
  Maybe semantically, the intent was conflicting, for example one user created an entity called "person" while the other user created one called "party". Or one user added an attribute called "zipCode", while another user added "postalCode". But to Git and Hackolade Studio, these are separate objects, and both will be kept during an automatic merge.
- users make changes on the same objects (container, entity, attribute, view, relationship, definition, etc.) but the changes are made on different properties. For example one user changes the name of an entity, while another user adds an index to that entity. Different properties of a same object are non-conflicting changes in Hackolade data models, so these changes are merged automatically.
- users move entities in the ERD. The x-y coordinates of entities in the ERD are automatically merged, even if conflicting per se, as well as the timestamp of last modifications, and internal model cross references. These are considered model metadata that Hackolade automatically arbitrates based on the strategy chosen in Tools > Options > Repository > Default strategy for merging conflicts: either "Keep only incoming changes" (from the remote) or "Keep only local changes".

&nbsp;

> [!NOTE]
> Automatic merge can sound a bit scary. This is why we strongly recommend to leverage the standard workflow feature of Git platforms for Change Requests (called Pull Requests in GitHub and Bitbucket) and Reviews. Humans who understand the context and purpose of changes can easily review, then approve or reject changes that, while not conflicting technically, may be unnecessary or even undesirable. Hackolade Studio provides a powerful screen to support this workflow.

&nbsp;

Also useful is the ability in Hackolade Studio Workgroup to review model history, compare commits on a data model, compare branches, etc.

&nbsp;

### Requires human intervention

Here is an example of a conflicting change which requires human arbitration:

- a user makes a change locally to the name of an entity, while another user made a different change to the same name property of the exact same entity and pushed it to the remote. That's a conflict which must be resolved by a human, to choose which name must be kept. This example is illustrated below.

&nbsp;

Fortunately, conflict resolution of data models is made easy by a powerful interactive merge dialog.

&nbsp;

## Normal process

As a user, you generally don't even know that changes may have occurred elsewhere, and even less whether some of these changes might cause a conflict. No worries, this is a normal use case.

&nbsp;

When you click the save button, you get a dialog to enter a commit message. If you have the rights to do so, and you wish to bypass the (recommended) process of processing this change in a branch (new or existing), then you can save your model in the branch where it was opened from:

&nbsp;

![Save To remote repo dialog](<lib/Save To remote repo dialog.png>)

&nbsp;

In effect, this action executes all the following steps at once:

- save your changes;
- commit your local changes;
- pull remote commits;
- push your local local commit.

&nbsp;

During the (virtual) pull of remote commits, the application first evaluates where some changes have been made to the model you were editing and trying to save. You are alerted of this situation, and are given the opportunity to either review the changes side-by-side, or merge then commit you changes:

&nbsp;

![Save To remote repo change detected](<lib/Save To remote repo change detected.png>)

&nbsp;

During the evaluation, the application may detect conflicting changes. A different set of options is presented:

- keep only changes coming from the remote (which in effect discards your own changes),
- keep only local changes (which in effect discards the changes previously made on the remote),
- create a new branch for this commit (which in effect postpones dealing with the conflicts to a later time),
- or solve conflict with a side-by-side panel.

&nbsp;

![Save To remote repo conflict detected](<lib/Save To remote repo conflict detected.png>)

&nbsp;

In the merge dialog, you see you local model in the left pane, the remote model in the right pane, and the proposed merged model in the middle pane. All differences are merged. And in case of a conflict of a property of an attribute of an entity of a container, the default is to take the value of the right-hand remote side. If you disagree and wish to take the value from the left-hand local side, then you must uncheck the corresponding bow in the central pane.

&nbsp;

![Save To remote repo conflict merge dialog](<lib/Save To remote repo conflict merge dialog.png>)

&nbsp;

When you click the save button, all the selected changes are merged into your local model, so that you can now commit the change to the remote repo.
