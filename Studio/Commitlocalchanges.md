# Commit local changes

## Commit changes

When you make changes in a data model, or in any other file, and if you (auto-)save these changes, you see a badge popping up on the icon of the repository view in the left bar. This badge is a reminder that you still need to [commit](<Concepts1.md>) your changes in your local repository, and to [push](<Concepts1.md>) them to the remote repository.

![Workgroup reposity change badge](<lib/Workgroup reposity change badge.png>)

&nbsp;

When you open the repository view while having uncommitted changes, you see the number of modified files next to the menu entry "Commit local changes".&nbsp; That counter is colored, the intent being to remind that you need to commit your changes before pushing them. Remember that a same commit can include changes made in multiple files.

![Workgroup explore models changes](<lib/Workgroup explore models changes.png>)

&nbsp;

Click on "Commit local changes" to list actions that are related to local changes.&nbsp; The primary action - "commit" in this case - has a blue header.&nbsp; If secondary actions are available, they have a grey header if they are not destructive, and a red header otherwise.

![Workgroup commit changes](<lib/Workgroup commit changes.png>)

&nbsp;

You can show the sequence of Git commands executed by Hackolade Studio, if you are familiar with the Git command line interface and want to better understand what happens under the hood,&nbsp;

![Image](<lib/Workgroup commit git commands.png>)

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

![Workgroup commits comparison](<lib/Workgroup - History commits comparison.png>)

&nbsp;

## Unstage changes

To exclude some modified models from your commit,&nbsp; simply uncheck the checkbox "Commit all changes".&nbsp; Then use the middle controls to move model files from the "Commit now" pane to the "Commit later" pane, or back.&nbsp; You may then proceed with your Commit action.

&nbsp;

![Image](<lib/Workgroup commit partial.png>)

&nbsp;

&nbsp;

## Stash changes

Temporarily shelve your uncommitted changes for later reuse, so you can work on something else in the meantime.

&nbsp;

Imagine that you are busy working on a data model.&nbsp; You made some changes but they are not ready to be committed yet.&nbsp; For one reason or another, you now need to put your work on hold and switch to another task, potentially on a different branch of the repository.&nbsp; You don't want to discard your changes but you don't want to commit them either.&nbsp; You just want to park your changes and re-apply them later when you start working on this task again.&nbsp; That's exactly what the STASH action is meant for.&nbsp; You may stash away your uncommitted changes, then re-apply them at a later stage.

&nbsp;

![Workgroup stash changes](<lib/Workgroup stash changes.png>)

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

![Workgroup discard changes confirmation](<lib/Workgroup discard changes confirmation.png>)

&nbsp;

&nbsp;

To exclude some modified models from being discarded,&nbsp; simply uncheck the checkbox "Discard all changes".&nbsp; Then use the middle controls to move model files from the "Keep changes" pane to the "Discard changes" pane, or back.&nbsp; You may then proceed with the Discard action.

&nbsp;

![Image](<lib/Workgroup discard changes.png>)

&nbsp;

&nbsp;

## Sign commits with a digital signature

Adding a digital signature to your commit helps confirm that it genuinely came from you and not someone else impersonating you. It’s a cryptographic tool used to verify the commit’s authenticity.&nbsp; Git providers generally allow signature with SSH and GPG, sometimes with X.509 and others, with the [exception, apparently, of Azure DevOps Repos](<https://developercommunity.visualstudio.com/t/show-whether-commits-are-verified-with-gpg-key-on/383281> "target=\"\_blank\"").

In all cases, this option must be configured outside of Hackolade Studio.&nbsp; When configured properly, Hackolade Studio simply invoke commit routines that leverage whatever way the Git client has been configured.

Please follow the instructions of your Git provider:&nbsp;

\- Bitbucket: [https://support.atlassian.com/bitbucket-cloud/docs/learn-how-to-use-commits/](<https://support.atlassian.com/bitbucket-cloud/docs/learn-how-to-use-commits/> "target=\"\_blank\"")

\- GitHub: [https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits](<https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits> "target=\"\_blank\"")

\- GitLab: [https://docs.gitlab.com/user/project/repository/signed\_commits/](<https://docs.gitlab.com/user/project/repository/signed\_commits/> "target=\"\_blank\"")

&nbsp;

&nbsp;

