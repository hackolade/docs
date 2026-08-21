# Monitoring and alerting

You can operate the Model Hub like any other production web service: watch process health, resources, logs, and model-sync failures.

&nbsp;

## Health checks and readiness

The Model Hub process listens on port *3000* and exposes a *GET /health* and *GET /ready* endpoint. A successful check is an HTTP *200* response.

&nbsp;

Use this endpoint for:

* Docker / Compose health checks (already defined in the official image)
* Kubernetes liveness and readiness probes
* Load balancer health checks

&nbsp;

See Install and start the server for the reference health-check command.

&nbsp;

Also monitor the **database migration** job on install and upgrade. A non-zero exit from *model-hub-\*-database-migration* would mean that the schema was not applied successfully; do not ignore failed migration containers.

&nbsp;

## Resource metrics

Collect at least:

&nbsp;

* CPU and memory usage for the *model-hub* container (or pod)
* Disk usage for the filestore volume (/home/node/.hub)
* Database CPU, storage, connection count, and free space (on the external PostgreSQL or Oracle instance)

&nbsp;

Alert when the Model Hub container restarts repeatedly, when memory grows without bound under sync load, or when the filestore volume is close to full.

&nbsp;

## Logs

&nbsp;

The Model HUB writes \*\*JSON logs\*\* to the container’s standard output (stdout). Ship them to your central logging platform.

&nbsp;

You will see:

* Access / request logs for HTTP traffic
* Warning and error logs for unexpected conditions (for example database connectivity problems or Git provider failures)

&nbsp;

&nbsp;

Useful alert ideas on log streams:

* Spikes in HTTP \*\*5xx\*\* responses
* Repeated \*\*401\*\* / \*\*403\*\* after authentication was enabled (often an IdP or redirect URI misconfiguration)
* Messages indicating database connection or pool errors
* Messages indicating Git provider or webhook processing failures

&nbsp;

&nbsp;

## Model sync errors

When the Model Hub fails to process a webhook or to sync a model file, it records the failure in the \`sync\_errors\` table in the Model HUB database. Monitor this table in addition to logs.

&nbsp;

&nbsp;

### Useful columns

&nbsp;

| **Column** | **Meaning** |
| --- | --- |
| *error\_type* | *webhook\_error*&nbsp; failure when the Git provider called the webhook endpoint; model\_sync failure while processing model files |
| *error\_message* | Human-readable error text for troubleshooting |
| *created\_at* | When the error was recorded |
| *git\_request\_id* | Identifier from the Git provider webhook, when available |
| *git\_provider* | Provider that triggered the sync |
| *repository\_name* | Repository involved, when available |
| *branch\_name* | Branch involved, when available |
| *model\_path* | Model file path involved, when available |
| *http\_status\_code* | HTTP status related to the failure, when applicable |


&nbsp;

&nbsp;

### Example queries

#### PostgreSQL (schema hck\_hub)

&nbsp;

> SELECT error\_type, error\_message, git\_provider, repository\_name, model\_path, created\_at\
FROM hck\_hub.sync\_errors\
WHERE created\_at \> now() - interval '24 hours'\
ORDER BY created\_at DESC\
LIMIT 100;

&nbsp;

&nbsp;

Count recent webhook failures:

&nbsp;

> SELECT count(\*) AS webhook\_errors\_last\_24h\
FROM hck\_hub.sync\_errors\
WHERE error\_type = 'webhook\_error'\
&nbsp; AND created\_at \> now() - interval '24 hours';

&nbsp;

&nbsp;

#### Oracle

&nbsp;

> SELECT error\_type, error\_message, git\_provider, repository\_name, model\_path, created\_at\
FROM sync\_errors\
WHERE created\_at \> SYSTIMESTAMP - INTERVAL '1' DAY\
ORDER BY created\_at DESC\
FETCH FIRST 100 ROWS ONLY;

&nbsp;

&nbsp;

Alert when the rate of new *sync\_errors* rows rises suddenly, or when *webhook\_error* rows appear continuously (often a bad webhook URL, secret, or network path from the Git provider to the Model Hub).

&nbsp;

&nbsp;

## Suggested alert checklist

&nbsp;

* */health* failing or Model Hub container/pod not ready
* Repeated container restarts
* Elevated HTTP 5xx rate
* Repeated 401/403 after authentication was enabled
* Database connectivity errors in logs
* Growth of rows in *sync\_errors* (especially *webhook\_error* spikes)
* Filestore / disk usage high on */home/node/.hub*

&nbsp;

