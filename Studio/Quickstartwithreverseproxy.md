# Quick start with reverse proxy

This guide walks you from an empty Linux server to a working Model Hub environment reachable at *https://\<your-domain-name>* with a valid Let's Encrypt certificate.

&nbsp;

For this quick start to work, you need the following:

- A domain name you control
- A Linux server with a public IPv4 address
- Inbound access to TCP 80 and 443 from the internet
- Outbound access to Let's Encrypt servers

&nbsp;

## Create a DNS name that points to the Model Hub server

### Find your server's public IP

On the server, run:

&nbsp;

```bash
curl -4 ifconfig.me
```

&nbsp;

Or copy the **Public IP** from your cloud provider console (AWS, Azure, GCP, etc.). Write it down, as you will use it in the next step.

&nbsp;

**You are done with this step when:** you know the public IPv4 of the machine that will run Model Hub.

&nbsp;

Let's Encrypt will only issue a certificate if your hostname resolves to this server on the public internet. Do this **before** starting Docker.

&nbsp;

### Pick a hostname

Choose a subdomain, for example:

&nbsp;

```text
* hck.yourcompany.com
```

&nbsp;

Use that exact name everywhere below (DNS, Traefik config, browser).

&nbsp;

### Create an A record at your DNS provider

Log in to wherever your DNS is managed (examples: Cloudflare, GoDaddy, Route 53, Azure DNS, Namecheap, Google Domains).

&nbsp;

Open the DNS settings for your domain (e.g. *yourcompany.com*).

&nbsp;

Add a new record:

&nbsp;

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
<td>Your server's <strong>public IPv4</strong> from the checklist</td>
</tr>
</tbody>
</table>

&nbsp;

Save the record.

&nbsp;

### Wait and verify DNS

DNS can take a few minutes (sometimes longer). From any machine, check that the name resolves to your server IP:

&nbsp;

```text
nslookup hck.yourcompany.com
```

&nbsp;

The result must be **the same public IP** you set in the A record.

&nbsp;

**Do not continue until this works:** If DNS is wrong, Let's Encrypt will fail, and you may hit rate limits if you keep retrying.

&nbsp;

**You are done with this step when:** *nslookup* returns your server's public IP for your Model Hub hostname.

&nbsp;

## Edit your Docker Compose file

Deploy Model Hub like described above but edit the Docker Compose shown on that page with the one below. It provides Model Hub and a PostgreSQL database. On top of that, it deploys a reverse proxy ([traefik](<https://traefik.io/traefik> "target=\"_blank\"")), which automatically generates a certificate with [Let's Encrypt](<https://letsencrypt.org/docs/> "target=\"_blank\"")

&nbsp;

**Note** that model-hub doesn't expose port 3000 with this configuration anymore. Model Hub will instead be served by the reverse proxy Traefik

&nbsp;

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
    image: hackolade.azurecr.io/postgres/postgres:18.4-alpine
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
      # Edit REPLACE_WITH_YOUR_EMAIL before starting the stack.
      # Do NOT redirect HTTP→HTTPS on the web entrypoint — that breaks Let's Encrypt HTTP-01.

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
      # Replace hck.example.com under tls.domains — used only for the Let's Encrypt certificate.
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
                - main: ${HCK_DOMAIN_NAME}
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

&nbsp;

> [!NOTE]
> Also make sure that the volume \`letsencrypt\` is configured like shown in the example. This allows you to store the certificate on the server to avoid losing it on restarts.

&nbsp;

Create a \`.env\` in the same folder as the compose file, similar to the one below, and fill it with your information

&nbsp;

```text
MODEL_HUB_VERSION=REPLACE_WITH_MODEL_HUB_VERSION
CERTIFICATE_EMAIL=REPLACE_WITH_YOUR_EMAIL
HCK_DOMAIN_NAME=REPLACE_WITH_YOUR_DOMAIN
```

&nbsp;

where:\
1\. change the value of *MODEL_HUB_VERSION* with the version you want to deploy from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\"")\
2\. change the value of *REPLACE_WITH_YOUR_EMAIL* with a real email address. This email address will be used to link it to the generated certificate.\
3\. change the value of *REPLACE_WITH_YOUR_DOMAIN* with the exact DNS name from Step 1.
