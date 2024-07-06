# GitHub

The information below applies to repositories on github.com in the cloud as well as GitHub Enterprise Server.&nbsp; It explains how to grant Hackolade Studio access to your GitHub account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

## Personal access tokens

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token.&nbsp; You can find more information on how to generate a personal access token in the [GitHub documentation](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"").

&nbsp;

![Workgroup - manage hub connections](<lib/Workgroup%20-%20manage%20hub%20connections%20-%20GitHub.png>)

&nbsp;

&nbsp;

Clicking on the "generate" link brings you to the GitHub form pre-filled with most of the information needed to be provided.&nbsp; Note that, in terms of permissions / scopes, Hackolade Studio only needs "repo" (aka full control of private repositories).

![Workgroup - GitHub token scopes](<lib/Workgroup%20-%20GitHub%20token%20scopes.png>)

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

![Workgroup - GitHub token error](<lib/Workgroup-GitHub%20personal%20accesstoken%20error.png>)

&nbsp;

If you see this message, please follow the instructions above.

## OAuth

**Important:** this option is only available on github.com (Enterprise or not) where we can control the declaration of our app as a trusted source.&nbsp; OAuth for Hackolade Studio is NOT available with GitHub Server (self-hosted) as we have no such access to the instance.

&nbsp;

As an alternative to generating a personal access token, GitHub can also let you grant Hackolade Studio access to your account through [OAuth](<https://oauth.net/> "target=\"\_blank\"").&nbsp;

&nbsp;

From the menu Repository \> Manage Repository Connections, create a new connection, select the provider and specify the domain name if necessary, then select the connection method OAuth:

![GitHub OAuth connection settings](<lib/GitHub%20OAuth%20connection%20settings.png>)

&nbsp;

Then click on the "Connect" button to display the instructions:

&nbsp;

![GitHub OAuth connection instructions](<lib/GitHub%20OAuth%20connection%20instructions.png>)

&nbsp;

&nbsp;

You just need to click on "Copy code \& open browser". This will open a page in your browser where you can paste the temporary code.

![GitHub OAuth device activation code](<lib/GitHub%20OAuth%20device%20activation%20code.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

click on "Continue", then confirm by clicking the "Authorize hackolade" button.&nbsp; Note that Hackolade only requests the minimum subset of permissions for it to function properly.

&nbsp;

![GitHub OAuth device activation auth](<lib/GitHub%20OAuth%20device%20activation%20auth.png>)

&nbsp;

Hackolade Studio should now have access to GitHub.
