---
description: Set up Hackolade Model Hub on a Linux server open to the internet, with Traefik and a free Let's Encrypt certificate for your hostname.
seoTitle: Hackolade Model Hub with Traefik and Let's Encrypt
---
# Model Hub with Traefik and Let's Encrypt

This guide walks you from an empty Linux server to a working Model Hub environment reachable at `https://<your-hostname>` with a valid Let's Encrypt certificate. The Model Hub is then open to the whole internet, protected by its sign-in once you configure it. It is written for your infrastructure team.

For this guide, you need the following:

- The hostname registered with the Hackolade Helpdesk, as described in [Model Hub prerequisites](ModelHubprerequisites.md), in a domain that you control
- A Linux server with a public IPv4 address, and Docker Engine with Docker Compose 2.23.1 or later, installed as described in [Install Docker Engine](<https://docs.docker.com/engine/install/> "target=\"_blank\"")
- Inbound access to TCP 80 and 443 from the internet
- Outbound access to Let's Encrypt servers

Let's Encrypt checks your hostname from the internet before it issues the certificate. If your server sits on a private network, for example a cloud instance without a public IP address that users reach through a VPN, this guide cannot get a certificate. Use your cloud provider's load balancer with a certificate instead, as described in [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) and [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md).

## Point your hostname to the server

### Find your server's public IP

On the server, run:

```bash
curl -4 ifconfig.me
```

Or copy the **Public IP** from your cloud provider console (AWS, Azure, GCP, etc.). Write it down, as you will use it in the next step.

**You are done with this step when:** you know the public IPv4 of the machine that will run Model Hub.

Let's Encrypt will only issue a certificate if your hostname resolves to this server on the public internet. Do this **before** starting Docker.

### Use your registered hostname

Use the hostname that you registered with the Hackolade Helpdesk, for example:

```text
* hck.yourcompany.com
```

Use that exact name everywhere below (DNS, Traefik config, browser).

### Create an A record at your DNS provider

Log in to wherever your DNS is managed (examples: Cloudflare, GoDaddy, Route 53, Azure DNS, Namecheap, Google Domains).

Open the DNS settings for your domain (e.g. *yourcompany.com*).

Add a new record:

<table style="width:35%">
<colgroup><col style="width:34%"><col style="width:66%"></colgroup>
<thead>
<tr>
<th>Field</th>
<th>What to enter</th>
</tr>
</thead>
<tbody>
<tr>
<td>Type</td>
<td>A</td>
</tr>
<tr>
<td>Name / Host</td>
<td><em>hck</em> (for <em>hck.yourcompany.com)</em></td>
</tr>
<tr>
<td>Value / Points to / IPv4</td>
<td>Your server's <strong>public IPv4</strong>, found in the previous step</td>
</tr>
</tbody>
</table>

Save the record.

### Wait and verify DNS

DNS can take a few minutes (sometimes longer). From any machine, check that the name resolves to your server IP:

```text
nslookup hck.yourcompany.com
```

The result must be **the same public IP** you set in the A record.

**Do not continue until this works:** If DNS is wrong, Let's Encrypt will fail, and you may hit rate limits if you keep retrying.

**You are done with this step when:** *nslookup* returns your server's public IP for your Model Hub hostname.

## Create the Docker Compose file

Prepare the project folder and the two secret files as described in [Create the project layout](<https://hackolade.com/help/ModelHubonyourownserver.html#2.%20Create%20the%20project%20layout>), then use the Docker Compose file below instead of the one of that page. It provides Model Hub and a PostgreSQL database in a container, which suits a trial only. For production, use a database that your organization operates and backs up: prepare it as described in [Prepare the database](<https://hackolade.com/help/ModelHubonyourownserver.html#1.%20Prepare%20the%20database>), remove the `postgres` service and the `depends_on` lines below, and set `DB_CONNECTION` and `DB_USERNAME` as in [Create docker-compose.yml](<https://hackolade.com/help/ModelHubonyourownserver.html#3.%20Create%20docker-compose.yml>). On top of that, it deploys a reverse proxy ([traefik](<https://traefik.io/traefik> "target=\"_blank\"")), which automatically generates a certificate with [Let's Encrypt](<https://letsencrypt.org/docs/> "target=\"_blank\"")

**Note** that model-hub doesn't expose port 3000 with this configuration anymore. Model Hub will instead be served by the reverse proxy Traefik

```yaml
services:
  traefik:
    image: traefik:v3.7
    deploy:
      restart_policy:
        condition: always
        delay: 5s
        window: 30s
    ports:
      - 80:80
      - 443:443
    volumes:
      - letsencrypt:/letsencrypt
    configs:
      - source: traefik_static
        target: /etc/traefik/traefik.yml
      - source: traefik_dynamic
        target: /etc/traefik/dynamic.yml
  postgres:
    image: postgres:18-alpine
    deploy:
      restart_policy:
        condition: always
        delay: 5s
        window: 30s
    environment:
      POSTGRES_USER: hck_hub
      POSTGRES_PASSWORD_FILE: /run/secrets/db_password
      POSTGRES_DB: hck_hub
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U hck_hub -d hck_hub"]
      interval: 30s
      timeout: 5s
      retries: 10
      start_period: 5s
    volumes:
      - "model-hub-db-data:/var/lib/postgresql:rw"
    secrets:
      - db_password
  model-hub:
    image: hackolade/model-hub:${MODEL_HUB_VERSION}
    deploy:
      restart_policy:
        condition: always
        delay: 5s
        window: 30s
    environment:
      DB_TYPE: pg
      DB_CONNECTION: pg://postgres:5432/hck_hub
      DB_USERNAME: hck_hub
      DB_PASSWORD_FILE: /run/secrets/db_password
      CURRENT_ENCRYPTION_KEY_FILE: /run/secrets/model_hub_encryption_key
    depends_on:
      postgres:
        condition: service_healthy
    secrets:
      - db_password
      - model_hub_encryption_key
networks:
  default:
    name: hub
volumes:
  letsencrypt: {}
  model-hub-db-data: {}
configs:
  traefik_static:
    content: |
      # Traefik static configuration.
      # CERTIFICATE_EMAIL comes from the .env file.
      # Do NOT redirect HTTP to HTTPS on the web entrypoint: that breaks the Let's Encrypt HTTP-01 challenge.

      entryPoints:
        web:
          address: ":80"
        websecure:
          address: ":443"
      providers:
        file:
          filename: /etc/traefik/dynamic.yml
      certificatesResolvers:
        letsencrypt:
          acme:
            email: ${CERTIFICATE_EMAIL}
            storage: /letsencrypt/acme.json
            httpChallenge:
              entryPoint: web
  traefik_dynamic:
    content: |
      # All traffic that reaches Traefik is proxied to Model Hub.
      # HCK_HOSTNAME comes from the .env file; Let's Encrypt issues the certificate for it.
      # HTTP→HTTPS redirect is a router middleware (ACME challenge on :80 still works).
      http:
        middlewares:
          redirect-to-https:
            redirectScheme:
              scheme: https
              permanent: true
        routers:
          http-to-https:
            rule: PathPrefix(`/`)
            entryPoints:
              - web
            middlewares:
              - redirect-to-https
            service: model-hub
          model-hub:
            rule: PathPrefix(`/`)
            entryPoints:
              - websecure
            service: model-hub
            tls:
              certResolver: letsencrypt
              domains:
                - main: ${HCK_HOSTNAME}
        services:
          model-hub:
            loadBalancer:
              servers:
                - url: http://model-hub:3000
secrets:
  db_password:
    file: ./secrets/db_password
  model_hub_encryption_key:
    file: ./secrets/model_hub_encryption_key
```

> [!NOTE]
> Also make sure that the volume `letsencrypt` is configured like shown in the example. This allows you to store the certificate on the server to avoid losing it on restarts.

Create a `.env` file in the same folder as the compose file, similar to the one below, and fill it with your information

```text
MODEL_HUB_VERSION=REPLACE_WITH_MODEL_HUB_VERSION
CERTIFICATE_EMAIL=REPLACE_WITH_YOUR_EMAIL
HCK_HOSTNAME=REPLACE_WITH_YOUR_HOSTNAME
```

where:\
1\. change the value of *MODEL_HUB_VERSION* with the version you want to deploy from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\"")\
2\. change the value of *REPLACE_WITH_YOUR_EMAIL* with a real email address. This email address will be used to link it to the generated certificate.\
3\. change the value of *REPLACE_WITH_YOUR_HOSTNAME* with your registered hostname, as used in the DNS record above.

## Start and verify

From the folder that contains the Docker Compose file, run:

```bash
docker compose up -d
```

On the server, check that `docker compose ps` shows the services running and healthy, and that `docker compose logs model-hub` shows `Server ready`. Traefik requests the certificate on its first start, which can take a minute. From the workstation of one of your users, open `https://<your-hostname>`: the Model Hub loads with a valid certificate. If the browser shows a certificate warning, run `docker compose logs traefik` to see why Let's Encrypt refused the request; the usual causes are a DNS record that does not point to the server yet, or port 80 closed to the internet.
