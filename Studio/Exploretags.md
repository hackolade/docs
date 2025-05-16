# Explore tags

A [Git tag](<https://git-scm.com/docs/git-tag> "target=\"\_blank\"") is a reference pointing to a specific commit in the Git history. [Tagging](<https://git-scm.com/book/en/v2/Git-Basics-Tagging> "target=\"\_blank\"") is used to capture a milestone in the Git history, generally to mark a version release (i.e. v1.0.1).&nbsp; The Git client makes it possible to tag a given commit with an arbitrary name. It is also possible - but not mandatory - to provide a description when tagging a commit.

&nbsp;

Hackolade Studio started to support the creation of tags within the application with v8.1.0

## Create a tag

In the Tags screen, the button to create a tag is always enabled. Clicking on it opens a bottom pane that renders the tag action parameters.

&nbsp;

![Workgroup - Create tag](<lib/Workgroup - Create tag.png>)

&nbsp;

By default a newly created tag implicitly applies the latest commit, the Head of the active branch.&nbsp; If you want to create a tag for an earlier commit, it must be done from the [history screen](<Explorehistory.md>). &nbsp;

&nbsp;

You must provide a name for the tag. It is mandatory.&nbsp; A common pattern is to use version numbers like v1.4.2. Note however that there are several restrictions to tag names.&nbsp; If possible, create tag names that don't contain special characters, as these would need to be escaped. A safe default set of characters to use for tag names is:

\- The English alphabet (a to z and A to Z)

\- Numbers (0 to 9)

\- A limited set of punctuation characters:

&nbsp; &nbsp; - period (.)

&nbsp; &nbsp; - hyphen (-)

&nbsp; &nbsp; - underscore (\_)

&nbsp; &nbsp; - forward slash (/)

To avoid confusion, you should start tag names with a letter.

When only a name is provided, the tag is said to be *lightweight*. It is just a pointer to a commit and it contains no additional metadata.

&nbsp;

Specifying a description turns the tag into an *annotated* tag. Such a tag is materialized as a Git object that contains additional metadata such as the tag author and date. Note that it is possible to force the creation of an *annotated* tag without specifying a description.

&nbsp;

You have the option to specify a description but it is optional. But best practice is to create *annotated* tags, as they embed [interesting metadata](<https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag> "target=\"\_blank\"").&nbsp;

&nbsp;

You decide whether or not to push the tag to the remote repository.&nbsp; If the local repository has a remote, then that option must be enabled by default because we believe that it is the expected behavior in most cases. Deselecting the checkbox allows the user to create personal tags.&nbsp; If the local repository has no remote, then that option must be disabled and the checkbox must be hidden.

&nbsp;

The button *Create tag* is always enabled. It starts by validating the form. It highlights the tag name with a red border if it is not filled in.

&nbsp;

&nbsp;

## List existing tags

The tags are listed in a table. &nbsp;

&nbsp;

![Workgroup - List repository tags](<lib/Workgroup - List repository tags.png>)

&nbsp;

There is a contextual menu for every tag with the following options:

\- Show in history view: redirects the user to the History view where the top filter Branch or Tag is set to the selected tag.&nbsp;

\- Review...: opens the bottom pane with the Review tab selected.

\- Checkout...: opens the bottom pane with the Checkout tab\] selected.

\- Delete...: opens the bottom pane with the Delete tab\] selected.

\- Push...: opens the bottom pane with the Push tab selected.&nbsp;

&nbsp;

You can search for a tag using the filter that is located at the top of the table. Only the tags whose name match the search pattern are listed.&nbsp;

&nbsp;

## Review tag details

It is possible to review a tag by selecting it in the table or by clicking on *Review...* in the contextual menu.

![Image](<lib/Workgroup - Review a tag.png>)

&nbsp;

&nbsp;

## Checkout a tag

Checking out a tag allows to inspect or test a specific version without worrying about ongoing changes.&nbsp; Unlike branches, tags are **read-only references.**&nbsp; This prevents accidental commits or changes when working on a specific release.

![Image](<lib/Workgroup - Checkout a tag.png>)

&nbsp;

&nbsp;

The Git client makes it possible to checkout a tag without creating a new branch. However, that command turns the local repository into *detached HEAD* state, which can be extremely misleading for the user. To avoid any kind of problems, we offer the option to checkout a tag but only as a new branch. This allows the user to use the tag as a starting point for making new changes (e.g. when working on a patch).

&nbsp;

## Push a tag

It is possible to push a tag to the remote repository (assuming that it has not been pushed at creation time) by selecting it in the table or by clicking on *Push...* in the contextual menu.

![Workgroup - Push a tag](<lib/Workgroup - Push a tag.png>)

&nbsp;

&nbsp;

The *Push* tab is hidden (as well as the corresponding entry in the contextual menu) if the local repository has no remote.

&nbsp;

## Delete a tag

It is possible to delete a tag by selecting it in the table or by clicking on *Delete...* in the contextual menu.

![Workgroup - Delete a tag](<lib/Workgroup - Delete a tag.png>)

&nbsp;

&nbsp;

By default, the tag is also deleted from the remote repository (like newly created tags that are pushed by default). However, the user can disable that option. A confirmation message is displayed before executing the action.

&nbsp;

&nbsp;

## Compare two tags

The history view makes it easy to review the a given tag.&nbsp; But it does more: since a tag is a pointer to a specific commit which itself is basically a snapshot of your entire repository at a given point in time, you may want to compare 2 tags to analyze the differences, with a user-friendly visualization.

&nbsp;

![Workgroup - Compare 2 arbitrary tags](<lib/Workgroup - Compare 2 arbitrary tags.png>)

&nbsp;

Select which tag should be used in left pane and which other tag should be used in right pane for the comparison using the icons in the table.&nbsp; Your selection is retained even if you apply different filters.&nbsp;

&nbsp;

After selecting 2 tags, you can click on the "Compare" button to open the Compare dialog:

![Visually compare commits](<lib/Compare and merge - compare view.png>)

&nbsp;

