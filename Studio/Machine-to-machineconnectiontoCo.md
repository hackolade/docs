# Machine-to-machine connection to Collibra

This page is relevant for machine-to-machine OAuth to a Collibra instance using a service account.  It does not apply for Hackolade Studio [client connection to a Collibra instance using an identified user via OAuth](<OAuthsetupwithEntraID.md> "client connection to a Collibra instance using an identified user via OAuth").

&nbsp;

Use this Machine-to-machine OAuth for Collibra Data Dictionary to create and test a connection in Hackolade Studio, then run publishing to Collibra via the Command Line Interface, possibly on a dedicated server, and possibly in Docker. Connecting from the Studio application is not supported for this auth type.

&nbsp;

## Connect the CLI to Collibra with client credentials

### &#49;. Prerequisite in Collibra: register a new application

&nbsp;

&#49;. In Collibra, go to OAuth settings and register a new application [Collibra OAuth documentation](<https://productresources.collibra.com/docs/collibra/latest/Content/Settings/OAuth/co\_oauth-settings.htm> "Collibra OAuth documentation")

&nbsp;

&#50;. Choose application type Integration (not Platform)

&nbsp;

![Collibra M2M Register application](<lib/Collibra M2M Register application.png>)

&nbsp;

&#51;. Retain the Client ID and Client Secret, they will be needed in next step in Studio.

&nbsp;

&nbsp;

### &#50;. Create a Collibra connection in Studio UI

1. Access the Data Dictionary Connections in Hackolade Studio Desktop.

   1. Create a new model (pick the target you need, e.g. MongoDB).
   1. Open Main Menu \> Tools \> Forward-Engineer \> Governance Platforms \> Collibra…

1. Click Add
1. Fill in in Connection tab:

   1. Name: e.g. My Collibra client credentials connection
   1. Path: your Collibra base URL (e.g. [https://your-instance.collibra.com](<https://your-instance.collibra.com/> "https://your-instance.collibra.com"))

1. Fill in in Authentication tab:

   1. Authentication: OAuth
   1. Identity provider: Collibra client credentials (Command Line Interface only)
   1. Client ID and Client Secret: obtained at step 1 from Collibra OAuth settings

1. Click Test connection: should succeed.
1. Click Save.

&nbsp;

A yellow warning explains this connection is CLI only.

&nbsp;

![Collibra M2M Create CLI connection](<lib/Collibra M2M Create CLI connection.png>)

&nbsp;

### &#51;. Use the connection in CLI

#### Option A: saved connection name

Export is optional if the connection is saved in the same Hackolade profile the CLI uses.

#### Option B: export file

&nbsp;

&#49;. In Studio ID, select the connection in the list.

&#50;. Click Export and save the JSON/BIN file.

&#51;. Then run CLI from a terminal (see [Command Line Interface documentation](<https://hackolade.com/help/CommandLineInterface.html#forwEngDataDictionary> "Command Line Interface documentation").)

&nbsp;

**Publishing example:**

&nbsp;

> hackolade forwengdatadictionary \\\
 --connectname="My Collibra client credentials connection" \\\
 --model="/path/to/model.json" \\\
 --targetresource=your\_collibra\_domain\_name

&nbsp;

**Reverse-engineer example:**

&nbsp;

> hackolade revengdatadictionary \\\
 --target=MONGODB \\\
 --connectname="My Collibra client credentials connection" \\\
 --datadictionaryresource=your\_collibra\_domain\_name \\\
 --model="/absolute/path/to/output-model.json"

&nbsp;

Use --connectfile instead of --connectname when using an exported JSON file.

&nbsp;

## Additional notes

While the GUI can be used to create a CLI connection in Hackolade Studio to be reused by the CLI, it is not possible to use a machine-to-machine OAuth mechanism from the GUI.

&nbsp;

CLI-only connections show a “CLI only” badge in the list. 

&nbsp;

![Collibra M2M CLI only badge](<lib/Collibra M2M CLI only badge.png>)

&nbsp;

Connect or double-click shows a warning and stops.

&nbsp;

![Collibra M2M CLI only dialog](<lib/Collibra M2M CLI only dialog.png>)
