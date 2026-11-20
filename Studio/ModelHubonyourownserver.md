---
description: Deploy Hackolade Model Hub on your own server with Docker Compose, your database, and your organization's reverse proxy or load balancer.
seoTitle: Deploy Hackolade Model Hub on your own server
---
# Model Hub on your own server

This guide deploys the Model Hub with Docker Compose on a Linux server of your own, on premises or on any cloud, with a database and a reverse proxy or load balancer that your organization operates. On AWS or Azure, [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) and [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md) cover the same steps with the services of each cloud.

Before you start, complete the [Model Hub prerequisites](ModelHubprerequisites.md): the Hackolade Helpdesk must have registered your hostname. This guide is for your infrastructure team, and needs no license key: the license key is entered in the browser after the installation. The examples use `hck.example.com` as the hostname; replace it with yours.

## 1. Prepare the database

The Model Hub uses a PostgreSQL or Oracle database that you provide. Prepare it before you start the Model Hub.

### Database checklist

1\. Create an empty database.\
2\. Create a dedicated user.\
3\. Grant that user permission to create, alter, and delete tables in its schema, and to read and write those tables.\
4\. Ensure the Model Hub containers can reach the database host and port.

### PostgreSQL

On PostgreSQL, the Model Hub creates its own `hck_hub` schema in the database, so its user must own the database. Connected to your PostgreSQL server as an administrator, run:

```sql
CREATE ROLE hck_hub WITH LOGIN PASSWORD '<database-password>';
GRANT hck_hub TO CURRENT_USER;
CREATE DATABASE hck_hub OWNER hck_hub;
```

The `GRANT` line lets an administrator who is not a superuser, such as the administrator of a managed database on AWS or Azure, create a database owned by the `hck_hub` user.

When your database requires encrypted connections, which is the default for managed PostgreSQL services, add `?sslmode=require` to `DB_CONNECTION` at step 3: `pg://<db-host>:5432/<database>?sslmode=require`. The Model Hub then checks the certificate of the database server against the usual public certificate authorities. For a certificate signed by another authority, such as Amazon RDS, see [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md).

### PostgreSQL on the same server

When PostgreSQL is installed directly on the server that runs Docker, outside a container, the Model Hub container reaches it through the address of the server on the Docker network. Add these lines to the `model-hub` service of your `docker-compose.yml` at step 3:

```yaml
    extra_hosts:
      - "host.docker.internal:host-gateway"
```

and use `pg://host.docker.internal:5432/<database>` as `DB_CONNECTION`.

PostgreSQL accepts only local connections by default, so you also have to change its configuration and then restart it:

- In `postgresql.conf`, set `listen_addresses` to include the address of the server on the Docker network, or `'*'` if a firewall protects port `5432`.
- In `pg_hba.conf`, allow the Docker networks, for example `host hck_hub hck_hub 172.16.0.0/12 scram-sha-256`.

Without these changes, the Model Hub logs `ECONNREFUSED` errors and restarts in a loop.

### Oracle

In `docker-compose.yml` at step 3, set `DB_TYPE` to `oracledb`, and `DB_CONNECTION` to an Oracle Connect descriptor or Easy Connect string:

```yaml
services:
  model-hub:
    image: hackolade/model-hub:${MODEL_HUB_VERSION}
    environment:
      DB_TYPE: oracledb
      DB_USERNAME: <db-user>
      DB_PASSWORD_FILE: /run/secrets/db_password
      DB_CONNECTION: "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=<db-host>)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=<service-name>)))"
      CURRENT_ENCRYPTION_KEY_FILE: /run/secrets/model_hub_encryption_key
    secrets:
      - db_password
      - model_hub_encryption_key
```

The rest of the file is the same as at step 3.

## 2. Create the project layout

```text
model-hub-deploy/
├── .env
├── docker-compose.yml
└── secrets/
    ├── db_password                       # the database password
    └── model_hub_encryption_key          # the encryption key
```

The encryption key is a 64-character hex string. The Model Hub uses it to encrypt sensitive information in the database, such as your Git provider configuration, and does not start without it. Keep a copy with your database backups: without the key, the Model Hub cannot read the configuration it stored.

Create the two secret files, with the password of the database user of step 1, and do not commit them to source control:

```bash
mkdir -p model-hub-deploy/secrets
cd model-hub-deploy
printf '%s' '<database-password>' > secrets/db_password
openssl rand -hex 32 > secrets/model_hub_encryption_key
chmod 700 secrets
chmod 644 secrets/*
```

The `secrets` folder is closed to other users of the server, while the Model Hub container can still read the files.

## 3. Create docker-compose.yml

Update `DB_CONNECTION` (and, if needed, `DB_USERNAME`) so they match your database host, port, database name, and user. The host is the database server as seen from inside the container: `localhost` there is the container itself, not your server. For a PostgreSQL installed on the same server outside Docker, see [PostgreSQL on the same server](<https://hackolade.com/help/ModelHubonyourownserver.html#PostgreSQL%20on%20the%20same%20server>).

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
      DB_CONNECTION: pg://<db-host>:5432/<database>
      DB_USERNAME: <db-user>
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

where:

<table style="width:65%">
<colgroup><col style="width:27%"><col style="width:73%"></colgroup>
<thead>
<tr>
<th>Setting</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr>
<td>DB_TYPE</td>
<td>Database driver. Use pg for PostgreSQL or oracledb for Oracle.</td>
</tr>
<tr>
<td>DB_CONNECTION</td>
<td>How the application reaches the database. Format depends on the database (see below).</td>
</tr>
<tr>
<td>DB_USERNAME</td>
<td>Database user</td>
</tr>
<tr>
<td>DB_PASSWORD_FILE</td>
<td>Path inside the container to a file containing the password.</td>
</tr>
<tr>
<td>CURRENT_ENCRYPTION_KEY_FILE</td>
<td>Path inside the container to a file containing the encryption key. Required.</td>
</tr>
<tr>
<td>TRUST_PROXY_IP_CIDR</td>
<td>Optional. Address range of your reverse proxy or load balancer, for example 10.0.1.0/24. The Model Hub then records the real IP addresses of your users in its logs.</td>
</tr>
<tr>
<td>Port 3000</td>
<td>Default HTTP port of the Model Hub process. Your reverse proxy or load balancer forwards requests to this port.</td>
</tr>
</tbody>
</table>

## 4. Create the .env file

The `.env` file gives Docker Compose the Model Hub version to deploy. Set `MODEL_HUB_VERSION` to a version from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\"").

```text
MODEL_HUB_VERSION=<model-hub-version>
```

## 5. Start the Model Hub

From the folder that contains `docker-compose.yml`, run:

```bash
docker compose up -d
```

What happens:\
1\. The model-hub container starts and listens on port 3000\
2\. When the container starts, it creates the database structure that it needs to run properly.\
3\. Once the setup is done, the application is ready to be used.

Follow its logs until they show `Server ready`, then press **Ctrl+C**:

```bash
docker compose logs -f model-hub
```

Check from the server that the Model Hub answers:

```bash
curl -f http://localhost:3000/ready
```

The Model Hub now runs, but your users cannot use it yet: the next step serves it over HTTPS on your hostname.

## 6. Serve the Model Hub over HTTPS

Your users reach the Model Hub through your reverse proxy or load balancer, never on port `3000` directly, as explained in [How users reach the Model Hub](<https://hackolade.com/help/Installandstarttheserver.html#How%20users%20reach%20the%20Model%20Hub>). Configure it as follows:

- It holds a TLS certificate for your hostname, issued by an authority that your users' browsers trust: a public one, or your organization's own.
- It forwards the requests to port `3000` of the server, over HTTP.
- It keeps the hostname in the `Host` header, or sends it in `X-Forwarded-Host`, and sends `X-Forwarded-Proto: https`. The Model Hub uses them to build the addresses of its [MCP server](MCPserver.md).
- It does not buffer responses: the MCP server streams its answers.
- Its health check calls `/ready` on port `3000`.
- Optionally, it redirects HTTP on port 80 to HTTPS.

On the server, allow port `3000` only from the reverse proxy or load balancer. Your Git provider must also reach your hostname over HTTPS, to notify the Model Hub each time models change (webhooks). With github.com, gitlab.com, Bitbucket Cloud or Azure DevOps, this traffic comes from the internet. Until sign-in is configured in the Model Hub, anyone who reaches your hostname can open the Model Hub and its Admin panel. Until then, allow only your own IP ranges. Then create the DNS record of your hostname, pointing to the reverse proxy or load balancer, in the DNS that your users' workstations resolve.

For example, with nginx on the same server, and the certificate files of your hostname:

```text
server {
    listen 443 ssl;
    server_name hck.example.com;
    ssl_certificate     /etc/nginx/certs/hck.example.com.crt;
    ssl_certificate_key /etc/nginx/certs/hck.example.com.key;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-Proto https;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_buffering off;
    }
}

server {
    listen 80;
    server_name hck.example.com;
    return 301 https://$host$request_uri;
}
```

## 7. Verify the installation

1\. On the server, `docker compose ps` shows the `model-hub` service running and healthy.\
2\. On the server, `curl -f http://localhost:3000/ready` returns HTTP `200`.\
3\. From a workstation, `curl -I https://<your-hostname>/health` returns HTTP `200` (`curl.exe` instead of `curl` in Windows PowerShell). If it fails, check the DNS record, the certificate, and the firewall rules between your users and the reverse proxy or load balancer.\
4\. From a workstation, opening `https://<your-hostname>` in a browser loads the Model Hub.

If one of these checks fails, follow [Model Hub installation troubleshooting](ModelHubinstallationtroubleshooting.md).

## Kubernetes and other container platforms

The steps above use Docker Compose. On Kubernetes or another orchestrator, run the same image with the same settings, and give it the two secrets as files, for example from Kubernetes secrets mounted in `/run/secrets`. Configure these probes on port `3000`:

- liveness: HTTP GET on `/health`
- readiness: HTTP GET on `/ready`

Your ingress controller or load balancer then plays the part of the reverse proxy at step 6.

## PostgreSQL in a container, for a trial

For a trial, you can run PostgreSQL in a container in the same Docker Compose file, instead of preparing a database at step 1. Use the Docker Compose file below at step 3, after you create the two secret files at step 2. It uses the official PostgreSQL image and already configures the Model Hub to connect to it. For production, prefer a database that your organization operates and backs up.

**Important:** the database is stored in the named volume `model-hub-db-data`. Keep that volume when you update or recreate the containers, and back it up as described in [Data backup](Databackup.md).

```yaml
services:
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
      - 'model-hub-db-data:/var/lib/postgresql:rw'
    secrets:
      - db_password
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
volumes:
  model-hub-db-data: {}
secrets:
  db_password:
    file: ./secrets/db_password
  model_hub_encryption_key:
    file: ./secrets/model_hub_encryption_key
```

In `DB_CONNECTION`, `postgres` is the name of the database service in this file: Docker Compose resolves it to the database container.

Then continue with steps 4 to 7. [Model Hub with Traefik and Let's Encrypt](Quickstartwithreverseproxy.md) uses the same database setup, with Traefik as the reverse proxy.
