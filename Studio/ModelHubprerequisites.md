---
description: "What to prepare before deploying Hackolade Model Hub: Studio and Hub licenses, a Git repository provider, a domain name and system requirements."
seoTitle: Hackolade Model Hub prerequisites
---
# Model Hub prerequisites

Please verify that each requirement below is fulfilled BEFORE you proceed with the deployment detailed in the following pages.

## 1. Hackolade Studio

The Model Hub is a model-driven metadata management collaboration platform. While you can use Studio without the Hub, the reverse is not possible. You must have Hackolade Studio to create and maintain data models. Each user must either [validate a license key](Softwareregistration.md), or [reuse a key already validated](<https://hackolade.com/help/Softwareregistration.html#Reuse%20in%20the%20Browser%20your%20license%20key%20already%20validated%20in%20the%20Desktop>) in their Studio instance.

## 2. Hackolade Model Hub license add-on

You must have purchased a subscription for the Model Hub for your users so they can access the portal.

## 3. Git repository provider

Your Git repository (or repositories) is (are) the single source-of-truth for your data models. Your data models must be stored with one of the supported Git repository providers, so your organization must have an account with one of the following: [GitHub](GitHub.md) (web or on-prem), [GitLab](GitLab.md) (web or on-prem), Bitbucket ([Cloud](BitbucketCloud.md) or [Data Center](BitbucketDataCenter.md)), or [Azure DevOps Repos](AzureDevOpsRepos.md).

## 4. Provide domain name and sub-domain to Hackolade Helpdesk

Model Hub and Studio in the browser will be running on your domain. For security purposes we need to configure domain locking and parameters. Send an email to [support@hackolade.com](mailto:support@hackolade.com?subject=Model%20Hub%20domain%20and%20sub-domain), specifying domain name and subdomain, for example hck.example.com

Our Helpdesk will confirm when the proper configuration has taken place, and will also provide the Model Hub license key for the instance.

Your users will open the Model Hub at exactly that hostname, over HTTPS. Plan for:

- a DNS record that points the hostname to your reverse proxy or load balancer, resolvable from your users' workstations
- a TLS certificate for the hostname, issued by Let's Encrypt, by your cloud provider, or by your organization's certificate authority

## 5. System requirements

### Software requirements

The Hackolade Model Hub can run on any system that supports Docker. Ideally, it should run on a Linux platform where Docker can run natively. You must be able to run [Docker Engine](<https://docs.docker.com/engine/> "target=\"_blank\"") and [Docker Compose](<https://docs.docker.com/compose/> "target=\"_blank\"") (or an equivalent container runtime.)

### Hardware requirements

Model Hub runs on two components: a Node.js server that serves the frontend assets and handles API calls, and database migration tools that ensure your database has the correct schema.

In terms of CPU, the backend is single-threaded, but it is, in theory, possible to scale it horizontally to use as many CPUs as available. The more CPUs, the more it can handle load pressure and the synchronization of repositories with multiple files. It is possible to start with at least 4 CPUs and scale up when necessary.

As for memory, Model Hub is as memory-hungry as the models it ingests. (TBD: build a grid that could serve as a reference)

For the disk, Model Hub doesn't store much data on the disk, as it uses a database to store most of it. You need enough disk space to store Docker images locally and for Docker to function correctly. You can start with a small server with 50GB of disk space and go up if it needs more.

Finally, Model Hub needs a fast network connection. On top of that, Model Hub has the following network requirements

- Inbound HTTPS (port 443) from your users' workstations to your reverse proxy or load balancer, and from there to port 3000 of the Model Hub server
- Outbound HTTPS from the Model Hub to your Git provider (to fetch and sync models)
- Outbound HTTPS to [hackolade.com](<https://hackolade.com/> "target=\"_blank\"") and studio.hackolade.com, plus [quicklicensemanager.com](<https://quicklicensemanager.com/> "target=\"_blank\"") and [qlmdr.com](<https://qlmdr.com> "target=\"_blank\"") for licensing, and [DockerHub](<https://hub.docker.com/u/hackolade> "target=\"_blank\"") to pull images
- Connectivity from the Model Hub to your database host and port

On a cloud provider, these rules translate into security groups or network security groups, and outbound internet access for the server's subnet. [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) and [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md) show them in full.

### Database requirements

> [!IMPORTANT]
> The Model Hub requires a database hosted and managed by the customer, whether deployed on-premises, in a public or private cloud environment, or as part of a hybrid infrastructure. The customer is solely responsible for procuring, licensing, configuring, operating, and maintaining the required database. Any database license fees or related infrastructure costs are excluded from the Model Hub pricing.

The database can be self-standing (installed on a host) or packaged as a container image.

The data models maintained in the customer’s Git repository must be replicated to the Model Hub database.

Model Hub stores most of its application data in a relational SQL database and currently supports:

- PostgreSQL 17 or later
- Oracle Database 23ai or 26ai

Customers should select the supported database platform that best aligns with their operational, maintenance, and configuration requirements, as well as with any applicable internal standards or organizational policies.

When configuring the database, you will need to create an empty database and a user with the following permissions: create, alter, and delete any tables in its schema, as well as read and write permissions on all tables. On PostgreSQL, the Model Hub creates its own schema, so its user must own the database. Further details are provided in [Install and start the server](<https://hackolade.com/help/Installandstarttheserver.html#1.%20Prepare%20the%20database>).
