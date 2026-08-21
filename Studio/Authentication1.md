# Authentication

You should enable authentication so users sign in with your organization’s identity provider. The same configuration protects the Model Hub UI, the Admin panel, and the MCP server.

&nbsp;

Supported identity providers:

* [Azure Entra ID](<IntegratingwithAzureEntraID.md>)
* [Okta](<IntegratingwithOkta.md>)

&nbsp;

Administrators need an IdP role/group that maps to Model Hub admin access (for example Hub.Admin). Configure that in your IdP, then enable authentication in Admin panel → Authentication.

&nbsp;

If you use AI assistants with MCP after authentication is enabled, also add the redirect URIs described in [MCP server](<MCPserver.md>).
