# Monitoring and alerting

You can operate the Model Hub like any other production web service: watch process health, resources, logs, and model-sync failures.

&nbsp;

## Health checks and readiness

The Model Hub process listens on port *3000* and exposes a *GET /health* and *GET /ready* endpoint. A successful check is an HTTP *200* response.

&nbsp;

Use this endpoint for:

- Docker / Compose health checks (already defined in the official image)
- Kubernetes liveness and readiness probes
- Load balancer health checks

&nbsp;

See Install and start the server for the reference health-check command.

&nbsp;

Also monitor the **database migration** job on install and upgrade. A non-zero exit from *model-hub-\*-database-migration* would mean that the schema was not applied successfully; do not ignore failed migration containers.

&nbsp;

## Resource metrics

Collect at least:

- CPU and memory usage for the *model-hub* container (or pod)
- Disk usage for the filestore volume (/home/node/.hub)
- Database CPU, storage, connection count, and free space (on the external PostgreSQL or Oracle instance)

&nbsp;

Alert when the Model Hub container restarts repeatedly, when memory grows without bound under sync load, or when the filestore volume is close to full.

&nbsp;

## Logs

The Model Hub writes **JSON logs** to the container’s standard output (stdout). Ship them to your central logging platform.

&nbsp;

You will see:

- Access / request logs for HTTP traffic
- Warning and error logs for unexpected conditions (for example database connectivity problems or Git provider failures)

&nbsp;

Useful alert ideas on log streams:

- Spikes in HTTP \*\*5xx\*\* responses
- Repeated \*\*401\*\* / \*\*403\*\* after authentication was enabled (often an IdP or redirect URI misconfiguration)
- Messages indicating database connection or pool errors
- Messages indicating Git provider or webhook processing failures

&nbsp;

## Model sync errors

When the Model Hub fails to process a webhook or to sync a model file, it records the failure in the \`sync_errors\` table in the Model Hub database. Monitor this table in addition to logs.

&nbsp;

### Useful columns

<table style="width:70%">
<colgroup><col style="width:13%"><col style="width:87%"></colgroup>
<thead>
<tr>
<th>Column</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr>
<td><em>error_type</em></td>
<td><em>webhook_error</em> failure when the Git provider called the webhook endpoint; model_sync failure while processing model files</td>
</tr>
<tr>
<td><em>error_message</em></td>
<td>Human-readable error text for troubleshooting</td>
</tr>
<tr>
<td><em>created_at</em></td>
<td>When the error was recorded</td>
</tr>
<tr>
<td><em>git_request_id</em></td>
<td>Identifier from the Git provider webhook, when available</td>
</tr>
<tr>
<td><em>git_provider</em></td>
<td>Provider that triggered the sync</td>
</tr>
<tr>
<td><em>repository_name</em></td>
<td>Repository involved, when available</td>
</tr>
<tr>
<td><em>branch_name</em></td>
<td>Branch involved, when available</td>
</tr>
<tr>
<td><em>model_path</em></td>
<td>Model file path involved, when available</td>
</tr>
<tr>
<td><em>http_status_code</em></td>
<td>HTTP status related to the failure, when applicable</td>
</tr>
</tbody>
</table>

&nbsp;

### Example queries

#### PostgreSQL (schema hck_hub)

```sql
SELECT error_type, error_message, git_provider, repository_name, model_path, created_at
FROM hck_hub.sync_errors
WHERE created_at > now() - interval '24 hours'
ORDER BY created_at DESC
LIMIT 100;
```

&nbsp;

Count recent webhook failures:

&nbsp;

```sql
SELECT count(*) AS webhook_errors_last_24h
FROM hck_hub.sync_errors
WHERE error_type = 'webhook_error'
  AND created_at > now() - interval '24 hours';
```

&nbsp;

#### Oracle

```sql
SELECT error_type, error_message, git_provider, repository_name, model_path, created_at
FROM sync_errors
WHERE created_at > SYSTIMESTAMP - INTERVAL '1' DAY
ORDER BY created_at DESC
FETCH FIRST 100 ROWS ONLY;
```

&nbsp;

Alert when the rate of new *sync_errors* rows rises suddenly, or when *webhook_error* rows appear continuously (often a bad webhook URL, secret, or network path from the Git provider to the Model Hub).

&nbsp;

## Suggested alert checklist

- */health* failing or Model Hub container/pod not ready
- Repeated container restarts
- Elevated HTTP 5xx rate
- Repeated 401/403 after authentication was enabled
- Database connectivity errors in logs
- Growth of rows in *sync_errors* (especially *webhook_error* spikes)
- Filestore / disk usage high on */home/node/.hub*
