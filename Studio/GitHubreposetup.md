# GitHub repo setup

To enable service-to-service communication, GitHub has what it calls [GitHub apps](<https://docs.github.com/en/apps/creating-github-apps/about-creating-github-apps/about-creating-github-apps> "target=\"\_blank\""). These apps can be used to access files on repositories using the GitHub API without the need for a service account.&nbsp;

&nbsp;

The repository administrator of an organization can create a GitHub app and install it within the organization on GitHub. The app only requires read-only access permission to the content.&nbsp; When installing it, the administrator can select the repository or repositories to which this app is allowed access.

&nbsp;

The app also supports [webhooks](<https://docs.github.com/en/webhooks/about-webhooks> "target=\"\_blank\"") to provide notifications to the Model Hub instance when certain events occur on GitHub.&nbsp; In our case, these events will occur when new models, or new versions of existing models, are pushed to the main branch of each of the linked repositories. &nbsp;

&nbsp;

We use a [GitHub app manifest](<https://docs.github.com/en/apps/sharing-github-apps/registering-a-github-app-from-a-manifest#implementing-the-github-app-manifest-flow> "target=\"\_blank\"") to simplify the user experience and pre-fill the app creation form with the appropriate parameters to create the endpoint and secret.&nbsp; Once the GitHub app is created, we store in the OCI Vault: the client ID, the private key, and the webhook secret for the model sync to work.&nbsp; Since this is sensitive information, it must be treated with care, meaning no logging and no way for the user to retrieve it once it is saved.

&nbsp;

&nbsp;

## Initiate the GitHub App creation from the Model Hub

Go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select GiHub

&nbsp;

![Model Hub Admin add GitHub org](<lib/Model Hub Admin add GitHub org.png>)

&nbsp;

Enter the name of your GitHub organization and click the button Register GitHub app. &nbsp;

&nbsp;

## Allow and configure the creation of the GitHub App in your organization

Admin role is not required for this step.&nbsp; The user performing this step must have the Apps Manager role at least.

&nbsp;

You may need to authenticate with GitHub.

&nbsp;

![GitHub authentication accesss confirmation](<lib/GitHub authentication accesss confirmation.png>)

&nbsp;

&nbsp;

The process may take up to one minute or so.&nbsp; When our automatic process to generate the app is completed, the application returns this screen:

&nbsp;

![Model Hub edit GitHub configuration](<lib/Model Hub edit GitHub configuration.png>)

&nbsp;

&nbsp;

You must now click on the Install button so that the creation can take effect on GitHub:

&nbsp;

![Model Hub GitHub app creation initial screen](<lib/Model Hub GitHub app creation initial screen.png>)

&nbsp;

You must select the repository or repositories for which you want to authorize the app to provide models to the Model Hub:

&nbsp;

![Model Hub GitHub app select one or more repos](<lib/Model Hub GitHub app select one or more repos.png>)

&nbsp;

You may edit the repository list at a later time if you want to change which ones should be replicated to the Model Hub:

&nbsp;

![Model Hub GitHub app select repos](<lib/Model Hub GitHub app select repos.png>)

&nbsp;

## Create a GitHub webhook

A [GitHub webhook](<https://docs.github.com/en/webhooks/about-webhooks> "target=\"\_blank\"") is a mechanism that sends HTTP requests with event data to a specified external URL whenever specific events, such as code pushes or pull requests, occur in a repository or organization.

&nbsp;

This is how the Hackolade Model Hub gets notified of the creation of a new model or change to an existing model in any folder of the default branch for your repository, or repositories.

&nbsp;

To create a GitHub webhook, go to the Settings menu of your repository, then select Webhooks in the left menu, then click on the button Add webhook.

&nbsp;

![GitHub add webhook](<lib/GitHub add webhook.png>)

&nbsp;

Fill the form

* **Payload URL:** /gateway/sync endpoint of your HUB domain (eg: https://\<yourcompany-prod\>.hackolade.com/gateway/sync)
* **Content type:** application/json&nbsp;
* **Secret:** generate a secret using a password generator.&nbsp; Keep this password in a safe location.&nbsp;
* **SSL verification:** keep the default value
* **Which events would you like to trigger this webhook?:**&nbsp; Just the push event
* **Active**: yes

&nbsp;

Then click on Add webhook.

&nbsp;

![Model Hub GitHub webhook configuration](<lib/Model Hub GitHub webhook configuration.png>)

&nbsp;

&nbsp;

&nbsp;

The replication of models into the Model Hub database should start automatically.&nbsp; Depending on the size of your model repository (or repositories), the initial process may take some time.

&nbsp;

&nbsp;

## Troubleshooting

If after a few minutes, the Model Hub database does not show your models, go to the Repositories tab of the admin panel to view the sync status of your repository of repositories.

&nbsp;

![Model Hub admin pane repositories tab](<lib/Model Hub admin pane repositories tab.png>)

&nbsp;

If you think that your Model Hub database is not in sync with a repository, it is possible to manually start one of 3 separate actions

![Model Hub admin pane repository actions](<lib/Model Hub admin pane repository actions.png>)

&nbsp;

If you have reasons to believe that the database is not receiving models from your GitHub repository, you can view on GitHub whether the webhook is delivering as expected.

&nbsp;

There is an easy way to access the GitHub screen.&nbsp; Go to the Repositories tab of the admin panel, then click on the Edit button of the GitHub box:

![Model Hub admin pane GitHub provider](<lib/Model Hub admin pane GitHub provider.png>)

&nbsp;

then click the Advanced button. &nbsp;

&nbsp;

You may also manually access the same screen by going to GitHub \> your organization \> Developer settings \> GitHub app \> select the app created above \> go to Advanced.

&nbsp;

![Model Hub GitHub webhook status screen](<lib/Model Hub GitHub webhook status screen.png>)

&nbsp;

&nbsp;

## Configure an additional repo for replication to the Model Hub

It is possible that you might need to add one or more repositories to the existing list of repos already being replicated to the Model Hub.&nbsp; This action must take place on GitHub.

&nbsp;

Go to GitHub \> your organization \> GitHub apps \> for the app created above \> click the Configure button.&nbsp; Or from the Model Hub admin panel \> Repositories, click on the Edit button of the GitHub repository provider, then click on the Advanced button.&nbsp; In both cases, you reach a page where you can click the button Select repositories to configure your choice.

&nbsp;

![Model Hub GitHub app change repo selection](<lib/Model Hub GitHub app change repo selection.png>)

