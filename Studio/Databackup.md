# Data backup

The Model Hub persists state in its state in the database. Back it up regularly, and always take a backup before upgrading.

&nbsp;

| **What** | **Where** | **Why it matters** |
| --- | --- | --- |
| SQL database | Your PostgreSQL or Oracle instance | Stores models metadata, sync state, Git provider configuration, and other application data |


&nbsp;

**Note:** if you restore the database without the matching filestore (or vice versa), encrypted secrets in the database may become unreadable. Treat the database and filestore as a single backup set.

&nbsp;

## Backup your Model Hub database instance

Use your organization’s standard backup process for the database engine you chose at install time:

&nbsp;

* **PostgreSQL 17+**: managed snapshots, continuous backup, or *pg\_dump* / *pg\_basebackup* according to DBA standards
* **Oracle 26ai**&nbsp; RMAN, managed backups, or your platform’s equivalent

&nbsp;

Back up the Model Hub database (and schema) used by the application. Follow your DBA guidelines for consistency (for example, a snapshot that includes all tables owned by the Model Hub).

&nbsp;

For a quick backup, you can also choose to just back up the tables *git\_repositories* and *kvs*.&nbsp;

* *git\_repositories* contains the list of all Git repositories that contain your models.&nbsp;
* *kvs* contains your configuration. Most importantly, the Git configuration and authentication.

&nbsp;

With only these 2 tables, Model Hub will be able to reconstruct the rest by syncing your models from the configured Git providers, which remain the master single-source-of-truth.

&nbsp;

**Note:** prefer a normal full or incremental database backup over exporting individual tables. The Model Hub schema is maintained by the migration image; do not rely on “recreating the schema on restart” as a substitute for a proper backup and restore procedure.

&nbsp;

## When to back up

On a regular schedule that matches your recovery objectives (for example daily database backups)

* Before every Model Hub upgrade (new *MODEL\_HUB\_VERSION*)
* Before and after major changes to Git provider configuration or authentication
* Before destructive maintenance on the database or host

&nbsp;

## Restore overview

&#49;. Restore your Model Hub database to a consistent point in time.

&#50;. Start Model Hub.

&#51;. Confirm:

* *GET /health* returns HTTP 200
* The UI loads
* Git provider configuration still works (or re-enter secrets if you intentionally rotated them)
* &nbsp;Recent models are visible / sync still functions

&nbsp;

You should document your restore *runbook* and test it periodically.

