# Pull remote commits

Hackolade Studio makes it easy to pull commits from a remote repository: you just need to open your own local repository (if not already opened) and navigate to "Pull remote commits".

![Workgroup pull remotecommits](<lib/Workgroup pull remotecommits.png>)

&nbsp;

All remote commits detected by Hackolade Studio are listed with their date, author, and message.&nbsp; You can refresh the page by clicking on the icon next to the title, if you believe that some recent commits are missing.&nbsp; Note that you can also click directly on the Pull button: all the available remote commits are pulled, including the ones that had not been detected yet.&nbsp; There is no need to systematically refresh the list prior to pulling commits.

&nbsp;

Git takes care of merging remote changes into your local repository.&nbsp; Most of the time, this happens "auto-magically"...&nbsp; However, there are 2 noticeable exceptions where a manual intervention may be required:

* Git cannot merge changes into uncommitted files.&nbsp; If someone pushed a change in a remote file when you have uncommitted changes in your local copy of that same file, then Git requests to commit your changes first, then it aborts the pull operation.&nbsp; You must [commit your changes](<Commitlocalchanges.md>) then redo the pull.
* Git cannot merge 2 versions of a same file where the same line has been modified differently.&nbsp; This is called a [conflict](<Concepts1.md>) and you need to choose which version must be kept.&nbsp; Fortunately, Hackolade Studio comes with a feature to visually [solve conflicts in data model files](<Solveconflicts.md>).

