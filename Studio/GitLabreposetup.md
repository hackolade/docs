# GitLab repo setup

## Important GitLab concepts

### Access tokens

To give the Model Hub access to fetch models from a GitLab repository, it is necessary to configure access using an access token. &nbsp;

&nbsp;

GitLab provides multiple ways to obtain an access token:

* [Service accounts](<https://docs.gitlab.com/user/profile/service\_accounts/> "target=\"\_blank\""): given that this data integration is machine-to-machine, a service account is the preferred authentication method.&nbsp; GitLab service accounts are user accounts representing non-human entities, rather than individual people, which is the case with the Model Hub.&nbsp; A service account allows to authenticate with a [personal access tokens](<https://docs.gitlab.com/user/profile/service\_accounts/#create-a-personal-access-token-for-a-service-account> "target=\"\_blank\"").&nbsp; There are 2 types of service accounts:

  * instance-wide service accounts: available to an entire GitLab instance, but must still be added to groups and projects like a human user. This is only available on GitLab Self-Managed and GitLab Dedicated.
  * group service accounts: owned by a specific top-level group and can inherit membership to subgroups and projects like a human user

* [Group access tokens](<https://docs.gitlab.com/user/group/settings/group\_access\_tokens/> "target=\"\_blank\""): Another good way to grant access to the Model Hub.&nbsp; Group access tokens grant access to all projects within a group, without being linked to a physical user
* [Personal access tokens](<https://docs.gitlab.com/user/profile/personal\_access\_tokens/> "target=\"\_blank\""): When there is no other choice, a personal access token is also a good solution, but being linked to a physical user, it means that only that user can configure the token and maintain it when it expires

&nbsp;

### Groups, subgroups, and projects

In GitLab, Groups, Subgroups, and Projects form a hierarchical structure for organizing code repositories and managing access control.&nbsp; This hierarchical model lets you organize projects logically, control access efficiently by assigning roles at group or subgroup levels, and manage large-scale developments across multiple teams or departments seamlessly.

&nbsp;

[Groups](<https://docs.gitlab.com/user/group/> "target=\"\_blank\"") serve as the top-level containers that can hold multiple related projects and subgroups. They allow you to organize projects by teams, departments, or product lines. Groups help manage permissions and resources collectively, so users added to a group gain access to all projects within it.

&nbsp;

[Subgroups](<https://docs.gitlab.com/user/group/subgroups/> "target=\"\_blank\"") are nested inside a parent group and provide an additional layer of organization. They enable finer-grained structuring by grouping related projects or teams under specific subgroups. Permissions can be managed separately at subgroup levels, allowing different access controls within the hierarchy, and subgroups can be nested up to 20 levels deep.

&nbsp;

[Projects](<https://docs.gitlab.com/user/project/organize\_work\_with\_projects/> "target=\"\_blank\"") are individual containers within groups or subgroups that hold a single Git repository along with associated features like issue tracking, wikis, and CI/CD pipelines. Each project is a distinct unit of work with its own repository and settings.

&nbsp;

### Webhooks

[Webhooks in GitLab](<https://docs.gitlab.com/user/project/integrations/webhooks/> "target=\"\_blank\"") are user-defined HTTP callbacks that send real-time notifications to external systems when specific events occur, such as code pushes or issue updates. They allow automation of workflows by triggering actions in other tools or services immediately after those events happen, without the need for continuous polling.

&nbsp;

This is how the Hackolade Model Hub gets notified of the creation of a new model or change to an existing model in any folder of the default branch for your repository, or repositories.

&nbsp;

Webhooks can be created for the different hierarchical levels within GitLab: group, subgroup, or project.&nbsp; So that you replicate to the Model Hub only the repositories that matter, it is important to create, in the steps below, webhooks(s) at the appropriate level. &nbsp;

&nbsp;

You may create one webhook per project/repo.&nbsp; But then you MUST use the same webhook "Secret token" (not be confused with the access token) for each webhook of each project.&nbsp; Or, if you have multiple repos in a group or subgroup, and they are all to be replicated with the Model Hub, then you may issue a single webhook for that group or subgroup.

&nbsp;

## Configure GitLab

Several steps must take place first on the GitLab side.

### Create a Service Account

Go to the correct “Service accounts” settings page:

* For a top-level group: navigate to the group \> Settings \> Service accounts
* For the instance (self-managed instance): in the sidebar go to Admin \> Settings \> Service accounts

&nbsp;

![Model Hub GitLab create service account](<lib/Model Hub GitLab create service account.png>)

&nbsp;

&nbsp;

### Create an access token for the service account

Click on the 3-dots for the menu, and choose Manage access tokens.

&nbsp;

Then click on the button Add new token, then fill in the form with a Token name, a Description.&nbsp; You must choose an expiration date sufficiently in the future to not have to constantly create a new token, while still remaining in compliance with your security policies.

&nbsp;

Then click the button Create token.

&nbsp;

![Model Hub GitLab create personal access token](<lib/Model Hub GitLab create personal access token.png>)

&nbsp;

&nbsp;

Make sure to copy and keep in a safe location the token value.&nbsp; This token is required in a later step.

&nbsp;

![Model Hub GitLab copy personal access token](<lib/Model Hub GitLab copy personal access token.png>)

&nbsp;

&nbsp;

### Grant access to the service account

Next, you must invite, as a member, the service account, thereby granting it access, with the reporter role.

&nbsp;

Go to Manage \> Members and click the button Invite members:

&nbsp;

![Model Hub GitLab Group Members list](<lib/Model Hub GitLab Group Members list.png>)

&nbsp;

&nbsp;

In the dialog, paste the name of the service account created above, select the role Reporter, and optionally set an expiration date, then click the invite button:

&nbsp;

![Model Hub GitLab Group Members invite](<lib/Model Hub GitLab Group Members invite.png>)

&nbsp;

You should now be able to see the binding of the service account with your repository group, where the service account auto-accepted the invitation.

&nbsp;

![Model Hub GitLab Group Members added](<lib/Model Hub GitLab Group Members added.png>)

&nbsp;

&nbsp;

## Create a GitLab webhook and webhook secret

See the discussion above, about groups, subgroups, and projects.&nbsp; And the discussion about webhooks.&nbsp; If you have only a single repository for which you need replication to the Model Hub database, then you should create the webhook at the project level.&nbsp; Even if you have multiple projects that should be replicated, but they are scattered across multiple groups or subgroups, then you may create one webhook per project, but you MUST use the same webhook secret token.&nbsp; Only of all the projects in a group or subgroup, should you create a single webhook for that group or subgroup.

&nbsp;

In the project page, go to Settings \> Webhooks \> Add new webhook

&nbsp;

![Model Hub GitLab create new webhook](<lib/Model Hub GitLab create new webhook.png>)

&nbsp;

&nbsp;

Fill in the form and provide:

* **Name:** give it a meaningful name, such as the Hackolade Model Hub environment name.
* **URL:** enter the /gateway/public/sync endpoint of your Hackolade Model Hub domain (eg: \`https://\<your company\>.hackolade.com/gateway/public/sync\`)
* **Secret token:** Use the webhook secret saved in the previous step
* **Trigger:** select Push events -\> Wildcard pattern, and enter the name of the main branch
* **SSL verification:** keep checked Enable SSL verification

&nbsp;

![Model Hub GitLab create webhook params 1](<lib/Model Hub GitLab create webhook params 1.png>)

&nbsp;

&nbsp;

To ensure that only the default branch events trigger a replication to the Model Hub, make sure to select the wildcard pattern that matches the name of the default branch:

![Model Hub GitLab create webhook trigger](<lib/Model Hub GitLab create webhook trigger.png>)

&nbsp;

&nbsp;

&nbsp;

Keep the SSL verification enabled:

![Model Hub GitLab create webhook SSL verif](<lib/Model Hub GitLab create webhook SSL verif.png>)

Then click the button Add webhook.

&nbsp;

![Model Hub GitLab webhooks list](<lib/Model Hub GitLab webhooks list.png>)

&nbsp;

&nbsp;

## Create the Model Hub configuration

Once the previous steps are all completed, go to the the Git Providers tab of the admin panel, then click on the button + setup Git Provider, and select GitLab.

&nbsp;

&nbsp;

Webhook URL: enter the sync endpoint of your Hackolade Model Hub, and already used above. This typically follows the format: /gateway/public/sync endpoint of your Model Hub domain (e.g., https://\<your organization\>.hackolade.com/gateway/public/sync)

&nbsp;

The hostname can stay empty when using the cloud version of GitLab (gitlab.com). If you have your own deployment, enter its hostname.

&nbsp;

Use the Access token and Webhook secret token saved during the execution of the previous steps to configure the Model Hub.

&nbsp;

![Model Hub GitLab add GitLab config](<lib/Model Hub GitLab add GitLab config.png>)

&nbsp;

&nbsp;

Click on the button Add webhook.

&nbsp;

## Troubleshooting

To trigger a replication of all models without waiting for the first commit, you must go back to the GitLab webhook previously created, then click on the Test button, and select Push events.

![Image](<lib/Model Hub GitLab test webhook push events.png>)

&nbsp;

To check the status of the webhook, click on the Edit button, then scroll to the Recent events section at the bottom of the screen.

&nbsp;

If a failure has occurred, it appears.&nbsp; Click the View details button and send it to [support@hackolade.com](<mailto:support@hackolade.com?subject=Model%20Hub%20GitLab%20webhook%20failed%20event>) for troubleshooting.

&nbsp;

![Model Hub GitLab webhook recent events](<lib/Model Hub GitLab webhook recent events.png>)

&nbsp;

