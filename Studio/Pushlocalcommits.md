# Push local commits

Once you have [committed the changes](<Commitlocalchanges.md>) made in your local repository, you need to push your local commits to the remote repository in order to make your changes available to other people.&nbsp; Hackolade Studio makes it easy for you to push commits to a remote repository: you just need to open your own local repository (if not already opened) and navigate to "Push local commits".

![Image](<lib/Workgroup%20push1.png>)

All your local commits that you haven't pushed yet are listed with their date, author (you), and message.

&nbsp;

Git will not let you push commits if you still have remote commits to pull.&nbsp; You need to [pull the remote commits](<Pullremotecommits.md>) that you don't have yet in your local repository, prior to pushing your own commits. This is because Git will only merge changes, and potentially trigger [conflicts](<Concepts1.md>), when you pull changes.&nbsp; When you push changes, Git just replaces the existing content with your content, which does not trigger conflicts.

&nbsp;

For users new to Git, let us explain why a pull action is necessary, possibly with a merge of remote changes into the local repo, before a push action can be performed.

&nbsp;

If I am making changes in the lower green branch below, based on a model originally in the remote, Git will reject my push at the end because changes were made to the same model.&nbsp; That's because my changes would otherwise write over the changes by the other users.

![Workgroup push denied](<lib/Workgroup%20push%20denied.png>)

&nbsp;

It is the responsibility of the last user who pushes changes to do the merge first and ensure that no conflicts exist, before pushing the merged model to the remote:

![Workgroup pull before push](<lib/Workgroup%20pull%20before%20push.png>)

&nbsp;

**Best practice**: to reduce the risks of facing conflicts, we recommend that you regularly pull remote commits.&nbsp; This will ensure that your local repository is up-to-date with all the changes that have been recently pushed by other team members to the remote repository.&nbsp; If you are about to start modifying a data model, then you should definitely pull first from the remote repository.&nbsp;

&nbsp;

You will have less headaches if you pull regularly from the remote and merge with your yet-be-pushed changes, so you merge smaller increments and deal with less complexity if conflict resolution turns out to be necessary.

![Image](<lib/Workgroup%20pull%20often%20before%20push.png>)

