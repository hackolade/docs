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

## Azure AD with Multi Factor Authentication

With the MFA method, depending on the set up of your Azure AD, you may be presented with this pop-up dialog:

![Azure AD MFA consent](<lib/Azure%20AD%20MFA%20consent.png>)

&nbsp;

Your IT admin must give consent in order to allow you access to the database.&nbsp; Consent is required once for the organization.

&nbsp;

Here is the description of the process:

1. Here is an [overview](<https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/user-admin-consent-overview>) of the process and a [blog article](<https://sharepointstuff.com/2020/12/03/how-to-grant-admin-consent-to-applications-in-azure/>).
1. Probably ["user consent settings"](<https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-user-consent?pivots=portal#configure-user-consent-settings>) are configured by your admins to "Do not allow user contest" for all apps or the user doesn't have enough permissions.\
That's why an admin confirmation is required to grant access to the Hackolade application.
1. Admins should review such requests, and can configure them in [Admin consent settings](<https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-admin-consent-workflow>).\
It's possible to select users or groups there and enable email notifications for requests.
1. When a user requests approval from an admin for an application, the admin may approve it using the link in an email notification or review a request in the [admin consent requests](<https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/review-admin-consent-requests>) UI.
1. The user should[ write a justification message and request approval from an admin](<https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/admin-consent-workflow-overview#how-the-admin-consent-workflow-works>), and the admin should review the request and allow access to the Hackolade app

 

&nbsp;

