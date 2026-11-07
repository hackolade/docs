---
description: Enable authentication of Hackolade Model Hub users with Microsoft Entra ID or Okta, protecting the UI, the Admin panel and the MCP server.
seoTitle: Model Hub authentication with Entra ID or Okta
---
# Authentication

You should enable authentication so users sign in with your organization’s identity provider. The same configuration protects the Model Hub UI, the Admin panel, and the MCP server.

Supported identity providers:

- [Azure Entra ID](IntegratingwithAzureEntraID.md)
- [Okta](IntegratingwithOkta.md)

Administrators need an IdP role/group that maps to Model Hub admin access (for example Hub.Admin). Configure that in your IdP, then enable authentication in Admin panel → Authentication.

If you use AI assistants with MCP after authentication is enabled, also add the redirect URIs described in [MCP server](MCPserver.md).
