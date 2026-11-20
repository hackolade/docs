---
description: Install Hackolade Model Hub as a Docker image with Docker Compose and a PostgreSQL database, then start the server.
seoTitle: Install and start the Model Hub server
---
# Install and start the server

## Overview

The Hackolade Model Hub is delivered as a Docker image that you run on a server. Once started, users access the Model Hub from a browser to navigate the data models with capabilities to search, browse, drill-down, where-used, lineage, etc. The source-of-truth remains the Git repositories where the data models are maintained.

You can deploy the Model Hub with Docker Compose, Kubernetes, or any orchestrator that runs containers. For a straightforward first installation, [Docker Compose](<https://docs.docker.com/compose/> "target=\"_blank\"") is recommended.

This page explains what each component does and how to configure a typical deployment to connect to a database controlled by the customer while external to the Model Hub container.

For a complete example on a cloud provider, from the network to the HTTPS address your users open, follow [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) or [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md).

### What gets deployed?

A Model Hub installation is made of standard components, with a secrets vault:

<table style="width:80%">
<colgroup><col style="width:11%"><col style="width:89%"></colgroup>
<thead>
<tr>
<th>Component</th>
<th>Role</th>
</tr>
</thead>
<tbody>
<tr>
<td>model-hub</td>
<td>The Model Hub application. Serves the web UI and APIs on port `3000`, behind your reverse proxy or load balancer.</td>
</tr>
<tr>
<td>Database</td>
<td>An external PostgreSQL or Oracle database that stores Model Hub data. You must provision and operate this database yourself.</td>
</tr>
<tr>
<td>Secrets</td>
<td><p>Sensitive values such as the database password and an encryption key for storing sensitive configuration.</p><p>Prefer Docker secrets (or your platform’s equivalent) over plain environment variables.</p></td>
</tr>
</tbody>
</table>

![Model Hub installation components](<lib/Model Hub installation components.png>)

### How users reach the Model Hub

Your users open the Model Hub in their browser at `https://<your-hostname>`, the hostname you gave the Hackolade Helpdesk as described in [Model Hub prerequisites](ModelHubprerequisites.md). A reverse proxy or a load balancer in front of the Model Hub holds the TLS certificate for that hostname and forwards the requests to port `3000` of the container.

HTTPS is mandatory: the Model Hub uses service workers in the browser, and browsers allow them only on HTTPS pages. If you open `http://<server-ip>:3000` from your workstation, the page loads but the license check fails. Always use the hostname, not an IP address or the load balancer's own name, as the Hackolade Helpdesk configures domain locking for that hostname.

### Pull images

Each new version of Model Hub is published on [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\""). You may specify the version to pull with

```bash
export MODEL_HUB_VERSION=<target-model-hub-version>
docker pull hackolade/model-hub:$MODEL_HUB_VERSION
```

## Quick start with Docker Compose and self-standing PostgreSQL database

The example below deploys the Model Hub application against an external PostgreSQL database. To run PostgreSQL in a container next to the Model Hub instead, see [Quick start with Docker Compose and PostgreSQL](<https://hackolade.com/help/Installandstarttheserver.html#Quick%20start%20with%20Docker%20Compose%20and%20PostgreSQL>).

### 1. Prepare the database

The Model Hub uses a database that you provide. Prepare it before you start the Model Hub.

#### Database checklist

1\. Create an empty database.\
2\. Create a dedicated user.\
3\. Grant that user permission to create, alter, and delete tables in its schema, and to read/write those tables, as described in [Model Hub prerequisites](ModelHubprerequisites.md).\
4\. Ensure the Model Hub containers can reach the database host and port.

#### PostgreSQL

On PostgreSQL, the Model Hub creates its own `hck_hub` schema in the database, so its user must own the database. Connected to your PostgreSQL server as an administrator, run:

```sql
CREATE ROLE hck_hub WITH LOGIN PASSWORD '<database-password>';
GRANT hck_hub TO CURRENT_USER;
CREATE DATABASE hck_hub OWNER hck_hub;
```

The `GRANT` line lets an administrator who is not a superuser, such as the administrator of a managed database on AWS or Azure, create a database owned by the `hck_hub` user.

When your database requires encrypted connections, which is the default for managed PostgreSQL services, add `?sslmode=require` to `DB_CONNECTION` at step 3: `pg://<db-host>:5432/<database>?sslmode=require`. The Model Hub then checks the certificate of the database server against the usual public certificate authorities. For a certificate signed by another authority, such as Amazon RDS, see [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md).

#### PostgreSQL on the same server

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

#### Oracle

In `docker-compose.yml` at step 3, set `DB_TYPE` to `oracledb`, and `DB_CONNECTION` to an Oracle Connect descriptor or Easy Connect string:

```yaml
model-hub:
  image: hackolade/model-hub:$MODEL_HUB_VERSION
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

### 2. Create the project layout

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

### 3. Create docker-compose.yml

Update `DB_CONNECTION` (and, if needed, `DB_USERNAME`) so they match your database host, port, database name, and user. The host is the database server as seen from inside the container: `localhost` there is the container itself, not your server. For a PostgreSQL installed on the same server outside Docker, see [PostgreSQL on the same server](<https://hackolade.com/help/Installandstarttheserver.html#PostgreSQL%20on%20the%20same%20server>).

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
<td>Port 3000</td>
<td>Default HTTP port of the Model Hub process. Your reverse proxy or load balancer forwards requests to this port.</td>
</tr>
</tbody>
</table>

### 4. Create the .env file

The `.env` file gives Docker Compose the Model Hub version to deploy. Set `MODEL_HUB_VERSION` to a version from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\"").

```text
MODEL_HUB_VERSION=<model-hub-version>
```

### 5. Start the Model Hub

From the folder that contains `docker-compose.yml`, run:

```bash
docker compose up -d
```

What happens:\
1\. The model-hub container starts and listens on port 3000\
2\. When the container starts, it creates the database structure that it needs to run properly.\
3\. Once the setup is done, the application is ready to be used.

Check its status:

```bash
docker compose ps
docker compose logs -f model-hub
```

Check from the server that the Model Hub answers:

```bash
curl -f http://localhost:3000/ready
```

Users cannot use the Model Hub until a reverse proxy or a load balancer serves it over HTTPS on your hostname, as explained in [How users reach the Model Hub](<https://hackolade.com/help/Installandstarttheserver.html#How%20users%20reach%20the%20Model%20Hub>). For a server reachable from the internet, follow [Quick start with reverse proxy](Quickstartwithreverseproxy.md). On a cloud provider, follow [Model Hub on Amazon EC2](ModelHubonAmazonEC2.md) or [Model Hub on an Azure virtual machine](ModelHubonanAzurevirtualmachine.md).

### 6. Configure health checks

When you run the official Model Hub image with Docker, a health check is already configured. On other platforms (Kubernetes, for example), configure an equivalent probe.

The Model Hub listens on port *3000* and exposes a */health* endpoint. A successful check is an HTTP `200` response from that endpoint.

Model Hub also exposes a */ready* endpoint. It responds with an HTTP `200` when Model Hub is ready to receive requests.

Reference health check from the Dockerfile:

```bash
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node -e 'fetch(`http://localhost:3000/health`).then(x=>x.status===200?process.exit(0):process.exit(1)).catch(()=>process.exit(1))'
```

Equivalent probes:

- **Kubernetes liveness:** HTTP GET on port *3000*, path */health*
- **Kubernetes readiness:** HTTP GET on port *3000*, path */ready*
- **Load balancer:** HTTP health check on */ready*

### 7. Verify the installation

1\. On the server, `docker compose ps` shows the `model-hub` service running and healthy.\
2\. On the server, `curl -f http://localhost:3000/ready` returns HTTP `200`.\
3\. From a workstation, `curl -I https://<your-hostname>/health` returns HTTP `200` (`curl.exe` instead of `curl` in Windows PowerShell). If it fails, check the DNS record, the certificate, and the firewall rules between your users and the reverse proxy or load balancer.\
4\. From a workstation, opening `https://<your-hostname>` in a browser loads the Model Hub.

### 8. Upgrade to new Model Hub version

Always back up the database before upgrading production systems, as described in [Data backup](Databackup.md). At least the tables *git_repositories* and *kvs*.

1\. Note the new version from the Hackolade release notes.\
2\. Update `MODEL_HUB_VERSION` in your `.env` file.\
3\. Pull the new image and restart the Model Hub:

```bash
docker compose pull
docker compose up -d
```

## Quick start with Docker Compose and PostgreSQL

To start quickly with Model Hub, run PostgreSQL in a container within the same Docker Compose file. The example below is ready to be copied into your own server. It uses the official PostgreSQL Docker image and already configures Model Hub to authenticate with it. Create the two secret files as described in [Create the project layout](<https://hackolade.com/help/Installandstarttheserver.html#2.%20Create%20the%20project%20layout>) first.

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

With this Docker Compose, the next step is to run it:

```bash
docker compose up -d
```

Then put a reverse proxy in front of it, as described in [Quick start with reverse proxy](Quickstartwithreverseproxy.md), which uses the same database setup.
