# Model Hub prerequisites

Please verify that each requirement below is fulfilled BEFORE you proceed with the deployment detailed in the following pages.

## Hackolade Studio

The Model Hub is a model-driven metadata management collaboration platform.&nbsp; While you can use Studio without the Hub, the reverse is not possible.&nbsp; You must have Hackolade Studio to create and maintain data models. &nbsp;

&nbsp;

## Hackolade Model Hub license add-on

You must have purchased a subscription for the Model Hub for your users so they can access the portal.&nbsp; Each user must either [validate a license key](<Softwareregistration.md>), or [reuse a key already validated](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop>) in their Studio instance.&nbsp;

&nbsp;

## Get a Personal Access Token from Hackolade Helpdesk

During the OCI Stack creation process, you will need to connect to our public repository to fetch the Terraform configuration.&nbsp; To facilitate this process, please open a ticket at [support@hackolade.com](<mailto:support@hackolade.com?subject=Please%20provide%20a%20Personal%20Access%20Token%20for%20the%20Model%20Hub%20installation>) and we will provide a PAT for your installation.&nbsp; For GitHub Enterprise Cloud, single sign-on (SSO) must be enabled on the PAT.&nbsp; See [Authenticating with SAML single sign-on (GitHub site)](<https://docs.github.com/en/authentication/authenticating-with-saml-single-sign-on>)

&nbsp;

## Git repository provider

Your data models must be stored with one of the supported Git repository providers, so your organization must have an account with one of the following: [GitHub](<GitHub.md>) (web or on-prem), [GitLab](<GitLab.md>) (web or on-prem), Bitbucket ([Cloud](<BitbucketCloud.md>) or [Data Center](<AzureDevOpsRepos.md>)), or [Azure DevOps Repos](<AzureDevOpsRepos.md>). &nbsp;

&nbsp;

## Account on Oracle Cloud Infrastructure (OCI)

The Model Hub runs on Oracle Cloud Infrastructure (OCI) as described in the [technical architecture page](<ModelHubtechnicalarchitecture.md>).

&nbsp;

If your organization already has an OCI account, you may proceed to the next pages.

&nbsp;

If you don't already have an OCI account, you can easily sign up for one.&nbsp; The [Oracle Cloud Free Tier](<https://www.oracle.com/cloud/free/> "target=\"\_blank\"") is sufficient to get started.&nbsp; It includes some free cloud credits, in addition to always free services.&nbsp; As scale, you will want to have a paid account to sustain your performance requirements.

&nbsp;

The process and screens below are indicative, and may change at any time as they are controlled by Oracle -- not Hackolade...

&nbsp;

From the [signup screen](<https://signup.cloud.oracle.com/> "target=\"\_blank\""), create your account information and verify your email.

![OCI Free Tier account info](<lib/OCI Free Tier account info.png>)

&nbsp;

Then enter your password, plus company name, a cloud account name of your choice, and the home region closest to the majority of your users.&nbsp; THis home region cannot be changed after account creation\!

![OCI Free Tier legal info](<lib/OCI Free Tier legal info.png>)

&nbsp;

Then enter your address information

![OCI Free Tier addresss info](<lib/OCI Free Tier addresss info.png>)

&nbsp;

&nbsp;

Oracle requires to enter payment/identity verification information to proceed:&nbsp;

![Image](<lib/OCI Free Tier identity info.png>)

&nbsp;

Then review the terms and conditions and Start your Free Trial if OK:

![OCI Free Tier agreement](<lib/OCI Free Tier agreement.png>)

&nbsp;

It takes a few minutes to set the account up:

&nbsp;

![OCI Free Tier setup wait screen](<lib/OCI Free Tier setup wait screen.png>)

&nbsp;

When completed, you should receive an email with further instructions:

&nbsp;

![OCI Free Tier signup wait screen](<lib/OCI Free Tier signup wait screen.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

![OCI Free Tier email](<lib/OCI Free Tier email.png>)

&nbsp;

When you first log in, you will be asked to set up 2-Factor Authentication:

&nbsp;

![OCI 2 factor authentication](<lib/OCI 2 factor authentication.png>)

&nbsp;

Once verified with the Oracle Authenticator App or any other compatible alternative, you get to your OCI Home screen:

&nbsp;

![OCI Home screen](<lib/OCI Home screen.png>)

&nbsp;

&nbsp;

