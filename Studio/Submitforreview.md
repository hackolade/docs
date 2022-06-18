# Submit for review

The peer review feature is a very popular collaboration extension to Git, supported by most of the repository hubs.&nbsp; It allows changes made by a user to be submitted for review and approval by another user before being merged into a target branch. &nbsp;

&nbsp;

Changes to data models are proposed in a branch, to ensure that the target branch only contains finished and approved work.&nbsp; Anyone with read access to a repository is allowed to submit changes for review.

&nbsp;

**Important:** to be able to submit changes for review, you first need to [connect to your repository hub](<Connecttoarepositoryhub.md>).

&nbsp;

**Note:**&nbsp; the naming conventions differ slightly between repository hub providers.&nbsp; GitHub, for example, uses the terminology *pull requests*, whereas GitLab uses *merge requests*.&nbsp; Both refer to the same concept.&nbsp; Hackolade Studio takes into account the specific terminology of the hub provider.&nbsp; However, in this documentation, we abstract them and refer to the more generic "change requests".\
&nbsp;

&nbsp;

A typical change process is to first [checkout a new branch](<Checkoutabranch.md>). then make the necessary changes, [commit](<Commitlocalchanges.md>) them, and [push](<Pushlocalcommits.md>) them.&nbsp; This makes your new branch available in the remote repository.&nbsp; Multiple changes can be made to a branch, and the change request applies to all the changes in that branch.&nbsp; If you want to split changes in different requests, you should create a separate branch for each group of changes.

&nbsp;

A branch is meant to be temporary: it should be reviewed, typically by another user, merged into a long-living branch, and ultimately deleted.&nbsp; In order to initiate the review process, you need to submit your changes for review.&nbsp; You can do it directly from Hackolade Studio.

&nbsp;

&nbsp;

## Submit a change request

In the repository context, select as the active branch, the branch for which you want to submit a change request, then click on the left menu item "Submit for review" to get the screen below:

![Workgroup submit for review](<lib/Workgroup%20submit%20for%20review.png>)

* provide a **title**, a short description of the changes made;
* optionally provide a more detailed **description** of the changes.&nbsp; You can write that description using the [Markdown syntax](<https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax>);&nbsp;
* select the **target** **branch** into which the changes must be merged.

&nbsp;

&nbsp;

![Workgroup submit for review markdown](<lib/Workgroup%20submit%20for%20review%20markdown.png>)

Hackolade lists all the commits to be included in the review.&nbsp; You can self-review the changes in these commits before submitting them using the "Review changes..." button. It opens up the [compare dialog](<Compareandmergemodels.md>) and provides a graphical visualization of the changes.

&nbsp;

You can then click on the "Open pull request" button to submit your changes.

&nbsp;

Once your change request is opened, you get the screen below, displaying a link to open the change request in a browser if necessary.

&nbsp;

![Workgroup submit for review - submitted](<lib/Workgroup%20submit%20for%20review%20-%20submitted.png>)

&nbsp;

## Display change requests you submitted

In the left menu, the counter of change requests "open by me" reflects the number of open change requests. Clicking on it displays the list of change requests you authored.

![Workgroup submit for review - open by me](<lib/Workgroup%20submit%20for%20review%20-%20open%20by%20me.png>)

&nbsp;

You can click on the title of a change request to display a detail screen and check if you received feedback from reviewers. The change request detail screen is documented in the [next page](<Reviewchangerequests.md>).

&nbsp;

**Note:** it is not allowed to create more than one change request for a same combination of source branch and target branch.&nbsp; However, nothing prevents you from making further changes while your change request is opened, and maybe being reviewed already.&nbsp; You just need to [commit](<Commitlocalchanges.md>) and [push](<Pushlocalcommits.md>) your changes: and they will be automatically included in your change request and made available to the reviewer(s).

&nbsp;

