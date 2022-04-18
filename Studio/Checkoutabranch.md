# Checkout a branch

When you open a local repository in Hackolade Studio, you see the name of the active [branch](<Concepts1.md>) in the top bar.&nbsp; Remember that every change you make and commit affects only that branch.

![Image](<lib/Workgroup%20explore%20models3.png>)

You can perform many branch-related actions directly from Hackolade Studio:

* listing your branches
* searching for an existing branch
* checking out an existing branch (local or remote)
* creating and checking out a new branch
* deleting a branch

&nbsp;

Hackolade Studio makes all these functionalities available through the Branch drop-down in the repository bar.

&nbsp;

## List your branches

When you open the Branch drop-down, you see the list of all the branches that you have checked out at least once.&nbsp; If you just cloned a repository, then you only see one single branch, the "main" (or "master") branch.

![List your branches](<lib/Workgroup%20branch%20list1.png>)

## Search for a branch

As you type some text in the Branch drop-down, it is filtered to only list the branches whose name matches your search pattern.

&nbsp;

## Create and checkout a new branch

To create a new branch and check it out, you just type a name in the Branch drop-down, then click on the "Create new branch message" appearing in the drop-down.&nbsp; The option to create a new branch with that name appears in the drop-down itself, unless there is already an existing branch with that same name (branch names must be unique).

![Image](<lib/Workgroup%20branch%20create.png>)

## Checkout a remote branch

Besides your own branches, there are also branches that have been pushed by other users to the remote repository.&nbsp; You can checkout such a remote branch as well: you just need to start typing the name of the desired branch in the Branch drop-down.&nbsp; The drop-down offers the option to checkout any remote branch whose name matches your search pattern.

![Image](<lib/Workgroup%20branch%20checkout%20remote.png>)

## Delete a branch

If you open the Branch drop-down, you can delete any branch, except the active one.

![Image](<lib/Workgroup%20branch%20list.png>)

&nbsp;

![Workgroup confirm branch deletion](<lib/Workgroup%20confirm%20branch%20deletion.png>)

&nbsp;

Note that, by default, the branch is only deleted from your own local repository: if it has been previously pushed to the remote, it remains available in the remote repository after the local deletion, unless you enable the option "Delete remote branch".

&nbsp;

**Warning**: when you delete a branch containing commits that haven't been pushed yet, you lose these changes.&nbsp; Although this is sometimes desirable (e.g. when you want to discard your changes), you need to do this carefully\! That's why you need to confirm the deletion of the branch by typing its name.

