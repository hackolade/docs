# Connect to a repository hub

A repository hub is a platform hosting repositories remotely and securely. [GitHub](<https://github.com/> "target=\"\_blank\""), [GitLab](<https://gitlab.com/> "target=\"\_blank\""), [Bitbucket](<https://bitbucket.org> "target=\"\_blank\"") and [Azure DevOps](<https://azure.microsoft.com/en-us/services/devops/#overview> "target=\"\_blank\"") are such platforms, just to name a few.

&nbsp;

Besides securing your remote repositories, such a hub provides additional features on top of the standard feature set of Git.&nbsp; For example, the peer review feature is a very popular extension to Git that is supported by most of the repository hubs. It allows changes made by a user to be reviewed and approved by another user before being merged into a target branch.

&nbsp;

Hackolade Studio is integrating with most of the popular repository hubs to bring peer review capabilities right into the application. You can [submit for review](<Submitforreview.md>) the changes made in a repository, without leaving Hackolade Studio.&nbsp; You can also list and [review change requests](<Reviewchangerequests.md>) submitted by other contributors.&nbsp; This review process is made easy by the data model visualization features of Hackolade Studio.&nbsp; Instead of presenting you with a complex text diff, Hackolade Studio shows you graphically what has been modified in a data model using its [compare view](<Compareandmergemodels.md>).&nbsp; This helps understand every single change, and decide whether or not it is legitimate.

&nbsp;

**Note:** you only need to read the information below if you use the hub workflow features to [submit for review](<Submitforreview.md>) or [review change requests](<Reviewchangerequests.md>).&nbsp; But in order to get access to the peer review features in Hackolade Studio, you need to configure how it connects to your repository hub.&nbsp;

&nbsp;

## Configuring a connection automatically

If you have already cloned a repository from your repository hub, then you just need to open your local clone in Hackolade Studio.&nbsp; It will automatically try to connect to your repository hub by reusing your existing Git credentials.

&nbsp;

If you see your username rendered in the top right corner of the repository view, then it means that Hackolade Studio could successfully connect to your repository hub.&nbsp; You can start using the peer review features right away, no more configuration is required\!

![Workgroup - hub connection automatic](<lib/Workgroup%20-%20hub%20connection%20automatic.png>)

Note that Hackolade Studio only tries to configure the connection automatically if you open a repository that you cloned over HTTPS.&nbsp; It is not possible to configure the connection automatically for a repository that you cloned over SSH.&nbsp; You have to configure the connection manually in that case (see next section).

&nbsp;

## Configuring a connection manually

If Hackolade Studio is not connected to your repository hub yet, then you see a blue link to configure the connection in the top right corner of the repository view.

![Workgroup - hub connection manual](<lib/Workgroup%20-%20hub%20connection%20manual.png>)

Alternatively, if you access the peer review features in the left menu, you get a placeholder that invites you to connect to the repository hub.

![Workgroup - hub connection placeholder](<lib/Workgroup%20-%20hub%20connection%20placeholder.png>)

&nbsp;

When you click on the connect link / button, the connection management dialog opens up.&nbsp; You may also open this dialog from the menu bar, by clicking on *Repository* \> *Manage Repository Connections*.

&nbsp;

![Workgroup - manage hub connections](<lib/Workgroup%20-%20manage%20hub%20connections.png>)

&nbsp;

To create a new connection, you must:

* select a provider from the list, knowing that the hub provider for the active repository should be selected by default, if any;
* provide the host domain name for the selected provider. It is pre-filled and read-only for standard providers running in the cloud (e.g. GitHub). It is blank and editable for providers running on your premises;
* select how you want to authenticate yourself. Using a personal access token is supported by most of the providers. See pages below for more details as each hub provider has a different process to generate such a token;
* click on "Connect" to save the setup and close the dialog.

&nbsp;

&nbsp;

## Editing a connection

You may have to edit an existing connection, for example if you opted for a connection with a personal access token and if the token that you provided has an expiration date.&nbsp; You must then provide a new token.

&nbsp;

To edit an existing connection, open the connection management dialog from the menu bar by clicking on *Repository* \> *Manage Repository Connections*.&nbsp; You can also click on the link in the top right corner of the repository view.

&nbsp;

Then select the connection that you want to edit, click on the "Edit" button, modify the necessary parameters, and save your changes by clicking on "Connect".

&nbsp;

![Image](<lib/Workgroup%20-%20manage%20hub%20connections%20-%20tokens.png>)

&nbsp;

&nbsp;

## Deleting a connection

To delete an existing connection, open the connection management dialog from the menu bar, by clicking on *Repository* \> *Manage Repository Connections*.&nbsp; You can also click on the link in the top right corner of the repository view.

&nbsp;

Then select the connection you want to delete, and click on the "Disconnect" button.

&nbsp;

## Generating personal access tokens

You can connect to most of the repository hubs by using a personal access token.&nbsp; Such a token is like a very complex password that is generated by your repository hub to connect to it in a secure manner, typically from 3rd-party applications such as Hackolade Studio.

&nbsp;

A personal access token can be revoked.&nbsp; It can have an expiration date, which forces you to update it regularly in order to increase the level of security.&nbsp; It can and should be restricted to a minimum subset of permissions (the so-called *OAuth* *scopes*).

&nbsp;

See pages below for information on how your repository hub generates tokens.

