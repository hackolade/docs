# Bitbucket Server

The information below applies to repositories on Bitbucket Server.&nbsp; It explains how to grant Hackolade Studio access to your Bitbucket Server account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

&nbsp;

**Note:** that access to the Bitbucket Server is not sufficient by itself.&nbsp; The user also need proper access rights the repositories, according to the [4 levels of Bitbucket Server permissions](<https://confluence.atlassian.com/bitbucketserverkb/4-levels-of-bitbucket-server-permissions-779171636.html> "target=\"\_blank\"").

&nbsp;

## Personal HTTP access tokens

**Important note:** in later releases of Bitbucket Server, it is now possible to issue Project tokens.&nbsp; We highly discourage the use of Project tokens in the context of Hackolade.  Using such tokens will create identification issues in terms of Git history and Pull request events, as Bitbucket Server automatically assigns a new internal username to users.  In fact, users will appear both with their public personnal account and also with the internal username Bitbucket is assigning to them, like if users had two identities.&nbsp; Personal HTTP tokens should be used instead.

&nbsp;

If you don't have a valid Personal Token, you may get the error message below, indicating that your token has passed its expiration date, or that it does not have the right permissions enabled.

![Workgroup - Bitbucket Cloud token error](<lib/Workgroup%20-%20Bitbucket%20Cloud%20token%20error.png>)

&nbsp;

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token. You can find more information on how to generate a personal access token in the [Bitbucket Server documentation](<https://confluence.atlassian.com/bitbucketserver0717/personal-access-tokens-1087535496.html> "target=\"\_blank\"").

&nbsp;

Depending on the version of Bitbucket Server, you may also be prompted for your username, so the application can assemble the right link in the "generate" button:

&nbsp;

![Workgroup - manage hub connections - Bitbucke](<lib/Workgroup%20-%20manage%20hub%20connections%20-%20Bitbucke.png>)

&nbsp;

.

Clicking on the "generate" link brings you to the Bitbucket Server form.&nbsp; Note that, in terms of permissions, Hackolade Studio requires at minimum the "repository write" permission in order to be able to perform Pull Requests actions.

![Workgroup - Bitbucket Server personal token](<lib/Workgroup%20-%20Bitbucket%20Server%20personal%20token.png>)

&nbsp;

If you don't have sufficient rights to issue tokens, you may have to request one from your administrator. &nbsp;

&nbsp;

To re-issue an expired token, proceed like creating a new one, then:

* navigate to your list of personal access tokens on Bitbucket Server;
* click on the Create Token button in order to create a new token;
* edit the connection in Hackolade, as described above, and copy-paste the new token from Bitbucket Server.

&nbsp;

# &nbsp;

## Username and Password

Alternatively, you may use your account username and password, but it is typically discouraged for security reasons. With a token, if an external system is compromised, you simply revoke the token instead of changing password, and consequently changing it in all scripts and integrations. It is recommended you only map one token per integration, then If the integrated system is compromised, you can remove that token and not affect any of the other integrations.

&nbsp;

In the repository connection manager, select Connect with Username and Password and enter your credentials.

![Workgroup - Bitbucket basic auth](<lib/Workgroup%20-%20Bitbucket%20basic%20auth.png>)

