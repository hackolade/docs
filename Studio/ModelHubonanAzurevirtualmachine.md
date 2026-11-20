---
description: Deploy Hackolade Model Hub on an Azure virtual machine with Azure Database for PostgreSQL and an Application Gateway that serves it over HTTPS.
seoTitle: Deploy Hackolade Model Hub on an Azure virtual machine
---
# Model Hub on an Azure virtual machine

This guide shows one way to deploy the Model Hub on Azure: a virtual machine, an Azure Database for PostgreSQL flexible server, and an Application Gateway that serves it over HTTPS. Other setups work too, as long as your users reach the Model Hub over HTTPS on its hostname: see [Adapt this example](<https://hackolade.com/help/ModelHubonanAzurevirtualmachine.html#Adapt%20this%20example>).

Before you start, complete the [Model Hub prerequisites](ModelHubprerequisites.md): the Hackolade Helpdesk must have registered your hostname. This guide is for your infrastructure team, and needs no license key: the license key is entered in the browser after the installation. The guide uses `hck.example.com` as the hostname; replace it with yours everywhere. If a step fails, [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md) lists the checks to run and what to send to Hackolade support. For the meaning of each setting of the Model Hub itself, see [Model Hub on your own server](ModelHubonyourownserver.md).

> [!TIP]
> To build this deployment with code instead of the Azure console, start from our [Bicep example](<https://github.com/hackolade/model-hub-deployment/tree/main/azure> "target=\"_blank\""). It builds the same deployment, and its comments name the step of this guide that each part follows. Read this guide first: it explains what the code builds and what to adapt.

## What you deploy

The deployment has four parts:

- an **Application Gateway** that receives your users' requests on `https://hck.example.com`, with the certificate of that hostname, and forwards them to port `3000` of the virtual machine
- a **virtual machine** without a public IP address, which runs the Model Hub with Docker Compose
- an **Azure Database for PostgreSQL flexible server**, reachable only from your virtual network
- outbound internet access for the virtual machine, usually through a NAT gateway, so that the Model Hub can reach Docker Hub, the Hackolade licensing servers and your Git provider

Your users never connect to the virtual machine directly: the Application Gateway is the only way in.

## Adapt this example

Each part can be swapped for what your organization already uses:

- **DNS**: Azure DNS or any DNS provider (step 9).
- **Certificate**: from Azure Key Vault, or a PFX file uploaded to the gateway (step 7).
- **Users on your corporate network**, through a VPN or ExpressRoute: a private frontend IP address instead of a public one (steps 1, 8 and 9).
- **Connecting to the virtual machine**: Azure Bastion, or SSH through your VPN (step 4).
- **Operating system**: Ubuntu, or any Linux distribution supported by Docker Engine (step 4).
- **Database for a trial**: PostgreSQL in a container on the virtual machine, with the Docker Compose file of [PostgreSQL in a container, for a trial](<https://hackolade.com/help/ModelHubonyourownserver.html#PostgreSQL%20in%20a%20container,%20for%20a%20trial>) at step 6; skip steps 3 and 5.
- **Containers**: AKS or Azure Container Apps instead of a virtual machine, with the settings of [Model Hub on your own server](<https://hackolade.com/help/ModelHubonyourownserver.html#Kubernetes%20and%20other%20container%20platforms>).

## 1. Plan the network

Create a resource group and a virtual network with three subnets:

| Subnet | Content | Notes |
| --- | --- | --- |
| `appgw-subnet` | The Application Gateway, and nothing else | Azure recommends a `/24` range |
| `vm-subnet` | The virtual machine | Attach a NAT gateway for outbound internet access |
| `db-subnet` | The PostgreSQL flexible server | Delegated to `Microsoft.DBforPostgreSQL/flexibleServers` when you create the server |

The NAT gateway gives the Model Hub access to the destinations listed in [Model Hub prerequisites](<https://hackolade.com/help/ModelHubprerequisites.html#Network%20requirements>). If your organization routes outbound traffic through its own firewall instead, allow these destinations there.

Choose how your users reach the Application Gateway:

- With a **public frontend IP address** when your users connect over the internet.
- With a **private frontend IP address** in `appgw-subnet` when your users connect through your corporate network. Your workstations must then have a route to the virtual network, and resolve the hostname through your corporate DNS or an Azure private DNS zone.

## 2. Create the network security groups

Create a network security group for each of the first two subnets, and associate it with its subnet:

| Network security group | Inbound rule | Source |
| --- | --- | --- |
| On `appgw-subnet` | TCP 443 and TCP 80 | The IP ranges of your users, or `Internet` for everyone |
| On `appgw-subnet` | TCP 65200-65535 | The `GatewayManager` service tag, which Azure requires for Application Gateway |
| On `vm-subnet` | TCP 3000 | The address range of `appgw-subnet` |

Your Git provider must also reach your hostname over HTTPS, to notify the Model Hub each time models change (webhooks). With github.com, gitlab.com, Bitbucket Cloud or Azure DevOps, this traffic comes from the internet. Until sign-in is configured in the Model Hub, anyone who reaches your hostname can open the Model Hub and its Admin panel. Until then, allow only your own IP ranges.

Keep the default rules, which allow traffic inside the virtual network, so the virtual machine reaches the database. There is no SSH rule from the internet: you connect to the virtual machine with Azure Bastion, at step 4.

## 3. Create the database

In the Azure portal, create an **Azure Database for PostgreSQL flexible server**, and set:

- **PostgreSQL version**: 17 or later
- **Authentication**: PostgreSQL authentication only, with an administrator login and password; keep them, you use them once at step 5
- **Networking > Connectivity method**: Private access (VNet Integration), with your virtual network and `db-subnet`, and a new private DNS zone

Choose the compute and storage that fit your number of models; you can change them later. Backups are on by default.

When the server is ready, copy its **Server name** from the **Overview** page, for example `hub-db.postgres.database.azure.com`.

The flexible server accepts only encrypted connections by default. Its certificate is signed by public certificate authorities, so `?sslmode=require` in the connection string is enough.

## 4. Create the virtual machine and install Docker

Create a virtual machine, and set:

- **Image**: Ubuntu Server 24.04 LTS
- **Size**: at least 4 vCPUs, for example `Standard_D4s_v5` (4 vCPUs, 16 GiB of memory)
- **Public inbound ports**: None
- **Disks**: an OS disk of 64 GiB
- **Networking**: your virtual network, `vm-subnet`, and **Public IP** set to None

When the virtual machine is running, open it, click **Connect > Connect via Bastion**, and deploy Azure Bastion if your virtual network does not have it yet. Once connected, become root for the rest of this guide:

```bash
sudo -i
```

Install Docker Engine and the Docker Compose plugin as described in [Install Docker Engine on Ubuntu](<https://docs.docker.com/engine/install/ubuntu/> "target=\"_blank\""). Then check that both are available:

```bash
docker version
docker compose version
```

## 5. Create the database user

From the virtual machine, connect to the database with the PostgreSQL client of the official PostgreSQL image, so that you do not have to install it. Replace the server name and the administrator login with yours; `psql` asks for the administrator password:

```bash
docker run --rm -it postgres:18-alpine psql "host=<server-name>.postgres.database.azure.com port=5432 dbname=postgres user=<admin-login> sslmode=require"
```

At the `psql` prompt, create the user and the database of the Model Hub, with a password of your choice, then quit with `\q`:

```sql
CREATE ROLE hck_hub WITH LOGIN PASSWORD '<hck_hub-password>';
GRANT hck_hub TO CURRENT_USER;
CREATE DATABASE hck_hub OWNER hck_hub;
```

The Model Hub creates its tables in this database the first time it starts.

## 6. Start the Model Hub

Create the folder of the Model Hub and its two secret files:

```bash
mkdir -p /opt/model-hub/secrets
cd /opt/model-hub
printf '%s' '<hck_hub-password>' > secrets/db_password
openssl rand -hex 32 > secrets/model_hub_encryption_key
chmod 700 secrets
chmod 644 secrets/*
```

Keep a copy of `secrets/model_hub_encryption_key` in a safe place, such as Azure Key Vault: without it, the Model Hub cannot read the configuration it stores in the database.

Create the file `/opt/model-hub/.env` with the Model Hub version you deploy, from [Docker Hub](<https://hub.docker.com/r/hackolade/model-hub/tags> "target=\"_blank\""):

```text
MODEL_HUB_VERSION=<model-hub-version>
```

Create the file `/opt/model-hub/docker-compose.yml`, with your server name in `DB_CONNECTION`:

```yaml
services:
  model-hub:
    image: hackolade/model-hub:${MODEL_HUB_VERSION}
    deploy:
      restart_policy:
        condition: always
        delay: 5s
        window: 30s
    ports:
      - "3000:3000"
    environment:
      DB_TYPE: pg
      DB_CONNECTION: pg://<server-name>.postgres.database.azure.com:5432/hck_hub?sslmode=require
      DB_USERNAME: hck_hub
      DB_PASSWORD_FILE: /run/secrets/db_password
      CURRENT_ENCRYPTION_KEY_FILE: /run/secrets/model_hub_encryption_key
    secrets:
      - db_password
      - model_hub_encryption_key
secrets:
  db_password:
    file: ./secrets/db_password
  model_hub_encryption_key:
    file: ./secrets/model_hub_encryption_key
```

Start the Model Hub, and follow its logs until they show `Server ready`:

```bash
docker compose up -d
docker compose logs -f model-hub
```

Press **Ctrl+C** to stop following the logs, then check that the Model Hub is ready:

```bash
curl -f http://localhost:3000/ready
```

The Model Hub now runs, but your users cannot reach it yet: the next steps put the Application Gateway in front of it.

## 7. Prepare the certificate

Application Gateway needs the certificate of `hck.example.com` with its private key, as a PFX file protected by a password. Get it from your organization's certificate authority or from a public one.

We recommend storing it in Azure Key Vault, as a certificate. Application Gateway then reads it through a user-assigned managed identity that has the **Key Vault Secrets User** role on the vault, and picks up renewed versions on its own. You can also upload the PFX file directly when you create the listener, and upload the renewed file yourself before it expires.

## 8. Create the Application Gateway

In the Azure portal, create an **Application Gateway**, and set:

- **Basics**: tier Standard V2, your virtual network, and `appgw-subnet`
- **Frontends**: a public IP address, a private IP address, or both, as chosen at step 1
- **Backends**: a backend pool with your virtual machine as target

In **Configuration**, add a routing rule:

- **Listener**: protocol HTTPS, port 443, with your certificate from Key Vault or your PFX file
- **Backend targets**: your backend pool, with new backend settings: protocol HTTP, port 3000, and **Override with new host name** set to No

Then add a health probe, so that the gateway sends requests only once the Model Hub is ready. Under **Settings > Health probes**, click **Add**, and set:

- **Protocol**: HTTP
- **Host**: `127.0.0.1`
- **Path**: `/ready`
- **Backend settings**: the backend settings of your rule

To send users who type the hostname without `https://` to the secure page, add a listener on HTTP, port 80, and a routing rule that redirects it to the HTTPS listener.

Under **Monitoring > Backend health**, your virtual machine shows as **Healthy** after a few probes.

## 9. Point the hostname to the Application Gateway

Copy the frontend IP address of the Application Gateway from its **Overview** page, then create an **A** record from `hck.example.com` to that address:

- For a public frontend, in your public DNS zone, in Azure DNS or at another provider.
- For a private frontend, in the DNS that your workstations resolve: your corporate DNS, or an Azure private DNS zone linked to the virtual network that your users come through.

## 10. Verify from a workstation

From the workstation of one of your users, check that the hostname resolves, then that the Model Hub answers over HTTPS. On Linux or macOS:

```bash
nslookup hck.example.com
curl -I https://hck.example.com/health
```

On Windows, in PowerShell, where `curl` alone runs another command, type `curl.exe`:

```powershell
nslookup hck.example.com
curl.exe -I https://hck.example.com/health
```

Then open `https://hck.example.com` in your browser: the Model Hub loads. The installation is done. Whoever holds the license key, usually the person who registered the hostname, then continues with the [Model Hub configuration](ModelHubconfiguration.md): the license key, sign-in and Git repositories. Your users can work in the Model Hub once it is done.

## When something does not work

Start with the logs of the Model Hub on the virtual machine, `docker compose logs model-hub`, then follow the request from the browser to the database:

| What you see | What to check |
| --- | --- |
| The browser times out, or `curl` cannot connect | The network security group of `appgw-subnet` allows your users' IP ranges. For a private frontend, your workstation has a route to the virtual network. `nslookup` returns the frontend IP address. |
| HTTP 502 from the Application Gateway | **Backend health** shows the virtual machine as unhealthy: the network security group of `vm-subnet` allows port 3000 from `appgw-subnet`, and `docker compose ps` shows the Model Hub running and healthy. |
| The logs show `ENOTFOUND` for the server name | The private DNS zone of the flexible server is linked to your virtual network. |
| The logs show `ECONNREFUSED` or a timeout to the server name | The flexible server uses private access in the same virtual network. |
| The logs show that SSL is required | `DB_CONNECTION` ends with `?sslmode=require`. |
| The page loads, but the license check fails | You opened the Model Hub with its hostname, not an IP address, and over HTTPS. The virtual machine reaches the licensing servers through the NAT gateway. |

If the problem is not in this table, follow [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md).

## Keep the Model Hub up to date

To install a new version, follow [Upgrade the Model Hub](UpgradetheModelHub.md) in `/opt/model-hub`. The flexible server backs up the database; keep the encryption key with those backups, as described in [Data backup](Databackup.md).
