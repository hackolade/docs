---
description: Grant Hackolade Studio access to GitHub or GitHub Enterprise Server with a personal access token or OAuth, for reviews and pull requests.
seoTitle: Connect Hackolade Studio to GitHub
image: lib/Workgroup - manage hub connections - GitHub.png
---
# GitHub

The information below applies to repositories on github.com in the cloud as well as GitHub Enterprise Server. It explains how to grant Hackolade Studio access to your GitHub account, which is a pre-requisite for using the features "[submit for review](Submitforreview.md)" and "[review change requests](Reviewchangerequests.md)".

## Personal access tokens

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token. You can find more information on how to generate a personal access token in the [GitHub documentation](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"_blank\"").

![Workgroup - manage hub connections](<lib/Workgroup - manage hub connections - GitHub.png>)

Clicking on the "generate" link brings you to the GitHub form pre-filled with most of the information needed to be provided. Note that, in terms of permissions / scopes, Hackolade Studio only needs "repo" (aka full control of private repositories).\
![Workgroup - GitHub token scopes](<lib/Workgroup - GitHub token scopes.png>)

If you don't have sufficient rights to issue tokens, you may have to request one from your administrator.

If you need to re-issue an expired token, then:

- navigate to [your list of personal access tokens](<https://github.com/settings/tokens> "target=\"_blank\"") on GitHub;
- select the token that you are using for Hackolade and click the "Regenerate token" button;
- edit the connection in Hackolade, as described above, and copy-paste the new token from GitHub.

If you don't have a valid Personal Token, you may get the error message below, indicating that your token has passed its expiration date, or that it does not have the right scopes enabled

![Workgroup - GitHub token error](<lib/Workgroup-GitHub personal accesstoken error.png>)

If you see this message, please follow the instructions above.

## OAuth with github.com

As an alternative to generating a personal access token, GitHub can also let you grant Hackolade Studio access to your account through [OAuth](<https://oauth.net/> "target=\"_blank\"").

### From Hackolade Studio Desktop

For instructions when using Hackolade Studio **in the Browser**, the setup is different. See dedicated section further down...

From the menu Repository > Manage Repository Connections, create a new connection, select the provider and specify the domain name if necessary, then select the connection method OAuth:\
![GitHub OAuth connection settings](<lib/GitHub OAuth connection settings.png>)

Then click on the "Connect" button to display the instructions:

![GitHub OAuth connection instructions](<lib/GitHub OAuth connection instructions.png>)

You just need to click on "Copy code & open browser". This will open a page in your browser where you can paste the temporary code.\
![GitHub OAuth device activation code](<lib/GitHub OAuth device activation code.png>)

click on "Continue", then confirm by clicking the "Authorize hackolade" button. Note that Hackolade only requests the minimum subset of permissions for it to function properly.

![GitHub OAuth device activation auth](<lib/GitHub OAuth device activation auth.png>)

Hackolade Studio should now have access to GitHub.

### From Hackolade Studio in the Browser

For instructions when using Hackolade Studio **Desktop**, the setup is different. See dedicated section above...

Generally, the administrator for your organization will have set things up for you to easily connect using your Entra ID single sign-on. If that's the case, you can skip the next section for Administrators. Otherwise, please have your administrator read the information below.

In Hackolade Studio for the browser, connecting to GitHub uses OAuth with PKCE through a GitHub App, so you can sign in with your GitHub user. That sign-in proves \*who you are\*.

Separately, GitHub controls whether an integration may see private repositories in an organization through the GitHub App installation and repository access (which repositories the app is allowed to access, and for which organizations it is installed). If the GitHub App is not installed or authorized for the organization and repositories your team needs, modelers may not see or open data models stored in those repos, even after a successful OAuth sign-in.

Understanding both steps avoids confusion when “I am connected” but “I still do not see my org’s private repositories.”

The app **Authorization for Hackolade Studio** is a GitHub App which is used for organization and repository access, following GitHub’s model for granting an application access to organization resources and specific repositories. Once installed in your GitHub organization, it allows users to connect with Single Sign-On from [https://studio.hackolade.com/](<https://studio.hackolade.com/> "target=\"_blank\"")

> [!NOTE]
> The setup requires multiple steps because GitHub separates user authentication (OAuth) from organization-level approval and repository-scoped access (GitHub Apps). This approach improves security for organizations, but it can mean individual users must involve an org admin when private repositories are involved.

#### Administrators

Use the GitHub UI to install or update the Hackolade GitHub App for the organization and set repository access according to your organization's policy (for example “Only select repositories” for least privilege, or “All repositories” if policy allows). You can do this, using this direct link [https://github.com/apps/authorization-for-hackolade-studio/installations/select_target](<https://github.com/apps/authorization-for-hackolade-studio/installations/select_target> "target=\"_blank\"") then Click the Configure button for the Hackolade app.

![GitHub OAuth PKCE install Hackolade Auth app](<lib/GitHub OAuth PKCE install Hackolade Auth app.png>)

This action will get you into the screen below where you can define whether the access is granted to all the repos in the organization (probably not an adequate option) or select one or more repositories that Hackolade Studio users will be allowed to access:

![GitHub OAuth PKCE config Hackolade Auth app](<lib/GitHub OAuth PKCE config Hackolade Auth app.png>)

The screen is also reachable by organization administrators on the organization’s Installed GitHub Apps page at

```text
https://github.com/organizations/ORG_NAME/settings/installations
```

For example, for the Hackolade organization:

```text
https://github.com/organizations/hackolade/settings/installations
```

#### Users

As noted above, the GitHub app **Authorization for Hackolade Studio** is required to have been installed and configured in order for users to have access. If the app has not yet been installed, users have the opportunity to request from their administrator(s) to do so, in which case the latter will receive an email such as this one:

![GitHub OAuth PKCE Hackolade Auth app email](<lib/GitHub OAuth PKCE Hackolade Auth app email.png>)

Once the GitHub App for Authorization of Hackolade Studio has been installed and configured, go to Repository > Repository connections, and select GitHub (i.e. NOT GitHub Server, as this functionality is not possible with self-hosted GitHub Enterprise) then click the Connect button:

![GitHub OAuth PKCE connect Hackolade Auth app](<lib/GitHub OAuth PKCE connect Hackolade Auth app.png>)

You should be seeing this temporary tab:\
![GitHub OAuth PKCE Hackolade Auth app success](<lib/GitHub OAuth PKCE Hackolade Auth app success.png>)

If you see the Authentication Successful tab, you should engage your administrator to review the information in the section above.

## OAuth with GitHub Server

This section describes how to connect Hackolade Studio to **GitHub Server** using **OAuth device authorization** with a **GitHub App** registered on your instance.

Hackolade Studio desktop can connect to an organization's **GitHub Enterprise Server** using **device authorization** with a **GitHub App** registered on that instance. A user can sign in on that instance instead of having each user provide a Personal Access Token (PAT)

> [!NOTE]
> This flow is available in **Hackolade Studio desktop** only. Hackolade Studio in the browser does not provide it for GitHub Server.

### Before you connect (administrators)

On the **same GitHub instance** modelers will use (self-hosted GitHub Enterprise Server or Enterprise Cloud with a dedicated hostname):

1. **Register** a new **OAuth App** on that instance.
2. In the form, give the application a name (like Authorization for Hackolade)
3. The homepage URL and the authorization callback URL are mandatory but they can be anything; Hackolade doesn't use that information at the moment
4. Check **Enable device flow**. Hackolade Studio requires it; if device flow is off, connections will fail until you turn it on.
5. Click on "Register application"
6. Copy the app **Client ID** from the OAuth App settings page and share it with modelers.

### Connect from Hackolade Studio desktop

1. Open `Repository > Repository Connections`
2. Create a connection or edit an existing GitHub Server connection.
3. Set **Provider** to **GitHub Server**.
4. Enter **Host domain name** (hostname or URL of your instance, as your administrator specifies).
5. Set **Connect with** to **OAuth**.
6. In **OAuth Client ID**, enter the **Client ID** of your organization’s OAuth App.
7. Click **Connect**. Studio shows a one-time **user code** and a link to the device login page on your instance:
8. Copy the code and open the link
9. On your GitHub instance, paste the code, sign in, and complete SSO or authorization if prompted.
10. When authorization succeeds, Studio completes the connection.

After you are connected, use repository features (open and save models, submit for review, review change requests) with the same Git workflows as for other GitHub Server connections, within the repositories your user can access on that instance.

### If the connection fails

Verify the following:

- **Host domain name** matches the instance where the OAuth App is registered.
- The OAuth Client ID matches the OAuth App Client ID for that instance, and **device flow** is enabled for that app.
- You can sign in to the instance and access the repositories you need, including any required SSO authorization for your organization.

If Studio reports an invalid client or that device flow is disabled, ask your GitHub administrator to review the OAuth App on the instance.
