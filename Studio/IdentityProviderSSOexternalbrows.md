# Identity Provider SSO (external browser)

To set up Azure AD for Single Sign-On with Snowflake, you should follow [these instructions](<https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/snowflake-tutorial> "target=\"\_blank\"") as well as [these](<https://support.snowflake.net/s/article/configuring-azure-active-directory-as-an-identity-provider> "target=\"\_blank\"").&nbsp; For Single Sign-On with Okta, you should follow [these instructions](<https://saml-doc.okta.com/SAML\_Docs/How-to-Configure-SAML-2.0-for-Snowflake.html> "target=\"\_blank\"").

&nbsp;

You must provide your network or Azure AD username, or Okta email address,&nbsp; depending on the provider:

&nbsp;

![Snowflake Auth - Identity Provider SSO External browser](<lib/Snowflake Auth - IdP SSO External browser.png>)

&nbsp;

which will be passed on to the Identity Provider, so you may proceed with the login process, possibly with Multi-Factor Authentication if applicable.

&nbsp;

![Snowflake Okta external browser SSO](<lib/Snowflake Okta external browser SSO.png>)
