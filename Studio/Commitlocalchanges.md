# Commit local changes

## Commit changes

When you make changes in a data model, or in any other file, and if you (auto-)save these changes, you see a badge popping up on the icon of the repository view in the left bar. This badge is a reminder that you still need to [commit](<Concepts1.md>) your changes in your local repository, and to [push](<Concepts1.md>) them to the remote repository.

![Image](<lib/Workgroup%20badge.png>)

&nbsp;

When you open the repository view while having uncommitted changes, you see the number of modified files next to the menu entry "Commit local changes".&nbsp; That counter is colored, the intent being to remind that you need to commit your changes before pushing them. Remember that a same commit can include changes made in multiple files.

![Image](<lib/Workgroup%20explore%20models%203%20chang.png>)

&nbsp;

Click on "Commit local changes" to list actions that are related to local changes.&nbsp; The primary action - "commit" in this case - has a blue header.&nbsp; If secondary actions are available, they have a grey header if they are not destructive, and a red header otherwise.

![Image](<lib/Workgroup%20commit1.png>)

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

![Workgroup review changes](<lib/Workgroup%20review%20changes.png>)

&nbsp;

&nbsp;

## Unstage changes

To exclude some modified models from your commit,&nbsp; simply uncheck the checkbox "Commit all changes".&nbsp; Then use the middle controls to move model files from the "Commit now" pane to the "Commit later" pane, or back.&nbsp; You may then proceed with your Commit action.

&nbsp;

![Image](<lib/Workgroup%20commit%20partial.png>)

&nbsp;

&nbsp;

## Stash changes

&nbsp;

*Coming soon*

&nbsp;

You may decide that the changes previously saved but not yet committed should not be committed yet, because you urgently need to work on something else, or you have changes conflicting with a commit you need to pull.&nbsp; You may stash away your uncommitred changes, then re-apply them at a later stage.

&nbsp;

![Workgroup stash changes](<lib/Workgroup%20stash%20changes.png>)

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

