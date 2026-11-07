---
description: Merge Git branches and perform other repository actions from Hackolade Studio.
seoTitle: Merge Git branches in Hackolade Studio
image: lib/Workgroup merge branch screen.png
---
# Other actions

Other ad-hoc actions allow you to adjust your repository.

## Merge branches

Merging is Git's way of putting a forked history back together again. Merging allows you to combine multiple sequences of commits into one unified history. In the most frequent use cases, merging is used to combine two branches. It creates a new "merge commit" that combines the changes of each queued merge commit sequence.

![Workgroup merge branch flow](<lib/Workgroup merge branch flow.png>)

Before starting the merge process, it is a good idea to pull remote commits to ensure that both the receiving branch and the merging branch are up-to-date with the latest remote changes.

To merge branches in the Repository context, you first must make sure that the base (receiving) branch is selected as the active branch in the top bar. Then you go to the "Other actions" side menu entry, and you select the branch for which changes must be merged into the active branch.

![Workgroup merge branch screen](<lib/Workgroup merge branch screen.png>)

You may review the changes first before you click the merge button. If no conflict is detected, a merge commit will be created to be pushed to the remote repository.\
![Workgroup merge branch success](<lib/Workgroup merge branch success.png>)

If the two branches you're trying to merge both changed the same part of the same model, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually.

![Workgroup merge branch conflict](<lib/Workgroup merge branch conflict.png>)

The great part of Hackolade's merging process is that it uses the familiar side-by-side compare and merge dialog to resolve merge conflicts. When you encounter a merge conflict, clicking the Solve conflicts button shows the differences that need to be resolved.

![Workgroup merge branch solve conflict](<lib/Workgroup merge branch solve conflict.png>)

Use the checkboxes to choose for each conflict which version you prefer to keep, then click the Solve button for the operation to proceed. Note that you may have conflicts in more than one model, so make sure to review each model in the dialog.
