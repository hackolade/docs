# Other actions

Other ad-hoc actions allow you to adjust your repository.

&nbsp;

## Merge branches

Merging is Git's way of putting a forked history back together again.&nbsp; Merging allows you to combine multiple sequences of commits into one unified history. In the most frequent use cases, merging is used to combine two branches. It creates a new "merge commit" that combines the changes of each queued merge commit sequence.

&nbsp;

![Workgroup merge branch flow](<lib/Workgroup merge branch flow.png>)

&nbsp;

Before starting the merge process, it is a good idea to pull remote commits to ensure that both the receiving branch and the merging branch are up-to-date with the latest remote changes.

&nbsp;

To merge branches in the Repository context, you first must make sure that the base (receiving) branch is selected as the active branch in the top bar.&nbsp; Then you go to the "Other actions" side menu entry, and you select the branch for which changes must be merged into the active branch.

&nbsp;

![Workgroup merge branch screen](<lib/Workgroup merge branch screen.png>)

&nbsp;

&nbsp;

You may review the changes first before you click the merge button.&nbsp; If no conflict is detected, a merge commit will be created to be pushed to the remote repository.

![Workgroup merge branch success](<lib/Workgroup merge branch success.png>)

&nbsp;

If the two branches you're trying to merge both changed the same part of the same model, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually. &nbsp;

&nbsp;

![Workgroup merge branch conflict](<lib/Workgroup merge branch conflict.png>)

&nbsp;

&nbsp;

The great part of Hackolade's merging process is that it uses the familiar side-by-side compare and merge dialog to resolve merge conflicts. When you encounter a merge conflict, clicking the Solve conflicts button shows the differences that need to be resolved.

&nbsp;

![Workgroup merge branch solve conflict](<lib/Workgroup merge branch solve conflict.png>)

&nbsp;

Use the checkboxes to choose for each conflict which version you prefer to keep, then click the Solve button for the operation to proceed.&nbsp; Note that you may have conflicts in more than one model, so make sure to review each model in the dialog.

