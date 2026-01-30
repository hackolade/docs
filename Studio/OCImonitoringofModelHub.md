# OCI monitoring of Model Hub

This page provides a step-by-step visual guide for monitoring an Autonomous JSON Database on OCI, based on this [Oracle documentation](<https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/mdw-monitoring-database-actions-database-monitor.html> "target=\"\_blank\"").

## Open console screen for your database

* In the OCI Console, open the menu → Oracle AI Database → [Autonomous AI Database](<https://cloud.oracle.com/db/adbs> "target=\"\_blank\"")
* Click your database name to open its [Details page](<https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/autonomous-monitor-perf-hub.html> "target=\"\_blank\""). &nbsp;

&nbsp;

## View high-level health in the Monitoring tab

On the database Details page, click Monitoring (this shows the default charts: CPU, DB Time, logons, storage, I/O, etc.).

* Use the Interval and Statistic controls on each chart to change granularity.
* This view is backed by the oci\_autonomous\_database metrics namespace.&nbsp; Consult this [documentation page](<•%20https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/autonomous-monitor-metrics.html> "target=\"\_blank\"") for further details. &nbsp;

&nbsp;

Quick reads

* CPU Utilization (percent across consumer groups): sustained \>~80% suggests need for scaling or tuning.
* DB Time (sec/sec): rises with latency and call volume, if DB Time climbs while CPU is low, wait events/I/O are likely.
* Current Logons / Sessions: concurrency pressure; combine with CPU and waits.
* Read/Write Throughput \& IOPS: large JSON scans or unindexed filters. Consult this [documentation page](<https://docs.oracle.com/iaas/autonomous-database-serverless/doc/autonomous-monitor-metrics-list.html> "target=\"\_blank\"") for further details. &nbsp;

&nbsp;

**Tip:** Many teams set an alarm on CpuUtilization \> 80% for 5 minutes to catch hot spots early. Consult this [documentation page](<https://www.ateam-oracle.com/post/oci-native-monitoring-and-alerting-for-autonomous-database-and-db-systems> "target=\"\_blank\"") for further details.

&nbsp;

## Deep dive in the Performance Hub

From the **Details** page, click **Performance Hub** (or go via **Database Actions → Performance Hub**).&nbsp; This opens the main tuning workspace.&nbsp; Consult this [documentation page](<https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/autonomous-monitor-perf-hub.html> "target=\"\_blank\"") for further details.&nbsp;

### What you’re looking at

* **Time Range / Time Zone** selectors at the top control all charts.
* **Activity Summary (Average Active Sessions)** breaks load into **CPU**, **User I/O**, and **Wait** — it is great for spotting *what* you’re constrained by. Consult this [documentation page](<https://docs.oracle.com/en-us/iaas/performance-hub/doc/common.html> "target=\"\_blank\"") for further details.

&nbsp;

### Tabs you’ll use most

* **Activity (ASH Analytics)**: slice active sessions by waits, SQL ID, user, module — use it when DB Time is high but CPU isn’t.&nbsp; Consult this [documentation page](<https://docs.oracle.com/en/database/oracle/oracle-database/26/tgdba/generating-performance-hub-active-report.html> "target=\"\_blank\"") for further details.&nbsp;
* **SQL Monitoring**: shows heavy SQL with plans and execution stats; click a **SQL ID** to open a live report.&nbsp; Consult this [documentation page](<https://docs.oracle.com/iaas/autonomous-database-serverless/doc/autonomous-monitor-metrics-list.html> "target=\"\_blank\"") for further details.&nbsp;
* **Reports**: generate **AWR** and **ASH** reports for sharing/offline analysis (Typical/Basic levels).&nbsp; Consult this [documentation page](<https://docs.oracle.com/en-us/iaas/performance-hub/doc/common.html> "target=\"\_blank\"") for further details. &nbsp;

## How to interpret quickly (cheat sheet)

* **CPU-bound (AAS mostly CPU)** → add OCPUs (autoscaling/ECPU helps) or tune top SQL. [docs.oracle.com](<https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/autonomous-monitor-perf-hub.html?utm\_source=chatgpt.com>)
* **I/O-bound (AAS mostly User I/O)** → add/filtering indexes (e.g., JSON Search Index), reduce scans, check read/write charts. [docs.oracle.com](<https://docs.oracle.com/iaas/autonomous-database-serverless/doc/autonomous-monitor-metrics-list.html?utm\_source=chatgpt.com>)
* **Wait-bound (AAS mostly “Wait”)** → use **Activity/ASH** to pinpoint the wait class (locks, concurrency, network). [docs.oracle.com](<https://docs.oracle.com/en-us/iaas/performance-hub/doc/common.html?utm\_source=chatgpt.com>)

&nbsp;

