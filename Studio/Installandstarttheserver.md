# Install and start the server

## Overview

The Hackolade Model Hub is delivered as a Docker image that you run on a server. Once started, users access the Model Hub from a browser to navigate the data models with capabilities to search, browse, drill-down, where-used, lineage, etc.&nbsp; The source-of-truth remains the Git repositories where the data models are maintained.

&nbsp;

You can deploy the Model Hub with Docker Compose, Kubernetes, or any orchestrator that runs containers.&nbsp; For a straightforward first installation, [Docker Compose](<https://docs.docker.com/compose/> "target=\"\_blank\"") is recommended.

&nbsp;

This page explains what each component does and how to configure a typical deployment to connect to a database controlled by the customer while external to the Model Hub container.

&nbsp;

### What gets deployed?

A Model Hub installation is made of standard components, with a secrets vault:

&nbsp;

| **Component** | **Role** |
| --- | --- |
| model-hub | The Model Hub application. Serves the web UI and APIs. Users connect to this process (default port \`3000\`) |
| Database | An external PostgreSQL or Oracle database that stores Model Hub data. You must provision and operate this database yourself. |
| Secrets | Sensitive values such as the database password and an encryption key for storing sensitive configuration.&nbsp; Prefer Docker secrets (or your platform’s equivalent) over plain environment variables. |


&nbsp;

&nbsp;

&nbsp;

&nbsp;

![Image](<lib/Model Hub installation components.png>)

&nbsp;

### Pull images

Each newx version of Model Hub is published on [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"\_blank\"").&nbsp; You may specify the version to pull with

&nbsp;

> export MODEL\_HUB\_VERSION=\<target-model-hub-version\>\
docker pull hackolade/model-hub:$MODEL\_HUB\_VERSION

&nbsp;

&nbsp;

The database can be self-standing (installed on a host) or packaged as a container image.

## Quick start with Docker Compose and self-standing PostgreSQL database

The example below deploys the Model Hub application against an external PostgreSQL database. For a quick start with PostgreSQL deployed on the same server, check the instructions in the next section below.

&nbsp;

### &#49;. Create the project layout

&nbsp;

> model-hub-deploy/\
├── .env\
├── docker-compose.yml\
└── secrets/\
&nbsp; &nbsp; └── db\_password &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # the database password\
&nbsp; &nbsp; └── model\_hub\_encryption\_key&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # the encryption key

&nbsp;

&nbsp;

Create the password file and do not commit it to source control.

&nbsp;

The encryption key needs to be a 64-character hex string. This encryption key is used to encrypt sensitive information like your Git Provider configuration in the database

&nbsp;

To generate one, you can run the following command:

&nbsp;

> openssl rand -hex 32

&nbsp;

&nbsp;

&nbsp;

### &#50;. Example of docker-compose.yml

Update DB\_CONNECTION (and, if needed, DB\_USERNAME) so they match your database host, port, database name, and user.

&nbsp;

> services:\
&nbsp; model-hub:\
&nbsp; &nbsp; image: hackolade/model-hub:${MODEL\_HUB\_VERSION}\
&nbsp; &nbsp; deploy:\
&nbsp; &nbsp; &nbsp; restart\_policy:\
&nbsp; &nbsp; &nbsp; &nbsp; condition: always\
&nbsp; &nbsp; &nbsp; &nbsp; delay: 5s\
&nbsp; &nbsp; &nbsp; &nbsp; window: 30s\
&nbsp; &nbsp; ports:\
&nbsp; &nbsp; &nbsp; - "3000:3000"\
&nbsp; &nbsp; environment:\
&nbsp; &nbsp; &nbsp; DB\_TYPE: pg\
&nbsp; &nbsp; &nbsp; DB\_CONNECTION: pg://\<db-host\>:5432/\<database\>\
&nbsp; &nbsp; &nbsp; DB\_USERNAME: \<db-user\>\
&nbsp; &nbsp; &nbsp; DB\_PASSWORD\_FILE: /run/secrets/db\_password\
&nbsp; &nbsp; &nbsp; CURRENT\_ENCRYPTION\_KEY\_FILE: /run/secrets/model\_hub\_encryption\_key\
&nbsp; &nbsp; secrets:\
&nbsp; &nbsp; &nbsp; - db\_password\
&nbsp; &nbsp; &nbsp; - model\_hub\_encryption\_key\
networks:\
&nbsp; default:\
&nbsp; &nbsp; name: hub\
secrets:\
&nbsp; db\_password:\
&nbsp; &nbsp; file: ./secrets/db\_password\
&nbsp; model\_hub\_encryption\_key:\
&nbsp; &nbsp; file: ./secrets/model\_hub\_encryption\_key

&nbsp;

&nbsp;

where:

| **Setting** | **Meaning** |
| --- | --- |
| DB\_TYPE | Database driver. Use pg for PostgreSQL or oracledb for Oracle. |
| DB\_CONNECTION | How the application reaches the database. Format depends on the database (see below). |
| DB\_USERNAME | Database user |
| DB\_PASSWORD\_FILE | Path inside the container to a file containing the password. |
| Port 3000 | Default HTTP port of the Model HUB process. |
| CURRENT\_ENCRYPTION\_KEY\_FILE | Path inside the container to a file containing the encryption key |


&nbsp;

&nbsp;

### &#51;. Edit the .env variable

The .env file supplies values to Docker Compose substitution.&nbsp; Change the value of *MODEL\_HUB\_VERSION* with the version you want to deploy from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"\_blank\"").

&nbsp;

> MODEL\_HUB\_VERSION: REPLACE\_WITH\_MODEL\_HUB\_VERSION

&nbsp;

&nbsp;

### &#52;. Start the stack

From the directory that contains docker-compose.yml

&nbsp;

> docker compose up -d

&nbsp;

&nbsp;

What happens:

&#49;. The model-hub container starts and listens on port 3000

&#50;. When the container starts, it creates the database structure that it needs to run properly.

&#51;. Once the setup is done, the application is ready to be used.

&nbsp;

&nbsp;

Check status

&nbsp;

> docker compose ps\
docker compose logs -f model-hub

&nbsp;

&nbsp;

Open the Model Hub

&nbsp;

> http://\<server-hostname-or-ip\>:3000

&nbsp;

It is mandatory to place a reverse proxy in front of the Model Hub and terminate TLS there because Model Hub uses service workers in the browser, which forces the use of HTTPS.. Consult this page for a [quick start setup](<Quickstartwithreverseproxy.md>).

&nbsp;

&nbsp;

### &#53;. Connect to the database

The Model Hub connects to a self-standing SQL database that you provide. Provision the database first, then point the application at it.

&nbsp;

#### Database checklist

&#49;. Create an empty database (and schema if required by your standards).

&#50;. Create a dedicated user.

&#51;. Grant that user permission to create, alter, and delete tables in its schema, and to read/write those tables — see [Pre-requisites](<ModelHubprerequisites.md>)

&#52;. Ensure the Model HUB containers can reach the database host and port.

&nbsp;

#### PostgreSQL

These environment variables must be configured to connect Model HUB with your PostgreSQL database

&nbsp;

> DB\_TYPE=pg\
DB\_CONNECTION=pg://\<db-host\>:5432/\<database\>\
DB\_USERNAME=\<db-user\>\
DB\_PASSWORD\_FILE=/run/secrets/db\_password

&nbsp;

#### Oracle

These environment variables must be configured to connect Model HUB to your Oracle database

&nbsp;

> DB\_TYPE=oracledb\
DB\_USERNAME=\<db-user\>\
DB\_PASSWORD\_FILE=/run/secrets/db\_password\
DB\_CONNECTION=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=\<db-host\>)(PORT=1521))(CONNECT\_DATA=(SERVICE\_NAME=\<service-name\>)))

&nbsp;

&nbsp;

DB\_CONNECTION is an Oracle Connect descriptor (or Easy Connect string).

&nbsp;

&nbsp;

Example Compose snippet:

&nbsp;

> model-hub:\
&nbsp; image: hackolade/model-hub:$MODEL\_HUB\_VERSION\
&nbsp; environment:\
&nbsp; &nbsp; DB\_TYPE: oracledb\
&nbsp; &nbsp; DB\_USERNAME: \<db-user\>\
&nbsp; &nbsp; DB\_PASSWORD\_FILE: /run/secrets/db\_password\
&nbsp; &nbsp; DB\_CONNECTION: "(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=\<db-host\>)(PORT=1521))(CONNECT\_DATA=(SERVICE\_NAME=\<service-name\>)))"\
&nbsp; &nbsp; CURRENT\_ENCRYPTION\_KEY\_FILE: /run/secrets/model\_hub\_encryption\_key\
&nbsp; secrets:\
&nbsp; &nbsp; - db\_password\
&nbsp; &nbsp; - model\_hub\_encryption\_key

&nbsp;

&nbsp;

### &#54;. Configure health checks

When you run the official Model Hub image with Docker, a health check is already configured. On other platforms (Kubernetes, for example), configure an equivalent probe.

&nbsp;

The Model Hub listens on port *3000* and exposes a */health* endpoint. A successful check is an HTTP \`200\` response from that endpoint.

&nbsp;

Model Hub also exposes a */ready* endpoint. It responds with an HTTP \`200\` when Model Hub is ready to receive requessts.

&nbsp;

Reference health check from the Dockerfile:

&nbsp;

> HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \\\
&nbsp; CMD node -e 'fetch(\`http://localhost:3000/health\`).then(x=\>x.status===200?process.exit(0):process.exit(1)).catch(()=\>process.exit(1))'

&nbsp;

&nbsp;

Equivalent probes:

&nbsp;

* **Kubernetes liveness:** HTTP GET on port *3000*, path */health*
* **Kubernetes readiness:** HTTP GET on port *3000*, path */ready*
* **Load balancer:** HTTP health check on */ready*

&nbsp;

&nbsp;

### &#55;. Verify the installation

&nbsp;

&#49;. *docker compose ps* must show that model-hub running.

&#50;. *curl -f http://localhost:3000/health* must return HTTP 200.

&#51;. Opening *http://\<host\>:3000* in a browser loads the Model Hub UI.

&nbsp;

&nbsp;

### &#56;. Stop and upgrade

#### Stop (keep the filestore volume)

&nbsp;

> docker compose down

&nbsp;

**Warning**: do not use the flag to delete volumes, which would delete filestore data.

&nbsp;

#### Upgrade

&nbsp;

&#49;. Always back up the database before upgrading production systems, as described in [Data backup](<Databackup.md>)

&#50;. Note the new *MODEL\_HUB\_VERSION* from the Hackolade release notes.

&#51;. Pull the matching model-hub image.

&#52;. Update *MODEL\_HUB\_VERSION* in your *.env* file then run

&nbsp;

> docker compose up -d&nbsp;

&nbsp;

and the application will restart.

&nbsp;

&nbsp;

&nbsp;

## Quick start with Docker Compose and PostgreSQL

To start quickly with Model Hub, just install a PostgreSQL container within the same Docker Compose file. The example below is ready to be copied into your own server. It uses the official PostgreSQL Docker image and already configures Model Hub to authenticate with it.

&nbsp;

**Attention:** you should also pay attention that there is a named volume *model-hub-db-data* for the database.

&nbsp;

&nbsp;

> services:\
&nbsp; postgres:\
&nbsp; &nbsp; image: postgres/postgres:18.4-alpine\
&nbsp; &nbsp; deploy:\
&nbsp; &nbsp; &nbsp; restart\_policy:\
&nbsp; &nbsp; &nbsp; &nbsp; condition: always\
&nbsp; &nbsp; &nbsp; &nbsp; delay: 5s\
&nbsp; &nbsp; &nbsp; &nbsp; window: 30s\
&nbsp; &nbsp; environment:\
&nbsp; &nbsp; &nbsp; POSTGRES\_USER: hck\_hub\
&nbsp; &nbsp; &nbsp; POSTGRES\_PASSWORD\_FILE: /run/secrets/db\_password\
&nbsp; &nbsp; &nbsp; POSTGRES\_DB: hck\_hub\
&nbsp; &nbsp; healthcheck:\
&nbsp; &nbsp; &nbsp; test: \["CMD-SHELL", "pg\_isready -U hck\_hub -d hck\_hub"\]\
&nbsp; &nbsp; &nbsp; interval: 30s\
&nbsp; &nbsp; &nbsp; timeout: 5s\
&nbsp; &nbsp; &nbsp; retries: 10\
&nbsp; &nbsp; &nbsp; start\_period: 5s\
&nbsp; &nbsp; volumes:\
&nbsp; &nbsp; &nbsp; - 'model-hub-db-data:/var/lib/postgresql:rw'\
&nbsp; &nbsp; secrets:\
&nbsp; &nbsp; &nbsp; - db\_password\
&nbsp; model-hub:\
&nbsp; &nbsp; image: hackolade/model-hub:${MODEL\_HUB\_VERSION}\
&nbsp; &nbsp; deploy:\
&nbsp; &nbsp; &nbsp; restart\_policy:\
&nbsp; &nbsp; &nbsp; &nbsp; condition: always\
&nbsp; &nbsp; &nbsp; &nbsp; delay: 5s\
&nbsp; &nbsp; &nbsp; &nbsp; window: 30s\
&nbsp; &nbsp; ports:\
&nbsp; &nbsp; &nbsp; - "3000:3000"\
&nbsp; &nbsp; environment:\
&nbsp; &nbsp; &nbsp; DB\_TYPE: pg\
&nbsp; &nbsp; &nbsp; DB\_CONNECTION: pg://postgres:5432/hck\_hub\
&nbsp; &nbsp; &nbsp; DB\_USERNAME: hck\_hub\
&nbsp; &nbsp; &nbsp; DB\_PASSWORD\_FILE: /run/secrets/db\_password\
&nbsp; &nbsp; volumes:\
&nbsp; &nbsp; &nbsp; - "model-hub-filestore-data:/home/node/.hub:rw"\
&nbsp; &nbsp; secrets:\
&nbsp; &nbsp; &nbsp; - db\_password\
networks:\
&nbsp; default:\
&nbsp; &nbsp; name: hub\
volumes:\
&nbsp; model-hub-db-data: {}\
&nbsp; model-hub-filestore-data: {}\
secrets:\
&nbsp; db\_password:\
&nbsp; &nbsp; file: ./secrets/db\_password

&nbsp;

&nbsp;

With this Docker Compose, the next step is to run it:

&nbsp;

> docker compose up -d

&nbsp;

&nbsp;

