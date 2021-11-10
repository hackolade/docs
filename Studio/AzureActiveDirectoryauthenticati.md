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

![Image](<lib/SQL%20Server%20-%20Azure%20AD%20authentication.png>)

&nbsp;

See instructions on [how-to find your tenant ID](<https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-to-find-tenant> "target=\"\_blank\"").

&nbsp;

With the MFA method, depending on the set up of your Azure AD, you may be presented with this pop-up dialog:

![Azure AD MFA consent](<lib/Azure%20AD%20MFA%20consent.png>)

&nbsp;

Your IT admin must give consent in order to allow you access to the database.&nbsp; Consent is required once for the organization.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

