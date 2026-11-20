---
description: "What to prepare before deploying Hackolade Model Hub: your hostname and license key, Studio and Git, the decisions to make, and system requirements."
seoTitle: Hackolade Model Hub prerequisites
---
# Model Hub prerequisites

Check each item below before the installation starts. Steps 1 to 5 are for you, the person who leads the Model Hub project in your organization. Step 6 is for your infrastructure team.

## 1. Register your hostname with the Hackolade Helpdesk

Start with this step: the installation cannot be finished without it.

Your **hostname** is the full address that your users will type in their browser to open the Model Hub, for example `hck.example.com`. It is usually a subdomain of your organization's domain. Your users open the Model Hub, and Hackolade Studio in the browser, at that exact hostname, over HTTPS. For security, the Hackolade Helpdesk locks the license to that hostname.

Send an email to [support@hackolade.com](mailto:support@hackolade.com?subject=Model%20Hub%20hostname) with your company name and the exact hostname. Send it early: the Helpdesk needs time to configure the hostname before your go-live date. The Helpdesk confirms when your hostname is configured, and sends you the **Model Hub license key** for it.

Keep the license key yourself. You enter it in the Model Hub in your browser once it is installed, as described in [Model Hub configuration](ModelHubconfiguration.md). Your infrastructure team does not need it. If you change the hostname later, send a new request to the Helpdesk.

Your infrastructure team will then need:

- a **DNS record**, the entry that sends your hostname to the Model Hub, resolvable from your users' workstations
- a **TLS certificate** for your hostname, the file that lets browsers open it over HTTPS, issued by Let's Encrypt, by your cloud provider, or by your organization's certificate authority

## 2. Hackolade Studio

The Model Hub is a model-driven metadata management collaboration platform. While you can use Studio without the Hub, the reverse is not possible. You must have Hackolade Studio to create and maintain data models. Each user must either [validate a license key](Softwareregistration.md), or [reuse a key already validated](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop>) in their Studio instance.

## 3. Hackolade Model Hub license add-on

You must have purchased a subscription for the Model Hub for your users so they can access the portal.

## 4. Git repository provider

Your Git repository (or repositories) is (are) the single source-of-truth for your data models. Your data models must be stored with one of the supported Git repository providers, so your organization must have an account with one of the following: [GitHub](GitHub.md) (web or on-prem), [GitLab](GitLab.md) (web or on-prem), Bitbucket ([Cloud](BitbucketCloud.md) or [Data Center](BitbucketDataCenter.md)), or [Azure DevOps Repos](AzureDevOpsRepos.md).

## 5. Decisions to make before the installation

Your infrastructure team needs your answers to these questions before it starts:

- **Hostname**: the one you registered at step 1.
- **Who must reach the Model Hub**: anyone on the internet, protected by the Model Hub sign-in once it is configured, or only people on your organization's network, including through your VPN. Your Git provider must reach it too, to notify the Model Hub when models change: with a cloud service such as github.com, that means from the internet.
- **Where it runs**: on AWS, on Azure, or on your organization's own servers, another cloud or Kubernetes. Your answer picks the installation guide.
- **Database**: PostgreSQL or Oracle, and which team runs and backs it up. A database in a container next to the Model Hub suits a trial only.
- **Git provider**: the address of your Git service, for example `github.com` or your own GitLab server, since the Model Hub must be able to reach it.
- **Sign-in**: Microsoft Entra ID or Okta, configured after the installation, as described in [Authentication](Authentication1.md).

Then send your infrastructure team these answers, a link to [Install and start the server](Installandstarttheserver.md), and a link to this page for the system requirements below.

## 6. System requirements

This section is for your infrastructure team.

### Software requirements

The Hackolade Model Hub can run on any system that supports Docker. Ideally, it should run on a Linux platform where Docker can run natively. You must be able to run [Docker Engine](<https://docs.docker.com/engine/> "target=\"_blank\"") and [Docker Compose](<https://docs.docker.com/compose/> "target=\"_blank\"") (or an equivalent container runtime.)

### Hardware requirements

Start with at least 4 CPUs. More CPUs help the Model Hub serve more users at the same time and synchronize large repositories faster.

The Model Hub needs more memory for larger models. Start with 16 GB, and add more if the Model Hub uses most of it with your models.

The Model Hub stores most of its data in the database, so the server disk mainly holds the Docker images and logs. Start with 50 GB, and add more if needed.

### Network requirements

The Model Hub needs a fast network connection, and the following access:

- Inbound HTTPS (port 443) from your users' workstations to your reverse proxy or load balancer, and from there to port 3000 of the Model Hub server
- Outbound HTTPS from the Model Hub to your Git provider (to fetch and sync models)
- Inbound HTTPS from your Git provider to your hostname, for the notifications it sends when models change (webhooks). With github.com, gitlab.com, Bitbucket Cloud or Azure DevOps, this traffic comes from the internet
- Outbound HTTPS to [hackolade.com](<https://hackolade.com/> "target=\"_blank\"") and studio.hackolade.com, plus [quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"_blank\"") and [qlmdr.com](<https://qlmdr.com> "target=\"_blank\"") for licensing, and [DockerHub](<https://hub.docker.com/u/hackolade> "target=\"_blank\"") to pull images
- Connectivity from the Model Hub to your database host and port

On a cloud provider, these rules translate into security groups or network security groups, and outbound internet access for the server's subnet. [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) and [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md) show them in full.

### Database requirements

> [!IMPORTANT]
> The Model Hub requires a database hosted and managed by the customer, whether deployed on-premises, in a public or private cloud environment, or as part of a hybrid infrastructure. The customer is solely responsible for procuring, licensing, configuring, operating, and maintaining the required database. Any database license fees or related infrastructure costs are excluded from the Model Hub pricing.

The Model Hub stores its application data in this database, including a copy of the data models of your Git repositories, which it keeps up to date. It currently supports:

- PostgreSQL 17 or later
- Oracle Database 23ai or 26ai

Choose the one that best fits your organization's standards and the skills of the team that will operate it. For production, prefer a database that your organization operates and backs up, rather than a database in a container next to the Model Hub.

Your infrastructure team creates the database and its user as described in [Prepare the database](<https://hackolade.com/help/ModelHubonyourownserver.html#1.%20Prepare%20the%20database>).
