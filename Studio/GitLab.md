# GitLab

The information below applies to repositories hosted on GitLab (cloud on gitlab.com and self-hosted instances.)&nbsp; It explains how to grant Hackolade Studio access to your GitLab account, which is a pre-requisite for using the workflow features [submit for review](<Submitforreview.md>) and [review change requests](<Reviewchangerequests.md>).

&nbsp;

## Personal Access Tokens

In the repository connection manager, you need to provide an access token, which is a complex password that must be generated by GitLab.

&nbsp;

![Workgroup GitLab - manager repo connections](<lib/Workgroup GitLab - manager repo connections.png>)

&nbsp;

Click on the "generate" link located to the right of the input field to navigate to the personal access token creation screen of GitLab. You need to click on the button "Create personal access token", as all the required fields should be pre-filled automatically. The access token will be available for you to copy at the top of the page.

&nbsp;

![Workgroup GitLab - Personal Access Tokens](<lib/Workgroup GitLab - Personal Access Tokens.png>)

&nbsp;

Then paste the access token in Hackolade Studio and click the "Connect" button.&nbsp; Take a look at the [GitLab documentation](<https://docs.gitlab.com/ee/user/profile/personal\_access\_tokens.html>) for more information.

&nbsp;

## OAuth

**INFO**: *connecting with OAuth is only possible if you use GitLab cloud and is not supported for self-hosted instances.*

&nbsp;

As an alternative to generating a personal access token, GitLab can also let you grant Hackolade Studio access to your account through [OAuth](<https://oauth.net/>).

&nbsp;

![Workgroup GitLab - OAuth](<lib/Workgroup GitLab - OAuth.png>)

&nbsp;

You just need to click on the "Connect" button to get the instructions below in your browser.

&nbsp;

![Workgroup GitLab - OAuth Authorization](<lib/Workgroup GitLab - OAuth Authorization.png>)

&nbsp;

Click on "Authorize", close the browser window/tab and go back to Hackolade Studio: it should now be connected to GitLab.

