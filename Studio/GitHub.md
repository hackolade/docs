# GitHub

The information below applies to repositories on github.com in the cloud as well as GitHub Enterprise Server.&nbsp; It explains how to grant Hackolade Studio access to your GitHub account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

## Personal access tokens

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token.&nbsp; You can find more information on how to generate a personal access token in the [GitHub documentation](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"").

&nbsp;

![Workgroup - manage hub connections](<lib/Workgroup - manage hub connections - GitHub.png>)

&nbsp;

&nbsp;

Clicking on the "generate" link brings you to the GitHub form pre-filled with most of the information needed to be provided.&nbsp; Note that, in terms of permissions / scopes, Hackolade Studio only needs "repo" (aka full control of private repositories).

![Workgroup - GitHub token scopes](<lib/Workgroup - GitHub token scopes.png>)

&nbsp;

&nbsp;

If you don't have sufficient rights to issue tokens, you may have to request one from your administrator.

&nbsp;

If you need to re-issue an expired token, then:

* navigate to [your list of personal access tokens](<https://github.com/settings/tokens> "target=\"\_blank\"") on GitHub;
* select the token that you are using for Hackolade and click the "Regenerate token" button;
* edit the connection in Hackolade, as described above, and copy-paste the new token from GitHub.

&nbsp;

If you don't have a valid Personal Token, you may get the error message below, indicating that your token has passed its expiration date, or that it does not have the right scopes enabled

&nbsp;

![Workgroup - GitHub token error](<lib/Workgroup-GitHub personal accesstoken error.png>)

&nbsp;

If you see this message, please follow the instructions above.

## OAuth

**Important:** this option is only available on github.com (Enterprise or not) where we can control the declaration of our app as a trusted source.&nbsp; OAuth for Hackolade Studio is NOT available with GitHub Server (self-hosted) as we have no such access to the instance.

&nbsp;

As an alternative to generating a personal access token, GitHub can also let you grant Hackolade Studio access to your account through [OAuth](<https://oauth.net/> "target=\"\_blank\"").&nbsp;

&nbsp;

### From Hackolade Studio Desktop

For instructions when using Hackolade Studio **in the Browser**, the setup is different.&nbsp; See dedicated section further down...

&nbsp;

From the menu Repository \> Manage Repository Connections, create a new connection, select the provider and specify the domain name if necessary, then select the connection method OAuth:

![GitHub OAuth connection settings](<lib/GitHub OAuth connection settings.png>)

&nbsp;

Then click on the "Connect" button to display the instructions:

&nbsp;

![GitHub OAuth connection instructions](<lib/GitHub OAuth connection instructions.png>)

&nbsp;

&nbsp;

You just need to click on "Copy code \& open browser". This will open a page in your browser where you can paste the temporary code.

![GitHub OAuth device activation code](<lib/GitHub OAuth device activation code.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

click on "Continue", then confirm by clicking the "Authorize hackolade" button.&nbsp; Note that Hackolade only requests the minimum subset of permissions for it to function properly.

&nbsp;

![GitHub OAuth device activation auth](<lib/GitHub OAuth device activation auth.png>)

&nbsp;

Hackolade Studio should now have access to GitHub.

&nbsp;

&nbsp;

### From Hackolade Studio in the Browser

For instructions when using Hackolade Studio **Desktop**, the setup is different.&nbsp; See dedicated section above...

&nbsp;

Generally, the administrator for your organization will have set things up for you to easily connect using your Entra ID single sign-on.&nbsp; If that's the case, you can skip the next section for Administrators.&nbsp; Otherwise, please have your administrator read the information below.

&nbsp;

In Hackolade Studio for the browser, connecting to GitHub uses OAuth with PKCE through a GitHub App, so you can sign in with your GitHub user. That sign-in proves \*who you are\*.

&nbsp;

Separately, GitHub controls whether an integration may see private repositories in an organization through the GitHub App installation and repository access (which repositories the app is allowed to access, and for which organizations it is installed).&nbsp; If the GitHub App is not installed or authorized for the organization and repositories your team needs, modelers may not see or open data models stored in those repos, even after a successful OAuth sign-in.

&nbsp;

Understanding both steps avoids confusion when “I am connected” but “I still do not see my org’s private repositories.”

&nbsp;

The app **Authorization for Hackolade Studio** is a GitHub App which is used for organization and repository access, following GitHub’s model for granting an application access to organization resources and specific repositories.&nbsp; Once installed in your GitHub organization, it allows users to connect with Single Sign-On from [https://studio.hackolade.com/](<https://studio.hackolade.com/> "target=\"\_blank\"")

&nbsp;

**Note:** the setup requires multiple steps because GitHub separates user authentication (OAuth) from organization-level approval and repository-scoped access (GitHub Apps).&nbsp; This approach improves security for organizations, but it can mean individual users must involve an org admin when private repositories are involved.

&nbsp;

#### Administrators

Use the GitHub UI to install or update the Hackolade GitHub App for the organization and set repository access according to your organization's policy (for example “Only select repositories” for least privilege, or “All repositories” if policy allows).&nbsp; You can do this, using this direct link [https://github.com/apps/authorization-for-hackolade-studio/installations/select\_target](<https://github.com/apps/authorization-for-hackolade-studio/installations/select\_target> "target=\"\_blank\"") then Click the Configure button for the Hackolade app.

&nbsp;

&nbsp;

![GitHub OAuth PKCE install Hackolade Auth app](<lib/GitHub OAuth PKCE install Hackolade Auth app.png>)

&nbsp;

&nbsp;

This action will get you into the screen below where you can define whether the access is granted to all the repos in the organization (probably not an adequate option) or select one or more repositories that Hackolade Studio users will be allowed to access:

&nbsp;

![GitHub OAuth PKCE config Hackolade Auth app](<lib/GitHub OAuth PKCE config Hackolade Auth app.png>)

&nbsp;

&nbsp;

The screen is also reachable by organization administrators on the organization’s Installed GitHub Apps page at&nbsp;

&nbsp;

> https://github.com/organizations/ORG\_NAME/settings/installations

&nbsp;

For example, for the Hackolade organization:

&nbsp;

> https://github.com/organizations/hackolade/settings/installations

&nbsp;

&nbsp;

#### Users

As noted above, the GitHub app **Authorization for Hackolade Studio** is required to have been installed and configured in order for users to have access.&nbsp; If the app has not yet been installed, users have the opportunity to request from their administrator(s) to do so, in which case the latter will receive an email such as this one:

&nbsp;

![GitHub OAuth PKCE Hackolade Auth app email](<lib/GitHub OAuth PKCE Hackolade Auth app email.png>)

&nbsp;

&nbsp;

Once the GitHub App for Authorization of Hackolade Studio has been installed and configured, go to Repository \> Repository connections, and select GitHub (i.e. NOT GitHub Server, as this functionality is not possible with self-hosted GitHub Enterprise) then click the Connect button:

&nbsp;

![GitHub OAuth PKCE connect Hackolade Auth app](<lib/GitHub OAuth PKCE connect Hackolade Auth app.png>)

&nbsp;

&nbsp;

You should be seeing this temporary tab:

![GitHub OAuth PKCE Hackolade Auth app success](<lib/GitHub OAuth PKCE Hackolade Auth app success.png>)

&nbsp;

If you see the Authentication Successful tab, you should engage your administrator to review the information in the section above.

&nbsp;

