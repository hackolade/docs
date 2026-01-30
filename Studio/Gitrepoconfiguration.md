# Git repo configuration

As per the [Model Hub architecture](<ModelHubtechnicalarchitecture.md>), the source for the Hub database is one or more Git repositories. &nbsp;

&nbsp;

Each repository provider must be configured to allow service-to-service communication, and send a notifications to the Model Hub instance when certain events occur in the repositories.&nbsp; In our case, these events occur when new models, or new versions of existing models, are pushed to the main branch of each of the linked repositories.&nbsp; Or if models gets moved or delete from the repository.

&nbsp;

**Important:** the Model Hub points to the **default** branch of each repository.&nbsp; It is currently not possible to point to a different branch than the default branch.

&nbsp;

&nbsp;

![Hackolade Model Hub empty database screen](<lib/Hackolade Model Hub empty database screen.png>)

&nbsp;

&nbsp;

You can connect your Model Hub to one or more repositories in the Model Hub admin panel from the menu in the top right corner

![Model Hub menu](<lib/Model Hub menu.png>)

&nbsp;

The Model Hub admin panel a dashboard, for example:

&nbsp;

![Model Hub admin dashboard](<lib/Model Hub admin dashboard.png>)

&nbsp;

You must first set up your repository provider by clicking the + button in the Git Providers tab:

&nbsp;

![Model Hub set up Git provider](<lib/Model Hub set up Git provider.png>)

&nbsp;

Then follow the steps in the corresponding sub page.

