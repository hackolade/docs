# Bitbucket Cloud

The information below applies to repositories hosted on Bitbucket Cloud. It explains how to grant Hackolade Studio access to your Bitbucket account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

&nbsp;

## App passwords

In the repository connection manager, you first need to provide your Bitbucket username (it is displayed on [your Bitbucket profile](<https://bitbucket.org/account/settings/>)). Note that using your email address as username does NOT work.

&nbsp;

![Workgroup - manage hub connections - Bitbucket Cloud](<lib/Workgroup - manage hub connections-BitBckt Cl.png>)

&nbsp;

You must provide an app password, which is a complex password generated by Bitbucket Cloud.&nbsp; Click on the "generate" link located to the right of the input field to navigate to the app password creation form. Give a meaningful name to your new app password - e.g. "Hackolade Studio" - and select the permissions "Account:Read" and "Pull requests:Write".

&nbsp;

![Workgroup - Bitbucket Cloud personal token](<lib/Workgroup - Bitbucket Cloud personal token.png>)

&nbsp;

Click on the "Create" button and copy-paste the generated password in Hackolade Studio. As a last step, click on "Connect" in Hackolade Studio and you are all set\!

You can find more information about app passwords in the [Bitbucket Cloud documentation](<https://support.atlassian.com/bitbucket-cloud/docs/create-an-app-password/> "target=\"\_blank\"").

&nbsp;

**Remarks:** To be able to retrieve the list of eligible reviewers for a pull request, you must belong to a user group. If you cannot get access to that list in Hackolade, contact your Bitbucket administrator and ask to be added to a user group.

&nbsp;

You may get the error message below if you didn't set a valid app password.&nbsp; It can also indicate that your app password has been revoked, or that it does not grant enough permissions to Hackolade Studio.

&nbsp;

![Workgroup - Bitbucket Cloud token error](<lib/Workgroup - Bitbucket Cloud token error.png>)

&nbsp;

If you see this message, please follow the instructions above.

