# Push local commits

Once you have [committed the changes](<Commitlocalchanges.md>) made in your local repository, you need to push your local commits to the remote repository in order to make your changes available to other people.&nbsp; Hackolade Studio makes it easy for you to push commits to a remote repository: you just need to open your own local repository (if not already opened) and navigate to "Push local commits".

![Image](<lib/Workgroup%20push1.png>)

All your local commits that you haven't pushed yet are listed with their date, author (you), and message.

&nbsp;

Git will not let you push commits if you still have remote commits to pull.&nbsp; You need to [pull the remote commits](<Pullremotecommits.md>) that you don't have yet in your local repository, prior to pushing your own commits. This is because Git will only merge changes, and potentially trigger [conflicts](<Concepts1.md>), when you pull changes.&nbsp; When you push changes, Git just replaces the existing content with your content, which does not trigger conflicts.

