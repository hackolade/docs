# Connect to a BigQuery instance

To access an Google BigQuery project, Hackolade currently supports access through a Service Account associated with your Google Could project.&nbsp; Credentials are loaded from a file created in the [Google IAM \& Admin console](<https://console.cloud.google.com/iam-admin/iam> "target=\"\_blank\"") by your administrator.

&nbsp;

Give a meaningful name to the connection, optionally provide a specific project id, and reference the path and name of the key file provided by your administrator.

&nbsp;

![BigQuery connection settings](<lib/BigQuery connection settings.png>)

&nbsp;

&nbsp;

The Hackolade process for reverse-engineering of Google BigQuery datasets includes the execution of SQL statements to discover datasets, tables and views, columns and their data types.&nbsp;

&nbsp;

## Instructions to create a Service Account key file

Here are the steps to follow:

&#49;) go to the IAM console, and choose [Service Accounts](<https://console.cloud.google.com/projectselector2/iam-admin/serviceaccounts?supportedpurview=project> "target=\"\_blank\"") in the menu

&#50;) select an existing project, and press the button + Create a Service Account

&#51;) provide the service account details, and create

&#52;) grant the following service account access to the project:

&nbsp; &nbsp; - BigQuery Data Viewer: in order to be able to perform reverse-engineering

and

&nbsp; &nbsp; - BigQuery Data Editor: in order to be able to forward-engineer (apply SQL script to instance)

&nbsp; &nbsp; - BigQuery Job User: in order to be able to forward-engineer (apply SQL script to instance)

![Image](<lib/BigQuery Service Account role creation.png>)

&nbsp;

then save the role

&#53;) select the action Manage Keys for the service account:

![BigQuery Service Account key creation](<lib/BigQuery Service Account key creation.png>)

&nbsp;

and create a new key with JSON type.&nbsp; The .json file gets downloaded in the browser.

&nbsp;

This is the file to be referenced in the connection settings dialog.

&nbsp;

