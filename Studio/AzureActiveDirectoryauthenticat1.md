# Azure Active Directory authentication

Azure AD authentication supports the following [authentication methods](<https://docs.microsoft.com/en-us/azure/azure-sql/database/authentication-aad-configure> "target=\"\_blank\""):

* Azure AD cloud-only identities
* Azure AD hybrid identities that support:

  * Cloud authentication with two options coupled with seamless single sign-on (SSO)

    * Azure AD password hash authentication
    * Azure AD pass-through authentication

  * Federated authentication

&nbsp;

Further details can also be found [here](<https://docs.microsoft.com/en-us/azure/azure-sql/database/authentication-mfa-ssms-overview> "target=\"\_blank\"").

&nbsp;

In the Authentication tab of the connection settings dialog, select the applicable Azure Active Directory authentication method, then provide the username/password and/or Tenant ID, depending on the option:

&nbsp;

![Image](<lib/SQL Server - Azure AD authentication.png>)

&nbsp;

See instructions on [how-to find your tenant ID](<https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-to-find-tenant> "target=\"\_blank\"").

&nbsp;

## Granting admin consent

With the Azure AD methods, whether with Username/Password or with MFA, the Azure administrator must grant tenant-wide admin consent to the Hackolade Studio application, as per the [documentation page](<https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/grant-admin-consent?pivots=portal#grant-tenant-wide-admin-consent-in-enterprise-apps-pane> "target=\"\_blank\"").&nbsp; Here is a shortcut to the [admin consent URL for Hackolade Studio](<https://login.microsoftonline.com/organizations/adminconsent?client\_id=0dc36597-bc44-49f8-a4a7-ae5401959b85> "target=\"\_blank\"").

&nbsp;

![Image](<lib/Azure AD MFA consent.png>)

&nbsp;

Your IT admin must give consent in order to allow you access to the database.&nbsp; Consent is required once for the organization.

&nbsp;

&nbsp;

&nbsp;

