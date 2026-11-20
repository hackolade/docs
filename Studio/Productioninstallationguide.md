---
description: "Who does what to install a production Hackolade Model Hub, and the steps in order: prerequisites, installation, configuration and maintenance."
seoTitle: Hackolade Model Hub production installation guide
---
# Production installation guide

Three parties install a production Model Hub: you (the lead of the Model Hub project in your organization), your infrastructure team, and the Hackolade Helpdesk. Your identity team also helps with sign-in.

## Who does what

- **You**: register your hostname with the Hackolade Helpdesk, make the decisions listed in the prerequisites, and send them to your infrastructure team. Once the Model Hub opens in your browser, enter the license key and configure sign-in and Git repositories.
- **Your infrastructure team**: prepares the database and the server, and serves the Model Hub over HTTPS on your hostname, with one of the guides of [Install and start the server](Installandstarttheserver.md).
- **The Hackolade Helpdesk**: registers your hostname, and sends you the Model Hub license key.
- **Your identity team**: registers the Model Hub in Microsoft Entra ID or Okta, as described in [Authentication](Authentication1.md), since that needs administrator rights.

## Steps

1. [Model Hub prerequisites](ModelHubprerequisites.md): start with the request to the Helpdesk, then make the decisions that your infrastructure team needs.
2. [Install and start the server](Installandstarttheserver.md), by your infrastructure team. If a step fails, [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md) lists the checks to run and what to send to Hackolade support.
3. [Model Hub configuration](ModelHubconfiguration.md), by you, right after the installation. Start with sign-in: Until sign-in is configured in the Model Hub, anyone who reaches your hostname can open the Model Hub and its Admin panel. Then the license key, [Authentication](Authentication1.md) with Microsoft Entra ID or Okta, the [Git repo configuration](Gitrepoconfiguration.md) for the providers that your organization uses, and the [MCP server](MCPserver.md).
4. [Model Hub maintenance](ModelHubmaintenance.md), by your infrastructure team: upgrades, backups and monitoring.

Your users can work in the Model Hub once it opens on your hostname and step 3 is done.
