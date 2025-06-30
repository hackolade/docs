# Connection and authentication

To properly connect Hackolade Studio to your Collibra instance, there are requirements for setup on the Collibra side, and there are requirements for information to be configured for connection and authentication on the Hackolade Studio client side.

## Collibra setup Requirements

The requirements on the Collibra side, for the Hackolade Studio integration to function properly, include REST API security configuration and user rights.

&nbsp;

To connect to your Collibra instance, you must first create a connection.&nbsp; The path is the same as the base URL of your Collibra instance.&nbsp; Do not include in the path additional information such as the link to a community, domain or asset.

![Collibra connection settings](<lib/Collibra connection settings.png>)

&nbsp;

### Security configuration

By default, the Collibra configuration is correct, and no action should be required.&nbsp; But your administrator may have changed one parameter that would prevent our REST API integration.&nbsp; If you encounter the error message below about CSRF token mismatch:

![Collibra CSRF Token mismatch](<lib/Collibra CSRF Token mismatch.png>)

&nbsp;

then an adjustment is required in the Collibra console, as per the [Collibra documentation](<https://productresources.collibra.com/docs/collibra/latest/Content/Console/Infrastructure/DGCService/SecurityConfiguration/ta\_configure-rest-security.htm> "target=\"\_blank\"").

![Collibra REST API security config](<lib/Collibra REST API security config.png>)

&nbsp;

&nbsp;

You may need to ask your administrator to go to https://console-\<your organization\>.collibra.com/#/infrastructure \> Environments \> your instance \> Data Governance Center \> Configuration tab \> 15 Security Configuration \> 15.3 REST \> 15.3a Limited CSRF and set it to False.

&nbsp;

![Collibra REST API security config console](<lib/Collibra REST API security config console.png>)

&nbsp;

&nbsp;

&nbsp;

&nbsp;

### User rights

In order to feed data model information to the Collibra instance, it is assumed that you have sufficient credentials to do so.&nbsp; If not, please contact your Collibra administrator.

To successfully import a Hackolade model into Collibra, a user should have the author's license type. The role that is assigned to the user should have been provided with the following permissions:

&nbsp;

* For global role and permissions:

  * **System administration** - *(This is necessary to apply the custom Hackolade configuration: attributeTypes, relationTypes, scope...)*

* For resource role and permissions:

  * **Asset:**

    * Add
    * **Attribute:**

      * Add
      * Remove
      * Update

  * **Attachment:**

    * Add

  * **Domain:** *(This is necessary for views and work with Hackolade Mapping Domain)*

    * Add
    * Remove
    * Update

&nbsp;

We also recommend assigning a user with the above permissions to the parent community of the target domain. It is needed to create/update/delete Hackolade Mapping Domain.

&nbsp;

The Hackolade Mapping Domain is used to represent links between view columns and columns in tables, for example:

![Collibra Mapping Domain](<lib/Collibra Mapping Domain.png>)

&nbsp;

&nbsp;

&nbsp;

## Username and password

To connect to the Collibra instance, you must first specify connection settings:

![Collibra connection settings](<lib/Collibra connection settings.png>)

You can then choose between two different authentication types: basic authentication (aka providing your username and password) or OAuth.

![Collibra authentication choices](<lib/Collibra authentication choices.png>)

&nbsp;

&nbsp;

## OAuth

Hackolade Studio supports connecting to Collibra through [OAuth](<https://frontegg.com/blog/oauth> "target=\"\_blank\""). OAuth is an open standard for token-based authentication over public networks. It allows Hackolade to connect to Collibra on your behalf without requesting your credentials.

&nbsp;

Using OAuth involves a few pre-requisites that must be taken care of by your IT administrator.

&nbsp;

Your Collibra instance must first be configured to hand over authentication to an identity provider (IDP), such as Microsoft Entra ID (formerly known as Azure Active Directory) or Okta. Your Collibra administrator can do that by following the instructions from the Collibra documentation: see [Configure Single Sign-On access](<https://productresources.collibra.com/docs/collibra/latest/Content/Console/Infrastructure/DGCService/SecurityConfiguration/ta\_configure-sso-access.htm>).

&nbsp;

The Hackolade Studio application must then be registered in your identity provider. That registration will provide the *Client ID* that you need to input in the Hackolade connection settings.

&nbsp;

### Microsoft Entra ID

If you use Microsoft Entra ID, then your administrator must [create an app registration](<https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app?tabs=certificate> "target=\"\_blank\"") with the following parameters.

&nbsp;

| **Parameter** | **Value** |
| --- | --- |
| Name | Hackolade Studio |
| Platform | Public client/native (mobile \& desktop) |
| Redirect URI | http://localhost:30424/oauth |


&nbsp;

Your administrator can then give you the settings that you need to provide to Hackolade Studio:

* **Tenant ID**: your administrator can find it using the instructions from [this page](<https://learn.microsoft.com/en-us/entra/fundamentals/how-to-find-tenant> "target=\"\_blank\"")
* **Client ID**: your administrator can find it in the *Overview* page of the app registration that was created in Entra ID for Hackolade Studio (it is labeled *Application ID*)

### Okta

If you use Okta, then your administrator must [create an OpenID Connect app integration](<https://help.okta.com/en-us/content/topics/apps/apps\_app\_integration\_wizard\_oidc.htm> "target=\"\_blank\"") and provide the following parameters in the wizard.

&nbsp;

| **Parameter** | **Value** |
| --- | --- |
| Sign-in method | OIDC - OpenID Connect |
| Application type | Native Application |
| App integration name | Hackolade Studio |
| Grant type | Authorization Code + Refresh Token |
| Sign-in redirect URIs | http://localhost:30424/oauth |
| Sign-out redirect URIs | None (remove default) |
| Assignments | Define who in the organization can access this app |
| Client authentication | None (default value) |
| Proof Key for Code Exchange (PKCE) | Yes (default value) |
| Proof of possession&nbsp; | No&nbsp; (default value) |


&nbsp;

&nbsp;

Your administrator can then give you the settings that you need to provide to Hackolade Studio:

* **Domain**: your administrator can find it using the instructions from [this page](<https://developer.okta.com/docs/guides/find-your-domain/main/> "target=\"\_blank\"")
* **Client ID**: your administrator can find it in the *General* page of the app integration that was created in Okta for Hackolade Studio
* **Authorization server**: if your organization uses [a custom authorization server](<https://developer.okta.com/docs/concepts/auth-servers/> "target=\"\_blank\""), then your administrator must give you the ID of that server

&nbsp;

### Other Identity providers

Hackolade Studio supports connecting through other identity providers than Microsoft Entra ID and Okta. The connection settings are just slightly different:

* **Client ID**: like for Entra ID and Okta, your administrator will get that client ID after registering Hackolade Studio in the identity provider
* **OIDC Metadata URL**: is the URL of the OIDC well known endpoint for your identity provider (it should end with */.well-known/openid-configuration*)
* **Scope**: contains the OAuth scopes that Hackolade Studio will request to your identity provider (we recommend you to stick to the default value)&nbsp;

&nbsp;

&nbsp;

### Troubleshooting

Hackolade Studio displays error codes generated by Collibra.&nbsp; The first step is to make sure that the user can access Collibra web application after authenticating with the IdP, and to make sure that the user has the proper rights, as per section earlier in this article.

&nbsp;

Then, please review the [Collibra documentation](<https://developer.collibra.com/tutorials/rest-api-authentication-jwt#jwt-troubleshooting> "target=\"\_blank\"") for the JWT token-related errors, and take the actions suggested by Collibra:

&nbsp;

![Colllibra JWT troubleshooting](<lib/Colllibra JWT troubleshooting.png>)

&nbsp;

&nbsp;

&nbsp;

