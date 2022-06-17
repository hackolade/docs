# GitHub

The information below applies to repositories on github.com as well as GitHub Enterprise Server.

&nbsp;

Click on the "generate" link that is displayed next to the input field for the personal access token.&nbsp; You will find more information on how to generate a personal access token in the [GitHub documentation](<https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token> "target=\"\_blank\"").

&nbsp;

![Workgroup - manage hub connections](<lib/Workgroup%20-%20manage%20hub%20connections.png>)

&nbsp;

Clicking on the "generate" link brings you to the GitHub form pre-filled with most of the information that need to be provided.&nbsp; Note that, in terms of permissions / scopes, Hackolade Studio only needs "repo" (aka full control of private repositories).

![Workgroup - GitHub token scopes](<lib/Workgroup%20-%20GitHub%20token%20scopes.png>)

&nbsp;

If you need to re-generate an existing token that expired, then:

* navigate to [your list of personal access tokens](<https://github.com/settings/tokens> "target=\"\_blank\"") on GitHub
* select the token that you are using for Hackolade and click on "Regenerate token"
* edit the connection in Hackolade, as described above, and copy-paste the new token from GitHub

&nbsp;

&nbsp;

If you don't have a valid Personal Token, you may get the error message below.&nbsp; It is possible that your token has passed its expiration date, or that it does not have the right scopes enabled

&nbsp;

![Image](<lib/Workgroup%20-%20GitHub%20token%20error.png>)

&nbsp;

&nbsp;

