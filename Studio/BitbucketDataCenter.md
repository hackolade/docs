# Bitbucket Data Center

**Note:** Bitbucket Server reached End-of-Support on&nbsp; February 15, 2024 and has been replaced by Bitbucket Data Center.

&nbsp;

The information below applies to repositories on Bitbucket Data Center.&nbsp; It explains how to grant Hackolade Studio access to your Bitbucket Data Center account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

&nbsp;

**Note:** that access to the Bitbucket Data Center is not sufficient by itself.&nbsp; The user also need proper access rights the repositories, according to the [4 levels of Bitbucket Data Center permissions](<https://confluence.atlassian.com/bitbucketserverkb/4-levels-of-bitbucket-server-permissions-779171636.html> "target=\"\_blank\"").

&nbsp;

## Personal HTTP access tokens

**Important note:** in later releases of Bitbucket Data Center, it is now possible to issue Project tokens.&nbsp; We discourage the use of Project tokens in the context of Hackolade Studio.&nbsp; With Project tokens, Bitbucket Data Center automatically assigns a new internal username to users, resulting in identification issues in terms of Git history and Pull Requests, as well as other anomalies.&nbsp; Personal HTTP tokens should be used instead.

&nbsp;

In the repository connection manager, click on the "generate" link located to the right of the input field for the personal access token. You can find more information on how to generate a personal access token in the [Bitbucket Data Center documentation](<https://confluence.atlassian.com/bitbucketserver0717/personal-access-tokens-1087535496.html> "target=\"\_blank\"").

&nbsp;

Depending on the version of Bitbucket Data Center, you may also be prompted for your username, so the application can assemble the right link in the "generate" button:

&nbsp;

![Workgroup - manage hub connections - Bitbucke](<lib/Workgroup - manage hub connections - Bitbucke.png>)

&nbsp;

.

Clicking on the "generate" link brings you to the Bitbucket Data Center form.&nbsp; Note that, in terms of permissions, Hackolade Studio requires at minimum the "repository write" permission in order to be able to perform Pull Requests actions.

![Workgroup - Bitbucket Server personal token](<lib/Workgroup - Bitbucket Server personal token.png>)

&nbsp;

If you don't have sufficient rights to issue tokens, you may have to request one from your administrator. &nbsp;

&nbsp;

To re-issue an expired token, proceed like creating a new one, then:

* navigate to your list of personal access tokens on Bitbucket Data Center;
* click on the Create Token button in order to create a new token;
* edit the connection in Hackolade, as described above, and copy-paste the new token from Bitbucket Data Center.

&nbsp;

If you don't have a valid Personal Token, you may get the error message below, indicating that your token has passed its expiration date, or that it does not have the right permissions enabled.

![Workgroup - Bitbucket Cloud token error](<lib/Workgroup - Bitbucket Cloud token error.png>)

&nbsp;

If you see this message, please follow the instructions above.

&nbsp;

## Username and Password

Alternatively, you may use your account username and password, but it is typically discouraged for security reasons. With a token, if an external system is compromised, you simply revoke the token instead of changing password, and consequently changing it in all scripts and integrations. It is recommended you only map one token per integration, then If the integrated system is compromised, you can remove that token and not affect any of the other integrations.

&nbsp;

In the repository connection manager, select Connect with Username and Password and enter your credentials.

![Workgroup - Bitbucket basic auth](<lib/Workgroup - Bitbucket basic auth.png>)

&nbsp;

## Troubleshooting

Here is a quick summary of the connectivity issue and how to resolve it:

* **The Problem:** Git failed with Could not resolve host. Web browsers handle corporate proxy settings automatically, but the standalone Git client installed on the machine and used by Hackolade Studio does not, causing DNS resolution to fail.
* **The Solution:** I configured Git to route traffic through the local network proxy ([127.0.0.1:8999](<http://127.0.0.1:8999>)) with environment variable HTTP\_PROXY et HTTPS\_PROXY (as per [Git documentation](<https://git-scm.com/docs/git-config#Documentation/git-config.txt-httpproxy> "target=\"\_blank\"")).

&nbsp;

**Commands to execute in the command prompt:**

git config --global http.proxy [http://127.0.0.1:8999](<http://127.0.0.1:8999>)

git config --global https.proxy [http://127.0.0.1:8999](<http://127.0.0.1:8999>)

git config --global http.sslVerify false

After setting the proxy, connect Hackolade using a **Personal Access Token** (Repository read \& write permissions) and you will be able to successfully clone the repository using its HTTPS .git URL.

&nbsp;

&nbsp;

&nbsp;

