# Git subtree

A Git subtree is a way to embed a repository into another repository. As a convention, we refer to the repository being embedded as the *child repository*, and to the other repository as the *parent repository*.&nbsp; The parent repository contains a subtree that reflects the content of a child repository at a given commit.&nbsp; You can read more about Git subtrees [here](<https://www.atlassian.com/git/tutorials/git-subtree> "target=\"\_blank\"").

&nbsp;

## Setting up subtrees

Following good practices, you first need to declare each child repository as being a remote of the parent repository. You can do so by executing the command below in the parent repository. Note that executing that command has no impact on the content of the parent repository.

&nbsp;

> \# e.g. git remote add models https://github.com/org/models.git

> git remote add \<child name\> \<child URL\>

> &nbsp;

Once you have executed that command for every child repository, Hackolade Studio detects that the parent repository has multiple remotes and will provide you with additional actions.

&nbsp;

## Pulling subtrees

Hackolade Studio helps you keep your Git subtrees up-to-date in the parent repository by making it easy to pull remote commits from child repositories. If the repository you opened in Hackolade Studio has more than one remote, then the additional action "PULL subtree" will be made available in the pane "Pull remote commits".

&nbsp;

![Image](<lib/Workgroup - Git subtree.png>)

&nbsp;

Using that action, you can pull any branch from any child repository into the subfolder of your choice. Besides expecting some inputs, the action behaves exactly like the primary PULL action and is also capable of [handling conflicts](<Solveconflicts.md>).

&nbsp;

## Pushing subtrees

Hackolade Studio makes it possible to pull remote commits from the child repositories into the parent repository.&nbsp; However, it does not support modifying subtrees in the parent repository and pushing commits back to the child repositories.&nbsp; We recommend that treat a subtree as a read-only copy of a child repository and to apply your changes to the child repository directly instead of through the parent repository.
