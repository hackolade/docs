---
description: Checks to run when the Model Hub does not start or users cannot open it, which logs and information to send to Hackolade support, and what never to send.
seoTitle: Troubleshoot Hackolade Model Hub
---
# Model Hub installation troubleshooting

Most installation problems come from the network, DNS, the certificate or the database connection, not from the Model Hub itself. Run the checks below first: they often show the cause in a few minutes. If they do not, send us the information listed in [Information to send to support](<https://hackolade.com/help/ModelHubinstallationtroubleshooting.html#Information%20to%20send%20to%20support>), and nothing more.

The examples use `hck.example.com` as the hostname of your Model Hub; replace it with yours.

## Checks to run first

Run the checks in this order. Each one assumes that the previous one passes:

1. **The Hackolade Helpdesk has confirmed your hostname** and sent you the Model Hub license key, as described in [Model Hub prerequisites](<https://hackolade.com/help/ModelHubprerequisites.html#1.%20Register%20your%20hostname%20with%20the%20Hackolade%20Helpdesk>). Until then, the license check fails, whatever you fix in your setup.
2. **The Model Hub runs.** On the server, in the folder of your `docker-compose.yml`, `docker compose ps` shows the `model-hub` service running and healthy.
3. **The Model Hub is ready.** On the server, `curl -f http://localhost:3000/ready` returns HTTP `200`. If it does not, read the logs, as described in [Collect the logs](<https://hackolade.com/help/ModelHubinstallationtroubleshooting.html#Collect%20the%20logs>).
4. **The hostname resolves.** From the workstation of one of your users, `nslookup hck.example.com` returns the address of your reverse proxy or load balancer.
5. **The Model Hub answers over HTTPS.** From the same workstation, `curl -I https://hck.example.com/health` returns HTTP `200`, without a certificate error. In Windows PowerShell, type `curl.exe` instead of `curl`.
6. **The browser opens the Model Hub.** Open `https://hck.example.com`, with the hostname: not an IP address, not `localhost`, and not the load balancer's own DNS name.

## Common problems

### Users cannot open the Model Hub, but it answers on the server

`curl` on the server only shows that the container runs. Your users go through DNS, your firewall or security groups, and your reverse proxy or load balancer. Run checks 4 and 5 from a workstation to find which one stops them.

The Model Hub needs a reverse proxy or a load balancer that serves it over HTTPS on your hostname, as explained in [How users reach the Model Hub](<https://hackolade.com/help/Installandstarttheserver.html#How%20users%20reach%20the%20Model%20Hub>). Follow the guide for your environment, listed in [Choose how to deploy](<https://hackolade.com/help/Installandstarttheserver.html#Choose%20how%20to%20deploy>).

### The page loads, but the license check fails

Check that:

- you opened the Model Hub over HTTPS, with the hostname that you gave the Hackolade Helpdesk
- the Hackolade Helpdesk has confirmed that hostname
- the server reaches the licensing servers over HTTPS, as listed in [Model Hub prerequisites](<https://hackolade.com/help/ModelHubprerequisites.html#Network%20requirements>)

### The Model Hub restarts in a loop

Read the logs, as described in [Collect the logs](<https://hackolade.com/help/ModelHubinstallationtroubleshooting.html#Collect%20the%20logs>). The cause follows the message `Failed to start server`; look for one of these:

- `KVS encryption key is required`: `CURRENT_ENCRYPTION_KEY_FILE` is missing from `docker-compose.yml`, or the file it names is missing.
- `Invalid KVS encryption key`: the key file must hold a 64-character hex string, as created with `openssl rand -hex 32`. If the Model Hub already stored its configuration with a key, use that same key.
- `ECONNREFUSED` to the database: the database host or port is wrong, or the database does not accept connections from the Model Hub server. Inside the container, `localhost` is the container itself, not your server. For PostgreSQL installed on the server itself, see [PostgreSQL on the same server](<https://hackolade.com/help/ModelHubonyourownserver.html#PostgreSQL%20on%20the%20same%20server>).
- `ENOTFOUND` for the database host: the server cannot resolve the database hostname.
- `no pg_hba.conf entry` with `no encryption`, or a message that SSL is required: add `?sslmode=require` at the end of `DB_CONNECTION`.
- `self-signed certificate in certificate chain`: the database certificate comes from an authority that the Model Hub does not trust by default, as with Amazon RDS. [Model Hub on Amazon EC2](<https://hackolade.com/help/ModelHubonAmazonEC2.html#6.%20Start%20the%20Model%20Hub>) shows how to add it.
- `password authentication failed`: the database user or the content of the password file is wrong.
- `permission denied for database`: the database user must own the database, as described in [Prepare the database](<https://hackolade.com/help/ModelHubonyourownserver.html#1.%20Prepare%20the%20database>).

### The certificate is missing with Traefik and Let's Encrypt

Let's Encrypt checks your hostname from the internet before it issues the certificate. The DNS record must point to your server, and port 80 must be open from the internet. [Model Hub with Traefik and Let's Encrypt](<https://hackolade.com/help/Quickstartwithreverseproxy.html#Start%20and%20verify>) shows how to read the reason in the Traefik logs.

## Collect the logs

The Model Hub writes all its logs to the standard output of its container. On the server, in the folder of your `docker-compose.yml`, save them to a file:

```bash
docker compose logs --no-color --timestamps model-hub > model-hub.log
```

To keep only the last hour, add `--since 1h`. On Kubernetes, use `kubectl logs <pod-name> > model-hub.log`, and add `--previous` when the pod restarts in a loop.

For a problem in the browser, take a screenshot of the page with the address bar visible, and one of the errors in the browser console (press **F12**, then open the **Console** tab).

The logs contain IP addresses and identifiers of your users. Look through the file before you send it, and remove any line that you do not want to share.

## Information to send to support

Write to [support@hackolade.com](mailto:support@hackolade.com) with:

- the Model Hub version, from your `.env` file
- where the Model Hub runs: your cloud provider or your own servers, and Docker Compose or Kubernetes
- the hostname that you gave the Hackolade Helpdesk
- what serves the Model Hub over HTTPS, such as Traefik, nginx, an AWS Application Load Balancer or an Azure Application Gateway, and where its certificate comes from
- the database: PostgreSQL or Oracle, its version, and whether it is a managed service, a server of its own, or on the Model Hub server
- the results of the [checks to run first](<https://hackolade.com/help/ModelHubinstallationtroubleshooting.html#Checks%20to%20run%20first>), with the full output of the first one that fails
- what you see, with the date, time and time zone when it happened
- the `model-hub.log` file and your screenshots
- your `docker-compose.yml`: with secret files, it holds no password; if you wrote passwords in it, remove them first

## What not to send

Never send us:

- the files of your `secrets` folder: the database password and the encryption key
- passwords, access tokens and client secrets, such as those of your database, Git provider, Microsoft Entra ID or Okta
- private keys, such as SSH or PuTTY keys and the private keys of your TLS certificates
- connection strings that contain a password, for any database
- data models, notes or other files that are not about the problem

When a file holds both useful and secret lines, copy only the useful lines into your message.

> [!WARNING]
> If you sent us a secret by mistake, consider it exposed: revoke or change it, then tell us, so that we delete it.
