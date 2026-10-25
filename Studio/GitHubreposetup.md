# GitHub repo setup

To enable service-to-service communication, GitHub has what it calls [GitHub apps](<https://docs.github.com/en/apps/creating-github-apps/about-creating-github-apps/about-creating-github-apps> "target=\"_blank\""). These apps can be used to access files on repositories using the GitHub API without the need for a service account.

&nbsp;

The repository administrator of an organization can create a GitHub app and install it within the organization on GitHub. The app only requires read-only access permission to the content. When installing it, the administrator can select the repository or repositories to which this app is allowed access.

&nbsp;

The app also supports [webhooks](<https://docs.github.com/en/webhooks/about-webhooks> "target=\"_blank\"") to provide notifications to the Model Hub instance when certain events occur on GitHub. In our case, these events will occur when new models, or new versions of existing models, are pushed to the main branch of each of the linked repositories.

&nbsp;

We use a [GitHub app manifest](<https://docs.github.com/en/apps/sharing-github-apps/registering-a-github-app-from-a-manifest#implementing-the-github-app-manifest-flow> "target=\"_blank\"") to simplify the user experience and pre-fill the app creation form with the appropriate parameters to create the endpoint and secret. Once the GitHub app is created, we store in the OCI Vault: the client ID, the private key, and the webhook secret for the model sync to work. Since this is sensitive information, it must be treated with care, meaning no logging and no way for the user to retrieve it once it is saved.

&nbsp;

## Initiate the GitHub App creation from the Model Hub

Go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select GiHub

&nbsp;

![Model Hub Admin add GitHub org](<lib/Model Hub Admin add GitHub org.png>)

&nbsp;

Enter the name of your GitHub organization and click the button Register GitHub app.

&nbsp;

## Allow and configure the creation of the GitHub App in your organization

Admin role is not required for this step. The user performing this step must have the Apps Manager role at least.

&nbsp;

You may need to authenticate with GitHub.

&nbsp;

![GitHub authentication accesss confirmation](<lib/GitHub authentication accesss confirmation.png>)

&nbsp;

In case configuration is to connect to a GitHub Enterprise Server instance, the hostname of that server should be provided.

&nbsp;

Enter the organization name where the GitHub App will be created, then click "Register GitHub App". This will redirect you to GitHub, where you can give this GitHub App a name, for example "Hackolade Model Hub":

&nbsp;

![Model Hub create GitHub app](<lib/Model Hub create GitHub app.png>)

&nbsp;

Once the button to create the GitHub App is clicked, the app will be created on the organization's account with the correct configuration. The configuration includes permissions to read any repository installed on the app and to create webhooks.

&nbsp;

After the creation is complete, a redirect will return the user to the admin app, where the app configuration will be saved in the OCI vault.

&nbsp;

The last step is now to install the GitHub App by clicking on the "Install" button.

&nbsp;

![Model Hub edit GitHub configuration](<lib/Model Hub edit GitHub configuration.png>)

&nbsp;

This button will return the user to GitHub, where they can install the application on the organization's account and select the repositories containing the models to be synced with Model Hub. Once this operation is complete, the selected repositories will be imported automatically, and the models will appear on the Model Hub.

&nbsp;

## Troubleshooting

If after a few minutes, the Model Hub database does not show your models, go to the Repositories tab of the admin panel to view the sync status of your repository of repositories.

&nbsp;

![Model Hub admin pane repositories tab](<lib/Model Hub admin pane repositories tab.png>)

&nbsp;

If you think that your Model Hub database is not in sync with a repository, it is possible to manually start one of 3 separate actions\
![Model Hub admin pane repository actions](<lib/Model Hub admin pane repository actions.png>)

&nbsp;

If you have reasons to believe that the database is not receiving models from your GitHub repository, you can view on GitHub whether the webhook is delivering as expected.

&nbsp;

There is an easy way to access the GitHub screen. Go to the Repositories tab of the admin panel, then click on the Edit button of the GitHub box:\
![Model Hub admin pane GitHub provider](<lib/Model Hub admin pane GitHub provider.png>)

&nbsp;

then click the Advanced button.

&nbsp;

You may also manually access the same screen by going to GitHub > your organization > Developer settings > GitHub app > select the app created above > go to Advanced.

&nbsp;

![Model Hub GitHub webhook status screen](<lib/Model Hub GitHub webhook status screen.png>)

&nbsp;

## Configure an additional repo for replication to the Model Hub

It is possible that you might need to add one or more repositories to the existing list of repos already being replicated to the Model Hub. This action must take place on GitHub.

&nbsp;

Go to GitHub > your organization > GitHub apps > for the app created above > click the Configure button. Or from the Model Hub admin panel > Repositories, click on the Edit button of the GitHub repository provider, then click on the Advanced button. In both cases, you reach a page where you can click the button Select repositories to configure your choice.

&nbsp;

![Model Hub GitHub app change repo selection](<lib/Model Hub GitHub app change repo selection.png>)
