# Bitbucket Cloud repo setup

**Important:** the APIs used by Bitbucket Data Center and Bitbucket Cloud differ, resulting in a different setup as well.&nbsp; Consult [this page](<BitbucketDataCenterreposetup.md>) if your repo is in Bitbucket Data Center.

&nbsp;

Several steps must take place first on the Bitbucket Cloud side.

## Create a Bitbucket Cloud Access Token

To give the Model Hub access to fetch models from a Bitbucket Cloud repository, it is necessary to configure access using an access token. &nbsp;

&nbsp;

There is three main types of [access tokens for Bitbucket Cloud](<https://support.atlassian.com/bitbucket-cloud/docs/access-tokens/> "target=\"\_blank\"") (used for scripting, CI/CD, and API access), scoped to different levels of access:

* [Access tokens for a Repository](<https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/> "target=\"\_blank\""): grants access to a single repository with permissions (scopes) set at creation.&nbsp; This is ideal for tasks like managing one repository or providing a CI/CD tool access to a single code source.
* [Access tokens for a Project (Premium feature)](<https://support.atlassian.com/bitbucket-cloud/docs/create-a-project-access-token/> "target=\"\_blank\""): provides access to a single project and all repositories within it.&nbsp; The permissions are defined during token creation, useful for managing or accessing multiple related repositories in one project.
* [Access tokens for a Workspace (Premium feature)](<https://support.atlassian.com/bitbucket-cloud/docs/create-a-workspace-access-token/> "target=\"\_blank\""): offers the broadest access, covering the entire workspace, including all projects and repositories.&nbsp; Permissions are specified at creation and allow for managing the entire workspace or accessing its contents.

&nbsp;

For the Hackolade Model Hub, you need an Access Token for a Repository:&nbsp;

* navigate to the repository of your organization\
![Hub Bitbucket Cloud repo settings](<lib/Hub Bitbucket Cloud repo settings.png>)\
&nbsp;
* in the side menu and select Repository settings, then choose Access tokens.
* click to Create a token.\
![Hub Bitbucket Cloud access tokens](<lib/Hub Bitbucket Cloud access tokens.png>)\
&nbsp;
* Assign to the token the following scopes: Repositories \> Read, and Webhooks \> Read and write\
![Hub Bitbucket Cloud create access token](<lib/Hub Bitbucket Cloud create access token.png>)\
&nbsp;
* Save the generated token securely. You will use this token later to configure the Git provider integration within Hub.\
\
![Hub Bitbucket Cloud copy access token](<lib/Hub Bitbucket Cloud copy access token.png>)\
&nbsp;

![Hub Bitbucket Cloud access token created](<lib/Hub Bitbucket Cloud access token created.png>)

&nbsp;

&nbsp;

&nbsp;

## Create a Bitbucket Cloud Webhook

[Webhooks in Bitbucket Cloud](<https://support.atlassian.com/bitbucket-cloud/docs/manage-webhooks/> "target=\"\_blank\"") provide a way to configure Bitbucket Cloud to make requests to an external service whenever certain events occur in Bitbucket Cloud. They allow automation of workflows by triggering actions in other tools or services immediately after those events happen, without the need for continuous polling.

&nbsp;

This is how the Hackolade Model Hub gets notified of the creation of a new model or change to an existing model in any folder of the default branch for your repository, or repositories.

&nbsp;

You may create one webhook per repo.&nbsp; But then you MUST use the same webhook "Secret token" (not be confused with the access token) for each webhook of each repository.) &nbsp;

&nbsp;

To create a webhook in Bitbucket Cloud so that it notifies the Model Hub when changes are pushed to the repository:

* In Repository settings, navigate to the Webhooks page from the side menu.\
![Hub Bitbucket Cloud webhooks](<lib/Hub Bitbucket Cloud webhooks.png>)\
&nbsp;
* Click Add webhook and enter the following details:

  * Title: Give the webhook a descriptive name (e.g., Hackolade Model Hub sync).
  * URL: Enter the sync endpoint of your Model Hub domain, which is typically formatted as the Hub URL followed by the specific endpoint. Example: https://\<your organization\>.hackolade.com/gateway/public/sync
  * Secret: create and preserve in a safe location the secret to be used to validate the webhook request
  * Status: Set the status to Active.
  * Triggers: Configure the trigger to be a Repository Push event (often the default option).\
\
![Hub Bitbucket Cloud create webhook](<lib/Hub Bitbucket Cloud create webhook.png>)\
&nbsp;

* Save the webhook configuration.

&nbsp;

![Hub Bitbucket Cloud webhook created](<lib/Hub Bitbucket Cloud webhook created.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

Webhook secret: NgeIPWQn\!YnZ9fvR

&nbsp;

&nbsp;

## Create the Model Hub configuration

Once the previous steps are all completed, go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select Bitbucket Cloud.

&nbsp;

Webhook URL: enter the sync endpoint of your Hackolade Model Hub, and already used above. This typically follows the format: /gateway/public/sync endpoint of your Model Hub domain (e.g., https://\<your organization\>.hackolade.com/gateway/public/sync)

&nbsp;

Use the Access token and Webhook secret token saved during the execution of the previous steps to configure the Model Hub.

&nbsp;

![Model Hub Bitbuclet Cloud add config](<lib/Model Hub Bitbuclet Cloud add config.png>)

&nbsp;

&nbsp;

Click on the button to Save configuration.&nbsp; Then in the Add Repository screen, type the name of your organization in your Bitbucket Cloud instance.&nbsp; Then select the repository that you want to replicate to the Model Hub database:

&nbsp;

![Model Hub Bitbuclet Cloud add repo config](<lib/Model Hub Bitbuclet Cloud add repo config.png>)

&nbsp;

&nbsp;

You may edit the configuration at a later time if desired.

&nbsp;

![Model Hub Bitbuclet Cloud edit config](<lib/Model Hub Bitbuclet Cloud edit config.png>)

&nbsp;

## Troubleshooting

To check the status of the webhook, click on the Edit button, then scroll to the Recent events section at the bottom of the screen.

&nbsp;

![Hub Bitbucket Cloud webhook event logs](<lib/Hub Bitbucket Cloud webhook event logs.png>)

&nbsp;

If a failure has occurred, it appears.&nbsp; Click the Event View details button and send it to [support@hackolade.com](<mailto:support@hackolade.com?subject=Model%20Hub%20GitLab%20webhook%20failed%20event>) for troubleshooting.

&nbsp;

