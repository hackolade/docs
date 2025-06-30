# Open model from Git repo

**Warning:** this feature is available only to Workgroup Edition license users

&nbsp;

Traditionally, you would open an existing data model located on the local drive, a shared folder, or a locally cloned repository (also on the local drive.) &nbsp; This *Open From* feature allows to open a model directly from a remote Git repository without requiring a locally-cloned repo.&nbsp; It works well with the [*Save To*](<SavemodeltoGitrepo.md>) feature which allows saving data models directly to remote Git repositories, also without the need for a locally-cloned repo

&nbsp;

To open a model, you would choose the keyboard shortcut (ctrl/cmd + O), or the menu option File \> Open, or the toolbar icon.&nbsp; And the Open dialog of you OS would open.

&nbsp;

## Open a model from a Git repository provider

With the Hackolade Studio release v7.8.0, a new option is available in the File menu to allow additional capabilities, including the possibility to open a data model directly from a Git provider, without the need for the data model to be present locally.

&nbsp;

![Open From file menu](<lib/Open From file menu.png>)

&nbsp;

Choosing this option leads to the Open From screen which takes the full workspace:

![Open From initial screen](<lib/Open From initial screen.png>)

With this Open From screen, you may drop a model file from your Windows Explorer or Mac Finder, or click the Browse files button, which gives you the same access to the OS Open dialog, as if you had gone straight to File \> Open.

&nbsp;

More importantly, this screen allows you, with the left pane, to access your Git repository provider.

&nbsp;

If you have never connected Hackolade Studio to your repo, you must perform a one-time registration of your connection, by following the instructions for the Git repo provider: [GitHub Cloud or Server](<GitHub.md>), [Azure DevOps Repos](<AzureDevOpsRepos.md>), [GitLab](<GitLab.md>), [Bitbucket Cloud](<BitbucketCloud.md>).&nbsp;

&nbsp;

![Open From create connection](<lib/Open From create connection.png>)

&nbsp;

&nbsp;

Once you have established your connection, the information gets stored, and the provider moves up in the "My sources" section, and the repositories for that source are displayed in the right-hand pane.

![Open From choose repo](<lib/Open From choose repo.png>)

Note that the APIs of some providers enforce a limit on the number of repos listed at once, and you may have to click the "Load more" button, if you have more than 100 repos.

&nbsp;

Once you choose a repo, you may navigate through the folder structure, select a branch, or go back up one level.&nbsp; Note that a breadcrumb at the top of screen allows quick navigation up the tree:

&nbsp;

![Open From navigate folders](<lib/Open From navigate folders.png>)

&nbsp;

&nbsp;

You may open your model from the selected folder.

![Open From open model](<lib/Open From open model.png>)

&nbsp;

&nbsp;

## Parameter for preferred source

You may change the behavior of the the Open buttons, keyboard shortcuts, and toolbar button to your preferred source, by changing the parameter in Tools \> Options \> General:

![Open From Tools Options parameter](<lib/Open From Tools Options parameter.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

