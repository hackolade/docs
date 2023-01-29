# Explore stashed changes

When you open a local repository and choose Explore repository \> Stashes in the left menu, you get a table listing all the uncommitted changes you might have stashed for later reuse.

&nbsp;

Each stash can be reviewed, applied back to uncommitted changes, or dropped.

![Workgroup explore stashes](<lib/Workgroup%20explore%20stashes.png>)

In the example above, the user has already stashed 2 different change sets, with their respective creation date and description. Clicking on a stash in the table opens a bottom pane that provides more details and actions.&nbsp; You can for example review the changes that are contained in the selected stash.&nbsp;

## Apply a stash

You can apply the changes in a stash.&nbsp; When doing so, you may chose between deleting the stash after apply (default), or keeping it for later reuse (e.g. on another branch).

&nbsp;

![Workgroup explore stashes without conflict](<lib/Workgroup%20explore%20stashes%20without%20conflict.png>)

## Unstash

When you don't need a stash anymore, you can drop it.

![Workgroup explore stashes and drop](<lib/Workgroup%20explore%20stashes%20and%20drop.png>)

## Resolve conflicts

When applying changes from a stash, you might face some conflicts between those changes and the content of your active branch (e.g. if you have committed some changes after creating the stash and before applying it.)&nbsp; Hackolade Studio detects this situation and offers the same [conflict resolution options](<Solveconflicts.md>) as for the other actions.

![Workgroup explore stashes solve conflicts](<lib/Workgroup%20explore%20stashes%20solve%20conflicts.png>)

Note that Hackolade Studio never deletes a stash that caused conflicts. This gives you the opportunity to re-apply the stash in case you end up not being satisfied with the results of the conflict resolution option that you chose.

