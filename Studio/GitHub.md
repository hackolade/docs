# GitHub

The information below applies to repositories on github.com as well as GitHub Enterprise Server.

&nbsp;

## Personal access tokens

If you don't have a valid Personal Token, you may get the error message below, indicating that your token has passed its expiration date, or that it does not have the right scopes enabled

&nbsp;

![Image](<lib/Workgroup%20-%20GitHub%20token%20error.png>)

&nbsp;

&nbsp;

&nbsp;

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token.&nbsp; You can find more information on how to generate a personal access token in the [GitHub documentation](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"").

&nbsp;

![Workgroup - manage hub connections](<lib/Workgroup%20-%20manage%20hub%20connections.png>)

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

## OAuth

TBA
