# Explore history

Storing your organization's Hackolade models (and other related files) into a repository provides major benefits.&nbsp; One of them is that you can easily navigate back in time and understand all the changes made by the team.&nbsp;

&nbsp;

Not only can you see what's changed, but also who made the changes, why and when.&nbsp; You can even compare 2 arbitrary versions and visually review all their differences.&nbsp; Never be afraid of modifying files anymore: you can easily research and open previous versions, including the files that have been deleted.&nbsp; Our comprehensive history view makes it easy to explore the commits of your repository and provides powerful search and comparison features.

&nbsp;

![Workgroup - History commits list](<lib/Workgroup - History commits list.png>)

## Anatomy of the history view

The history view consists of a list pane and a details pane.

&nbsp;

The list pane displays a table with commits as well as uncommitted changes, ordered from the most recent to the oldest one. It also renders a colorful tree graph to help you visualize parallel branches.

&nbsp;

The details pane displays more information about the commit row selected in the list pane. You can either select a commit by clicking on it, or use the up and down arrow keys to navigate through the history.

&nbsp;

![Workgroup - History commit details](<lib/Workgroup - History commit details.png>)

&nbsp;

The commit message gives context about the changes.&nbsp; It is visible in the description of every row, as well as in the title of the details pane.&nbsp; It is preceded by the name of the branch(es) that currently points to that commit.

&nbsp;

You can see all files that have been added, modified, or deleted in the selected commit.&nbsp; You can open past versions of Hackolade models in read-only mode, either in the current window by clicking on their names, or in a new application instance by clicking on the corresponding icon.&nbsp; You can click on "Review changes" to open the

[Compare \& Merge dialog](<Compareandmergemodels.md>) and analyze visually all the changes that have been made in each file (compared to the previous commit on the same branch.)

&nbsp;

&nbsp;

![Workgroup - History commits comparison](<lib/Workgroup - History commits comparison.png>)

&nbsp;

## Search for a commit

Different filters help you to find specific commits you might be looking for:

* type some free text to list the commits with matching messages
* select a model - or any other file of your repository - to list the commits concerning that file
* select a branch or a tag to list the commits in its history
* select an author to list the commits having been pushed by one of your teammates

&nbsp;

And, of course, you may combine filters to refine your search.

![Workgroup - History commits models filter](<lib/Workgroup - History commits models filter.png>)

&nbsp;

## Compare commits

The history view makes it easy to review the changes made in a commit.&nbsp; But it does more: since a commit is basically a snapshot of your entire repository at a given point in time, you can also select 2 arbitrary commits and analyze the differences thanks to user-friendly visualization.

&nbsp;

Select which commit should be used in left pane and which other commit should be used in right pane for the comparison using the icons in the table.&nbsp; Your selection is retained even if you apply different filters.&nbsp;

&nbsp;

In the example below, we are comparing the state of the repository in the "contract" branch with its state in the "main" branch.

![Workgroup - History commits compare selection](<lib/Workgroup - History commits compare selection.png>)

Once you have selected 2 commits, you can click on the "Compare" button to open the Compare dialog:

![Visually compare commits](<lib/Compare and merge - compare view.png>)

&nbsp;

&nbsp;

## Other actions

All the actions related to a given entry of the history are also available through a contextual menu. You just need to click on the 3 dots to open it.

![Workgroup - History list contextual menu](<lib/Workgroup - History list contextual menu.png>)

&nbsp;

For more information about tags for a commit, you may refer to the [tag screen documentation page](<Exploretags.md>).

&nbsp;

&nbsp;

