# Review change requests

&nbsp;

The peer review feature is a very popular extension to Git that is supported by most of the repository hubs. It allows collaboration on changes made by a user so they can be reviewed and approved by another user before being merged into a target branch. This page describes how to list and review change requests.

&nbsp;

**Important:** to be able to list and review change requests, you first need to [connect to your repository hub](<Connecttoarepositoryhub.md>).

&nbsp;

**Note:**&nbsp; the naming conventions differ slightly between repository hub providers.&nbsp; GitHub, for example, uses the terminology *pull requests*, whereas GitLab uses *merge requests*.&nbsp; Both refer to the same concept.&nbsp; Hackolade Studio takes into account the specific terminology of the hub provider in the screen.&nbsp; However, in this documentation, we abstract them and refer to the more generic "change requests".

&nbsp;

Click on the left menu item "All pull requests" to see the list of change requests currently open for the active repository. The buttons at the top of the table allow to display only the open change requests (by default), only the closed ones, or all of them.&nbsp;

&nbsp;

![Image](<lib/gitbookassetsworkgroup-pr-all-open.png>)

&nbsp;

Click on the title of a change request to get the detail screen:

![Image](<lib/gitbookassetsworkgroup-pr-details%201.png>)

&nbsp;

* the **title** of the change request is typically a short description of the changes;
* a **pen icon** next to the title allows editing the details of the change request, aka its title and description;
* a **refresh icon** next to the title allows to fetch the latest updates from the repository hub, aka the recent commits and comments;&nbsp;
* the **status** of the change request is rendered below the title.
- &nbsp;
  - "Open":
    - when a change request is created;
    - when a change request is rejected with some comments to be addressed by the author, its status remains "Open" and&nbsp; does not transition to a different status.
  - "Merged": when a change request is approved and merged;
  - "Closed": when a change request is rejected and definitely closed without being merged;
* the **author** of the change request is displayed, as well as the **target branch** and the **source branch**.
* the main component of this detail page is the **timeline**. It starts by the description of the change request.&nbsp; It then renders every commit and every comment sorted by chronological order.

&nbsp;

Besides displaying a lot of information about the change request, this detail screen also offers multiple actions that are documented below.

&nbsp;

## Review submitted change requests

You can review the changes that are included in a change request by clicking on "Review changes...".

![Image](<lib/gitbookassetsworkgroup-pr-details-review.png>)

&nbsp;

Hackolade Studio shows graphically what has been modified in a data model using its [compare view](<Compareandmergemodels.md>). This helps you understand every single change, and decide whether or not it is legitimate.&nbsp; This is much friendlier than complex text diff screens used by developers.

&nbsp;

![Image](<lib/Compare%20and%20merge%20-%20compare%20view.png>)

&nbsp;

## Submit a comment

It is possible to post comments without soliciting adjustments, approving the change request, or closing it.

![Image](<lib/gitbookassetsworkgroup-pr-details-comment-1.png>)

&nbsp;

* select "Comment";
* provide a comment (mandatory);
* click on the "Submit" button.

&nbsp;

![Image](<lib/gitbookassetsworkgroup-pr-details-comment-2.png>)

&nbsp;

## Solicit an adjustment

If reviewers are not satisfied with the change request, they can solicit adjustments from the author.

![Image](<lib/gitbookassetsworkgroup-pr-details-request-ch1.png>)

&nbsp;

* select "solicit adjustment";
* provide your feedback (mandatory);
* click on the "Submit" button.

&nbsp;

This gives the author of the change request the opportunity to process the reviewer's feedback and make adjustments if necessary. The author just needs to make the adjustments solicited in the same branch, [commit](<Commitlocalchanges.md>) them, and [push](<Pushlocalcommits.md>) them. The adjustments will be automatically included in the change request and made available to the reviewer, displayed following a timeline.

![Image](<lib/gitbookassetsworkgroup-pr-details-request-cha.png>)

&nbsp;

## Approve a change request

Once the reviewer is satisfied with the full change request, including adjustments if any, the change request can be approved.

![Image](<lib/gitbookassetsworkgroup-pr-details-approve-1.png>)

&nbsp;

* select "Approve";
* provide a comment (optional);
* click on the "Submit" button.

&nbsp;

**Note:** you cannot approve your own change requests.

&nbsp;

**Important:** approving a change request does not merge it into the target branch. The merge itself is a separate action. As you can see below, the change request is still open although it has been approved. This gives the opportunity to other reviewers to also provide their feedback.

![Image](<lib/gitbookassetsworkgroup-pr-details-approve-2.png>)

&nbsp;

## Merge a change request

Once a change request has been approved, it can be merged.&nbsp; Although merging a change request is typically done by the person who reviewed it, it can be done by other users as well, including the author of the change request.

![Image](<lib/gitbookassetsworkgroup-pr-detail-merge.png>)

&nbsp;

There are 3 different merge methods available through the drop-down button.

* **Merge** creates a merge commit that joins the source branch and the target branch together.

&nbsp;

![Image](<lib/gitbookassetsgit-merge.png>)

&nbsp;

&nbsp;

* **Squash and Merge** creates one single new commit that encompasses all commits from the source branch.

&nbsp;

![Image](<lib/gitbookassetsgit-merge-squash.png>)

&nbsp;

&nbsp;

* **Rebase** rewrites the history on top of the target branch.

&nbsp;

![Image](<lib/gitbookassetsgit-merge-rebase.png>)

&nbsp;

&nbsp;

Note that a remote repository can be configured to enforce the use of one of these merge methods.

&nbsp;

&nbsp;

## Close a change request (without merging it)

If the reviewer doesn't want a change request to be merged, it can be closed.&nbsp; The changes that it contains will not be integrated into the target branch.

![Image](<lib/gitbookassetsworkgroup-pr-detail-close-1.png>)

&nbsp;

* select "Close";
* provide a comment (optional);
* click on the "Submit" button.

&nbsp;

![Image](<lib/gitbookassetsworkgroup-pr-detail-close-2.png>)

&nbsp;

## Assign yourself to a change request

Generally, reviewers do not need to assign themselves to a request in order to review it.&nbsp; But there might be a desire to be notified of any adjustment, feedback and comment made to the request, or just so to see it in the list "Assigned to me".

&nbsp;

![Image](<lib/gitbookassetsworkgroup-pr-details-assign-1.png>)

&nbsp;

You can access the list of change requests that are assigned to you from the left menu, through *Check pull requests* \> *Assigned to me*.

![Image](<lib/gitbookassetsworkgroup-pr-details-assign-2.png>)

&nbsp;

You can unassign yourself from a change request by clicking on the cross icon next to your name in the list of assignees.

