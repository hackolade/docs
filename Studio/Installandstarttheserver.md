---
description: Choose how to deploy Hackolade Model Hub on AWS, on Azure, or on your own server, and what every deployment needs so that users reach it over HTTPS.
seoTitle: Install and start the Model Hub server
image: lib/Model Hub installation components.png
---
# Install and start the server

The Hackolade Model Hub is delivered as a Docker image, [hackolade/model-hub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\""), that you run on a server of your own. Your users then open it in their browser to search, browse and analyze the data models stored in your Git repositories.

Every deployment has the same parts:

- the **Model Hub container**, which serves the web interface and the APIs on port `3000`
- a **PostgreSQL or Oracle database** that you provide, where the Model Hub stores its data
- two **secrets**: the database password, and the encryption key that protects the configuration stored in the database
- a **reverse proxy or load balancer** that holds the TLS certificate of your hostname and serves the Model Hub over HTTPS

![Model Hub installation components](<lib/Model Hub installation components.png>)

## How users reach the Model Hub

Your users open the Model Hub in their browser at `https://<your-hostname>`, the hostname you gave the Hackolade Helpdesk as described in [Model Hub prerequisites](ModelHubprerequisites.md). The reverse proxy or load balancer receives their requests and forwards them to port `3000` of the container.

HTTPS is mandatory: the Model Hub runs part of its work in the browser, with service workers, and browsers allow them only on HTTPS pages. If you open `http://<server-ip>:3000` from your workstation, the page loads but the license check fails. Always use the hostname, not an IP address or the load balancer's own name, as the Hackolade Helpdesk configures domain locking for that hostname.

A Model Hub that answers on port `3000` of its server is not installed yet. The installation is done when a user's workstation opens `https://<your-hostname>` and the Model Hub loads. Your users can work in it once the license key holder finishes the [Model Hub configuration](ModelHubconfiguration.md): the license key, sign-in, and Git repositories.

## Choose how to deploy

Before you start, complete the [Model Hub prerequisites](ModelHubprerequisites.md): the Hackolade Helpdesk must have registered your hostname, and the decisions listed there must be made.

These guides are for your infrastructure team. Each one goes from the server to the HTTPS address that your users open:

- **On AWS**: [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md), with RDS for PostgreSQL and an Application Load Balancer. The same deployment is also available as [Terraform code](<https://github.com/hackolade/model-hub-deployment/tree/main/aws> "target=\"_blank\"").
- **On Azure**: [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md), with Azure Database for PostgreSQL and an Application Gateway. The same deployment is also available as a [Bicep template](<https://github.com/hackolade/model-hub-deployment/tree/main/azure> "target=\"_blank\"").
- **On a server that the internet can reach, with nothing in front of it**: [Model Hub with Traefik and Let's Encrypt](Quickstartwithreverseproxy.md). Traefik gets a free certificate for your hostname and serves the Model Hub over HTTPS. The Model Hub is then open to the whole internet, protected by its sign-in once you configure it.
- **Behind your organization's own reverse proxy or load balancer**, on premises, on another cloud, or on Kubernetes: [Model Hub on your own server](ModelHubonyourownserver.md). It describes every setting of the Model Hub, and what your reverse proxy must do.

Each guide is an example. You can adapt its parts to the standards of your organization, such as your DNS provider, your certificates or your network rules, as long as your users reach the Model Hub over HTTPS on its hostname.

To evaluate the Model Hub with your own models before a production deployment, use the [Standalone personal trial](Standalonepersonaltrial.md) on your computer instead.

## After the installation

When the Model Hub loads on your hostname, the person who holds the license key continues with the [Model Hub configuration](ModelHubconfiguration.md): sign-in first, then the license key and Git repositories.

> [!WARNING]
> Until sign-in is configured in the Model Hub, anyone who reaches your hostname can open the Model Hub and its Admin panel. Configure sign-in right after the installation, and until then let only your own IP ranges reach the hostname. If a step fails, [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md) lists the checks to run and what to send to Hackolade support.
