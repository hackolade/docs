# Commit local changes

## Commit changes

When you make changes in a data model, or in any other file, and if you (auto-)save these changes, you see a badge popping up on the icon of the repository view in the left bar. This badge is a reminder that you still need to [commit](<Concepts1.md>) your changes in your local repository, and to [push](<Concepts1.md>) them to the remote repository.

![Workgroup reposity change badge](<lib/Workgroup%20reposity%20change%20badge.png>)

&nbsp;

When you open the repository view while having uncommitted changes, you see the number of modified files next to the menu entry "Commit local changes".&nbsp; That counter is colored, the intent being to remind that you need to commit your changes before pushing them. Remember that a same commit can include changes made in multiple files.

![Workgroup explore models changes](<lib/Workgroup%20explore%20models%20changes.png>)

&nbsp;

Click on "Commit local changes" to list actions that are related to local changes.&nbsp; The primary action - "commit" in this case - has a blue header.&nbsp; If secondary actions are available, they have a grey header if they are not destructive, and a red header otherwise.

![Workgroup commit changes](<lib/Workgroup%20commit%20changes.png>)

&nbsp;

You can show the sequence of Git commands executed by Hackolade Studio, if you are familiar with the Git command line interface and want to better understand what happens under the hood,&nbsp;

![Image](<lib/Workgroup%20commit%20git%20commands.png>)

&nbsp;

Prior to committing your changes, you must provide a commit message.&nbsp; The best practice is to write a meaningful but concise description of what you changed and why.

&nbsp;

Some people checkout a new branch prior to making changes.&nbsp; Other people first make some changes, and then checkout a new branch prior to committing them. That's why there is also a Branch drop-down within the commit action. It behaves exactly like [the Branch drop-down in the top bar](<Checkoutabranch.md>).

&nbsp;

As soon as your changes are committed, Hackolade Studio checks if there are commits to pull from the remote repository.&nbsp; If so, the application opens [the pane to pull them](<Pullremotecommits.md>). If there are no remote commits, or once they have been pulled, Hackolade Studio opens [the pane to push your local commits](<Pushlocalcommits.md>).&nbsp; This behavior is similar to a wizard - commit \> pull \> push - but our user interface also offers the ability to trigger every action independently, and on demand.

&nbsp;

&nbsp;

## Review changes

Prior to committing your changes, you might want to review them.&nbsp; By pressing the "Review changes" button, you can display a side-by-side comparison for each modified model with its first parent.&nbsp; If you have multiple models, you may review them one at a time, using the controls at the bottom left of the dialog.

. &nbsp;

![Workgroup commits comparison](<lib/Workgroup%20-%20History%20commits%20comparison.png>)

&nbsp;

## Unstage changes

To exclude some modified models from your commit,&nbsp; simply uncheck the checkbox "Commit all changes".&nbsp; Then use the middle controls to move model files from the "Commit now" pane to the "Commit later" pane, or back.&nbsp; You may then proceed with your Commit action.

&nbsp;

![Image](<lib/Workgroup%20commit%20partial.png>)

&nbsp;

&nbsp;

## Stash changes

Temporarily shelve your uncommitted changes for later reuse, so you can work on something else in the meantime.

&nbsp;

Imagine that you are busy working on a data model.&nbsp; You made some changes but they are not ready to be committed yet.&nbsp; For one reason or another, you now need to put your work on hold and switch to another task, potentially on a different branch of the repository.&nbsp; You don't want to discard your changes but you don't want to commit them either.&nbsp; You just want to park your changes and re-apply them later when you start working on this task again.&nbsp; That's exactly what the STASH action is meant for.&nbsp; You may stash away your uncommitted changes, then re-apply them at a later stage.

&nbsp;

![Workgroup stash changes](<lib/Workgroup%20stash%20changes.png>)

&nbsp;

When stashing your changes, you should provide a description.&nbsp; Doing so will make it easier for you to find your changes, knowing that you can create multiple stashes containing different change sets.&nbsp; You also have the option to stash all your changes or to cherry-pick some files only.

&nbsp;

Like the DISCARD action, the STASH action will cancel your changes. Unlike the DISCARD action, it will save them for later reuse. You can find them back via the left menu, by clicking on "Stashes".

&nbsp;

See instructions to [apply stashed changes](<Explorestashedchanges.md>).

&nbsp;

## Discard changes

You may decide that the changes previously saved but not yet committed, should not be committed after all, and should be discarded instead.&nbsp; A warning dialog requests that you confirm the action:

&nbsp;

![Workgroup discard changes confirmation](<lib/Workgroup%20discard%20changes%20confirmation.png>)

&nbsp;

&nbsp;

To exclude some modified models from being discarded,&nbsp; simply uncheck the checkbox "Discard all changes".&nbsp; Then use the middle controls to move model files from the "Keep changes" pane to the "Discard changes" pane, or back.&nbsp; You may then proceed with the Discard action.

&nbsp;

![Image](<lib/Workgroup%20discard%20changes.png>)

&nbsp;

