# Install and start the server

## Overview

The Hackolade Model Hub is delivered as a Docker image that you run on a server. Once started, users access the Model Hub from a browser to navigate the data models with capabilities to search, browse, drill-down, where-used, lineage, etc. The source-of-truth remains the Git repositories where the data models are maintained.

&nbsp;

You can deploy the Model Hub with Docker Compose, Kubernetes, or any orchestrator that runs containers. For a straightforward first installation, [Docker Compose](<https://docs.docker.com/compose/> "target=\"_blank\"") is recommended.

&nbsp;

This page explains what each component does and how to configure a typical deployment to connect to a database controlled by the customer while external to the Model Hub container.

&nbsp;

### What gets deployed?

A Model Hub installation is made of standard components, with a secrets vault:

&nbsp;

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
<td>The Model Hub application. Serves the web UI and APIs. Users connect to this process (default port `3000`)</td>
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

&nbsp;

![Model Hub installation components](<lib/Model Hub installation components.png>)

&nbsp;

### Pull images

Each new version of Model Hub is published on [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\""). You may specify the version to pull with

&nbsp;

```bash
export MODEL_HUB_VERSION=<target-model-hub-version>
docker pull hackolade/model-hub:$MODEL_HUB_VERSION
```

&nbsp;

The database can be self-standing (installed on a host) or packaged as a container image. The app server and the database can be on separate machines.

&nbsp;

## Quick start with Docker Compose and self-standing PostgreSQL database

The example below deploys the Model Hub application against an external PostgreSQL database. For a quick start with PostgreSQL deployed on the same server, check the instructions in the next section below.

&nbsp;

### 1. Create the project layout

```text
model-hub-deploy/
├── .env
├── docker-compose.yml
└── secrets/
    └── db_password                       # the database password
    └── model_hub_encryption_key          # the encryption key
```

&nbsp;

Create the password file and do not commit it to source control.

&nbsp;

The encryption key needs to be a 64-character hex string. This encryption key is used to encrypt sensitive information like your Git Provider configuration in the database

&nbsp;

To generate one, you can run the following command:

&nbsp;

```bash
openssl rand -hex 32
```

&nbsp;

### 2. Example of docker-compose.yml

Update DB_CONNECTION (and, if needed, DB_USERNAME) so they match your database host, port, database name, and user.

&nbsp;

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
networks:
  default:
    name: hub
secrets:
  db_password:
    file: ./secrets/db_password
  model_hub_encryption_key:
    file: ./secrets/model_hub_encryption_key
```

&nbsp;

where:

&nbsp;

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
<td><pre><code class="language-text">Port 3000</code></pre></td>
<td>Default HTTP port of the Model Hub process.</td>
</tr>
<tr>
<td><pre><code class="language-text">CURRENT_ENCRYPTION_KEY_FILE</code></pre></td>
<td>Path inside the container to a file containing the encryption key</td>
</tr>
</tbody>
</table>

&nbsp;

### 3. Edit the .env variable

The .env file supplies values to Docker Compose substitution. Change the value of *MODEL_HUB_VERSION* with the version you want to deploy from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"_blank\"").

&nbsp;

```text
MODEL_HUB_VERSION=REPLACE_WITH_MODEL_HUB_VERSION
```

&nbsp;

### 4. Start the stack

From the directory that contains docker-compose.yml

&nbsp;

```bash
docker compose up -d
```

&nbsp;

What happens:\
1\. The model-hub container starts and listens on port 3000\
2\. When the container starts, it creates the database structure that it needs to run properly.\
3\. Once the setup is done, the application is ready to be used.

&nbsp;

Check status

&nbsp;

```bash
docker compose ps
docker compose logs -f model-hub
```

&nbsp;

Open the Model Hub

&nbsp;

```text
http://<server-hostname-or-ip>:3000
```

&nbsp;

It is mandatory to place a reverse proxy in front of the Model Hub and terminate TLS there because Model Hub uses service workers in the browser, which forces the use of HTTPS.. Consult this page for a [quick start setup](Quickstartwithreverseproxy.md).

&nbsp;

### 5. Connect to the database

The Model Hub connects to a self-standing SQL database that you provide. Provision the database first, then point the application at it.

&nbsp;

#### Database checklist

1\. Create an empty database (and schema if required by your standards).\
2\. Create a dedicated user.\
3\. Grant that user permission to create, alter, and delete tables in its schema, and to read/write those tables — see [Pre-requisites](ModelHubprerequisites.md)\
4\. Ensure the Model Hub containers can reach the database host and port.

&nbsp;

#### PostgreSQL

These environment variables must be configured to connect Model Hub with your PostgreSQL database

&nbsp;

```text
DB_TYPE=pg
DB_CONNECTION=pg://<db-host>:5432/<database>
DB_USERNAME=<db-user>
DB_PASSWORD_FILE=/run/secrets/db_password
```

&nbsp;

#### Oracle

These environment variables must be configured to connect Model Hub to your Oracle database

&nbsp;

```text
DB_TYPE=oracledb
DB_USERNAME=<db-user>
DB_PASSWORD_FILE=/run/secrets/db_password
DB_CONNECTION=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=<db-host>)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=<service-name>)))
```

&nbsp;

DB_CONNECTION is an Oracle Connect descriptor (or Easy Connect string).

&nbsp;

Example Compose snippet:

&nbsp;

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

&nbsp;

### 6. Configure health checks

When you run the official Model Hub image with Docker, a health check is already configured. On other platforms (Kubernetes, for example), configure an equivalent probe.

&nbsp;

The Model Hub listens on port *3000* and exposes a */health* endpoint. A successful check is an HTTP \`200\` response from that endpoint.

&nbsp;

Model Hub also exposes a */ready* endpoint. It responds with an HTTP \`200\` when Model Hub is ready to receive requessts.

&nbsp;

Reference health check from the Dockerfile:

&nbsp;

```bash
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node -e 'fetch(`http://localhost:3000/health`).then(x=>x.status===200?process.exit(0):process.exit(1)).catch(()=>process.exit(1))'
```

&nbsp;

Equivalent probes:

- **Kubernetes liveness:** HTTP GET on port *3000*, path */health*
- **Kubernetes readiness:** HTTP GET on port *3000*, path */ready*
- **Load balancer:** HTTP health check on */ready*

&nbsp;

### 7. Verify the installation

1\. *docker compose ps* must show that model-hub running.\
2\. *curl -f http://localhost:3000/health* must return HTTP 200.\
3\. Opening *http://\<host>:3000* in a browser loads the Model Hub UI.

&nbsp;

### 8. Upgrade to new Model Hub version

Always back up the database before upgrading production systems, as described in [Data backup](Databackup.md). At least the tables *git_repositories* and *kvs*.

&nbsp;

1\. Note the new *MODEL_HUB_VERSION* from the Hackolade release notes.\
2\. Pull the matching *model-hub* image with the command

&nbsp;

```bash
docker compose pull
```

&nbsp;

3\. Update *MODEL_HUB_VERSION* in your *.env* file\
4\. then run

&nbsp;

```bash
docker compose up -d
```

&nbsp;

and the application will restart.

&nbsp;

## Quick start with Docker Compose and PostgreSQL

To start quickly with Model Hub, just install a PostgreSQL container within the same Docker Compose file. The example below is ready to be copied into your own server. It uses the official PostgreSQL Docker image and already configures Model Hub to authenticate with it.

&nbsp;

**Attention:** you should also pay attention that there is a named volume *model-hub-db-data* for the database.

&nbsp;

```yaml
services:
  postgres:
    image: postgres/postgres:18.4-alpine
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
    volumes:
      - "model-hub-filestore-data:/home/node/.hub:rw"
    secrets:
      - db_password
networks:
  default:
    name: hub
volumes:
  model-hub-db-data: {}
  model-hub-filestore-data: {}
secrets:
  db_password:
    file: ./secrets/db_password
```

&nbsp;

With this Docker Compose, the next step is to run it:

&nbsp;

```bash
docker compose up -d
```
