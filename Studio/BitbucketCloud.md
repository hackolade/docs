# Bitbucket Cloud

The information below applies to repositories hosted on Bitbucket Cloud. It explains how to grant Hackolade Studio access to your Bitbucket account, which is a pre-requisite for using the features "[submit for review](<Submitforreview.md>)" and "[review change requests](<Reviewchangerequests.md>)".

&nbsp;

&nbsp;

**IMPORTANT:** as of September 9, 2025, app passwords can no longer be created. Use **API tokens with scopes** instead.&nbsp; All existing app passwords will be disabled on June 9, 2026.&nbsp; Migrate any integrations before then to avoid disruptions.&nbsp; While starting with v8.4.2, the Hackolade Studio dialog is updated to reflect the Bitbucket change to API tokens with scopes, it is possible to use older application versions to connect to Bitbucket Cloud.

&nbsp;

&nbsp;

## API Tokens with scopes, using v8.4.2 and above

API tokens are designed to be used for a single purpose with limited permissions, so they don't require two-factor authentication (2FA).&nbsp; API tokens are tied to an individual account's credentials and should not be shared. By sharing your API token you're giving direct, authenticated access to everything that the token has permissions to do with the Bitbucket APIs.&nbsp; Bitbucket API tokens are further described in [this link](<https://support.atlassian.com/bitbucket-cloud/docs/api-tokens/> "target=\"\_blank\"").

&nbsp;

![Image](<lib/Bitbucket Cloud connection dialog.png>)

&nbsp;

&nbsp;

&nbsp;

To create a connection to Bitbucket Cloud, go to Repository \> Repository Connections, then:

&nbsp;

* In the **Provider** dropdown, select **Bitbucket** (not Bitbucket Data Center)**.**
* The **Host domain name** should be **bitbucket.org** (not editable).
* The **Connect with** dropdown should be **App password** (not editable).
* The **email address** is the address that you use to connect to Bitbucket Cloud \
&nbsp;
* The **API token with scopes** generated following these instructions.

  * Click the Generate link to create an API token with scopes, or go to [https://id.atlassian.com/manage-profile/security/api-tokens](<https://id.atlassian.com/manage-profile/security/api-tokens> "target=\"\_blank\"")
  * **WARNING**: an simple API token will NOT work if is not created with scopes, so make sure to click the button *Create API token with scopes*.\
![Bitbucket create API token with scopes](<lib/Bitbucket create API token with scopes.png>)\
&nbsp;

    * Provide a name and expiration date that cannot be more than 365 in the future\
![Bitbucket API token name and expiry](<lib/Bitbucket API token name and expiry.png>)
    * Select the app Bitbucket\
![Bitbucket API token app selection](<lib/Bitbucket API token app selection.png>)\
&nbsp;
    * Select the scopes

      * The following scopes must all be selected:
- &nbsp;

  - &nbsp;

    - &nbsp;

      - &nbsp;

        - *read:pullrequest:bitbucket*
        - *read:repository:bitbucket*
        - *read:user:bitbucket*
        - *read:workspace:bitbucket*
        - *write:pullrequest:bitbucket*
        - *write:repository:bitbucket*

      - It is suggested to proceed in 2 steps, first for read scopes (make sure to list all the read scopes and select the 4 that are necessary) \
![Bitbucket API token read scopes](<lib/Bitbucket API token read scopes.png>)
      - then for write scopes\
![Bitbucket API token write scopes](<lib/Bitbucket API token write scopes.png>)\
&nbsp;
      - Review your settings and create the token\
![Bitbucket API token review](<lib/Bitbucket API token review.png>)\
&nbsp;
      - Copy your token, save it in a safe place for possible future reference and paste it in the Hackolade Studio dialog\
![Bitbucket API token copy](<lib/Bitbucket API token copy.png>)

&nbsp;

&nbsp;

## API Tokens with scopes, using a version of Hackolade Studio prior to v8.4.2

API tokens are designed to be used for a single purpose with limited permissions, so they don't require two-factor authentication (2FA).&nbsp; API tokens are tied to an individual account's credentials and should not be shared. By sharing your API token you're giving direct, authenticated access to everything that the token has permissions to do with the Bitbucket APIs.&nbsp; This is further described in [this link](<https://support.atlassian.com/bitbucket-cloud/docs/api-tokens/> "target=\"\_blank\"").

&nbsp;

To create a connection to Bitbucket Cloud, go to Repository \> Repository Connections, then:

&nbsp;

* In the **Provider** dropdown, select **Bitbucket** (not Bitbucket Data Center)**.**
* The **Host domain name** should be **bitbucket.org** (not editable).
* The **Connect with** dropdown should be **App password** (not editable).
* The **Username** should be filled in with the **email address** that you use to connect to Bitbucket Cloud (i.e. not your username anymore). The hint that pops up can be ignored.

![Bitbucket Cloud API Tokens with scopes](<lib/Bitbucket Cloud API Tokens with scopes.png>)\
&nbsp;

* The **App password** should be filled in with an **API token with scopes**.

  * Follow this link to create an API token with scopes: [https://id.atlassian.com/manage-profile/security/api-tokens](<https://id.atlassian.com/manage-profile/security/api-tokens>)
  * **WARNING**: it will NOT work if you provide a simple API token (with no scopes), so make sure to click the button *Create API token with scopes*.
  * The following scopes must all be selected:
- &nbsp;

  - &nbsp;

    - *read:pullrequest:bitbucket*
    - *read:repository:bitbucket*
    - *read:user:bitbucket*
    - *read:workspace:bitbucket*
    - *write:repository:bitbucket*
    - *write:pullrequest:bitbucket*

&nbsp;

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

