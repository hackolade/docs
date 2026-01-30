# Entra ID authentication

Microsoft Entra IDauthentication supports the following [authentication methods](<https://learn.microsoft.com/en-us/azure/azure-sql/database/authentication-aad-configure?view=azuresql\&tabs=azure-portal> "target=\"\_blank\""):

* Entra ID cloud-only identities
* Entra ID hybrid identities that support:

  * Cloud authentication with two options coupled with seamless single sign-on (SSO)

    * Entra ID pass-through authentication
    * Entra ID password hash authentication

  * Federated authentication

&nbsp;

Further details can also be found [here](<https://docs.microsoft.com/en-us/azure/azure-sql/database/authentication-mfa-ssms-overview> "target=\"\_blank\"").

&nbsp;

&nbsp;

In the Authentication tab of the connection settings dialog, select the applicable Entra ID code flow authentication method:

&nbsp;

![SQL Server - Entrq ID authentication lPCKE](<lib/SQL Server - Entrq ID authentication lPCKE.png>)

&nbsp;

&nbsp;

## Granting admin consent

With the Entra ID methods, whether with Username/Password or with MFA, the Azure administrator must grant tenant-wide admin consent to the Hackolade Studio application, as per the [documentation page](<https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/grant-admin-consent?pivots=portal#grant-tenant-wide-admin-consent-in-enterprise-apps-pane> "target=\"\_blank\"").&nbsp; Here is a shortcut to the [admin consent URL for Hackolade Studio](<https://login.microsoftonline.com/organizations/adminconsent?client\_id=0dc36597-bc44-49f8-a4a7-ae5401959b85> "target=\"\_blank\"").

&nbsp;

![Image](<lib/Azure AD MFA consent.png>)

&nbsp;

Your IT admin must give consent in order to allow you access to the database.&nbsp; Consent is required once for the organization.

&nbsp;

 

## Legacy username/password

In the Authentication tab of the connection settings dialog, select the applicable Entra ID legacy authentication method, then provide the username/password and Tenant ID:

&nbsp;

![SQL Server - Entrq ID authentication legqcy](<lib/SQL Server - Entrq ID authentication legqcy.png>)

&nbsp;

&nbsp;

See instructions on [how-to find your tenant ID](<https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-to-find-tenant> "target=\"\_blank\"").

