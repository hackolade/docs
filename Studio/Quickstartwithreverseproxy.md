# Quick start with reverse proxy

This guide walks you from an empty Linux server to a working Model Hub environment reachable at *https://\<your-domain-name\>* with a valid Let's Encrypt certificate.

&nbsp;

For this quick start to work, you need the following:

* A domain name you control
* A Linux server with a public IPv4 address
* Inbound access to TCP 80 and 443 from the internet
* Outbound access to Let's Encrypt servers

&nbsp;

&nbsp;

## Create a DNS name that points to the Model Hub server

### Find your server's public IP

On the server, run:

&nbsp;

> curl -4 ifconfig.me

&nbsp;

Or copy the **Public IP** from your cloud provider console (AWS, Azure, GCP, etc.). Write it down, as you will use it in the next step.

&nbsp;

**You are done with this step when:** you know the public IPv4 of the machine that will run Model Hub.

&nbsp;

Let's Encrypt will only issue a certificate if your hostname resolves to this server on the public internet. Do this **before** starting Docker.

&nbsp;

### Pick a hostname

&nbsp;

Choose a subdomain, for example:

&nbsp;

> \* hck.yourcompany.com

&nbsp;

Use that exact name everywhere below (DNS, Traefik config, browser).

&nbsp;

&nbsp;

### Create an A record at your DNS provider

Log in to wherever your DNS is managed (examples: Cloudflare, GoDaddy, Route 53, Azure DNS, Namecheap, Google Domains).

&nbsp;

Open the DNS settings for your domain (e.g. *yourcompany.com*).

&nbsp;

Add a new record:

&nbsp;

| **Field** | **What to enter** |
| --- | --- |
| Type | A |
| Name / Host | *hck* (for *hck.yourcompany.com)* |
| Value / Points to / IPv4 | Your server's **public IPv4** from the checklist |


&nbsp;

Save the record.

&nbsp;

&nbsp;

### Wait and verify DNS

DNS can take a few minutes (sometimes longer). From any machine, check that the name resolves to your server IP:

&nbsp;

> nslookup hck.yourcompany.com

&nbsp;

&nbsp;

The result must be **the same public IP** you set in the A record.

&nbsp;

**Do not continue until this works:**&nbsp; If DNS is wrong, Let's Encrypt will fail, and you may hit rate limits if you keep retrying.

&nbsp;

**You are done with this step when:** *nslookup* returns your server's public IP for your Model Hub hostname.

&nbsp;

&nbsp;

## Edit your Docker Compose file

Deploy Model Hub like described above but edit the Docker Compose shown on that page with the one below. It provides Model Hub and a PostgreSQL database. On top of that, it deploys a reverse proxy ([traefik](<https://traefik.io/traefik> "target=\"\_blank\"")), which automatically generates a certificate with [Let's Encrypt](<https://letsencrypt.org/docs/> "target=\"\_blank\"")

&nbsp;

**Not** that model-hub doesn't expose port 3000 with this configuration anymore. Model Hub will instead be served by the reverse proxy Traefik

&nbsp;

&nbsp;

> services:\
&nbsp; traefik:\
&nbsp; &nbsp; image: traefik:v3.7\
&nbsp; &nbsp; deploy:\
&nbsp; &nbsp; &nbsp; restart\_policy:\
&nbsp; &nbsp; &nbsp; &nbsp; condition: always\
&nbsp; &nbsp; &nbsp; &nbsp; delay: 5s\
&nbsp; &nbsp; &nbsp; &nbsp; window: 30s\
&nbsp; &nbsp; ports:\
&nbsp; &nbsp; &nbsp; - 80:80\
&nbsp; &nbsp; &nbsp; - 443:443\
&nbsp; &nbsp; volumes:\
&nbsp; &nbsp; &nbsp; - letsencrypt:/letsencrypt\
&nbsp; &nbsp; configs:\
&nbsp; &nbsp; &nbsp; - source: traefik\_static\
&nbsp; &nbsp; &nbsp; &nbsp; target: /etc/traefik/traefik.yml\
&nbsp; &nbsp; &nbsp; - source: traefik\_dynamic\
&nbsp; &nbsp; &nbsp; &nbsp; target: /etc/traefik/dynamic.yml\
&nbsp; postgres:\
&nbsp; &nbsp; image: hackolade.azurecr.io/postgres/postgres:18.4-alpine\
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
&nbsp; &nbsp; &nbsp; - "model-hub-db-data:/var/lib/postgresql:rw"\
&nbsp; &nbsp; secrets:\
&nbsp; &nbsp; &nbsp; - db\_password\
&nbsp; model-hub:\
&nbsp; &nbsp; image: hackolade/model-hub:${MODEL\_HUB\_VERSION}\
&nbsp; &nbsp; deploy:\
&nbsp; &nbsp; &nbsp; restart\_policy:\
&nbsp; &nbsp; &nbsp; &nbsp; condition: always\
&nbsp; &nbsp; &nbsp; &nbsp; delay: 5s\
&nbsp; &nbsp; &nbsp; &nbsp; window: 30s\
&nbsp; &nbsp; environment:\
&nbsp; &nbsp; &nbsp; DB\_TYPE: pg\
&nbsp; &nbsp; &nbsp; DB\_CONNECTION: pg://postgres:5432/hck\_hub\
&nbsp; &nbsp; &nbsp; DB\_USERNAME: hck\_hub\
&nbsp; &nbsp; &nbsp; DB\_PASSWORD\_FILE: /run/secrets/db\_password\
&nbsp; &nbsp; &nbsp; CURRENT\_ENCRYPTION\_KEY\_FILE: /run/secrets/model\_hub\_encryption\_key\
&nbsp; &nbsp; secrets:\
&nbsp; &nbsp; &nbsp; - db\_password\
&nbsp; &nbsp; &nbsp; - model\_hub\_encryption\_key\
networks:\
&nbsp; default:\
&nbsp; &nbsp; name: hub\
volumes:\
&nbsp; letsencrypt: {}\
&nbsp; model-hub-db-data: {}\
configs:\
&nbsp; traefik\_static:\
&nbsp; &nbsp; content: \|\
&nbsp; &nbsp; &nbsp; # Traefik static configuration.\
&nbsp; &nbsp; &nbsp; # Edit REPLACE\_WITH\_YOUR\_EMAIL before starting the stack.\
&nbsp; &nbsp; &nbsp; # Do NOT redirect HTTP→HTTPS on the web entrypoint — that breaks Let's Encrypt HTTP-01.

> \
&nbsp; &nbsp; &nbsp; entryPoints:\
&nbsp; &nbsp; &nbsp; &nbsp; web:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; address: ":80"\
&nbsp; &nbsp; &nbsp; &nbsp; websecure:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; address: ":443"\
&nbsp; &nbsp; &nbsp; providers:\
&nbsp; &nbsp; &nbsp; &nbsp; file:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; filename: /etc/traefik/dynamic.yml\
&nbsp; &nbsp; &nbsp; certificatesResolvers:\
&nbsp; &nbsp; &nbsp; &nbsp; letsencrypt:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; acme:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; email: ${CERTIFICATE\_EMAIL}\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; storage: /letsencrypt/acme.json\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; httpChallenge:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; entryPoint: web\
&nbsp; traefik\_dynamic:\
&nbsp; &nbsp; content: \|\
&nbsp; &nbsp; &nbsp; # All traffic that reaches Traefik is proxied to Model Hub.\
&nbsp; &nbsp; &nbsp; # Replace hck.example.com under tls.domains — used only for the Let's Encrypt certificate.\
&nbsp; &nbsp; &nbsp; # HTTP→HTTPS redirect is a router middleware (ACME challenge on :80 still works).\
&nbsp; &nbsp; &nbsp; http:\
&nbsp; &nbsp; &nbsp; &nbsp; middlewares:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; redirect-to-https:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; redirectScheme:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; scheme: https\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; permanent: true\
&nbsp; &nbsp; &nbsp; &nbsp; routers:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; http-to-https:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rule: PathPrefix(\`/\`)\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; entryPoints:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - web\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; middlewares:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - redirect-to-https\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; service: model-hub\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; model-hub:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rule: PathPrefix(\`/\`)\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; entryPoints:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - websecure\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; service: model-hub\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; tls:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; certResolver: letsencrypt\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; domains:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - main: ${HCK\_DOMAIN\_NAME}\
&nbsp; &nbsp; &nbsp; &nbsp; services:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; model-hub:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; loadBalancer:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; servers:\
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; - url: http://model-hub:3000\
secrets:\
&nbsp; db\_password:\
&nbsp; &nbsp; file: ./secrets/db\_password\
&nbsp; model\_hub\_encryption\_key:\
&nbsp; &nbsp; file: ./secrets/model\_hub\_encryption\_key

&nbsp;

&nbsp;

&nbsp;

**Note:** also make sure that the volume \`letsencrypt\` is configured like shown in the example. This allows you to store the certificate on the server to avoid losing it on restarts.

&nbsp;

Create a \`.env\` in the same folder as the compose file, similar to the one below, and fill it with your information

&nbsp;

> MODEL\_HUB\_VERSION: REPLACE\_WITH\_MODEL\_HUB\_VERSION\
CERTIFICATE\_EMAIL: REPLACE\_WITH\_YOUR\_EMAIL\
HCK\_DOMAIN\_NAME: REPLACE\_WITH\_YOUR\_DOMAIN

&nbsp;

&nbsp;

where:&nbsp;

&#49;. change the value of *MODEL\_HUB\_VERSION* with the version you want to deploy from [DockerHub](<https://hub.docker.com/r/hackolade/model-hub> "target=\"\_blank\"")

&#50;. change the value of *REPLACE\_WITH\_YOUR\_EMAIL* with a real email address. This email address will be used to link it to the generated certificate.

&#51;. change the value of *REPLACE\_WITH\_YOUR\_DOMAIN* with the exact DNS name from Step 1.

&nbsp;

&nbsp;

&nbsp;

