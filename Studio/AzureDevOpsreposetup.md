# Azure DevOps repo setup

This guide details the steps to configure an external application to securely authenticate and interact with Azure DevOps using a Microsoft Entra ID app registration. This flow is intended to be used for service-to-service integrations (aka no user interaction).

&nbsp;

## Prerequisites

In Azure DevOps Repos, the user executing the steps below must have access to the settings of the project containing the models, plus Admin role to grant permissions

&nbsp;

## In the Azure Portal

In the Azure Portal, go to Microsoft Entra ID \> Manage \> [App registrations](<https://portal.azure.com/#view/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/~/RegisteredApps> "target=\"\_blank\"")

### Create a Microsoft Entra ID App Registration (Service Principal)

This section describes how to declare your application as a service principal in Entra ID.

&nbsp;

![Microsoft Entra ID-Manage-App registrations](<lib/Microsoft Entra ID-Manage-App registrations.png>)

&nbsp;

To register the application, execute the following steps:

* click on New registration
* enter a meaningful Name (e.g. Hackolade-Model-Hub-prod)
* select Accounts in this organizational directory only (single-tenant) or as required
* leave Redirect URI blank (not needed for Client Credentials Flow)
* click the Register button

&nbsp;

**Important:** save the essential **tenant ID** and **client ID**, as you will need to use them in a later phase

&nbsp;

![Azure App registration essential IDs](<lib/Azure App registration essential IDs.png>)

&nbsp;

&nbsp;

### Create an Application (client) Secret

After successfully registering your application, you must generate a Client Secret (App Secret).&nbsp; This secret acts as a password for your application when authenticating with Azure, and its value is essential for configuring the Azure connection in your Model Hub instance.

&nbsp;

In the Azure Portal still, follow the steps below:

* find and select the application you just created
* in the side menu for your registered app, select Manage \> Certificates \& secrets
* under the Client secrets tab, click the button + New client secret
* in the form, provide a clear Description (e.g., "Hackolade Model Hub integration secret") and set the Expires duration (e.g., 1 year or 2 years) as required by your security policy
* click the Add button
* immediately after the secret is created, the new secret's Value will be displayed in the table.&nbsp; This is the only time the secret value will be visible.

&nbsp;

**Important:** copy the **Value** of the new secret and save it securely.&nbsp; If you lose this value, you will need to create a new secret

&nbsp;

![Azure create app client secret](<lib/Azure create app client secret.png>)

&nbsp;

Your application secret is listed in the following screen

&nbsp;

![Azure app client secret created](<lib/Azure app client secret created.png>)

&nbsp;

&nbsp;

## In Azure DevOps

### Grant the Service Principal access to Azure DevOps Repos

**Attention:** this step does not take place in the Azure Portal.&nbsp; It must take place in the selected repository of the [Azure DevOps Repos](<https://dev.azure.com/> "target=\"\_blank\"") for your organization

&nbsp;

A service principal in Azure DevOps is an identity created for use with applications, services, and automation tools to authenticate and access Azure resources programmatically.&nbsp; It acts as a secure application identity with permissions assigned through Azure Role-Based Access Control (RBAC), enabling Azure DevOps pipelines or tools to interact with Azure resources without needing a user login.&nbsp; Essentially, it is an authorized security principal representing an application, with a client ID and client secret used for authentication in Azure DevOps workflows.

&nbsp;

To grant the service principal access to Azure DevOps, you must add it to your Azure DevOps organization/project like a traditional user.

&nbsp;

Follow the steps below:

* navigate to your Azure DevOps organization.
* go to the Organization settings option at the bottom of the left pane\
![Azure DevOps Org settings](<lib/Azure DevOps Org settings.png>)\
&nbsp;
* then choose Users and click the button&nbsp; Add users\
![Azure DevOps Org settings - add user](<lib/Azure DevOps Org settings - add user.png>)

&nbsp;

* in Users, start typing the the app's display name (from registration) and select it when it appears.&nbsp; (Avoid using the client ID directly; use the name for reliable search.)
* assign an Access level as Basic&nbsp;
* select the Project or Projects&nbsp;
* for the Project, assign Azure DevOps built-in roles such as Project Reader for read-only access.
* click the Add button\
&nbsp;

![Azure DevOps Org - add user screen](<lib/Azure DevOps Org - add user screen.png>)

&nbsp;

&nbsp;

**NOTE:** for more information on built-in roles, see [Azure DevOps permissions](<https://learn.microsoft.com/en-us/azure/devops/organizations/security/permissions?view=azure-devops\&tabs=preview-page#organization-level-permissions> "target=\"\_blank\"").

&nbsp;

Your organization users are listed in the following screen

![Azure DevOps Org settings list of users](<lib/Azure DevOps Org settings list of users.png>)

&nbsp;

### Create a webhook

An [Azure DevOps webhook](<https://learn.microsoft.com/en-us/azure/devops/service-hooks/services/webhooks?view=azure-devops> "target=\"\_blank\"") enables sending JSON payloads for repository events like code pushes, pull requests, and repository changes to external HTTPS endpoints.&nbsp; These integrate repos with services such as CI/CD tools or notification systems via service hooks.

&nbsp;

This is how the Hackolade Model Hub gets notified of the creation of a new model or change to an existing model in any folder of the default branch for your repository, or repositories.

&nbsp;

To create a Azure DevOps webhook, follow the steps below:

* navigate to your your project
* at the bottom of the left column, select Project Settings
* in the Project settings menu, click on Service hooks
* click the + sign to create a new subscription
* from the list of available services, select WebHook, then click Next\
![Azure DevOps project create webhook service](<lib/Azure DevOps project create webhook service.png>)\
&nbsp;
* configure the Triggering Event and Filters:

  * for event trigger, select Code pushed.
  * Select the repo and branch in the filters as required for your project. &nbsp; You must choose the branch that has been set up as the default branch, generally "main". &nbsp; Currently it is not possible to send webhook event to the Model Hub from any branch that then default branch.
  * Group should be \[Any\]

\
![Azure DevOps project create webhook trigger](<lib/Azure DevOps project create webhook trigger.png>)\
&nbsp;

&nbsp;

* in the Action section, configure the following:

  * URL: Enter the sync endpoint of your Hackolade Model Hub. This typically follows the format: /gateway/public/sync endpoint of your Model Hub domain (e.g., https://\<your organization\>.hackolade.com/gateway/public/sync)
  * Create Basic Auth credentials, username and password, to secure the connection.&nbsp; You must preserve this username and password in a safe place.&nbsp; They will need to be entered in the Model Hub admin screen, as described below.

&nbsp;

![Azure DevOps project create webhook action](<lib/Azure DevOps project create webhook action.png>)

&nbsp;

&nbsp;

* leave the rest of the for as is:

![Image](<lib/Azure DevOps project create webhook action 2.png>)

&nbsp;

&nbsp;

Your project webhooks are listed in the following screen

&nbsp;

![Azure DevOps project list of webhooks](<lib/Azure DevOps project list of webhooks.png>)

&nbsp;

&nbsp;

## In the Hackolade Model Hub admin panel

Once the previous steps are all completed, go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select Azure DevOps.

### Create the Azure DevOps repository provider

Webhook URL: enter the sync endpoint of your Hackolade Model Hub, and already used above. This typically follows the format: /gateway/public/sync endpoint of your Model Hub domain (e.g., https://\<your organization\>.hackolade.com/gateway/public/sync)

&nbsp;

Use the Tenant ID, Client ID, Client Secret and Basic Auth credentials saved during the execution of the previous steps to configure the Model Hub.

&nbsp;

![Model Hub admin add Azure DevOps config](<lib/Model Hub admin add Azure DevOps config.png>)

&nbsp;

&nbsp;

### Link to the repository source

Once connected to the Azure DevOps instance, you must add add the repository or repositories before syncing the models.

&nbsp;

![Model Hub admin page Git repo providers](<lib/Model Hub admin page Git repo providers.png>)

&nbsp;

Click on the Start button to reach the Add repository screen, then type the name of your oraganization in Azure DevOps:

&nbsp;

![Model Hub admin add Azure repo 1](<lib/Model Hub admin add Azure repo 1.png>)

&nbsp;

&nbsp;

The screen retrieves the visible repos by project.&nbsp; You can select one or more repositories to be replicated into the Model Hub database:

&nbsp;

![Model Hub admin add Azure repo 2](<lib/Model Hub admin add Azure repo 2.png>)

&nbsp;

It may take some time to execute the first replication, depending on the number or repositories and their size:

&nbsp;

![Model Hub admin list repositories](<lib/Model Hub admin list repositories.png>)

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

If you have reasons to believe that the database is not receiving models from your Azure DevOps repository, you can view in AzureDevops whether the webhook is delivering as expected.

&nbsp;

To access the [Azure DevOps](<https://dev.azure.com/> "target=\"\_blank\"") webhook created previously, select you project, then at the bottom of the left column, select Project Settings, then click on Service hooks.

&nbsp;

For the Model Hub web hook, click on the 3-dots to display the menu and click Edit...

&nbsp;

![Azure DevOps service webhook screen](<lib/Azure DevOps service webhook screen.png>)

&nbsp;

Then click Next to get to the Action screen, then click the Test button:

&nbsp;

![Azure DevOps service webhook test](<lib/Azure DevOps service webhook test.png>)

&nbsp;

If you do not get a successful 200 response, please provide the full response to the Hackolade helpdesk at [support@hackolade.com](<mailto:support@hackolade.com?subject=Azure%20DevOps%20webhook%20to%20Model%20Hub%20issue>)

&nbsp;

![Azure DevOps service webhook response](<lib/Azure DevOps service webhook response.png>)

&nbsp;

&nbsp;

## Configure an additional repo for replication to the Model Hub

It is possible that you might need to add one or more repositories to the existing list of repos already being replicated to the Model Hub.&nbsp; This action must take place on GitHub.

