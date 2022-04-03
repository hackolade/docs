# Commit local changes

When you make changes in a data model, or in any other file, and if you (auto-)save these changes, you see a badge popping up on the icon of the repository view in the left bar. This badge is a reminder that you still need to [commit](<Concepts1.md>) your changes in your local repository, and to [push](<Concepts1.md>) them to the remote repository.

![Image](<lib/Workgroup%20badge.png>)

&nbsp;

When you open the repository view while having uncommitted changes, you see the number of modified files next to the menu entry "Commit local changes".&nbsp; That counter is colored, the intent being to remind that you need to commit your changes before pushing them. Remember that a same commit can include changes made in multiple files.

![Image](<lib/Workgroup%20explore%20models%203%20chang.png>)

&nbsp;

Click on "Commit local changes" to list actions that are related to local changes.&nbsp; The primary action - "commit" in this case - has a blue header.&nbsp; If secondary actions are available, they have a grey header if they are not destructive, and a red header otherwise.

![Image](<lib/Workgroup%20commit1.png>)

Prior to committing your changes, you must provide a commit message.&nbsp; The best practice is to write a meaningful but concise description of what you changed and why.

&nbsp;

Some people checkout a new branch prior to making changes.&nbsp; Other people first make some changes, and then checkout a new branch prior to committing them. That's why there is also a Branch drop-down within the commit action. It behaves exactly like [the Branch drop-down in the top bar](<Checkoutabranch.md>).

&nbsp;

If you don't want to include all modified files in the same commit, then simply uncheck the checkbox "Commit all changes".&nbsp; This allows you to exclude files that you want to commit later.

![Image](<lib/Workgroup%20commit%20partial.png>)

You can show the sequence of Git commands executed by Hackolade Studio, if you are familiar with the Git command line interface and want to better understand what happens under the hood,&nbsp;

![Image](<lib/Workgroup%20commit%20git%20commands.png>)

As soon as your changes are committed, Hackolade Studio checks if there are commits to pull from the remote repository.&nbsp; If so, the application opens [the pane to pull them](<Pullremotecommits.md>). If there are no remote commits, or once they have been pulled, Hackolade Studio opens [the pane to push your local commits](<Pushlocalcommits.md>).&nbsp; This behavior is similar to a wizard - commit \> pull \> push - but our user interface also offers the ability to trigger every action independently, and on demand.

