# Bitbucket Data Center repo setup

**Important:** the APIs used by Bitbucket Data Center and Bitbucket Cloud differ, resulting in a different setup as well.&nbsp; Consult [this page](<BitbucketCloudreposetup.md>) if your repo is in Bitbucket Cloud.

&nbsp;

Several steps must take place first on the Bitbucket Data Center side.

## Create a Bitbucket Data Center Access Token

To give the Model Hub access to fetch models from a Bitbucket Data Center repository, it is necessary to configure access using an access token. &nbsp;

&nbsp;

There is three main types of access tokens for Bitbucket Data Center (used for scripting, CI/CD, and API access), scoped to different levels of access:

* [Access tokens for a Repository](<https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/> "target=\"\_blank\""):&nbsp; allows administrators to implement fine-grained access control for specific repositories..&nbsp; This is ideal for tasks like managing one repository or providing a CI/CD tool access to a single code source.
* [Access tokens for a Project](<https://confluence.atlassian.com/bitbucketserver/using-project-permissions-776639801.html> "target=\"\_blank\""): project permissions in Bitbucket Data Center allow you to manage access to repositories within a project in an aggregated way

&nbsp;

For the Hackolade Model Hub, you need an Access Token for a Repository:&nbsp;

* navigate to the repository of your organization

![Bitbucket Data Center repo settings](<lib/Bitbucket Data Center repo settings.png>)\
\
&nbsp;

* in the side menu and select Repository settings, then choose Access tokens.
* click to Create a token.\
![Hub Bitbucket Data Ctr access tokens](<lib/Hub Bitbucket Data Ctr access tokens.png>)\
\
&nbsp;
* Assign to the token the following scopes: Repositories \> Read, and Webhooks \> Read and write\
![Hub Bitbucket Data Ctr create access token](<lib/Hub Bitbucket Data Ctr create access token.png>)\
\
&nbsp;
* Save the generated token securely. You will use this token later to configure the Git provider integration within Hub.\
\
![Hub Bitbucket Data Ctr copy access token](<lib/Hub Bitbucket Data Ctr copy access token.png>)\
\
\
&nbsp;

![Hub Bitbucket Data Ctr access token created](<lib/Hub Bitbucket Data Ctr access token created.png>)\
&nbsp;

&nbsp;

&nbsp;

&nbsp;

## Create a Bitbucket Data Center Webhook

[Webhooks in Bitbucket Data Center](<https://confluence.atlassian.com/bitbucketserver/manage-webhooks-938025878.html> "target=\"\_blank\"") provide a way to configure Bitbucket Data Center to make requests to an external service whenever certain events occur in Bitbucket Data Center. They allow automation of workflows by triggering actions in other tools or services immediately after those events happen, without the need for continuous polling.

&nbsp;

This is how the Hackolade Model Hub gets notified of the creation of a new model or change to an existing model in any folder of the default branch for your repository, or repositories.

&nbsp;

You may create one webhook per project/repo.&nbsp; But then you MUST use the same webhook "Secret token" (not be confused with the access token) for each webhook of each project.&nbsp; Or, if you have multiple repos in a group or subgroup, and they are all to be replicated with the Model Hub, then you may issue a single webhook for that group or subgroup.

&nbsp;

To create a webhook in Bitbucket Cloud so that it notifies the Model Hub when changes are pushed to the repository:

* In Repository settings, navigate to the Webhooks page from the side menu.\
![Hub Bitbucket Data Centerwebhooks](<lib/Hub Bitbucket Data Centerwebhooks.png>)\
&nbsp;
* Click Add webhook and enter the following details:

  * Title: Give the webhook a descriptive name (e.g., Hackolade Model Hub sync).
  * URL: Enter the sync endpoint of your Model Hub domain, which is typically formatted as the Hub URL followed by the specific endpoint. Example: https://\<your organization\>.hackolade.com/gateway/public/sync
  * Status: Set the status to Active.
  * Secret: create and preserve in a safe location the secret to be used to validate the webhook request
  * Authentication; leave this choice to None
  * Events: Configure the trigger to be a Repository Push event (often the default option).\
\
![Image](<lib/Hub Bitbucket Data Ctr create webhook.png>)\
\
&nbsp;

* Save the webhook configuration.

&nbsp;

![Hub Bitbucket Data Ctr webhook created](<lib/Hub Bitbucket Data Ctr webhook created.png>)\
&nbsp;

&nbsp;

## Create the Model Hub configuration

Once the previous steps are all completed, go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select Bitbucket Cloud.

&nbsp;

Webhook URL: enter the sync endpoint of your Hackolade Model Hub, and already used above. This typically follows the format: /gateway/public/sync endpoint of your Model Hub domain (e.g., https://\<your organization\>.hackolade.com/gateway/public/sync)

&nbsp;

Use the Access token and Webhook secret token saved during the execution of the previous steps to configure the Model Hub.

&nbsp;

![Model Hub Bitbuclet Data Ctr add config](<lib/Model Hub Bitbuclet Data Ctr add config.png>)\
&nbsp;

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

