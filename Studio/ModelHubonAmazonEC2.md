---
description: Deploy Hackolade Model Hub on an Amazon EC2 instance with RDS for PostgreSQL and an Application Load Balancer that serves it over HTTPS.
seoTitle: Deploy Hackolade Model Hub on Amazon EC2
---
# Model Hub on Amazon EC2

This guide shows one way to deploy the Model Hub on AWS: an EC2 instance, an Amazon RDS for PostgreSQL database, and an Application Load Balancer that serves it over HTTPS. Other setups work too, as long as your users reach the Model Hub over HTTPS on its hostname: see [Adapt this example](<https://hackolade.com/help/ModelHubonAmazonEC2.html#Adapt%20this%20example>).

Before you start, complete the [Model Hub prerequisites](ModelHubprerequisites.md): the Hackolade Helpdesk must have registered your hostname. This guide is for your infrastructure team, and needs no license key: the license key is entered in the browser after the installation. The guide uses `hck.example.com` as the hostname; replace it with yours everywhere. If a step fails, [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md) lists the checks to run and what to send to Hackolade support. For the meaning of each setting of the Model Hub itself, see [Model Hub on your own server](ModelHubonyourownserver.md).

> [!TIP]
> To build this deployment with code instead of the AWS console, start from our [Terraform example](<https://github.com/hackolade/model-hub-deployment/tree/main/aws> "target=\"_blank\""). It builds the same deployment, and its comments name the step of this guide that each part follows. Read this guide first: it explains what the code builds and what to adapt.

## What you deploy

The deployment has four parts:

- an **Application Load Balancer** that receives your users' requests on `https://hck.example.com`, with a certificate from AWS Certificate Manager (ACM), and forwards them to port `3000` of the instance
- an **EC2 instance** in a private subnet, which runs the Model Hub with Docker Compose
- an **RDS for PostgreSQL** database in private subnets
- outbound internet access for the instance, usually through a NAT gateway, so that the Model Hub can reach Docker Hub, the Hackolade licensing servers and your Git provider

Your users never connect to the instance directly: the load balancer is the only way in.

## Adapt this example

Each part can be swapped for what your organization already uses:

- **DNS**: Route 53 or any DNS provider (steps 7 and 9).
- **Certificate**: requested from ACM, or your own certificate imported into ACM (step 7).
- **Users on your corporate network**, through a VPN or AWS Direct Connect: an internal load balancer instead of an internet-facing one (steps 1, 8 and 9).
- **Connecting to the instance**: Session Manager, or SSH through your VPN (step 4).
- **Operating system**: Ubuntu, or any Linux distribution supported by Docker Engine (step 4).
- **Database for a trial**: PostgreSQL in a container on the instance, with the Docker Compose file of [PostgreSQL in a container, for a trial](<https://hackolade.com/help/ModelHubonyourownserver.html#PostgreSQL%20in%20a%20container,%20for%20a%20trial>) at step 6; skip steps 3 and 5.
- **Containers**: Amazon ECS or EKS instead of an instance, with the settings of [Model Hub on your own server](<https://hackolade.com/help/ModelHubonyourownserver.html#Kubernetes%20and%20other%20container%20platforms>).

## 1. Plan the network

Use a VPC with subnets in at least two Availability Zones: both the load balancer and the RDS database require two zones.

- Put the instance and the database in **private subnets**, without public IP addresses.
- Give the private subnets outbound internet access, through a NAT gateway or your organization's own outbound route. The Model Hub needs it for the destinations listed in [Model Hub prerequisites](<https://hackolade.com/help/ModelHubprerequisites.html#Network%20requirements>).
- Choose how your users reach the load balancer:
  - **Internet-facing**, in public subnets, when your users connect over the internet.
  - **Internal**, in private subnets, when your users connect through your corporate network. Your workstations must then have a route to the VPC, and resolve the hostname through your corporate DNS or a Route 53 private hosted zone.

## 2. Create the security groups

In the EC2 console, under **Network & Security > Security Groups**, create three security groups in your VPC. Each one allows only the traffic of the previous step in the chain:

| Security group | Inbound rule | Source |
| --- | --- | --- |
| `hub-alb` | HTTPS, TCP 443, and HTTP, TCP 80 | The IP ranges of your users, or `0.0.0.0/0` for everyone on the internet |
| `hub-ec2` | Custom TCP, port 3000 | The `hub-alb` security group |
| `hub-db` | PostgreSQL, TCP 5432 | The `hub-ec2` security group |

Your Git provider must also reach your hostname over HTTPS, to notify the Model Hub each time models change (webhooks). With github.com, gitlab.com, Bitbucket Cloud or Azure DevOps, this traffic comes from the internet. Until sign-in is configured in the Model Hub, anyone who reaches your hostname can open the Model Hub and its Admin panel. Until then, allow only your own IP ranges.

Keep the default outbound rules. The `hub-ec2` security group has no SSH rule: you connect to the instance with AWS Systems Manager Session Manager, at step 4.

## 3. Create the database

In the RDS console, click **Create database**, and set:

- **Engine type**: PostgreSQL, version 17 or later
- **Credentials**: a master username and password; keep them, you use them once at step 5
- **Virtual private cloud (VPC)**: your VPC, with a DB subnet group made of your private subnets
- **Public access**: No
- **VPC security group**: `hub-db`

Choose the instance class and storage that fit your number of models; you can change them later. Enable automated backups.

When the database is available, copy its **Endpoint** from the **Connectivity & security** tab, for example `hub-db.abc123xyz.eu-west-1.rds.amazonaws.com`.

RDS for PostgreSQL accepts only encrypted connections by default. Its certificate is signed by Amazon's own certificate authority, so step 6 gives the Model Hub the Amazon RDS certificate bundle.

## 4. Launch the instance and install Docker

In the EC2 console, click **Launch instance**, and set:

- **Application and OS Images**: Ubuntu Server 24.04 LTS
- **Instance type**: at least 4 vCPUs, for example `m7i.xlarge` (4 vCPUs, 16 GiB of memory)
- **Network settings**: your VPC, a private subnet, **Auto-assign public IP** disabled, and the `hub-ec2` security group
- **Configure storage**: 50 GiB, gp3
- **Advanced details > IAM instance profile**: a role with the `AmazonSSMManagedInstanceCore` policy, so that you can connect with Session Manager

When the instance is running, select it, click **Connect**, open the **Session Manager** tab, and click **Connect**. Then become root for the rest of this guide:

```bash
sudo -i
```

Install Docker Engine and the Docker Compose plugin as described in [Install Docker Engine on Ubuntu](<https://docs.docker.com/engine/install/ubuntu/> "target=\"_blank\""). Then check that both are available:

```bash
docker version
docker compose version
```

## 5. Create the database user

From the instance, connect to the database with the PostgreSQL client of the official PostgreSQL image, so that you do not have to install it. Replace the endpoint and the master username with yours; `psql` asks for the master password:

```bash
docker run --rm -it postgres:18-alpine psql "host=<rds-endpoint> port=5432 dbname=postgres user=<master-username> sslmode=require"
```

At the `psql` prompt, create the user and the database of the Model Hub, with a password of your choice, then quit with `\q`:

```sql
CREATE ROLE hck_hub WITH LOGIN PASSWORD '<hck_hub-password>';
GRANT hck_hub TO CURRENT_USER;
CREATE DATABASE hck_hub OWNER hck_hub;
```

The Model Hub creates its tables in this database the first time it starts.

## 6. Start the Model Hub

Create the folder of the Model Hub, its two secret files, and download the Amazon RDS certificate bundle:

```bash
mkdir -p /opt/model-hub/secrets
cd /opt/model-hub
printf '%s' '<hck_hub-password>' > secrets/db_password
openssl rand -hex 32 > secrets/model_hub_encryption_key
chmod 700 secrets
chmod 644 secrets/*
curl -fsSL -o rds-ca-bundle.pem https://truststore.pki.rds.amazonaws.com/global/global-bundle.pem
```

Keep a copy of `secrets/model_hub_encryption_key` in a safe place, such as AWS Secrets Manager: without it, the Model Hub cannot read the configuration it stores in the database.

Create the file `/opt/model-hub/.env` with the Model Hub version you deploy, from [Docker Hub](<https://hub.docker.com/r/hackolade/model-hub/tags> "target=\"_blank\""):

```text
MODEL_HUB_VERSION=<model-hub-version>
```

Create the file `/opt/model-hub/docker-compose.yml`, with your RDS endpoint in `DB_CONNECTION`:

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
      DB_CONNECTION: pg://<rds-endpoint>:5432/hck_hub?sslmode=require
      DB_USERNAME: hck_hub
      DB_PASSWORD_FILE: /run/secrets/db_password
      CURRENT_ENCRYPTION_KEY_FILE: /run/secrets/model_hub_encryption_key
      NODE_EXTRA_CA_CERTS: /etc/ssl/rds-ca-bundle.pem
    volumes:
      - ./rds-ca-bundle.pem:/etc/ssl/rds-ca-bundle.pem:ro
    secrets:
      - db_password
      - model_hub_encryption_key
secrets:
  db_password:
    file: ./secrets/db_password
  model_hub_encryption_key:
    file: ./secrets/model_hub_encryption_key
```

`?sslmode=require` encrypts the connection to the database, and `NODE_EXTRA_CA_CERTS` lets the Model Hub check the certificate of RDS against the bundle.

Start the Model Hub, and follow its logs until they show `Server ready`:

```bash
docker compose up -d
docker compose logs -f model-hub
```

Press **Ctrl+C** to stop following the logs, then check that the Model Hub is ready:

```bash
curl -f http://localhost:3000/ready
```

The Model Hub now runs, but your users cannot reach it yet: the next steps put the load balancer in front of it.

## 7. Request the certificate

In the AWS Certificate Manager console, in the same region as your instance:

1. Click **Request**, choose **Request a public certificate**, and click **Next**.
2. In **Fully qualified domain name**, enter `hck.example.com`.
3. Keep **DNS validation**, and click **Request**.
4. Open the certificate, and add the CNAME record it shows to the DNS zone of your domain. If the zone is in Route 53, click **Create records in Route 53**.

The certificate status changes to **Issued** a few minutes after the record exists.

ACM validates the domain through public DNS, even for an internal load balancer. To use a certificate from your own certificate authority instead, click **Import**, and import the certificate and its private key.

## 8. Create the load balancer

First, create the target group. In the EC2 console, under **Load Balancing > Target Groups**, click **Create target group**, and set:

- **Target type**: Instances
- **Protocol and port**: HTTP, port 3000
- **VPC**: your VPC
- **Health check path**: `/ready`

On the next page, select your instance, click **Include as pending below** with port 3000, and click **Create target group**.

Then create the load balancer. Under **Load Balancing > Load Balancers**, click **Create load balancer**, choose **Application Load Balancer**, and set:

- **Scheme**: Internet-facing or Internal, as chosen at step 1
- **Network mapping**: your VPC, and one subnet in each of two Availability Zones
- **Security groups**: `hub-alb` only
- **Listeners and routing**: change the listener to HTTPS, port 443, forwarding to your target group
- **Default SSL/TLS server certificate**: your certificate, from ACM

Once the load balancer is active, select it, open the **Listeners and rules** tab, and add a listener on HTTP, port 80, with the action **Redirect to URL**, HTTPS, port 443. Users who type the hostname without `https://` then land on the secure page.

In your target group, the **Targets** tab shows the instance as **healthy** after a few health checks.

## 9. Point the hostname to the load balancer

Copy the **DNS name** of the load balancer, for example `hub-alb-123456789.eu-west-1.elb.amazonaws.com`, then create a **CNAME** record from `hck.example.com` to it, in the DNS that your workstations resolve: your public zone, your corporate DNS, or a Route 53 private hosted zone for an internal load balancer. In Route 53, an **A** record with **Alias** enabled works as well.

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

Start with the logs of the Model Hub on the instance, `docker compose logs model-hub`, then follow the request from the browser to the database:

| What you see | What to check |
| --- | --- |
| The browser times out, or `curl` cannot connect | The `hub-alb` security group allows your users' IP ranges. For an internal load balancer, your workstation has a route to the VPC. `nslookup` returns the load balancer's addresses. |
| HTTP 502 or 503 from the load balancer | The target is **unhealthy**: the `hub-ec2` security group allows port 3000 from `hub-alb`, and `docker compose ps` shows the Model Hub running and healthy. |
| The logs show `ECONNREFUSED` or a timeout to the RDS endpoint | The `hub-db` security group allows port 5432 from `hub-ec2`, and the database is in the same VPC. |
| The logs show `no pg_hba.conf entry` and `no encryption` | `DB_CONNECTION` ends with `?sslmode=require`. |
| The logs show `self-signed certificate in certificate chain` | The `NODE_EXTRA_CA_CERTS` line and the volume of `rds-ca-bundle.pem` are in `docker-compose.yml`. |
| The page loads, but the license check fails | You opened the Model Hub with its hostname, not an IP address or the load balancer's DNS name, and over HTTPS. The instance reaches the licensing servers through the NAT gateway. |

If the problem is not in this table, follow [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md).

## Keep the Model Hub up to date

To install a new version, follow [Upgrade the Model Hub](UpgradetheModelHub.md) in `/opt/model-hub`. RDS automated backups protect the database; keep the encryption key with them, as described in [Data backup](Databackup.md).
